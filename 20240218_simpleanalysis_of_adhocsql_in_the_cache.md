#Analyzing Adhoc SQL in the procedure cache

##Introduction
I went to a new customer recently & found they have a bit of a problem with cache bloat due to a lot of ad-hoc SQL. 
Interestingly they have optimize for adhoc SQL enabled but not the database option for forced parameterization.

Still the question is how can one get a handle on 150000 different adhoc SQL plans in the cache - certainly too many to browse through.
In this particular database there are about 1000 tables so it seemed like a good approach would be to concentrate on the tables that each query targets
and ignore the columns and the where criteria on the working theory that this is where the dynamic SQL is concentrated.

'''
SELECT * FROM x
'''
