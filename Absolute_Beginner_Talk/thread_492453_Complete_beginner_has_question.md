---
title: "Complete beginner has question"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by ShadowdogKGB on 2007-07-04
Hi all, I've been waiting for the time when Linux would be as easy to install as Windows. I've played around with earlier versions but it was too problematic and time consuming for me. I do home computer repair here in PA. I would love to have an alternative that I could offer customers.

My question is how does this Ubuntu get along with the latest hardware (motherboards, video cards etc.)
Thanks.
Jay

---

### Post by Jimmyfj on 2007-07-04
As far as I know must new hardware comes with excellent Linux support in drivers. I haven't heard of any issues other than a few wireless network cards. All in all Linux is very well supported by most hardware products

---

### Post by Trevster on 2007-07-04
Try the live CD and see how things work.

---

### Post by Antonio44 on 2007-07-04
For the most part there is a driver for just about everything. If there isn't you can use ndiswrapper to use the windows driver. Some things are better supported then others. Like Broadcom Wireless cards are notorious for being a problem and ATI and Nvidia cards can sometimes cause display issues. But for the most part there isn't any problems. 

A.

---

### Post by Malibu Illusion on 2007-07-04
Things have come a long way in a few years; Ubuntu 7.04 Feisty Fawn does have excellent hardware support right out of the box, including the ability to turn propriatory drivers for devices such as ATI or nVidia GPU units on or off from a menu.

There are definitely hardware issues with Wi-Fi devices, though.  Many times, people have to resort to using the Windows drivers with an application called ndiswrapper.  Some bleeding-edge devices just won't run under Linux, period such as the Abit Airpace WiFi PCI-E card.

Overall though, support is good generally, particularly for "generic" components that are pretty standard.  Anything absolutely brand new though you may run into problems with.

Take care.

---

### Post by smoker on 2007-07-04
> **ShadowdogKGB said:**
> Hi all, I've been waiting for the time when Linux would be as easy to install as Windows. I've played around with earlier versions but it was too problematic and time consuming for me. I do home computer repair here in PA. I would love to have an alternative that I could offer customers.

My question is how does this Ubuntu get along with the latest hardware (motherboards, video cards etc.)
Thanks.
Jay

most popular linux distros are great at hardware detection, and getting better all the time, and the installation is usually far easier than installing windows. it is getting customers that are used to windows to try linux that will be your biggest problem. be prepared for a lot of tech calls.

that said, it is always good to have a linux machine set up with beryl (compiz fusion) running, the customers that have heard of linux 'may take a chance'

best of luck.

---

### Post by robertc36 on 2007-07-04
> **smoker said:**
>  it is getting customers that are used to windows to try linux that will be your biggest problem. be prepared for a lot of tech calls

I second that. Getting the not technically minded used to the architecture could be a problem .

---

### Post by johnc4510 on 2007-07-04
ShadowdogKGB, you should also get in touch with the PA Loco Team here:

[http://ubuntuforums.org/forumdisplay.php?f=228](http://ubuntuforums.org/forumdisplay.php?f=228)

They would be very interested in helping you offer an alternative operating system.

---

### Post by Wiebelhaus on 2007-07-04
once you get by the learning curve , you'll never look back bro , for normal end user this OS is tailor made (For your customers) internet , multimedia , pictures , music , simple documents , imaging software , videos , no maintenance needed if you don't want , you can use and old version of ubuntu as long as you want....on the flip side updates are easier then windows , three agreeing clicks and your done , no fuss or BS , there's much more as well.

---

### Post by Wiebelhaus on 2007-07-04
also , you could set it up in such a fashion that would virtually make it impossible for them to kill it , unlike windows.

---

### Post by ShadowdogKGB on 2007-07-04
Right on, thanks everyone for the input. What kind of problems come from Linux being able to read, say, MS Word and other office programs? I'm going to put it on a machine here and see how we do.

---

### Post by kejava on 2007-07-04
Hi ShadowdogKGB,

For the most part, OpenOffice (OO) can open most MS Word, Excel, and PowerPoint files just fine.  However, I've seen some formatting issues with some Word files.  Things like margins, headers/footers, and fonts can sometimes be a bit off after being imported into OO.

If you're looking for other alternatives to OO, there is also Abiword, gnumeric, and planner (similar to MS Project).  You can install them from Synaptic Package Manager (System --> Administration).

---

### Post by ShadowdogKGB on 2007-07-08
Okie dokie. I put it on an older machine here. I booted from the Ubuntu CD. Everything came up just fine for all I can tell. However, it seems dreadfully slow. The machine I put it on has an AMD Athlon 1 ghz cpu and 256mb of 168-pin ram on an old Gigabyte 7ixe4 motherboard with an older 20gig hard drive. Looking at the hardware manager I can see that it has correctly identified the chipset and the other devices. Did I miss something or is this machine not Linux ready?

Thanks.

---

### Post by Vague on 2007-07-08
> **ShadowdogKGB said:**
> Okie dokie. I put it on an older machine here. I booted from the Ubuntu CD. Everything came up just fine for all I can tell. However, it seems dreadfully slow. The machine I put it on has an AMD Athlon 1 ghz cpu and 256mb of 168-pin ram on an old Gigabyte 7ixe4 motherboard with an older 20gig hard drive. Looking at the hardware manager I can see that it has correctly identified the chipset and the other devices. Did I miss something or is this machine not Linux ready?

Thanks.

Two things I can think of.  1) If you're booting from the LiveCD, it's going to be slow.  It will be much faster once it's installed.  2) For older machines, you might be better off installing Xubuntu, which uses the lighter-weight Xfce desktop environment instead of GNOME.

