 mysql  单列索引和组合索引 简介  
<pre>
1  表建立数据 
   数据尽量大 数据小很有可能用不到索引
2 第一种情况 
  表 
  假如有  a  b  c 列 
  a 列单独索引 
  abc 组合索引    
  select  * from  表 where a=1212
  此时 表只会用到a 索引    
  select * from  表  where a=1212 and b=1212
  此时表用到 abc 组合索引  
  select * from  表  where b=1212 and  a=1212
  此时数据库会优化查询语句  还是会用到abc组合索引  
  select * from 表  where  a=1212 or b=2121
  此时搜索中有or的时候  单列索引a和组合abc 全部用到

3 第二种情况
   表
   假如有  a  b  c 列
   a 列单独索引
   b 列单独索引  
   select  * from  表 where a=1212
   此时 表只会用到a 索引   
   select * from  表  where a=1212 and b=1212
   此时表 只会用到一个索引 数据会从a 和b 索引中选择最优索引  
   select * from  表  where b=1212 and a=1212
   此时表 只会用到一个索引 数据会从a 和b 索引中选择最优索引  
   select * from 表  where  a=1212 or b=2121
   此时搜索中有or的时候   单列索引a和单列索引b 全部用到

4 第三情况
   表
   假如有  a  b  c 列
   a 列单独索引   
   select  * from  表 where a=1212
   此时 表只会用到a 索引  
   select * from  表  where a=1212 and b=1212
   此时 表只会用到a 索引  
   select * from  表  where b=1212 and a=1212
   此时 表只会用到a 索引  
   select * from 表  where  a=1212 or b=2121
   此时搜索中有or的时候  无索引可以使用
 
 

