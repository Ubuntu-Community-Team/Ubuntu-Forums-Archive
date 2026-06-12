---
title: "[SOLVED] How do i take of the touch pad tap to click option?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-07
Its getting super annoying and I'm used to it not licking anything when i tap it. How do i take it off? I need to know please.

---

### Post by tgm4883 on 2007-07-07
i think you have to install gsynaptic.  There is also something you have to add to your xorg.conf.  Can't remember what it is, but when you try to run gsynaptic it will tell you.

---

### Post by candtalan on 2007-07-07
you can edit the /etc/X11/xorg.conf
to include a maxtaptime value of zero
for more details asearch here on maxtaptime will bring up some information
hth

---

### Post by Alterax on 2007-07-07
Quick fix that works for me (mine is bad about doing this after coming out of suspension)

sudo trackpad notap

Now to figure out how to do this automatically when it wakes up....

--Alterax

---

### Post by ~~Tito~~ on 2007-07-07
I did a search in the app installer thing and i found it. Thanks guys.

---

### Post by jimbster2 on 2007-07-15
Look in /etc/pbbuttonsd.conf near the bottom of the file for TPMode    =tap
Change this to   =notap

This change will remain after restart.

Somebody let me know if this works for you.

---

### Post by anewguy on 2007-07-15
For those who may be looking at this thread, these are the steps I took to get control of my touchpad:

(1) sudo gedit /etc/X11/xorg.conf

    look for the device that shows as touchpad, and add this:

                    Option          "SHMConfig"              "true"

    then save and exit

(2) via system/administration/synaptic package manager, search for and install the following:

       gsynaptics    

(3) reboot

(4) you should now have a touchpad icon in your top bar that you can click on to control your touchpad


These things worked for me on my Gateway MX3215.  Perhaps they will work for you as well, as I think they are generic things.:)

---

### Post by tgm4883 on 2007-07-16
> **anewguy said:**
> For those who may be looking at this thread, these are the steps I took to get control of my touchpad:

(1) sudo gedit /etc/X11/xorg.conf

    look for the device that shows as touchpad, and add this:

                    Option          "SHMConfig"              "true"

    then save and exit

(2) via system/administration/synaptic package manager, search for and install the following:

       gsynaptics    

(3) reboot

(4) you should now have a touchpad icon in your top bar that you can click on to control your touchpad


These things worked for me on my Gateway MX3215.  Perhaps they will work for you as well, as I think they are generic things.:)

Thats what I did.  If the OP has fixed the problem, I urge him to mark the thread as resolved.

---

