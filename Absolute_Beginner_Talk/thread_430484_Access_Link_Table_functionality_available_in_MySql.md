---
title: "Access Link Table functionality available in MySql?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by johnleonard on 2007-05-02
Access has a very useful feature of being able to link to external data sources (eg a spreadsheet) via the Link Table functionality. This is great for a one-off query as linking to a spreadsheet is quicker and easier than importing it and does not result in a huge unwieldy database. 

I have been scouring the various forums to see if this is possible in MySQL. Specifically I would like to run a query on a large Excel or CSV file on localhost without having to go through the hasssle of importing it. Does anyone know how this could be done?

---

### Post by gerscht on 2007-05-02
Nope, unfortuantly that's not possible.
But if you have a csv file, you can load it quite fast in your DB (providing the table structure exists) using 
```
LOAD DATA INFILE
```
[http://dev.mysql.com/doc/refman/5.0/en/load-data.html](http://dev.mysql.com/doc/refman/5.0/en/load-data.html)

Gerscht

---

### Post by johnleonard on 2007-05-02
Thanks Gerscht

I feared that might be the case. A useful feature for Mysql developers to think about perhaps. The problem is I work with large (wide) spreeadsheets and don't really want to have to split them up into individual tables, create table structures, import them and export the query results for just one query. On another forum someone mentioned trying the ODBC connector, but they didn't sound too sure.  has anyone tried this?

---

