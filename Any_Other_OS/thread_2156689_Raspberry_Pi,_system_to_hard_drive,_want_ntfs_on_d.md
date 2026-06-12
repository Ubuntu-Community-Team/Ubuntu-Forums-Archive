---
title: "Raspberry Pi, system to hard drive, want ntfs on drive also"
date: 2013-06-22
forum: Any Other OS
---

### Post by squakie on 2013-06-22
I have a Raspberry Pi I am setting up for use as a media center using XBMC.  I am currently (and for the foreseeable future ;) ) loading my disks on to my PC's hard drive.  When it comes time to set up the hard disk for the Pi, I'd like to put everything but the essential boot files on the hard disk.  I found [this]("http://forum.stmlabs.com/showthread.php?tid=481") thread that shows how to do that.  I al wold like a ntfs partition on that same disk to actually store the movies (so I don't have to copy everything if the disk [external] gets moved for use on another box).

From reading that thread, I'm getting a little lost.  Does anyone see any reason why I can't use gparted on my PC to create the partitions first and load those somehow from my PC?  I know that warning about losing data is because the disk is being repartitioned - and since it's a raw drive that doesn't apply.  I'm just a little confused on the rest - perhaps because I'm such a novice on the Pi (it is running Raspbian - derived from Debian) even though I do mostly fine with Ubuntu.  Maybe I just need to read through those instructions many times to get the idea of what they are really doing (create partitions for system, home, etc.) and just adding in the creation of a ntfs partition.

Any ideas would be greatly appreciated ;)

---

### Post by squakie on 2013-06-25
Looks like the link is outdated.  

EDIT:  removed text here as I got this to work quite easily.

---

### Post by squakie on 2013-06-28
EDIT:  Forgot to mention, did all of this from Ubuntu

OK, got this working.

I tried following several threads on the net - all basically the same - load the Pi wheezy img (I'm using the 5/25/2013 image) to both the hard disk (or flash drive) AND to the SD card via:

dd bs=4M if=<image file path and name> of=/dev/sdx

where:

bs=4M is the block (buffer) size to use in the transer.  If you have problems with this is you can shrink the size but it takes longer.

/dev/sdx  is the ID of the device you are loading the image to.  Be careful - use dh -f prior to inserting each device and after inserting each device so you know you are working with the correct device each time.

A couple of notes:

- the device being used for the disk, be it a USB flash drive or an actual USB hard disk, should be connected directly to one of the Pi's USB ports for better speed.  DO NOT connect a USB bus powered external USB disk to the Pi directly - use a POWERED hub.

- just do one media at a time (USB flash/disk, SD card) to avoid confusion

- the threads on the net say to delete things from the SD card and copy them back from the USB flash/disk.  I just skipped this step - think about it - they both have the SAME image loaded to them.


After both of the media have been create, there are a couple of additional steps:

- The Pi uses the SD card to boot - it MUST be there with the same partitions defined and defined as a boot device.  Loading the image did this for you.  However, a small change needs to be made to one of those boot files to direct it to the USB flash/disk.  For me, I ejected the SD card, removed it from the slot, then inserted it again so it would get recognised by the system again.  2 logical drives will be mounted - you only need to change the one that says "root".  Using the file manager, open "root" and look for the file called "cmdline.txt".  Right-click on the file and open it in an editor.  Search for the string that looks something like:


root=/dev/xxxxxxxxxx

replace the xxxxxxxxxx part with sda2.  The result should show:

root=/dev/sda2

This tells the boot process the all of the file system resides on the USB flash/disk.

Save the file.

Eject the SD card.

Insert/attach the USB drive/disk.  The size of the file system is currently set to a small size because the image was loaded.  To make use of the extra space, there are a couple of options:


(1) Expand the file system itself to take up all the space

(2) Create a new partition in the new space.  I chose this option so I could have a NTFS partition where I store my media for the media server I'm building with the Pi.

For both options:


[LIST]
[*]start gparted as super user (I just opened a terminal window and did sudo gparted) 
[*]select the device that is the USB flash/disk 
[*]delete the "linux" partition 
[*]create a new partition of the size/type you want - I just used all of the remaining space as a NTFS space. 
[*]I don't know if this step is needed, but it only takes a couple of seconds anyway:  format the partition in the file system type you selected and give it a name if you wish - I named mine Pi1xbmcshares 
[*]close gparted 
[*]eject the device 
[/LIST]

Now just put the SD card in the Pi and attach the USB flash/disk to the Pi.  For the first boot, you MUST have a keyboard attached.  I use a wireless keyboard and mouse so this makes it simple.

Be sure your monitor/TV (I use my HDTV - it's small but it works! ) is set for input from the Pi.

Plug in the Pi.  If everything was done correctly it should boot and eventually you'll get the first-time config screen.

EDIT 2:  With the Pi, you really should use a USB hub, and this hub MUST be powered via an A/C adapter - you will far exceed the current limit of the Pi if it isn't, and things can get ugly (burn out the Pi, things like that ;) ).  My personal configurations are:

- USB A/C powered hub with updated power supply.  I use 5 amp even though it's overkill for my 7 port hub as the adapter was dirt cheap on Ebay.  This hub is connected to one of the USB ports on the Pi.

- my external USB hard disk is connected to the other USB port on the Pi.

- I have a wireless keyboard/mouse plugged in the hub
- I have a wireless adapter plugged in the hub
- I have a couple of USB flash drives for "playing" plugged in the hub

---

### Post by Bucky Ball on 2013-06-28
Well, you've just about got it right. I would advise RaspBMC for the Pi media center. It rocks. That is basically Xbmc for the Pi. Xbian is out there also. 

Yep, just create the NTFS partition like you would any other on the hard drive and stick your movies in there. I think the only thing you need to worry about is, yes, the Pi will see that partition without any issue, but will it be able to read/write to it? You might need software on the Pi to deal with NTFS.
All do-able though as you can drop to a terminal (in RaspBMC you 'Exit' and then hit ESC to get to a shell) and 'sudo apt-get install' whatever you need, just the same as Ubuntu.

Wondering why you're using NTFS at all, though, as you are connecting the drive to the Pi. Why not EXT4? 

You won't get a Ubuntu on there, incidentally. That chip is an older ARM apparently which Ubuntu no longer supports. Debian is halfway there, though. ;)

---

### Post by squakie on 2013-06-28
I did test xmbc on the Pi using an external data disk in NTFS before I started the rest of the project, as I wanted to be sure things would work correctly before I went to all the trouble.  Just hoping I haven't done anything to mess that up now ;)

I chose NTFS as a "just in case", that being that if something happened the drive could still be plugged into a (gulp!) Windows box and be able to at least access all the media content.

I was thinking of using just RaspBMC when everything is all done and working correctly.  Right now I'm doing too much "playing" on the dang thing besides getting the media center going - you know how that goes ;)

I did run into a rather curious thing - and I think I need a little help.  After changing the Sd and hard disk for the Pi that will be the media center so it using the hard disk instead of just booting and running off the SD I somehow got my wireless messed up.  It worked before I made the switch over.  Currently it can scan and see networks.  I can select mine but it just keeps failing (cyles through scanning, trying to connect, over and over) as if the network password is incorrect.  I've deleted the network from the network config gui (for wpa) and then it doesn't scan anything.  I reboot - the old definition is back and it gets stuck in the cycle again.  I know it's asking for a tkip key - I just don't remember how I set up the router, but I think it was WPA2/AES.  Perhaps I made some change before on the Pi that let it work that I have forgotten about.

I've also been setting up another Pi for my nieces' husband and his weather station.  I got it set up using the SD card for boot and the system itself on a 32GB USB flash drive.  Installed wview (THAT was a challenge - I probably should have searched the net more for better instructions! ;) ) for the weather station to interact to, and "borrowed" the wireless adapter from the media center Pi.  Everything the same as the media center - SD card for boot, USB device for system, A/C powered USB hub with wireless network adapter, wireless keyboard/mouse adapter, couple of flash drives.  The wireless works there.

So obviously I've done something stupid with the media center wireless - I just either have to reload it (there's nothing but the system and an empty for now NTFS partition on the drive so easy to re-do), or I need to find out what the heck I did so I can back it out and start again.  Talk about feeling stupid!

