---
title: "Live CD 6.06 hanging at kernel booting"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Myrgen on 2007-01-18
Hello,
I am running Dapper on one machine, without any problem. Wanted to install Dapper on the other machine. This other machine runs Windows XP Pro, has 40 Gb HD, 256 RAM, AMD chip, (not AMD 64!).All data are backed up so the HD can be wiped clean if needed.
I downloaded the latest version of Dapper Drake, burned a fresh CD, and rebooted with the CD in the drive. The splash screen 'Ubuntu' displays nicely, and I select 'run or install Ubuntu'. It decompresses Linux without error message, then goes to black screen, displaying "booting kernel..."... and stays there forever.. 
Anything I should be doing that I am not doing?
Thanks for your help!

---

### Post by ubdai on 2007-01-18
Try disconnecting any external devices usb hubs, card readers etc.

This may help. It did for me.

ubdai

---

### Post by Myrgen on 2007-01-18
Thank you for your help, but it didn't work. I unplugged ethernet cable, speakers, printer, leaving only monitor, keyboard and mouse plugged in. Same result: it hangs at 'booting kernel' :(

---

### Post by pscout on 2007-01-18
I had the same problem with 6.06 on a 6600/ds3 rig.

I had previously loaded 6.10 successfully on a few other intel/asus rigs without problem so i tried it on the 6600/ds3 and it installed fine.

This is my first post here ... i am now trying to find out why ia32.libs won't install for me on this 6.10 setup since i had no problem with it on 4 other 6.10 setups. :(

Good luck.

---

### Post by Myrgen on 2007-01-19
I've now disconnected -and- removed all unecessary peripherals. This computer is bare bones: HD, CD/DVD player, ethernet card, mother board with AMD chip and integrated Radeon Video. And still nothing??!! Would anyone have some more ideas on how I could install Ubuntu there?? Thanks

---

### Post by healthpellets on 2007-01-19
I had this same problem when i first tried to use the 6.06 or the 6.10 Live CDs.  

Now, I can't tell you exactly what the problem was, but in the first instance I was at home downloading the ISO over a slow DSL connection (took about 7 hours), and then I went to my girlfriend's house and used a much faster DSL connection (1 hour to download), and I had no problems with the install after that.

So if someone knows why this happened, I'd be interested in knowing.

---

### Post by pscout on 2007-01-19
> **Myrgen said:**
> I've now disconnected -and- removed all unecessary peripherals. This computer is bare bones: HD, CD/DVD player, ethernet card, mother board with AMD chip and integrated Radeon Video. And still nothing??!! Would anyone have some more ideas on how I could install Ubuntu there?? Thanks

Beyond removing things physically, did you disable all uncessary hardware in bios?

Did you try 6.10?   I am certainly no expert but it worked for me where 6.06 wouldn't with the exact same symptoms that you have.

I now have 7 rigs running it and other than a slight dificulty in getting the ia32.libs installed on the last setup, it has been running fine.   I don't use many of the features but it looks exactly the same to my untrained eye as 6.06.  I run just run folding on mine 724, and use the browser a bit.  My only customization have been to configure network to static ip and set autologon for my id.

I also had  the same symptoms as you on another rig i tried to put 6.10 on a p5wd2-E ... so this weekend i will likely try to put 6.06 on it to see if that avoids whatever problem 6.10 has with it.   

The only reason i even have the 6.06 cd is becuz i set it up on another rig under wxp and free vmware server so that i could gpu fold under wxp and smp fold under 64 bit linux on the same rig.


Hmmmm ... that just gave me another thought ... are you installing the 32 bit or 64 bit version .... maybe that has something to do with it?   Mine are all the 64 bit version.

And here is another thought ... i read on the vmware site that it is also a good workaround for getting linux installed on machines the have compatibility issues with linux.  It is really quite painless to install and since it virtuallizes all the hardware, it may just work for you assuming your hardware is compatible.  You don't even have to setup partitions for it on your hd.  The wmware server for windows is all you need ... it is free but you have to register to get a licence key.   With vmware you can run windows and linux at the same time ... pretty cool.  On intel many of the D processors support virtualization and all the conroes.  Not sure what the feature is called on AMD cpu's.


