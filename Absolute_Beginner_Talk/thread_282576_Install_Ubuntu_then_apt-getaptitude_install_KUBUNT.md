---
title: "Install Ubuntu then apt-get/aptitude install KUBUNTU?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-22
Will there be any difference between installing Ubuntu and then installing KDE instead of installing Kubuntu?
(As in boot loading speed, general computer performance, etc.)

---

### Post by ReaderRat on 2006-10-22
> **Dual Cortex said:**
> Will there be any difference between installing Ubuntu and then installing KDE instead of installing Kubuntu?
(As in boot loading speed, general computer performance, etc.)
Installing the KDE desktop is certainly easier than switching to Kubuntu from Ubuntu,if you just want the KDE features. I believe the code is:
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
You might back up xorg.cong first.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by aysiu on 2006-10-22
There is a difference, but it has nothing to do with loading speed or general computer performance.

The big difference is that if you install Ubuntu and then *kubuntu-desktop* on top of that (please use *aptitude*, not *apt-get*, if you do), you'll have both Ubuntu and Kubuntu installed. You can pick whichever want you want to use at login. You'll also have the default Ubuntu programs installed (Evolution, Firefox, etc.) in addition to the default Kubuntu programs (KMail, Konqueror).

If you install just Kubuntu without Ubuntu, you will have only KDE to choose from and only Kubuntu's default programs.

There are several versions of KDE, by the way. You can install *kdebase*, *kde-core*, *kubuntu-desktop*, or *kde*.

*kde-core*, if you're worried about performance, is probably your best bet. It's the best combination of functionality and speed. > **ReaderRat said:**
> You might back up xorg.cong first.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` Can you explain the reasoning behind backing up xorg.conf? I don't think changing desktop environments affects that file... unless you're also going to install Beryl/Compiz.

---

### Post by ReaderRat on 2006-10-22
[quote=aysiu]Can you explain the reasoning behind backing up xorg.conf? I don't think changing desktop environments affects that file... unless you're also going to install Beryl/Compiz.[/quote]
Newbie here....I back up a lot of stuff. I don't know when I will need to have a backup available.

---

### Post by Dual Cortex on 2006-10-23
ok, thanks!
i had already installed kubuntu before starting this thread. Yes, i did my research and used aptitude. i was just worried about a 1 sec. performance loss :)

---

### Post by aysiu on 2006-10-23
I don't think it's ever a bad idea to back up important system files. I just don't want Dual Cortex to get the impression that xorg.conf gets affected by installing new desktop environments.

---

### Post by randiroo76073 on 2006-10-26
Hmmm, I installed Kubuntu desktop[6.06] using the above commands[cut&paste] to Ubuntu[6.06] and all I got was another entry on my main menu labeled Debian w/list of all apps.  No choice at boot, straight into Ubuntu.  Did I miss something?

---

### Post by Arby on 2006-10-26
randiro: When you get to the login screen do you have an 'options' button at the bottom left (or possibly right)? If you do then you should be able to click that and choose select session. I think that's the command, I'm on Windows box (work) at the moment so I can't check.

You should then have a list of options to choose Gnome or KDE, just choose kde. It will probably ask you if you want to make this your default desktop session. Please yourself on this. 

My laptop does this, I had ubuntu installed and then installed kubuntu-desktop on top. Now when I boot the machine it gets to the ubuntu login screen. I chose to make kde my default session so when I login it actually goes to a kubuntu desktop.

I could probably change this so that the login screen displays kubuntu as well but I don't care enough to bother since I probably look at that screen for all of 30 seconds

---

### Post by randiroo76073 on 2006-10-29
Thanks Arby, that was what I was looking for, just didn't know where it was. :)

---

### Post by NegativeSpace on 2006-10-29
Hi,

If I were to install *kubuntu-desktop* and all the programs associated with it, and later uninstalled it, how could I easily remove all the extra programs it installed? Or is it done automatically?

Cheers

---

### Post by Bachstelze on 2006-10-29
If you installed it with aptitude, yes. Just remove it with aptitude as well :)

---

### Post by Rashid584 on 2006-10-29
To prevent KDE apps from showing up in Gnome menus and vice-versa, do the following before you install kubuntu-desktop :

(you can also create a small cleaner.sh script witht he following and run it as root)
$ sudo -s -H
#cd /usr/share/applications
#for i in *.desktop; do \
# if ! grep -q ^OnlyShowIn= $i; then \
# echo &#8216;OnlyShowIn=GNOME;&#8217; >> $i \
# fi
#done

Now, after installing kubuntu-desktop do:

$cd /usr/share/applications/kde
$sudo -s -H
#for i in *.desktop; do
# if ! grep -q ^OnlyShowIn= $i; then
# echo &#8216;OnlyShowIn=KDE;&#8217; >> $i
# fi
#done

What we did above was to tell the Gnome apps to only show in the gnome menus, and later, the KDE apps to only show in KDE menus. 

[http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/](http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/)

-Rashid

---

### Post by Bhawns on 2006-12-20
Arby that issue that you mention there I am haviny the same problem (Breezy 5.10 64bit) did the aptitude update and install but no KDE in the session list but Debian and all the apps in the application list in ubuntu. What should I do now. to get the Kubuntu desktop?

---

