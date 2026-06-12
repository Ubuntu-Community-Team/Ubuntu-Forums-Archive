---
title: "Install ubuntu on powermac g5 that can't boot from cd or usb"
date: 2013-02-10
forum: Apple Hardware Users
---

### Post by Jephuff on 2013-02-10
Hello,
I've been desperately trying to install Ubuntu onto a old Power mac G5. The problem I am having is that I can't get the install to boot from CD or USB. 

What I was thinking, but very unsure if it's possible, was to install Ubuntu onto a hard drive using my other computer and then putting the hard drive into the Mac. I currently have a windows 8 desktop but would definitely be willing to dual boot Linux if I need to. 

I also tried too net boot, but with no success. 

I can provide any specs or details if some one thinks this is possible, and any help would be greatly appreciate!

Thank you,
J

---

### Post by venividivici24 on 2013-02-11
Make sure that you downloaded the powerpc version of Ubuntu: [https://wiki.ubuntu.com/PowerPCDownloads/](https://wiki.ubuntu.com/PowerPCDownloads/)

 If you've already done that, make sure that you burn your disc correctly, I use a program call ImageBurn on Windows. Instructions can be found on the internet on how to burn a disc image.
Insert your disc into your mac and right after you've turned it on, press and hold the "c" key on your keyboard. It should boot into the cd and come to a yaboot prompt. Then, press "Tab" to list the options for booting, you'll want to select a 64 bit option.
 If the problem persists, try to download the "Alternate" install disc and see if that works. If that still doesn't work, you can always try Debian. Here is an excellent install guide: [http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-i.html](http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-i.html)

It would also be helpful if you posted your specs....

You might also check out the Ubuntu PowerPc FAQ and the Ubuntu PPC Known Issues.

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

I hope this helps,
  -veni vidi vici

---

### Post by Jephuff on 2013-02-17
thank you!
I had done everything except use the "Alternate" install disc" but it also could have been something else I did. I'm still having a bit of trouble booting, but I just installed it a couple minutes ago so hopefully I will be able to figure this one out. 

Thanks again!

---

### Post by rfetch on 2013-03-26
Did you get it to work, I'm curious. I was having the same issues, now I'm stuck at the terminal.

---

### Post by venividivici24 on 2013-03-27
If you've made it to a terminal, that's great news. Do you have Xorg installed? Or does it just boot into the terminal? What happens when you enter:  startx  ? 

The MintPPC forums are a great resource for Powermac related issues with Linux, you might check there for a solution to your problem. If you have an Nvidia graphics card, a likely problem is linux thinks you have a monitor plugged into a "ghost" port, and isn't starting the gui correctly; or you could try plugging in your monitor to the other DVI port, that helped some people. Here is a great thread for fixing the "ghost port" problem:
 [http://mintppc.org/forums/viewtopic.php?f=15&t=810&start=10](http://mintppc.org/forums/viewtopic.php?f=15&t=810&start=10)
 Scroll down to the "Step by Step Guide" and follow the instructions.

I hope this helps you,

  -venividivici24

---

### Post by BenTin2 on 2013-04-05
Hi PPC peeps - I'm working on Ubuntu installs on a late 2005 G5 with nvidia and airport card -  I just went through some difficulties in getting Ubuntu running - tried alpha/beta 13.04 of course, but that appears to require more digging than I can handle right now... no luck either with 12.10. after many days of frustration and experimentation, I finally found that my key problems surrounded the airport card and my SATA plugin- I'd install everything happily, but when it came time to boot off the hard drive, would get a text error about "bootstrap stage 2" - that was remedied by simply connecting the hd to the *other* sata plug, though holding option at boot to change boot drive might work too. The airport card was also a hangup - I was unable to get 12.04 to boot up initially until I unplugged the airport card from the motherboard - it's still not working, but the B43 driver install instructions floating around on the net look promising. Need to figure out how to make an image of existing system so I don't have to do the time-suck of reinstalling and updating each time I kill off the GUI by messing with boot scripts.. .  anyone done this? Or gotten 13.04 to work?

---

