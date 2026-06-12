---
title: "nOOb here need help please"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Snoopy1966 on 2006-11-06
Hello,
I have been doing some reading and maybe not enough yet, so please forgive me. :confused: I am using the Live CD of Ubuntu and have installed EasyUbuntu.  I have tried downloading the codecs to get media to play. No Luck :(  I have gone into the Software properties and did what the tutorials have said.  
I received this error when installing Amorok
Setting up amarok-xine (1.3.9-0ubuntu4) ...
Setting up amarok (1.3.9-0ubuntu4) ...
find: WARNING: Hard link count is wrong for .: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
find: WARNING: Hard link count is wrong for .: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

Amorok is in Applications, no sound though.  I installed MPlayer no sound also.  I know I am missing something here. Any guidance would be greatly helpful.  I like this forum it seems very nice and the response time is very fast too.  Help me break from the cursed Widows!! :)  I really like whay I see so far with Ubuntu  Thanks in advance.:-D

I also received this error

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

Found out that my sound card is not supported  Sound Blaster X-FI  Anything I can do?  Thanks

---

### Post by ironfistchamp on 2006-11-06
You said you are using the LiveCD. Do you mean that you have not installed Ubuntu on your hard drive. If that is the case I believe that is why you can't install the codecs. 

Hope this was of some help.

Ironfistchamp

---

### Post by mahy on 2006-11-06
If you're sure your soundcard isn't supported, there's nothing you can do, except for waiting and/or writing your own driver :) However, i don't think that's the situation. Try some googling. Maybe you'll find a patch to apply to existing drivers. That's what i did with Intel HDA soundcard back in 2005 when it wasn't supported.

As for the 'find' error, it looks strange. Try installing Ubuntu to your hard drive and install the codecs using Automatix.

---

### Post by Snoopy1966 on 2006-11-06
This place is great!  Thanks for the help.  For now I think a dual boot would be good then, correct until I know I can get sound.  I know this might be a really dumb question but here it goes.  When I am able to do a full install of Ubuntu, will I be able to save any files existing on my computer?  Meaning, will I have the option to save existing files?  Or do I make a back up of my files?  I think if I delete soem stuff from my external hard drive I can fit it all on there.  I recently did a system reset from the Dell software to original factory settings.  I just got this cpu in April and I am really hating Windoze.  It already is taking a long time to boot. ](*,) 
OK I have one final question.  I do have the option of setting up the dual boot when I install from the Live CD? Thanks, it feels nice to be part of a community :cool: Not that will be $100 if you would like some software support today ;)

---

### Post by Bachstelze on 2006-11-06
Whad do you mean "save your existing files", the files you have on your Windows drive ?

---

### Post by Snoopy1966 on 2006-11-06
Yes that is what I mean :oops:

---

### Post by Bachstelze on 2006-11-06
You don't need to save them, just resize your Windows partiton to make room for Linux, Windows won't notice anything ;)

---

### Post by lyceum on 2006-11-06
> **Snoopy1966 said:**
> This place is great!  Thanks for the help.  For now I think a dual boot would be good then, correct until I know I can get sound.  I know this might be a really dumb question but here it goes.  When I am able to do a full install of Ubuntu, will I be able to save any files existing on my computer?  Meaning, will I have the option to save existing files?  Or do I make a back up of my files?  I think if I delete soem stuff from my external hard drive I can fit it all on there.  I recently did a system reset from the Dell software to original factory settings.  I just got this cpu in April and I am really hating Windoze.  It already is taking a long time to boot. ](*,) 
OK I have one final question.  I do have the option of setting up the dual boot when I install from the Live CD? Thanks, it feels nice to be part of a community :cool: Not that will be $100 if you would like some software support today ;)

Yes, you can dual boot, but you will have to create 2 partitions first (from my experiance). I find it is easier, if you want to save data, to get a new hard drive if you want to dual boot. Just use the second hard drive for Ubuntu. When you start up the machine, it will give you the option of Ubuntu or Windows.

When you put a new OS on a PC, you are erracing all data on the harddrive, wiping it clean. IF this is what you want to do, be sure you save all data first.

