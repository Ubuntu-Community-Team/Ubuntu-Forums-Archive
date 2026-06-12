---
title: "'Unshield' fails every time."
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Gryfft on 2007-01-25
I'm trying to get my wireless card to work, I have been following the instructions on the Ndiswrapper wiki, have found the appropriate drivers and am now trying to extract the .cab files to get the .sys and .inf files for Ndiswrapper. I extracted one of them with cabextract and am trying to get Unshield to work on the other ones (data1.cab and data2.cab, both of which apparently have Installshield headers.)

When I try to extract them, I get the error message "Aborted (core dumped)"

Am I on the right track, how can I fix this? :(

---

### Post by jackcy on 2007-05-18
same problem here, but I did't find a solution 'til now. I'll let you know.

---

### Post by jackcy on 2007-05-20
Here's an excerpt on [http://forum.abit-usa.com/showthread.php?t=122455](http://forum.abit-usa.com/showthread.php?t=122455)

You will need the Windows (2000/XP) driver files. There is a catch-- you cannot simply unpack the driver files from the cd/download because they're in the new Installshield 12 format, which to my knowledge (correct me if I'm wrong) cannot be extracted with existing tools. If you have the driver installed in Windows, simply search your windows directory for the following 3 files: aw5006.sys, net2425.inf & net2425.cat. You will need these files on a partition that is accessible from your Linux distribution.

[...] Don't know if this is your card, but it is the same extracting issue.

I tried to extract it with cabextract, unshield and orange - no success. Finally I installed the driver in a virtual machine an put the files on a usb stick.

---

### Post by tgbrowning on 2007-05-29
Any chance you could make your copies of those files available?

I just realized something that makes what I'm trying to do a heck of a lot harder. I'm runing Windows Vista on my main machine (which is  why I'm running like hell for Ubuntu) and don't have easy access to an XP machine.  

Browning>>>

---

