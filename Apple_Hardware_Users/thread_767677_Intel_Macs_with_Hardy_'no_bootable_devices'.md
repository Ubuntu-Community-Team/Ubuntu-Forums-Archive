---
title: "Intel Macs with Hardy 'no bootable devices'"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by cyberdork33 on 2008-04-25
After installing Ubuntu on an Intel Mac, you may get a 'no bootable devices' error or simply a blinking cursor after choosing Ubuntu with rEFIt., or no other operating systems show up at all when holding the Option key on startup. (You may also get a Question Mark Folder on startup). There is a bug in the installer that wipes out information about your partitions in the MBR. This data is required in order to boot what Apple calls "legacy" operating systems (meaning linux, windows).
[COLOR=Red][B]
WARNING: For those that have very complicated multi-boot systems (numerous installs of linux and/or windows). This may leave some of your installs unbootable. Please post in the forum to get specialized help with your setup.[/B][/COLOR] 

[SIZE=3]**If you Dual-Boot or Triple-Boot:**[/SIZE]


[LIST=1]
[*]If you have the Question Mark Folder icon as descied above then you will need to create a rEFIt CD or install it on a USB key. Otherwise, you can install it normally from within OS X.
[*]Once you boot into the rEFIt menu, choose to start the partition tool. It will ask if you want to sync your partitions. Say yes. after rebooting, you should be able to select the Linux icon in rEFIt and it will boot into your Ubuntu install.
[*]_PLEASE _add your comment to this bug report. This is a serious issue and should be addressed. It will not get attention unless it affects a lot of people: [https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/222126](https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/222126)
[/LIST]
**[SIZE=3]Additional Problems:[/SIZE]**

After all this, choosing to boot linux from refit can cause a freeze on the Tux logo or still other problems actually booting the OS. Many people have reported this problem to go away if they power down (completely, not reboot) and try to boot into Linux a few times. Please try this first.

If that doesn't work, reinstalling Grub seems to work. Directions are here:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)
Although it indicates that you should install to the Ubuntu partition, you may very likely end up with two boot options if you do. Just install to the MBR unless you also have / want to install windows.

---

### Post by Chaz_UK on 2008-04-26
I've been trying for days to gat a dual Leopard/Ubuntu setup on my mini with that same error wand was just going to post a thread asking about what to do.

Thanks for posting this! Time to install.

---

### Post by darcyb on 2008-04-29
When I used refit's partition tool to sync the mbr, the behavior went from displaying the blank screen with white text "no bottable device" error, to sitting on a grey screen with the penguin image in the middle indefinitely.

When I did the partitioning with Bootcamp instead of gparted, the error message changed to a blank screen with white text "no operating system found." If I synced the mbr after that experience, I'd again get stuck on the indefinite grey screen with penguin.

---

### Post by Hatfield on 2008-04-29
My experience with a triple-boot malfunction may help some people out.
My triple boot is explained [here](http://ubuntuforums.org/showthread.php?p=3512449#post3512449).Long story short,

I installed Boot Camp, repartitioned the new Boot Camped partition to accommodate Vista AND Ubuntu and installed both.  When I held the Options key, I would have a choice between Mac and Windows.  To get to Linux, I would press Windows which would put me into GRUB where I would have a choice between Ubuntu and Vista.
So Boot Camp Option Key=
Mac=Mac
Windows=Windows or Linux(GRUB)

To clean install 8.04, I deleted the Ubuntu 7.10 partition and its swap and installed 8.04.  But then when I held the Option key at boot-up, it only gave me an option for Mac.  Whoops.
So Boot Camp Option Key=
Mac=Mac and that's it

Enter rEFIt.  Intalled rEFIt and after syncing it gave me a choice of Mac, Linux, and Windows.  But when I choose Linux, it sticks on the gray tux page and stays there.  When I choose Windows, it kicks me over to GRUB like before where I have the choice between Ubuntu and Vista.
So rEFIt menu =
Mac=Mac
Linux=nothing
Windows=Windows or Linux(GRUB)(like before)

Hope this helps.

And I'm getting ready to get rid of the Vista partition.
1)Zero out the hard drive.
2)Repartition with gParted LiveCD.
3)MacOS(10.4 no more boot camp)
4)Ubuntu 8.04
5)rEFIt
I'll update the progress.

---

### Post by darcyb on 2008-04-29
For me, with Bootcamp as the partition solution, I would get a Windows startup icon while holding down the option key too, but pre-resync I would be brought to a "no operating system found" error on a blank screen. After a resync, the windows launch icon sat in the middle of the screen and wouldn't do anything further.

---

### Post by calizu15 on 2008-04-29
I had the same problem and the solution from the 1st post fixed it. Thanks! 
Now if I can figure out the rest of it... =) 

cheers

---

### Post by cyberdork33 on 2008-04-29
> **darcyb said:**
> For me, with Bootcamp as the partition solution, I would get a Windows startup icon while holding down the option key too, but pre-resync I would be brought to a "no operating system found" error on a blank screen. After a resync, the windows launch icon sat in the middle of the screen and wouldn't do anything further.
I still think you might have other problems with your partitions. If you are getting freezing with the default Mac chooser (by holding option) then this is likely a bug in Ubuntu, not refit... unfortunately, we still have not found the reason for it, nor a fix...

---

### Post by cyberdork33 on 2008-05-02
I added info to fix the refit freeze issue!

---

### Post by Navelpluis on 2008-05-08
Had the same problem with kubuntu and Ubuntu-studio.
Did a fresh install with 7.10 and did an online update.
No problems,accept sound doesn't work yet.

---

### Post by skiwithpete on 2008-05-10
I also did a 7.10 install, and then upgraded to 8.10 to avoid the "no system disk" error. 

Sound doesn't work.
Its very hot.
And I haven't figured out the touchpad configuration (right clicks, and middle clicks are a complete mystery).

---

### Post by OCTOG3N on 2008-05-10
Thanks, that solved my problem. I had to do both the initial fix and the fix for the tux icon. However, now, for some reason, in refit, in addition to boot OS X from HD and boot Linux from HD, there is a boot linux from Partition 3 option. This seems redundant to me.

---

### Post by mabovo on 2008-05-10
I supposed installer hadn't this kind of bug. After a clean install on my MacBook a message in a dark screen inform "no bootable device please insert a boot cd and press enter".

By now I guess my Mac looks like a win98 environment.

---

### Post by cyberdork33 on 2008-05-10
> **skiwithpete said:**
> I also did a 7.10 install, and then upgraded to 8.10 to avoid the "no system disk" error. 

Sound doesn't work.
Its very hot.
And I haven't figured out the touchpad configuration (right clicks, and middle clicks are a complete mystery).
please create new threads for other issues.

---

### Post by mabovo on 2008-05-11
Unfortunately I had to format all partitions, because my /home (sda3) partition was placed before root system (sda4)

rEFIT considers the first linux partition as bootable and don't check if partition is the root system or home.