As for your sound card prob, I have never had any problems with Creative sound cards. They work very well and seem to run great on Linux (Ubuntu). You may want to up grade, or just go to a used place an pay $5 to $10 for an old one. Depending on how much sound means to you. 

Good luck!

---

### Post by Snoopy1966 on 2006-11-06
I found in some thread to a link to find if my sound card was supported.  It is the Sound Blaster X-FI.  It was in Red, no support, to new, drive not rleased or something.  It is a very new card and it rocks for DTS certified surround sound.  My sound means a lot to me.  All I have is net, no TV no Dish, just a couple of free channels from the antenna. I like to watch movies and listen to stuff on my computer. I will do a dual boot install and see if that works.   See you in a little while!
Thanks :-D

---

### Post by Snoopy1966 on 2006-11-06
OK I am trying to install with a dual boot.  I have two 250 GB hard drives that in Windows are connected to show one drive at 500GB.  I have an external 250 GB hard drive too. I am at the step of creating a partition.  I think all three are showing up.  
I have: 
/dev/sda SCSI1 (0,0,0) (sda)-250 GB ATA WDC WD20JS-75N
/dev/sdb SCSI3 (0,0,0) (sdb)-250 GB ATA WDC WD20JS-75N
/dev/sdd SCSI5 (0,0,0) (sdd)-250 GB HDS72252 5VLAT80

Then the manual edit option.

I have around 370GB left on my Drive.  How do I know which one to make the partiton and not wipe out any files?  Scared to go any further right now.  Any advice??  Thanks

---

### Post by argie on 2006-11-06
Well, before you resize any partitions you should run all the defrag tools on Windows.

---

### Post by Snoopy1966 on 2006-11-06
OK, cancel install for now and go back to Windoze and defrag.  What then?
Thanks

---

### Post by lyceum on 2006-11-06
> **Snoopy1966 said:**
> OK, cancel install for now and go back to Windoze and defrag.  What then?
Thanks

When you get to the partision options, don't use the one windows is on. I would also disconect the external for now. You wouldn't use that one either. that should give you 2 choises, Window's partition & the empty space. I normally make sure they are not the same amount, that way it is easier to see which one is the one  want to use, or I leave the Ubuntu space unpartioned all together.

As for the sound card, you can have more than one in your PC, if you have room. You can put a cheep one in until your new card is supported.

Cheers! :)

---

### Post by Snoopy1966 on 2006-11-06
OK thanks for the help.  I am sorry, I feel really dumb asking all these questions.  How do I know what part Windows is on?  Do I use the manual option and create a space?  I am guessing it might be on the sdb part?  Sorry for the dumb Windows guy here.  :oops: 
Thanks again

---

### Post by ironfistchamp on 2006-11-06
Don't apologize for not knowing about Linux we all have to start somewhere. I remember when I was asking similar questions :p

---

### Post by ebozzz on 2006-11-06
> **Snoopy1966 said:**
> OK thanks for the help.  I am sorry, I feel really dumb asking all these questions.  How do I know what part Windows is on?  Do I use the manual option and create a space?  I am guessing it might be on the sdb part?  Sorry for the dumb Windows guy here.  :oops: 
Thanks again

I'm pretty new to Linux & Ubuntu as well. I have completed 4 installs and with the exception of one, all of them are set up to dual boot with an existing XP OS. The exception was a complete clean install (new hard drive) and I partitioned the drive while  installing XP. After I finished with the Windows install I just had Ubuntu to use the remainder of the continuous free space.  

On the drives where there were no partitions, I simply allowed Ubuntu to resize my drives (50% for XP & 50% for Ubuntu). It detected how much space was being used by XP. It is suggested that you back up all data if your are going to do this. I didn't but I didn't have anything critical that I was concerned about.  I also have all of my software just in case I needed to reinstall. 

Once the drives were resized the install went very smoothly.  When I booted XP for the first time after completion, it noticed the changes made to the drive and ran a check consistency to make sure all was well. Now, I'm not saying this is the best way to go about accomplishing your task. I'm just saying that this method worked for me and my lack of knowledge. :) As my knowledge grows so will my abilities. Future installs will probably have  more partitions.

---

