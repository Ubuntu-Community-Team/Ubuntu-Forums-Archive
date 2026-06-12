---
title: "MySQL Remote Connection"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Digital221 on 2006-10-06
Hi all, Im trying to connect to my MySQL database from a remote server. Im using the below asp srcipt but im having no luck.  Im getting this error: 

[MySQL][ODBC 3.51 Driver]Can't connect to MySQL server on '83.146.35.143' (10060)

Can anyone tell me i need to download to get the connection working or what settings i need to change?  Im happy to change the driver im using. Thanks

<%
Dim sConnection, objConn , objRS

sConnection = "Driver={mySQL ODBC 3.51 Driver};Server=83.146.35.143;Port=3306;Option=4;Database=MyDatabase;Uid=ben;Pwd=33EA2B98AFCE5A050F054938B310CD3E461EFE5E;"

Set objConn = Server.CreateObject("ADODB.Connection")

objConn.Open(sConnection)

Set objRS = objConn.Execute("SELECT username, password FROM accounts")

Response.Write objRS.Fields("username") & ", " & objRS.Fields("password") & "<br>"

objRS.Close
Set objRS = Nothing
objConn.Close
Set objConn = Nothing
%>

---

### Post by sbassett on 2006-10-06
> **Digital221 said:**
> Hi all, Im trying to connect to my MySQL database from a remote server. Im using the below asp srcipt but im having no luck.  Im getting this error: 

[MySQL][ODBC 3.51 Driver]Can't connect to MySQL server on '83.146.35.143' (10060)

Can anyone tell me i need to download to get the connection working or what settings i need to change?  Im happy to change the driver im using. Thanks

<%
Dim sConnection, objConn , objRS

sConnection = "Driver={mySQL ODBC 3.51 Driver};Server=83.146.35.143;Port=3306;Option=4;Database=MyDatabase;Uid=ben;Pwd=33EA2B98AFCE5A050F054938B310CD3E461EFE5E;"

Set objConn = Server.CreateObject("ADODB.Connection")

objConn.Open(sConnection)

Set objRS = objConn.Execute("SELECT username, password FROM accounts")

Response.Write objRS.Fields("username") & ", " & objRS.Fields("password") & "<br>"

objRS.Close
Set objRS = Nothing
objConn.Close
Set objConn = Nothing
%>

I believe you can grab the mysql-client out of the repos, also make sure port 3306 is open on your MYSQL server.

---