As always, thanks SO much for your help!  If you have any ideas on the wireless (didn't give much to go on) please let me know.

I also had another thought that I just haven't tried yet.  What do you think about powering the Pi with a micro-usb to usb power cable right off the hub?  I've got plenty of ports on the hub and a power supply to handle the load.  I don't see any reason why not, but just wondering if there's something obscure there I may be missing.

---

### Post by squakie on 2013-06-28
BTW - I just checked - bye the default mount in /media, the NTFS file system is read-only.  IO plan to use it as Samba shares as well, so I'm thinking perhaps when I was testing this before I had mounted the shares elsewhere ivia fstab.  Going to try setting that up again and see how it works.


EDIT:  I DID make a boo-boo - you were right about the NTFS stuff on the Pi.  I think what I did before was actually copy a movie from the Ubuntu box (the external drive there is NTFS for the same reasons) to the media center disk but the media center disk was indeed ext4.

So, since I'll have back up of all the movies, etc., on the Ubuntu box, I'm going to re-do the USB drive, just expanding the ext4 system space with gparted.  Will make the Samba shares easier to set up that way also.

Thanks for the heads-up!

---

### Post by squakie on 2013-06-29
Just reloaded the image to the USB hard drive and expanded the ext4 partition and all is well - the wireless works again also.

I'm also curious - has anyone gotten an external USB dvd/rw drive working on the Pi and with xbmc there as well?  My attempts have failed.  I finally gave up on the for now, but I would like to get one working if I can prior to giving the media center to my sister and brother inlaw.  

I also tried the "touch" of the USB hard drive every 5 minutes in crontab as suggested elsewhere.  It seems to do what it's supposed to, but with an unwelcome side effect:

if you are watching a movie in xbmc (and I suspect other things are succeptible as well) the "touch" causes the xbmc to loose the drive so the movie stops and you have to restart xmbc.  That presents a challenge since you have to actually reboot on xbmc exit - this would not be acceptable needless to say.  So, I've removed the crontab entry.  I'm just worried about the drive going to sleep again as it doesn't seem to wake up on the Pi.

And of course another question:  since the Pi has no clock, is there anyway to set the fake time?  I'm sure for my niece's husband's Pi weather station he will want real time, not some time off  by who knows how much.  A little difficult to keep true statistics otherwise.

---

