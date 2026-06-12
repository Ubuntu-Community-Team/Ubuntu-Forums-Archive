---
title: "Belkin USB Network Hub"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by soaklord on 2007-08-17
I have a Belkin USB network hub that requires software to work over the network ( [http://www.belkin.com/support/article/?lid=en&pid=F5L009&aid=7709&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5L009&aid=7709&scid=0) ).  Is it possible to get this to work on ubuntu.  

My final desired setup atm is to get my Dell 8000 running only on Ubuntu on a wireless network.  I have a desktop that will wire to the wireless router that I also am looking to set up fully on Ubuntu and a third machine (laptop) running XP and possibly dual boot.  I want all three to access the same DVD burner, Scanner, Printer, and 2 external hard drives.  Currently, I can do this with the Belkin USB hub, though access is one machine at a time only.  

I am new to networking, so don't know if it would be better to have the wired desktop become a server for all of the above, (essential is that I can get ink levels reported back to the machines) or if there are other better ways to do it.

---

### Post by gobbles414 on 2007-08-17
Most routers can be configured via a web browser. You should be able to find a procedure for this either in your instruction manual, or in an article on the Belkin website. You'll be looking for something similar to this: [http://192.xxx.x.x](http://192.xxx.x.x)

EDIT: I don't know if this will work for a USB hub that has a network interface. But it is worth a try.

---

### Post by soaklord on 2007-08-17
As I recall, this did not come with a configuration page/specific ip address.  I can double check when I get home, but I don't recall a 192.xxx.x.x for this one.  Rather, it runs on software that makes it act like a usb hub attached to the computer even though it is working over the wrouter.

---

### Post by soaklord on 2007-09-20
After trying like mad to get this thing to work, I can not find anywhere that will allow access without the proprietary software.  The IP address on the network is the address for the hub itself and the hard drives and printer can be seen by going to the ip address, but there is no available access through that ip.

---

### Post by ImNeat on 2007-12-28
Just picked up a Belkin USB network hub myself. 

The hub is set for DHCP by default so it can be seen as an attached device in a router's configuration.  Pointing directly to the device's IP using a brower shows information about the device, including what peripherals are attached to it, but there is no way to connect to them from this prompt.

So far as I can tell the only way to connect to the attached devices is through Belkin's software.  The software can be installed from the CD for Windows XP/Vista machines and OS X up to version 10.4.  The software installs the SXUPTP driver maintained by Silex.

We need a linux version of this driver...

Anyone else have any additional findings?

---

### Post by kimme on 2008-01-12
I would also like any information on how to get this network usb hub working with ubuntu. Have anyone tried to install the CD with the wine emulator?

---

### Post by eolson on 2008-01-12
Not the same thing,  but I have a Belkin USB wifi for my laptop.  The Windows driver installed fine using Ndiswrapper.   Ndis says invalid driver,  but it works fine.

---

### Post by Woozyerdaddee on 2008-02-21
Here was the response I got:

XXXXXXX, we understand that you require Linux driver for Belkin Hub F5L009.

We currently do not have Linux drivers for F5L009, however when we release the drivers for this product, they would be posted at : [https://www.belkin.com/support/article/?lid=en&pid=F5L009&aid=8547&scid=0](https://www.belkin.com/support/article/?lid=en&pid=F5L009&aid=8547&scid=0)

We regret the inconvinience this might cause.


Yeah...thanks for NOTHING!

---

### Post by jserink on 2008-03-03
Hello All:

I'm not Ubuntu user but am on Gentoo (boo, hiss, hiss from the studio audience) but this was the only forum I could find on this product. I bought it to see if I can make it do what Digi's USB/Anywhere can do, that is, give my windows virtual machines access to USB ports, primarily so that I can run windoze SW that requires USB security keys.

Comments about the unit:
1. Its aesthetically lovely,
2. The documentation is below crap level. The pdf manual on the CD is even worse so don't get your hopes up,
3. If you screw things up, you need to press down the reset button for 10 seconds, else it doesn't quite reset.

How to set it up:
1. Get your grandmother's XP box and load the crap SW onto it,
2. Bring up the silly app that comes with it and find the damn thing's IP address(its dhcp by default),
3. Once you've got that, head back to your Linux box and bring up a browser,
4. Pop the IP into the address bar and you are there,
5. There is no user name, but the password is nothing, just press submit,
6. First thing you need to do is got over to the System Information to password and get something in there
that is a little bit better than a blank,(don't be fooled, the security selection under network settings is for IP filtering, not access to the device setup),
7. Now that we are in network settings, let get a static IP in there,(note, after you hit submit it will take ~10 second before it starts answering pings),
8. Ok, now the windoze box shows the unit with the new IP but my KVM session running XP can't see the damn thing AND, there is no way to tell this brilliant windoze driver the static IP of the unit....call tech support and make sure NOT to mention linux,
9. Ok, after 10 minutes,...its solved
10 Trick for new players here...
In the windoze driver, when you click Configure General (click on the word general), you'll get a "Network USB Hub Settings" dialoge with a little window showing the hubs you are connected to, which is of course, empty. Now, if you click on refresh options, THE TRICK FOR NEW PLAYERS IS HERE. They specifically ask for the broadcast address of the subnet your network hub is on....DON'T BE FOOLED! You're suppose to enter the IP of the hub not the broadcast address like the dialog tells you. When you do, you can see the devices.
Nicely enough, I plugged in one of the rainbow security keys and she came up straight away.

Kudos to the board here, got the idea to check the DHCP IP from the board. if you're using this thing the way I am, you're away. If you actually wanted to use this thing under linux to give you USB over IP, you're out of luck. Even Digi's USBanywhere has only windoze drivers.

Cheers,
john

---

