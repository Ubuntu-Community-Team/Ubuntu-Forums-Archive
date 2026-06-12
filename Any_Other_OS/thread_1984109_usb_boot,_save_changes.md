---
title: "usb boot, save changes"
date: 2012-05-21
forum: Any Other OS
---

### Post by penguinslide on 2012-05-21
Hi, hope this isn't a repeat thread, I have searched the forum more than a few days.

The problem is: My son is booting mint from a school laptop (windows) and is loving the speed  of linux off a usb on the lightweight pc. 

What he isn't enjoying is having to re entering wifi password and key chain password on every startup. Would also like to add software.

Is there a way to have it working less as a live cd and actually save changes?

 I chose mint because of the pre installed flash etc, if I need to use a different distro on the usb to achieve saving changes, thats fine too, am familiar with a few of them now.

---

### Post by coffeecat on 2012-05-21
In Ubuntu, if you use the app startup disk creator you can create a bootable USB with persistence. Settings, installed apps, personal files are saved. You can only use an Ubuntu ISO with Startup disk creator - it doesn't work with a Fedora ISO for example - but if you are using the Ubuntu-based version of Mint (not Debian based), see if startup disk creator is included.

If it isn't (I haven't used Mint for some years, so I don't know), one alternative would be to use Ubuntu and install the package ubuntu-restricted-extras which should give you most, if not all, of what you get out of the box in Mint.

---

### Post by penguinslide on 2012-05-21
Thanks Coffeecat, will try what you suggest.

---

### Post by penguinslide on 2012-05-22
Couldn't find how to do it with ubuntu, but found this, looks promising:

[http://www.pendrivelinux.com/create-a-linux-mint-8-usb-flash-drive-from-cd/](http://www.pendrivelinux.com/create-a-linux-mint-8-usb-flash-drive-from-cd/)

---

### Post by coffeecat on 2012-05-22
> **penguinslide said:**
> Couldn't find how to do it with ubuntu, but found this, looks promising:

[http://www.pendrivelinux.com/create-a-linux-mint-8-usb-flash-drive-from-cd/](http://www.pendrivelinux.com/create-a-linux-mint-8-usb-flash-drive-from-cd/)

You couldn't find how to do it with Ubuntu? I don't understand you. Startup disk creator (package usb-creator-gtk) comes as standard with Ubuntu. Your link simply tells you how to install usb-creator-gtk to Mint in order to run it. Beware that your link is for an obsolete version of Mint, although I guess you should be able to run usb-creator-gtk in the latest version of Mint.

Good luck with that.

---

### Post by drawkcab on 2012-05-22
I'm pretty sure that usb-creator-gtk works with Mint .iso files--though not Mint Debian Edition .isos obviously.

I think the problem here is that you would need to boot into a live session of Ubuntu in order to create a persistent usb install of Mint if that makes sense.  In other words, you would need two usb drives--the first dedicated to persistent install and the second to boot into a live session of Ubuntu so as to create the first.

---

### Post by penguinslide on 2012-05-23
Sorry Coffeecat, I'm an idiot, or at least was last night. I should have re read your reply, misunderstood what you had said in the first line, although re reading it now I can't see how I could have, you made it clear enough. 

Thanks for the Suggestion  Drawkcab, burning iso's is about all my blank discs are good for these days, so may as well do it that way

Mint 11 which I'm currently using has startup creator, am downloading 32 bit mint 12 to suit sons laptop now. Will let you know when I have it working.

---

### Post by coffeecat on 2012-05-23
Actually, another thought, and a caveat about a live USB created with startup disk creator. A live USB with persistence created with startup disk creator will do everything that you want but there are a couple of drawbacks. The user account will be called ubuntu in Ubuntu and mint in Mint (:) !) and if you choose try Ubuntu/Mint it will boot straight to the live desktop with no login - mainly because there is no password. Which leads to the main point - you can elevate to sudo rights without a password. This means that, in a terminal:

```
sudo <insert-dangerous-command-here>
```

... will execute without a password prompt and without delay. That could be a drawback. (Masterful understatement!)

Another alternative would be to create a conventional installation on the USB stick - this is quite possible - but this needs more planning. Points you would need to consider are:

[list]
[*]If you are installing to a flash drive, you would probably want to avoid premature failure from uneven wear by installing to a non-journalled filesystem such as ext2 and by not having a swap partition - both of which introduce their own potential problems. It could be that with newer flash devices, with wear-levelling built into the firmware, this is no longer necessary, but I'm a bit out-of-date and hazy on this point.
[*]You would need to ensure that grub is installed to the mbr of the USB device and not the hard drive of the machine you are using for creating the installation.
[/list]
Both the above would need the use of the "something else" (used to be called advanced) option in the installer, so if you need help with this, do post back.

---

### Post by penguinslide on 2012-05-24
Drawkcab, your idea was a great one, had forgotten how slow working off a live cd was, especially with heavy distros. 

I have had many installs and experimentation on a 4gig usb, I haven't had any successful mint persistent installs on the usb, on boot kept coming up with an error message  (sorry can't remember it exactly, should have taken notes) under some details mentioning Debian, was sure I was careful to download non debian as recommended for usb boot, don't know why that is.

I have successfully got a 32 bit ubuntu 12.04 to work fine, but does that shaded window thing if I try to do more than one thing at a time. I will continue to play around with it. Have just read on a web page mint likes to boot off a usb bigger than 4 gig, so will wait for a 16 gig to arrive via ebay before trying mint again.

Coffeecat, yes I won't be showing my son the awesome power of the terminal for many years yet! ;) Yes I found that info on uneven wear on usb leading to failure in my surfing around, I did notice that ext2 is used when the persistence file is created with start up disk creator. 

The usb boot won't be used for serious data use so a failure of this nature won't be a disaster. I believe the usb boot will be short term, just sons first step towards doing a duel boot on the netbook. 

Thanks Drawkcab and Coffeecat for your help.

---

### Post by drawkcab on 2012-05-24
Cool, glad its working out.  Yeah, Mint needs more room to function and setting up a dual-boot system would be way better than booting from usb.

---

