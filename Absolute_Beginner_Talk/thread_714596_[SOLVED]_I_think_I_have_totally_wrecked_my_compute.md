---
title: "[SOLVED] I think I have totally wrecked my computer"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by roshm on 2008-03-04
I installed Ubuntu and the wireless did not work,  now windows is gone too. I can't even get into the os with safemode. I can't help but feel the firmware.. if any that came with my wireless connection is gone. If so I have no idea how to find it or re-install it with Ubuntu.  Ubuntu is still there.    Any ideas other than putting a presario 500c in the garbage?

---

### Post by Rocket2DMn on 2008-03-04
That's not very useful.  Is there something in particular that is wrong that you would like us to help you with?

---

### Post by hhhhhx on 2008-03-04
why?, what happened?

---

### Post by nmartine on 2008-03-04
And then what happened?

---

### Post by roshm on 2008-03-04
well wasn't those speedy replies from a tight knit community....  thanks guys.

---

### Post by gtdaqua on 2008-03-04
roshm, so u re gonna tell us or what? whats the exact problem? u cud still use the ubuntu live CDs without having to install and recover data.

---

### Post by roshm on 2008-03-04
the data I am concerned about is in vista... it allocates the pci regions when it starts.  Now it won't boot in Vista. I moved, and don't have the recovery disks I made. I have the Ubuntu cd and really hate vista.... good combo huh?  I need my network connections and I don't have them right now with Ubuntu.

---

### Post by kbless7 on 2008-03-04
you're gonna want to boot into ubuntu, open a terminal and type

```
sudo gedit /boot/grub/menu.lst
```

Then go the bottom of the page and add

```
Windows Vista Sucks
root     (hd0,0)
makeactive
chainloader     +1
```
of course the (hd0,0) part depends on which partition you have windows loaded onto. this will make windows available in the grub menu list upon startup

---

### Post by roshm on 2008-03-04
Thanks for the interest, but no go.  The first command went through then I was asked to provide a password.  I did so and got " command not found "  now if I try the command there is no promp for a password and I get straight away "  command not found "  still trying to figure out how to log on as root.
I have found my hardware listed in the terminal and used ndiswrapper to install a network driver and have found the driver in the terminal and it is working.  When I physically press the wireless button on the unit the light does not come on.  When I plug into the ethernet there is no light also.  I can find these pieces of hardware on the terminal, but there seems to be no power going to them.  If I can learn how to get  Ubuntu on the internet and sync with my palm pda  I see no reason to maintain Vista.  I should also note a special thanks to my Girlfriend for letting me use her computer.

---

### Post by philinux on 2008-03-04
I would copy and paste that command to make sure no typos.

---

### Post by justin whitaker on 2008-03-04
> **roshm said:**
> Thanks for the interest, but no go.  The first command went through then I was asked to provide a password.  I did so and got " command not found "  now if I try the command there is no promp for a password and I get straight away "  command not found "  still trying to figure out how to log on as root.
I have found my hardware listed in the terminal and used ndiswrapper to install a network driver and have found the driver in the terminal and it is working.  When I physically press the wireless button on the unit the light does not come on.  When I plug into the ethernet there is no light also.  I can find these pieces of hardware on the terminal, but there seems to be no power going to them.  If I can learn how to get  Ubuntu on the internet and sync with my palm pda  I see no reason to maintain Vista.  I should also note a special thanks to my Girlfriend for letting me use her computer.

To login as root, first you need to execute sudo password, and give root it's own password. Then you will be able to login and execute the above commands.

---

### Post by Tatty on 2008-03-04
> **roshm said:**
> Thanks for the interest, but no go.  The first command went through then I was asked to provide a password.  I did so and got " command not found "  now if I try the command there is no promp for a password and I get straight away "  command not found "  still trying to figure out how to log on as root.
I have found my hardware listed in the terminal and used ndiswrapper to install a network driver and have found the driver in the terminal and it is working.  When I physically press the wireless button on the unit the light does not come on.  When I plug into the ethernet there is no light also.  I can find these pieces of hardware on the terminal, but there seems to be no power going to them.  If I can learn how to get  Ubuntu on the internet and sync with my palm pda  I see no reason to maintain Vista.  I should also note a special thanks to my Girlfriend for letting me use her computer.

_You should never log in as root in Ubuntu_, there is no need to and it opens a massive security risk.  The root account is disabled by default.  To perform root actions you need to use the command "sudo" before whatever you want to do...  The password it asks you for is the password you logged into your account with.

