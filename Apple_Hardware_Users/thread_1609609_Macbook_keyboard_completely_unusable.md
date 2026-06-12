---
title: "Macbook keyboard completely unusable"
date: 2010-10-30
forum: Apple Hardware Users
---

### Post by skibler on 2010-10-30
I installed 10.10 on a rev 1.1 macbook last week. It has been up and running quite well all week.

I reset the computer, and now I have no keyboard input at all! I could only log in by bringing up the on-screen keyboard using the mouse. I tried plugging in a usb keyboard, but that did not work either.

Once logged in neither the built in or usb keyboard work.

Under System>Preferences>Keyboard>Layouts I have (and have had!):

USA Macintosh, Keyboard model: Apple Laptop.

It was like that before and the keyboard was working just fine. Putting it on 105 key generic makes no difference.

I can ssh and use vnc to connect and control the laptop, but it is otherwise quite useless right now!

Where do I begin in trying to fix this?! Thank you for any help!


edit: The keyboard works in grub, but if I boot into recovery mode the keyboard doesn't work at the recovery menu :/.

---

### Post by linuxopjemac on 2010-10-31
You need the following line in /etc/modprobe.d/options.save

```
options hid pb_fnmode=2
```

some people reported they had
pm_options hid pb_fnmode=2
They remove pm_ and it worked after that.

Other reported to have luck with this site:
[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

See this thread where I got the solutions from:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1472117](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1472117)

---

### Post by skibler on 2010-10-31
Thank you linuxopjemac!

That wasn't my problem specifically, but it did lead me to the solution!

Earlier in the week I had been searching for a way to have the Function Keys behave normally, like having a permanent f-lock key.

I followed advice on a wiki article [here](https://help.ubuntu.com/community/AppleKeyboard), and made a conf file in /etc/modprobe.d/ with "options hid_apple fnmode=2" in it.

That file was the culprit! I removed that file and rebooted and the keyboard works normally!

Thanks again! I feel pretty silly :p.

---

### Post by vincebs on 2010-11-06
What did you do? I'm confused.

Did you create the file hid_apple.conf or did you delete it?

---

### Post by kosumi68 on 2010-11-06
Actually, having a kernel module bail out because the wrong kernel parameters are set sounds like a *kernel* bug. I was hit by this problem too, in a slightly different setting.

In other words, great that you brought this up!

---

### Post by skibler on 2010-11-08
> **vincebs said:**
> What did you do? I'm confused.

Did you create the file hid_apple.conf or did you delete it?

I had created that file myself as per the info in that page I linked. After resetting the computer, my keyboard was dead. I finally figured out that removing that file was the solution.

---

