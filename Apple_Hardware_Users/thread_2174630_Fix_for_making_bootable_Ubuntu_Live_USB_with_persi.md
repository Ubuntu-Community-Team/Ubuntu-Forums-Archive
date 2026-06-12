---
title: "Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac"
date: 2013-09-15
forum: Apple Hardware Users
---

### Post by Quackers on 2013-09-15
************
Please see the addendum at the bottom of this post if you're having problems not achieving persistence with a recent version of Ubuntu.


I have been spending a lot of time recently trying to make an Ubuntu Live USB with persistence that will boot on a Mac. 
Persistence is worthwhile having, at least in my case as my wifi does not work "out of the box" so without persistence any driver and firmware that I install once booted to the live desktop would become lost once the system is rebooted. I can obviously have things like Bookmarks for important sites retained too.

I would make the USB with Unetbootin but at the end of the process it would report that this USB would not boot on a Mac. On trying to boot it it would always give either a "Boot error" message or "this is not a bootable disc..........." error.

Most of the information I needed was already available (thanks to Christopher Friedt and others) but it just wouldn't quite work for me. It seemed I was missing a step or something. It seems I was.

Apparently Unetbootin fails to write Syslinux to the MBR of the flash drive (or not correctly, if at all). This could possibly be a licensing kind of thing. It also seems to misread or misinterpret the boot flag or the active partition in some way. If Syslinux is not in the MBR there's nothing to point to where to go to boot anything. 

Anyway, I have just made a 2GB Ubuntu Live USB with persistence following the method below and not only does it boot on a Mac but the persistence actually works! :lolflag:

What you'll need:-
A Mac which is capable of booting from a USB flash drive
A USB stick (2GB upwards in size if you want persistence)
An Ubuntu .iso file - I had Ubuntu 13-04 amd64 for mac - **** if you want EFI boot on a Mac use a non-mac version of the Ubuntu iso
Syslinux (a small downloaded file)
Unetbootin for Mac

OK, here we go:

Plug your USB flash drive into your Mac.

Open a terminal and run
```
diskutil list
```
and in its output note carefully the drive designation of your USB (the size will probably be the giveaway) mine for instance was /dev/disk1 but yours may be something else depending on what else is plugged in to your Mac.

Open Disk Utility and select your USB drive and delete any current partitions. That is click on any partitions in the left pane and in the right pane click erase.
Then click on your USB drive in the left pane and the partition tab in the right pane and create one partition of MS-DOS FAT type naming it anything you want. It's probably wise to click on the options tab and make sure that MBR is ticked. Click on apply.
Ok, once that's run we're finished with Disk Utility.

In the terminal unmount the USB with ```
diskutil unmountDisk /dev/diskX
```  -  changing the X to your drive's number

Now we'll mark the partition as active (even though some programs will already think so, like gparted, for instance)

Open a terminal and run ```
sudo fdisk -e /dev/rdiskX
```  (yes, the extra r is advisable (quicker) and change the X to the number of your USB disc that diskutil gave you earlier)
at this point your prompt will become an fdisk prompt and I got the following message ```
fdisk: could not open MBR file /usr/standalone/i386/boot0: No such file or directory
Enter 'help' for information
``` which I ignored.

now enter these 3 commands ```
f 1
write
exit
```
Please note that you should be able to see your desktop (the area where discs mount) and if at any time during the above the disk appears and stays there run the unmount command again.

Ok, so far so good. 
Now download [syslinux]("https://www.kernel.org/pub/linux/utils/boot/syslinux/")
 
Now it can get a bit messy. In the terminal you need to cd to the folder which has the mbr.bin. 

In syslinux version 6.01 the mbr.bin is in the syslinux-6/bios/mbr folder so that's where you'd need to cd to. 
My (older) version was different (syslinux/mbr) and I've also seen it elsewhere too so you need to have a look where this file is first. If you've extracted the zip file you can have a look in these places for it in the Finder before cd'ing.

Now we can write the much needed code to the MBR of the USB drive

```
sudo dd conv=notrunc bs=440 count=1 if=mbr.bin of=/dev/diskX
```  -  again change the X to your drive's number

After a second or two it should report bytes written count which should be 440.

If this gives an error about not getting access run the unmount command again for your USB (above)

If it gives an error about no mbr.bin then you've cd'd to the wrong part of syslinux folder - possibly!

It may report that the changes won't be made unless you reboot. If it does just type y and enter, then reboot.

Ok now download and install Unetbootin for Macs and use it in the normal way to make the Live USB choosing if you wish to make the persistence file by entering a size in the appropriate field.
It will give the usual guff about what it's doing and may even appear to hang for a while, even give the spinning coloured wheel - just leave it running. It could take about 20 minutes or so, maybe a touch more but leave it anyway.

It will finish and report that the USB will not be bootable on a Mac.  Bah, humbug! 

Reboot leaving your USB flash drive inserted and if you don't have rEFInd installed hold the Option (ALT) key after the chime until the appropriate menu choices appear. 
If you have rEFInd installed you'll see a nice penguin at the end - choose that
If no rEFInd choose the one that wasn't there before (can't remember as I use rEFInd).

You should be greeted by a Unetbootin menu with Default as the top option. You only have a few seconds to choose but my menu included an option to "try Ubuntu without installing" (3rd item down) and I chose that one. Others have reported no such menu item and have used Default, but that doesn't boot for me.

Ubuntu should start loading. Enjoy!

I loaded Ubuntu desktop and changed some wifi setting as my wifi doesn't work out of the box and installed one or two things in the sidebar.
I then rebooted and those changes were still there! Wifi worked without any changes. 
ie persistence now works!! Something I have never got to work before.


As stated above this is what worked for me. It is not guaranteed and if you break something it's on your head!
For instance if you make a mistake entering any of these commands you WILL VERY POSSIBLY destroy data on another drive!!!!!!! Be very careful!!!

This information has been gathered from many sources including the [syslinux.wiki]("http://www.syslinux.org/wiki/index.php/SYSLINUX"), Christopher Friedt's sites 
[http://dropsafe.crypticide.com/article/8368]("http://dropsafe.crypticide.com/article/8368")
and
[http://perpetual-notion.blogspot.co.uk/2011/08/unetbootin-on-mac-os-x.html]("http://perpetual-notion.blogspot.co.uk/2011/08/unetbootin-on-mac-os-x.html")
and much trawling through the Net.

Having said all that if you come across any problems I will try to help - though I am no coder!

****** ADDENDUM********
It seems in more recent versions of Ubuntu that the persistence can fail (particularly if booted in EFI).
I've had a mooch around and thanks to others there may be a fix. At least it's currently working for me and one other :-)

I plugged the newly made USB in to my Mac and opened the drive then navigated to /boot/grub then opened grub.cfg with textedit
In the newly opened file go to this menu entry 
```
menuentry "Try Ubuntu without installing" {
``` which is the first one in the file.
Just further down the file is the line below to which I've added the word "persistent"
```
linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper [COLOR="#FF0000"]persistent[/COLOR] quiet splash --
```
Once added you can save the file and then boot from it and hopefully have persistence.
 
Good luck!

---

### Post by Quackers on 2013-09-15
By way of addition there is a recent innovation called Mac-Linux-USB-Loader which I have tried. It actually gets to booting the linux kernel but then fails as it doesn't seem to have support for Nvidia chips. It also uses EFI to boot.
There is currently no persistence option but it is a possible future enhancement.

---

### Post by pindar on 2013-09-16
I just wanted to thank you for your detailed explanations, your efforts are highly appreciated. I followed your instructions, and for the first time, unetbottin created a USB stick that would boot both my MBA and my iMac. Given that more recent macs come without an optical drive, this is important knowledge. May I suggest you write them down somewhere which is less volatile and more visible than a forum post?

---

### Post by sudodus on 2013-09-16
Threads in the Ubuntu Forums are persistent. And I have linked to this thread from an Ubuntu wiki page

[URL="https://help.ubuntu.com/community/Installation/FromUSBStick#From_Mac_OSX"]https://help.ubuntu.com/community/Installation/FromUSBStick#From_Mac_OSX
[/URL]
Of course, more links are welcome :-)

---

### Post by Quackers on 2013-09-16
pindar 
I'm glad it worked for you. :D and thanks for your comments.
I'm looking for other places to post this information but would appreciate confirmation of the guide's validity first. ie different versions of Ubuntu and Syslinux etc.

For my own information could you please give me the following details? 
The size and make of your USB stick
Which exact version of Ubuntu/Linux iso file you used
Which version of Syslinux you downloaded and which of its directories the mbr.bin was in
Were there any problems for you or was there anything I have missed from the guide?

Many thanks and enjoy your new Live USB  :D

---

### Post by pindar on 2013-09-16
> **Quackers said:**
> pindar 
For my own information could you please give me the following details? 
The size and make of your USB stick
Which exact version of Ubuntu/Linux iso file you used
Which version of Syslinux you downloaded and which of its directories the mbr.bin was in
Were there any problems for you or was there anything I have missed from the guide?

Many thanks and enjoy your new Live USB  :D
Sure, glad to be of help:

USB stick: SanDisk Cruzer, 8GB

I used linuxmint xfce edition, 64bit (but will happily try other ubuntu editions)

syslinux: version 6.01

mbr.bin was in syslinux-6.01/bios/mbr

Problems: one small glitch was that your command
```
sudo dd conv=notrunc bs=440 count=1 if=mbr.bin of=/dev/rdiskX
```
wouldn't work for me, I always got an error message dd: /dev/rdisk1: Invalid argument." When I replaced /dev/rdiskX with /dev/diskX, the command completed successfully.

---

### Post by Quackers on 2013-09-16
Great, thanks for the details.
I'll make another USB shortly and check that out - maybe the r is confusing things and it doesn't really need to be there as it isn't writing much anyway.