It sounds like your probably made a typo somewhere as "sudo gedit /boot/grub/menu.lst"  should open the file in a text editor with root privilages.  Or if you are using kubutu you might want to try "sudo kate /boot/grub/menu.lst".

If all of that fails try "sudo nano /boot/grub/menu.lst" as that will open it in a text based text editor in the terminal.

Although what worries me most is that you say the wireless light does not come on when you press the button on your laptop - that should be entirely hardware dependant, and the fact that it does not come on sounds like a possible hardware problem.

---

### Post by roshm on 2008-03-04
I tried " sudo gedit /boot/grub/menu.1st "  and found it was a keyed error on my part. I was presented a "tabbed window? " with one tab and it was named menu 1st.  The page was blank and I entered nothing because when I turn on the computer I am given a list of boot options.  Ubuntu, Ubuntu (recovery mode), and Windows Vista.  When I try to boot in Vista the screen just stays blank. When I try to boot in Vista Safemode the files start to load and then stops.  I think when I used the partitioning option Ubuntu supplied, and configured my hard drive space I damaged the files needed to run Vista.  I created an extra partition of 5 gigs and chose that area to swap files.  The version of Ubuntu I installed is (Edgy Eft )  version 6.10.  I puchased a book called Linux Bible 2007 Edition.  The hardware is fine.  Was working 100% before I tried to use Ubuntu

---

### Post by NiceGuy on 2008-03-04
Ok, right... first of all,

DON'T PANIC

Right, first of all there is no way you have damaged the hardware of your PC (or wiped the firmware of your wireless card or whatever) by installing ubuntu. The WORST case scenario is that you have formatted the hard drive/partition with windows on it and if you want to dual boot with windows or whatever then you will have to re-install vista but lets see if thats the case or not.

Right lets see if I've got this straight.

Your computer had windows Vista installed on it and you say you installed ubuntu.

Right now HOW did you install ubuntu? Did you put it on a separate partition or separate hard drive or did you just click 'use all of the hard drive'.

If you did install it on a separate partition or drive to your windows installation then what we need to do it edit the grub bootup menu and make sure you've got vista listed so you can boot to it again (normally it does this automatically but sometimes weird things happen in the wonderful world of computing).

If on the other hand you did click use all drive or something similar then thats ok, again don't panic you machine is not lost, but you personal data stored in windows may be.

To find this out if your not sure then open up a terminal (Applications > Accessories > Terminal) and type:

```
sudo fdisk -l 
```

That's **sudo** (super user mode), **fdisk** (a program for partitioning hard drives, don't worry we're just using it to find out whats there) and  **-L** (the 'L' is lowercase and means list partitions) in short this command will tell you what partitions are on you drive. 

Then.... well tell us what you see and what you want to do - eg. "I see my windows partition (the NTFS one) it is at /dev/sda1 and I want to be able to boot into windows" or "Its gone I just have an ubuntu partition and a swap partition but its ok as I didn't like vista anyways"

Once we establish that we can move on.

If you did want to completely get rid of windows then ok, we move onto 'sorting out your wireless' but if not then you may have to reinstall windows (which may be tricky without recovery disks). and then we can see about talking you through correctly partitioning your hard drive so you can dual boot.

I realize that I'm bombarding you with information but I've got one more 'tip':) 

As a quick tip about your wireless, assuming its an internal one then you may need to make sure its configured to be 'on at start up' in your bios as that may be a stop gap solution till we find the correct drivers for powering up your wireless via a button. The bios is normally accessed by pressing the 'delete' or sometimes 'F2' key when your computer first starts boot (normally at the manufacturers splash screen or if thats not turned on when your computer is checking the RAM).

ps. its getting late here so you may have to wait till the morning for an answer from me, but I'm sure others will be able to take over. But I think its important to find out the situation with your hard drive before we go any further and you start editing your grub menu etc.

---

### Post by roshm on 2008-03-04
I can access what is called "PhoenixBIOS Setup Utility" by using the esc key during system  boot.    embedded wlan device radio is on...  sata Native support is on. This is a setup utility and not a bios screen I have seen before.  Your  assessment of my situation is correct.  I would also like to mention I am not too concerned about not having Vista as my o.s.        as for my partitions????   I have 4.  dev/sda1 and dev/sda2 have a system named hpfs/ntfs and dev/sda3 has a system named linux.  dev/sda4 has a system named linux swap / solaris.    to find that information I used " fdisk -l "

