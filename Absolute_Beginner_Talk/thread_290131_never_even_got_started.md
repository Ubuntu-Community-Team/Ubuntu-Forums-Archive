---
title: "never even got started"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by moonman4au on 2006-10-31
I have downloaded 6.10 from the dl site.  I tested the iso hashes? and all is fine.  When I restart my computer with the live cd in the drive, it will not try to boot from it.  It goes straight to Windows, however my boot order is cd, floppy, hd.  Any suggestions?  I would like to start using this, but I need it to load first.

Thanks in advance for any help.

---

### Post by devilsadvocate1987 on 2006-10-31
Make sure there is nothing wrong with the boot order - put in a windows cd or a dapper cd or something which you know boots into the drive and check if it boots from there. If the problem is on the cd itself, you can try to burn the iso again. Burn at the lowest possible speed and finalize the disc once you're done. I think the disc-at-once option in nero is better than track-at-once for this but someone will need to confirm that.

---

### Post by aktiwers on 2006-10-31
How did you burn the Iso?
Did you remember to burn it as Image?
When you burn it, there should NOT be only one file on the CD.

---

### Post by moonman4au on 2006-10-31
Okay, I burned the iso as an image with nero at 4x.  There are about 20 files in the folder.  When i put the cd in and windows is already running, it pulls up the logo.  I shut down at that point because I did not know if that would mess up the windows.  I have burned the cd twice and tried it on 2 different machines.  Same thing happens.  Straight to windows.  I know the boot order is correct.

---

### Post by aktiwers on 2006-10-31
Sorry but im just making sure. After you tried this, you did reboot your computer with the CD in, right?
EDIT:
Nevermind.. just relooked at your post, and see you clearly state you have tried this.

---

### Post by devilsadvocate1987 on 2006-10-31
Dont worry, it cant mess up windows. Can you post a link to the iso  you downloaded.. just so we can make sure its supposed to boot?

---

### Post by ewl1217 on 2006-10-31
This might be a silly question, but did you save the boot order when you exited the BIOS? If you didn't then that would be the problem.

---

### Post by slimdog360 on 2006-10-31
> Originally Posted by ewl1217 View Post
This might be a silly question, but did you save the boot order when you exited the BIOS? If you didn't then that would be the problem.


I cant believe it took 7 posts for someone to say that.

---

### Post by aktiwers on 2006-10-31
yeah and remember it should boot from CD as the first thing.. but again that might be silly to say as well..

---

### Post by moonman4au on 2006-10-31
the defalut boot order is cd, floppy, hd.  Usually the first two are empty so it goes to hd.  Here is the link [http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)

went to a location near me.  I even checked the hashes for the iso.
here is the full name of the file i downloaded. ubuntu-6.10-desktop-i386

---

### Post by PriceChild on 2006-10-31
Try burning to a CD-R if you are currently burning to CD-RW.

I've seen issues resolved by this.

---

### Post by moonman4au on 2006-10-31
> **PriceChild said:**
> Try burning to a CD-R if you are currently burning to CD-RW.

I've seen issues resolved by this.

I have a copy on both types of media now.  The first was RW and I decided to put one on a R.  Thanks for the help guys and gals.

---

### Post by devilsadvocate1987 on 2006-10-31
Do you have 2 cd drives by any chance?

And although i'm not sure of this myself, could there be some wild master - slave issues?

---

### Post by moonman4au on 2006-10-31
> **devilsadvocate1987 said:**
> Do you have 2 cd drives by any chance?

And although i'm not sure of this myself, could there be some wild master - slave issues?

only one cd drive, no idea about a master-slave i dont even know what that is.  sorry i am not real good with all of this bios stuff.

---

### Post by devilsadvocate1987 on 2006-10-31
I'm sure stumped. It should be working. :\

Try burning it on another computer. Maybe something is wrong with your cd writer. That happened to me a couple of times...

---

### Post by aktiwers on 2006-10-31
yeah me too..  or what program do you burn it with? Maybe the program is burning it wrong?

You could try to mount the CD with Daemon Tools and simply burn a copie from there. Not sure if that will fix anything though, sorry.

---

### Post by randomnumber on 2006-10-31
Do you have more than one cdrom drive? If you do then you need to make sure the cdrom drive the cd it is in is the same as the one you are booting with. It has been my experience that the cdrom booting only checks one drive then moves to the boot device.

---

### Post by steven8 on 2006-10-31
> It has been my experience that the cdrom booting only checks one drive then moves to the boot device.

That is not true of all computers, I'd say.  My bios offers three boot options.  I have them set as floppy, cdrom, hde0.  When it runs through the boot, it tries all three of my cd drives. It shows:

CDROM. . .
CDROM. . .
CDROM. . .

I can put put a disk in any and have it work.

I can tell you that some drives do not like some media, though.  My CD-R disks will boot from my cdrom drives upstairs, but they won't read in the cdrom drive of my computer downstairs at all!  let alone boot.

---

### Post by seshomaru samma on 2006-10-31
Another possible problem is the fact that ISO files appear with an icon similar to zip files on Windows, which confused me the first time I downloaded a Linux ISO , I proceded to unzip the ISO before burning and in result it didn't boot. The file should not be unzipped but burned as it is.

---

### Post by Scheater5 on 2006-11-01
I've heard it's not the greatest policy in the world, but instead of adjusting the Bios to change the boot order, I always choose to boot from the CD directly.  On my Dell Inspiron this is done by holding F12 at startup (the Bios setup is F2), and then selecting the CD drive from the menu.  I'm not sure why this is not is frowned upon, but in your case it may be worth trying, just in case something is wrong with the way you are setting up the bios that we cannot diagnose remotely.

---

### Post by kvonb on 2006-11-01
Do any CDs boot on your computer? If not, you need to find one that will.

Did you write the CD on that computer?  If not it might be an older drive.

Re-burn it at a slower speed, ie 16x

---

### Post by steven8 on 2006-11-01
perhaps ordering one of the premade CD's might help.

---

### Post by moonman4au on 2006-11-01
I have no idea why it would not boot the first 30 times I tried, but amazingly enough, it booted on the last attempt.  Crasiest thing ive ever seen.  Thanks all for the help.

---

### Post by steven8 on 2006-11-01
Go figger.  I'd make a joke about having to tape a quarter to the needle, but I'm not sure how many folks here would understand.

Now. . .how do you like it??!!! :-)

---

### Post by spinflick on 2006-11-01
> **steven8 said:**
> Go figger.  I'd make a joke about having to tape a quarter to the needle, but I'm not sure how many folks here would understand.


A quarter of what? :p

---

### Post by RanDinCarolina on 2006-11-01
He just got all the dust off the laser.:)

---

### Post by steven8 on 2006-11-01
> A quarter of what?

I rest-a my case!! :mrgreen:

---

