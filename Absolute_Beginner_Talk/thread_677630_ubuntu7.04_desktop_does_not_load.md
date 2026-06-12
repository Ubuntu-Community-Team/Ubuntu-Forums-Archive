---
title: "ubuntu7.04 desktop does not load"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by bennolederer on 2008-01-25
at the command user-name@desktop i typed in "startx" and i recieved the following message No devices dectected  Fatal server error  No Screens Found  XIO: Fatal IO error 104      what does this mean?  do i need a video driver or a new video card?

---

### Post by jeffus_il on 2008-01-25
What video card do you have?

---

### Post by Rocket2DMn on 2008-01-25
You need to reconifgure X.  The following command will ask you questions about your hardware, do your best to answer.  If you have an ati video card, select "ati" for the video driver, but select "nv" if your card is an nvidia, or "intel" if you're using an onboard intel card.  At the resolutions questions, use TAB to move around and SPACEBAR to select your monitor's max resolution and everything less.
```
sudo dpkg-reconfigure xserver-xorg
```
Then restart gnome
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

Also, version 7.10 has been available for a few months, so you may want to consider upgrading.
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