### Post by lyceum on 2006-11-06
> **Snoopy1966 said:**
> OK thanks for the help.  I am sorry, I feel really dumb asking all these questions.  How do I know what part Windows is on?  Do I use the manual option and create a space?  I am guessing it might be on the sdb part?  Sorry for the dumb Windows guy here.  :oops: 
Thanks again

For me, this is why I make differant sizes or leave the space I need unpartitioned. If they both say "100 gigs" or what ever, they look the same to me. I've only tried creating space once, and it did not work. Just make sure everything is backed up first. I will say that if you tell it to find/use empty space, that is what it will do. Windows will not be on the empty space. 

I don't know that I am saying any more than the last poster, but I hope this helps. Keep asking questions as needed, I just hope everything works out for you.

Good luck!

---

### Post by ebozzz on 2006-11-06
> **lyceum said:**
> Keep asking questions as needed.

Ain't that the truth! :) 

One more thing. I didn't which Windows OS you are using. If it's XP and you formatted it using NTFS, Ubuntu will identify NTFS where it is being used. That will give you some indicator about how to figure out where Windows is. If it's an older Os that uses FAT32, you will see that after the drive has been scanned.

---

### Post by Snoopy1966 on 2006-11-06
Hello,
OK I thought I had it all.  I made the partition of 100GB, but I think I messed up in the swap.  I put 300 instead of 3000.  The partition I made was 1000,000, meaning 100 GB, correct? I made the swap inside that first partition, but I made it 300 like I said.  I  thought about this when it was installing, but it was too late.  I have most of my stuff on DVD's from my last format of Windows.  There was some stuff I did not back up since then.  No big deal I can get most of it back.
  When I restarted my cpu, It started loading Grub and I received Error 25, whatever that is.  I have another computer that I am posting from now.  I should have used this one instead of my new one.  What is error 25 and what do I do now?  :confused: 
Thanks for your help :)

Yes I have Windows XP and I found that the sdb section had no partition on it.

---

### Post by ebozzz on 2006-11-06
Sorry to hear about your difficulties. I've never heard of the Error 25 message but they may be some answer about it that you can find on the board. I guess that's why I let Ubuntu sort of determine how it was best for me to proceed. I was going to try to complete the partitions manually but decided against it. I just wasn't sure that I totally understood what I was doing by using that method. So, I chose the easy routes for my installs and I will continue to do so until such time as I am confident that I have a clear understanding of the process. I'm not that far away but I still have some  learning to do. Hopefully someone will chime in with a solution.

---

### Post by Snoopy1966 on 2006-11-06
Is there anyway I can boot into windows now?  I can not do the F8, it will not let me into the boot menu now.  Or did I just trash my system?

---

### Post by lyceum on 2006-11-06
I have seen the Error 25, but do not know what it means. If you lost your data and are starting over from scratch, do you have an XP disk? If you do try this:

Install Windows, formating your hard drive into 2 partitions. Depending on which you will use more, make one 100 gigs, the other 200. Use the OS you will use the mst on the larger partition. I use Ubuntu more so I would do this:

100 g Windows

leave 200 unpartitioned

Once Windows is done, put the Ubuntu disk in. When it gets to the different paritions, you know that the 100 g is Windows. Choose the 200 g for Ubuntu. This will leave Windows untouched. 

IF you will use Windows more, do the same, but:

200 g Windows

leave 100 g unpartitioned.

This is how I normally do it. As for finding data curently on your PC that you do not want to lose, if your Windows in in FAT32 space (a type of partition) you should be able to get to your info from the Ubuntu live disk. If Ubuntu runs to slow, try a smaller live Cd ,like Nimble X

