---
title: "Java"
date: 2005-08-18
forum: Apple PPC Users
---

### Post by BigTunaCan on 2005-08-18
I installed the Java with Netbeans bundle.  The install appeared to go fine.  Netbeans opens and runs correctly.  But when I try to run any of the Java files in the bin directory they do not do anything.

When I enter java or javac at the terminal prompt I just recieve the message "command not found".  What am I doing wrong?  I'm a complete newb to Linux...

---

### Post by heimo on 2005-08-18
Maybe you don't have your path set to find binaries in that /bin directory where javac (and other binaries you installed) are located?
 ```

echo $PATH

``` 

You can set it in ~/.bashrc or /etc/profile.

 > But when I try to run any of the Java files in the bin directory they do not do anything. 

If you run them in the bin directory and it's not in PATH, you have to run them like
 ```
./javac
```

---

### Post by BigTunaCan on 2005-08-19
Thanks for your quick response!  That was exactly what was wrong!  After I added the path into the bash.bashrc file it worked fine.  I'm so used to Windows where the current directory is always implied in the path.

---

