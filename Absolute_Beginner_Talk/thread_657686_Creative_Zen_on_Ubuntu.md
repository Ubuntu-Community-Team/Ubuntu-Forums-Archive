---
title: "Creative Zen on Ubuntu"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by alexjohnc3 on 2008-01-03
I just got a [Creative Zen](http://us.creative.com/products/product.asp?category=213&subcategory=214&product=16999) and I wanted to know how to get it working in Ubuntu. I've done some searches and installed Gnomad2, but I get the error "No jukeboxes found on USB bus" when I start the application.

This is what I get when typing lsusb in the terminal:
Bus 002 Device 005: ID 041e:4157 Creative Technology, Ltd 
Bus 002 Device 002: ID 0586:340f ZyXEL Communications Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:3012 Dell Computer Corp. 
Bus 001 Device 002: ID 045e:00b4 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by dstew on 2008-01-04
Does the player show up as a disk? You could probably mount it like any other disk, then put files into it. Try```
sudo mount /dev/sda1 /mnt
```This assumes the USB player is detected as /dev/sda1. If you have another USB disk, it might be /dev/sda2, or even /dev/sdb1.

---

### Post by PinkFloyd102489 on 2008-01-04
It would be sdb if you have another. The number in /dev refers to the partition on that device. So /dev/sda5 would refer to the 5th partition on device sda. A second device would show up as sdb and so forth.

---

### Post by txHarleyMan on 2008-01-04
> **alexjohnc3 said:**
> I just got a [Creative Zen](http://us.creative.com/products/product.asp?category=213&subcategory=214&product=16999) and I wanted to know how to get it working in Ubuntu. I've done some searches and installed Gnomad2, but I get the error "No jukeboxes found on USB bus" when I start the application.

This is what I get when typing lsusb in the terminal:
Bus 002 Device 005: ID 041e:4157 Creative Technology, Ltd 
Bus 002 Device 002: ID 0586:340f ZyXEL Communications Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:3012 Dell Computer Corp. 
Bus 001 Device 002: ID 045e:00b4 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000

I had to install mine as an MTP device in Amarok, that is.

---

### Post by eheyl on 2008-01-05
Hey all just got a creative zen 4gb and have been trying to get it to be found in gutsy. I hit sudo mtp-detect and on the zen it said docked but nothing else found it. I disconnected and now nothing is coming up on the Zen, no screen, and I can't seem to turn it off. Whats happening? 

EDIT: Just hit reset and everything is fine. I really need some help on this. I've read through some threads here but the cvs stuff is over my head. And I've downloaded libmtp0.2.4 but don't know how to install it. Any help would be appreciate. Just when I thought I was getting smart on this, it kills me......

---

### Post by eheyl on 2008-01-05
All I really want to do is burn some files that I've got on bought cds to mp3 and put them on, I also want to burn some bought dvd movies on as well. What are some good programs for that? Its times like this that I wonder if switching was best for me. But then I remember all the stuff I don't have to do (virus removal, spyware removal, contstant patching). So I'm just a bit frustrated.

---

### Post by alexjohnc3 on 2008-01-06
I'm kind of in the same boat as eheyl. I don't really know too much about Ubuntu or Linux.

dstew: How do I verify if it's showing up as a disk? There is nothing in the computer folder related to my Zen, if that's how I would, which I doubt.
Also, there's nothing in the dev folder that appears to be related to my Zen either.

txHarleyMan: The instructions on how to do this ([http://amarok.kde.org/wiki/Media_Device:MTP](http://amarok.kde.org/wiki/Media_Device:MTP)) are really confusing.

Also, using [this tutorial](http://pclosmag.com/html/Issues/200708/page09.html) (although I have libmtp6) gave me an error message in Amarok that said, "Could not connect to MTP Device."

---

### Post by eheyl on 2008-01-06
My question is how do I install the most recent libmtp? I downloaded 0.2.4 as a tarball and am not sure how. I feel I'm very close to gettign this solved, just need a bit more help. I will try the solution with amarok.

---

### Post by indytim on 2008-01-06
> 
All I really want to do is burn some files that I've got on bought cds to mp3 and put them on, I also want to burn some bought dvd movies on as well. What are some good programs for that? Its times like this that I wonder if switching was best for me. But then I remember all the stuff I don't have to do (virus removal, spyware removal, contstant patching). So I'm just a bit frustrated.


SoundJuicer works well for converting from CDA -> mp3. Can't comment on the dvd ripping as it's illegal here in the States.

IndyTim

---

### Post by eheyl on 2008-01-06
I'm not selling or redistributing the dvd in anyway, I simply want to take it with me on long trips in my zen.

---

### Post by indytim on 2008-01-06
Sorry mate.  If you live in the U.S. it is illegal to make copies of even the DVDs you own.  Complain to the numb nuts in Washington :).

There are Linux apps out there to do what you want.


IndyTim

---

### Post by eheyl on 2008-01-06
Then I'm very happy I don't live in the US at this time. I'm in Canada. Between the damn DMC and the constant fighting over video games its a wonder people don't riot more. :)

---

### Post by Omnios on 2008-01-06
Try launching it with sudo
 
 I modified my menu with gksudo in front of the aunch command in the menu.

---

### Post by eheyl on 2008-01-06
Ominos, could you expand a bit on your tip? I know about sudo and have used it but not sure how to with what little you've said. And what is aunch? I'm still fairly green at the subtlties of the command line, but getting better. Give it to me step by step and I'll see what I can do. Thanks mate!

Erik

---

### Post by eheyl on 2008-01-06
So I compiled libmtp-0.2.4 from source. it looked like everything worked, how can I check? So now tnomad still comes with the same error can't find anything. I'm stumped and still not sure what Ominos meant and would like clarification. Slowly but surely with help I'll get this.

---

### Post by dstew on 2008-01-06
> dstew: How do I verify if it's showing up as a disk?Did you do the mount command as I recommended? If so, did you get an error message? If not, you should find the disk in the /mnt directory. Did you look there?
To make sure your computer sees the player as a disk, plug it in and issue the command```
sudo fdisk -l
```It should be listed in the output of this command. Post the results to the forum if you don't understand the output.

---

### Post by Omnios on 2008-01-06
> **eheyl said:**
> Ominos, could you expand a bit on your tip? I know about sudo and have used it but not sure how to with what little you've said. And what is aunch? I'm still fairly green at the subtlties of the command line, but getting better. Give it to me step by step and I'll see what I can do. Thanks mate!

Erik

 K in the menu under /System /Preferences

 choose /Main Menu

 "In main menu app"

you can add sudo.


 "K now thinking about this I have the same problem that was solved bu plugging in the zen to the usb. Then I turned the zen on. when it boots up then try launching the gnomead2 program."

---

### Post by eheyl on 2008-01-06
I tried that and  I still get the no jukebox found message. and I'm still not sure what you mean about adding sudo. I went and did it, but now what? Sorry guys, I must be missing something.

---

### Post by eheyl on 2008-01-06
drstew I tried the command on the first page, nothing seemed to happen, so I used sudo fdisk -l and all it listed was the hard disk partitions no zen at all not even as a hdd.

---

### Post by dstew on 2008-01-06
Can you detect any USB devices at all? Like a thumbdrive, or external hard drive?

---

### Post by hobo on 2008-01-07
On my 7.10 image, using Amarok, my Zen works well after setup. It is a MTP device not USB. To rip K3b works great.
On my 6.06 image Amarok has no idea what a MTP device is.

---

### Post by dstew on 2008-01-07
Is the mpt-tools package installed? If not, you can get it from Synaptic (universe repository). This is more reliable that installing from source.

---

### Post by alexjohnc3 on 2008-01-08
> **dstew said:**
> Is the mpt-tools package installed? If not, you can get it from Synaptic (universe repository). This is more reliable that installing from source.
MTP, not MPT. :P


I get the same results as eheyl when I type sudo fdisk -l. When I type lsusb Ubuntu does seem to see that my Zen is attached to the PC though. Edit: Also, nothing in the mnt directory.

---

### Post by alexjohnc3 on 2008-01-08
Using sudp mtp-detect, it sort of detects my Zen. It says that my Zen is docked when I run it.

I think [these instructions](http://ubuntuforums.org/showthread.php?t=643512&highlight=libmtp) might work, but they didn't work for me. Any advice?

Edit: This is what sudo mtp-detect returns:
libmtp version: 0.2.1

Attempting to connect device(s)
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after resetting USB
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting


Running sudo gnomad2 gives me this:
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after resetting USB
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
LIBMTP_Get_First_Device: Error Connecting
PDE device NULL.

---

### Post by macogw on 2008-01-08
> **eheyl said:**
>  it said docked but nothing else found it. I disconnected and now nothing is coming up on the Zen, no screen, and I can't seem to turn it off. Whats happening? 

EDIT: Just hit reset and everything is fine.
Zens seem to have a tendency to freeze.  My Zen Vision M did it a few times...keep paper clips on hand for that player.

---

### Post by eheyl on 2008-01-11
So its still not finding it, and every other usb device (my wifes ipod for instance, what a kick in the teeth) gets found and connected. So for now, I've dual booted with xp and have it working that way. Its funny I started with ubuntu and now my wife says are you done with windows yet, boot it back to linux. She HATES windows now with the fire of 1000 suns.

---

### Post by eheyl on 2008-01-11
I've got mtp-tools installed what now? :)

---

### Post by dstew on 2008-01-11
Plug in your player. Try the command **mtp-files**. This should show you what is on your player. The command **mtp-folders** should list the folders in your player. To put a track into the player, use the command **mtp-sendtr**.

---

### Post by alexjohnc3 on 2008-01-13
No offense eheyl, but you kind of hijacked my thread. Your problem is a bit different than mine, so it's confusing to read responses that have nothing to do with my situation.

---

### Post by dstew on 2008-01-13
alexjohnc3:

> Device 1 (VID=041e and PID=4157) is UNKNOWN.My Zen has PID=4150, and it is listed as known, and works. Is it possible that your libmtp does not recognize your Zen? That is, the libmtp maintainers have not been able to add that device to their library.  I have libmtp5  version 0.1.0-0ubuntu2 installed on a Feisty 7.04 system.

---

### Post by alexjohnc3 on 2008-01-13
> **dstew said:**
> alexjohnc3:

My Zen has PID=4150, and it is listed as known, and works. Is it possible that your libmtp does not recognize your Zen? That is, the libmtp maintainers have not been able to add that device to their library.  I have libmtp5  version 0.1.0-0ubuntu2 installed on a Feisty 7.04 system.
I have libmtp6, version 0.2.1-0ubuntu3 and I've tried reinstalling it from the Synaptic Package Manager. Is your Zen the same as [mine](http://us.creative.com/products/product.asp?category=213&subcategory=214&product=16999)? Also, I'm using Ubuntu 7.10. I have the 7.04 LiveCD, so should I load that up and see if it works?

---

### Post by dstew on 2008-01-13
No, mine is an older model Zen V. You could try the LiveCD. If mtp-tools is not installed, you can use Synaptic to install it to your LiveCD system (it will disappear after shutdown, of course). That would be an interesting experiment.

---

### Post by jaktar on 2008-01-14
I was about to start working on this myself when I stumbled upon your post.  I have both a Zen Microphoto and a Zen Vision M.  There's a guide here ([http://ubuntuforums.org/showthread.php?t=662567](http://ubuntuforums.org/showthread.php?t=662567)) that may work for you.  I'm running through it now.:popcorn:

---

### Post by Rubunter on 2008-01-23
Hi there. I'll tell you what i did to get my zen working with amarok. First of all you have to update the firmware of your Zen to the last version (you need windows to do so). After doing that, you also need to install the last version of libmtp, which is libmtp.0.2.4. Then open amarok as a root (sudo amarok) and go to amarok settings/Devices and add your Zen as a MTP device. That done, go to the main screen of amarok again and to the devices tab, click connect and it will detect your zen and show all the music files you have inside. 
I did all these steps and it worked for me. However, 3 days later, I tried to sync again and I couldn't because my zen got hanged. Anyway it should work for you. 
Bye!

---

### Post by eheyl on 2008-02-12
Hoo YA! Got it working. Now just have to start collecting music. Wonder if I can get audible to work?

---

### Post by henter2007 on 2008-04-08
can somebody explain me why I have to run gnomad2 as root to get my device recognized?

:confused:

---

### Post by dburnett77 on 2008-04-20
I'm just popping through the forums.  I have a Creative Zen 4GB, and couldn't get it to work; until I loaded Ubuntu 8.04 Hardy Heron beta.
It shows in Gnomad2, Rhythm Box, and Banshee.  And, works flawlessly.  So, wait 4 days to upgrade, or try the beta.  Worked for me.

---

### Post by alexjohnc3 on 2008-04-27
> **Rubunter said:**
> However, 3 days later, I tried to sync again and I couldn't because my zen got hanged. Anyway it should work for you. 
Bye!
Did the act of syncing your Zen cause it to hang? o_____o

---

### Post by Extraneous on 2008-04-28
Apologies for hi-jacking the thread but I'm having similar problems.

I have the latest mtp-tools and libmtp installed.

lsusb lists the device.

If I run Gnomad it seems to sync with my Zen, but after it scans the datafiles Gnomad freezes (goes all grey) and I have to kill it (no harm done to the Zen though) or unplug the Zen.

Amarok will not detect it. 

Trying to /mount it (/sudo mount /dev/bus/usb/008 /mnt) returns 'not a block device'.

Halp?

Edit: Got a step further by looking properly in the Amorak settings. Now it'll fine the Zen and try to sync with it but, like Gnomad, it freezes up when it finishes.

---

### Post by biasedopiniondrummer on 2008-04-30
I recently installed ubuntu on a friends laptop and we are having issues connecting his zen. it can be seen in  banshee and amarok but I cannot transfer files to or from. it will not play music from the zen on the computer. in gnomad2 i tell it to transfer a song. It looks like it does but the when i check the zen there is no music. any thoughts?

thanks

Clay

---

