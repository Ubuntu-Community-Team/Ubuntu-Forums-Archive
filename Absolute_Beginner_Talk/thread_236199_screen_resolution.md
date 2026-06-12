---
title: "screen resolution"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2006-08-14
I changed out the monitor and now I can't change the screen resolution, so everything is huge.  It only has one size on screen resolution.  Any ideas?

---

### Post by bruce89 on 2006-08-14
In terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by anubis2814 on 2006-08-14
That didn't do anything but thanks.

---

### Post by Kobalt on 2006-08-14
Then try :
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions and make sure to chose the resolutions you want in the list by typing the space-bar on each one. Then, resatrt X with Ctrl+Alt+Backspace. 

Now it should work.
Cheers ! :rolleyes:

---

### Post by davebgimp on 2006-08-14
I've had that problem myself at one time or another. Check this HOWTO:

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by bruce89 on 2006-08-14
Did you select the resolutions you want to have in the menu.  I forgot to say you have to restart X by pressing Control+Alternate+Backspace after it.
> **Kobalt said:**
> Then try :
```
sudo dpkg-reconfigure xserver-xorg
```
The -phigh switch skips all the steps apart from resolution.

---

### Post by anubis2814 on 2006-08-14
Thanks alot guys, It works now!:)

---

### Post by satbunny on 2006-08-14
How can I get my screen refresh to be other than 60Hz which is the only refresh rate my install gave me? My monitor suport higher and 60Hz gives me headaches.

---

