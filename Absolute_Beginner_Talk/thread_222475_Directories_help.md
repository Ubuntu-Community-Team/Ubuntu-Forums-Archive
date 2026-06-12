---
title: "Directories help"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Soap_Dude on 2006-07-25
Hi,

I was [ls -l] some directories, and I'm not sure what the "l" in "lrwx..." means. Also, how do I create one of those. Thanks

---

### Post by timetunnel on 2006-07-25
The "l" means that it's not a real file/directory but only a *link* to another file/directory in *another* location.

Say you have a file with a long name called /usr/bin/blah/blah.12.moreblah.34 and want to have "simpler" way to access it, without all the numbers and gibberish. You can create a link to it called /usr/bin/blah, which is nothing more than a pointer to /usr/bin/blah/blah.12.moreblah.34
So if you do anything with or to  /usr/bin/blah you're doing it to /usr/bin/blah/blah.12.moreblah.34 actually. However, deleting such a link does not delete the stuff it links to.

The command "ln" can be used to create links. For more information, see "man ln".

---

### Post by Thund3rstruck on 2006-07-25
For a quick review of parameters use the --help option

$ls --help

---

### Post by ProjectGod on 2006-07-25
those lovely cyan coloured objects are symlinks. kinda like window's shortcuts. 

create them with:

x@y:/$ **ln -s <sourcetargetname> <destinationlinkname>**

e.g. x@y:/$ [B]ln -s /sbin/masteryoda /home/skywalker/desktop/yoda
[/B]
when you do an: ls -l at the terminal you can tell what these symbolic links are point to... link > source.

alternatively you can create symlinks with the cp command too:

x@y:/$ **cp -s /sbin/masteryoda /home/skywalker/desktop/yoda**

---

