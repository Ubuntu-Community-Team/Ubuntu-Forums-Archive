---
title: "what to do when you get to *****@ubuntu:~$"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by jkblitz on 2005-12-02
hi im a begining user of linux i have used live cds before and i have not had any probs but now that i decide to take the step of instaling ubuntu on my computer its just saying Myname@ubuntu:~$ and i dont know what to do so if any one can help me i would be very thankfull.

---

### Post by linbetwin on 2005-12-02
Where does it say that? Did you install it?

---

### Post by jkblitz on 2005-12-02
ya i put the cd in and went through all the setup steps (the blue screens)
abd then i took out the cd and restarted the comp then some more steps then i came to this thing the same thing happend to me when i had tried a diffrent destro

---

### Post by aysiu on 2005-12-02
You might have accidentally done a server install.
Try ```
startx
``` If that doesn't work, try ```
sudo dpkg-reconfigure xserver-xorg
``` If that doesn't work, try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by az on 2005-12-02
Do not worry.  Although the lack of the graphical interface may seem like a big problem, you are not far off from having your system up and running.

It should be an easy fix.

---

### Post by jkblitz on 2005-12-02
none of those codes worked

---

### Post by linbetwin on 2005-12-02
You say this also happened with other distros? How old is your computer? What CPU and how much RAM?

---

### Post by jkblitz on 2005-12-02
yes i used debian i had the same prob my computer is p3 512 mb of ram on 30 gb maxtor hd

---

### Post by aysiu on 2005-12-02
[QUOTE=jkblitz]none of those codes worked[/QUOTE] Thanks. What happens when you type those codes in? "It doesn't work" doesn't help. What are the exact errors you're getting?

---

### Post by jkblitz on 2005-12-02
[QUOTE=aysiu]You might have accidentally done a server install.
Try ```
startx
``` If that doesn't work, try ```
sudo dpkg-reconfigure xserver-xorg
``` If that doesn't work, try ```
sudo apt-get install ubuntu-desktop
```[/QUOTE]
for the first one it says command not found and for the other two it says 
sudo:unable to lookup ubuntu via get hostname

---

### Post by az on 2005-12-02
You either have a bad cd or some bad hardware.  Is this an older hard drive or computer and was it working properly beforehand?

Also, can you boot the installer cd again and make it do an integrity check?  (You get to this menu by skipping the part when it asks you about the keybord.  Scroll down to the integrity check and make that go.

Either way, you did not do anything wrong.  It is not supposed to do that.

---

### Post by jkblitz on 2005-12-02
ya this hard drive is working fine i was just useing win me before i installed ubuntu and the comp was working fine il do the installer again and see what happens

---

