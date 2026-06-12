---
title: "Ubuntu versus SUSE?"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by loudking on 2006-01-31
I am a newbie to linux, and somebody suggests Ubuntu to me, so I am now using Ubuntu.

The problem is that Ubuntu is just too [COLOR="Red"]SLOW[/COLOR] on my laptop, even slower than Windows (maybe the reason is gnome??)

The hardware configuration of my laptop is:
CPU: Intel Centrino 1.3MHz
Memory: 256 M

Another guy just suggests SUSE to me, so would anybody just give me a comparision between Ubunu and SUSE? Will SUSE run faster on my laptop than Ubuntu?

Thanks

---

### Post by mcduck on 2006-01-31
No, SUSE is not likely to be faster, as it's the desktop enviroment that's slowing your performance. And Gnome is Gnome and KDE is KDE, whatever distro you are running.

First thing I'd do is turning reduced resources on in gnome:

Open Applications/System Tools/Configuration Editor.
Browse to apps/metacity/general and mark 'reduced_resources'

If that's not enough, you could try XFCE4 instead of gnome: 'sudo apt-get install xubuntu-desktop'

Buying some more memory is also a good idea, buying RAM is never waste of money. It's the one thing that has most effect on basic desktop computing. even upgrading to 512MB would help you a lot.

---

### Post by davmac on 2006-01-31
Once you've installed xubuntu desktop, the next time you log in, choose "Sessions" and "XFCE" or you'll just go straight back into Gnome.

...and I would add, If you install xubuntu-desktop and you still find it too slow, have a look at a minimalist distribution like DamnSmallLinux at [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Hope this helps,

Dave Mac

---

### Post by newuser111 on 2006-01-31
is dma enabled hdparm /dev/hda


or hdparm /dev/sda maybe?

---

### Post by JNowka on 2006-01-31
I don't know about GNOME but I can tell you a way to speed up KDE bootup.

Run Command >> kcontrol >> KDE Components >> KDE Performance

Log into Admin Mode with the button on the bottom.

Switch over to the system tab.

and select the "Disable system configuration startup check" check box.

As it warns you there, there is a danger, basically don't forget to uncheck it any time you make a change to the configuration before you reboot.

---

### Post by Adrian on 2006-01-31
SUSE (KDE version) is much faster than (K)Ubuntu on my 700MHz machine with 384MB RAM. This might not be the case on your machine, but it's worth a try.

---

### Post by cotcot on 2006-01-31
I switched first to Kubuntu then Ubuntu because Suse (9.2) was way too slow (especially yast was slow : yast is in Suse what synaptic is for Ubuntu).   
There was a difference between the 9.1 (home version) and the 9.2 (pro version) of Suse. Suse 9.2 took some 6 minutes to boot; Suse 9.1 "only" 4 minutes on my test PC (see below). I have not checked the actual Suse version (10.0 or 10.1 ?)
Kubuntu need 3 minutes.

---

### Post by riktzvet on 2006-01-31
I dual boot both Suse 10 and Ubuntu 5.10 on a PIII 550 w\512 ram and have the Ubuntu to be a little faster at booting.

---

### Post by Adrian on 2006-01-31
I haven't thought about boot times, because I always hibernate and both of them are fairly quick at resuming.

My problems is that all X-related tasks consume more CPU power in (K)Ubuntu (this has improved a lot with Dapper, but SUSE is still faster for **me**). I have a thread regarding this here:
[http://www.ubuntuforums.org/showthread.php?t=116421](http://www.ubuntuforums.org/showthread.php?t=116421)

Debian vs. Suse gives me the same results.

---

