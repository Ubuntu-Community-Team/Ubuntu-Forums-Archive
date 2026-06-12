---
title: "uninstall ubuntu"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Phoenix {iOTi} on 2007-07-12
hi , ive just recently installed ubuntu and realized it isnt for me (its way too confusing) and i want to switch back to vista. but when i installed ubuntu i went with the option to format my hard drive wich i realize now was stupid. so now im wondering how to uninstall ubuntu and put windows vista back on any help (p.s. i have read and searched for awnsers none of them seem to help)

---

### Post by Seisen on 2007-07-12
I'm assuming you completely removed Vista from your hard drive, well just pop in you Vista cd and be on your merry way. If you don't have a Vista cd then you might be SOL.

---

### Post by JRoDDz on 2007-07-12
Run the Vista re-installation CD if you have it.

---

### Post by FluffyBunny on 2007-07-12
Sorry to hear it,  I recently got my wife to switch on her laptop, and after a week or so she likes it better, but then again I set up everything on it for her.

To reinstall vista you need a bootable Windows Vista CD, and running the installation from it should have the same option of reformatting the hard drive. Meaning that you don't really uninstall ubuntu, but installing windows will delete everything on the hard drive when it reformats

---

### Post by godd4242 on 2007-07-12
> **Phoenix {iOTi} said:**
> hi , ive just recently installed ubuntu and realized it isnt for me (its way too confusing) and i want to switch back to vista. but when i installed ubuntu i went with the option to format my hard drive wich i realize now was stupid. so now im wondering how to uninstall ubuntu and put windows vista back on any help (p.s. i have read and searched for awnsers none of them seem to help)

If you don't have a hard CD you're screwed


NOT THAT IM SUGGESTING ANYTHING BUT IM SURE DOWNLOADING A TORRENT CLIENT NEVER HURT ANYONE HUR HUR HUR

Either way, you're gonnna need to get your paws on a DVD one way or another.

---

### Post by Phoenix {iOTi} on 2007-07-12
yes i did realize that putting the windows vista disk in would make sense ive gone through everything and tried to format the hard drive but when doing so it gives me an error idk dont know it exactly i can find out if needed though

---

### Post by Eggnog on 2007-07-12
Post the error message if you can.

---

### Post by FleetAdmiral74 on 2007-07-12
Dude, you have two beans! Give it a chance before you abandon it, use the forum!

Personally, I would have left Ub (prolly Linux) if not for this GREAT forum. The people are responsive, nice, and you really should give us a chance. 

But if you still want to go, thats totally your decision. Linux is not for everyone. Well, it should be....but its not :)

---

### Post by Seisen on 2007-07-12
> **Phoenix {iOTi} said:**
> yes i did realize that putting the windows vista disk in would make sense ive gone through everything and tried to format the hard drive but when doing so it gives me an error idk dont know it exactly i can find out if needed though

Download Gparted LiveCd and completely wipe the harddrive out so it is just one big continous unallocated space and hopefully Vista will install then.

---

### Post by Phoenix {iOTi} on 2007-07-12
ok first off thank you everyone for all the help fleetadmiral (sorry if i misspelled) i would consider staying with linux but  im so used to windows and linux is just way to confusing when i tried to install i knew nothing about it i might consider putting on my older computer and im going to try what the last guy who posted sugested (i dont remember his username x.x)

---

### Post by Phoenix {iOTi} on 2007-07-12
also the error msg was "Failed to format selected partion [error . ox8ooo4oo5]"

---

### Post by Eggnog on 2007-07-12
It sounds like perhaps it would work if you were to wipe out the current partitions and just start from scratch.

---

### Post by Phoenix {iOTi} on 2007-07-12
would that be what seisen is talking about?

---

### Post by aktiwers on 2007-07-12
Yes
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Seisen on 2007-07-12
Yes, I use  Gparted all the time it has come in handy many of times.

---

### Post by slumcat05 on 2007-07-12
I believe Gparted is on the Ubuntu install LiveCD (if I'm wrong about any of this, somebody please feel free to correct me), so just boot from that as if you were going to install Ubuntu (but, obviously, don't click the "install" icon). When it finishes loading, go to System > Administration > GNOME Partition Editor (or from the terminal type "gksudo gparted").

Make sure any partitions shown are unmounted (right-click on it in the list and choose unmount), then select each partition and choose delete. If you click Apply now, it will simply delete the partitions (I think just the partition table?) but you'd probably be better off selecting the unpartitoned space and creating a new partition (click new, choose the partition type, probably FAT32, choose ok, and click apply). This will completely wipe everything Ubuntu related, and Vista should have no problem formatting after that.

Although downloading the small Gparted LiveCD might be quicker and easier, it's up to you.

---

