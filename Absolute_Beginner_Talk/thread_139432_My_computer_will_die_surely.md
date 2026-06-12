---
title: "My computer will die surely"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-04
Because I cannot access internet on my Huawei Wireless modem while in Ubuntu, I have to keep shuttling between Ubuntu and Windows all the time. Whenever I want internet access I restart Windows.

This is slowly but surely killing my computer because of too many restarts. The modem has no driver for linux.

What is the remedy?

---

### Post by qwazert on 2006-03-04
Do you turn you computer off completely to restart it?

If you're simply rebooting, this should have no tangible effect on its life-span.

---

### Post by AtinLango on 2006-03-04
I reboot.

---

### Post by yatesDELTA on 2006-03-04
a waste of time in my opinion. couldnt so,meone convert it for you? i htink its a matter of reversin codes. i have absolutly no idea but i reckon its possible

anyways my computor is dying without anyhelp from me

---

### Post by soonindallas on 2006-03-04
what is preventing you from using your modem ?

---

### Post by mips on 2006-03-04
What "Huawei Wireless modem" do you have ???

You dont require drivers to talk to a wireless access point, it's ethernet.

You do however require drivers for your wireless card (client) if that is what you are talking about.

Maybe you should elaborate a bit more as to what hardware you are using and what the problem is because currently we are just guessing based on the little information you have given.... Surely you cannot expect people to help you based on the information you supplied ??? When i say to you, "My Toyota car is not working" would anybody know what the problem is ?

---

### Post by AtinLango on 2006-03-04
I use a Huawei Wireless modem which connects from USB on PC to DB9 COM on the wireless handset. I imagine the modem is inside the wireless handset.

The handset came with a CD for Windows driver only, thats why I use it in Windows without any problem.

When I try configuring the modem in Ubuntu, it cannot be detected. Ihave tried using wvdial as well as the ppp configuration tool in GNOME.

I had posted this problem here sometime ago but I seem to be stuck with it at the moment.

Thanx in advance.

---

### Post by mips on 2006-03-06
**[COLOR="Red"]What wireless handset are you using, Brand & Model PLEASE ????[/COLOR]**

