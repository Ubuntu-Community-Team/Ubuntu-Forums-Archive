---
title: "Pendrive TUTORIAL help"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by astudentis on 2008-03-22
Hello, I am brand NEW to the world of Ubuntu. :roll: I have a few questions to ask:

1. Can i use this [tutorial to run ubuntu]("http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/") from a flash drive

2. When i boot from my USB key, would i need to install some drivers (i have dell xps 420, nvidia 8800GT, E8500)?

3. While i am logged in via the USB, and type persistent on log in will it save every setting on my usb?

4. When i am in ubuntu, can i use [this tutorial]("http://www.pendrivelinux.com/2007/03/23/ubuntu-edgy-beryl-installation/") to install beryl (while i am still running it on the USB)
- also what is "edgy" and does this install beryl on my usb?


If it seems like i am approaching this act of running ubuntu from usb and having the cool beryl effects installed on the usb as well totally wrong, please guide me as to how i should approach this.

Thank You very much


(also when i am running ubuntu from usb, can i save files that i worked on ie in open office text doc on my hard drive as opposed to the usb?)

---

### Post by talsemgeest on 2008-03-23
Ok I'll give this a try.

1. Yes, you should be able to. 
However I would suggest simply doing an install onto your usb drive, as this will give you the best results but you will have to reboot to get to ubuntu.


2. Any drivers you need should be installed automatically, with the possible exception of the graphics driver. With that you simply open up the "restricted drivers manager" and put a tick next to the graphics driver, which will then install it for you.

3. It certainly should.

4. Beryl has merged with compiz to make compiz-fusion. This is automatically installed in Ubuntu 7.10, so you don't have to worry about beryl, as all of the effects are already installed. 
4.5. Edgy is a name given to Ubuntu 6.10 (Edgy Eft). It is just like how people call ubuntu 7.10 (Gutsy Gibbon) Gutsy.

5. When you boot from the USB drive all hard disks should be mounted automatically so you should be able to save files anywhere you want.


I hope this helps and good luck with getting everything working! :)

---

### Post by alexsabree on 2008-04-10
I tried just simply installing onto my usb drive and it was a no-go. I also tried taht tutorial and when i choose to start ubuntu and save changes it doesnt work.. but if i boot it as a live cd it works fine.. but i cant save anything. :(

---

### Post by Zimmer on 2008-04-10
> **alexsabree said:**
> I tried just simply installing onto my usb drive and it was a no-go. I also tried taht tutorial and when i choose to start ubuntu and save changes it doesnt work.. but if i boot it as a live cd it works fine.. but i cant save anything. :(

It is unclear (to me, anyway) what you have exactly done. 
Did you first try the Qemu program method which requires you to run Qemu on a Windows host and 'switch' into Ubuntu on the USB drive?

Or have you attempted the installation of Ubuntu onto a USB drive and attempted to boot the computer with the USB device inserted ?

If the latter, then you must create the persistant image  and on Boot supply parameters to get it to boot with the persistent feature, otherwise it just works like a Live CD.

To boot persistently, at the boot menu press F6 to enter a custom boot option. Add persistent to the end of the boot string: add persistent to the boot options.

From the tutorial at [http://www.pendrivelinux.com/2007/09/27/making-ubuntu-710-casper-persistent/](http://www.pendrivelinux.com/2007/09/27/making-ubuntu-710-casper-persistent/)
it would seem that Gutsy now has that persistent feature somewhere in its menus. That means you should be able to boot the USB as a Live CD, find the feature in the menus when loaded and follow the instructions on scren to create persistence, then reboot using 'persistent' as one of the boot options.

I have a Knoppix install on USB that works in that way.

---

### Post by TJCIB on 2008-04-10
I used this tutorial [http://duggmirror.com/linux_unix/Run_Ubuntu_7_10_Gutsy_Gibbon_from_your_USB_Flash_Drive/](http://duggmirror.com/linux_unix/Run_Ubuntu_7_10_Gutsy_Gibbon_from_your_USB_Flash_Drive/)

as well as checking this out
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2)

Following the first one got my usb working fine.  I did use the text for syslinux.cfg file from the second link.  I made sure the text matched, I only had to change the word "persistent" in one place.  All it did was make it boot a little faster, don't know if it matters...

Be sure, when you are using the Persistent Mode that you don't just update everything without looking at the updates.  It will install kernel updates and such and then you could possibly lose persistent mode.

I hope it helps.

---

