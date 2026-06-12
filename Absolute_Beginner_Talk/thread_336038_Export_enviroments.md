---
title: "Export enviroments"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by yeoheric on 2007-01-11
Hi,

I edited my .bashrc file and added in the following at the bootom of the file:
 
export JAVA_HOME=/foo/bar/dir
export CATALINA_HOME=/too/much/dir 

When I log off and on again, I get this:

[FONT="Courier New"]indon@snoopy:~$ echo $JAVA_HOME

indon@snoopy:~$ echo $CATALINA_HOME

[/FONT]

I should get something like [FONT="Courier New"]/foo/bar/dir [/FONT]when I type in [FONT="Courier New"]echo $JAVA_HOME[/FONT] right?

Please assist as it's a real hassle to do the export of variables everytime before I run Tomcat.

Some extra info, I am running Ubuntu Server 6.06.1 and the user indon is the second user created and belong to his own group,

Thanks.

Eric

---

