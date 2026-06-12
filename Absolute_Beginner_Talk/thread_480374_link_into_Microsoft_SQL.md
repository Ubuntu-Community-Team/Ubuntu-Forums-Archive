---
title: "link into Microsoft SQL"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by avago on 2007-06-21
Hello all
    This is my first post, I have a server running Ubuntu, the server processes information from clients (650 )
which is using Mysql on the  server at present, because of all the different bits of info coming back from the clients ( 20000) at present the SQL is struggling to process the requests fast enough.

Is it Possible to have an external SQL server ( MS 2XXX ) and how is it done, If it is possible it would speed things up.

Hope someone may Be able to help

Best Regards

AVAGO:)

---

### Post by asommer on 2007-06-21
It's possible to connect to a MSSQL database from Linux you'll need to install these packages and their dependencies:
```

  tdsodbc                   
  unixodbc 
```

You'll then need to configure them.  Here's a guide that should give you a rough idea of which files to edit and what to edit inside those files:

[http://wiki.rubyonrails.org/rails/pages/HowtoConnectToMicrosoftSQLServerFromRailsOnLinux](http://wiki.rubyonrails.org/rails/pages/HowtoConnectToMicrosoftSQLServerFromRailsOnLinux)

The guide is specific to Rails, but once you have **unixodbc** and **freetds** configured you'll then need to install the binding for your specific language.  For instance I use **libdbd-odbc-perl** for Perl.

Hope that helps if you have a more specific question reply and I'll see if I can help.

---

