---
title: "ethernet Cable Activity Chaos...."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by John Murphy on 2006-08-29
I've had more trouble regarding my cable modem on SuSE9.3 than I care to mention....... The Drake is still much better but still a long way from good!

I'm not sure what it is or why it happens but practically everytime  reboot my internet connection dissappears. The only way I can get it back is by shutting down, booting into the Windows Partition, shutting it down in turn and then restarting The Drake.......

Having ne or two weird issues like this..........

Anyone know how I can fix this so that I connect every time  - Linux is really dependent on Internet Connection more so than WindA$$Ex-Pee and I want to stay connected til I have everything configured more or less how I want them...... Hard work this!!!!!

---

### Post by funchords on 2006-08-30
Hmmm.  Try this in a terminal window next time...  (replace eth0 with the proper device name)

sudo ifconfig eth0 down
sudo ifdown eth0
sudo ifconfig eth0 up
sudo ifup eth0

If that helps, then next time try a subset, such as just these two:

sudo ifconfig eth0 down
sudo ifconfig eth0 up

or these two 

sudo ifdown eth0
sudo ifup eth0

The results will tell us which way to go next.  Either way, we'll be editing a script in /etc/networks I think.

If none of the above is of any help, what happens if -- instead of rebooting into windows -- you simply unplug and reattach the network cable to the computer?

---

### Post by John Murphy on 2006-08-30
Hey Thanks - but my systems gone........... Am seriously having to rethink whether or not I will reinstall Dapper as The crash was similar to one I had on SuSE 9.3 last year - as other have pointed out most likely a hardware issue and I'm thinking strongly it's my nVidia GeRorce Go 5600 (on a Dell Inspiron 8600). There's nothing much I can do........ but thanks again!

---

