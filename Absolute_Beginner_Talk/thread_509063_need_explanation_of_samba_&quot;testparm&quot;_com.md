---
title: "need explanation of samba &quot;testparm&quot; command"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by waqas_butt0071 on 2007-07-25
well on my system it is working fine but i do not know what the comamnd 

"sudo testparm"

is doing. i have installed the samba server and configured its config file. but i do not know what this command does.

---

### Post by Koybe on 2007-07-25
It's just checking your config file fore any error. If you want to know more about a command you can always type "man command" :
```
man testparm
```> **DESCRIPTION**

       This tool is part of the **[samba(7)]("http://www.hmug.org/man/7/samba.php")** suite.


       **testparm**  is  a very simple test program to check an **[smbd(8)]("http://www.hmug.org/man/8/smbd.php")** configura-
       tion file for internal correctness. If this program  reports  no  prob-
       lems,  you  can  use  the  configuration file with confidence that **smbd**
       will successfully load the configuration file.


       Note that this is **NOT** a guarantee that the services  specified  in  the
       configuration file will be available or will operate as expected.


       If the optional host name and host IP address are specified on the com-
       mand line, this test program will run through the service  entries  re-
       porting whether the specified host has access to each service.


       If  **testparm**  finds  an  error in the  *smb.conf* file it returns an exit
       code of 1 to the calling program, else it returns an exit  code  of  0.
       This allows shell scripts to test the output from **testparm**.





---

