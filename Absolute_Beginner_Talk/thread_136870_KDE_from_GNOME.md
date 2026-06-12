---
title: "KDE from GNOME"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by darkbullet87 on 2006-02-26
I remember seeing a thread in here a while back that showed how to install KDE desktop on an Ubuntu box running GNOME....but I can't seem to find it. Does anyone know where it went to or how to do this? 

Thanks in advance :)

---

### Post by Sutekh on 2006-02-26
```
sudo apt-get install kubuntu-desktop
```
Then you can choose which one to use at the login screen, by clicking **Sessions**

---

### Post by darkbullet87 on 2006-02-26
Excellent...thanks a lot :)

---

### Post by Sutekh on 2006-02-26
No problems.

Also if you should ever want to remove GNOME/KDE you will need to do more than removing the ubuntu-desktop/kubuntu-desktop.  They are just meta-packages that gather all the packages you need.

These links will show you how to remove ubuntu/kubuntu

[Ubuntu Forums - Howto fully uninstall the ubuntu-desktop meta-package - by ]("http://www.ubuntuforums.org/showthread.php?t=96046")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

[Ubuntu Forums - Howto fully uninstall the kubuntu-desktop meta-package - by ]("http://www.ubuntuforums.org/showthread.php?t=96048")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

---

### Post by Kurt` on 2006-02-26
What about changing the display manager? (kdm vs gdm)

I have GNOME installed on Kubuntu (breezy), but when I boot into it, I notice that it's running off of KDM.

Is there an easy way to change which display manager is run on boot? I just installed XGL on GNOME and would be interested in staying on GNOME until I have XGL working in KDE. ;)

---

### Post by Xian on 2006-02-26
[QUOTE=Kurt`]Is there an easy way to change which display manager is run on boot?[/QUOTE]

From a terminal:

$ sudo dpkg-reconfigure kdm

---

### Post by aysiu on 2006-02-26
You can also ```
sudo nano /etc/X11/default-display-manager
``` and change it from ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
``` or vice versa.

---

### Post by Sutekh on 2006-02-26
Is there any difference between GDM and KDM?  What does the display manager handle?

---

### Post by drachir on 2006-02-26
I just installed KDE and X as well. I found a great guide for everything you can do with ubuntu.
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by Xian on 2006-02-26
[QUOTE=Sutekh]Is there any difference between GDM and KDM?  What does the display manager handle?[/QUOTE]

They both serve the same purpose, but on a visual level each compliments the respective desktop that they were built for. You could switch from one to the other and obtain the same basic functionality.

---

### Post by aysiu on 2006-02-26
[QUOTE=Sutekh]Is there any difference between GDM and KDM?  What does the display manager handle?[/QUOTE] I know at the very least they handle the login screens, but if you use GDM, you can't shut down from KDE, and if you use KDM, you can't shut down from Gnome.

---

### Post by Sutekh on 2006-02-26
[QUOTE=Xian]They both serve the same purpose, but on a visual level each compliments the respective desktop that they were built for. You could switch from one to the other and obtain the same basic functionality.[/QUOTE]
Ok thats kinda what I thought, cheers!

[QUOTE=aysiu]I know at the very least they handle the login screens, but if you use GDM, you can't shut down from KDE, and if you use KDM, you can't shut down from Gnome.[/QUOTE]Really?  What does that mean?  Do you have to log out first, then use the display manager to shut down?

---

### Post by Xian on 2006-02-26
[QUOTE=Sutekh]Really?  What does that mean?  Do you have to log out first, then use the display manager to shut down?[/QUOTE]

Yep, that's it exactly. With my uptime on Linux I don't notice. :)

---

### Post by aysiu on 2006-02-26
[QUOTE=Sutekh]
Really?  What does that mean?  Do you have to log out first, then use the display manager to shut down?[/QUOTE] Yes. 

So if you use Gnome most of the time, you should use GDM. You can still dip into KDE from time to time, but you'll have to log out of KDE in order to shut down.