Edit in fact I've removed it and will test shortly.
Edit2  yep works fine without the r

---

### Post by sudodus on 2013-09-17
Could this be a clue to why it is difficult to make USB flash drive that can boot on Macs? See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues](https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues)

> You need Mac OS X to create a USB flash drive that can boot on Macs.  Even so, the process is less reliable than using a CD, as the USB flash  drive is not always recognized on boot. Reversely, you can't create  bootable USB flash drives for other platforms than Macs from within Mac  OS X. This is because Macs use a custom EFI bios with a custom  boot-loader and need a special filesystem layout to boot correctly. 

---

### Post by Quackers on 2013-09-17
I don't know tbh. 
Mine recognised the Live USB every time and it recognised that it should have been bootable but could not find the bootable elements on that drive. I suspect this is closer to the truth.
Macs don't have a bios as such. They have a kind of bios emulation, as I understand it, which is a not accessible as far as I'm aware.
The U3 problem as mentioned in that article seems to be solved with regard to the Sandisk Cruzers at least as I have successfully created a bootable Ubuntu Live USB on one, as did pindar.

---

### Post by sudodus on 2013-09-17
This is old stuff from the days of Ubuntu 11.04, and if you think it is not relevant, I can wipe it from the wiki page.

---

### Post by Quackers on 2013-09-17
I don't think it's relevant to me personally but it may be relevant to people who have a Mac of that age and may come across those particular problems, maybe.

---

### Post by pindar on 2013-09-17
> **sudodus said:**
> Could this be a clue to why it is difficult to make USB flash drive that can boot on Macs? See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues](https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues)
I don't have the knowledge for extensive testing, just some anecdotal evidence: I took the Sandisk Cruzer that I had prepared following Quackers' great tutorial, wiped the content and used unetbootin under linux to install a different linux system (xubuntu 13.04). The drive booted both my MacBook and a Lenovo Thinkpad. So the information might be not 100 % accurate.

---

### Post by Quackers on 2013-09-17
That's good to know. Thanks pindar.

---

### Post by sudodus on 2013-09-17
I added this note in the paragraph ['Known Issues']("https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues")

[This information about known issues is a few years old, and may or may not be valid today (September 2013).]

---

### Post by Quackers on 2013-09-17
Thanks sudodus

---

### Post by sthrss on 2013-10-01
> **Quackers said:**
> pindar 
I'm glad it worked for you. :D and thanks for your comments.
I'm looking for other places to post this information but would appreciate confirmation of the guide's validity first. ie different versions of Ubuntu and Syslinux etc.

For my own information could you please give me the following details? 
The size and make of your USB stick
Which exact version of Ubuntu/Linux iso file you used
Which version of Syslinux you downloaded and which of its directories the mbr.bin was in
Were there any problems for you or was there anything I have missed from the guide?

Many thanks and enjoy your new Live USB  :D

Thank you for your effort and your information, i followed your guide but i didn't manage to make a functional live-usb. This are my information:

OS: Mac OS X 10.6.8
Hardware: Mac Mini 3,1
Ubuntu ISO version: ubuntu-13.04-desktop-amd64+mac
syslinux version: 6.01
usb pen drive: Corsair 8gb

I tried the following:

1. format and partition the flash drive with MBR (disk utility -> options) and use:
1.1 /syslinux-6.01/bios/mbr/mbr.bin/
1.2 /syslinux-6.01/efi32/mbr/mbr.bin/
1.3 /syslinux-6.01/efi64/mbr/mbr.bin/

2. with GUID:
2.1 /syslinux-6.01/bios/mbr/mbr.bin/
2.2 /syslinux-6.01/efi32/mbr/mbr.bin/
2.3 /syslinux-6.01/efi64/mbr/mbr.bin/

"Boot Error" was the result and of course after each of these 6 "experimentations" re-format the flash drive and follow step-by-step your instructions, always checking if the flash-drive was mounted.

Also, the command: ```
[COLOR=#000000][FONT=Ubuntu Mono]diskutil unmount /dev/diskX[/FONT][/COLOR]
``` never worked for me, instead i used: ```
diskutil unmountDisk /dev/diskX
```

If you could provide me with any insights/suggestions/directions i'm happy to test them :D

ps: I even replaced the rEFIt program i used with the rEFInd that you used, so i could reduce the possible errors/problems.

ps2: all 3 mbr.bin files seems to contain the same (bytecode?) text, so i assume that it doesn't make any difference which one anyone choose.

---

### Post by Quackers on 2013-10-01
sthrss, you're right about the unmount command. I suspect I've chopped the end off whilst editing. Thanks I've edited that.

Just for clarification you need to cd to syslinux-6/bios/mbr then run the command (not to /syslinux-6.01/bios/mbr/mbr.bin/)
I would have expected your command to give an error message. Was that the case?

You're probably better off with rEFInd than with rEFIt as that's not maintained any more.

---

### Post by sthrss on 2013-10-01
> **Quackers said:**
> sthrss, you're right about the unmount command. I suspect I've chopped the end off whilst editing. Thanks I've edited that.

Just for clarification you need to cd to syslinux-6/bios/mbr then run the command (not to /syslinux-6.01/bios/mbr/mbr.bin/)
I would have expected your command to give an error message. Was that the case?

You're probably better off with rEFInd than with rEFIt as that's not maintained any more.

Thank you for your quick reply and info! Yes, you're right about the folder i actually run (each time reformating my flash drive and repeating your steps from the beginning):

```

1st time:
sudo dd conv=notrunc bs=440 count=1 if=/Users/sthrss/Downloads/syslinux-6.01/bios/mbr/mbr.bin of=/dev/disk1

2nd time:
sudo dd conv=notrunc bs=440 count=1 if=/Users/sthrss/Downloads/syslinux-6.01/efi64/mbr/mbr.bin of=/dev/disk1

3rd time:
sudo dd conv=notrunc bs=440 count=1 if=/Users/sthrss/Downloads/syslinux-6.01/efi32/mbr/mbr.bin of=/dev/disk1

```

which is the same. My system didn't gave more errors than those that you've mentioned at your 1st post, the ones you've ignored.

---

### Post by Quackers on 2013-10-01
Hi, just checking but does your Mac boot from a flash drive? It has that capability? Some don't.
Secondly do you have a different kind of flash drive to try? I have read that some types of flash drive may not have EFI drivers available which could be a problem.
I can think of no reason why it shouldn't work other than the above.

It's really the same thing but a different way to go about it but if you copy or move the Syslinux folder to your user's home directory it makes it a lot easier to cd to it. You can then try to run the commands as posted.
However, if you aren't getting any errors when entering the commands I can't explain why it isn't working.

---

### Post by sthrss on 2013-10-02
> **Quackers said:**
> Hi, just checking but does your Mac boot from a flash drive? It has that capability? Some don't.
Secondly do you have a different kind of flash drive to try? I have read that some types of flash drive may not have EFI drivers available which could be a problem.
I can think of no reason why it shouldn't work other than the above.

It's really the same thing but a different way to go about it but if you copy or move the Syslinux folder to your user's home directory it makes it a lot easier to cd to it. You can then try to run the commands as posted.
However, if you aren't getting any errors when entering the commands I can't explain why it isn't working.

After a long series of tests (lol) i managed to make it work!

