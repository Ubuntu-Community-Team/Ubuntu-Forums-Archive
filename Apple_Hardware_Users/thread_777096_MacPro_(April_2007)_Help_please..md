---
title: "MacPro (April 2007) Help please."
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by MacPro8core on 2008-05-01
Hello everyone.

I am a complete newby to all this Linux stuff. A few weeks ago, i downloaded and installed the latest release of Ubuntu onto my MacPro. The installation completed with no problems at all. I quickly figured out how to get m second display working and then hit a stumbling block. No sound!

Anyway, i have just downloaded the newly released Ubuntu and decided to give the whole thing another go. Curiosity, more than anything else.

Last time i installed, i simply put the disc in the drive, formatted a spare HD and let the installer run. However, before i install this new release, i would like some expert guidance to make sure i do the whole thing properly. I would like to get as much of my Mac Pro hardware working as possible and would appreciate some step-by-step help with this.

A list of my hardware...

MacPro 3.0Ghz 8core (April 2007 model), 16GB RAM, ATI X1900XT, Airport Extreme, Bluetooth, Sonnet PCIe USB2 card. I have two 23" Apple Cinema Displays connected to it all as well as an Epson Stylus DX8400 printer, Maxtor 500GB external USB 2 HD and a 500GB Apple Time Capsule.

Firstly, i would like to know if should just bung in the Ubuntu CD and install it onto a spare HD. Should i do anything prior to install? Once i have installed, what should i do next? How do i enable the Bluetooth, Wireless, Sound etc etc?

Since i last installed Ubuntu, i have added Vista Ultimate 64bit to my Mac Pro. Along with XP Pro and Mac OS X 10.5.2, adding Ubuntu will produce a quadruple boot system. OS X, XP Pro, Vista 64bit + Ubuntu.

Any help will be much appreciated. In return, i will be happy to offer help with Apple equipment as i am an Apple Tech.

Thanks.

---

### Post by cyberdork33 on 2008-05-01
Unfortunately, on this latest release, there are couple of issues.

You should install rEFIt before anything. 

In addition to the recent bugs, installing to a second hard drive usually results in a strange problem that needs a little manual fixing. See the link in the FAQ for information.

---

### Post by MacPro8core on 2008-05-02
> **cyberdork33 said:**
> Unfortunately, on this latest release, there are couple of issues.

You should install rEFIt before anything. 

In addition to the recent bugs, installing to a second hard drive usually results in a strange problem that needs a little manual fixing. See the link in the FAQ for information.

Thanks for taking the time to reply. However....

Curiosity got the better of me and i went ahead with an installation. No problems installing it. Bluetooth worked with no fiddling required, but still no sound.. All was well until i tried to boot into XP from the normal Mac boot selection screen (holding down 'alt' key at startup). XP gave some error about not being able to locate 'autochk'. Then restarted. Couldn't find a solution to this so i ended up doing an XP repair install. All done and dusted, but i broke it again by reinstalling the HD with Ubuntu on it. Did some fishing on the net and discovered that something called GRUB is probably causing this.

Then i read your reply. I have installed refit several times and it doesn't do anything. It install fine, but i don;t get a boot load screen or anything. No idea what is meant to happen. From what i can see, the only problem i have is that Ubuntu screws up XP. If there is a solution to this, i will have a quad boot Mac Pro. The only non-standard thing about my Mac is that i use a pair of HD's in RAID 0 as my OS X drive. Will this cause problems with refit?

Forgot to mention that, although XP fails with the autochk thing when booted directly, Parallels boots from the same drive with nor problems!!!

Your help is much appreciated.

---

### Post by cyberdork33 on 2008-05-02
if ubuntu works, then you repair windows, don't reinstall ubuntu, it doesn't need it. you should install grub to the ubuntu root partition. See the link in my signature for details.

you need to run the enable script in the refit dirrectory.
```
sudo /efi/refit/enable.sh
```
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

---

### Post by MacPro8core on 2008-05-03
> **cyberdork33 said:**
> if ubuntu works, then you repair windows, don't reinstall ubuntu, it doesn't need it. you should install grub to the ubuntu root partition. See the link in my signature for details.

you need to run the enable script in the refit dirrectory.
```
sudo /efi/refit/enable.sh
```
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

Thanks for your reply.

I have given up with rEFIt. I have tried every guide i can find, nothing works. Even the instructions to install it within the EFI partition don't work. Seems that rEFIt isn't really needed.

OK, done some thinking and i will now give my opinion of what went wrong.

Some MacPro info first...

HD Bay 1 = 500GB RAID 0 Slice 1
HD Bay 2 = 500GB RAID 0 Slice 2
HD Bay 3 = 250GB XP Pro
HD Bay 4 = 250GB BLANK

The above configuration is what i had before installing Ubuntu. I think that the Ubuntu installer screwed with the bootloader on the XP drive. I base this on the info i read around the net that states the GRUB bootloader is, by default, installed on the first partition of the first hard drive. I am assuming that the 2 RAID slices will be ignored by the Ubuntu installer, making the XP drive HD 0.

I now have a clean install of XP Pro that is fully functional. I also have Vista Ultimate 64bit on the drive i removed to install the blank 250GB drive for Ubuntu and, of course, Mac OS X is working perfectly.

I would like your opinion on the following idea.

If i remove the XP drive and install my blank drive in Bay 3, will the installation of Ubuntu onto that drive result in GRUB being actually installed on that drive? (Assuming that Bay 3 is seen as HD 0 by the installer)

My hope is that it will and i can then plug in my XP drive again without GRUB screwing it up again.

I am happy to use the Mac boot selection screen as, and when, required. It appears that rEFIt is simply a tool that  loads a boot choice screen by default. I am not interested in that. XP, Vista and Ubuntu will be used infrequently.

---

