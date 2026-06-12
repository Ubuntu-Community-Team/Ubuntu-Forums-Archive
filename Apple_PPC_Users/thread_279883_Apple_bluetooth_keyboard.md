---
title: "Apple bluetooth keyboard"
date: 2006-10-18
forum: Apple PPC Users
---

### Post by danraider on 2006-10-18
Greetings everyone, this is my first post. Long time Linux user, first time Ubuntu user. (ok, in fairness I have been off Linux for a while...)

My usual dist of choice would be Slackware but now I have a mac mini PPC and even though OS X kick some serious b**t every now and then you need a dose of good old gnome.

Just to make it perfectly clear, I have been googleing:
[http://www.ubuntuforums.org/showthread.php?t=224673&highlight=bluetooth+keyboard](http://www.ubuntuforums.org/showthread.php?t=224673&highlight=bluetooth+keyboard)

Above mentioned is essentially my problem. The problem being that my bluetooth keyboard does not work. I have read every here and there about commands you can *type* to get it to work, but let's face it, I don't have that luxury, if I had I wouldn't be posting here about my problems, would I?

What I'm asking for good sir (or madam for that matter) is a way to sort this issue while logged on to OS X where my keyboard evidentially is working.

Now I'm not a rich man I can only reward you with respect and virual hugs and kisses. Should you choose to accept such a currency I would greatly appreciate it.

Thanks heaps! - Dan

[edit] - Sorted some spelling

---

### Post by sergiez on 2006-10-20
Dear Dan,

I don´t think your problem could be solved booting from OSX. The thing is the ubuntu bluetooth module is not working with the Apple wireless keyboard. In my case the problem was solved just removing the bluez-utils package from the ubuntu installed system. So may be somone near you can lend you an USB keyboard so you can use your ubuntu system, remove this package and restart with your wireless keyboard to check if it is running.

No kisses are required.

Good luck!

---

### Post by Rocan on 2007-05-09
Dan we are nearly identical in our problems. Sergiez ty for that but sadly i cant seem to find anyone who is willing to lend me there keyboard for a day:mad: :mad: . i shall have to wait for my master linux friend eric to help me since i am new to linux. if i master linux then i will have mastered all three os's!:) :)

---

### Post by aantn on 2007-05-10
Its fixable (or at least I fixed it on my Mac). The only problem is that you need a wired keyboard or mouse to fix it. 

You have to uninstall a few packages that begin with "bluez". I think bluez-cups, bluez-gnome, bluez-pin, and bluez-utils. 

Try running:
sudo apt-get remove bluez-cups bluez-gnome bluez-pin bluez-utils

---

### Post by aantn on 2007-05-10
If you're in Israel then I can lend you a keyboard :grin:

---

### Post by zalberico on 2007-05-11
I've done it!
Really easy fix :)
open up synaptic package manager (in system administration I think) then find and unistall bluez-utils.
Mouse and keyboard will work immediately:)
enjoy!

---

### Post by Rocan on 2007-05-11
i know how to fix it i just need a wired keyboard. thanks aant for the invatation but im in ny sadly:( :( .  also i still need to partition my HD to install ubuntu because i havent installed it yet because i need to cleaqr about 25 gigs worth of games of my HD for some space. thanks for your help guys. i appreciate it!

P.S. sorry for all the errors im rushing!

---

### Post by Rocan on 2007-05-13
hmmmmmmm.... just thinking can it be done with only a wired mouse?
If so then say how!!!

---

### Post by bitterbug on 2007-05-18
I love you guys!!!

I'd been entering text one letter at a time with the charmap utility during setup, at least until I found this thread.

Verified:
Provided you have a USB mouse handy, all you need to do is open Synaptic from the System menu as stated above. Remove the bluez* packages, apply, and about 30 seconds later at most your Bluetooth Keyboard will be fully functional.

Update:
While it worked fine in LiveCD mode, once Ubuntu was fully installed I ran into a small problem. Now I can't get past the login screen to access Synaptic to get it working there. Poop.

---

### Post by bitterbug on 2007-05-19
Got it working :)

Dan,
Does your bluetooth keyboard connect okay when yaboot is booting the system, and then stops working at the login screen?

If it does, then you can just type:
```
Linux single
```

at the yaboot prompt and it will load a console as root for you.

Then use apt-get or aptitiude to remove the bluez-* modules noted above.

When you reboot you should be able to use your keyboard at the graphical login screen. :)

---

### Post by null84 on 2008-04-18
hey guys. thanks for the thread. it got my bt keyboard and mouse working. however, the bluetooth option for other device is gone now. does that mean i cannot use my mac bt for other device such as my cell phone?

---

