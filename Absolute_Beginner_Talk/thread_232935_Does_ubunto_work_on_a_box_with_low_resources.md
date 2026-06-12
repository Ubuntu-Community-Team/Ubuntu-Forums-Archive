---
title: "Does ubunto work on a box with low resources?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by martinmanzana on 2006-08-09
Here is the story:
I like to fool around with computers. I got my own desktop with windows xp and recently I received as gift, an old laptop. Not too old. Its a Toshiba Satellite 2250XCDS. It has a intel celeron 600Mhz, 64Mb of ram, and a 4GB hard drive. I installed windows xp on it. Tried to reduce the resource consumption as much as I could, but it runs very slow still.
The truth is I don't want to go back to any prior windows' version, they are just a headache. I read on a forum a while back that Linux works great on low resources systems. I was wondering up to what point this is true. Will my kinky laptop run linux smoothly? Thats what I am looking for, smooth. I don't want the computer to idle for 5 minutes before I can move the mouse again, if you get what I mean :( .
I have thought of trying out linux before. But never had the time to sit down and get dirty with it. Besides I need my desktop running well, I can't risk having it full of bugs. But since the laptop is an accessory item, I can risk it. It will even be a personal project.
So anyway, is ubuntu right for my low resource laptop?
Thanks

---

### Post by Paerez on 2006-08-09
64m RAM is too little for the normal version of ubuntu (with the Gnome desktop) but Xubuntu is a version of ubuntu designed for low-resource systems. Check it out:
[http://xubuntu.com/](http://xubuntu.com/)

---

### Post by martinmanzana on 2006-08-09
Great!!! Thanks! Seems to be what I am looking for. But is there any cutbacks compared to ubuntu? Or is it just lighter on graphics? Thanks

---

### Post by UltraMathMan on 2006-08-09
Iirc Xubuntu uses the Xfce Windows Enviroment. You can chech out the link Paerez gave or [this one]("http://www.xfce.org/").

-Hope this helps :)

---

### Post by Paerez on 2006-08-09
linux is just the kernel, on top of which applications are run. So ubuntu runs the Gnome gui, Kubuntu runs the KDE gui, and Xubuntu runs the xfce4 gui. So what you get is the same base system, but with a different gui program. They each have their own quirks, but the super-duper-ulta-summarized version is:
Gnome: Friendly and Simple (thats why it's ubuntu's default)
KDE: Pretty and highly customizable (not to say others aren't pretty)
XFCE4: Fast and Versatile

So the eye-candy is less, but you still have the majority of the functionality (firefox, word processor, etc).

I have not personally used xubuntu, so I don't know many details.

---

### Post by tagra123 on 2006-08-09
I have Xubuntu installed on a Dell Laptop with 128MB ram 500mhz processor and it works great. It lacks some of the menus and items installed with Ubuntu but it works great.

After installing I can even get it to run Windows 98 using VMware -- very cool. VMWARE seems better than dual booting.

It found my Belkin wireless network card with no extra effort.

I basically have the default install I went ahead and added OpenOffice - I dont think it automatically installed

I also have  Firefox  installed too, If I remember correctly you can apt-get most of the same things you would install on Ubuntu.

Believe it or not, this old laptop is performing better than it ever did using Windows.

---

### Post by dusu on 2006-08-09
I think the usual xubuntu desktop install requires 128MB... so this will be a problem. Maybe you can give a try with the alternate install CD ? Anyone tried this ?

Personally, I would suggest you to install a server version, and then put some very-low memory/cpu consuming graphical environment on top, such as blackbox.

---

### Post by Paerez on 2006-08-09
Thanks for pointing that out dusu. Here are some links to blackbox and other lightweight window managers:

[Blackbox]("http://blackboxwm.sourceforge.net/")
[Fluxbox]("http://fluxbox.sourceforge.net/")
[Icewm]("http://www.icewm.org/")

The server install is a good idea, but it may be a bit over his head. We can help you, though!

---

### Post by daou on 2006-08-09
I installed Xubuntu on an old IBM laptop (200MHz, 128MB). It couldn't run the live cd (loaded forever) but I was able to install it with the alternate cd. Runs fine, with some resource saving tweaks. But I'm guessing 64MB RAM is not enough to run even Xubuntu well. You can still give it a shot with the alternate-install cd, but I would go with dusu's recommendation of installing the server version with something lighter that XFCE.

---

### Post by avtolle on 2006-08-09
[http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntulite](http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntulite) may be another approach for you to consider. This is called ubuntulite; I don't use it, but I keep track of it because of an old, minimal resource computer I am about to get (long story), and want to "keep it going". HTH.

---

### Post by WADemosthenes on 2006-08-09
It would run fine, just not fast.  I would look at Damn Small and Vector Linux, which use even less.  From my experience, xubutnu is WAY easier though, so if your new just try it for a while.  Too slow, try Vector, still too slow... Damn Small Linux is as small and fast as you can get (hence Damn Small).

---

### Post by avtolle on 2006-08-09
Concur w/WADemosthenes. DSL is as the name suggests, and runs well on a 32mb RAM machine, believe it or not.

---