---

### Post by cyberdork33 on 2008-05-11
> **mabovo said:**
> Unfortunately I had to format all partitions, because my /home (sda3) partition was placed before root system (sda4)

rEFIT considers the first linux partition as bootable and don't check if partition is the root system or home.
that is dependent on where the boot flag is set in your partition table.

---

### Post by hardawayd on 2008-05-12
I have a bit of a similar problem. I have been using Gusty and beta Hardy on partitions 5 and 6 respectively on my MBP. I upgraded Gusty on 5 to Hardy and erased partition 6 and installed Xubuntu to it and installed Grub to partition 6. Now I get the gray screen with the penguin with the message 'no operating system found". I have resynched the tables using EFI partitioner but since I am not using the MBR since my partions are in 5 and 6 i am not sure what to do to get Grub to come up again. Any ideas?

---

### Post by nourani on 2008-05-20
No problem upgrading from 7.10 to 8.04. But clean install of 8.04 from CD ruins the MBR table for the Linux partition. As suggested by cyberdork33, you can fix this by running the partition tool, resyncing and choosing to save this to the MBR table. The suggested MBR table should look something like this:

 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    245514279  af  Mac OS X HFS+
 3 *    245776424    307693959  83  Linux
 4      307956111    312581111  82  Linux swap / Solaris

Cheers & good luck

---

### Post by feddi on 2008-05-28
> **skiwithpete said:**
> I also did a 7.10 install, and then upgraded to 8.10 to avoid the "no system disk" error. 

Sound doesn't work.
Its very hot.
And I haven't figured out the touchpad configuration (right clicks, and middle clicks are a complete mystery).

I too have upgraded from 7.10 and it boots fine except that I can't log in as simple user, I can log in in GNOME mode and others from the options but if I try to log in with my user name it just freezes at the orange screen....help anyone? thanks...:confused:

---

### Post by mezerik on 2008-05-28
I had this problem, i had to keep using my cd to boot up then it worked fine without the cd once booted.

After carrying out the instructions in the first post on here it boots up fine now.

---

### Post by alicebtoklas on 2008-05-30
> **OCTOG3N said:**
> Thanks, that solved my problem. I had to do both the initial fix and the fix for the tux icon. However, now, for some reason, in refit, in addition to boot OS X from HD and boot Linux from HD, there is a boot linux from Partition 3 option. This seems redundant to me.

The same for me: I fixed the two problems with the solutions proposed in the first post, and now I have to choose between "Linux from HD" and "Linux from partition 3". Which one should I boot from? Does that mean that there still is a problem? If yes, is there a way to fix it?
Thanks for your help.

---

### Post by cyberdork33 on 2008-05-30
For those getting the two Linux Icon issue, it is because there are two instances of Grub installed, one in the MBR and one on the Ubuntu partition. you should remove the one from the MBR:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

It really shouldn't effect anything other than showing two icons.

---

### Post by AmbroseBSOD on 2008-05-30
Solves my problem!

Thanks for the heads up

---

### Post by Ethos07 on 2008-05-31
Thanks for the info. I used the first thread and it fixed mine MB. 

The first time I tried to go to Ubuntu it hung on the Penguin but has been good since. 
I did a combination of manual and automatic install of refit. I had to run the enable.sh in a terminal before I saw it of startup. 

All is good now. Thanks again. Now for wireless...

---

### Post by kanpachi on 2008-05-31
what do i do if i don't want to dual boot ubuntu and mac os x?
i want ubuntu to be the ONLY OS on mac mini, but it won't boot after installation
i keep getting the ? sign

---

### Post by cyberdork33 on 2008-05-31
> **kanpachi said:**
> what do i do if i don't want to dual boot ubuntu and mac os x?
i want ubuntu to be the ONLY OS on mac mini, but it won't boot after installation
i keep getting the ? sign
Use boot camp to resize your osx partition, then boot the Ubuntu LiveCD, and delete the fat32 partition. start the installer and choose to install to the free space. after you have configured the install, you will be given a summary of what will be done to your system... there is a button in the corner of the window that says advanced, tell it to install grub to the Ubuntu Root partition (which will be shown in the summary). Then you can follow the fix in this thread.

IDK why you are having issues with your mini. Is it an Intel Mini or PPC?

---

### Post by kanpachi on 2008-06-01
it's an intel mac mini
plus is there any solution that doesn't include mac os x?
i don't want mac os x on my mac mini AT ALL

---

### Post by cyberdork33 on 2008-06-01
> **kanpachi said:**
> it's an intel mac mini
plus is there any solution that doesn't include mac os x?
i don't want mac os x on my mac mini AT ALL
There is nothing special needed to install Ubuntu on your Mac Mini. Just put in the disc and boot it up. In the installer, tell it to use the entire drive.

---

### Post by egeier on 2008-06-13
I’m now getting the Windows Boot Manager screen about winload.exe...here’s the story:

I have a Mac Mini with Leopard + Vista + Ubuntu

I had Leopard and Vista working fine, but I installed Ubuntu and then got “No bootable device error” when trying to access both Vista and Ubuntu from the rEFIt screen. I then synced my partitions using the rEFIt tool; this got rid of the no bootable device error and let me boot into Ubuntu but now when I access Windows, the Windows Boot Manager screen comes up and says Windows Failed to start... winload.exe...missing or corrupt. This happens after I choose Windows from the screen where I can choose variants of Ubuntu or Windows.

I reinstalled grub and it didn’t help.

Please help, thanks! - Eric

---

### Post by cyberdork33 on 2008-06-13
> **egeier said:**
> I reinstalled grub and it didn’t help.
Yea grub is not the culprit here. It does not touch your windows files. You might try booting from the windows disc into recovery mode and using the fixmbr command.

---

### Post by Naturally on 2008-07-07
Hi,

I need some help.

I am trying to tripple boot OSX, XP, and Ubuntu 8.04 on my MacBook bought a couple of months ago. I  upgraded the hard disk to a WD 320 GB, otherwise all is as designed.

After installing OSX, I used boot camp and installed windows XP SP2 to a 220 GB partition. That got both windows and OSX working fine.

I then created a 20 GB partition using OSX disk partition. This 20 GB was from the OSX partition. I then installed reFIt and installed ubuntu 8.04. GRUB was loaded into the samd disk as ubuntu, in my case disk 03.

Currently, I get the reFIt menu with an OSX icon, a linux icon, and a windows icon.

OSX and ubuntu work fine.

When I select windows, I get the XP screen and then I get a blue screen that flashes very fast (I cannot read what it displays) and the computer reboots. I tried to go into windows again and I get the option for safe mode which also fails.

I tried botting into the XP installation CD and using FIXMBR. The command works well with no error, however, windows still does not boot and causes the computer to reboot.

Any idea? I have looked all over and am really stuck.

---

### Post by Naturally on 2008-07-07
Never mind. Just solved it, OS X, Ubuntu, and XP professional work fine together now.

