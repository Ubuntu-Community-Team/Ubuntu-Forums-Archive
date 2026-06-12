---
title: "When I try to boot Ubuntu through rEFIt, it boots Windows instead"
date: 2010-10-08
forum: Apple Hardware Users
---

### Post by mikeydangerous on 2010-10-08
I have a 2006 Macbook (black plastic 2GHz Core 2 Duo). I am trying to set up a tri-boot system. The partitions are set up:

1 - EFI
2 - OSX (10.6.4) 
3 - Ubuntu (10.10)
4 - Windows 7

I've got rEFIt 0.14 installed, and I can install Ubuntu, but every time I try to boot into Ubuntu, it launches Windows instead. I've tried reinstalling a few times, changing the boot partition option on install, but nothing seems to work. 

Any ideas?

---

### Post by jwhendy on 2010-10-08
Are your tables synced?

Would you be able to boot into your OSX disk and output the result of:
```
gpt show /dev/rdisk0 #assuming the HD is disk0
```

This should show you the GUID partition table layout. Then also run:
```
fdisk -l /dev/sda #assuming the HD is sda...
```

I think you can also use the rEFIt partition tool to look at both. I'd just make sure they both (GUID vs. MBR) seem to match (starting/ending cyls, sizes, and types. Perhaps something is awry in the MBR and for some reason Ubuntu isn't listed as the right partition.

Oh, also post your pertinent section from /boot/grub/menu.lst. Ubuntu, based on the scheme you listed, should be something like:

```

#(2) Ubuntu
title  Ubuntu
root   (hd0,2)
kernel /boot/blah blah
initrd /boot/blah blah
```

---

### Post by mikeydangerous on 2010-10-09
> **jwhendy said:**
> Are your tables synced?

Would you be able to boot into your OSX disk and output the result of:
```
gpt show /dev/rdisk0 #assuming the HD is disk0
```


Thanks for the help, but I'm having troubles. First, rEFIt is saying the tables are synced. 

Second, I can't get the info you're asking for, this is what I'm getting:

[http://east73crew.squarespace.com/storage/temp/Screen%20shot2.jpg](http://east73crew.squarespace.com/storage/temp/Screen%20shot2.jpg)
[http://east73crew.squarespace.com/storage/temp/Screen%20shot%203.jpg](http://east73crew.squarespace.com/storage/temp/Screen%20shot%203.jpg)

And, I don't know how to run the rEFIt tools in the terminal to get you that info.

---

### Post by jwhendy on 2010-10-09
> **mikeydangerous said:**
> Thanks for the help, but I'm having troubles. First, rEFIt is saying the tables are synced. 

Second, I can't get the info you're asking for, this is what I'm getting:

[http://east73crew.squarespace.com/storage/temp/Screen%20shot2.jpg](http://east73crew.squarespace.com/storage/temp/Screen%20shot2.jpg)
[http://east73crew.squarespace.com/storage/temp/Screen%20shot%203.jpg](http://east73crew.squarespace.com/storage/temp/Screen%20shot%203.jpg)

And, I don't know how to run the rEFIt tools in the terminal to get you that info.

Hmmm. Maybe it should be /dev/disk0 instead of rdisk0? Not sure. The diskutil command is quite promising. We just need the specifics.

Though... if rEFIt says they're good to go, perhaps it's in grub. Could you post your Ubuntu section from menu.lst?

---

### Post by mikeydangerous on 2010-10-09
> **jwhendy said:**
> Hmmm. Maybe it should be /dev/disk0 instead of rdisk0? Not sure. The diskutil command is quite promising. We just need the specifics.

Though... if rEFIt says they're good to go, perhaps it's in grub. Could you post your Ubuntu section from menu.lst?

How would I do that? I've googled it, but that seems like something I'd need to be able to boot into Ubuntu to do.

---

### Post by mikeydangerous on 2010-10-09
> **jwhendy said:**
> Hmmm. Maybe it should be /dev/disk0 instead of rdisk0? Not sure. The diskutil command is quite promising. We just need the specifics.

Though... if rEFIt says they're good to go, perhaps it's in grub. Could you post your Ubuntu section from menu.lst?

Also, I checked the partition tables in rEFIt, everything was matched up, but there's also an asterisk next to the partition for Ubuntu. Does that mean anything?

[http://east73crew.squarespace.com/storage/temp/shot.jpg](http://east73crew.squarespace.com/storage/temp/shot.jpg)

---

### Post by mikeydangerous on 2010-10-10
> **jwhendy said:**
> Hmmm. Maybe it should be /dev/disk0 instead of rdisk0? Not sure. The diskutil command is quite promising. We just need the specifics.

Though... if rEFIt says they're good to go, perhaps it's in grub. Could you post your Ubuntu section from menu.lst?

 I figured it out. Of course, it was the simplest answer that I didn't try. I just had to uninstall/reinstall rEFIt, and now everything is fine. 

Thanks for the help.

---

### Post by jwhendy on 2010-10-10
Alrighteo. For your first question, you'll want to do this:

- boot into an Ubuntu CD
- choose the option to try Ubuntu
- Mount /dev/sda3 (the Ubuntu partition on your hard drive, the live CD might automount it for you)
- figure out where that partition got mounted; from a terminal type:
```
mount
```
--- you should see a line like "/dev/sda2 mounted on /???"
--- note whatever that is, maybe like /media/someName?
- Open up a terminal and type
```
sudo nano /media/someName/boot/grub/menu.lst
```
- scroll down to the bottom and find something that looks like
```
#(2) Ubuntu
title  Ubuntu
root   (hd0,2)
kernel /boot/blah blah
initrd /boot/blah blah

```

Mainly what we need to verify is the "root (hd#,#)" line. If that's point to the Windows partition for some reason, it would explain a lot!

For the heck of it, why don't you post the section for Windows as well.

Lastly, it just occurred to me that if you installed Windows last it might have overwritten grub entirely. Do you remember the order you installed things in? I think there's only room for whatever OS X needs and one other system's boot loader. For that reason, you might be selecting Ubuntu, but it's Windows' bootloader that's installed in the MBR and thus... Windows boots.

Check out this page: [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Also, there seems to be some community documentation from the Ubuntu community itself about this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If that seems plausible to you, I'd follow the instructions to reinstall grub and then chainload Windows. That means every time you start Ubuntu you'll have an option in the grub list for Windows and boot it from there.

Alternatively, you can do the same with the Windows system. I can't find info about Win 7, but you can for sure add Ubuntu to a Win XP boot menu (I've done it on my wife's computer). See this page as an example: [http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/](http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/)

Sorry for the info overload. I'm leaning toward it just being a bootloader issue and think that would explain a lot. You tell it to boot Ubuntu, it looks in the bootloader section of the MBR and only finds the Windows one...

Let me know what you think.

---

### Post by jwhendy on 2010-10-10
> **mikeydangerous said:**
> I figured it out. Of course, it was the simplest answer that I didn't try. I just had to uninstall/reinstall rEFIt, and now everything is fine. 

Thanks for the help.

Awesome!! I was writing a post before seeing this. That's awesome! Doesn't it freaking feel amazing when things finally work?

---

