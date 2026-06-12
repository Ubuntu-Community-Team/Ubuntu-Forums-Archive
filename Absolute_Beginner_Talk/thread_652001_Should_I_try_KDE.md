---
title: "Should I try KDE?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by alx010 on 2007-12-28
I have Ubuntu Studo installed on an older Compaq running a Celeron 1.3ghz processor, with 512MB of RAM. The one thing that's killing me is Gnome/Nautilus using a lot of CPU. With the desktop idle, Gnome-system  shows 10 to 20% cpu usage. When I begin browsing folders it can spike to 60 to 80%. I don't have Compiz installed, & have no desktop effects enabled.

I'm used to running XP on this machine, without any problems like this. XP usually idles at 0 to 5% CPU usage.

I think maybe I'm ready to try the KDE environment , to see if that helps. Any tips, advice on making the switch? 

BTW, if it's relevant, my graphics card is an Nvidia 6200, with 128MB RAM.

Thanks

---

### Post by LinuxIsInnovation on 2007-12-28
You can try KDE.. In Gnome, max CPU is used up by the gnome-panel
You can switch to AWN (Avant Window Navigator) and remove the panels to lessen CPU usage. If you want to remove all panels, I would tell you how to. :)

---

### Post by meindian523 on 2007-12-28
In general,it's said KDE is more bloated than Gnome,so instead you might want to check out whether you installed something (as a plugin for Gnome/Nautilus maybe) which might warrant that much CPU usage.....maybe try checking for rootkits?

---

### Post by atomkarinca on 2007-12-28
If you're only having problems with Nautilus then you can try using [Thunar]("http://ubuntuforums.org/showthread.php?p=1760300") instead. Just as an advice, you don't have to switch to KDE completely, you can install it and switch between Gnome and KDE as you'd like.

---

### Post by meindian523 on 2007-12-28
> **sayakb said:**
> You can try KDE.. In Gnome, max CPU is used up by the gnome-panel
You can switch to AWN (Avant Window Navigator) and remove the panels to lessen CPU usage. If you want to remove all panels, I would tell you how to. :)

Um,wouldn't AWN be heavier since it would require a compositing manager like C-F/Beryl which are known to be resource-heavy?

---

### Post by Hallvor on 2007-12-28
> **alx010 said:**
> I have Ubuntu Studoi installed on an older Compaq running a Celeron 1.3ghz processor, with 512MB or RAM. The one thing that's killing me is Gnome/Nautilus using a lot of CPU. With the desktop idle, Gnome-system  shows 10 to 20% cpu usage. When I begin browsing folders it can spike to 60 to 80%. I don't have Compiz installed, & have no desktop effects enabled.

I'm used to running XP on this machine, without any problems like this. XP usually idles at 0 to 5% CPU usage.

I think maybe I'm ready to try the KDE environment , to see if that helps. Any tips, advice on making the switch? 

BTW, if it's relevant, my graphics card is an Nvidia 6200, with 128MB RAM.

Thanks

Why not try Xubuntu? It feels lighter than both Gnome and KDE.

---

### Post by LinuxIsInnovation on 2007-12-28
> **meindian523 said:**
> Um,wouldn't AWN be heavier since it would require a compositing manager like C-F/Beryl which are known to be resource-heavy?

Ah well, it is as a matter of fact.
This is my personal experience. I had the 2 default panels + a couple of screenlets that kept my CPU up at 8%
I have removed the panels and use AWN.. It came down to 2%

But yes, for his case, he might need more CPU to incorporate the composition managers.. :|

---

### Post by LinuxIsInnovation on 2007-12-28
Btw, I said AWN because he has an additional GPU..

---

### Post by alx010 on 2007-12-28
Thanks for the quick responses. As far as panels, I'm using just the bottom panel, with autohide enabled, no transparency. (tried switching autohide off with no effect) I've added nothing to the panel except a couple of launchers. 

As far as removing panels,I like to have a 'clean' desktop, (no or very few icons).

Any further advice on how I go about checking for rootkits?

---

### Post by The Cog on 2007-12-28
Could it be the sound file preview feature? In nautilus, choose Edit->Preferences, Previews and disable sound file previews and see if that makes a difference. I gather from other posts here that there may be a bug in the sound preview in Gutsy anyway, that generates "This directory could not be read" os something like that.

---

### Post by LinuxIsInnovation on 2007-12-28
Btw, transparency doesnt use up CPU, the panel applets do.. :)

---

### Post by meindian523 on 2007-12-28
Well,I use AWN too but I don't exactly trust the CPU usage the applet shows.....feels too low....

about the rootkits,use Synaptic,search for chkrootkit

---

### Post by meindian523 on 2007-12-28
though this is a Disclaimer worth mentioning:

"Please note that this is not a definitive test, it does not ensure that the
target has not been cracked. In addition to running chkrootkit, one should
perform more specific tests."

---

### Post by philinux on 2007-12-28
Have you used 

top

from the terminal to see whats eating cpu or did you use system monitor

---

### Post by alx010 on 2007-12-28
Actually have used system monitor, & top, with the same results, both show Gnome-system leading the pack in cpu usage.
 
Will try some of the sugesstions made so far, but have a busy morning ahaed, again, thanks for the quick answers!:-)

---

### Post by philinux on 2007-12-28
My old croc idles at about 9% it does spike right up when firefox starts etc.

---

### Post by alx010 on 2007-12-30
Thanks again to all who offered advice :) After doing some more searching, & learning, I followed the steps in this article;

[http://www.pcworld.com/printable/article/id,132030/printable.html]("http://www.pcworld.com/printable/article/id,132030/printable.html")

and installed the xubuntu-desktop.  I've  been using it for less than an hour, but so far I'm loving it! :)

So far, my computer seems more responsive, and I can now right click images & open them with Photofiltre, which I had installed a few days ago using wine. (using Gnome-Nautilus, Photofiltre would open, but I would get an error saying that it was unable to open the image)

I also found it very easy to change themes, colors etc, and found settings for  whether or not to display window content while dragging etc, which was a tweak I used in Windows to cut cpu usage.

Another thing I like is the option to right click the desktop to show the full menu :) 

Again, thanks to all!

---

### Post by meindian523 on 2007-12-30
If your issue is now resolved,please mark the thread solved.

---