I will record what I did, since maybe this will help someone having this problem in the future.


As stated above, I used FIXMBR from windows XP CD and this did not solve the problem.

I then tried to synchronise the partitions through rEFIt partition tool. That reported that all Boot tables were synchronised and that there was no need to do anything.

However, the rEFIt partition tool, showed me that windows is installed in partition 4.

I then checked the windows boot.ini to see what partition it is trying to load from. I found that boot.ini is trying to boot from partition 3 instead of 4. So, I changed the two lines that are referring to partition 3 to point at partition 4 instead.

This fixed everything. All work fine now. I can boot from all of them.

Sorry for the false alarm.

---

### Post by ohyeah12321 on 2008-07-10
Okay, I seem to be running into obstacle after obstacle trying to get Ubuntu to work. First, I got it so that it freezes when selecting Ubuntu through rEFIt (grey screen, tux logo freeze). I followed the steps in the guide for how to get around that, and that is where my trouble lies. Instead of ending up with Ubuntu working, I now have 2 boot logos for Ubuntu (boot from HD and boot from partition 3) and both of them bring me to a command prompt screen and nothing else. Sorry for the broad question, but where do you think I went wrong and how do I fix it? Please forgive me for being a total noob,  but I made my journey into the world of Ubuntu last night.

---

### Post by cyberdork33 on 2008-07-10
> **ohyeah12321 said:**
> Okay, I seem to be running into obstacle after obstacle trying to get Ubuntu to work. First, I got it so that it freezes when selecting Ubuntu through rEFIt (grey screen, tux logo freeze). I followed the steps in the guide for how to get around that, and that is where my trouble lies. Instead of ending up with Ubuntu working, I now have 2 boot logos for Ubuntu (boot from HD and boot from partition 3) and both of them bring me to a command prompt screen and nothing else. Sorry for the broad question, but where do you think I went wrong and how do I fix it? Please forgive me for being a total noob, but I made my journey into the world of Ubuntu last night.Answer is in the original thread:
[http://ubuntuforums.org/showthread.php?t=854995](http://ubuntuforums.org/showthread.php?t=854995)

---

### Post by iPodAddict181 on 2008-07-11
Thank you so much, I was about to start a new thread on this. I kept trying to put Ubuntu on my Mac but it kept giving me that message. Now I will finally be able to put Ubuntu on my Mac, I subscribed to this thread too, and I also hope it stays alive.

---

### Post by MstrPBK on 2008-07-11
I heard of Ubuntu this morning as a bridge OS for Windows environments (am I correct on this understanding).  Has the discussion on this thread actually agreed on a solution?

I have no interest in loading Vista on my innocent Mac Mini; that in itself seems to be to much punishment for it.

Signed: Considering the bridge.
Peter Kelley
St. Paul, MN

---

### Post by cyberdork33 on 2008-07-11
> **MstrPBK said:**
> I heard of Ubuntu this morning as a bridge OS for Windows environments (am I correct on this understanding).  Has the discussion on this thread actually agreed on a solution?

I have no interest in loading Vista on my innocent Mac Mini; that in itself seems to be to much punishment for it.

Signed: Considering the bridge.
Peter Kelley
St. Paul, MN
Um, you might have to explain what you mean, and maybe start a new thread as I don't think what you are asking has anything to do with this thread.

---

### Post by Pederm on 2008-07-23
> **egeier said:**
> 
I had Leopard and Vista working fine, but I installed Ubuntu and then got “No bootable device error” when trying to access both Vista and Ubuntu from the rEFIt screen. I then synced my partitions using the rEFIt tool; this got rid of the no bootable device error and let me boot into Ubuntu but now when I access Windows, the Windows Boot Manager screen comes up and says Windows Failed to start... winload.exe...missing or corrupt. This happens after I choose Windows from the screen where I can choose variants of Ubuntu or Windows.

Please help, thanks! - Eric

I have the exact similar problem with XP in stead of Vista. XP says that "<windows root>\system32\hal.dll" is missing.

---

### Post by cyberdork33 on 2008-07-23
> **Pederm said:**
> I have the exact similar problem with XP in stead of Vista. XP says that "<windows root>\system32\hal.dll" is missing.
You usually get this error because the partitions have changed on the disk after you have installed Windows. There is really no "fix" other than to try reinstalling. This has been happening to people for far longer than Hardy or even Gutsy has been out.

Some say this works, but nobody has had much luck with it recently:
[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386)

---

### Post by mac-wilson on 2008-09-03
I'm getting those two problems mentioned in the first post of this topic.  My external HD has 3 partitions: MacOS backup, Linux, Linux swap.

If I sync paritions will all of the information inside of each seperate partition stay undamaged?  I don't want to have to re-backup my MacOS all over again.

---

### Post by cyberdork33 on 2008-09-03
> **mac-wilson said:**
> I'm getting those two problems mentioned in the first post of this topic.  My external HD has 3 partitions: MacOS backup, Linux, Linux swap.

If I sync paritions will all of the information inside of each seperate partition stay undamaged?  I don't want to have to re-backup my MacOS all over again.
Unfortunately, refit will only sync the partitions on your primary hard drive although I think that the gptsync command can be installed in Ubuntu and can sync partitions elsewhere.

You will not be able to boot your Ubuntu install off the external hard drive though still. There are many threads about this being an issue including a very long thread linked in the FAQ.

---

### Post by mac-wilson on 2008-09-04
I looked at those topics earlier.  It seems that people are able to boot off of a USB external HD.  My I can switch to a USB or eSATA connector if I wanted.

Right now I think my best choice would be to make my External HD for backing up ALL of my MacOS.

Then, I think I'll partition 80 GB of free space in the Internal HD, and set it as "Free Space."  So when I get to the partition chooser of the Ubuntu Install, I select Largest Continuous Free Space.  Largest Continuous Free Space applies to a partition that has NOTHING on it except space, correct?  So I don't run the risk of having it install on my MacOS partition, because there is over 80 GB free there, even AFTER I partiton it?

So if I select Largest Continuous Free Space and let it do an automatic install, Ubuntu will set up a swap for me.

Then when it's done and I reboot, I reboot into rEFIt and select the Legacy (or Linux) icon?  This is the part that got me confused.  Do I select the Linux icon or the BootCamp Windows looking icon labled Legacy OS?  I don't have any Windows softeware on my computer.

---

### Post by cyberdork33 on 2008-09-04
> **mac-wilson said:**
> I looked at those topics earlier.  It seems that people are able to boot off of a USB external HD.  My I can switch to a USB or eSATA connector if I wanted.No, it is the opposite. You _cannot_ boot a legacy OS from an external hard drive, USB or Firewire. (You can if you create a boot partition on your internal drive, but that is still technically booting from the internal.)

> **mac-wilson said:**
> Right now I think my best choice would be to make my External HD for backing up ALL of my MacOS.

Then, I think I'll partition 80 GB of free space in the Internal HD, and set it as "Free Space."  So when I get to the partition chooser of the Ubuntu Install, I select Largest Continuous Free Space.  Largest Continuous Free Space applies to a partition that has NOTHING on it except space, correct?  So I don't run the risk of having it install on my MacOS partition, because there is over 80 GB free there, even AFTER I partiton it?Yes you are correct. By 'free space' it means space that has no partition on it, not 'space that has no files'. I find that the easiest way to do this is to use bootcamp to resize your OSX partition and create a Windows FAT32 partition. Then you start the Ubuntu LiveCD and run the partition editor (gparted) and delete the FAT32 partition (leaving free space). Then start the Ubuntu installer and choose to install to the largest free space.

> **mac-wilson said:**
> So if I select Largest Continuous Free Space and let it do an automatic install, Ubuntu will set up a swap for me.correct

> **mac-wilson said:**
> Then when it's done and I reboot, I reboot into rEFIt and select the Legacy (or Linux) icon?  This is the part that got me confused.  Do I select the Linux icon or the BootCamp Windows looking icon labled Legacy OS?  I don't have any Windows softeware on my computer.You shouldn't have a windows-looking icon after you install Ubuntu. BUT, you will probably need to sync your partition tables in rEFIt first before Ubuntu will bootup anyway because of a bug in the Ubuntu installer. The first post of this thread shows specific directions for fixing that problem.

---

### Post by plaintiger on 2008-09-12
my first post! wheee!  :P

i wish it was a happier one:

i'm having a problem i'm not seeing mentioned anywhere quite the way i'm experiencing it. i downloaded the files and created an 8.0.4 install CD (AMD 64-bit). i followed the instructions [here]("http://mindbat.com/?p=30") to install on my 3.0 GHz dual quad Mac Pro (the April '07 version with the 667 MHz RAM). all goes just peachy, including booting from the LiveCD - i have full functionality, if you don't count Ubuntu being unable to see my Broadcom wireless card. so i say, "oh this is so cool (and maybe the actual install will be able to see my wireless card)" and proceed with the install, which also goes just as it should. when the install's complete i take out the CD, close the tray and restart, and choose the cute iddle penguin in rEFIt.

