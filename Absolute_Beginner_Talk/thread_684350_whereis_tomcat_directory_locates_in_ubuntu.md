---
title: "whereis tomcat directory locates in ubuntu"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-02-01
i just installed apache tomcat admin 5.5 on my system from synaptic package manager
after installation im wondering where i can find the installed directory of apache tomcat
im using ubuntu 6.10
plz help me

---

### Post by ssuehr on 2008-02-02
A couple thoughts.  From the command line, you could do:

dpkg -L <package name>

I'm not sure what the package name is for tomcat, but if it was apache-tomcat you'd do:

dpkg -L apache-tomcat

That would list all the files and directories and their locations from that package.

Otherwise if the directory was named tomcat you could do:

find / -name tomcat

---

