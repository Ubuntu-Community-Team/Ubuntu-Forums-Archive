---
title: "Ubuntu wont let me install mint"
date: 2011-10-26
forum: Any Other OS
---

### Post by mushy365 on 2011-10-26
I have ubuntu 11.04 but im looking to switch over to mint, i got the boot cd for mint and when i run it, at the boot screen it only gives me the option to boot from harddrive or run mint. 

so i choose run mint and it comes up, running from a live cd. On the desktop there is a icon that says install linux mint, but when i click it nothing happens. I can do other things on the iive cd, but it wont let me install mint. 

Any ideas?

---

### Post by philinux on 2011-10-26
Moved to other os/distro talk forum.

---

### Post by Kilz on 2011-10-26
> **mushy365 said:**
> I have ubuntu 11.04 but im looking to switch over to mint, i got the boot cd for mint and when i run it, at the boot screen it only gives me the option to boot from harddrive or run mint. 

so i choose run mint and it comes up, running from a live cd. On the desktop there is a icon that says install linux mint, but when i click it nothing happens. I can do other things on the iive cd, but it wont let me install mint. 

Any ideas?

Did you check the md5sum of the disk image you burned before you burned it to a disk?

---

### Post by cavh on 2011-10-26
Right-click the 'install Mint' icon on the desktop and make sure it's set to be executable. If it isn't, you will have a problem as the CD is unlikely to be able to be written to, in which case I would use a USB stick and download Mint from the Mint website and then set the 'boot to USB' option as 'enabled' in your BIOS and go from there.

---

### Post by mushy365 on 2011-10-26
i dont know what the md5sum is so im pretty sure i didnt check it, also dont have a usb stick. ill try booting nto mint again and seeing if its rwx

---

### Post by Kilz on 2011-10-26
> **mushy365 said:**
> i dont know what the md5sum is so im pretty sure i didnt check it, also dont have a usb stick. ill try booting nto mint again and seeing if its rwx

md5sum is a hash of the disk file. Its a long number usaly found next to the download link on the mint pages. [Here is a page]("https://help.ubuntu.com/community/HowToMD5SUM") that will help you check that. It will make sure you have a good file to burn, if not a bad disk file may give a lot of errors or not let you do things.

---

### Post by mushy365 on 2011-10-26
well i just booted into mint and the install linux mint icon is marked as executable.  so i guess ill go back to ubuntu and try the md5sucm

---

### Post by mushy365 on 2011-10-26
booted back into ubuntu the md5sum values match perfectly. What could be happening? I had a look a Gparted and it wont even let me create new partitions on my hard drive. Im pretty sure im using it correctly, but the option to add a new partition is greyed out.

---

### Post by mushy365 on 2011-10-26
is it a bad idea to go to system->administration->disk utitlity and format the drive? I dont want to do that if the live cd wont install tho.

---

### Post by qamelian on 2011-10-26
How many primary partitions do you see on the drive? If you already have 4, you will need to do some juggling, as 4 is the maximum number of primary partitions possible.

---

### Post by mushy365 on 2011-10-26
there is 1 i think here is a picture, you can see even with it highlighted i cant create a new partition


