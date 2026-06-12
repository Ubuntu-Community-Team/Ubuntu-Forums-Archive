---
title: "Defrag  and Registry Cleaner for Linux"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Tobster on 2006-09-17
Do you have to defrag your computer like you would a Windows system? 

Is there a Registry Cleaner for Linux

---

### Post by kidders on 2006-09-17
Linux doesn't have a registry.

Also, most of its filesystems are incredibly resistant to fragmentation ... at least by comparison to Microsoft's ones!

---

### Post by xpod on 2006-09-17
WHAT registry:D 
No need for none of THAT nonsense over here.
Your Ubu will do a check every 30 boots to make sure it`s house is in order.

---

### Post by Indras on 2006-09-17
For the record: most modern operating systems really don't need to defrag.  Even Windows XP does a pretty good job of keeping files on the hard drive contiguous.  Naturally, companies that make defragmentation programs will tell you otherwise, but really, the performance boost from defragmenting your drive is actually minute compared to the amount of time it takes to actually defrag your drive.

However, the Linux kernel has always been superior at keeping files in order... you don't need to worry about a defragmenter here.

The closest thing to registry is the gnome configuration file.  Hit Alt-F2 and type in 'gconf-editor' and hit enter to see it.  Since it is such a small file used only for configuring gnome and gnome applications, there's no reason why you'd need a cleaner for it.

---

### Post by bodhi.zazen on 2006-09-17
> **Tobster said:**
> Do you have to defrag your computer like you would a Windows system? 

Is there a Registry Cleaner for Linux

[color=blue]Welcome to Linux. It's a whole new world.[/color]

> **Indras said:**
> For the record: most modern operating systems really don't need to defrag.  Even Windows XP does a pretty good job of keeping files on the hard drive contiguous.

Err... what windows XP have you been runnig?

Define "pretty good". Fragmentation in Windows remains problematic although I do not think you need a comercial defragmenter...

---

### Post by brucevangeorge on 2006-09-18
> **Indras said:**
> For the record: most modern operating systems really don't need to defrag.  Even Windows XP does a pretty good job of keeping files on the hard drive contiguous.

What have you been smoking?

I have been using XP for years and it does a TERRIBLE job. I have to defrag at least every two weeks otherwise it starts lagging.

But you're right about those "professional" defragging tools. They're not useful unless you got terabytes lying around. Only then will you see a noticeable difference.

---

### Post by bulldog on 2006-09-18
> **Indras said:**
> For the record: most modern operating systems really don't need to defrag.  Even Windows XP does a pretty good job of keeping files on the hard drive contiguous.  Naturally, companies that make defragmentation programs will tell you otherwise, but really, the performance boost from defragmenting your drive is actually minute compared to the amount of time it takes to actually defrag your drive.


Boot XP 5 times and take a look.

Or my XP is mixed up, but after playing a game, what should be blue was alarming red

---

### Post by bruce89 on 2006-09-18
> **Tobster said:**
> Do you have to defrag your computer like you would a Windows system? 

No, [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Fedz on 2006-09-18
I'm pleased you asked as I've been wondering this very question for weeks :)

I found *gconf-editor* what Indras pointed out above but, does Ubuntu (like Window$) have a registry file for each and every file on your HD and if you delete this file does the registry still reference it?

eg: on Window$ if you delete a file then do a registry search you can still find the file name and extension until you do a reg. clean - is it same on Ubuntu?

Tia

---

### Post by bruce89 on 2006-09-18
> **Fedz said:**
> I'm pleased you asked as I've been wondering this very question for weeks :)

I found *gconf-editor* what Indras pointed out above but, does Ubuntu (like Window$) have a registry file for each and every file on your HD and if you delete this file does the registry still reference it?

eg: on Window$ if you delete a file then do a registry search you can still find the file name and extension until you do a reg. clean - is it same on Ubuntu?

Tia

gconf is only GNOME-only configuration settings, such as program preferences and suchlike.  It is more akin to mozilla's about:config than the binary-easily-corruptable windows registry.

I suppose the nearest thing to a registry in Linux are the files in /etc.

---

### Post by Fedz on 2006-09-18
Yeah! true. I noticed this from having a good look around when I put Ubuntu on but, wasn't altogether sure.

So Ubuntu actually only uses what it knows is their from direct access to the files as opposed to Window$ it has the files but only access these through it's knowledge of it's registry.

Like you say this is why it (Window$) corrupts as it relies upon it's registry for reference as Ubuntu filesystem relies upon it's actual files been their.

I think that's the basic anyway ;)

---

### Post by Atomic Dog on 2006-09-18
> **bodhi.zazen said:**
> [color=blue]Welcome to Linux. It's a whole new world.[/color]



Err... what windows XP have you been runnig?

Define "pretty good". Fragmentation in Windows remains problematic although I do not think you need a comercial defragmenter...

Oh come now.  He must be running OSxp because XP fragments more than a glass window with a brick through it.

---

### Post by fragos on 2006-09-18
There is thankfully no registry for malware to hide in Linux.  The configuration bits are handled by application and frequently saved saved in *.conf files.  One of the most significant ones is /etc/X11/xorg.conf.  It's probably a good one to look at to see what a .conf file is like.  Some applications save their configs in .xml files.  For the most part if you stick with the GUI for configuration changes you'll not need to edit .conf files directly.

---

### Post by Mapleman on 2006-10-12
I am just curious as to why there is a "Defragmentation" Package available if that is not something Linux needs to re-organize it's files. I only ask because I too am used to the brute force operating of the O/S that windows forces upon you like defrag and scandisk etc and other rituals to maintain somewhat functionality. Anyone know a way to manually tweak the 30 boot check process? I think I have gone package happy and finding it a bit crowded eh

 Thank you kindly

---

### Post by fragos on 2006-10-12
In the open source commmunity where money isn't king, developers will work on software that someone wants and not only on that wich all may buy.  I didn't know such software was available in Linux.  It might be used in a mixed Microsoft Linux environment where Windows can't utilize the superior Linux disk formats.

---

### Post by bodhi.zazen on 2006-10-12
> **Mapleman said:**
> I am just curious as to why there is a "Defragmentation" Package available if that is not something Linux needs to re-organize it's files. I only ask because I too am used to the brute force operating of the O/S that windows forces upon you like defrag and scandisk etc and other rituals to maintain somewhat functionality. Anyone know a way to manually tweak the 30 boot check process? I think I have gone package happy and finding it a bit crowded eh

 Thank you kindly

For boot options [[color=darkred]See here[/color]](http://ubuntuforums.org/showpost.php?p=1348702&postcount=38)

[[color=darkblue]Linux Defragmentation[/color]](http://www.linuxquestions.org/questions/showthread.php?t=55710)

---

### Post by Mapleman on 2006-10-12
I appreciate the reply and the link, will see if that helps

Thank you :D

---