So if you use KDE most of the time, you should use KDM. You can still dip into Gnome from time to time, but you'll have to log out of Gnome in order to shut down.

**Edit**: Xian is right--if you never shut down your computer, it's a non-issue.

---

### Post by Sutekh on 2006-02-26
[QUOTE=Xian]Yep, that's it exactly. With my uptime on Linux I don't notice. [/QUOTE]
[QUOTE=aysiu]
**Edit**: Xian is right--if you never shut down your computer, it's a non-issue.[/QUOTE]
I always feel bad about leaving my PC on all the time, especially since it's most probably not doing anything useful.  I hardly switch between GNOME and KDE these days anyway.

Thanks for the info though.

---

### Post by BriGy86 on 2006-02-27
(new member here, hi)

I've had a question for some time and it probably fits best in this thread.

I myself like the KDE desktop over Gnome.  I recently noticed that they now have Kubuntu (so natuarlly I'm thinking about installing that over Ubuntu)

Here are the options i see

A: install Kubuntu
B: install Ubuntu and then put on the KDE desktop

Is there any difference?  What it looks like to me is that Kubuntu just has KDE in it by default.  Am i right?

---

### Post by Sutekh on 2006-02-27
Have a read of this [Ubuntu Forums - How to run KDE desktop? - Post #4]("http://ubuntuforums.org/showpost.php?p=771433&postcount=4")

Yes Kubuntu uses KDE (Ubuntu uses GNOME), but includes extra options to make it *Kubuntu*.  


So those options you listed are available with one more (slightly different)

 C: Install Ubuntu and then put on the Kubuntu desktop

Have you already downloaded the Ubuntu (GNOME) CD?

---

### Post by BriGy86 on 2006-02-28
i have downloaded Kubuntu and have the latest Ubuntu CD that was mailed to a friend of mine (he gave me a copy)

you're saying i should install Ubuntu and then install the Kubuntu desktop?
(that option would be best?)

and also what's an easy way to find this thread again, instead of having to search for it everytime

---

### Post by theturner on 2006-02-28
If you have the Kubuntu CD-ROM, you can configure it as a package source in Synaptic in your Ubuntu installation and then install kubuntu-desktop. So you don't have to do a complete reinstallation and don't have to download anything again (except updates, maybe).
If you have no Ubuntu installed right now, just install from the Kubuntu CD. It will give the same result, but is less complicated.
You can subscribe to a thread. See "Thread Tools" at the top of this page.

---

### Post by BriGy86 on 2006-02-28
i don't have any of them installed right now

thats pretty much what i was wondering

installing right from the Kubuntu CD i guess will give me the same exact result as putting on ubuntu first and then putting KDE on it (with less hassle)

thanks for the answers

---

### Post by theturner on 2006-02-28
[QUOTE=BriGy86]installing right from the Kubuntu CD i guess will give me the same exact result as putting on ubuntu first and then putting KDE on it (with less hassle)[/QUOTE]
Correct. You're welcome.

---

### Post by Klaidas on 2006-02-28
How about icons of KDE applications appearing in GNOME and GNOME apps appearing in KDE?
I heard that could happen. Is there like a script to prevent this?

---

### Post by Klaidas on 2006-02-28
Nevermind, found it here: [http://www.ubuntuforums.org/showthread.php?t=123983&highlight=kde+gnome+icons](http://www.ubuntuforums.org/showthread.php?t=123983&highlight=kde+gnome+icons)

---

### Post by BriGy86 on 2006-03-01
how about the quick search deal?

is there a link i can click that will bring up all hte thread's i've posted in?

---

### Post by aysiu on 2006-03-01
[QUOTE=BriGy86]how about the quick search deal?

is there a link i can click that will bring up all hte thread's i've posted in?[/QUOTE] Click **Search** and **Find all your posts**

---

### Post by BriGy86 on 2006-03-02
just what i needed, thanks

---

