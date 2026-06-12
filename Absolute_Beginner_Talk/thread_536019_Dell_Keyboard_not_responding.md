---
title: "Dell Keyboard not responding"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Webby_s on 2007-08-27
So the keyboard is not responding at boot. But when the Grub screen has disapeared and started to boot Ubuntu 7.04, the keyboard comes back. I have a Dell 25** Inspirion I believe. (I am at work now):-#

So is it something with the BIOS. It all happened when I moved it from one room to the next in the house. I am also in the process of possibly switching over to Kubuntu so I don't want to start that process and not have the keyboard work while reinstalling.

Thanks in advance.

---

### Post by kellemes on 2007-08-27
You have to turn on legacy usb support in BIOS, newer mb's should recognize it.
But your mb has to support the newer USB2-connection though..
In my case it doesn't, so I have a PS2 keyboard only to be able to use the bootmenu.

Edit: this is a USB-keyboard?

---

### Post by Webby_s on 2007-08-27
Funny you should ask. And sorry I didn't specify earlier!  No it is not a USB keyboard, only the mouse is. The keyboard is a PS2! Sorry! Hope this helps.

Also if this problem procist can I still install a different disto (Kubuntu) with out any problems. But don't get me wrong I would like to fix the problem first and formost!

---

### Post by Webby_s on 2007-08-27
Still no resolution. Should I go to a dell BIOS specific forum?

---

### Post by kellemes on 2007-08-27
I'll be honest with you.. I don't know what's happening here!

Anyway, when you do install Kubuntu, you only have to install ubuntu-desktop (I believe) to get Ubuntu. So if this works for you, it's the way to do it.

---

### Post by Webby_s on 2007-08-27
**kellemes** thanks for the quick response. The main reason I am reinstalling/switching to Kubuntu is to see if I then get my Keyboard response on boot up back and because I want to try the KDE platform. I like the look and feel of the KDE and I just want to be able to possibly dual boot in the future with Kubuntu and possibly a different distro.

Thanks again and I may just go ahead and try it. Wish me luck or I will be out a computer for 3 days (at home that is.)

---

### Post by Chris S. on 2007-08-27
Whoa.  Before you take that leap (which probably wouldn't hurt, but may not fix your problem), try going into the BIOS anyway and looking around for keyboard options.  It won't be a USB issue, since you are using a PS2 keyboard, but if your keyboard works in Ubuntu but not during the GRUB startup, then there may be a problem in the BIOS.  The thing is, if the BIOS is messing up the keyboard, I wonder if you can still use the keyboard to access the BIOS at startup...

Otherwise, you could try to restore GRUB, which I don't know how to do, but you could search the forums.

Edit: You could also try to reset the BIOS from the motherboard, but that can be a crap shoot.  Still, if you can't get into the BIOS, it's the best way to get keyboard support back and get back in.

---

### Post by Webby_s on 2007-08-27
Exactly.... I can't get into the BIOS because I that is the time that the keyboard is not working. The first think after the DELL logo at initial startup is "keyboard not detected" then it goes through the count down at the GRUB menu and when I get to the Ubuntu logon screen all is well. I will more then happily reset the BIOS on the MB but to be honest with you I don't know how, I will search the web and learn but until then I don't. 

So thank you **Chris S.** for the suggestion!

PS reseting the BIOS do I take out the battery on the MB? What will I have to do once I reset the BIOS just reset the Date and Time?

---

### Post by kellemes on 2007-08-27
For my mb I have to shortcut a jumper to reset the BIOS, the battery has nothing to do with the BIOS.
You should visit the Dell site to find out how to..

---

### Post by Webby_s on 2007-08-27
I have posted the problem over there at the dell forums. Lets keep are fingers crossed.

---

### Post by Chris S. on 2007-08-27
Do you have any other PS/2 keyboards you can try?  Maybe borrow a friend's or "borrow" one from work or school?  Oh, and good luck; this is as much as I can help. :)

---

### Post by Webby_s on 2007-08-28
Thanks again **Chris S.**

Here is an update. So I have got Kubuntu up and running on this Dell Dimm 8380 but the keyboard keeps doing the same thing: At start up the keyboard doesn't work then once Ubuntu starts to load everything is fine **EXCEPT:** when I have num lock on my arrow keys (specificly left and right) will launch armok (it did it both in Ubuntu and Kubutu FYI). So when I have num lock off everything is fine. Weird and a pain in the butt but not life threatning.

---

### Post by kellemes on 2007-08-28
Never heard of this one..
But glad you solved it anyway..

---

### Post by Webby_s on 2007-08-28
Thanks **kellemes**

But I wouldn't call it *solved*, more like a nuisance and a pain in my rear end side cuz I can't dual boot if I would like to.

---