[http://nimblex.net/](http://nimblex.net/) 

or fluxbuntu 

[http://fluxbuntu.com/](http://fluxbuntu.com/)

Again, these will only work for finding any lost windows data if you have Windows in FAT32 partition, you can chack in fdisk (dos command) but I recomend you do not do that. 

If you have a standard disk for re-doing your PC (starting EVERYTHING over), you may not be able to do any of this. Also, you will mostlikly not be using FAT32 partitioned space.

I hope this is not too confusing and actually helps. You can also start looking for Error 25, which I am going to do right now.

Again, good luck.

---

### Post by dca on 2006-11-06
Did you unplug the USB HDD during install or anything?  The only other thing is check all the cables on the HDD(s) and CD drives....  Although, Error 25 is grub-related... Hmmm....  Might as well start from scratch as the above post mentioned...  Or just go all-out Ubuntu and if you don't like it, you still have the XP OS install CD, right?

---

### Post by Snoopy1966 on 2006-11-06
Thanks for the quick response.  This place is great and I will not let my failure defeat me!  I have the XP CD and everything is in NTFS 
I can not get to the boot menu though.  I hope I can I will try some more.  
I looked for Error 25, but I did not find anything as of yet.  I am very busy trying to maintain a web site I mod at, and all this too.   I hope I get this sorted out soon.

I unplugged my external hard drive before the install.  I left my printer plugged in though.  Could that have been a problem?  Nothing was messed with during the install.  I was hooked up to the net to with my broadband.  Off to play some more!

---

### Post by lyceum on 2006-11-06
> **Snoopy1966 said:**
> Thanks for the quick response.  This place is great and I will not let my failure defeat me!  I have the XP CD and everything is in NTFS 
I can not get to the boot menu though.  I hope I can I will try some more.  
I looked for Error 25, but I did not find anything as of yet.  I am very busy trying to maintain a web site I mod at, and all this too.   I hope I get this sorted out soon.

I unplugged my external hard drive before the install.  I left my printer plugged in though.  Could that have been a problem?  Nothing was messed with during the install.  I was hooked up to the net to with my broadband.  Off to play some more!

I just checked for error 25, all I could find was that it was a grub error, as you already know. Sorry, it looks like you will have to start over. Just make sure your new XP is set up in FAT32 so you can share files between Ubuntu & Windows. That will make your life easier anyway.

---

### Post by ebozzz on 2006-11-06
> **Snoopy1966 said:**
> Thanks for the quick response.  This place is great and I will not let my failure defeat me!  I have the XP CD and everything is in NTFS 
I can not get to the boot menu though.  I hope I can I will try some more.  
I looked for Error 25, but I did not find anything as of yet.  I am very busy trying to maintain a web site I mod at, and all this too.   I hope I get this sorted out soon.

I unplugged my external hard drive before the install.  I left my printer plugged in though.  Could that have been a problem?  Nothing was messed with during the install.  I was hooked up to the net to with my broadband.  Off to play some more!

Are you settings still configured for a boot from the CD-ROM drive first? If so, couldn't you just boot from the XP disc to attempt to repair/install XP?

---

### Post by ebozzz on 2006-11-06
> **lyceum said:**
> Just make sure your new XP is set up in FAT32 so you can share files between Ubuntu & Windows. That will make your life easier anyway.

What type of files can be shared by doing that? Tell me more, please!

---

### Post by Snoopy1966 on 2006-11-06
> Are you settings still configured for a boot from the CD-ROM drive first? If so, couldn't you just boot from the XP disc to attempt to repair/install XP?
Reply With Quote

I did not configure my computer to boot from CD.  I used the boot menu F12.  I am able to get Windows CD to start now.  I will try a repair install, if i try to save stuff, will I still have Ubuntu on there too?

---

### Post by Snoopy1966 on 2006-11-06
I could not do a repair install.  It said the structure was badly damaged.  I could not get the option to format to FAT32.  My external hard drive is NTFS anyway and I do not know how I could back up 190GB.  I am installing Windows again now, it is still formatting.  I am a little gun shy now.  Maybe I am not ready for this.  I should have maybe went out and got a different sound card until the X-FI is supported and just dove into Linux Ubuntu.  Can I bail from the set up windows and install Linux?  Everything is lost anyway.

---

### Post by Sef on 2006-11-06
First **back up** your files.

Next, read [Psychocats Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing").

---

### Post by Hrugaar on 2006-11-06
ebozz - if you use FAT32 both linux and windows can see it and write to it, in theory the same should go for NTFS but in my experience linux seems to mess it up a little. On my desktop machine i use NTFS for my windows partition, ext3 for my linux partition, and FAT32 for 3 other partitions for music, files, etc...

hope this helps

Ru

---

### Post by gn2 on 2006-11-06
Your soundcard will not work in Linux until someone writes a driver, which might prove tricky because the Windows driver for this card relies on having Quicktime installed.

As for multi-disk dual booting, this may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by ebozzz on 2006-11-06
> **Hrugaar said:**
> ebozz - if you use FAT32 both linux and windows can see it and write to it, in theory the same should go for NTFS but in my experience linux seems to mess it up a little. On my desktop machine i use NTFS for my windows partition, ext3 for my linux partition, and FAT32 for 3 other partitions for music, files, etc...

hope this helps

Ru

Thank you Sir! It helps a great deal.

---

### Post by Snoopy1966 on 2006-11-06
Thanks for your help.  I think I will try a full install on my other computer.  I will check to see if all the video and sound cards are supported.  That one has surround sound too, but I think it is supported.  I can not remember the name of the sound card.  Question though.  Will I be able set up a wireless connection to it.  That is how I have it now.  My main computer that I have going again, thank God, with a wireless router and my other computer has the wireless card.  It is a Linksys WRT54G v.5 router.
Snoopy

---

### Post by lyceum on 2006-11-07
> **Snoopy1966 said:**
> Thanks for your help.  I think I will try a full install on my other computer.  I will check to see if all the video and sound cards are supported.  That one has surround sound too, but I think it is supported.  I can not remember the name of the sound card.  Question though.  Will I be able set up a wireless connection to it.  That is how I have it now.  My main computer that I have going again, thank God, with a wireless router and my other computer has the wireless card.  It is a Linksys WRT54G v.5 router.
Snoopy

Wireless is a hit and miss with Linux. First check the list of supported hardware. The FSF site states that Linksys, WMP54G v4 *, WUSB54G v4 *, WUSB54GP v4 * should work with Linux. If it does not work with the start up disk, it will not work without special help. You may want to check the networking or laptop sections of the forum before doing anything. 

As for the FAT32 set up, Linux can only be installed on FAT32, which makes it possible to share files with another OS in the same file type. If you have an external hard drive, and it is not FAT32, you will be able to SEE the files, but may not be able to use them. In some cases you may not even see them. I don't know why. I am just speaking from experience. If you are choosing between a laptop and  a desk top, which to install, I would go with the desk top, as there will be less hardware issues. I had to dual boot my laptop to use my wireless, as the card was not supported. 

Don't give up! you are almost there.

---

### Post by Snoopy1966 on 2006-11-08
Hello again,
Ok I have been doing some searching around and it looks like everything is supported on my other computer.  There is a driver my Creative Audigy sound card.  I also saw that they are trying to get a driver for my X-FI and they said it will be out in 2007 sometime.  This is cool so I can play around with Ubuntu on my other system until then.  The only other questions that I have right now are these

I think I will still try a dual boot on my system.  Lyceum has said that Linux needs to be on FAT32.  When I let Ubuntu make the partition this time will it make it FAT32?  Any suggestions?

Next question.  The only thing I did not see supported was my wireless router Linksys WRTG54G.  I found this thread [http://www.ubuntuforums.org/showthread.php?t=123371&highlight=WRTG54G]("http://www.ubuntuforums.org/showthread.php?t=123371&highlight=WRTG54G") on it.  Can some explain to me the steps in order to get the wireless to work?  It is in the last post and probably some info along in the same thread.

I hope I can try to get something going now.  Thanks for all your help,  this place is great. :cool: 
Snoopy

---

### Post by Snoopy1966 on 2006-11-08
I was using the Live CD again and I got sound :)  Not the greatest, but I think that can be improved if I get online and get some other stuff configured.  

Can someone help me with the wireless?  I set up many different things in the Admin Network settings. Putting in DNS Servers, IP, default gateway, WEP Key, tried static IP.  Is there something to run from the Terminal to enable or disable something to get this to work?  It detected the wireless, but I can not get on the net.  I know I am missing something.  Any ideas?

---

### Post by lyceum on 2006-11-08
To answer your question, yes, Ubuntu will format in FAT32. That is great that your sound card works. Life is always better with music :-D

As for the wireless, what kind of card is it? If it is broadcome, go here:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

If not, post whatkind it is. I'll check back later and see if I can do anything to help. If it is broadcom, it may never work right. You might need to get an external card. Sorry. 
Also, you may want to check out the networking forum.

---

### Post by Snoopy1966 on 2006-11-08
Thanks for the reply
I have a Linksys Wireless-G PCI Adapter.  I have been searching all over for help in this matter and I can not find anything.  Ubuntu recognizes my network but I can not get on the net.  I am still using the live CD on my second system.  It froze up on me once trying to configure some settings in Networking.  Now it just froze up from the screen saver.  I did not play around with the graphics card yet.  I did the ifconfig -a and I got 6 losses and 14 collisions.  I wish I wrote it all down.  I can not copy and paste the results.  Waiting eagerly :)

EDIT I forgot to mention every time I load the CD the PCMCIA never gets an OK when loading.  Not sure what it is, just though I would mention it.

---

### Post by lyceum on 2006-11-08
> **Snoopy1966 said:**
> Thanks for the reply
I have a Linksys Wireless-G PCI Adapter.  I have been searching all over for help in this matter and I can not find anything.  Ubuntu recognizes my network but I can not get on the net.  I am still using the live CD on my second system.  It froze up on me once trying to configure some settings in Networking.  Now it just froze up from the screen saver.  I did not play around with the graphics card yet.  I did the ifconfig -a and I got 6 losses and 14 collisions.  I wish I wrote it all down.  I can not copy and paste the results.  Waiting eagerly :)

The Linksys shouldn't be the problem. It is just a router. Do you know what the card inside your PC is? You may have to open up your lap top to find out. Also, you may not be able to fix it until you have Ubuntu on the PC, rather than using a live CD. I am at school right now so I don't have access to any of my books for quick reference, but there are some tests you can do to 'ping' the net to get more info on what is wrong. I did a quick check at the Networking & Wireless page, but found nothing. Again, their may be something there, but I didn't have a lot of time to check. I will keep looking as I can. In the mean time, see if you can find out what kind of card you have inside the laptop. It will be easier for me to trouble shoot if I know what you are working with. There is also a program you can install you give you more control over your network, called netware manager. It is a Gnome add on. If you follow the link I posted earlier, there are details on how to load it. Start with #5 on the list of things to do. 

Good luck!

---

### Post by Blutack on 2006-11-08
Hope this makes you feel better - your sound card will be supported soon(ish)...
[http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi](http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi)

---

### Post by Snoopy1966 on 2006-11-08
> **lyceum said:**
> The Linksys shouldn't be the problem. It is just a router. Do you know what the card inside your PC is? You may have to open up your lap top to find out. Also, you may not be able to fix it until you have Ubuntu on the PC, rather than using a live CD. I am at school right now so I don't have access to any of my books for quick reference, but there are some tests you can do to 'ping' the net to get more info on what is wrong. I did a quick check at the Networking & Wireless page, but found nothing. Again, their may be something there, but I didn't have a lot of time to check. I will keep looking as I can. In the mean time, see if you can find out what kind of card you have inside the laptop. It will be easier for me to trouble shoot if I know what you are working with. There is also a program you can install you give you more control over your network, called netware manager. It is a Gnome add on. If you follow the link I posted earlier, there are details on how to load it. Start with #5 on the list of things to do. 

Good luck!

OK a little confusion here but that is my fault.  Good news first of all from Blutack on the release I hope for the X-FI sound card.

I am not going to install Ubuntu on the computer I was talking about first off with the X-FI card until it is supported. Now I am trying to get my other Desktop working with Ubuntu.  It seems everything is supported, just having troubles getting on the net.  I think I will install a dual boot on it yet tonight. 

This cpu has SB Audigy sound card and ATI graphics card that was recognized by the system devices.  I am sorry for any confusion, this is the cpu I have been trying to get on the net for the past few posts here.  I should have started a new thread, but I thought it would be good to stay in this one with some 'history' :)

