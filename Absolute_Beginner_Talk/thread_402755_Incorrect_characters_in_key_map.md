---
title: "Incorrect characters in key map"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by pippy on 2007-04-06
Recently I installed some software via apt-get in order to share files. Now every once in a while gnome comes up with an error stating that there is an incorrect character '#' in the keyboard map. 

I know why it is doing this, but I don't know how to fix it. Terminal used to talk directly to the kernel, but now it is acting like a ssh or ftp server. Before it used to look like this:

[HTML]torleif@ubuntu-desktop: [/HTML]

Now it looks like:

[HTML]
torleif@#torleif-desktop
127:~$ 
[/HTML]

What software do I uninstall to remove it?

---

### Post by pippy on 2007-04-06
OK I fixed the problem =D

System > Networking > General

Remove the # in the name. This is an invalid character. I don't know how it got there, must just be a bug.

you will have to reset after doing so.

---