alas, i only get to the black screen with the little white cursor blinking in the upper left. once there, that's where i stay until i force a shutdown with the power button on the front of my machine (ugh).

i've tried this twice with no luck. anybody got any suggestions?

many thanks in advance...

tiger

---

### Post by cyberdork33 on 2008-09-12
> **plaintiger said:**
> my first post! wheee!  :P

i wish it was a happier one:

i'm having a problem i'm not seeing mentioned anywhere quite the way i'm experiencing it. i downloaded the files and created an 8.0.4 install CD (AMD 64-bit). i followed the instructions [here]("http://mindbat.com/?p=30") to install on my 3.0 GHz dual quad Mac Pro (the April '07 version with the 667 MHz RAM). all goes just peachy, including booting from the LiveCD - i have full functionality, if you don't count Ubuntu being unable to see my Broadcom wireless card. so i say, "oh this is so cool (and maybe the actual install will be able to see my wireless card)" and proceed with the install, which also goes just as it should. when the install's complete i take out the CD, close the tray and restart, and choose the cute iddle penguin in rEFIt.

alas, i only get to the black screen with the little white cursor blinking in the upper left. once there, that's where i stay until i force a shutdown with the power button on the front of my machine (ugh).

i've tried this twice with no luck. anybody got any suggestions?

many thanks in advance...

tiger
I assume you synced the partition tables as shown in the beginning of this thread? Can you post the content of the Partition Tool (part of refit, located in your /Applications/Utilities folder in OSX)

---

### Post by plaintiger on 2008-09-12
i had synched the partition tables (after which i tried to do it a couple more times, with rEFIt telling me each time that they were already synched)  and was still getting this result, but since posting my message i've followed the procedure again and this time had success. now if i can just get Ubuntu to see my wireless card...

thank you for your response - sorry i didn't post earlier that i'd gotten past the problem, but i was up all night working on it and when i finally succeeded i just crashed straight into bed.  :D

---

### Post by cyberdork33 on 2008-09-12
> **plaintiger said:**
> i had synched the partition tables (after which i tried to do it a couple more times, with rEFIt telling me each time that they were already synched)  and was still getting this result, but since posting my message i've followed the procedure again and this time had success. now if i can just get Ubuntu to see my wireless card...

thank you for your response - sorry i didn't post earlier that i'd gotten past the problem, but i was up all night working on it and when i finally succeeded i just crashed straight into bed.  :D

For your WiFi, post a new thread and give the output of lspci. I think I know what it is though.

---

### Post by plaintiger on 2008-09-12
> **cyberdork33 said:**
> For your WiFi, post a new thread and give the output of lspci. I think I know what it is though.

k. thank you.

---

### Post by BoardDWorld on 2008-09-28
Awesome, thanks for your help. Everything mentioned happened, and was resolved with the solutions, right down to the freezing tux and powering off properly.

:popcorn:

---

### Post by Snowdrift42 on 2008-11-20
I have a first-generation Mac Pro. I tried installing Ubuntu on it, but after a reboot I only got the "no operating system found" message. 

When I start up my Mac now, it shows me the flashing folder icon with the question mark. The cooling fans inside are spinning at full speed.

The computer doesn't accept any key commands, so I can't boot from the Mac OS X installer DVD, or any other connected disk for that matter. For the same reason, I also can't zap the PRAM or follow the other steps that have been suggested by forum members or indeed the official Apple support pages. I have created a firmware restore CD (following the steps on Apple's support page), but I am unable to use it because the Mac refuses to initiate the firmware update when I hold down the power button at startup. Instead it just turns off again.

Any help with this would be appreciated, because I have the feeling I just acquired an oversized $4000 paperweight.

Cheers!

David

---

### Post by cyberdork33 on 2008-11-20
I don't know why this would affect your ability to boot from a CD, or use keyboard combos on startup. That sort of stuff is built into the firmware of your mac.

---

### Post by pxwpxw on 2008-11-20
On the Apple mac pro support page, Restting the SMC covers the unresponsive computer/kbd  situation,
holding in the power button for 10 seconds or more is one option.

---

### Post by Snowdrift42 on 2008-11-21
Thanks for your reply, Cyberdork. EDIT: and PXWPXW

I managed to fix the problem on my own. For reasons unknown to me, somehow during the install, my SMC must have become corrupt. So resetting the SMC fixed half of the problem. I then was able to use rEFIt to fix my MBR. Now everything is back to normal. Phew!

David

---

### Post by Kingpatzer on 2008-12-19
I'm having similar issues and it seems pretty clear I need to install rEFIt. However, i don't have a working Mac at this point and the rEFIt distribution comes in a .DMG and .CDR format. How do I burn a bootable CD of rEFIt when I only have a PC to burn from?

---