---

### Post by philinux on 2008-03-04
> **roshm said:**
> I tried " sudo gedit /boot/grub/menu.1st "  and found it was a keyed error on my part. I was presented a "tabbed window? " with one tab and it was named menu 1st.  The page was blank and I entered nothing because when I turn on the computer I am given a list of boot options.  Ubuntu, Ubuntu (recovery mode), and Windows Vista.  When I try to boot in Vista the screen just stays blank. When I try to boot in Vista Safemode the files start to load and then stops.  I think when I used the partitioning option Ubuntu supplied, and configured my hard drive space I damaged the files needed to run Vista.  I created an extra partition of 5 gigs and chose that area to swap files.  The version of Ubuntu I installed is (Edgy Eft )  version 6.10.  I puchased a book called Linux Bible 2007 Edition.  The hardware is fine.  Was working 100% before I tried to use Ubuntu

I asked you to copy and paste because it's not menu.1st its' menu.Lst but its a lower case L

---

### Post by roshm on 2008-03-04
Greetings Philinux.  I am unable to copy and paste because the computer I am trying to install Linux on is not on the net or connected with a network to the computer I am using for this forum.   All help is greatly appreciated, thanks.

---

### Post by philinux on 2008-03-04
> **roshm said:**
> Greetings Philinux.  I am unable to copy and paste because the computer I am trying to install Linux on is not on the net or connected with a network to the computer I am using for this forum.   All help is greatly appreciated, thanks.

Ok so use the command with the lower case L not a 1

---

### Post by roshm on 2008-03-04
Well now thats a handy little item to remember.  Lesson 1, how to access the grub file and write to it. I found that it didn't give me any more options at startup than I already had tried.  Thanks anyway though, still no power to the networking hardware

---

### Post by StandardBlueCaboose on 2008-03-04
> **roshm said:**
> I can access what is called "PhoenixBIOS Setup Utility" by using the esc key during system  boot.    embedded wlan device radio is on...  sata Native support is on. This is a setup utility and not a bios screen I have seen before.  Your  assessment of my situation is correct.  I would also like to mention I am not too concerned about not having Vista as my o.s.        as for my partitions????   I have 4.  dev/sda1 and dev/sda2 have a system named hpfs/ntfs and dev/sda3 has a system named linux.  dev/sda4 has a system named linux swap / solaris.    to find that information I used " fdisk -l "

Ok, so it seems like you've got 2 NTFS partitions, one is possibly a recovery partition added by your hardware manufacturer. It seems to me as if the Vista partition is still there, so that's good news.

Is it possible to plug an Ethernet cable into your laptop, so you have access to the internet? Just for now, until things get sorted out.

---

### Post by roshm on 2008-03-04
1st answer is yes the partition is from the manufacturer and unfortunately the second answer is no.  I have one internet cord. The grub file make me think of how Vista would boot.  HP Wireless Assistant would start automatically and with Ubuntu it doesn't.  Is there a way I can have that program boot in Ubuntu?

---

### Post by crjackson on 2008-03-04
If I were you, I would download and burn ubuntu 7.10 Gutsy Gibbon LiveCD.  Boot from that CD and see if you have better luck with your internet connection.  The newer distro has better support for wireless and it may work out of the box.

If that works, chances are you will be better off installing the newer version of Ubuntu and perhaps that alone will solve most of your problems.  It's worth a try...

---

### Post by bobbob1016 on 2008-03-04
roshm, what they are doing with the "sudo gedit /boot/grub/menu.lst" command is getting your computer to boot Vista again.  

All you do is open a terminal, by clicking Applications->Accessories->Terminal
Then type "sudo gedit /boot/grub/menu.lst" without the quotes, it is menu.Lst with a lowercase L.  That is the list of things you see when you boot.
Secondly, they are having you add vista to that list, by adding
"Windows Vista Sucks
root     (hd0,0)
makeactive
chainloader     +1" 
without the quotes, to the end of the file, and saving it.  This SHOULD get you back in to Vista when you reboot.

When you reboot, you will see a list, containing items like Ubuntu, Ubuntu Recovery Mode, and memtest, you should also now see one called Windows Vista Sucks, you press the down arrow on the keyboard until Windows Vista Sucks is highlighted in white, then pressing enter.  You SHOULD now see Vista.

Also, I noticed you said your laptop is a Pavillion 500c, are you sure you didn't mean C500?  I am just asking, since it will make it easier for you to figure out what you need for your wifi if you have the correct model number.

