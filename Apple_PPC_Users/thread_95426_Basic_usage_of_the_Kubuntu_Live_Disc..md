---
title: "Basic usage of the Kubuntu Live Disc."
date: 2005-11-26
forum: Apple PPC Users
---

### Post by rhubarb&amp;custard441 on 2005-11-26
Hi everyone, I've recently downloaded the Kubuntu 5.10 Live CD for PPC and would really appreciate your help.

After booting from the CD on my iMac G3 and watching the Kubuntu logo appear along with various items, I am presented with a command prompt (#ubuntu@ubuntu: , or something simular). I am unsure what to type here, but would like to load a GUI.

Can anybody advise what to do? Do I have to type the path of the KDE binary or simply ask it to continue somehow?

---

### Post by Ptero-4 on 2005-11-26
The livecd loads the GUI by default. You probably have either a bad burned cd or a very odd videocard that kubuntu can't handle. Can you tell us which exact iMac you got (early iMac G3's come with crappy ati rage cards later iMac G3's come with radeons).

---

### Post by rhubarb&amp;custard441 on 2005-11-27
According to the system profiler in OS X, I have a 'ATY,Rage128Pro' from ATI, on a 450Mhz CPU. Does that mean I can't run any variations of Ubuntu variations on this machine or is there a way to get around this?

---

### Post by linear on 2005-11-27
[QUOTE=Scott Bodrell]According to the system profiler in OS X, I have a 'ATY,Rage128Pro' from ATI, on a 450Mhz CPU. Does that mean I can't run any variations of Ubuntu variations on this machine or is there a way to get around this?[/QUOTE]

There are a number of postings in the Ubuntu Macintosh/Apple/PPC forum on iMac G3 problems. Since you end up at a command prompt, you could try editing /etc/X11/xorg.conf (sketchy instructions here: [http://ubuntuforums.org/showpost.php?p=525584&postcount=3]("http://ubuntuforums.org/showpost.php?p=525584&postcount=3"), but don't try to restart Gnome!). If it works, "startx" should get KDE going.

---

### Post by rhubarb&amp;custard441 on 2005-11-28
Thanks, but what am I suppost to write in this file?

---

### Post by linear on 2005-11-28
Check if settings make sense for your iMac. Generally, horizontal and vertical refresh rates are wrong.

Try "60-60" for horizontal and "75-117" for vertical.

---

### Post by rhubarb&amp;custard441 on 2005-11-28
Thank you so much. Just so anybody else who has a simular problem...
I'm running an Sage Apple iMac G3 450MHz with an ATI Rage 128 Pro. I simply did what this guy said by editing that file and it worked, hope that helps.

---

