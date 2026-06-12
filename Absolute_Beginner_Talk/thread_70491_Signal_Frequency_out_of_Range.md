---
title: "Signal Frequency out of Range"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by todger on 2005-09-30
Hi all,

I am obviously a newb and need some help. I thought I might get further than this though. On boot the OS (Hairy 5.04) lets me log-on, I can see enough to know the Rez is set way too high. I then get a black screen with a red box telling me the Signal Frequency is out of range FH>107.6kHz FV>130Hz.
Please change signal timing.

Is this a driver issue, a monitor issue or something more sinister?

---

### Post by heimo on 2005-09-30
[quote=todger](Hairy 5.04)[/quote]

LOL :D 

(two minutes later)

Ok... ;) To the question. It's configuration issue. You should be able to press ctrl+alt+F1 (these three buttons at the same time) to get console. You can login with the account created during install. Then you should enter these commands:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```
It will ask bunch of questions, pay attention to the ones about your monitor and graphics card. After reconfiguration, enter this:
```
sudo /etc/init.d/gdm start
```

To get more specific instructions, just ask - and if you could, please include your xorg.conf file (as an attachment) and model of your monitor and graphics card. :)

---

### Post by todger on 2005-09-30
Sorry about the delay in getting back to you guys... It was bed time here for four year olds, either that or get him to help me.

I'm glad I gave you a good chuckle....

I have just come back in to find I could re-boot and now have a GUI....Thanks and Thanks....

I'm sure you will see me here asking more FAQ's but I gotta learn....

Cheers.

---

### Post by _smd_ on 2005-11-12
heimo-  I had tried what you had suggested with my friend earlier this week.  I am still getting the same error  - out of frequency range.  Not sure what else to try.  Do you have any other suggestions?

---