Also also, I agree with everyone else, it is not possible that Ubuntu broke your hardware, or erased the firmware or anything.  Ubuntu might require firmware to work with your wifi card, but it didn't erase it.  I'd suggest finding somewhere connect the laptop to the internet with ethernet (Lan) cable.  This will get you online with Ubuntu for the time being.  I'd recommend once you get Vista working again, and backed up your data, to do a fresh install of either Ubuntu Feisty (one version behind) or Gutsy (the latest as of March 4th 2008).  They contain a program called "Restricted Drivers Manager" which installs drivers for a lot of hardware automatically, although I am not sure if your wifi will be included in that, it is worth a try.

---

### Post by crjackson on 2008-03-04
> **StandardBlueCaboose said:**
> Ok, so it seems like you've got 2 NTFS partitions, one is possibly a recovery partition added by your hardware manufacturer. It seems to me as if the Vista partition is still there, so that's good news.

Is it possible to plug an Ethernet cable into your laptop, so you have access to the internet? Just for now, until things get sorted out.

It's not just a recovery partion.  The it actually does have the BIOS configuration loader on some Compaq's and you must boot to that partition to change your BIOS settings.

---

### Post by roshm on 2008-03-04
how would I boot to that partition?

---

### Post by Tatty on 2008-03-04
> **roshm said:**
> HP Wireless Assistant would start automatically and with Ubuntu it doesn't.  Is there a way I can have that program boot in Ubuntu?

No, that is windows software so wont work in Ubuntu.  Ubuntu has the "network-manager" application which does all the same things - although occasionally it doesnt quite work out of the box.  It should load automatically as an icon in the top-right corner of the desktop.

Which version of Ubuntu are you using?  Apologies if you already said and i missed it...

---

### Post by zabien1970 on 2008-03-04
Maybe not that important but on my dell laptop the wireless light doesn't work but I can still connect so don't rely on the light for an indication of internet connection

---

### Post by bobbob1016 on 2008-03-04
roshm, First try what was suggested with editing the menu.Lst (lowercase L) file.  If the hd(0,0) doesn't work, try making it "hd(0,1)" without quotes, and try progressively moving the number up until you see Vista boot, although 1 should work.  DON'T add it to your menu.Lst (lowercase L) each time, just modify the "hd(0,0)" without quotes, line under the Windows Vista Sucks line to "hd(0,1)".  This should get you back into Vista.  I think this will ease your nerves a bit, since you feel you lost Vista and damaged your hardware.

---

### Post by crjackson on 2008-03-04
> **roshm said:**
> how would I boot to that partition?

The same as any other BIOS config.  There is a Key combination you must press when the BIOS report screen is displayed.  I don't know off hand what it is for your computer, but it should tell you to Press (whatever key) for setup.

---

### Post by roshm on 2008-03-04
I do, and I have the option of trying to boot vista.  I have tried and it doesn't load.  I have tried safemode and it freezes while loading the needed files.  I don't care If I have Vista, but I do need an OS that functions on a network.  I have tried to download and install a wireless assistant and I get the error that my machine is an i386 and the vender chose to not support my laptop.... whatever that means.

---

### Post by roshm on 2008-03-04
I can't help but feel that the networking section in the bios has been altered during installation. I can use a bios utility but I cannot get to the bios.  Any ideas? oh well back to searching.

---

### Post by bobbob1016 on 2008-03-04
If you don't care about Vista, plug your laptop in via ethernet, just for now.  Go to [www.ubuntu.com](www.ubuntu.com) and download an ISO for Ubuntu Gutsy Gibbon (version 7.10).  
Put in a blank CD, click "Ignore" when it asks what you want to do.
Right click the file you downloaded, and click "Write to disc".
When it is done, reboot and install Ubuntu.
There should be an option in the install that says something like "Remove all linux partitions and install there" or something like that, select that option.

Once you have it installed, just plug the ethernet in again, click System->Administration->Restricted Drivers Manager, you should see something about your wifi card there, click the checkbox to install it if you see it, then click Apply.  You should be ok after that.

EDIT:  Ubuntu did not touch your BIOS, all that it does, and I'm not sure it does it anymore, is set your clock to the time Ubuntu has.  The networking will work, once you get the wifi working.  There is nothing in the BIOS that should get Ubuntu working with your wifi, you have to do this the ways that have been suggested.

---

