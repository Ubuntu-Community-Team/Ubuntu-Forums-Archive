---
title: "Lucid Lynx Macbook Keyboard Not Working"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by barretme on 2010-05-04
I upgraded to 10.04 on my Macbook and everything was working fine. Now, my keyboard isn't working at all. I didn't do any system tweaks or anything. Has anyone else experienced this?

---

### Post by Dimitar Dobrev on 2010-05-06
I experienced exactly the same: I upgraded from 9.10 to 10.04 on a Macbook Pro 5.2 (early 2009). My keyboard does not work at all, neither in the login screen nor after login (in fact I wouldn't have been able to log in if it wasn't for the on-screen keyboard).

---

### Post by CohibaMan on 2010-05-09
Same exact problem here after upgrading from 9.10 to 10.4.  Any help with the matter will be greatly appreciated.

---

### Post by kmyram on 2010-05-10
My keyboard stopped working after upgrading as well.
Macbook1,1

---

### Post by linuxopjemac on 2010-05-10
what about a fresh installation ?

---

### Post by frabcus on 2010-05-10
I have exactly the same problem. Had Karmic installed, upgraded to Lucid in place, rebooted, and keyboard didn't work.

If in grub (pressing Esc quickly after boot) I select the previous kernel (still left over from my Karmic installation) 2.6.31-21-generic then everything seems to work fine.

I haven't got a working CD to boot off right now to try a fresh installation. Would be interested to know if that is better for people.

---

### Post by CohibaMan on 2010-05-10
This appears to have fixed it for me...

[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

I hope it will work for you guys as well.

*Edit* I should add that it did not quite say on my system what it said in the article but I made the same changes regardless and switched back to the MacBook keyboard once I was actually logged in.  Seems to be normal now.

---

### Post by Dimitar Dobrev on 2010-05-10
Thanks, frabcus, your solution works for me, it's much better than nothing.

CohibaMan, my console-setup is quite different:
XKBMODEL="macbook78"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS="grp:alt_shift_toggle,grp_led:scroll"

and I don't know how to change it. Do you have any idea or should I experiment?

Another thing: before you fixed your keyboard did you get the following message during boot:
"hid: Unrecognized parameter: pb_fnmode"?

---

### Post by CohibaMan on 2010-05-10
Dimitar-

I am still very much a beginner with Ubuntu and Linux in general (albeit I am also a quick learner) so I am hesitant to give any advice directly.  My settings were something similar to what you mentioned.  I initially just replaced them with the following since I didn't know what my own settings were:

> XKBMODEL=&#8221;pc105&#8243;
XKBLAYOUT=&#8221;us&#8221;
XKBVARIANT=&#8221;"
XKBOPTIONS=&#8221;"That actually worked.  After I logged back in, I reconfigured my keyboard settings to MacBook.  My current settings look like this - using these values might be a better solution than what I did:

> XKBMODEL="macbook78"
XKBLAYOUT="us,us"
XKBVARIANT="mac,"
XKBOPTIONS=""You can change it by going to /etc/default and running "sudo nano console-setup" -- you can directly change the settings there and write your changes to the file.

I should note that running the earlier kernal did NOT work for me so it is also possible that we have different problems here.

At any rate, best of luck.

---

### Post by Dimitar Dobrev on 2010-05-10
Thanks. That did not work, unfortunately - apparently my problem has to do with that "pb_fnmode" thing I mentioned.

---

### Post by JoeMac42 on 2010-05-10
The fix didn't work for me, but a clean install did work.  I'm using one of the "Windtunnel" Dual-G4 Macs.

---

### Post by frabcus on 2010-05-11
Dimitar - looking at my kern.log, yes with the new kernel I got "hid: Unknown parameter `pb_fnmode'" lots of times.

I have that set in a couple of places in modprobe.d:

cat:/etc# grep -r pb_fnmode *mod*
modprobe.d/macbook-special.conf:options hid pb_fnmode=2
modprobe.d/hid_apple.conf:options hid pb_fnmode=2

It's the option which makes it so the function keys are normal functions keys, and you press Fn to make them set the volume / brightness (rather than the default, which is the other way round).

Aha! Here's the magic, a bug report with fix for the same thing in Arch Linux: [http://bugs.archlinux.org/task/12815](http://bugs.archlinux.org/task/12815)

Found thanks to use spotting the pb_fnmode error, which is what I searched for to find the report.

---

### Post by Dimitar Dobrev on 2010-05-12
I finally found the problem. In /etc/modprobe.d/options.save I had the line of "options hid  pb_fnmode=2". Ubuntu was confused by the extension ("save") and showed it to me as a binary file which is why it took me so long to fix this. I removed "pb_" (that is, the line became "options hid fnmode=2") and now my keyboard works just fine, with functional keys working as normal keys.

---

