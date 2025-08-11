Advanced Data Mining Lab 6: Association Rule Mining

Purpose of Lab Work

This lab explores association rule mining techniques using the Apriori and FP-Growth algorithms to analyze retail data. The primary objectives were to:

- Identify frequent itemsets in customer purchase patterns using both Apriori and FP-Growth algorithms
- Generate meaningful association rules to find out the hidden relationships between products
- Compare algorithm performance between Apriori and FP-Growth approaches
- Apply data visualization techniques using Seaborn to interpret mined patterns and insights
- Understand real-world applications of association rule mining in retail scenarios

The lab uses the Online Retail Dataset from UCI Machine Learning Repository, containing real-world e-commerce transactions.

Key Insights from Analysis and Association Rules

Dataset Characteristics
- Original Dataset: 541,909 transactions across 8 columns
- After Cleaning: 397,884 valid transactions with 4,338 unique customers
- Product Diversity: 3,877 unique products (filtered to top 150 for analysis)
- Analysis Base: 13,387 transactions containing 2+ items

Frequent Itemset Discovery
Both algorithms identified 246 frequent itemsets with identical results:
- 150 single-item sets: Individual products meeting minimum support threshold (2%)
- 91 two-item sets: Product pairs frequently purchased together  
- 5 three-item sets: Complex product combinations with strong associations

Top Frequent Items by Support:
1. WHITE HANGING HEART T-LIGHT HOLDER (14.18% support)
2. REGENCY CAKESTAND 3 TIER (11.95% support)
3. JUMBO BAG RED RETROSPOT (11.68% support)
4. ASSORTED COLOUR BIRD ORNAMENT (9.81% support)
5. PARTY BUNTING (9.76% support)

Association Rules Analysis
Generated 199 high-quality association rules meeting confidence threshold (20%):

Strongest Association Rules:
- PINK REGENCY TEACUP + ROSES REGENCY TEACUP → GREEN REGENCY TEACUP
  - Support: 2.91%, Confidence: 89.45%, Lift: 17.41
  - Interpretation: Customers buying pink and roses teacups have 89% probability of also purchasing green teacups

- PINK REGENCY TEACUP + REGENCY CAKESTAND → GREEN REGENCY TEACUP
  - Support: 2.02%, Confidence: 87.70%, Lift: 17.07
  - Interpretation: Strong cross-selling opportunity between coordinated tea service items

Business Insights:
- Product Bundling Opportunity: Regency tea set items show exceptionally strong associations (lift values >17)
- Cross-selling Potential: Garden-themed items (kneeling pads) demonstrate complementary purchase patterns
- Customer Behavior: High-confidence rules indicate predictable purchasing patterns for home décor items

Algorithm Performance Comparison
- Apriori Execution Time: 3.11 seconds
- FP-Growth Execution Time: 6.32 seconds  
- Result: Apriori performed 0.49x faster than FP-Growth for this dataset
- Consistency: Both algorithms produced identical frequent itemsets and association rules

Challenges Faced and Decisions Made

Memory Optimization Challenge
Problem: Initial dataset contained 3,871 unique products, creating a massive search space requiring 7.39 GiB memory allocation that exceeded system capabilities.

Solution Implemented:
- Filtered dataset to top 150 most popular items based on purchase frequency
- Reduced memory requirements from 7.39 GiB to manageable levels
- Maintained analytical integrity while focusing on most commercially relevant products

Parameter Tuning Decisions
Support Threshold: Increased from 1% to 2% minimum support
- Rationale: Higher threshold ensures more statistically significant patterns
- Impact: Focused analysis on items appearing in at least 267 transactions
- Benefit: Reduced noise and improved rule interpretability

Confidence Threshold: Set at 20% minimum confidence
- Rationale: Balanced between rule quantity and quality
- Result: Generated 199 meaningful rules with practical business value

Data Quality Considerations
Missing Data Handling:
- Removed 135,080 transactions missing CustomerID (25% of original data)
- Eliminated 1,454 transactions with missing product descriptions
- Filtered out negative quantities (cancelled transactions)

Transaction Filtering:
- Included only transactions with 2+ items for meaningful basket analysis
- Focused on positive quantities and valid unit prices
- Maintained data integrity while maximizing analytical value

Technical Implementation Decisions
- Visualization Strategy: Created item co-occurrence heatmaps for top 20 products to highlight strongest associations
- Performance Monitoring: Implemented timing analysis to compare algorithm efficiency
- Memory Management: Used pandas optimization techniques for large dataset handling

Repository Structure
MSCS_634_Lab_6/
├── association_rule_mining_lab6.ipynb    # Main analysis notebook
├── Online_Retail.xlsx                    # Dataset (download separately)
├── README.md                            # This documentation
└──                   


Key Takeaways
1. Algorithm Selection: For this dataset size and structure, Apriori outperformed FP-Growth in execution time
2. Memory Management: Product filtering is essential for large retail datasets with diverse inventories  
3. Data Quality: Proper preprocessing significantly impacts analysis quality and computational efficiency