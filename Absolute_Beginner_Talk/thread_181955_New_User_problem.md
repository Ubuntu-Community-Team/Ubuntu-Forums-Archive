---
title: "New User problem"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Tom Thomas on 2006-05-25
i have 128 MB DDR Ram.
My screen resolution is set to default 640 x 840. But my friend with 256 MB, ubuntu looks like having 1024 x 1280. How to change in my pc.

how to install codecs to play my mp3 and avi video.
how to run C programming
Tips to utilize my 128 MB Ram with good speed. 

I want Malayalam fonts and entire OS to be in that language. Is that possible and how ?

My modem Conexant SoftK56 PCI modem does not get detected.
How to play data CDs.

---

### Post by Sef on 2006-05-25
> how to install codecs to play my mp3 and avi video.

Go to [RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats").

> Tips to utilize my 128 MB Ram with good speed.

Get more ram.  512 is good.  Gnome runs much better on it.

---

### Post by hotbrainz on 2006-05-25
Did you try changing the resolution. Well it is :

System --> Preferences ---> Screen resolution.

I dont think there is an Ubuntu in Malayalam. Well if you are a Malayali hopefully you can develop one :).

---

### Post by kart3r on 2006-05-25
I can try this if you can't change your screen resolution in gnome:

sudo dpkg-reconfigure xserver-xorg here you can configure your screen resolution, just follow the steps. Hope it helps you

---

### Post by ProjectGod on 2006-05-25
you can get codecs buuttt xmms media player rocks... its got a cool winamp look to it and plays mp3s! :) 

get it via synaptic or via the terminal.

sudo apt-get install xmms.

about changing the screen resolution. no guarantee this will work but you can edit the /etc/X11/xorg.conf

holler back if you want more information on how to do this.

utilising your 128 ram... if your running low on money. download xfce window manager! :) after installation. reboot and you can choose the window manager xfce at login screen.

---

### Post by Sef on 2006-05-25
> I dont think there is an Ubuntu in Malayalam.

That is incorrect.

To get your computer to run Malayalam.  

First System > Administration > Language Support  > Select Malayalam > Apply > set as default language, if so desired > ok

Second System > Preferences > Keyboard > Layouts > select Malayalam > close

Third System > Preferences > SCIM Input Method Set up> Front End   > Global Setup > Turn on > push keys or keys for language > ok

---

### Post by hotbrainz on 2006-05-25
Sorry Tony and thanks Sef. My Apologies..

---

