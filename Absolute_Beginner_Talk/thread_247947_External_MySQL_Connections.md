---
title: "External MySQL Connections"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Sam Fisher on 2006-08-31
I have setup SQL with PHP etc and apache2. It works perfectly locally. However, I am trying to access the database from an external server, also one elsewhere in a different place via the internet. I have tried commenting out the 'BIND IP      = 127.0.0.1' line in 'my.cnf' too no avail. I also am not trying to use root as that cannot be reached externally. 

Any ideas what im doing wrong?

---

### Post by kidders on 2006-09-03
There are two things you need to take care of here.

1 - Get mysql to listen on (bind to) an externally accessible IP
2 - Set up a mysql user with enough privileges to connect

**Listening on the right port**

If you are altering a "bind-address" directive in my.cnf, make sure it is one in the [mysqld] section, which affects running servers. Also, take a look for others within the same section that might be overriding yours. Don't forget to restart the service afterwards.

**Setting up a user**

You need to specify acceptable hostnames (or hostname patterns) in your "GRANT" statements to successfully connect. Since you didn't specify in your post, I'm not sure if the problem you're having is here, or with establishing any kind of connection in the first place.

Other considerations include, of course, your firewall settings.

Is any of this helpful?

---