Good luck :)

---

### Post by az on 2007-01-19
> **Myrgen said:**
> Hello,
I am running Dapper on one machine, without any problem. Wanted to install Dapper on the other machine. This other machine runs Windows XP Pro, has 40 Gb HD, 256 RAM, AMD chip, 

Some combinations of older optical drives and fast processors can create problems like this.  I have heard this about installing Windows, too.  Some people have had success with bruning the cd at a really slow speed (like 4x).  You may also have success by using a different optical drive.

I had one old laptop that would install fine one time, but If I tried to install a second time in the same day (I was trying daily builds of the Hoary installer) it would fail.  I guess it the poor thing was overheating.  Or something.

---

### Post by Myrgen on 2007-01-19
I'm trying to install the 32bit version. I have a 512 DSL connection, which isn't that great, but still ok. I must say, though, that on the machine running Ubuntu successfully, I first installed 5.01 (a while back), /then/ when it came out, upgraded it to 6.06. So maybe I should try the same strategy.. Thanks for your help and if this isn't working, I'll try wmware :)

---

### Post by pscout on 2007-01-19
> **Myrgen said:**
> I'm trying to install the 32bit version. I have a 512 DSL connection, which isn't that great, but still ok. I must say, though, that on the machine running Ubuntu successfully, I first installed 5.01 (a while back), /then/ when it came out, upgraded it to 6.06. So maybe I should try the same strategy.. Thanks for your help and if this isn't working, I'll try wmware :)


Just noticed that your rig is 256 mb ... that may be a bit small to run wxp and vmware and linux decently ... although i have read that vmware does a good job of swapping out unused memory.
My rigs are all 1gb minimum ... task mgr is showing my lunux process using 282 mb atm. but top in linux is showing a lot less for my folding app in res which i am guessing is how much of the virtual mem is resident..

---

### Post by Myrgen on 2007-01-19
Yes, I came to the same conclusion. Ihave 2 machines with 750 RAM, and that problematic one with 256 only. I think it is time to give them all a serious boost and to splurge on memory for all 3. I'll keep you posted. A heartfelt thanks to all who tried to help, though!

---

### Post by piller on 2007-01-19
Memory might be the problem.  You might also try the Alternate Install CD.

---

### Post by Myrgen on 2007-02-01
Latest news: I upgraded de memory (it now has 512). The HD has 20G free space, and yet I'm still unable to install 6.06.
I disabled USB stuff in the bios, disconnected all that wasn't necessary (keyboard and mouse excepted), and still no joy!
Any more ideas I could try? :)

---

### Post by Moulton on 2007-02-02
If you have just burned a fresh CD from ISO and have not verified the burn, you should check to make sure it's an error-free burn.

You could try to use the CD to boot your other machine and see if everything works properly, or if the same error occurs.  If so, suspect the burn to be erratic.

Another way to test the CD is to find the utilities to compute the MD5 checksum from the CD (do this on your good machine) and compare it to the published MD5 for the ISO that you downloaded.  You can also compute the MD5 from the downloaded ISO image as well.  All three figures should agree.  If not, you have an erratic copy of the ISO image or an erratic burn.

---

### Post by Myrgen on 2007-02-03
Thank you for your help. I re-downloaed both a LiveCD and an Alternate. Checked CHKSUM, both on the downloaded iso and the burnt discs. Tried again, no joy. I then tried to do a net install, by downloading the kernel 'linux', and grub4dos, following the instructions on another thread of this forum. No joy: it was asking me for the HAL.dll that /windows/ couldn't find!!!. Otherwise, with the CDs, I have /always/ the same error (I set the boot to be not 'quiet'): the error message is 'can't find DSDT'. It occurs after the ACPI line. I tried then to boot with acpi=off, but the process still stops right at the same line. I am starting to believe that this machine has Windows ingrained in the bios (just kidding!) ;)
Sorry for this un-technical post, I'm not really technical, if I know my way around most stuff, just being very new to Linux.

---

