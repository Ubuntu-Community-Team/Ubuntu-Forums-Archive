---
title: "CUPS... Can I fix it?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by John CCC on 2007-07-06
Hi... 
I've been trying to get my Lexmark X1270 running. I was following [this thread]("http://ubuntuforums.org/showthread.php?p=2975693#post2975693") to do it.  It seems like it's possible but, I ran into problems.  After installing KDE too, and using it to get these drivers installed, when I tried to set up the printer, I got the message: 
> The CUPS server could not be contacted.
I researched it, but am having a really hard time figuring out what to do.  Some people were saying that they tracked this problem down to a conflict with systems that are IPV4 and IPV6 compatible.  Although, I now know what those terms mean, I have next to no idea how to go about fixing such an issue.  Or, more importantly, confirming if that really is the issue.  
I wanted to just reinstall CUPS, but when I chose it in the Synaptic Package Manager, the systems that it said it needed to uninstall along with it included "Gnome Desktop" and "Kubuntu Desktop".  I wasn't sure if it meant that those would be completely uninstalled or just changed.  I didn't want to take a chance.  
So... bottom line, CUPS... Can I fix it?    :D

---

### Post by mikeyphi on 2007-07-07
CUPS probably OK!
You normally interact with the CUPS server during the add Printer diaolog, but assuming you have a direct connection you should be able to just go through the add printer system and point to the appropriate PPD file.
Have a look at this website: [http://facorread.150m.com/lexmark.html](http://facorread.150m.com/lexmark.html)

---

### Post by John CCC on 2007-07-07
Thanks for the reply.  I checked out that link.  I'm pretty sure that those are the drivers that I downloaded when I followed the thread I linked to in my first post.  However, I think that something happened that messed up CUPS.  My understanding is that you need CUPS to add a printer.  When I go to System>Administration>Printers, that is when I get the error message.  What is another way to add a printer?

---

### Post by John CCC on 2007-07-07
Ok... I got CUPS to run with this simple command: 
> sudo /etc/init.d/cupsys start
The printer still isn't working but, at least I know why cups wasn't listening... it wasn't running.  Well at least that's worked out.. Now, If I can just locate the ppd and point CUPS to it, I should be good to go

---

### Post by sailor2001 on 2007-07-07
system/administration/network tools is where you can select ipv4 or 6

---