---

### Post by ShadowdogKGB on 2007-07-08
How do I install it? First timer here.

ps. I download Ubuntu 7.04 and made a bootable cd.

---

### Post by gary0 on 2007-07-08
When running from the live cd, double click the install icon on the desktop and away you go...

Have fun,
Gary.

---

### Post by kejava on 2007-07-08
There should be an "install" icon on the desktop.  Double click it and follow the instructions.  If it's not there ... that could be an issue.

Sorry, garry0.  Didn't see your post.

---

### Post by forrestcupp on 2007-07-08
If you haven't installed it to the hard drive yet, you'll notice a huge difference when you do.  However, 256 megs of RAM isn't much, so if it's still slow, you may need to download and install Xubuntu instead.

One thing you could try, though, is the Restricted Drivers Manager.  Sometimes installing proprietary video drivers improves the responsiveness.

---

### Post by Skidpad on 2007-07-08
[**Here**]("https://help.ubuntu.com/community/GraphicalInstall") is the link to the Graphical Installation procedure.

As others have said, boot the LiveCd to the desktop, double-click the Install button, and then follow the procedure in the link I posted.

Welcome to the community!

---

### Post by ShadowdogKGB on 2007-07-08
Excellent. I did the install and to my amazement it recognized everything...even the network connection. Very very impressive!

But alas all things are not perfect. If I could get this thing to run Yahoo messenger, AOL instant messenger and the other chat programs; and work with the common wireless routers from Lynksys and Belkin; and the popular printers from Lexmark and Hp,  I'd have a slam dunk.

ps. thanks for the help. I'll go over to the PA support forums now that I'm up and running. Thanks!

---

### Post by Matakoo on 2007-07-08
> **ShadowdogKGB said:**
> But alas all things are not perfect. If I could get this thing to run Yahoo messenger, AOL instant messenger and the other chat programs; and work with the common wireless routers from Lynksys and Belkin; and the popular printers from Lexmark and Hp,  I'd have a slam dunk.

As for the instant messenger, Gaim (or Pidgin as it's called now IIRC) can talk to just about every other im client out there. Including AOL, Google talk, MSN, Yahoo, and ICQ. At the same - sure beats having several chat programs loaded (available for Windows as well).

Wireless routers? I assume you mean getting the wireless card up and running, because talking to the router shouldn't be a problem once that is taken care of (and at least some Linksys routers are based on Linux...). Wireless is somewhat of a mess really, and I wish there was a foolproof way of making that work regardless of card. What you can do, as a first port of call, is to check this webpage:

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)

Lots of information there :) 

I haven't used a Lexmark in years, so I can't help you there. For HP, you should find a utility called HP toolbox installed in one of the menus. It can take care of most HP printers, whether low-cost inkjets or networked color-lasers.

Here is one link that might help you out a bit:

[http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters)

Epson, Canon, and Brother inkjets generally work well too. If you, or a customer, wants even better support for your printer (still not Lexmarks though), you can always download Turboprint from [http://www.turboprint.info/](http://www.turboprint.info/) It is not free software, but it's cheap and there's a demo available. And a whole lot cheaper to just buy turboprint than having to buy a Windows license :)

---

