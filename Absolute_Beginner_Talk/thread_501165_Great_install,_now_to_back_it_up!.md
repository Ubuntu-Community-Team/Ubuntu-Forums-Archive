---
title: "Great install, now to back it up!"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by pbesing on 2007-07-14
Ok, now I've got Ubuntu going, even with wireless atheros chipsets!  Thanks to all for the help.   I'm sure this question has been asked, but I couldn't find a direct answer to this, so my apologies.  Is the system I have now an updated Kernel, or is it the same kernel, just software installed, etc?  

Can I back up my install, so that I can restore this configuration now in case I screw something up while tweaking things (highly likely in my case, cause I'm always trying to make it better)

Thanks!  What a great o/s and a great community..wish I'd found this earlier than now.

Paul

---

### Post by ramjet_1953 on 2007-07-14
There are a few ways to do this, depending upon how much you want to back -up

1. Probably the easiest way is just to make a copy of your /home directory, either to a separate partition, or to DVD.

2. Use [COLOR="Blue"]aptoncd[/COLOR] which you can install from the repositories.
In a terminal copy and paste this: [COLOR="Red"]sudo apt-get install aptoncd[/COLOR]
Here's a link for information: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

3. for the ultimate backup, use something like Ghost for Linux (G4L) to clone your HDD.
Here's a link for the iso download : [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

4. If you are comfortable with the command line the [COLOR="Blue"]dd[/COLOR] command will also do it for you. (in a terminal type [COLOR="Blue"]man dd[/COLOR] for directions on how to use)

Regards,
Roger :cool:

---

### Post by Nekiruhs on 2007-07-14
I recommend PartImage.

---

### Post by bodhi.zazen on 2007-07-14
+1 partimage

Here is a thread that covers most of your options :

[http://ubuntuforums.org/showthread.php?t=500621](http://ubuntuforums.org/showthread.php?t=500621)

If you have the RAM I suggest tweaking on VirtualBox or VMWare.

If you have the Hard Drive space, I then suggest tweaking on a test partition.

---