Here is a list of possible devices made huawei:
[http://www.huawei.com/mobileweb/en/products/browseProductCatalog.do?id=38](http://www.huawei.com/mobileweb/en/products/browseProductCatalog.do?id=38)
[http://www.huawei.com/mobileweb/en/products/browseProductCatalog.do?id=39](http://www.huawei.com/mobileweb/en/products/browseProductCatalog.do?id=39)
[http://www.huawei.com/mobileweb/en/products/browseProductCatalog.do?id=37](http://www.huawei.com/mobileweb/en/products/browseProductCatalog.do?id=37)
[http://www.huawei.com/mobileweb/en/products/browseProductCatalog.do?id=44](http://www.huawei.com/mobileweb/en/products/browseProductCatalog.do?id=44)

Other companies also implement their chipsets so it might be a diffreent brand.

You might wanna look at some of the links in this post [http://www.ubuntuforums.org/showthread.php?t=109083](http://www.ubuntuforums.org/showthread.php?t=109083)

---

### Post by AtinLango on 2006-03-06
Handset is HUAWEI ETS2077

---

### Post by AtinLango on 2006-03-06
Since I downloaded and installed Ubuntu, I have really enjoyed it apart from this problem of no internet. I have done some reading on ndiswrapper and I can see a remote ray of hope in it.

It is useless for me at the moment to download the sources for ndiswrapper since the compiler is not yet installed anyway. Where can I download the .deb file and dependencies for ndiswrapper.

---

### Post by o_fortuna on 2006-03-06
[QUOTE=AtinLango]Since I downloaded and installed Ubuntu, I have really enjoyed it apart from this problem of no internet. I have done some reading on ndiswrapper and I can see a remote ray of hope in it.

It is useless for me at the moment to download the sources for ndiswrapper since the compiler is not yet installed anyway. Where can I download the .deb file and dependencies for ndiswrapper.[/QUOTE]
[http://packages.ubuntu.com]("http://packages.ubuntu.com")

For all of your packaging needs! :)

[http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils]("http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils") That's what you need for ndiswrapper. Hope you can get this working.

---

### Post by AtinLango on 2006-03-07
I have tirelessly downloaded ndiswrapper and its dependencies, and installed them on my laptop.

I have also installed the modem driver from Windows into Ubuntu using ndiswrapper. The driver installation seemed so successful at every stage that my spirits got so high. I expected after restarting the computer that I would be able to access internet.

But this thing has got me stumped! My spirits are dampened. I think I may forget about internet using Ubuntu with my modem.

---

### Post by mips on 2006-03-08
You DON'T need ndiswrapper as it is not a wireless card.

Here is a procedure to get the Huawei ets2077 to work under Suse:
[http://www.linuxforums.org/forum/peripherals-hardware/36506-huawei-ets2077-fixed-wireless-terminal.html](http://www.linuxforums.org/forum/peripherals-hardware/36506-huawei-ets2077-fixed-wireless-terminal.html)

You will probably have to make some changes for Ubuntu.

Once you have it figured out write up a guide and post it here.

---

### Post by AtinLango on 2006-03-08
I got the following Instructions from the link you provided:

****************
1. Update the hwinfo, udev and mkinitrd packages. You can find them here:
[http://ftp.gwdg.de/pub/linux/suse/people/agruen/i386/](http://ftp.gwdg.de/pub/linux/suse/people/agruen/i386/)
2. Download the 9.3 kernel from [http://ftp.gwdg.de/pub/suse/i386/9.3...4-20a.i586.rpm](http://ftp.gwdg.de/pub/suse/i386/9.3...4-20a.i586.rpm)
3. Create an executable script file called /etc/hotplug/usb/ti_usb_3410_5420 and paste the following:
Code:
****************

I have tried and tried to no avail.

1. First the link in 1 above does not exist.
2. Second, I think I have the latest (?) version of the kernel. Even when I go to the link in 2 above, they are asking me to download the kernel which I already have.
3. Third, having got lost, I tried to do 3 above. but it is not helping.

---

### Post by deBaas on 2006-03-08
[QUOTE=AtinLango]
This is slowly but surely killing my computer because of too many restarts. The modem has no driver for linux.[/QUOTE]

BS: rebooting doesn't kill any computer if you normaly shut-down and start up.

---

### Post by AtinLango on 2006-03-08
[QUOTE=deBaas]BS: rebooting doesn't kill any computer if you normaly shut-down and start up.[/QUOTE]

Even when on average I reboot over 15 times in a day?

---

### Post by mips on 2006-03-09
[QUOTE=AtinLango]I got the following Instructions from the link you provided:

****************
1. Update the hwinfo, udev and mkinitrd packages. You can find them here:
[http://ftp.gwdg.de/pub/linux/suse/people/agruen/i386/](http://ftp.gwdg.de/pub/linux/suse/people/agruen/i386/)
2. Download the 9.3 kernel from [http://ftp.gwdg.de/pub/suse/i386/9.3...4-20a.i586.rpm](http://ftp.gwdg.de/pub/suse/i386/9.3...4-20a.i586.rpm)
3. Create an executable script file called /etc/hotplug/usb/ti_usb_3410_5420 and paste the following:
Code:
****************

I have tried and tried to no avail.

1. First the link in 1 above does not exist.
2. Second, I think I have the latest (?) version of the kernel. Even when I go to the link in 2 above, they are asking me to download the kernel which I already have.
3. Third, having got lost, I tried to do 3 above. but it is not helping.[/QUOTE]


I said you would most likely have to make changes for Ubuntu and not follow the guide by the letter seing it is for Suse !

Ignore the links as they are for Suse. As far as I know the Ubuntu Kernel is up to date (The suse one is ver 2.6.11.4-20a) see if your version is later.
Check your versions of hwinfo, udev and mkinitrd packages and update them if newer versions are available.
Follow steps 3&4

---

