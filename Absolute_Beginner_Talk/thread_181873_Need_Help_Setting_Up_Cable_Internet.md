---
title: "Need Help Setting Up Cable Internet"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by eeefresh on 2006-05-24
Hello all.  I am a brand new Ubuntu/Linux user and could use a little help.  My mom recently gave me an old Sony Vaio Pentium 3 laptop, so I decided to load Ubuntu on it and try it out.  The installation seemed to go smoothly and I have spent the last 48 hours playing around and learning about using Linux.

My other computer is a desktop, and I use Insight Cable Internet through it.  It came with an installation CD, so setting it up was a cinch on XP.  Now I  want to hook the Ubuntu laptop up to the cable modem.  I don't have a router (I have  been using ZoneAlarm and Windows firewall on the desktop).  Here is what I have tried so far, with no success:

1. Plugging the ethernet cable directly into the laptop -- No luck
2. Resetting the cable modem, then trying step 1 again -- No luck
3. Reinstalling Ubuntu with the cable plugged in -- No luck (I get a DHCP not found error.)

I searched the forums and didn't find much (at least, not much that I understood.)  I'm not opposed to using Terminal, but I am pretty unfamiliar with it at this point and would prefer an auto-configuration, if possible.  I'm also not very experienced with networks in general...so basically I need someone to hold my hand each step of the way! :)

Any help would be appreciated!

---

### Post by zhoux on 2006-05-24
did you try pluggin in the cable, then go to system => administration => Networking?

You may need to active one of those connections. perhaps something like eth0(which is mine).

hope that helps

---

### Post by nalmeth on 2006-05-24
Haven't had to bust this one out in a while, but chew on it and see how it tastes.
[Wired Ethernet Troubleshooting]("http://www.ubuntuforums.org/showthread.php?t=87643") 
There will be terminal work, but hopefully your problem is something simple.
Report back any more problems

---

### Post by nanotube on 2006-05-25
[QUOTE=eeefresh]Hello all.  I am a brand new Ubuntu/Linux user and could use a little help.  My mom recently gave me an old Sony Vaio Pentium 3 laptop, so I decided to load Ubuntu on it and try it out.  The installation seemed to go smoothly and I have spent the last 48 hours playing around and learning about using Linux.

My other computer is a desktop, and I use Insight Cable Internet through it.  It came with an installation CD, so setting it up was a cinch on XP.  Now I  want to hook the Ubuntu laptop up to the cable modem.  I don't have a router (I have  been using ZoneAlarm and Windows firewall on the desktop).  Here is what I have tried so far, with no success:

1. Plugging the ethernet cable directly into the laptop -- No luck
2. Resetting the cable modem, then trying step 1 again -- No luck
3. Reinstalling Ubuntu with the cable plugged in -- No luck (I get a DHCP not found error.)

I searched the forums and didn't find much (at least, not much that I understood.)  I'm not opposed to using Terminal, but I am pretty unfamiliar with it at this point and would prefer an auto-configuration, if possible.  I'm also not very experienced with networks in general...so basically I need someone to hold my hand each step of the way! :)

Any help would be appreciated![/QUOTE]
there is one other thing you should have tried:
4. plug ethernet cable directly from cable modem to laptop (while the laptop is turned on), and THEN reboot the cable modem.

then, see what is the output of "ifconfig" command - if all went well, you should have an ip address...

---

### Post by eeefresh on 2006-05-25
Thank you all for the help.  I tried Nanotube's advice first (since it was the easiest) and it seemed to work.  Thanks gain!

---

