---
title: "[SOLVED] How do I report a keyboard bug/ help fixing it"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by mactece on 2007-07-09
I'm thinking I have a bug (described below). There are two threads on this topic on the forums site but no-one mentions if they have reported it as a bug. Symptoms seem to be sililar to mine. There may be a common factor in the motherboard. I have an ASUS KT7A, one of the other posts mentions a similar board.

Q1 - is it a bug?
Q2 - if so how do I report it?
Q3 - Either way can anyone help me with it?

Thanks
David

I had to do a clean install of Windows and Ubuntu 7:04 following a hard drive crash. Now when I boot into Ubuntu the keyboard is not working. The hardware is ok and windows is working and the keyboard works with live distros (CD ROMs) of PCLinux and Ubuntu 6.10. 

I have reinstalled Ubuntu 7:04 twice and go the problem both times. I can't work around it as I can't get into Ubuuntu. I tried a recovery boot and it gave me a prompt but I couldn't use the keyboard.

One really odd thing is that I have the same problem with the Live Distro of 7:04 and a backup hard drive I made for system rescues (once bitten...) 2 days ago. What makes it really odd is that they were both working when I did the initial install with that live cd to that hard drive. And now they are not.

other things I have done: cleared the CMOS, swapped the hard drives, unplugged the keyboad and plugged it back in again.

---

### Post by KIAaze on 2007-07-09
Q1 - is it a bug?
Does sound like one to me.
Q2 - if so how do I report it?
[https://launchpad.net/ubuntu/+bugs]("https://launchpad.net/ubuntu/+bugs")

And the keyboard works in Windows?
Have you tried installing Debian or other distros to see if it works with it?

Personnally, I noticed that SCIM caused my keyboard to malfunction, so I disabled it. ([bug posted here]("https://sourceforge.net/tracker/?func=detail&atid=650539&aid=1734093&group_id=108454"))
But it never prevented me from logging in and even after that my keyboard worked sometimes. It was just that it seemed to freeze from time to time.

---

### Post by mactece on 2007-07-09
Thanks for the suggestions - while I was at work my wife wanted to use the PC so simply tried every port including the mouse port which of course I didn't because I know what it's for. And the keyboard is back! Brilliant work and I feel a bit daft. But...

With Linux cd rom distributions (including 6:10) I can plug the keyboard into either the mouse or keyboard ps2 port and the keyboard works. With windows (which I need for work applications which aren't available in Linux) the keyboard must be plugged into the keyboard port and with Ubuntu 7:04 (my preferred OS) it must be plugged into the mouse port.

Hey ho!

Will keep trying swaps and messing about and seeing if I get a result but it does feel like Ubuntu is not seeing the keyboard ps2 port.

Anyone know how to check?

David

---

### Post by KIAaze on 2007-07-09
And the mouse works in the keyboard PS2 port?
Really weird. ^^

---

### Post by mactece on 2007-07-09
The mouse is in a USB port -  just as well, really

---

### Post by mactece on 2007-08-17
I finally fixed this by buying a USB keyboard. Problem solved. However I still have the PS2 keyboard and will need it if I ever have to reinstall windows. The installation cd for XP can only see the PS2 keyboard for some reason.

---

### Post by Arthur Archnix on 2007-08-17
Nice job solving this. Oh and great detail in your original post. You've got a knack for asking good questions, which is probably why you ended up fixing your own problem.

---

### Post by mactece on 2007-09-26
Thanks - all praise gratefully accepted!

---

