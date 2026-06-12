---
title: "EDGY shutdown issues &amp; mplayer issues"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by QUEEN HIPPOLYTA on 2007-02-26
I recently upgraded to edgy and I love it except for the face I can no longer reboot because it hangs on shutdown and I have to do a manual shutdown of my computer, also I am running into an issue with getting mplayer to work in firefox, I removed totem, and reinstalled mplayer thinking this would work but all I get is a black spot where video should be and on some sites it says no video in the black spot, on other sites it just hangs. I even went so far as to do a fresh install thinking this was the cause of both of my issues but I am still running into the same thing. 

Also before I forget, is there a way to get the text back on my my usplash? I really like to see what is and is not loading. 

If anyone can help me with these issues I will be really greatful :D

---

### Post by QUEEN HIPPOLYTA on 2007-02-26
Sorry to reply to my own post, but I need help on this because things are not working and I really don't want to have to reinstall the older version of UBUNTU

---

### Post by jkeyes0 on 2007-02-26
can you provide more specifics on your computer and installation? The shutdown problem you're having sounds like the issue I had. Do you have an ATi video card, and if so, did you install the 8.34 driver?

---

### Post by QUEEN HIPPOLYTA on 2007-02-26
My graphics card is VIA and it the onboard graphics card for the compaq I have.

---

### Post by jkeyes0 on 2007-02-26
In that case I'm not sure about the shutdown issue.

Do you have the package totem-mozilla installed? (you can check in Synaptic Package Manager). If so, remove it, and make sure you have the package mozilla-mplayer installed.

---

### Post by QUEEN HIPPOLYTA on 2007-02-26
> **jkeyes0 said:**
> In that case I'm not sure about the shutdown issue.

Do you have the package totem-mozilla installed? (you can check in Synaptic Package Manager). If so, remove it, and make sure you have the package mozilla-mplayer installed.

I found out why my video would not work for some reason which I am not sure of the mozilla plug in for vlc got installed on my system. I have also removed the mozilla totem package. 

Now after doing that, I am left with a few questions----What is the differance between totem xine and totem gstreamer? All I know on the subject is AUOTOMATIX replaces the gstreamer version with the xine version. Is there any advantage to using either one? Are there any extras from the repositories needed to make each one work properly? If so what are they?

Thanx for all the great help on this :guitar:

---

### Post by Maestro23 on 2007-02-26
Take a read on Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats#head-79bfba9a0e96d62a622a47430239a1d49454c953](https://help.ubuntu.com/community/RestrictedFormats#head-79bfba9a0e96d62a622a47430239a1d49454c953)

---

### Post by QUEEN HIPPOLYTA on 2007-02-27
Thanks for the help on the media players, I am still stuck having to reboot manually because my system gets stuck on shutdown. I am hoping someone has an answer for what is going wrong so I can fix it, and I would love to get my scrolling text back un the usplash.

Thanx for all the help so far :KS :popcorn: :)

---

### Post by Boodah on 2007-02-27
I was having a similar issue with my Dell Dimension. Seems to be an issue with older PCs

Post three from Ridgeland on the following link solved my problem [http://www.ubuntuforums.org/showthread.php?t=359190&highlight=shutdown+hangs](http://www.ubuntuforums.org/showthread.php?t=359190&highlight=shutdown+hangs)

in my case  adding a kernel option of "acpi=force lapic" worked.
Hope this helps

---

### Post by confused57 on 2007-02-27
This worked for my Edgy shutdown problem:
[http://www.ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1714220&postcount=9)

---

### Post by nonewmsgs on 2007-02-27
to disable spalsh load the /boot/grub/menu.list file in (sudo) gedit scroll to the bottom you should see a line like this

kernel /boot/vmlinuz-2.16.15-10-386 root=/dev/hda1 ro quiet splash

and remove the word spash

darn i think that's for the initial one not the end one :(

---