0. **GUID** partitioning of usb
1. follow all the steps from your guide except the unebootin part.
2. sudo dd if=/path/to/downloaded[FONT=Ubuntu][SIZE=3][COLOR=#333333].[/COLOR][/SIZE][/FONT]**iso**of=/dev/**disk**N bs=1m

[FONT=Ubuntu][SIZE=3][COLOR=#333333]I read that the [/COLOR][/SIZE][/FONT][SIZE=4]**"r" **[/SIZE][FONT=Ubuntu][SIZE=3][COLOR=#333333]in front of [/COLOR][/SIZE][/FONT]**disk **[FONT=Ubuntu][SIZE=3][COLOR=#333333]is like a parameter for faster copy, so i just preferred the "simple and safer" method; silly thought but it might did the trick.[/COLOR][/SIZE][/FONT]

[FONT=Ubuntu][SIZE=3][COLOR=#333333]Then mac os x returned a window with an error message, something that my device is not recognised and i ignored it. Reboot and voila! the usb worked![/COLOR][/SIZE][/FONT]

**BU****T **[FONT=Ubuntu][SIZE=3][COLOR=#333333]after the first steps of installation the partition i wanted to use (my hdd was already partitioned, 1 mac os x, 1 16gb for linux and 1 2,1gb for swap), was already in use by [/COLOR][/SIZE][/FONT]**/cdrom**[FONT=Ubuntu][SIZE=3][COLOR=#333333], i couldn't unmount it by any means, so i opened the partition it was mount [/dev/sda5 -> the one i want to use for the installation] and found that it contained data from the usb, i returned to mac os, reformat them [/dev/sda5; /dev/sda6 -> swap] in [/COLOR][/SIZE][/FONT]**ntfs **[FONT=Ubuntu][SIZE=3][COLOR=#333333](just in case ubuntu mounts the usb to any free fat32 -like the usb's fs- partition), reboot and the installation run smoothly...[/COLOR][/SIZE][/FONT]

[FONT=Ubuntu][SIZE=3][COLOR=#333333]... after the final -thought to be- reboot, i tryied to load the new ubuntu installation but efi returned this message:[/COLOR][/SIZE][/FONT]

[FONT=Ubuntu][SIZE=3][COLOR=#333333]> No bootable device - insert boot disk and press any key[/COLOR][/SIZE][/FONT]


[FONT=Ubuntu][SIZE=3][COLOR=#333333]I'm really exhausted with the situation and the worst part is that i don't have 2nd computer, the cdrom driver is broken and i really need a linux distro in my stupid-for-buying-it-because-it-was-on-discount-offer, old mac mini...[/COLOR][/SIZE][/FONT]


[FONT=Ubuntu][SIZE=3][COLOR=#333333]If you have any thoughts/directions/info on how i should proceed i'm happy to follow, because right now i'm really puzzled and confused on what to do, thanks in advance :D


**PS: **Suddenly now i have no boot options (just boot directly to the mac os), tried to reinstall rEFInd but it didn't help, also i cant reformat the partition were i made the installation nor the swap; when i used "**disk utility.app**" to erase (format) the partitions, it returned: 

[/COLOR][/SIZE][/FONT]> 
Volume Erase failed with the error:

Could not modify partition map
[FONT=Ubuntu][SIZE=3][COLOR=#333333]

:([/COLOR][/SIZE][/FONT]

---

### Post by Quackers on 2013-10-02
Glad to hear the flash drive now boots at least :-)
As far as your new installation goes I take it you're trying to install it in EFI mode. 
Also you need to make sure that your Mac is using GPT solely - as in no hybrid mbr (which is what a previous BootCamp partition will have created - if you've had one) as going past 4 partitions with a hybrid mbr can be dodgy.

Did you install grub? I elected to select "try Ubuntu" first then ran "ubiquity -b" in the terminal so that grub would not be installed at all (rather than just setting the Ubuntu installer loose).
Then, once installed I booted into OSX and installed rEFInd and placed rEFInd's ext4fs driver in a new folder called drivers which I placed in EFI/Boot iirc - I can check that later.

Did you press the Alt key whilst re-booting the Mac?

---

### Post by sthrss on 2013-10-02
> **Quackers said:**
> Glad to hear the flash drive now boots at least :-)
As far as your new installation goes I take it you're trying to install it in EFI mode. 
Also you need to make sure that your Mac is using GPT solely - as in no hybrid mbr (which is what a previous BootCamp partition will have created - if you've had one) as going past 4 partitions with a hybrid mbr can be dodgy.

Did you install grub? I elected to select "try Ubuntu" first then ran "ubiquity -b" in the terminal so that grub would not be installed at all (rather than just setting the Ubuntu installer loose).
Then, once installed I booted into OSX and installed rEFInd and placed rEFInd's ext4fs driver in a new folder called drivers which I placed in EFI/Boot iirc - I can check that later.

Did you press the Alt key whilst re-booting the Mac?

I didn't understand quite right what you've done with the ext4fs driver and what is the "iirc". What i understood for the ext4fs driver: you've moved the file /efi/EFI/boot/drivers_x64/ext4_x64.efi to the new folder /efi/EFI/boot/drivers_x64/**drivers**/ext4_x64.efi ?


Also i tried the Alt key, and returned an icon of a hdd with the title: "EFI Boot", choose it and load mac os again. I just can't recall what i did differently and now i lost the boot options and i'm unable to reformat the partitions...

maybe that "ubiquity -b", after the first installation would be the key to the solution.

**PS: **I'm setting up a vm until i find what to do, thank you for your time and effort anyway :D

---

### Post by Quackers on 2013-10-02
Hi, iirc means if I recall correctly.
Sadly I've re-installed OSX since I did that with the ext4fs driver so can't check that now.
I think I moved the driver to a new folder called "Drivers" which I created but I can't remember where exactly :-(
I think you may find more details on the rEFInd site about installing the driver.

What matters more for the moment is your drive's partition scheme - GPT with a protective mbr or GPT with a hybrid mbr. That should be checked first.
Then it matters how you've installed Ubuntu and where grub is and in what form.

When you Alt booted what other symbols were shown?

---

### Post by sthrss on 2013-10-02
Thanks for the advice i'll start with the rEFInd documentation :)

After the Alt there was only the hdd icon entitled "efi boot".

---

### Post by Quackers on 2013-10-03
Really? No Macintosh HD or Recovery HD?

Well If you're going over to rods books site (rEFInd) download and install disk and run it to see what your partitions look like and see whether you have protective mbr or hybrid mbr.

---

### Post by donovan2 on 2013-10-13
Sorry i sound like a complete noob, but i dont know what exactly i need to do when we get to 'cd' the mbr.bin im a little confused could you help me?

---

### Post by Quackers on 2013-10-14
Which version and file type of Syslinux did you download and where did it download to?

If you downloaded syslinux 6.01.zip to your Downloads folder you can extract the zip file there.
Then in the terminal do ```
cd /Downloads/syslinux-6/bios/mbr
```
You should see your terminal prompt change to that. 
You can then run the sudo dd command in the terminal changing the /dev/diskX entry to the correct one for your USB drive - i.e. /dev/disk1, perhaps.

---

### Post by j.stopak on 2013-11-06
Hey Quackers,

I have just tried going through your steps and it was going great until the unetbootin step.  Once I input all required information including boot.iso path and persistence size in MB and then click OK button, nothing happens.  It doesn't start the process of creating the live USB at all.  I could just sit there clicking OK over and over but nothing happens at all.  I am using Mac OSX 10.8.5 (Lion) and the Mac version of Unetbootin version 585.  Also the boot.iso I have is Linux Mint, not Ubuntu, but that shouldn't make a difference here right?

Ever seen this at all?  Any advice?  Maybe look for older versions of unetbootin to test with?

Thanks and let me know if you have any suggestions!

---

### Post by Quackers on 2013-11-07
It's not always apparent that unetbootin has started working, even though it has.
Have you tried looking at the running processes once you have clicked on the OK button?

I haven't tried it with a Linux Mint iso so I don't really have any suggestions for you I'm afraid.

---

### Post by antoniolamb on 2013-11-07
I have not been able to get this to work at all :/. I have a macbook pro 8.1 with AMD Radeon card... Can anyone help out a fellow mac user? I want to run a usb distro to keep my personal files separate from my host machine. I tried following your guide but mountian lion just ends up saying "this disk is unreadable". 
[http://ubuntuforums.org/showthread.php?t=2186318](http://ubuntuforums.org/showthread.php?t=2186318)

---

### Post by Quackers on 2013-11-07
Hi antoniolamb,
did you get any error messages during the attempt at making the USB installer?
What exact version of Ubuntu are you using?
Do you have a different make of USB flash drive to try it on?
My method is not foolproof it seems, as I have the odd failed attempt.

---

### Post by antoniolamb on 2013-11-07
Hey Quackers. Thanks for the reply. I do not get any errors in making the USB drive, and everything finishes... it's just that when everything is finished, this pops up: 
[IMG]http://s18.postimg.org/40nxhspg9/error.png[/IMG]

I will try again and post exactly what I did. It's driving me crazy that I can't get this to work :/. I can't boot any kind of linux on this piece of crap haha. I didn't realize how bad my mac sucks :/

---

### Post by antoniolamb on 2013-11-07
Alrighty... well, I made some progress. The drive actually shows up in refind now, but now this happens:
[IMG]http://s8.postimg.org/xubffyowl/image.jpg[/IMG][IMG]http://s18.postimg.org/acvrt6lzt/image_1.jpg[/IMG]

Here are my specs and what I did:
[COLOR=#000000]Computer specs:[/COLOR]
[COLOR=#000000]MacBookPro8,2[/COLOR]
[COLOR=#000000]Processor Name:    Intel Core i7[/COLOR]
[COLOR=#000000]graphics/displays: [/COLOR]**AMD Radeon HD 6750M (PCIe)+Intel HD Graphics 3000 (built-in)**
Ubuntu ISO: trusty-desktop-amd64+mac.iso (MD5 6a6c95faf613baa98e89895b0fc26490... [COLOR=#006400]**verified**[/COLOR])

What I did:

Terminal 
**[COLOR=#006400]dhcp-209-206:~ antoniolamb$ diskutil list[/COLOR]**

/dev/disk0 **[COLOR=#ff0000][My HDD][/COLOR]**
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *750.2 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            749.3 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3

/dev/disk1 [COLOR=#ff0000]**[<-----USB drive. I formatted as FAT32 MBR before I did everything.]**[/COLOR]

   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *4.1 GB     disk1
   1:                        EFI                         209.7 MB   disk1s1
   2:       Microsoft Basic Data UNTITLED 1              3.9 GB     disk1s2
**[COLOR=#008000]dhcp-209-206:~ antoniolamb$ diskutil unmountdisk /dev/disk1[/COLOR]**
Unmount of all volumes on disk1 was successful
**[COLOR=#008000]dhcp-209-206:~ antoniolamb$ sudo fdisk -e /dev/rdisk1[/COLOR]**
fdisk: could not open MBR file /usr/standalone/i386/boot0: No such file or directory
Enter 'help' for information
[COLOR=#008000]**fdisk: 1> f 1**[/COLOR]
Partition 1 marked active.
**[COLOR=#008000]fdisk:*1> write[/COLOR]**
Writing MBR at offset 0.
**[COLOR=#008000]fdisk: 1> exit[/COLOR]**
**[COLOR=#006400]dhcp-209-206:~ antoniolamb$ diskutil unmountdisk /dev/disk1[/COLOR]**
Unmount of all volumes on disk1 was successful
**[COLOR=#006400]dhcp-209-206:~ antoniolamb$ cd /Users/antoniolamb/Desktop/syslinux-6.02/bios/mbr [/COLOR]**
**[COLOR=#006400]dhcp-209-206:mbr antoniolamb$ sudo dd conv=notrunc bs=440 count=1 if=mbr.bin of=/dev/disk1[/COLOR]**
1+0 records in
1+0 records out
440 bytes transferred in 0.018932 secs (23241 bytes/sec)
[B][COLOR=#006400]dhcp-209-206:mbr antoniolamb$ done....

Then I went on to Unetbootin
[/COLOR][/B][IMG]http://s13.postimg.org/qo6uywtw7/image.png[/IMG][IMG]http://s8.postimg.org/pc718qoph/image.png[/IMG][IMG]http://s18.postimg.org/3ugplhdy1/image.png[/IMG][IMG]http://s23.postimg.org/bwqusowij/image.png[/IMG]
[IMG]http://s22.postimg.org/58r31oett/image.png[/IMG]
Everything seems to go well, but then when I select "boot linux" for the thumbdrive in refind, nothing happens...

I have also tried to follow this wiki, but unfortunately, I am too much of a newb to figure out what it's saying. All I know is that I have to change something with my graphics card. Never would have thought it would be so hard to boot an OS off the thumb drive. ****ing apple.
[https://help.ubuntu.com/community/MacBookPro8-2/Raring](https://help.ubuntu.com/community/MacBookPro8-2/Raring)

---

### Post by Quackers on 2013-11-08
Thanks for all the info.
I have had this happen once and when I re-tried it with the same flash drive it worked.
Obviously you have tried it more than once so even though everything appears to go well it doesn't appear to work. Maybe the version of Syslinux could be a factor. I notice you used 6.02. Is the mbr.bin in the same place?
Apple are known for their finicky nature when booting from flash drives. I presume that your Mac is capable of booting from a flash drive?

Sorry but I really don't know what to suggest other than trying other methods.

Best of luck to you.

---

### Post by mattholl82 on 2013-12-08
Just installed 13.10 on a 10,1 retina.  This was a big help thanks!

---

### Post by Quackers on 2013-12-09
> **mattholl82 said:**
> Just installed 13.10 on a 10,1 retina.  This was a big help thanks!
Glad to hear that  :D
Glad to hear that it still works!

---

### Post by m6a2t3t on 2013-12-27
Hello Quackers,

I'm brand new to this forum and reluctantly admit I haven't posted to any forum for probably 10 years; much has changed in the way of protocol and etiquette I realize. But anyway..

Thanks for this thread, it has helped me greatly. I followed your instructions without a hitch. I copied ubuntu-13.10-desktop-amd64+mac to a PNY 8gb usb stick on a MacBook Pro mid 2012 retina (10,1). I used 8000 MB as the persistence size in unetbootin. The problem I am having is that during the boot process, after the unetbootin boootloader, no graphical screen is shown, just the text output is shown and it ends with the BusyBox [initramfs] prompt. First time I booted it ended just before this prompt, no input was excepted. Subsequent boots seem to end at this prompt. Input is excepted, I tried 'exit', which gave a couple errors both something about a kernel panic.

What do you think I should try next?

---

### Post by Quackers on 2013-12-27
There is a question that springs to mind. If you're using an 8GB stick and giving 8000MB to persistence it doesn't leave any space for Ubuntu. I'm surprised that Unetbootin allowed it. Are those numbers correct?

---

### Post by duhd on 2014-01-02
Thanks a million ! This saved me some serious googling and headaches.

---

### Post by Quackers on 2014-01-02
Glad it helped :D

---

### Post by brill.kennyzeniant on 2014-01-16
> **mattholl82 said:**
> Just installed 13.10 on a 10,1 retina.  This was a big help thanks!

Hey! I have been trying to install ubuntu to a MBP 2009, so I'm very interested in exactly what you did, the image (I'm using 13.10 + mac .iso), the persistence space, the syslinux used, refind/refit, etc I can't get mine to work :S

---

### Post by brill.kennyzeniant on 2014-01-17
@Quackers: I followed all your instructions and it appears to boot (a white line appears at the left top corner, like a prompt) for a while, then it **boots to the windows partition**, I think it has something to do with nVidia drivers missing... because I only can boot a livecd selecting the nomodeset flag.

---

### Post by Quackers on 2014-01-18
> **brill.kennyzeniant said:**
> @Quackers: I followed all your instructions and it appears to boot (a white line appears at the left top corner, like a prompt) for a while, then it **boots to the windows partition**, I think it has something to do with nVidia drivers missing... because I only can boot a livecd selecting the nomodeset flag.

So you can boot the Ubuntu live cd with nomodeset then?
If you have then installed Ubuntu from that live desktop you will need to use the nomodeset boot option to boot the newly installed Ubuntu system - at least until Nvidia drivers are installed.

---

### Post by david139 on 2014-01-18
Hi there, Quackers,

Thank you very much for this tutorial; it was supremely helpful. Unfortunately, I'm running into the same issue as m6a2t3t. I've loaded 12.04 onto my 8GB drive, setting the persistent file as 4GB (like I'm used to doing with Windows-based live USBs). All of the steps worked without a hitch, but I ended up with a bunch of [FONT=courier new]"timeout: killing '/sbin/blkid -o udev -p /dev/sdaX'"[/FONT] messages followed by the BusyBox/(initramfs) prompt. Any ideas?

---

### Post by Quackers on 2014-01-18
I'm afraid not as I'm not familiar with that error message. It occurs to me though that the later kernels may be more useful for installing on Macs.
You don't say which Mac you are installing on but I would suggest using 13-04 or even 13-10, especially on later Macs.
I've also seen others using the non-Mac version of Ubuntu too.

---

### Post by Paul_Goodwin on 2014-01-29
As a relative noob to Ubuntu, I'm scratching my head with this.

Followed all of the instructions to install on an 8gb usb plugged into my 2012 retina and can't get it to work if I use one of the amd 64 mac iso's from the ubuntu site - everything goes swimmingly, but when I hold the alt key on boot I get mac hd, recovery hd and a single yellow windows drive, there's no EFI. If I try to boot from the windows drive I just get command line, lots of lines of code and no ubuntu.

I tried creating a usb using ubuntu_live_64 (the top option in unetbootin) and that gives me an EFI drive to boot from, it boots up into ubuntu desktop, but no persistence, and not the mac version.

Don't know what to do!

---

### Post by Quackers on 2014-01-29
A Mac will call an Ubuntu USB a Windows USB. When booting from the "Windows" USB you are seeing what you should see - Ubuntu loading various things.
What is the last line it shows and how long are you leaving it running?

---

### Post by Paul_Goodwin on 2014-01-29
> **Quackers said:**
> A Mac will call an Ubuntu USB a Windows USB. When booting from the "Windows" USB you are seeing what you should see - Ubuntu loading various things.
What is the last line it shows and how long are you leaving it running?

If I boot from the windows drive I get what looks like an msdos type blue screen which counts down, then screen goes black, lines of scrolling code and it ends up with a prompt:

(initramfs) _

I could post a pic if that would help?

---

### Post by Quackers on 2014-01-29
Does the blue window include options? If so the third option down should be "try ubuntu without installing" - select that, but be quick!
It sounds like the Unetbootin default screen.

---

### Post by Paul_Goodwin on 2014-01-29
I get this

[http://www.flickr.com/photos/31147369@N08/12209056073/](http://www.flickr.com/photos/31147369@N08/12209056073/)

Then this if I press tab

[http://www.flickr.com/photos/31147369@N08/12209458026/](http://www.flickr.com/photos/31147369@N08/12209458026/)

then this

[http://www.flickr.com/photos/31147369@N08/12209055933/](http://www.flickr.com/photos/31147369@N08/12209055933/)

and it ends with this:

[http://www.flickr.com/photos/31147369@N08/12209055773/](http://www.flickr.com/photos/31147369@N08/12209055773/)

:confused:

---

### Post by Quackers on 2014-01-29
I see, it's not booting fully.
You said earlier you got an Ubuntu_Live_64 USB to boot to a desktop. Why can't you use that to install Ubuntu?
I'm not clear on whether you're using the guide in post 1 or not.
I'm not absolutely clear on what you want to achieve. Obviously you want to install Ubuntu but you mention EFI installation. That's not up to a boot option - that's done during installation.
I would respectfully suggest that you get clear on what you want, why you want it and have an idea on how to do it.
Or, at least, explain more clearly :confused:

---

### Post by Paul_Goodwin on 2014-01-29
Hi, sorry if I'm not clear. 

I am following the instructions in the first post - my intention is to get a live usb with persistence so that I can boot from the usb and run ubuntu directly from it without installing on the mac.

---

### Post by Quackers on 2014-01-29
Ok, thanks.
You don't mention whether any error messages were shown when making the USB. Which version of Syslinux used. Which version of Ubuntu. How much persistence did you create? What size of USB are you using?
Others have had success with non-mac versions of Ubuntu instead which is maybe something you could try.
It's interesting that the Ubuntu_Live_64 (whatever that is) booted to a desktop whereas your other USB only goes to an initramfs prompt. Something is obviously different, though I don't know what.
Try a different USB, perhaps.

---

### Post by Paul_Goodwin on 2014-01-29
I've tried 12.10, 13.04 and 13.10 mac iso's of ubuntu and they all do the same thing, I'm using syslinux-6 and the latest version of unetbootin.

The live version is from the distributions option in unetbootin, selecting ubuntu and 13.04_Live_x64 (I also tried the 12.10 version and it's the same.

I've tried varying sizes for persistence, from zero to 2000mb and always left a gig or more spare on the usb stick - I've also tried three different sticks: HP, a couple of different cheap Chinese sticks and a PNY, as well as an SD card. All cards seem to behave the same apart from the PNY which won't boot.

The only consistency I can find is that if I use one of the distributions (in unetbootin, that it downloads itself) it boots to the ubuntu desktop, but if I select a downloaded iso in unetbootin I get the results in the images.

Most odd.

---

### Post by Quackers on 2014-01-29
So the only way you get Ubuntu to boot to a desktop is by not using the guide on page 1, it seems :D
All attempts using that guide fail to boot to a desktop.
You've obviously invested some effort in this quest and I'm sorry that it's not working for you. It hasn't worked for some and I don't know why that is. All I know is that I tried it and it's worked for me with a couple of different isos and two different types of USB stick.
I'm as stumped as you are  :confused: It is somewhat annoying.

It's the persistence feature that I was looking for initially as my network doesn't work "out of the box" so always needed drivers and firmware installed.

---

### Post by Paul_Goodwin on 2014-01-29
Pretty much :)

It is really weird, I thought I was going mad at first, but have tried all different permutations without success. C'est la vie. Going to keep trying and will let you know if I get anywhere - thanks for the feedback tho'

---

### Post by Quackers on 2014-01-29
Well good luck to you :)

---

### Post by p2ranger on 2014-01-29
Thanks for putting together this tutorial

I have a late 2009 iMac with snow leopard 10.6.8

I'm trying to run Ubuntu 13.10 on a USB hard drive.

I followed your tutorial and everything seemed to work until rebooting.

The problem I'm running into now is that it won't show that drive for me to choose from when I reboot and hold down alt. I have Win 7 installed with bootcamp, so I can choose between OSX and Windows. 

Before I came across your thread, I tried using Linux USB builder [http://penguintosh.com/tag/linux-usb-creator/](http://penguintosh.com/tag/linux-usb-creator/) I was able to select the USB drive on rebooting when I tried using that application for this. However, when ubuntu booted up, it showed 4 desktops all showing the same thing. I don't know what the deal was with that, but that does tell me that I can boot off this drive as it was a selection for me.

So, any ideas on how to get this drive to show up when I press ALT on rebooting?

Thanks

Jason

---

### Post by Quackers on 2014-01-30
The Ubuntu USB may show up in the boot menu as a Windows USB. Does nothing show up at all for the USB?
If that's the case then it hasn't worked.
Can a 2009 iMac boot from a USB?

---

### Post by p2ranger on 2014-01-30
Nothing shows up for the USB. It only allows the choice that I normally have of OSX and Windows.


As far as I can gather, the 2009 iMac does allow you to boot up from USB. The previous method that I tried got me the choice to choose what was labeled as EFI Boot along with windows and osx. Selecting the EFI from the previous method got me to a screen that showed 4 Ubuntu desktops, all showing the same mouse movement and interaction at the same time. Only two of the desktops were complete, the other two were partially off the screen. It was in a 2x2 pattern. Not usable and only readable enough for me to select shutdown. The app that created the boot up method is a couple of years old and I thought the issue may lie in the change with unity. I did try a pre unity flavor, but it still did the same thing.

So my problem seems to be using your method to get the disk to be bootable.

Any ideas would be great

Thanks

Jason

---

### Post by Quackers on 2014-01-30
I may be wrong but I would be surprised if your iMac has a cd drive yet boots from a USB, unless you've altered the info.plist file.

On another tack I have just made an Ubuntu installation USB with a USB2 Sandisk cruzer blade 4GB and a 13-10 normal iso (i.e. not a mac version) and it boots fine through Unetbootin's menu when I select "try Ubuntu without installing". I used my guide from post 1 and it just works.

That's perhaps something you could try (a non-Mac version). I've now tried several USB's and a number of Mac and non-Mac Ubuntu versions and they've all booted fine on my rMBP (mid 2012).

So I'm at a loss to understand why yours does not work if your system can boot from a USB.
Do you have any other USB's with a bootable operating system on them that you could try to boot on your iMac?

---

### Post by p2ranger on 2014-01-31
I've tried lots of different combinations and I could never get the drive to show on reboot.

I installed the rEFInd thing and that showed the drive on reboot. It even showed the tux penguin. The only problem is that when I selected it for boot, it went into my windows bootcamp installation.

I'm at a loss as to what to do next.

Thanks

Jason

---

### Post by Quackers on 2014-02-01
I think refind can get mixed up and show the penguin for Windows by mistake. If that was the only other option showing in your boot menu then the USB was not appearing, again.
Have you ever booted anything by USB on this Mac?

---

### Post by p2ranger on 2014-02-01
Yes I have. I used something from this site: [http://penguintosh.com/tag/linux-usb-creator/](http://penguintosh.com/tag/linux-usb-creator/)
I used that to put the iso on my USB drive. I was able to boot in to ubuntu, but the screen didn't look right. I think there was a display driver issue.

As to rEFInd mixing up the icon, I tried selecting the linux icon and the windows icon, and they both sent me to windows.

Jason

---

### Post by Quackers on 2014-02-01
So you've had Ubuntu Live desktop running twice. The first time you had 4 screens and the next time the display didn't look right.
I would suggest that you look into solving the display problems as your problem booting into Ubuntu seems to be gone.

---

### Post by p2ranger on 2014-02-02
Thanks for you help. I'm going to post this here as a reference in case someone else may need it.

The last post on this thread was an easy way to help me get to where I could boot to an Ubuntu desktop, but I have a display problem where it is showing four of them.

[http://www.linux.org/threads/mac-linux-usb-loader.3579/](http://www.linux.org/threads/mac-linux-usb-loader.3579/)

YMMV

Jason

---

### Post by Quackers on 2014-02-02
Post a question regarding your 4 desktops in General Help forum and see if anyone has seen it before.

---

### Post by sally2 on 2014-03-05
Hi Quackers I don't know if you're still monitoring this thread but I've been trying to get this to work for the past few days on my MacBook Pro 10 retina using a 4gb usb and everything works BUT the persistence option. I am able to boot Ubuntu and use it without any problem but I can't get the files I create to stay on the USB. When I configure the persistence option on unetbootin I tried sizes from 256mb to 2048 mb but none of those seemed to work. I'm using syslinux 6.01 with the MBR partition. What's weird is that it seems like the persistence file is being created, because when I look at the USB using gparted after boot I see a difference in "free space" between when i allocated 2gb and 256mb persistence. But for some reason it just refuses to stay. If you happen to have any ideas that'd be great!

edit: there seems to be a bug with 12.04 onwards (even appearing in Trusty) that makes persistence not work on UEFI boots. [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1159016](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1159016) , did you run into this?

---

### Post by Quackers on 2014-03-05
Hi sally2, yes I'm finding the same thing, sadly.
I made one a day or two ago and persistence does not work on that either. I can only assume that something has changed, as you say.
As I don't know what's actually changed I'm not knowledgable enough to do anything about it at the moment.

---

### Post by Quackers on 2014-03-05
Sally2 I've been playing and reading that bug report you linked to.

As a consequence (in OSX) I plugged in the Ubuntu USB and opened it (double-click). I navigated to Boot/Grub and right-clicked on grub.cfg choosing to open with Textedit.
Under the heading ```
menuentry "Try Ubuntu without installing" {
```
I then added "persistent" (no quotes) to the following line before quiet splash then saved the change.
```
linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
```

When I boot holding the Alt key down (on my Mac) with the Ubuntu USB plugged in I get 2 USB icons in the menu.
The first is Windows (presumably because Apple can't conceive of anything else being booted) and the second is EFI Boot. 
On booting the Windows one I set up my wireless connection and changed a couple of things and then rebooted in to the same icon (Windows).
The changes persisted, which is good.
I then rebooted using the EFI Boot option and the changes were still there :-)  That's also good.
So I think my edit to grub.cfg has worked. Have a try for yourself.

---

### Post by sally2 on 2014-03-06
When you tested this was it for Ubuntu 13.10 (64bit) with SysLinux 6.01 or was it the original 13.04+MAC version in the original post? I will try this out as soon as I can on my 13.10 and let you know. Thanks a lot for following up on this, you're great

---

### Post by Quackers on 2014-03-06
It was 13-10 amd64 (non-mac) and Syslinux 6.2 (but that seems to be the same as 6.1, for our purposes). Though for EFI Boot Syslinux isn't used for booting.

---

### Post by sally2 on 2014-03-06
Alright, it works! I had played around with that persistence option before but it never seemd to work, maybe I just need to be more patient. I found that startup can take up to 3 minutes AFTER you click try without installing, and it's overall a little bit slow which is excepted. When I tried booting into the "Windows" partition it said no boot found, but I was able to do everything through the UFI partition without problem.

I got this working on my Mac Mini using a 4GB Sandisk Cruzer USB drive. Thanks for the help and speed at which you responded to this, I really appreciate it. People like you make the Ubuntu community awesome!!

---

### Post by Quackers on 2014-03-06
Glad it works for you too  ):P

I've added an addendum to the original post to give details of this edit.

I too was surprised by how long it takes to boot using the EFI Boot option. I would have thought that EFI Boot would be faster than "Windows" (bios) boot.
I'm only using a USB 2.0 flash drive so it won't be as fast as USB 3.0 but even so it should still be faster I think.

Using the Windows option on mine I get a unetbootin menu where I can choose to "try ubuntu without installing" and on choosing that the screen flashes black then the same menu appears again with my previous choice highlighted. Pressing the enter key again allows Ubuntu Live session to boot.
Do you see the same thing, or not?

---

### Post by sally2 on 2014-03-06
When I use the Windows option it just says something like, "no boot partition found, press any key to reboot". ONCE when I clicked Windows (different USB, same methodology) I got a menu with only "default" as the option and when i loaded into it it just gave me this weird shell. When I booted into UFI on this USB, I did have persistence working, but I only allocated 32MB so I wasn't able to test it thoroughly.

---

### Post by Quackers on 2014-03-06
Hmm I've heard of this before but I haven't seen it myself on any of the USB's I've made. Maybe it's a difference in the Mac's?
At least you're up and running with persistence in EFI now.

---

### Post by sally2 on 2014-03-06
Another thing to note for people who are trying to use these instructions. I tried running this setup on a Mac pro from 2008, and when I booted all I saw was a couple purple blocks, and a bunch of green/purple artifacts on the screen. From what I've read  that this due to some graphics card issue that conflicts with Ubuntu. I think I can safely say that live booting Ubuntu on those older laptops just won't work but I've only personally only tried it my 2008 macbook.

---

### Post by Quackers on 2014-03-06
There are boot options which can be employed (such as "nomodeset") which can allow certain graphics cards to boot to a desktop.
Alternatively older versions of Ubuntu (with older kernels) may also be tried for older machines.

---

### Post by sudodus on 2014-03-06
> **sally2 said:**
> ...
I got this working on my Mac Mini using a 4GB Sandisk Cruzer USB drive ...

If you want persistence it is important to have a fast USB drive, for example a good USB 3 pendrive or a USB disk. Sandisk Cruzer is reliable and a good booter, but rather slow, much slower than the USB 2 interface. See this link with some tips for faster pendrives

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

and this link for a general background

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Quackers on 2014-03-06
Thanks sudodus, I've been meaning to invest in some nice shiny USB3 sticks but haven't got around to it yet  :D
I'll put it on my to-do list  ;)

---

### Post by tiffany3 on 2014-03-07
Everything has worked perfectly...except Unetbootin. I've been watching the Activity Monitor, and when I click OK on unetbootin, it shows up as Active but then, about 30 seconds later, it is inactive, and then, about 30 seconds after that, it's active again! unetbootin app has been sitting there appearing to do nothing. Nothing tells me it's doing anything! What could be going on?

---

### Post by Quackers on 2014-03-07
If you're using persistence Unetbootin can take a while. Some of my sticks took 20 minutes or so - one even took half an hour.
I know it seems to sit there doing nothing and sometimes you will even see the coloured rainbow wheel, but just leave it. Go and have a cup of tea and watch the telly :-)
I haven't had one that failed yet - it's just slow and appears to stop, but it doesn't.

---

### Post by tiffany3 on 2014-03-07
ok, I'll be a little bit more patient. It's hard when i've been at this for 20 hours now (yes, I've been counting!) ](*,)

---

### Post by Quackers on 2014-03-07
Have a lie down :-)

---

### Post by tiffany3 on 2014-03-07
i'm going to have to try another option. it's been over an hour and nothing from unetbootin. there are long spells of it in the Active Processes portion of the Activity Monitor, then it disappears, then it's back...but over an hour?!  will it be ok to leave the ext hard drive partitioned and all or should i erase/repartition?

---

### Post by Quackers on 2014-03-07
That's too long. Is the USB stick alright? Have you use it recently for anything else? How is it formatted? Can you try another?
Yes, it should be fine to leave the drive partitioned.

---

### Post by tiffany3 on 2014-03-07
background information: 
Seagate GoFlex Desk 2.0TB 3.0USB, bought new; never used; formatted MS-DOS (FAT) with MBR checked...all 3 partitions
Working on iMac 24" intel Core2Duo Extreme 2.8GHz 4GB 

I have an iMac 20" with a blown internal hard drive. I'm not sure of the specs except that it's RAM was up'ed to 4 GB. I'm wanting to use the external hard drive to "store" other operating systems (ubuntu, and if possible, steam). If the OS is on the external, then i can switch to it on my 24" mac without having to do any partitioning of the internal drive; and, i will be able to use the 20" mac by booting from the external hard drive. And last, this is a class project! 

i've read so much my brain is mixing everything up! gparted, grub2, rEFIt, rEFInd...sudo this, sudo that, cd, dd, sadlkj, fjkl;asdfjlk'sdf!!! 

i'm so close! i can feel it! 

ubuntu os i've downloaded: 13.04 desktop amd64; 13.04 desktop amd64+mac; 12.04 desktop amd64; 12.04 desktop i386; 12.04 server i386
i've downloaded: rEFInd (installed on both Mac 24" - that was an accident - and external hard drive), unetbootin, syslinux-6, mac linux usb loader

---

### Post by tiffany3 on 2014-03-07
actually, now i have to erase and repartition the external. it refuses to mount the partition i made for ubuntu

---

### Post by Quackers on 2014-03-07
Might be time to have a rest and come back to it with fresh eyes and a clear head :-)
I see no reason why it should'nt work though.

---

### Post by tiffany3 on 2014-03-07
Finally! Unfortunately, the unetbootin way did not work for me. What did work: repartition external with Ubuntu as 1st partition. Install rEFInd on Ubuntu partition. Used Mac Linux USB loader and Ubuntu 12.04 desktop i386. Holding option, rEFInd appeared with 2 EFI drives. I chose the one that resembled a hard drive, and not the one that resembled a usb drive. Then I was prompted either 1. Load Linux Boot (ISO)... or 2. Advanced Formatting. I chose #2. There were a number of options...I chose: noefi and something about GPT...sorry I can't remember!  I was able to get Ubuntu onto my Mac 24" through the external hard drive! :biggrin:

Now what should i do?! I'd really like to understand why your way did not work, and my way did. It shouldn't matter if the internal drive is working or not, right, as I'm booting from an external drive. Will the external work if I hook it up to a Windows computer? 

I am going to go through this again step by step and write it all down. may be it'll work for someone else.

---

### Post by Quackers on 2014-03-07
To be honest I'm not absolutely sure what you want to achieve.
The point of this thread is to make an Ubuntu Live USB which has persistence and which is bootable on a Mac.
You seem to be trying to install Ubuntu on an external drive. 
Is that correct?

---

### Post by tiffany3 on 2014-03-07
Yes.My goal was to install ubuntu onto an external hard drive. i read through your entire post (and lots and lots of other posts), but i could not get unetbootin to work. i wanted to have the ubuntu operating system on an external drive/usb because the internal drive on my Mac 20" is shot. your tutorial was the most concise and easy to follow (and you've been so kind responding to my posts), and everything worked perfect except unetbootin. i'm sorry if i hijacked your post. it seems i've misunderstood. i thought a bootable ubuntu live usb WAS what i wanted. persistence would be great but i didn't get unetbootin to work, and the mac linux usb loader didn't offer it.

---

### Post by Quackers on 2014-03-07
It's not a case of hijacking the thread. Not at all.
None of the other methods that I know of can create a persistent Live USB. They will boot on a Mac though.
You spoke of a 2 TB USB drive rather than a flash drive.
If you were trying to use that with Unetbootin (depending on the size of persistence file) the process could take a long time. One of mine took half an hour to make and I only allocated 2.6GB of persistence. If you start allocating GB's of persistence the process will lengthen greatly.

So, have you installed Ubuntu on the 2 TB drive or have you created an Ubuntu Live system on a partition of that drive?

---

### Post by tiffany3 on 2014-03-07
I believe that i have created an Ubuntu Live System. I would like to install Ubuntu onto the 2 TB drive. I had no idea this would be so confounding when I started! It's actually been the terminology between different users/posters that has confused the heck outta me. 

The persistence file I was trying to create with unetbootin was only 1GB. 

So the preference for a Live USB is being able to have persistence is my understanding so far, right? And if I were to install the Ubuntu OS onto the 2 TB USB of which I've allocated 666.08 GB to each partition, since I do not have persistence, I would not be able to save files. Is this correct? I do have a flash drive (8 GB) I could use to do this tutorial. but tomorrow. my head hurts :)

---

### Post by Quackers on 2014-03-07
Lol
It depends on what you want and how your system is set up.
I wanted persistence in a Ubuntu Live USB because without it I have to install some packages to get my wifi working. I would have to do that every time I booted the Live USB if it didn't have persistence. It also keeps some other changes that I like to have on a Live USB.

As I said, for a 2.6GB persistence file it took Unetbootin about half an hour to make.
But that was on a flash drive, which is very much quicker than a USB hard drive. This process performed on a hard drive would take much longer.

This process does not install Ubuntu to the flash drive - it merely copies the Ubuntu iso file on to the flash drive and provides for persistence.

If you install Ubuntu on to a hard drive (or a partition within that hard drive) you will automatically have persistence by virtue of the fact that the rest of that partition will act as a persistence file.

---

### Post by tiffany3 on 2014-03-07
i'm understanding! it's starting to make sense. the flash drive is a portable "disc" as computers are being made without optical drives. right? i hope i'm right. i want to feel like i've learned something! i really appreciate that you've responded so quickly and you've been very helpful. and incredibly patient :) you, sir, are awesome.

---

### Post by Quackers on 2014-03-07
Yes, that's right. They are flash drives, in that they use flash memory rather than a spinning hard drive (and yes, they are replacing optical drives).
Their advantage is that their read/write speeds are far better than spinning hard drives. USB 2.0 was better than USB 1.1 and now USB 3.0 is much faster than 2.0
They leave spinning hard drives in their wake!
Some laptops now come equipped with flash memory type drives, though these are not USB but PCI or even PCIe which makes them even faster than USB flash drives.
But that's a whole different story :-)
Enjoy your learning curve!

Oh, beware if you choose to install Ubuntu on to an external drive - there are pitfalls!
The first is to make sure you are using the correct drive and then the correct partition - in the partitioning phase.
The second (and more important for your existing system) is that grub will install to the default destination (usually /dev/sda) which may not be where you want it to go.
You have to change that manually and this can only be done in the "something else" option of the Ubuntu installer.
You DON'T want grub to be installed to the hard drive of the computer you are using - it MUST be installed to the external hard drive or your current system may refuse to boot next time! This may often be /dev/sdb or /dev/sdc even.
This needs to be checked and double-checked, if you go down this route.

---

### Post by sally2 on 2014-03-08
Hey, I noticed you wrote in the addendum with the persistent fix,  "[COLOR=#000000]At least it's currently working for me and one other [/COLOR]:smile:". I can confirm that with the persistent keyword being added to the grub.cfg file, persistence has worked worked for several different people that I'm managing who have macbooks that range from the years 2011 to late 2013 on MPBs, MPB-R, Airs, and mac mini (Running 10.9 and 10.8). The other thing I noticed while helping install all of these is that ( like[COLOR=#000000] sudosus mentioned) USB quality is a LOT to do with how fast it takes for the iso to burn using unetbootin. One flash drive that was used was able to burn in something like 11 minutes, while another took a little over 30, (all being burnt on the same computer). All were usb 2.0. 

One thing you may want to add to the OP is that when using persistence, boot up and shutdown can take a couple minutes, and if the user hard resets the computer with their shutdown button it corrupts the filesystem and renders the live boot unusable. I saw this happen a few times. Also, It seems like it takes slightly longer to boot/reset as the persistent FS gets filled. Cheers!![/COLOR]

---

### Post by Quackers on 2014-03-08
Thanks for the updates sally2 :-)
Speeds of flash drives definitely differ wildly.
I wasn't aware of any problems caused by a hard shutdown. I haven't had the need to do a hard shutdown so far :-)
Cheers :)

---

### Post by sudodus on 2014-03-09
> **sally2 said:**
> ...[COLOR=#000000]

One thing you may want to add to the OP is that when using persistence, boot up and shutdown can take a couple minutes, and if the user hard resets the computer with their shutdown button it corrupts the filesystem and renders the live boot unusable. I saw this happen a few times. Also, It seems like it takes slightly longer to boot/reset as the persistent FS gets filled. Cheers!![/COLOR]

+1 :-)

Maybe I would add, that unplugging the USB drive before it has finished shutdown is as bad as hard reset.

---

### Post by turbolego on 2014-03-28
I can't get this to work, i'm stuck at "write".

Please advice.
> 
diskutil list

sudo fdisk -e /dev/rdisk2

Password:
fdisk: could not open MBR file /usr/standalone/i386/boot0: No such file or directory
Enter 'help' for information
fdisk: 1> f 1
Partition 1 marked active.
fdisk:*1> write
Device could not be accessed exclusively.
A reboot will be needed for changes to take effect. OK? [n] y
Writing MBR at offset 0.


If i select y:

> 
sudo dd conv=notrunc bs=440 count=1 if=mbr.bin of=/dev/disk2
dd: /dev/disk2: Resource busy

---

### Post by Quackers on 2014-03-28
Does the USB device show up on your desktop? If so run the unmount command first.

---

### Post by turbolego on 2014-03-28
i'm still getting "Resource busy"

> /dev/disk2   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *8.4 GB     disk2
   1:                 DOS_FAT_32 UNTITLED                8.4 GB     disk2s1
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ diskutil unmountDisk /dev/disk2
Unmount of all volumes on disk2 was successful
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ sudo fdisk -e /dev/rdisk2
fdisk: could not open MBR file /usr/standalone/i386/boot0: No such file or directory
Enter 'help' for information
fdisk: 1> f 1
Partition 1 marked active.
fdisk:*1> write
Writing MBR at offset 0.
fdisk: 1> exit
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ sudo dd conv=notrunc bs=440 count=1 if=/Users/TURBOLEGO/Desktop/oculus/syslinux-6.02/bios/mbr/mbr.bin of=/dev/disk2
dd: /dev/disk2: Resource busy
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ 

i tried reformatting it in disk utility too, same error.
should i partition it in some special way?

---

### Post by Quackers on 2014-03-28
Does the USB device appear on your desktop?

---

### Post by turbolego on 2014-03-28
yup, seems like i had to unmount it twice... seems to be working now.

transcript:

> /dev/disk2   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *8.4 GB     disk2
   1:                 DOS_FAT_32 UNTITLED                8.4 GB     disk2s1
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ diskutil unmountDisk /dev/disk2
**Unmount of all volumes on disk2 was successful**
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ sudo fdisk -e /dev/rdisk2
fdisk: could not open MBR file /usr/standalone/i386/boot0: No such file or directory
Enter 'help' for information
fdisk: 1> f 1
Partition 1 marked active.
fdisk:*1> write
Writing MBR at offset 0.
fdisk: 1> exit
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ sudo dd conv=notrunc bs=440 count=1 if=/Users/TURBOLEGO/Desktop/oculus/syslinux-6.02/bios/mbr/mbr.bin of=/dev/disk2
dd: /dev/disk2: Resource busy
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ diskutil unmountDisk /dev/disk2
**Unmount of all volumes on disk2 was successful**
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ sudo dd conv=notrunc bs=440 count=1 if=/Users/TURBOLEGO/Desktop/oculus/syslinux-6.02/bios/mbr/mbr.bin of=/dev/disk2
1+0 records in
1+0 records out
440 bytes transferred in 0.003603 secs (122121 bytes/sec)
TURBOLEGOs-MacBook-Pro:mbr TURBOLEGO$ 

thanks!

---

### Post by Quackers on 2014-03-28
That's better :-)

---

### Post by turbolego on 2014-03-28
I got persistence working now, but now everything is very slow and choppy at times.

Is there a reason for this?

Will persistence make everything slower?

---

### Post by sudodus on 2014-03-28
A persistent live system is slower than a live system without persistence. You can compensate for that by using a fast pendrive. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

### Post by Quackers on 2014-03-28
> **turbolego said:**
> I got persistence working now, but now everything is very slow and choppy at times.

Is there a reason for this?

Will persistence make everything slower?
Yes, USB devices are slower than hard drives - sort of. Especially if using USB2 devices.
It's not as slow as having to do all previously done changes over again :-)

See sudodus' post above.

---

### Post by turbolego on 2014-03-28
welp... i got only usb2... so i`m gonna get my firewire drive then, at least that`s faster.

---

### Post by turbolego on 2014-03-28
Hm... i did the same procedure on my 500 gb firewire-disk, but unetbootin doesn't do anything when i click "OK" after selecting the drive and preserved space...

any tips?

**[EDIT:]**

would this work?

1. boot up ubuntu from usb
2. select the "install ubuntu" app
3. install ubuntu from within the ubuntu usb on to the firewire disk
4. <something about persistence here>

**[EDIT2:]**

I`m stuck at "erase and install ubuntu"
the cursor still has the "loading" idicator symbol rolling, but i`m not sure how long it should stay on this screen...

picture:
[[IMG]http://i.imgur.com/ceA9Kic.png[/IMG]](http://imgur.com/ceA9Kic)

---

### Post by turbolego on 2014-03-29
Ok... so i tried the same procedure that worked on my usb-stick on my firewire disk.

The only way to make the firewire-disk boot, is if i DON'T edit the grub.cfg file and leave the usb (with persistence) connected!
I think the usb has some files or whatever that the firewire needs to have in order to boot...

This is what shows up if i try to boot the firewire, without persistence, and without the usb:

[IMG]http://i.imgur.com/DW4nr8n.png[/IMG]

This is what happens if i try to boot the firewire, WITH persistence and WITH the usb:

[IMG]http://i.imgur.com/kiVqLvR.png[/IMG]

What's going on?

---

### Post by Quackers on 2014-03-30
This is a whole different subject than what this thread is about  :)

I would have thought that installing Ubuntu on to the firewire disc would be better (as it would automatically be persistent), however, I think there are problems installing it on firewire.
Try googling around as I think I read about possible workarounds.
Sorry but that's all I can offer.

---

### Post by curious3 on 2014-04-07
This is excellent...it works exactly as described. The instructions are excellent.

Do you or anyone else have any information on how to make an encrypted install on a USB. I have not been able to make that work.

> **Quackers said:**
> ************
Please see the addendum at the bottom of this post if you're having problems not achieving persistence with a recent version of Ubuntu.


I have been spending a lot of time recently trying to make an Ubuntu Live USB with persistence that will boot on a Mac. 
Persistence is worthwhile having, at least in my case as my wifi does not work "out of the box" so without persistence any driver and firmware that I install once booted to the live desktop would become lost once the system is rebooted. I can obviously have things like Bookmarks for important sites retained too.

I would make the USB with Unetbootin but at the end of the process it would report that this USB would not boot on a Mac. On trying to boot it it would always give either a "Boot error" message or "this is not a bootable disc..........." error.

Most of the information I needed was already available (thanks to Christopher Friedt and others) but it just wouldn't quite work for me. It seemed I was missing a step or something. It seems I was.

Apparently Unetbootin fails to write Syslinux to the MBR of the flash drive (or not correctly, if at all). This could possibly be a licensing kind of thing. It also seems to misread or misinterpret the boot flag or the active partition in some way. If Syslinux is not in the MBR there's nothing to point to where to go to boot anything. 

Anyway, I have just made a 2GB Ubuntu Live USB with persistence following the method below and not only does it boot on a Mac but the persistence actually works! :lolflag:

What you'll need:-
A Mac which is capable of booting from a USB flash drive
A USB stick (2GB upwards in size if you want persistence)
An Ubuntu .iso file - I had Ubuntu 13-04 amd64 for mac - **** if you want EFI boot on a Mac use a non-mac version of the Ubuntu iso
Syslinux (a small downloaded file)
Unetbootin for Mac

OK, here we go:

Plug your USB flash drive into your Mac.

Open a terminal and run
```
diskutil list
```
and in its output note carefully the drive designation of your USB (the size will probably be the giveaway) mine for instance was /dev/disk1 but yours may be something else depending on what else is plugged in to your Mac.

Open Disk Utility and select your USB drive and delete any current partitions. That is click on any partitions in the left pane and in the right pane click erase.
Then click on your USB drive in the left pane and the partition tab in the right pane and create one partition of MS-DOS FAT type naming it anything you want. It's probably wise to click on the options tab and make sure that MBR is ticked. Click on apply.
Ok, once that's run we're finished with Disk Utility.

In the terminal unmount the USB with ```
diskutil unmountDisk /dev/diskX
```  -  changing the X to your drive's number

Now we'll mark the partition as active (even though some programs will already think so, like gparted, for instance)

Open a terminal and run ```
sudo fdisk -e /dev/rdiskX
```  (yes, the extra r is advisable (quicker) and change the X to the number of your USB disc that diskutil gave you earlier)
at this point your prompt will become an fdisk prompt and I got the following message ```
fdisk: could not open MBR file /usr/standalone/i386/boot0: No such file or directory
Enter 'help' for information
``` which I ignored.

now enter these 3 commands ```
f 1
write
exit
```
Please note that you should be able to see your desktop (the area where discs mount) and if at any time during the above the disk appears and stays there run the unmount command again.

Ok, so far so good. 
Now download [syslinux]("https://www.kernel.org/pub/linux/utils/boot/syslinux/")
 
Now it can get a bit messy. In the terminal you need to cd to the folder which has the mbr.bin. 

In syslinux version 6.01 the mbr.bin is in the syslinux-6/bios/mbr folder so that's where you'd need to cd to. 
My (older) version was different (syslinux/mbr) and I've also seen it elsewhere too so you need to have a look where this file is first. If you've extracted the zip file you can have a look in these places for it in the Finder before cd'ing.

Now we can write the much needed code to the MBR of the USB drive

```
sudo dd conv=notrunc bs=440 count=1 if=mbr.bin of=/dev/diskX
```  -  again change the X to your drive's number

After a second or two it should report bytes written count which should be 440.

If this gives an error about not getting access run the unmount command again for your USB (above)

If it gives an error about no mbr.bin then you've cd'd to the wrong part of syslinux folder - possibly!

It may report that the changes won't be made unless you reboot. If it does just type y and enter, then reboot.

Ok now download and install Unetbootin for Macs and use it in the normal way to make the Live USB choosing if you wish to make the persistence file by entering a size in the appropriate field.
It will give the usual guff about what it's doing and may even appear to hang for a while, even give the spinning coloured wheel - just leave it running. It could take about 20 minutes or so, maybe a touch more but leave it anyway.

It will finish and report that the USB will not be bootable on a Mac.  Bah, humbug! 

Reboot leaving your USB flash drive inserted and if you don't have rEFInd installed hold the Option (ALT) key after the chime until the appropriate menu choices appear. 
If you have rEFInd installed you'll see a nice penguin at the end - choose that
If no rEFInd choose the one that wasn't there before (can't remember as I use rEFInd).

You should be greeted by a Unetbootin menu with Default as the top option. You only have a few seconds to choose but my menu included an option to "try Ubuntu without installing" (3rd item down) and I chose that one. Others have reported no such menu item and have used Default, but that doesn't boot for me.

Ubuntu should start loading. Enjoy!

I loaded Ubuntu desktop and changed some wifi setting as my wifi doesn't work out of the box and installed one or two things in the sidebar.
I then rebooted and those changes were still there! Wifi worked without any changes. 
ie persistence now works!! Something I have never got to work before.


As stated above this is what worked for me. It is not guaranteed and if you break something it's on your head!
For instance if you make a mistake entering any of these commands you WILL VERY POSSIBLY destroy data on another drive!!!!!!! Be very careful!!!

This information has been gathered from many sources including the [syslinux.wiki]("http://www.syslinux.org/wiki/index.php/SYSLINUX"), Christopher Friedt's sites 
[http://dropsafe.crypticide.com/article/8368](http://dropsafe.crypticide.com/article/8368)
and
[http://perpetual-notion.blogspot.co.uk/2011/08/unetbootin-on-mac-os-x.html](http://perpetual-notion.blogspot.co.uk/2011/08/unetbootin-on-mac-os-x.html)
and much trawling through the Net.

Having said all that if you come across any problems I will try to help - though I am no coder!

****** ADDENDUM********
It seems in more recent versions of Ubuntu that the persistence can fail (particularly if booted in EFI).
I've had a mooch around and thanks to others there may be a fix. At least it's currently working for me and one other :-)

I plugged the newly made USB in to my Mac and opened the drive then navigated to /boot/grub then opened grub.cfg with textedit
In the newly opened file go to this menu entry 
```
menuentry "Try Ubuntu without installing" {
``` which is the first one in the file.
Just further down the file is the line below to which I've added the word "persistent"
```
linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper [COLOR=#FF0000]persistent[/COLOR] quiet splash --
```
Once added you can save the file and then boot from it and hopefully have persistence.
 
Good luck!

---

### Post by Quackers on 2014-04-07
Thank you for your comments and I'm happy to hear that all went well :-)
Sadly encryption is a layer of complexity too far for me. I have no need for encryption so it's not something I've ever tried.
I try to keep installations as simple as possible (so there's less to go wrong!) so can't help you there other than to say that I'm sure there will be guides around here or on the net for what you want to do.

---

### Post by k4ranger2 on 2014-10-17
Worked!

USB-stick: Kingston 16.06GB

I used backbox-4.0-amd64.iso (persistance didn't work, I booted in EFI. Will try to edit grub.cfg later.)

syslinux: version 6.03

mbr.bin was in syslinux-6/bios/mbr

MacBook Air mid 2012
OS X 10.9.5 (Mavericks)

Backbox worked out of the box, no extra driver needed.

EDIT 1: Adding persistance to grub.cfg didn't work. Any ideas?
EDIT 2: My bad! I put persistent in the right line and it worked!
EDIT 3: After updating Backbox I got the same error turbolego got.

---

### Post by raj12 on 2015-01-11
Hi Quackers,
Thank you so much for the instructions and the help you provided to all over the years!  After following your instructions, now I can reboot my mac by holding alt option.  I see three boot options.  one for my mac HD, one called windows, and one called EFI boot.  mac HD takes me to my mac.  Windows option flashes and the system quickly reboots to my default mach HD.  The EFI boot option gives a screen that has few options to select from.
1. Try without installing UBUNTU
2. Install UBUNTU
and 1 or 2 more options that I cannot recall exactly.

I can use option 1 (Try without install) and login to Ubuntu just fine.  But I want to install UBUNTU and run from the same USB stick.  I am assuming that when I choose the install UBUNT&#8203;U option (option # 2) it will give me an option to install the OS to this USB drive.  Is that possible or do I need to have a fresh and additional USB drive to install the UBUNTU OS into?

I am installing Ubuntu 14.04 LTS
Syslinunx version 6.03
Persistance size of 2 GB entered for unetbootin options.
I am running 10.10 Yosemite on Mackbook Air
USB stick size: 8GB

Thank you in advance for your help.

Regards,
Raj

---

### Post by Quackers on 2015-01-12
You would need another USB stick or drive to install Ubuntu on to.
You currently have an Ubuntu system on your current USB stick which you can use as is. You should also have persistence, i.e. you can change things and store things and it will remember those changes.
By selecting the "try Ubuntu without installing" option you will boot into that system.

Beware! If you install Ubuntu from this USB to another USB or drive you need to be sure of that drive's designation (i.e. /dev/sdb, /dev/sdc etc) and be sure to install to that drive. Otherwise you could erase a system you currently use (like your Yosemite, for instance!)

---

### Post by jwgsub on 2015-01-12
Hi, I first attempted to do this a few years ago probably 2012, but can't get it to work. I tried using syslunix 6.03, Ubuntu 14.04 desktop for Mac, used the terminal commands without a problem, selected 2 gigs for the persistent space, and tried to boot it.  In the past it has booted, but not saved to the persistence file and after searching the internet I finally gave up.  Today, I plugged it in, restarted my computer and held option, but only my MacintoshHD drive came up.  

I would appreciate any help on this subject as well as other ways to make it persistent.  I have tried just about every solution on the internet and am counting on the masters to help me out.



Thank you

-Jeremy:confused:

---

### Post by raj12 on 2015-01-12
Hi 
Thank you for the help.  I understand now.  Couple quick questions
1.  I created a text file on the file system after logging into 'try ubuntu without installing".  But that file did not persist when I rebooted into the OS again.  I thought it should.
2.  It does not recognize my wireless network. 

Again, I appreciate your help.
Raj

---

### Post by Quackers on 2015-01-13
Yes it should have remembered that text file. It seems that persistence is not working there.

Jwgsub
See your private message inbox regarding your earlier questions.
Not much help I'm afraid for you.

---

### Post by asim3 on 2015-03-24
> **Quackers said:**
> ************
Good luck!

Hi Quackers,

Thank you very much for such a detailed tutorial. You're indeed such a wonderful and humble human being. I don't know if you're still maintaining this thread or not, but i'm giving it a try here while quoting your original post.

I'm new to this forum (even to Linux OS), and I followed your tutorial bit-by-bit to install Ubuntu 14.10 on MBP 5,2 (Mid 2009 Model). Everything goes okay, but as soon as I select ''Try Ubuntu without Installing", I got the following error,

[IMG]http://s8.postimg.org/nbo7zwbc5/image.jpg[/IMG]

I force Shut Down MBP, and went for a second try... now this time it went past the first error, and end up with the following,

[IMG]http://s10.postimg.org/ue0rd7vfd/image.jpg[/IMG]

Could you please tell me what I'm doing wrong, or is it that my machine is not compatible?

Regards
Asim

---

### Post by Quackers on 2015-03-26
Hi Asim, it maybe that the hardware you're using is too old for that version of Ubuntu.
The second screenshot shows a kernel panic, probably due to the nouveau video driver.
When you get to that stage next time try using a boot prompt. Sadly I work away all week and have no links with me. Perhaps you could google the boot prompts available for video problems and see if you can get it to boot that way.
Sorry I can't be more helpful.

You could possibly try an older version of Ubuntu, say a. Erosion issued a year or so after your hardware was new.

---

### Post by jwgsub on 2015-05-30
I finally got the drive working all the way! Thanks so much for all the instructions!

-Jeremy

---