### Post by Seisen on 2007-07-12
> **slumcat05 said:**
> I believe Gparted is on the Ubuntu install LiveCD (if I'm wrong about any of this, somebody please feel free to correct me), so just boot from that as if you were going to install Ubuntu. When it finishes loading, go to System > Administration > GNOME Partition Editor (or from the terminal type "gksudo gparted").

Make sure any partitions shown are unmounted (right-click on it in the list and choose unmount), then select each partition and choose delete. If you click Apply now, it will simply delete the partitions (I think just the partition table?) but you'd probably be better off selecting the unpartitoned space and creating a new partition (click new, choose the partition type, probably FAT32, choose ok, and click apply). This will completely wipe everything Ubuntu related, and Vista should have no problem formatting after that.

I believe you are correct on that.

---

### Post by Phoenix {iOTi} on 2007-07-12
ok im in the partition table when i right click on them unmount is not clickable (its grey) i want to make sure theres nothing wrong before i continue

---

### Post by zarajoe on 2007-07-12
I recently installed Ubuntu as a dual boot with Windows Vista.  Though I like Ubuntu, I have decided to remove it because, I have Vista tweaked and customized to my liking and I can't be bothered doing it all over again with linux.

I removed Ubuntu by deleting the Ubuntu partition and adding the free space back to the Windows partition using 'Disk Manager' in Windows.  The problem I then faced was that the Grub loader was not removed, and because ubuntu was not installed, every time I turned on my computer the Grub loader would fail to work, and Vista wouldn't load.  To fix the problem I reinstalled Ubuntu.

How can I remove both Ubuntu and the Grub loader thing without damaging my Windows Vista install.

---

### Post by bodhi.zazen on 2007-07-12
[http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)

Note : Threads merged

---

### Post by ArtDeco on 2007-07-12
Ok. Linux is confusing. MS is confusing. You are already ahead of the MS clones by realizing that. Keep your Linux partion if you don't need the disk space anyway since lots of corporations that don't understand Linux pay thousands of dollars for "secure storage" that you already have for free just by saying 'I think I'll try Linux'. 

Dual Boot.

You can understand a safe place to keep files that you don't want Korporate Klones  and Script Kiddies  to access? Yes? Read the uninstall Faqs and we will see you next year.

---

### Post by tcoffeep on 2007-07-12
You want to delete Ubuntu???

*kills self*

---

### Post by Phoenix {iOTi} on 2007-07-12
art ive decided on not keeping it and im thinking of installing it on my older computer it would be nice if someone could continue helping me from my last post i really dont want to mess things up further

---

### Post by RichPicker on 2007-07-13
I apologize, that I can not help you uninstall Ubuntu. But I do think you are making the right decision. I did the same thing you did, but I don't have the Widows install disc. Rather than purchase one, I've stayed with Ubuntu. It's been seven months now.  Ubuntu is much much trouble. The useability is very low. The interfaces are counter-intuitive. Though I disagree with Windows for many reasons, it eats up less time in your life by using Windows instead of Ubuntu. Good luck to youi.

---

### Post by mytwobears on 2007-07-13
> **Phoenix {iOTi} said:**
> art ive decided on not keeping it and im thinking of installing it on my older computer it would be nice if someone could continue helping me from my last post i really dont want to mess things up further

Hi

The unmount option is not available because the partitions are not mounted, so just continue on and have gparted delete the partitions and make them 1 big unallocated space.  Then exit from the gparted disk and put in the VISTA disk and boot from it, VISTA should be able to install from there.

HTH :).

---

### Post by Phoenix {iOTi} on 2007-07-13
thank you all so much i am now running windows vista again i do have one more problem its with my back up drive
during the partition i did somthing (when i first installed linux) i think i tried to use half of it for storing the files i was installing but didnt work out so i just formatted my hard drive wich led into this could someone please help either this topic or aim xxpaintb4ll3rxx or pm if this topic is not appropriate [edit] just realized my problem wasnt included , my problem is the partitions that i made from the drive wernt deletable nor unmountable and they no longer appear under "computer" and i would like to somehow get it back if possible

---

### Post by quinnten83 on 2007-07-13
If you formatted the partitions as ext2/ext3 for use under linux, then they won't be detectable in windows.
I don't have vista so I'm not quite sure if this is the same as in XP, but go to disc management and in there reformat en recreate the partition. Yo will lose all data though, but it doesn't sound like there is much on it to begin with.

---

### Post by digital_sabotage on 2007-07-13
phoenix  ...if you want to completely erase everything on your hard drive you should do a low level initialize ...this more or less resets the polarity if i'm not mistaken 

...with newer hard drives you are best off determining the make and model of your hard drive ...go to >System >Preferences >Hardware Information

you should be able to find it ...it will have sub-headings under it titled 'volume'

once you have the model of your hard drive go to the manufacturer's site and try to find a 'format disk' or 'low-level initialize disk' or whatever title they give it

...download this to your desktop and burn it to a cd or floppy

...reboot with disk in and follow instructions  ...keep this disk and if you choose to play with linux again you will have no problems

...if you can't find a disk specific to your hard drive you could try 'dban' ...derek's boot and nuke ...i've never tried it myself though so read about it

...hope this helps ...good luck and hope you come back eventually  ...windows is boring

---

### Post by tcoffeep on 2007-07-13
> **digital_sabotage said:**
> ...hope this helps ...good luck and hope you come back eventually  ...windows is boring

HERE HERE!

---

### Post by macogw on 2007-07-14
> **Phoenix {iOTi} said:**
> ok im in the partition table when i right click on them unmount is not clickable (its grey) i want to make sure theres nothing wrong before i continue

If they show on the desktop, right click and unmount.  If they're not on the desktop, they're not mounted and that's why it's greyed out meaning you dont have to do anything

richpicker, idk what you're talking about.  xp -> ubuntu is much easier than xp -> vista, especially if you put Office 2007 on vista.  omg office2k7 is the most confusing interface EVER, and then they went and hid all of the options on vista so anyone who knew how to find stuff on xp is totally lost on vista....yuck

---

