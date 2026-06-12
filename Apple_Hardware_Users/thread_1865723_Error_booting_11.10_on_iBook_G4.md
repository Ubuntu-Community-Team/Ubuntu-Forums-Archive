---
title: "Error booting 11.10 on iBook G4"
date: 2011-10-20
forum: Apple Hardware Users
---

### Post by mpicker0 on 2011-10-20
I tried to upgrade from 11.04 to 11.10 when prompted a few days ago, and was unable to boot.  I don't recall the exact message.

 I then downloaded the 11.10 ISO image from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and burned it.  I installed it, and chose to "Erase Ubuntu 11.10 and reinstall".  
 
 The installer runs nearly to completion, then looks like it wants to download updates.  /var/log/syslog shows
[FONT=Courier New]DEBUG: command: wget -q [http://mirror/ubuntu-ports//dists/oneiric/Release](http://mirror/ubuntu-ports//dists/oneiric/Release) -O - | grep -E '^(Suite|Codename):'
 WARNING **: mirror does not support the specified release (oneiric)[/FONT]

and I get a pop-up saying there is an error trying to use the specified Ubuntu archive mirror.  If I click "OK," the message pops up again forever.  The "Installation Complete" dialog is also shown, but when I click either "Continue Testing" or "Restart Now," the installer crashes.  I think the installation is mostly good, and these errors might not be a big deal.
 
When I reboot, I get into yaboot, and the kernel is loaded.  However, after just a second or two, I get the messages:
 
 [FONT=Courier New]/build/buildd/linux-3.0.0/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
 VFS: Cannot open root device "UUID=0e1743a4-c94b-4d0d-b5cf-0d6165eebf10" or unknown-block(0,0)
 Please append a correct "root=" boot option; here are the available partitions:
 Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[/FONT]  
 I have read the following two threads, which relate to "WARNING bootdevice may be renamed.", but these are slightly different from my problem.
 [http://ubuntuforums.org/showthread.php?t=1865439]("http://http://ubuntuforums.org/showthread.php?t=1865439")
 [http://ubuntuforums.org/showthread.php?t=1861871]("http://http://ubuntuforums.org/showthread.php?t=1861871")
 
 I also tried booting from the installer CD, and running yabootconfig:
 [FONT=Courier New]sudo mount /dev/sda3 /mnt
 sudo yabootconfig --chroot /mnt --root /dev/sda3
 sudo umount /mnt
 sudo reboot[/FONT]
 
 This doesn't help; I get the same messages.

Did anyone else have challenges booting after an upgrade, or know what might be wrong?

---

### Post by jumil on 2011-10-20
Have you tried to use the entire disk rather than erasing 11.10 and reinstalling into the old partition? Since yaboot seems to have trouble finding your entire harddrive repartitioning it might help. Or are you dual booting OSX?
Unless I am reading the error wrongly that is. I am not an expert yet either.

I have not tried upgrading or installing from a live disk yet but have been able to install Ubuntu onto my iBook G4 by installing a 11.04 command line system from the mini iso and upgrading that.
I did this because the 11.10 mini iso would not recognize my harddrive during install and thus would not even offer to partition it.
I used the mini iso so I would be able to choose from the different desktop environments before installing mint Ubuntu. I ended up using Ubuntu anyway, but thats a different story.

It runs like charm except for some trouble with the backlight, sleeping and wifi indicator. No absolute show stoppers really.
[http://ubuntuforums.org/showthread.php?t=1863407](http://ubuntuforums.org/showthread.php?t=1863407)

I'd be curious to know if you can reproduce that behavior with the current live disk or the mini iso method I used.

It now occurs to me that the 11.10 isos, mini or desktop, having trouble recognizing the harddisk at some point might be a recurring theme here.
What iBook G4 do you have exactly. And how big is the harddrive?
[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

---

### Post by mpicker0 on 2011-10-21
[COLOR=#000000][FONT=Sans Serif]I have tried using the entire disk, not just installing into the old partition.  I have gone as far as running mac-fdisk by hand and deleting all the partitions.  I am not dual-booting OSX.[/FONT][/COLOR]

 [COLOR=#000000][FONT=Sans Serif]Earlier today, I tried installing 11.04 from a mini ISO (like you, the 11.10 mini ISO did not recognize my hard disk), but had problems with it related to mismatched signatures from the mirror.[/FONT][/COLOR]

 [COLOR=#000000][FONT=Sans Serif]I'm not exactly sure which iBookG4 I have; it is a white 14-inch model with a silver audio jack, purchased in the summer of 2004.  The model number on the bottom is A1055.  It has a 40GB hard disk.[/FONT][/COLOR]

 [COLOR=#000000][FONT=Sans Serif]Thanks for the suggestions; I think I will probably go back to 10.10 (11.04 had some high CPU issues which are documented on the forums, for example [http://ubuntuforums.org/showthread.php?t=1859152]("http://http://ubuntuforums.org/showthread.php?t=1859152")) until some better news comes out.[/FONT][/COLOR]

---

### Post by fixerdave on 2011-10-22
I've got the same error.  This is on a "use whole disk" install of 11.10 to a Mac Mini PPC.  I've gone all through Yaboot hell, up to manually editing the yaboot.conf file and then using ybin with the -C option to use said edited config file.  It's still saying "Cannot open root device "sda3" or unknown-block(0,0)"

As fdisk -l shows /dev/sda3 has the root file system and that's what I put in the config file... well, I'm starting to think it may be that 'or' thing... unknown-block(0,0).  Whatever that is... maybe something that needs the hctosys.c(rtc0) bit that errored out right before (though google says it's about the real-time-clock).

Sigh... maybe time I dust off that 10.10 disk too.  It's just annoying as it seems sooooo close.

Edit: interesting... the 10.10 install shows the internal drive as hda, not sda... yet it reported the other way round in 11.10... (doubting myself now - hate that feeling).  Though, I had typed in hda3 on the first go round with yaboot.conf anyway (following the examples while not checking).  Maybe that's the source of the error... Me thinks I'll be checking the contents of my 1TB usb drive after 10.10 finishes it's install.  Not a big deal... just did a backup of it anyway.  Edit: Yeah, scrambled... sigh.  Note to self: unplug all USB drives before starting install.  Might have been the source of the error.

---

### Post by raganius on 2012-01-10
Hello everybody! I also have Apple PowerBook G4 with 867Mhz CPU, 512Mb  RAM and new 160gb Samsung HDD. I wanted to install 11.10 from Live CD as  I have Installed for my PC, but unfortunately the most recent version  is daily build of 12.04LTS Precise Pangolin.
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
I have burned boot Live CD and it booted without problems. The Unity GUI  was working fine. Then I started clean installation (that Ubuntu would  manage space & wipe old data) with internet connection and option to  apply latest updates, and with install/user interface language &  keyboard set to Lithuanian, location to Vilnius. Everything seemed fine,  but in almost end was: "Archive Mirror Error". Then I started clean  installation without internet connection & latest updates - result  was the same. The 3rd Install was with internet connection & latest  updates but with installation language & keyboard set to English,  location to London - result was the same. I tried these different  settings, because I thought that the local mirror I am connecting to  doesn't have Ubuntu for PowerPC image or distribution files -  unfortunately Live CD Ubuntu installation doesn't give option for mirror  selection.

Then I downloaded Ubuntu 10.10 Maverick Meerkat Live CD - Installation  went well. Unfortunately there was no Unity GUI. Updates for 10.10.  downloaded & installed well, upgrade to 11.04 also went well,  however I was given notice that my graphic card doesn't meet  requirements (As I understood for Unity GUI sidebar) even 12.04 live CD  started that Unity interface with sidebar, and there wasn't any error  when I used it. Then I started suggested upgrade to 11.10.After more  than 2 hours upgrade seemed completed and then there was white screen in  full contrast appeared, signaling something was wrong with the  installation (I don't remember at the moment was there also a Archive  Mirror Error). After waiting for 10minutes & forced turn-off, G4  started with these suggestions: 

Gave up waiting for the root device. Common problems:
   - Boot args (cat /proc/cmdline )
     - Check rootdelay= (did the system wait long enough?)
     - Check root= (did the system wait for the right device?)
   - Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/ba9fa3f2-3805-41c2-bc77-coc720064bf4 does not exist. Dropping to a shell!

BusyBox 1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

Then I started booting from 11.10 mini.iso but it haven't found my HDD  controller. Maybe it is why the upgrade from 11.04 to 11.10 went wrong?

Then I tried booting from 11.04 mini.iso with mirror from London,  Language & Keyboard set to Lithuanian and location set to Vilnius,  selected install security updates automatically & Ubuntu Desktop as  the only package. Ubuntu started well, however I got the same message  regarding that my system doesn't meet requirements for Unity GUI (even  it was working on 12.04 Live CD) and the I again started suggested  upgrade to 11.10 - again after 2hours of waiting the same white screen  of misery, the same console messege that I wrote above!!!

It may seem strange to you why I went all this way to mini.ISO of 11.04  and then again 11.10 - I really badly wanted the most updated OS my MAC  can get, and I thought that there was a readon why for 11.04 & 11.10  mini.ISO are suggested. However, it is a shame that even this day 11.10  miniISO for PowerPC is suggested, when there are reports that 11.10  mini.ISO doesn't find HDD on G4. 

Then I tried to install 11.04 mini.ISO with Location & Keyboard set  to US, and Location set to Toronto. I was suggested the same London  mirror. After Install I was suggested the same upgrade to 11.10. As  allways there were no updates to 11.04. Of course I didin't upgrade to  11.10 this time, I couldn't find any logical reason what could change: I  tried different images (2 LiveCD, 2 mini ISO), I tried 2  Language,Keyboard & Location profiles)...
And then G4 was very noisy all the time, it seemed that the management  of CPU speed, power consumption, ventilator speed wasn't working. Then I  noticed that GPU was very slow also - it seemed like it worked on a  generic driver - it was really much much much smoother in MacOS X 10.5  Leopard. I tried to install VLC media player to test how it works with  the movies - installation failed. Chromium also failed but I guess it is  because they don't offer distribution for PowerPC platform. However  installation of other programs, like Last.fm client, Epiphany, Audacious  & few others went well. Then I changed system updates settings to  include unsupported & pre-released updates. The only worthy updates  were 3 Kernel updates - I was prepared that system would crash, but  contrary it made the system more responsive and run faster & even  GPU was running faster, or it seemed like that (I couldn't see frames  when scrolling up & down, for example in system settings), but not  fast enough as in MacOS.

Thank you for reading this extensive description of my problem. I really need a good advice: 
What is the best system for my PowerBook G4? Should I stay with 10.10 or  10.04? Is there a solution to Archive Mirror Error when Installing  12.04 from Live CD?
Can I have Unity GUI with sidebar as in 12.04 LiveCD?
Is it possible to make 11.10 to run?
Is it possible to apply some kind of CPU management & GPU drivers in 11.04?
I haven't tested 10.10 properly and it would took me another 3 hours to  get there, so this time I need suggestion, is CPU management & GPU  performance better in 10.04/10.10?

Please help! I believe I tried really hard looking from the user  perspective - I am not a programmer,developer, I don't have knowledge to  modify Linux distributions, kernels & compile kernels.
I started to look for the best Ubuntu for my G4 after I found 11.10 on  my Toshiba Satellite L100 stable, quick & interesting. Thank you for  reading again.

---

### Post by rsavage on 2012-01-10
It's very frustrating to read your long list of problems.  On the PowerPCDownloads page is a link to instructions on how to install from the mini cd.  If you read that it will answer all your queries.
 
I've also spent quite a lot of time updating the [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) page and I'm still in the process of updating the [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) page.  I will add links to these too on the PowerPCDownloads page, but since you've ignored the instructions I wrote already then I'm not sure if that would of helped in your case.  If you can give me any advice how these should be linked so that people read them I would be grateful.  
 
Your mirror server problem with live CDs is answered here [http://ubuntuforums.org/showpost.php?p=11409752&postcount=27](http://ubuntuforums.org/showpost.php?p=11409752&postcount=27) .  No idea if it works with 12.04.

---

### Post by fixerdave on 2012-01-11
> **rsavage said:**
> ... 
I've also spent quite a lot of time updating the [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) page ...

Very nice, thank you!  Now I don't feel so crazy about the hda/sda bit.  The yaboot info is much appreciated as well... seems I went the long way around on that one... certainly not the first time, sigh,

   David...

---

### Post by raganius on 2012-01-12
Dear rsavage,

This is the quote from PowerPCKnownIssues
[https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_11.10_Oneiric_Ocelot](https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_11.10_Oneiric_Ocelot)
**Ubuntu 11.10 Oneiric Ocelot**

  
**Mini iso fails to recognize hard drive**

 The mini iso  (debian-installer or d-i) is missing the pata_macio module.  If your  machine requires this module then you may get some sort of message  telling you that your hard drive has not been recognised.  The easiest  solution is to install 11.04 and immediately upgrade.  The kernel team  are [already aware of this]("https://lists.ubuntu.com/archives/kernel-team/2011-November/017979.html") and it will be fixed in 12.04.

So, as instructed on [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) 
**I used minimal CD (mini.ISO) to install 11.04 & 11.10**. And I have wrote that :
"and then I again **started suggested  upgrade to 11.10** - again after 2hours  of waiting the same **white screen**  of misery, the **same error in the console**: 

"Gave up waiting for the root device. Common problems:
   - Boot args (cat /proc/cmdline )
     - Check rootdelay= (did the system wait long enough?)
     - Check root= (did the system wait for the right device?)
   - Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/ba9fa3f2-3805-41c2-bc77-coc720064bf4 does not exist. Dropping to a shell!"

As you can see, your **suggestion to use minimal installation CD for 11.04 and then upgrade to 11.10** & to use **this post** 
"For 11.04 and 11.10 use the minimal CDs and follow instructions in this  post 
([http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1))  "

& **read this link**: 
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

& **to read this link**:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

could be more helpfull, because "The easiest solution is to install 11.04 and immediately upgrade to  11.10" advice doesn't work for me and I wonder is it a good advice for  somebody? I updated from 11.04 to 11.10 three times (2 times after intalling from 11.04 from minimal CD and instantly upgrading to 11.10) and I got the error that is written above and is not put in the known issues list, and all this mess could be avoided if there would be
1.Clearl list of actually working releases without workarounds. From my experience, 11.10 you have to use workarounds to start it.
2.If there are problems for the specific PowerPC users with specific release, warnings should be given for these PowerPC users in the download page. If most of PowerPC users doesn't have this issue, then there should be warning only to these users. If most of people is shocked with BusyBox after upgrade from 11.04 to 11.10, then it is not easiest sollution from the users point of view as mentioned in PowerPCDownloads page, so then I suggest that in [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) you only list 11.04 minimal CD installation giving link to [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) , because it is the currently working installation that you don't need workaround and in the separate line mention that if somebody wants 11.10 the easest way is to install 11.04 from minimal CD, then instantly upgrade to 11.10, then fix BusyBox problems using instructions mentioned here: 
[https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_11.10_Oneiric_Ocelot](https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_11.10_Oneiric_Ocelot)
3. If there would be a fresh step-by-step instructions for 11.04 & 11.10. Thank you for creating [How to install power pc Lubuntu 11.04 with Firefox 5]("http://ubuntuforums.org/showthread.php?p=11020435#post11020435") . But I have to say that too much of irrelevant information is supplied thrtr for users who are installing Ubuntu 11.04 & 11.10. It really doesn't need to be the first reference for installing 11.04 & 11.10 in PowerPCDownload page in my opinion. Short, 12 step (for example) instruction should be enough for most of the people who had no experience with Ubuntu before, because in 11.04 installation you just have to follow what is suggested - it is fairly stress & difficulty free, especially if you are proceeding with a fresh install. When in the PowerPCDownload page 11.04 and 11.10 are mentioned next to each other, then it seems for the user that is equally easy to install 11.04 and 11.10, and that they both offer the same level of integrity, wich is certainly not true from my experience.
4. Error mentioned above would be listed in the PowerPCKnownIssues. I admit that I am unexperienced with Ubuntu OS terms, commands, structure but when I read 
[https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_11.10_Oneiric_Ocelot](https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_11.10_Oneiric_Ocelot)
I didn't realize that 
a.) the error I got was in BusyBox environment (as you can see there is no term BusyBox in error description). I couldn't find clear answer/term what is BusyBox, and what does it do in Ubuntu.
b.) as I understand now everybody faces that BusyBox error after upgrade from 11.04 to 11.10. If it is true, it wasn't mentioned that this is immediate problem after installing/upgrading to 11.10. I would suggest that known issues, if they are connected would be mentioned in steps, and not as a separate problems in PowerPC Known Issues.

Thank you for creating [PPC] How to install power pc Lubuntu 11.04 with Firefox 5 again. Thank you for showing me solutions for my problems by giving links. If after all I will succeed with 11.10 installation I will use this link 
[http://ubuntuforums.org/showpost.php?p=11483024&postcount=11](http://ubuntuforums.org/showpost.php?p=11483024&postcount=11) 
to repair Unity interface, even the problem is described as "Ubuntu-desktop won't install" - not sure if it will help in my case.

To everybody who is reading:
I would encourage other PowerPC users, who experience the same problems to make a short post here, because now it seems that I am the only one having problems with information that is listed in the download & known issues page, how installation issues are listed only in known issues page and how suggested connected problems have seperate, and not step-by-step solutions. I can make a short, step by step manual for users installing 11.04 from minimal CD, if you agree that it is needed and I am the right person to do it.

---

### Post by rsavage on 2012-01-12
Yeah, and on the Known Issues page is a heading "Busybox prompt after upgrade".  Is this not your problem?

---

### Post by rsavage on 2012-01-12
raganius, I think you'd of been better posting a new reply rather than editing your previous post.
 
The wiki's are free for anybody to edit them. So if you feel the instructions are unclear then you have the power to make them better.
 
With respect to the Lubuntu instructions, yes I am aware that they are not ideal, they appear too wordy and people don't want to read them. It seems there is a culture now of hitting google and reading page after page of irrelevant stuff rather than instructions that are put in front of you. People then hit the forum tired and frustrated and they don't get much sympathy from me.
 
That is why I'm transferring the information to the PowerPC FAQ. People can change the instructions how they want then. I won't be reading the forum to pick up the pieces.
 
EDIT: Just to add quickly, not all machines have the pata_macio module so the 11.10 iso is still relevant for some people. Personally I like how the Downloads/KnownIssues pages are structured at the moment. The downloads page is clean and uncluttered. When I finish the FAQ I will change the install link away from the Lubuntu instructions. The FAQ already has shorter instructions about installing from the mini iso. I don't think the information is "irrelevant", you have to appreciate others may have different problems/needs to yourself. From experience, getting people to do a cli install first is far less error prone, something you may turn out to realise.

---

### Post by rsavage on 2012-01-13
> **raganius said:**
> If after all I will succeed with 11.10 installation I will use this link 
[http://ubuntuforums.org/showpost.php?p=11483024&postcount=11](http://ubuntuforums.org/showpost.php?p=11483024&postcount=11) 
to repair Unity interface, even the problem is described as "Ubuntu-desktop won't install" - not sure if it will help in my case.
 
The Known Issues page is assuming you are following the instructions from the FAQ. So that is why it says ubuntu-desktop won't install. It will make sense if you follow the instructions.
 
> I would suggest that known issues, if they are connected would be mentioned in steps, and not as a separate problems in PowerPC Known Issues.

I'm still not convinced you have read the FAQ instructions or the lubuntu instructions. The missing pata_macio module is described in the Lubuntu instructions (because the 11.10 Known Issues section was not written when I wrote the guide) and a problem with the 11.10 iso is described in the install instructions in the PowerPCFAQ. So I can't see how you can say the problem is hidden away on the Known Issues page. The busybox problem only effects certain machines btw.
 
The FAQ and Known Issues pages are still in a state of flux. I haven't yet fully decided where information will end up. My current thinking is that the FAQ shouldn't have any release specific information, just general stuff. So the workaround to upgrade from 11.04 to 11.10 (at present in the FAQ) will probably end up in the known issues page. That way the FAQ doesn't seem outdated when 12.04 is released etc.
 
EDIT: I have made the change described above.  See what you think.

---

### Post by raganius on 2012-01-23
Hello everybody! I succesfully installed 12.04 Precise Pangolin using LiveCD on my PowerBook G4 without internet connection and without any modification to LiveCD or fixing various boot errors with workarounds in Busy Box! So if you want most recent working installation from LiveCD choose 12.04 LiveCD!
More about installation process.
Just for reference my Mac PowerBook G4 has 7455 series CPU with 867Mhz and 512Mb Ram - It is reported that it will work with iBook G3 as you can in see here in [http://agentoss.wordpress.com/2011/12/23/ubuntu-12-04-precise-pangolin-on-imac-g3-powerpc/](http://agentoss.wordpress.com/2011/12/23/ubuntu-12-04-precise-pangolin-on-imac-g3-powerpc/) where you can see step-by-step instructions for alternative network installation using Terminal/Console. I downloaded 12.04 Precise Pangolin daily build on 21 January from [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) and burned it onto DVD+R. I am pretty sure that with the good quality CD-R and OverBurn and ShortLeadOut option you would succesfully burn 721Mb .iso file - I tried to do it in the past and Nero CD verification tool found no errors, however I was not successful with installation, but I think this was because I was using Internet connection and haven't tried to install from that CD-R without internet connection, so I can't confirm it, however I believe it would work).
In my case The Secret to successful installation was to install 12.04 without internet connection (I tried 2 times installing with modified /etc/hosts file to avoid Archive Mirror Error and using download available updates & fraunhofer option but without success). Without internet connection all went well to the end of the installation and because pata macio module is added in 12.04 LiveCD there was no need to add pata macio module before to installation or during the installation. After installation it just booted from the first time - there was no Archive Mirror Error or boot problems that needed fixing with BusyBox. 
( [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) ). In the boot screen it says 12.04 but in the system info it says 11.04.
So, to summarize the improovements are:
1.Easy step by step installation using Unity GUI from LiveCD.
2.No Archive Mirror Error if you are installing without internet connection.
3.No BusyBox prompt after installation.
4.Boots from the first time (also shutdowms and restarts without any problem).
5.Unity GUI is working on G4 VGA card without any errors.

There some important faults I experienced that maybe be a relevant to you:
1.G4 Airport Wifi doesn't connect even to a wireless router even without password (unsecured wireless router).
2.Graphic card works on generic driver so Ubuntu unity may seem slow if you were working with faster GUI before - but IMO it is definitely a huge improvement over GUI used in Ubuntu 10.04/10.10. Video performance is worse than working with Mac OS 10.5 Leopard, but IMO the GUI is much more logical and useful than Leopards, so it is worth using it and waiting for further improvements. 
3.Ubuntu Software Center is slow - If you know how to use apt-get, I would recommend to use it because it is a much faster option.
4. After booting the system the sound is muted/turned of, so you have to manually activate sound.
5. There is a limited number of apps compared to Intel x86 platform. Particularly painful is the absence of Skype, Adobe Flash, Shockwave and Java (this software is present for and working on MacOs X Leopard 10.5) - of course you know about this if you have used Ubuntu on you PowerPC MAC before. They are also listed here: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
6. Memory usage is pretty high - command "top" in terminal showed that that all of 512mb of RAM is allready used, even when launching one application at a time: Mozilla, Software Center, Opera. The CPU use is also higher and the system is not so smooth as 10.04/10.10. It could be because of Unity GUI or it could be kernel - it is only my guess. I hope that can be solved with newer 3.2.0-10 kernel (the version that comes with 12.04 Precise Pangolin is 3.2.0-9).
7.Errors from various programs, but it is not annoying and expected from unofficial release.

To rsavage: I will write my suggestions to current PowerPc Download/KnownIssues/FAQ page later - I still think it can be improved to be more helpful and attract more of MAC PowerPC users. I believe is the only one serious alternative to MacOS X Leopard, the most serious alternative platform for PowerPC owners to migrate in order to revive old PCs left that where left on its own.

---

### Post by rsavage on 2012-01-23
raginus, don't encourage people new to linux to install 12.04 unless you are going to answer every problem that gets raised on the forum.  12.04 is still in heavy development and is not for everyday use.  
 
It is also pointless to add a list of problems with it on the known issues page as things are likely to change every day.  Ideally, known issues should be confirmed by others and discussed on the forum.  The page is really there to pass on good workarounds and to save people the time searching the forums.  However, please feel free to add your feedback about the live cd install to what I already wrote.
 
I'm glad you are happy with your install though.

---

