---
title: "New to linux, install problems"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by zephyr3.14 on 2007-03-20
Hello,

This is the first time I have tried to install linux. I have used it to some extent in labs at my uni but have never tried to run it at home.

The laptop I am working on is here [http://www.newegg.com/Product/Product.aspx?Item=N82E16834220118](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220118)
graphics card:
ATI Mobility Radeon X1700

I downloaded the kubuntu 6.10 DVD iso from the website and burned it to disk. When I loaded it it asked if I wanted to install/boot from liveCD. I tried this and it started loading (like it has done on other computers when I just want to run off the liveCD (with same disc)). Then it hangs.. and after about 10 minutes I shut it down and tried it again, with the same results.
Then I decided to try a different install choice from the CDs boot menu. It was the OEM install. I was able to get through all the menus and install it from there. Then I reboot hoping that everything worked out.
When it boots I get the standard load screen with the little scroll bar and then everything stops and soon after a screen comes up that looks like nothing I've seen before, after playing around a bit I figured out it was a warped image of the login screen (it was at a 45 deg angle and wraped around the screen periodically about 10 times). I was able to login just using the keyboard and guessing. After loging in the screen stayed warped so I restart again.

Now I boot up in recovery mode and try to update my graphics drivers only to find out that my ethernet card is not recognized and I cannot connect to the internet via wired or wireless. 

I was wondering if there was a way to fix either or both of these problems?

Thank you for reading this far. I would really like to get linux to work.

Here is my output from lspci

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71d5
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
06:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

the rest is cut off and I have no way to copy and paste from the comp (no ethernet = no ssh).

any help would be greatly appreciated!

Thank you!

---

### Post by gingin on 2007-03-20
Welcome, on that mater it is a lot of information [http://ubuntuforums.org/tags/index.php/ati/](http://ubuntuforums.org/tags/index.php/ati/)

---

### Post by zephyr3.14 on 2007-03-20
I've looked at many of those fixes. And tried editing my video diver in my xconfig file from 'vesa' to 'ati' to no avail.
It seems that some of the fixes require acess to the internet to get new packages etc. I was attempting to fix the ati problem when I realized that niether of my network cards work.

Does anyone have any idea how to fix the network card problems?

Thanks!

---

### Post by caintona on 2007-03-20
try using envy.

I have used it for a couple of months and works fine on getting my ati card to work

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

however I cannot get the beryl to work with it.  I think its just a matter of the ati drivers though.

---

### Post by zephyr3.14 on 2007-03-20
Thank you, I will try that. In order for it to work though I seem to need access to the internet.

Does anyone have any ideas on how to make either NIC work?

Thanks!

---

### Post by gingin on 2007-03-20
Try this is it really god way to solve graphic card problems
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

---

### Post by zephyr3.14 on 2007-03-20
Thank you! 

Don't you need internet access to use apt-get? I will try this as soon as I can figure out how to get my NICs to work or somehow get connected to the internet in linux.

Does anyone know how to get either of my NICs, wired OR wireless to work? Thank you!

---

### Post by dstew on 2007-03-20
I see your ethernet controller on your lspci list. What do you see in the network manager?

---

### Post by zephyr3.14 on 2007-03-20
How do I get to network manager? Sorry, I'm new to this. Thanks.

---

### Post by dstew on 2007-03-21
Its in the software menu, usually under system-->networking, or something like that.

---

### Post by zephyr3.14 on 2007-03-21
I can't get to any menus because of the video issue which I cant fix until I can get the internet to work. I am currently only able to boot from the recovery mode and only have command line. Is there any way to get to it from the command line?

Thank you!

---

### Post by dstew on 2007-03-21
Sorry I forgot you couldn't see it. If you have a way to access the internet from another computer, and can transfer files to your linux computer, you can download application packages and transfer them to your linux computer, then unpackage and install them using the command **dpkg**. You don't absolutely have to use **apt-get**.

If you want to continue to try to get on-line with the command line only, try the command 

**ifconfig -l**

This should list your interfaces.

---

### Post by zephyr3.14 on 2007-03-21
I have a windows comp with internet and a usb thumb drive that I can put packages on. Where can I get packages online? and which ones should I get first (to resolve the network issue)?

ifconfig -l returns:
ifconfig: option '-l' not recognized.
ifconfig: '--help' gives usage information.

ifconfig returns:
lo  Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets: 0 (all others are 0 too)
TX packets: 0 (all others are 0 too)
RX bytes: 0 TX bytes: 0

Thank you!

---

### Post by dstew on 2007-03-21
You can find the downloadable individual packages here:

[http://packages.ubuntu.com/edgy/](http://packages.ubuntu.com/edgy/)

I think you can get your internet connection going by doing some configuration. It looks like most of the people that successfully get ATI graphics working are using **apt-get** to install the packages. I couldn't find out how to do it by downloading and installing with **dpkg**.

Since you have two problems at once -- no internet, and no video -- you might consider re-installing with a different distribution.

But, if you want to carry on, we need to get your internet working. Please list your /etc/network/interfaces file. We can edit this file, or use **ifconfig**, to create the parameters for your internet connection, and then use **ifup** to start it.

---

### Post by zephyr3.14 on 2007-03-21
I would like to get this to work.. If at all possible. I like the Ubuntu interface and it seems user friendly enough once it gets up and running (from what I've seen on other computers).

When I run
cat interfaces
I get:
(comments)
auto lo
iface lo inet loopback

P.S. what other distribution would you recomend? In our physics labs at my uni we run OpenSUSE, is that any good?

---

### Post by dstew on 2007-03-22
What has happened is that you are booting a very minimal "recovery mode" system, and it does not load the ethernet driver at startup. It would be difficult to create a working system from recovery mode, and I am not sure I can help you much at this point.

You might try a different Ubuntu distribution, like 6.06 Dapper, or maybe use an alternate install disk.

Other linuxes, like OpenSUSE, are good also.

---

### Post by i.am.canadian on 2007-03-22
Hi there, I'm really not sure what to suggest here, as I'm a bit of a noob myself, however you could try something.  If you reinstalled without installing a graphical desktop (ie GNOME KDE XFCE).  This way you would boot a full system, but just to the command line.

My logic being if you can't get the internet to work because you have to boot into a recovery mode to deal with your graphics issue, you should be able to boot into a non-graphical (but fully featured mode) with internet access to do the same thing....I hope.

Once you had addressed your graphics issue you could then simply enter ```
sudo aptitude install kde
``` to get the graphical user interface afterwards.

I don't know if that will help at all, but it might be worth a try if you're willing to take the extra time.  On a side note, OpenSUSE was my second choice for a linux distro, though it is obviously different in quite a few ways.

Best of luck!

---

### Post by zephyr3.14 on 2007-03-22
I tried openSUSE 10.2 and it worked perfectly the first time (fixed both problems). I think I'll stick with that until Feisty comes out and stableizes (the herd 5 install didn't fix the problem). Thank you all for your support and suggestions!

---

