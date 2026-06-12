---
title: "side buttons on Mouse not work."
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-11-12
My Logitech mx518 Mouse worked pretty fine the first time I installed Ubuntu.  The mechanical switching between the 3 DPI speed settings worked without any extra help.  But the 2 side buttons does not respond, especially when surfing on Firefox and you want to flip Forwards and Backwards just by clicking your Mouse side buttons.

I went to Preferences=>Mouse settings but it didn't have anything were you could assign new buttons and function.
How can I solve this?

---

### Post by klytu on 2006-11-12
> **jingo811 said:**
> My Logitech mx518 Mouse worked pretty fine the first time I installed Ubuntu.  The mechanical switching between the 3 DPI speed settings worked without any extra help.  But the 2 side buttons does not respond, especially when surfing on Firefox and you want to flip Forwards and Backwards just by clicking your Mouse side buttons.

I went to Preferences=>Mouse settings but it didn't have anything were you could assign new buttons and function.
How can I solve this?

Try following the steps [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#Activate_side-mouse-buttons_in_FireFox"). That should correct your issues with Firefox. To enable functionality of most of your mouse buttons in Nautilus you can try installing [IMWheel]("http://ubuntuguide.org/wiki/Ubuntu_dapper#Install_.26_Configure_IMWheel").   I noticed you are using Breezy and I realize the steps above are for Dapper, but I think the procedures will still work for you.

---

### Post by jingo811 on 2006-11-12
tnx! also I changed my profile to 6.06 i just installed yesterday.
When installing IMwheel i get this
> mike@mike-shark:~$ **sudo apt-get install imwheel**
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imwheel
mike@mike-shark:~$

Will that last warning line be a problem in the future?
...Also I can't add any command lines in the imwheel file/folder since it doesn't seem to exist.
Know what the problem can be?

---

### Post by klytu on 2006-11-12
> **jingo811 said:**
> tnx! also I changed my profile to 6.06 i just installed yesterday.
When installing IMwheel i get this

Will that last warning line be a problem in the future?
...Also I can't add any command lines in the imwheel file/folder since it doesn't seem to exist.
Know what the problem can be?

This:

> mike@mike-shark:~$ sudo apt-get install imwheel
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imwheel
mike@mike-shark:~$

means apt couldn't find the imwheel package, so it wasn't installed. That's why the imwheel file/folder doesn't exist. It could be that you need to update your /etc/apt/sources.list, a file which contains the list of repositories apt searches to download and install packages. Follow the instructions [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories"). Then try:

```
sudo apt-get install imwheel
```

again.

---

### Post by jingo811 on 2006-11-12
Tnx klytu that did the trick for Nautilus.  However there's one more program I want the side buttons to work on namely the Eye of GNOME 2.14.3.

In Windows XP when viewing galleries of pictures you can move Forwards and Backwards with the side buttons, how can I do that in Eya of GNOME?

---

### Post by klytu on 2006-11-13
> **jingo811 said:**
> Tnx klytu that did the trick for Nautilus.  However there's one more program I want the side buttons to work on namely the Eye of GNOME 2.14.3.

In Windows XP when viewing galleries of pictures you can move Forwards and Backwards with the side buttons, how can I do that in Eya of GNOME?

I don't know if you can. How Eye of Gnome responds to different mouse button events is determined by the way its developers coded it. In the latest version, [2.17.1]("http://lwn.net/Articles/205329/"), this functionality was supposedly added, but I haven't tried that version yet.

---

### Post by jingo811 on 2006-11-13
Do you know when Eye of GNOME upgrade option will be available in the Synaptic Manager?  I went there but it was untickable.  Then I tried to download it from that link but got a butt load of error messages when following the install instructions.  Something about no acceptable C compiler found in $path....so I'm hoping I won't have to deal with this complicated compiler stuff.
And just click it in Synaptic.

---

