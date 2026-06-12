---
title: "Frustrations rule"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by anoldsalt on 2007-08-28
Hello world,
I am in need of some serious TLC after doing my best to try my hand at Linux/Ubuntu and being frustrated at every turn.  In a nutshell, i am trying to retool my career and I am taking classes in Oracle.   I have a PC dedicated to use as a sandbox for the courses.  I have installed Ubuntu 7.04 without a hitch and it is sharing the machine with Vista, but on its own dedicated drive with dual boot.  I have installed Oracle 10gXE.  My frustration comes from the following areas:

I am having trouble getting an Oracle java app to open in Firefox.  I get a message that: "Firefox can't establish a connection to the server at 127.0.0.1:8080."  Okay - no biggee says I - just do a little research over on the Oracle house and find the answer.  Everyone over there thinks the problem is within the etc\hosts file.  So - I will follow their advice and try to change things.

Probs:
If I try to edit the \etc\hosts file using gedit it comes back and barks at me that it cannot save the file because I don't have permission.  Okay - $ sudo gedit etc\hosts, problem solved.  Except why should I have to pretend I am root to edit a lousy hosts file?  And after the changes I still have not solved my Oracle issue.  Forum advice over there now tells me to see if the "listener" is active with LSTNRCTL STATUS.  That result = sh: lstnrctl: not found.  Ok - is it not found because Linux does not know where to look or is not installed?  I cannot find a 'path' equivalent in Linux and Nautilus simply loops forever without finding the file.  I cannot locate LSTNRCTL in the standard Linux commands, so I have assumed it is an Oracle command.  Nowhere is it to be found in the Oracle dirs, so now what?   

Wait - I am still a nube, it gets better.  I do the obligatory reading, spend $$ on books and still not much better off.  So that brings me to you all.  What can you suggest in the way of things to check?  Anyone in Ubuntu land have Oracle working or know of a good place to find a 'how-to' doc?  And yes - I have read the Oracle/Linux docs and tried my best to follow along, but they were written for RPM and not Deb, so it is not a good match.

Thanks world ...

---

### Post by sumguy231 on 2007-08-28
I don't have any Oracle experience so I can't exactly help you with your problem, but one comment piqued my interest:

> Except why should I have to pretend I am root to edit a lousy hosts file? 
You aren't pretending you're root, you are root. It makes perfect sense to require root permissions for the hosts file, as it wields great power and isn't exactly something you want any old user on a system to be able to edit.

P.S. In the future, if you want to run graphical apps as root use 'gksu' instead of 'sudo'.

---

### Post by freebeer on 2007-08-28
I know nothing of Oracle (except for some of the writings of the Great Oracle :wink:) but that particular port, :8080 is usually a http port.  Maybe the instructions that you're following assume that you are running Apache along with Oracle?  Hopefully it's a hint in the right direction...

---

### Post by bodhi.zazen on 2007-08-29
Yes, learning a new OS is frustrating.

You can look at this link for Oracle : [http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

Also, yes Oracle on Linux is fairly specialized. You *might* consider an alternate version of Linux such as Centos (Centos = Open source Red Hat)

---

