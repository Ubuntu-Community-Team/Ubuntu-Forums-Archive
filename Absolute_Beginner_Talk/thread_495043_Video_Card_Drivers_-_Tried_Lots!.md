---
title: "Video Card Drivers - Tried Lots!"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by shroomduck on 2007-07-07
Ok well I am literally 2hr old ubuntu users, just got 7.04 (fiesty) and i am have troubles with my vid card.

I have a Toshiba Laptop model#  A100-SK9 with a Geforce Go 7300 256mb PCI-E Video card.

I have tried envy, and I have had to reboot and reconfigre xserver like 3 times already, just cannot get it to work, please help =):popcorn:

---

### Post by Twizz on 2007-07-07
You could try Automatix from Getautomatix.com  I thinkt hey have Nvidia Driver installation.  I hope it helps you.  I'm stuck with An old ATI 9000, so I never had a need to figure out Nvidia Drivers.  Also if your new Automatix can make life easy by installing most everything you will need.

---

### Post by annda on 2007-07-07
have you tried getting the driver via restricted drivers manager? it installs the driver from the repositories, which should work fine with your card (i have 7400, so it's very similar)

---

### Post by shroomduck on 2007-07-07
how is this done?

---

### Post by forestpixie on 2007-07-07
system>admin>restricted driver management

---

### Post by Dark Seraphim on 2007-07-07
oh go to applications and add/remove and in the search bar type nvidia should give you some drivers try them all cause im not sure sorry

---

### Post by shroomduck on 2007-07-07
did this to no avail [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by splintercellguy on 2007-07-07
I thought you had nvidia card?

---

### Post by shroomduck on 2007-07-07
sorry wrong link lol, gotta find the one i used

---

### Post by Vague on 2007-07-07
> **shroomduck said:**
> did this to no avail [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Try this one instead: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

;)

---

### Post by Dark Seraphim on 2007-07-07
sudo aptitude install nvidia-glx-legacy 

try that

---

### Post by shroomduck on 2007-07-07
> **forestpixie said:**
> system>admin>restricted driver management

worked! thanks alot guys, really appreciate the help and fast responses, can already tell i'm gonna love it here =)

---

### Post by Dark Seraphim on 2007-07-07
oh cool im glad it worked out for you. welcome to ubuntu lol

---

### Post by shroomduck on 2007-07-07
ok, after thinking it was fixed, I checked my screen resolutions and cannot get my toshibas 1280x800 so I think something is wrong, I've tried everything listed in this thread to no avail.

---

### Post by Dark Seraphim on 2007-07-07
system>prefrences>screen resolution

I think that might help but I found that I cant get any higher resolutions just lower resolutions

---

### Post by shroomduck on 2007-07-07
yes it appears im stuck at 1024x768?

---

### Post by annda on 2007-07-07
try

```
gksudo nvidia-settings
```

make sure you save changes to xorg.conf before exiting!

---

### Post by Dark Seraphim on 2007-07-07
sudo dpkg-reconfigure -phigh xserver-xorg might do somethin or restart your pc maybe

---

### Post by shroomduck on 2007-07-07
```

ERROR: Failed to add display device 'LPL' to screen 0!
ERROR: Failed to add X screen 0 to X config.
ERROR: Failed to add X screens to x config.
ERROR: Failed to generate an X config file!

```

I get that when I try to switch it to 1280x800

---

### Post by shroomduck on 2007-07-07
when i do gksudo nvidia-settings

---

### Post by shroomduck on 2007-07-07
holy crap I think we got it, had to hit apply instead of hitting Save to x

---

### Post by Dark Seraphim on 2007-07-07
oh cool hope everything goes smootly for you after this lol.

---

### Post by shroomduck on 2007-07-07
you and me both man lol

---