[http://i41.tinypic.com/350toj4.png](http://i41.tinypic.com/350toj4.png)

---

### Post by haqking on 2011-10-26
> **mushy365 said:**
> there is 1 i think here is a picture, you can see even with it highlighted i cant create a new partition


[http://i41.tinypic.com/350toj4.png](http://i41.tinypic.com/350toj4.png)

You have no free space to create a partition, and you cannot resize to free up space as the partition is mounted.

You can do this from the Mint CD or Ubuntu CD etc as the local partition shouldnt be mounted, or at least if it is you can unmount

---

### Post by mushy365 on 2011-10-26
would that be what is stopping me installing mint from boot cd? Because i dont get that option on the boot cd.

Could i use disk utility to formate the enite drive on ubuntu or do i need an ubuntu live cd?

---

### Post by verymadpip on 2011-10-26
Any chance of a GParted screenshot before you do anything?

Oops, I see we're already there, sorry.

---

### Post by mushy365 on 2011-10-26
i posted one.

---

### Post by haqking on 2011-10-26
> **mushy365 said:**
> would that be what is stopping me installing mint from boot cd? Because i dont get that option on the boot cd.

Could i use disk utility to formate the enite drive on ubuntu or do i need an ubuntu live cd?

Like i just said you cant do anything to the disk/partitions whilst it is mounted.

If you boot to a gparted boot CD or Ubuntu/Mint Live CD you can then use gparted or fdisk etc to resize and partition the disk.

Or you can use the Mint/Ubuntu CD installer to manage the paritions

> **verymadpip said:**
> Any chance of a GParted screenshot before you do anything?

there is one in  post #11

---

### Post by mushy365 on 2011-10-26
like i was saying tho, the mint cd wont let me run the installer for some reason.

---

### Post by verymadpip on 2011-10-26
You'll need to do it from a Live CD.
If you want to install Mint & have a Mint Live CD use that.  It'll save messing about with CDs in & out of the drive.

Your Mint CD does run the live environment right?

You need to shrink sda1 to create the space for your Mint install.  

Oops, again.  I think I'll just stay out of this  :)

---

### Post by haqking on 2011-10-26
> **mushy365 said:**
> like i was saying tho, the mint cd wont let me run the installer for some reason.

dont choose the try option then when booting from it, choose the install option.

However make sure all your personal data is backed up

---

### Post by mushy365 on 2011-10-26
The live cd install does not give me a try or install option. Just saying booting to mint in 10 seconds and give me a countdown. I hit escape and a menu came up but only to  

boot from disk, boot from live cd and something about safe mode. No option to install.

---

### Post by verymadpip on 2011-10-26
Either let the coundown do its thing, which should take you into a Live session from the CD, or choose "Boot from Live CD".

---

### Post by mushy365 on 2011-10-26
ive tried both, it takes me to the mint desktop running from the live cd. It wont let me run the install mint application though.

---

### Post by verymadpip on 2011-10-26
What happens when you hit install Mint?
It won't spring instantly to life as you're running from CD, it may take a minute or two...

---

### Post by mushy365 on 2011-10-26
nothing happens, just like i didnt click anything. Ive left it for 5 minutes or so and still nothing.

---

### Post by verymadpip on 2011-10-26
Odd.
Okay, how much space do you want for your Mint install?
Which Mint are you trying to install?
Can you access GParted in the live session?
Am I correct in saying that you've no option to check the disc (CD) for defects?

Sometimes I've had to click the install icon a couple of times before it gets the message, but I'm guessing you've already tried that.

I'm running out of ideas 'cos this usually goes like clockwork.  In my experience anyway.

---

### Post by mushy365 on 2011-10-26
> **verymadpip said:**
> Odd.
Okay, how much space do you want for your Mint install?
Which Mint are you trying to install?
Can you access GParted in the live session?
Am I correct in saying that you've no option to check the disc (CD) for defects?

Sometimes I've had to click the install icon a couple of times before it gets the message, but I'm guessing you've already tried that.

I'm running out of ideas 'cos this usually goes like clockwork.  In my experience anyway.

Just booted into mint again. 

I dont mind how much space, ill use the whole disk overwriting ubuntu i dont mind
im trying to install the latest version of mint which is 11 i think
There is gparted in the live session but when i click on it nothing happens
when i boot and press esc it gives me options 
boot to linux mint
boot to linux mint (compatability mode) <- this just takes me to a terminal
check cd integrity <- ran this and said it found one error but continued on booting
ill keep clicking the install linux mint button and waiting to see if i get any more ideas

---

### Post by mushy365 on 2011-10-26
Umm weird, the installer ran there for a bit, then crashed. I guess there is a problem with the live cd. Thats the first time it had ever ran.

---

### Post by houseworkshy on 2011-10-26
Seems odd.  Use gparted in the Ubuntu cd running live.  Create a partition using any old file system ( it's going to be overwriten anyway).  Once the partition is made look at the flags and make sure the "bootable" one is checked.  Then try again allowing the installer to do it's own thing on the new blank partition ( NOT the whole disk ).  That should be ok.  If not make sure that your bios is set to look at the cd/dvd drive first when booting.  If you are unsure about the integrity of your live cd download a new iso.  The md5 is a checksum which checks the integrety of the file.  One can use it from the terminal; open a terminal and type "man md5" for details on how.  An easier way to use it is with a firefox addon called downthemall.  Bung that in then when you download a fresh iso choose "with downthemall" it will open a window asking where to put it etc.  At the bottom of that window is a place where you can paste the checksum in and choose which checksum method to use.  I'm in a bit of a hurry atm so don't have time to find the checksum for you be nice if it was on the same page as the download but it isn't, it is on there somewhere though.  I'd recomend going with an older but still supported Ubuntu which has had time to have bugs ironed out.  The 10.04.3 or maybe 4 by now is  good.  It's always a good idea to back up your important bits first, don't bother with things you can reinstall from the net or installations discs.  Unless you have irreplaceable films the important bits are usually fairly small, address book, documents, some pics, save games etc.  If the only out of the pc you have is the dvd/cd get a copy of puppy ( a tiny system which can be loaded to ram then have it's disk removed so freeing up the dvd drive) and do the backing up with that.You can also email yourself to a webmail ( like gmail )
with precious bits.  Google docs gives one a lot of room but is incredibly unprivate ( it will all get scanned for marketing information, so nothing with banking details on it).  Good luck.

Edit, Sorry I read too fast.  It is mint you want to install.  Well it all still applies.  I'm not sure what sort of drive manager mint has but gparted from either distro should do the job.  At the last stage, installing, just use mint.  It may be a good idea to ask on the mint forums too.  Mint is based on Ubuntu but is nearly as differant from it as Ubuntu is from Debian ( which is what Ubuntu is based on).

---

### Post by verymadpip on 2011-10-26
There's the possibility that the one error could be the issue.
Can you burn another CD?  Try at the slowest speed possible.

I find that installing from USB saves on CDs/DVDs, so that may be a way forward from here.

Do you still have a working "real" desktop? (looks like Ubuntu 10.10/04 maybe from the earlier screenshot).  If you do & you have a spare USB stick (2Gb should be enough) we can try to do this from USB

What are the specs of your rig by the way?

Another oops moment lol

---

### Post by houseworkshy on 2011-10-26
Another quick thought.  For operating system disk always burn onto write once only media, lots of people have had problems with rewriteables.  Also worth seeing what sort of bootloader the two systems use, if differant the latter should overwrite the former but I'm not expert enough to know for sure.

---

### Post by mushy365 on 2011-10-26
I have ubuntu 11.04 it looks older because if i dont run it with no effects the computer freezes on boot, which is why i have decided to switch. I think there is an error with the cd even tho the md5sum matched. 

I am downloading an earlier version and going to burn that, i dont have a usb stick which sucks. 

If this does not work i might try arch linux instead.

---

### Post by houseworkshy on 2011-10-26
"don't have a usb stick" Yeah get puppy too, part of it's not bad range of software concidering the size is a cd/dvd burner. There are various "puplets" too, some of which have things like compiz.  As you may be using it anyway it could be worth seeing if you can get desktop effects to work as a check on your hardware.  If they do it could be that the desktop effects problem is a software thing ( which would be rather good news as you are doing a reinstall anyway :) )

---

### Post by verymadpip on 2011-10-26
If your md5 sums match you're download is good.  Just burn the CD as slowly as your hardware will allow which should minimise the chance of errors.

As far as I can tell arch is pretty hardcore, you build the system from the ground up so to speak:

[https://wiki.archlinux.org/index.php/Beginners%27_Guide](https://wiki.archlinux.org/index.php/Beginners%27_Guide)
(I'm too much of a coward to attempt anything like it yet).

If you want a lightweight distro I'd recommend Lubuntu.
What spec is your rig?  RAM, graphics card & such like...

---

### Post by houseworkshy on 2011-10-26
Yet more thoughts while my bath runs.  For system info install sysinfo, run it and choose "save file" it's the easy way to get the main spec's ( pretty sure that one can put it in mint.  Another idea comes from the extra symptom of crashes when running desktop effects.  If you are not low on ram that could easily be heat.  You could find out by installing lm-sensors, once in, type sensors in the terminal to find out what temperature you are running at.  If too high the box may need a good clean.

---