OK now I have a Linksys WRT54G Router on my main cpu that I trashed this week, that sends the signal to my other Desktop with the Linksys Wireless-G PCI Adapter.  I went into Networking enabled the wireless, selected DCHP, put in my WEP key and then activated it.  Then I went to Networking Tools > Devices tab, and from the drop down menu the Unknown Interface(ra0)connection was there and I saw transmitted packages and received packages.  The numbers kept on going.  That is a good thing.  But how in the world do I connect to it? :confused: 
In the Network Tools under Devices in the Interface info all the categories were n/a :( 
I saw Protocol IPv6 somewhere too.  Sorry for the mess I hope this makes some sense.  

I will have to try out the netware manager thing in a little while.  I have some things to do and I will be back home later.  
OK thanks for the help. :-D

Edit  Is there a way I can download stuff in Windows and have it to install in Ubuntu when I am using it?  I can not get on the net so I can not do some of the stuff from your link.  Also when I set up the dual boot, how do you switch from Ubuntu to Windows?

---

### Post by lyceum on 2006-11-08
Okay, to get everything striate, you have 2 PC's, the main PC, with Windows that got messed up, and the now Ubuntu machine, I was under the impression that it was a laptop, but that's okay (my bad). It doesn't matter if it is a laptop or desktop, except that a desk top is easier to open and replace parts. Anyhow, since you have Ubuntu on the 2nd PC, lets call it the Ubuntu machine (UM), or just forget the main PC for now until you get access to the net on the UM. 

If you cannot get the card to configure, it will not connect to the net, even if Ubuntu can see it. If Ubuntu can see the wireless card, but it will not work, then it most likely requires proprietary (closed source) drivers. If this is the case, there are answers to fixing the problem, but it means you would need the drivers. To get the drivers, you need to know what kind of card you have in the machine. To be honest, if you can network without wireless, that would be your best option. 

For now, see if you can configure, you will need the same info you needed to configure Windows to the network. I went to Linksys' site, and they only offer Windows support.

---

### Post by lyceum on 2006-11-08
Okay, to get everything striate, you have 2 PC's, the main PC, with Windows that got messed up, and the now Ubuntu machine, I was under the impression that it was a laptop, but that's okay (my bad). It doesn't matter if it is a laptop or desktop, except that a desk top is easier to open and replace parts. Anyhow, since you have Ubuntu on the 2nd PC, lets call it the Ubuntu machine (UM), or just forget the main PC for now until you get access to the net on the UM. 

If you cannot get the card to configure, it will not connect to the net, even if Ubuntu can see it. If Ubuntu can see the wireless card, but it will not work, then it most likely requires proprietary (closed source) drivers. If this is the case, there are answers to fixing the problem, but it means you would need the drivers. To get the drivers, you need to know what kind of card you have in the machine. To be honest, if you can network without wireless, that would be your best option. 

For now, see if you can configure, you will need the same info you needed to configure Windows to the network. I went to Linksys' site, and they only offer Windows support. Your post is a bit confusing, sounds like it should be working, so you may just not be configured. Once the network manager is up and you make sure you are configured, you should know more about what is going on.

---

### Post by Snoopy1966 on 2006-11-08
Well I have Ubuntu installed everything was going OK, but I still could not access the net on the UM.  I could see the packet transfer again, but no luck in hooking up to the net.

I did the step you said about installing the network manager and it said the file was not found :(  

Then I did this from a thread I read earlier it said something about running this from the Terminal 

sudo /etc/init.d/networking restart

I did that and the UM froze up on me.

Now I can not boot up Ubuntu.  It stops at Configuring Network Interfaces. I tried recovery mode and no luck there either.  Now what should I do? :confused:

---

### Post by Snoopy1966 on 2006-11-09
OK I found something that said to pres Ctrl then C and it will load.  I enter my user name, then password and now I have the brown screen of death.  Is that the equivalent to windows blue screen of death?  I am able to boot to windows still.  what now?  Install Ubuntu again?  When I downloaded the CD file, I checked it with hash tab and it matched.  ](*,)

Anyone out there to please help me?

---

### Post by lyceum on 2006-11-09
At this point you are beyond my area of expertize, sorry. If your network manager says you are configured, there is no reason you should not see your router. I hate to say this, but you may need to start a new post in the wireless forum. The people there would be more able to help. I would just cut and paste all the use full info on your problem. Again, if you can go wired, I have found that works better. 

Linksys doesn't seem to support Linux, so you may not be able to get your wireless to work without using some other tools  like ndiswrapper. I don't know enough about that program yet not to screw up your PC. The good news is that wireless is one of the top priorities for the next release, due out next year. You also may want to try Edgy, 6.10, to see if that makes a difference. It did for me. Again, sorry I could not be of more help.

---

