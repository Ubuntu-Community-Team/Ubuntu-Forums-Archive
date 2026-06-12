---
title: "Installing Ubuntu 5.0.6 on an iMac CRT G3 - The Installation Experience"
date: 2006-07-18
forum: Apple PPC Users
---

### Post by GREGMACKENZIE on 2006-07-18
Hi All, 

This is my first post.

I'd been following Ubuntu for a while and wanting to install it on my aging IBM 380 laptop but I felt that the laptop was a bit underpowered (96 mb of ram). So, when my son gave me a CRT iMac he rescued from going to a landfill I saw my chance to finally give the Ubuntu OS a try.

I wanted to install Ubuntu mostly because it is a community OS and also because I didn't have any license/disks for the Apple OS currently on the crt iMac. I confirmed that the iMac would boot under its current OS, so it was working just fine. This particular crt iMac G3 was an early 333 mhz tray loader CD-ROM model with 288mb of ram and the RagePro video card, with a 6 gb hard drive. It came with an apple single button mouse and keyboard, both usb.

I don't have any real experience with Ubuntu or Linux. However, I've used both the Mac and Windows OS for a number of years. So, I didn't feel intimidated by any potential command line stuff I might have to enter even though it might be different from what I was used to.

I had ordered CDs to distribute to all my (cough) "geek" friends and had both version 5.0.6, and the latest Dapper Drake v6 install of Ubuntu. I'm on dial up and downloading is not really an option for super large files so ordering the OS on cd is perfect. Thanks for sending it! 

The first step was to see if the live disk would work. So, I booted the iMac, and once OS X was running I then inserted the 5.0.6 live cd. I rebooted the iMac using the menu, and on restart began holding down the "c" key to get it to boot from the CD-ROM. Once the CD-ROM started the live CD was running.

Basically, the screen was initially black, some information was displayed, and "boot:" appears as the last line. If you push the enter button on the keyboard it chugs along nicely. A GUI appears and I was asked about the keyboard, and location, and after a few minutes Ubuntu 5.0.6 live desktop was running. Neat! Having satisfied myself that 5.0.6 would work on the iMac, I then shut down, and the cd ejected. Groovy. 

Another reboot to the Mac OS quickly followed, and this time I put in the latest Dapper Drake CD since I really wanted to install that, and confirm it would work. I immediately ran into a problem, as the Dapper Drake v6 cd would only get so far. I should have written down exactly what the display said. 

Basically, the screen was initially black, some information was displayed, and "boot:" appears as the last line. If you push the enter button on the keyboard it chugs along briefly and then a white screen pops up with some cryptic text. Well, cryptic to me at this stage anyway. I should have written it down. The last line then says "ok". At this point I wasn't really able to do anything with it. Eventually I'll consult the Ubuntu community for more information about installing Dapper Drake. Obviously something went wrong.

However, in the meantime since the live Ubuntu 5.0.6 worked just fine (Hoary Hedgehog?) I elected to install this earlier version until I could figure out the Dapper Drake install problem and/or upgrade to it. I pressed the iMac power button to shut down. On rebooting to the Mac OS I then switched to the 5.0.6 install cd, rebooted and held down the "c" key. In short order I found myself at the "boot:" command prompt. I pushed the enter key.

A few general comments are in order here. The 5.0.6 install is pleasant and simple. If the live cd works on your computer the installer cd should run. If anyone can answer a few questions they can install Ubuntu. Basically all the install session does is ask basic questions in a simple GUI (graphical user interface). I was presented with the following:

I was asked if I wanted to completely wipe the drive, install Ubuntu on a partition, etc. Throwing caution to the wind I elected to wipe the drive and make Ubuntu my OS of choice. Brave or what? Actually this is what I wanted to do from square one but it may not be the ideal for others.

What sort of network was I using? The default was DCHP. I used the down arrow to move the selection to configure later as I don't have a network.

I was asked about my location, and keyboard. Simple enough, Canada, and English.

I was asked in succession to type in my name, then a user name, and finally a password. You type each in and then follow it by pressing enter. 

The user name must start with a lower case letter. 

The password box really threw me off at first as the cursor didn't move as I typed on the keyboard. I got lost! However you can go backwards and do it over. I used the down arrow to hilight the text to take you back one step, and by pressing enter, returned to the previous GUI window; to press enter again and start the next window over again. I got it right and was asked to confirm the password again. This is nothing anyone should be afraid of.

At this point the installation gets a bit boring as line upon line of installation process feedback rolls by. However after refreshments one returns to the computer screen to find it asking for the removal of the installation cd, upon which it informs you that it has more stuff to install on its own and will reboot itself when completed. I removed the cd, I believe I may have had to press enter again, and the installation continues. More installation information rolls by. Oh dear time to find something else to do.

When I returned to the iMac I found the screen dark, the monitor power saver feature must have kicked in by default because as soon as I wiggled the mouse the monitor came back to life and there was the Ubuntu Log-in screen waiting for me. Woo Hoo!

I typed in my username and password and then there I was at the Ubuntu Desktop. Groovy!

I'll have to figure out if I can upgrade to the Dapper Drake from the cd later on. However, for now I'm just happy I've got a working 5.0.6 Ubuntu OS! I still have yet to work out how to connect my printer, joystick, cd burner, and camera, more fun for later on!

Greg
:-)

---

### Post by linear on 2006-07-18
Both Breezy and Dapper don't set up xorg.conf correctly for the iMac G3. You can search the forums for more info and fixes when you're ready to upgrade.

I believe the recommended path to Dapper is first upgrade from Hoary to Breezy, then Breezy to Dapper. Check the [wiki]("http://wiki.ubuntu.com") for details.

It's supposedly possible to do an upgrade via the alternate install CD, but I haven't seen instructions anywhere.

Good luck!

---

### Post by avtolle on 2006-07-18
Linear is correct, as I understand. Once you're ready to install Hoary, and have it as you want, then you should go to Breezy. Once that is done, you may then (if you want) upgrade to Dapper w/out obtaining installation disks, or you may do a total clean install from CD. I would also opine that when you are ready for Dapper, you should obtain an "alternate" CD, which uses the text based installer. Of course, when that time comes, Edgy may be released.:) Good luck.

---

### Post by GREGMACKENZIE on 2006-07-18
Hi,

Thanks for the replies! Ah, I knew there was a trick in there somewhere to get 6 installed. Well, I obviously need to get in some reading before trying either the upgrade path or just the direct install to Dapper Drake. Of the two the direct install would be far easier and more appealing as images are too large for me to download. As you may have guessed I have two of the three releases. When there is a new release I usually ask for the disks. I may experiment a little with Ubuntu to see what I can learn before I do any upgrade. I've sure got a learning curve ahead of me.

Greg
:-)

---

### Post by avtolle on 2006-07-18
You need to be aware that the CD you receive from Shipit is the Desktop CD, and its installer is a bit shaky (to put it kindly). The only way to obtain the Alternate Install CD is to download and burn ISO, AFAIK. Also, it is my understanding and belief that the kernel on the so-called "live" CD is not the same as on the Alternate Install CD; and, FYI, since installing Dapper in mid-June, there have been 3 or 4 kernel updates, one or more of which will (hopefully) take care of some of the issues Linear referenced. Again, best wishes and good luck.

---