### Post by crjackson on 2008-03-04
> **roshm said:**
> I do, and I have the option of trying to boot vista.  I have tried and it doesn't load.  I have tried safemode and it freezes while loading the needed files.  I don't care If I have Vista, but I do need an OS that functions on a network.  I have tried to download and install a wireless assistant and I get the error that my machine is an i386 and the vender chose to not support my laptop.... whatever that means.

Well, your not exactly trying an up to date version.  You should get a LiveCD of version 7.10 and boot to the CD.  You may have the wireless support then.

---

### Post by crjackson on 2008-03-04
> **roshm said:**
> I can't help but feel that the networking section in the bios has been altered during installation. I can use a bios utility but I cannot get to the bios.  Any ideas? oh well back to searching.

The bios utility is your interface to the bios.  That's about as far as you're going to get I think.

You are incorrect in thinking the bios was altered by ubuntu during the install.  It can't do that at all...

---

### Post by roshm on 2008-03-04
Well there bobbob1016......good call.  downloading as I post.  I'll give it a go and see what happens.

---

### Post by kbless7 on 2008-03-05
yeah it works on mine and that command is definitely in existant

---

### Post by Terry of Astoria on 2008-03-05
If there are any data on your Windows partition, you may want to try to recover it. In that event, I suggest you try the program called testdisk. It can be run from the system rescue cd. 
Google it. I was able to recover a completely gone partition which just disappeared on me in windows XP. To run the program, download the system rescue cd, a linux cd, burn it just like the guy suggested to burn the Ubuntu CD above, and then boot it the same way. Many tools are in there. Testdisk is awesome. In fact, a search here at the forums should turn up my post on it from before.

---

### Post by roshm on 2008-03-06
well here I am looking at no network capabilities with a fresh install of 7.10... not a surprise though.  While I was installing the different versions, during a boot a line appeared that said drive blah blah blah has not been checked within the last 30 boots and a diagnostic check was to take place. Then an error shown saying that the firmware could not be found and then something to the effect of broadcom bcm43xx bla bla bla. Sorry I'm not a speed reader yet. Then pci bridge resources could not be allocated.  Gives me something to search for anyway.  Oh well, back to the net and find fwcutter.  any other  ideas or usefull tools would be greatly appreciated since I have made the decision to make this OS function if I can.

---

### Post by Kiri on 2008-03-06
Did your wirless or network hardware come with any special driver disks or fimware disks?

If you know they manufacturer and model information if might help to find the right drivers to look for, since ubuntu might not surrport those particular ones by default.

---

### Post by Terry of Astoria on 2008-03-06
Please keep trying.
I have learned that the key is to not give up.

---

### Post by gigaferz on 2008-03-06
hello!
sorry to interrupt.

So, you have a fresh installation right?
 ok, what im going to advise here is called "ndiswrapper" Is a program to use windows drivers for wireless devices

Click system  then, Administration, then Synaptic package manager.

insert your ubuntu cd
It will ask you for your password
Search for "ndiswrap" 
If found  check  ndiswrapper-commons and ndiswrapper-utils for installation (it should look in your cd for those programs)

You will need to know all waht you can about your wireless device.
Also you need a floppy ,usb stick or cd to use the drivers (well try that later )

 I know there has ben a lot of improvement in wireless networking,but  do not expect it to work out of the box (it could,but is not for sure always try the livecd first then research and then install)


so you know It looks like a master boot sector issue what you have with windows. Or just  some files corrupted in your hard drive, there are some utilities for that ,let us know what happens

---

### Post by roshm on 2008-03-06
well well well Ubuntu World.  Hello.  Here I am for the first time on my Ubuntu System.  I still need to get the wireless working or should I say configured because the wireless is working right now.  I am so pleased that this community is here.  It was a firmware problem that needed to be addressed.  When I am fully connected I will post the links that is credited with solving my firmware problem.

---

### Post by roshm on 2008-03-06
Ok...  here I am posting a reply on a kinda slow wireless connection.  But it is a wireless connection.  I feel kinda silly for all of the worrying I have done, especially when what I did to resolve the problem is almost nothing.  After I identified the problem here is what I did to repair it.   I went to this forum post      "http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom " by DarkNOOb and used the off line installer in section 1.  Then followed the instuctions and wha-la.  The firmware was restored and the networking hardware was on.  Even the little lights that show it is powered up were on.  Then I installed a program called wifi radar and connected to the router. Then to the internet. Now I am pleased.

---