### Post by cyberdork33 on 2008-12-19
> **Kingpatzer said:**
> I'm having similar issues and it seems pretty clear I need to install rEFIt. However, i don't have a working Mac at this point and the rEFIt distribution comes in a .DMG and .CDR format. How do I burn a bootable CD of rEFIt when I only have a PC to burn from?

you can burn the .cdr image to disc from any computer. If you need a burning application, I would suggest ImgBurn:
[http://www.imgburn.com/](http://www.imgburn.com/)

Can you not boot OSX by holding Option on startup?

---

### Post by pxwpxw on 2008-12-19
> **Kingpatzer said:**
> I'm having similar issues and it seems pretty clear I need to install rEFIt. However, i don't have a working Mac at this point and the rEFIt distribution comes in a .DMG and .CDR format. How do I burn a bootable CD of rEFIt when I only have a PC to burn from?

If you have a ubuntu live cd you can download the ubuntu refit package and run gptsync to sync the MBR, if that is your problem.
```

sudo apt-get install refit
sudo gptsync /dev/sda

```

---

### Post by arjunjain on 2008-12-27
Hi everyone,

I am in a similar problem, but my case is a little different. I had a nice refit installation with all os working (i have mac os x, ubuntu and win xp). 

Then, I decided to give more space to win xp, and this resulted in moving the partitions around, i used ubuntu live cd and gparted.

Now, the win and the ubuntu refuse to boot.. I have synced the mbr from the refit menu, i am thinking of reinstalling grub as given on [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11) . But this will still not fix my windows boot, will it? What can I do to fix it?

Any help will be very helpful!
TIA,
Arjun

---

### Post by hanzomon4 on 2008-12-27
I figured out what the problem was:

You have to use disk utility to create an hfs+ partition were you want to install Linux. Simply making free space and formating it with the Ubuntu installer will cause you to install on /dev/sda5 or disk0s5. If you make the hfs+ partition with disk utility and then format that partition in the installer it's listed as /dev/sda4 or disk0s4. 

The numbers maybe different for you, in my case I have a separate / and /Users partition. What seems to cause this weirdness is the fact that in addition to / you also have /efi and /apple_boot(or something like that) partitions that don't show up in the OS X disk utility but are still there. To see them just run "diskutil list" in the OSX terminal.

---

### Post by cyberdork33 on 2008-12-28
> **arjunjain said:**
> Hi everyone,

I am in a similar problem, but my case is a little different. I had a nice refit installation with all os working (i have mac os x, ubuntu and win xp). 

Then, I decided to give more space to win xp, and this resulted in moving the partitions around, i used ubuntu live cd and gparted.

Now, the win and the ubuntu refuse to boot.. I have synced the mbr from the refit menu, i am thinking of reinstalling grub as given on [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11) . But this will still not fix my windows boot, will it? What can I do to fix it?

Any help will be very helpful!
TIA,
ArjunNope, that is a different issue. Windows doesn't like when you mess with partitions after it has been installed.

---

### Post by zowey on 2008-12-31
I have problem when i try to boot linux from partition3 it shows me just GRUB and blinking cursor

---

### Post by cyberdork33 on 2008-12-31
> **zowey said:**
> I have problem when i try to boot linux from partition3 it shows me just GRUB and blinking cursor
Reinstall GRUB as shown in the second part of the first post.

---

### Post by zaksoup on 2008-12-31
I recently Attempted to install Ubuntu 8.10 on an external volume (120 GB iomega) from a 2006 macbook (white). Now when i reboot I get the flashing question folder no matter what. I cannot boot into either the ubuntu external drive or the macbook's internal os x drive. Could this problem be caused by the ubuntu 8.10 bug or is it unrelated.

---

### Post by pxwpxw on 2008-12-31
> **zaksoup said:**
> I recently Attempted to install Ubuntu 8.10 on an external volume (120 GB iomega) from a 2006 macbook (white). Now when i reboot I get the flashing question folder no matter what. I cannot boot into either the ubuntu external drive or the macbook's internal os x drive. Could this problem be caused by the ubuntu 8.10 bug or is it unrelated.

Possible fix is to use your OSX dvd to reset the startup volume to internal OSX.

---

### Post by leogibson on 2009-02-01
Ive had this problem for a few days, but i'm making progress.  I'm triple booting OSX, XP, Intrepid.  I have installed refit, and i have all the right icons when I boot up, i was able to fix the "freezing tux" and "two tux icon" issues myself whith a combination of managing flags in gparted, syncing the MBR with the refit CD, and reinstalling grub to my ubuntu partition (im not sure if that actually helped, because when i installed ubntu, the installer wouldnt let me install GRUB to hda 0,3 (ubuntu) it only let me install to hda0,1 (my MBR?).  

I installed osx first, then used bootcamp to install xp, then made a partition at the end for ubuntu.  At first boot after install, it wouldnt let me boot from refit, but holding option, selecting "windows" did.  now when i boot, the windows and linux icons both start booting windows....???

do i need to edit the boot.ini in windows?  how will that let me boot into ubuntu when i select the linux icon?  do i need to reinstall refit?  do i edit boot.ini file with the xp install cd?

---

### Post by cyberdork33 on 2009-02-01
> **leogibson said:**
> Ive had this problem for a few days, but i'm making progress.  I'm triple booting OSX, XP, Intrepid.  I have installed refit, and i have all the right icons when I boot up, i was able to fix the "freezing tux" and "two tux icon" issues myself whith a combination of managing flags in gparted, syncing the MBR with the refit CD, and reinstalling grub to my ubuntu partition (im not sure if that actually helped, because when i installed ubntu, the installer wouldnt let me install GRUB to hda 0,3 (ubuntu) it only let me install to hda0,1 (my MBR?).  

(hd0,3) would be the 4th partition on the primary hard drive... 
(hd0,1) would be the second partition (likely OSX)
(hd0) would install to the MBR

> **leogibson said:**
> I installed osx first, then used bootcamp to install xp, then made a partition at the end for ubuntu.  At first boot after install, it wouldnt let me boot from refit, but holding option, selecting "windows" did.  now when i boot, the windows and linux icons both start booting windows....???This happens when the windows bootloader is installed in the MBR (as it is for XP) and the bootloader for Ubuntu (GRUB) is not installed properly.

> **leogibson said:**
> do i need to edit the boot.ini in windows?  how will that let me boot into ubuntu when i select the linux icon?  do i need to reinstall refit?  do i edit boot.ini file with the xp install cd?If windows boots OK, I wouldn't mess with anything there.

I think you are going to have to reinstall GRUB again.

Can you boot into OSX and post the Partition information from the Partition Inspector tool found in /Applications/Utilities ?

---

### Post by leogibson on 2009-02-01
im pretty sure i solved this, but it involved deleting windows...i never use it anymore anyways. :)  now i can boot to linux, but i had to remove the boot flag with gparted.  (i did this before and it diddnt seem to matter.

now that windows is gone. how to i remove it from the grub menu?  i cant recall the config file, but im sure some commenting would fix it.  

in any case, here is my new partition info:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  MS Reserved
 2         409640    106205714  Mac OS X HFS+
 4      106205715    156296384  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2             40       409639  c0  Unknown
 3         409640    106205714  af  Mac OS X HFS+
 4 *    106205715    156296384  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type MS Reserved
 Listed in MBR as partition 2, type c0  Unknown

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 106205715:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

my kaplan premiere GRE companion is supposed to work according to the wine app database, but i get some errors still.  it would be cool if i could get that and my blackberry desktop manager to work in either wine or darwine, which is the only reason i had windows to begin with.

i spent hours trying to fix this problem and got fed up with it, so this immediately solved it.  now if gparted could make my HFS+ partition bigger, that would rock, but i dont think it can

thanks for your help

Matt

---

### Post by cyberdork33 on 2009-02-01
> **leogibson said:**
> im pretty sure i solved this, but it involved deleting windows...i never use it anymore anyways. :)  now i can boot to linux, but i had to remove the boot flag with gparted.  (i did this before and it diddnt seem to matter.
Just as a future reference, I wouldn't mess with the flags manually. Let OSX and the installers set them as they seem to do it correctly. Plus there is a bug in gparted that can mess up FAT32 partitions by placing a bad flag on it (that cannot then be removed).

> **leogibson said:**
> now that windows is gone. how to i remove it from the grub menu?  i cant recall the config file, but im sure some commenting would fix it.  
Should be pretty easy. just open /boot/grub/menu.lst and find the Windows Entry and remove it or comment it out.

> **leogibson said:**
> in any case, here is my new partition info:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  MS Reserved
 2         409640    106205714  Mac OS X HFS+
 4      106205715    156296384  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2             40       409639  c0  Unknown
 3         409640    106205714  af  Mac OS X HFS+
 4 *    106205715    156296384  83  Linux

It appears that there is a problem. you seem to have a FAT32 partition defined in your MBR partition table, but not in your GPT. I would sync the partition tables with rEFIt again... If something becomes unbootable after that then it can be fixed.

> **leogibson said:**
> i spent hours trying to fix this problem and got fed up with it, so this immediately solved it.  now if gparted could make my HFS+ partition bigger, that would rock, but i dont think it cannope. no open source tool can "grow" an HFS+ partition currently. Some can create a new one though. You can use DiskUtility to resize your HFS+ partition i you want to.

---

### Post by septic1 on 2009-05-11
Hi,

I am trying to install Ubuntu 9.04 to my Macbook following [these instructions](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation?highlight=%28%5CbCategoryMac%5Cb%29#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu). Everything went well until i rebooted my computer and tried to sync partitions using rEFIt. It just keeps telling me "Tables are ok, no need to synchronize", but I still ain't able to boot Ubuntu. It freezes on the grey Tux logo every time.

What I am supposed to do next?

---

### Post by cyberdork33 on 2009-05-12
> **septic1 said:**
> Hi,

I am trying to install Ubuntu 9.04 to my Macbook following [these instructions]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation?highlight=%28%5CbCategoryMac%5Cb%29#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu"). Everything went well until i rebooted my computer and tried to sync partitions using rEFIt. It just keeps telling me "Tables are ok, no need to synchronize", but I still ain't able to boot Ubuntu. It freezes on the grey Tux logo every time.

What I am supposed to do next?
I think the partition syncing issue was fixed in jaunty.

Try shutting down and restarting again a couple of times (not rebooting). If that doesn't help, you may need to reinstall grub as indicated in the thread.

---

### Post by kokoroexchange on 2009-06-13
What a nightmare this has been!!

I have been working on getting Ubuntu (9.04) running on a Mac Mini (2.0Ghz Intel) for three days now.  

I first tried by following the instructions for Single-Boot [here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#GRUB2%20/%20GRUB_EFI") but I couldn't install Grub and my Mini subsequently became a brick.  Couldn't boot from anything (CD, HD, nothing). Finally manged to get it back by mounting the drive in target disk mode and reformatting to HFS and then reinstalling Max OSX.

Tried the same thing again with same results.

Then tried doing a dual boot using Bootcamp first to minimize the OSX partition to it's smallest possible size.

Then used the 9.04 CD again and that time was able to install everything, including Grub!!  But I put it on the wrong partition (oops).

Also, forgot to mention, I did install rEFIt on the OSX partition.  Instead of starting all over and reinstalling Mac OSX because I can't mess with the partition made with Bootcamp without reinstalling, I just installed 9.04 again and put Grub in the correct location the second time (I thought).  

Booted up and got the rEFIt screen and selected the 2nd penguin but now all I have is a blinking cursor.  Maybe I was supposed to select the Bootcamp penguin...?  No, tried that and I get a blinking GRUB....  So, do I have GRUB on one partition and Linux on another.  Hmmm... run the partition synchronizer again...?

Feel like I'm close but what a ridiculous journey this has been.

Any advice welcome.

Jason

P.S. At least I can boot into something now since I have OSX on the machine. :-)

---

### Post by kokoroexchange on 2009-06-14
WOW!!! FINALLY!!

I tried again with a slightly different method and finally achieved success!!!

When installing I had previously tried the LVM option and installing to the sda3 open partition and both of these failed spectacularly.

Tried again with the "use entire disk" option and everything worked :-)  Grub was installed and upon restarting I was able to boot into my LAMP.  I guess the fix that has been incorporated into 9.04 was only for the desktop version and they haven't implemented it yet on the server CD.  Oh well, I don't need LVM....not yet at least 

Jason

---

### Post by cyberdork33 on 2009-06-15
> **kokoroexchange said:**
> WOW!!! FINALLY!!

I tried again with a slightly different method and finally achieved success!!!

When installing I had previously tried the LVM option and installing to the sda3 open partition and both of these failed spectacularly.

Tried again with the "use entire disk" option and everything worked :-)  Grub was installed and upon restarting I was able to boot into my LAMP.  I guess the fix that has been incorporated into 9.04 was only for the desktop version and they haven't implemented it yet on the server CD.  Oh well, I don't need LVM....not yet at least 

Jason
It may just be an issue with LVM as I am pretty sure that most users have not been trying to use that method.

---

### Post by rederic4 on 2009-09-15
I have been banging my head against the wall for five days now and no joy. Found this thread and still can not make things go. I am attempting to Triple boot Snow Leopard, Windows 7, and Jaunty on an Intel MacBook. I have tried several methods including bootcamp install of windows and then installing Jaunty. Osx then Jaunty then windows, all with no joy. Today I came the closest with a new install of Snow Leopard, then partitioned the disc so I had the partition for OSX, then a partition for Windows, then linux swap, then Ubuntu. I formated the Ubuntu partition as a ext3 with "/" and installed the Grub loader to this partition. After install reFit showed a OSX disc, a Windows disc, and a Linux disc. OSX booted to OSX, Windows booted to Windows, Linux showed no OS. Ran reFit partition sync, it said there was nothing to sync and showed OSX drive as MAC, Windows drive as Windows, and Linux drive as Basic Data. Exited and tried to select Linux OS, it froze. Shut Down and on reboot tried to select Linux OS, it booted to windows. Reinstalled grub twice using the method linked to (Live Disc, sudo grub, find....etc.) No Joy..........any help would be greatly appreciated.

---

### Post by andrewroth on 2009-11-16
I have a 4.1 macbook pro, and I had 8.04 triple booting.  Did a clean install of 9.04, and I do see the tux icon but when I choose it the screen says "GRUB" for a second then reboots (by itself).  Tried various grub options with no luck.  Any ideas appreciated.

---

### Post by e85 on 2009-11-16
My first post here and I am a newbie to Ubuntu too so please forgive me if I am missing something obvious.

I have after some initial problems a triple boot setup in my 2006 macbook Core Duo.
It has OS X 10.4 on a HFS+ partition on which I used bootcamp to make a partition to install WINXP on  and then shrinked the apple partition more o make a partition for Ubuntu 9.10 between the OSX and WINXP partition. I installed GRUB on the linux partition as well as rEFIt and triple booting worked well untill this morning.  
 
rEFIt shows me 3 options like it did before, MacOS, generic legacy icon (for Ubuntu) and a windows flag. The partition tool show me that the partition tables are in sync but when I try to boot into Linux GRUB tells me that there are no bootable devices and I should insert a (booable) disk and then press any key. Normally Grub gave me the option to boot in Ubuntu, Ubuntu safe mode, WinXP as well as mac OS, luckily, booting in OS X (10.4) from rEFIt still works.

the three partitions visible in mac os disk utility
Mac OS Extended, with mac OS
Ext2 File System, with Ubuntu, in os x not mountable ext3 formatted partition
MS-DOS-filesystem (FAT32), with winxp and also mounted in mac os x

Any advice welcome!

/Aryan

---

### Post by sunbird on 2010-02-20
I just did a clean install on a new HDD for my Macbook Pro 3,1. This is a single-boot, 9.10AMD64 machine.

I cannot get the partition table to resync, either using parted, booting into a live cd, or using a rEFIt cd. This is the error:

```

# gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             34          424  Unknown
 2            425       586362  Basic Data
 3         586363      4492613  Basic Data
 4        4492614    625142414  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1             34          424  00  Unknown
 2 *          425       586362  83  Linux
 3         586363      4492613  00  Unknown
 4        4492614    625142414  00  Unknown

Status: GPT partition of type 'Unknown' found, will not touch this disk.

```

Why, you may ask, do I have such a miniscule partition #1? It's because earlier in the reinstall process, I had been unable to get grub to install, and I read a thread saying you need to leave a small partition of 128kiB in the first slot for grub to use.

Also, the partition table for the drive was created using disk utility running from OSX install. Everything else was done through a fresh 9.10 installation.

The thing is, the tables appear to be in sync. But I can only boot by holding the OPTION key on startup and selecting the partition. 

I don't want/need rEFIt, I just want the box to boot without holding option.

Ideas?

**Update:** Okay, all I needed to do was bless my /boot partition. Duh! However, I still get the weird error above on running gptsync, but everything works! Boots straight to ubuntu. Yay!

---

### Post by linuxopjemac on 2010-02-21
The "I will not touch this disk" error is known, you might want to check this link:

[http://mac.linux.be/content/gptsync-gpt-partition-type-unknown-found-will-not-touch-disk](http://mac.linux.be/content/gptsync-gpt-partition-type-unknown-found-will-not-touch-disk)

---

### Post by gotschi on 2010-03-24
I have a MB Pro 5,1 trying to install the 10.04 beta via Wubi on the Boot Camp partition.

After some researching, i decided to do this via Wubi, but ended up in booting into a grub screen, where no commands were allowed, maybe because there was no shell sh:

then i completely removed the win 7 partition (30-day trial nearly over) in the disk utility and tried to install via CD - Desktop-i386.iso

starting boot camp assistant - rebooted and some install screen thing came up, but after loading 2 icons it hangs at a blinking cursor screen

i know it's beta but these are my experiences and i
hope someone can help me out :)

[edit]: sorry, wrong place :/

---

### Post by linuxopjemac on 2010-03-25
start your exploration with some good reading:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by jzhou2oo6 on 2010-03-30
Macbook 5,2 I have mac 10.6.2, windows 7 and ubuntu 9.10 however ubuntu is stuck at a blank screen after grub

---

### Post by thann on 2010-04-08
Hello there, some feedback: 

I created a Bootcamp partition a while ago and installed Vista on it. I decided that the partition grew too small for me and I wanted Windows 7 + a Linux partition anyway, so I removed the Windows partition via Disk Utility and created a new, larger Bootcamp partition on which I installed Windows 7 (which worked, too). I then wanted to use the partition program on the Ubuntu DVD to further create the Linux partition (as part of the newly created Win Bootcamp partition, which did not work for some reason I don't remember. So instead, I resized the Bootcamp partition with Windows' hard disk partition tool thingy and installed Ubuntu (the newest 10.04 beta) on the created free space. I also installed rEFIt and it's working for MacOS and for Windows (shows GRUB and when I choose Windows, it boots correctly). However, if I choose Linux, GRUB comes up and going for Ubuntu there again, I get some two lines of output and a black screen afterwards. 
Now I came across this thread, the problem I'm facing right now is: If I try to use rEFIt's resync tool, it says it's out of sync and underneath: 
```
Error: Not found returned from gptsync.efi
```Hitting any key, I get back to rEFIt's boot menu. Also, if I try to enter the refit console, the computer just freezes. 
The blank screen also goes for booting from Ubuntu DVD btw (I even got it when I wanted to run the GParted live cd). 

Any help on this would be appreciated!

---

### Post by linuxopjemac on 2010-04-08
Do you use rEFIt 0.14? I would expect it to be able to sync better now. Otherwise you might want to follow this thread:

[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

[http://mac.linux.be/content/refit-014-released](http://mac.linux.be/content/refit-014-released)

---

### Post by thann on 2010-04-08
Thanks,
yes, I use rEFIt 0.14 . Also, I found some threads in some message boards when searching for the error message, and the usual response there seemed to be something along the lines of "Uh oh, something went terribly wrong" ...

---

### Post by envious86 on 2011-04-08
I am having a problem. I have done all the suggestions in the first post but when I go to partition tool it says "no need to sync, hit any key to continue" when I do it kicks me back out to the refit menu and I get the blinking cursor. how can I fix this?

I am using iMac 10.6.7 with vista already installed with bootcamp and I have rEFIt installed.

---

### Post by mochiswelt on 2011-10-12
I have a Macbook with a 2GHz Intel Core 2 Duo Processor (the Black One) and 4 GB Ram ...

Right now I'm Trying to run from Live CD the Ubuntu 64 bits version, in the forums said that it will take a long time to mac to boot Ubuntu... but... I waited all night in a Black screen that displays something like "choose CD to Boot"... (at least 9 hrs!!!!) 

 This is normal??? should I wait more time??

I'm Using rEFit to make it bootable...

---

### Post by chaud245 on 2011-11-04
I am attempting to install Ubuntu to an external hard drive and I am having no luck.

Parts:

[LIST]
[*]2.26 Ghz Intel Core 2 Duo MacBook, 2 GB DDR3 ram
[*]Ubuntu Live Bootdisc (11.10 and 10.04)
[*]500 GB external hard drive (USB)
[*]rEFIt bootable disk
[/LIST]
I am not the administrator on my internal HD (Mac OSX 10.6.8 ) therefore I am not aloud to manipulate anything on my Internal drive. Although I have been given permission to create my own Mac OSX installation on the external (which works fine if I want it to), but I want Ubuntu on my external (I don't care if it's Dual-boot or Single-boot). I installed my ubuntu both alongside and as a single boot on my external and neither worked. Both times I receive the black screen stating the error "No Operating System Found", keep in mind BootCamp cannot manipulate external drives therefore I am using Disk Utility (from a Mac OSX install disc).

Please help I've tried for almost a week to solve this myself by surfing the web looking for similar cases, but with limited time to work on this and everything I try doesn't change anything, so I am quickly becoming frustrated.

---

### Post by jhenes on 2011-11-13
I have just installed Ubuntu 11.10 onto my iMac and this is how I was able to succeed :

1. Partition the disk as you want it with Disk Utility from OSX (any filesystem type will do)
2. (Install reFit - if desired)
3. Boot the computer from the LiveCD and open a terminal window.
4. Start fdisk and copy the partition info into text edit (or similar)
5. Run the installer, and choose manually the partitions you made in Disk Utility to install to, setting right type etc.
6. When the installer has completed, do the following before reboot :
- Download and install GptSync from [http://packages.debian.org/sid/gptsync](http://packages.debian.org/sid/gptsync)
- Run fdisk and delete all partitions - and re-create everything as it was before you started the installer.
- Run GptSync : 'sudo gptsync /dev/sda' (replace "sda" with your disk)
(I was not able to get GPTSync to succeed without re-creating the partition table using fdisk... the Ubuntu installer seems to screw up the MBR somehow)
7.  Reboot, the system should be able to boot again now

Good luck ;-)

Johan
---
Some useful information : 

[I]First, if I create a new partition on an empty device, fdisk appropriately 
uses 1MB offset from beginning by default:
"First sector (2048-10239999, default 2048 ):"
[/I]
[I] Yes, this is default. Anyway, you can move the begin of the first
 partition to sector <1..N> in expert menu (commands 'x' and 'm') where
 <N> is the end of the first partition.[/I]

---

### Post by jhenes on 2011-11-13
> **mochiswelt said:**
> I have a Macbook with a 2GHz Intel Core 2 Duo Processor (the Black One) and 4 GB Ram ...

Right now I'm Trying to run from Live CD the Ubuntu 64 bits version, in the forums said that it will take a long time to mac to boot Ubuntu... but... I waited all night in a Black screen that displays something like "choose CD to Boot"... (at least 9 hrs!!!!) 

 This is normal??? should I wait more time??

I'm Using rEFit to make it bootable...

See previous post

Johan

---

### Post by wariobrega on 2012-05-16
Hello I'm having the same issue that most of you experienced. After updating my mac OS to 10.7.4,my refit settings went off and after reinstall refit I've got the Tux logo / blinking cursor.

I already sync refit to the partition table and I cannot install grub from the ubuntu 12.04 live CD: apparently the instructions stated  [here]("http://ubuntuforums.org/showpost.php?p=3303463&postcount=11") are no valide, according to the terminal there is no grub installed on my system (impossible of course), and I should reinstall it from the terminal (not possible of course because the mac drivers are not set up in the live cd). Using the ```
diskutil list 
``` command i got the following disk table: 
```
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *750.2 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS WarioMac                630.3 GB   disk0s2
   3:       Microsoft Basic Data                         117.5 GB   disk0s3
   4:                 Linux Swap                         2.0 GB     disk0s4
```

("Microsoft basic data" is my linux partition)

Any idea on how to restore/reinstall grub in this case scenario?
My specs:

MacEarly 2011;
Ubuntu 12.04 installed

Thanks!

---

### Post by Imago Hominis on 2012-12-03
Okay, new Ubuntu user, first post, could probably have done this better if I'd planned ahead, but think I have something useful to contribute and get the impression that actively contributing is part of the whole linux thing.
 
I installed 12.10 from a CD onto my early 2009 Mac mini. I followed the instructions here:
 
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
 
These instructions were pretty good, but there is a section as follows (important bit in red), which left me facing the 'no operating system installed' message until I changed my approach:
 
*[SIZE=2]Start Installing[/SIZE]*
 
*[SIZE=2]Back on the Ubuntu LiveCD desktop, start the Ubuntu Installer from the desktop icon. When prompted, choose to manually partition. Select the EXT4 partition and click change. Select to use the space as the EXT4 filesystem and root (/) as the mount point. You will also want to check the box to format the partition. [COLOR=red]On the last dialog of the installer, be sure to click the “Advanced” button and choose to install the boot loader (grub) to your root Ubuntu partition, for example /dev/sda3. This will be the only partition with the EXT4 file system.[/COLOR][/SIZE]*
 
I think this is now superseded. When you try to install the boot loader to the Ubuntu partition, you don't get offered an 'Advanced' button and you do get an error message telling you the boot loader needs to go on a small additional partition marked as 'BIOS'. Sorry this isn't brilliantly explained, but I can't / won't try to reinstall to get the detail clearer. What I can say is that if you 'cancel' this step, you get back to the partition table and it is straightforward to add a new 1 GB partition and choose the 'BIOS' option from the drop down table. And then installation proceeds smoothly.
 
I did have to sync the partition tables in rEFIt, as others have described. This bit was easy.
 
Moral of the story: pay close attention to the error messages - they are intended to be useful and informative.
 
I had my system working cleanly for 36 hours, but have now done something to corrupt the screensaver so that I have to do a hard reboot every time it sleeps. But that's for another thread.
 
So, linux is looking a bit harder than Mac OS X "it just works". Conversely, I want to upgrade my computer to something more powerful, with an optical drive, for less than a bazillion pounds, and I don't care if the screen is more than 5 mm thick. I don't see why I have to replace my screen at all, to be honest. 
 
Cheers

---

### Post by alexferreirag on 2013-03-22
I think this might help some of you:
[h=2][Linux for Mac Help: rEFIt No Bootable Device Error Fixed]("http://pumpedupgeek.com/?p=55")[/h]

---

