---
title: "problem with apache !!!!"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-02-25
hello all 

iam facing aproblem with my apache i want to setup an an alias that makes me able to access the documentations out side the document root .....

first i make a dir called test at the /var and 

then i creat an html file at the /var/test/index.html 

[PHP]adam@adam-laptop:/var/test$ cat index.html 
<html>
<body><P>hello</p></body>
</html>
[/PHP]

so at the apache httpd.conf file i set an alias to make this accessible by the broweser by [http://localhost/test](http://localhost/test) and here is the configuration that i made > 

[PHP] 
<IfModule alias_module>
    #
    # Redirect: Allows you to tell clients about documents that used to 
    # exist in your server's namespace, but do not anymore. The client 
    # will make a new request for the document at its new location.
    # Example:
    # Redirect permanent /foo http://www.example.com/bar

    #
    # Alias: Maps web paths into filesystem paths and is used to
    # access content that does not live under the DocumentRoot.
    # Example:

    #
    # If you include a trailing / on /webpath then the server will
    # require it to be present in the URL.  You will also likely
    # need to provide a <Directory> section to allow access to
    # the filesystem path.
alias   /test   /var/test
 [/PHP]

as shown i made alia	/test	/var/test 


and when i get my apache up and want to access the page i got this error 

Forbidden

You don't have permission to access /test on this server.


so what is the problem how ever when i doing ls -ali for the /var/test

[PHP] adam@adam-laptop:/var/test$ ls -ali
total 12
2215235 drwxr-xr-x  2 root root 4096 2007-02-24 05:24 .
1987137 drwxr-xr-x 20 root root 4096 2007-02-24 05:24 ..
2215236 -rw-r--r--  1 adam root   42 2007-02-24 05:25 index.html
[/PHP]

as the shown the index.html is owned by adam which is normal user at the system so what is the problem plz :)

---

### Post by solar george on 2007-02-25
You need to set the ownership of the directory and files to www,

```
sudo chown -R WWW:WWW /var/test
```

---

### Post by black_ice on 2007-02-25
thanx it works :)

---

