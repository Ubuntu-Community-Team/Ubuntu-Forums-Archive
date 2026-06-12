---
title: "Modem Help, PLEASE!"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by sw1995 on 2007-07-10
Hello,

I have been using Ubuntu for about three months. For those three months I used a wireless network card to access the internet, no problems whatsoever. I am in a situation now where I only have access to dial up internet.

I'm in full blown panic mode because I need my computer because I teach online classes. At my house there is a windows machine that accesses the dial up internet but I need my laptop to run.

I am having a hard time figuring this out! Can someone please help me. I have read through the forums but I am at a loss. I am sure I need to provide more information but I just don't know what to say.

lspci tells me this about my modem (or a close approximation, I had to write it out):
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)

I guess this means Ubuntu recongnizes my modem.

Here is what I know about my connection: user name, password, and phone number.

I used the GNOME network configuration tool, but so far that doesn't seem to help (nor is there any kind of "connect" button so I'm not even sure if it is trying)

Any thoughts?  Thank you in advance for any help! This is my first urgent Ubuntu problem and it has me freaked out because it's do or die. Where do I begin!?

S

---

### Post by st0nes on 2007-07-10
Hi sw1995,

I would suggest you go here initially: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

If you still can't get it right then perhaps this will help: [http://www.sdc.org/support/dialup-ubuntu.shtml](http://www.sdc.org/support/dialup-ubuntu.shtml)

If neither of these solve your problem, you could ring up your ISP and ask them whether or not they have a specific option that needs to be set.

Regards

---

### Post by sw1995 on 2007-07-10
Thank you for the links. I have a feeling I am in deep trouble, as this is not newbie friendly stuff:(

EDIT: I am trying something out from the above link.

---

### Post by Bartender on 2007-07-10
What's your laptop brand/model?
I'm guessing the internal modem won't work because most of them don't.  Some can be made to work but from your comments I'm guessing you've seen some of the arcane directions and found them intimidating.
  
Such as this thread...[http://ubuntuforums.org/showthread.php?t=190728](http://ubuntuforums.org/showthread.php?t=190728)

Screwing around with pon/poff, wvdial, gnome-ppp, etc. is just a waste of time unless your modem is Linux-compatible.  Just cause lspci saw it doesn't mean it is.

You're not gonna like this, but the most straightforward method will probly be scrounging up a used or buying a new external serial modem, and using your laptop's serial port to connect.  Don't have a serial port?  Then you'd have to buy a serial-to-USB cable also, another expense and I'm not sure that all of them work as one would expect.

And if you're used to broadband, dial-up will seem like water torture.

Googled 82801CA
[http://www.linuxcompatible.org/Modem_Driver_DownloadInstallation_-_82801CACAM_AC_97_t31198.html](http://www.linuxcompatible.org/Modem_Driver_DownloadInstallation_-_82801CACAM_AC_97_t31198.html)
Other links didn't look very promising.  Some are old, back in 2003 or thereabouts.  Sometimes someone figures out a hack for a winmodem, then a new kernel comes out and the winmodem stops working again...

---

### Post by sw1995 on 2007-07-10
Thanks for the feedback!

Through some kind of combination I actually got it to work. I am incredibly proud of myself:)

So, it works for now--hopefully I will not have to rely upon it too long.

And you are right, dial-up is murder. Plain and simple.

S

---

### Post by Papi-KB7VGW on 2007-07-10
Congratulations on getting your modem up and running.  Pretty soon you will be comfortable hacking into everything.

---

### Post by Bartender on 2007-07-10
It'd be great if you could explain how you did it...I think a lot of lappies use similar hardware.

---

