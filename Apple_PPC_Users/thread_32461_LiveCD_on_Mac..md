---
title: "LiveCD on Mac."
date: 2005-05-07
forum: Apple PPC Users
---

### Post by SparkyDawg on 2005-05-07
My friend has a problem where he burns the live cd and when he starts into his mac with the live cd in, it just boots into osX.

Any help would be appreciated.

---

### Post by ssam on 2005-05-07
has he tried holding down 'C' at boot time

---

### Post by SparkyDawg on 2005-05-08
Yes

---

### Post by dnix71 on 2005-05-08
I tried the live ppc version yesterday and it worked fine. I have a 1.25 GHz G4 eMac with two external hd's and an external cd/dvd burner. A cold boot while holding down the C key will do it unless the disc your friend burned is no good.
I downloaded my iso on a pc running Win98 and burned it as an image file under EZ CD Creator 5 Platinum.
I'm still living on dialup at home, so I had to borrow a dsl connected computer for the iso download and burn.

---

### Post by sgmorr on 2005-05-09
I read an article on MacMerc.com about the live linux CD and was interested. I just downloaded the live CD 5.04 and burned the disk image using FireStarter FX. I know how to boot my iMac from a CD, but have one question first. Are there any potential problems that might be caused by booting from the live CD? Sorry, but I'm new to this. But I am a Mac veteran running Tiger 10.4. Thanks very much.

Steve M.

---

### Post by Len on 2005-05-09
The LiveCD will not touch anything on your mac.

It is TOTALLY SAFE to run it, that's where it is for :D

Go ahead and try it! Do not be scared for the questions about your country. Those are only for the locale, keymap and date.

Again: it will NOT touch anything on your disk and after a reboot you're back to normal so safer it can't be :D

---

### Post by sgmorr on 2005-05-09
[QUOTE=Len]The LiveCD will not touch anything on your mac.

It is TOTALLY SAFE to run it, that's where it is for :D

Go ahead and try it! Do not be scared for the questions about your country. Those are only for the locale, keymap and date.

Again: it will NOT touch anything on your disk and after a reboot you're back to normal so safer it can't be :D[/QUOTE]
 Thanks Len!

---

### Post by sgmorr on 2005-05-09
Len,

When I'm booted from the live cd, how do I quit or exit it to boot back up from my OS X HD? I suppose it will be obvious, but I just want to know what to look for. Thanks.

Steve M.

---

### Post by Len on 2005-05-09
When GNOME is running, just choose "Log out" from one of the menus on top.

In the rare case you get no image or a distorted image so you can't see the menu, just pull the plug. Since your harddisk is not mounted (read: not used) even this will do absolutely no damage to your Mac.

But, forget about that rare case and just put in the CD. Things are rather obvious really :). I expect your next post to be from Firefox running off the Ubuntu Live CD ;).

EDIT:
Addition:
Since the mac will only boot from the CD when the 'c' key is pressed, it is not needed to get the CD out when you reboot. So in case the worst happens: the system crashes, pulling and reinserting the plug will get you back to Mac OS, even if the CD is still in the drive.

---

### Post by sgmorr on 2005-05-09
Len,

When I'm booted from the live cd, how do I quit or exit it to boot back up from my OS X HD? I suppose it will be obvious, but I just want to know what to look for. Thanks.

Steve M.

---

### Post by sgmorr on 2005-05-09
Thanks for all your help Len. I'm posting using Safari in Tiger on my iMac G4 right now. I decided to put the live CD into my old iMac G3 and boot it. It started and I got lots of text on the screen. It reached a point where I was asked to choose among various selections for PPC 3s or 4s. It said one of them should be predesignated with an "*", but I didn't see it. So I just hit "return". The boot process continued (very slowly) and I finally got what must be the brown desktop with a menu bar at the top and a bar at the bottom. There was also an open window. At various times I had either a cursor or a little spinning circle. I never could get any of the menus to respond. I kept hearing activity from the drive during the whole boot process. After about 45 minutes I just powered my iMac off.

My old rev. B 233 MHz has 96 MB of RAM. Is it out of spec. for the live CD or did I do something wrong? I'll be waiting to try it in my 1 GHz flat panel G4 with 1GB of RAM.

Thanks again!

---

### Post by Rxke on 2005-05-10
Yeh, booting from the liveCD is slow.
And the 96 Mb won't help either, IIRC, that really is the bares minimum to get thing up and running. the disk-chatter you got was probably the HD being used as virtual memory

(Is that possible? On a live CD, not supposed to touch the HD... Hmmm...)



I booted the live CD on a g3@350MHz, and it took a looooong time too, but I had more memory, so eventually it worked.
Then I burned an install cd, and it took even longer :D
but that is of course only the first time booting: lots of things get installed, configured... 

So live CD should be seen as some kind of 'virtual' install, lots of shuffling files etc before you get to where you want. Live CD's are not something you want to boot every day, heh.

---

### Post by Len on 2005-05-10
The Live CD requires at least 128 MB of RAM. Since Linux cannot use 'virtual memory' when booted from the CD this is the absolute minimum needed.

I didn't know it would crash on 96 MB already, but there you are: the worst case: things crashed, and still nothing went wrong. That's where a LiveCD is for :).
I hope this scenario took away your fears :P

If you plan to put Ubuntu or Mac OS X on that old machine at least 160 MB of RAM is *highly* recommended. OS 9 does fine with 96 though, and various small linux distributions also do.

---

### Post by sgmorr on 2005-05-10
Thanks for the feedback. I've learned a lot and gained some confidence. I'll try the live CD in my G4 iMac with 1GB of RAM and see what happens.

What Linux apps are present in the live CD install?

Steve M.

---

### Post by sgmorr on 2005-05-19
Well, I've done it. I'm booted from the live CD on my iMac G4 and browsing using Firefox. Pretty neat!

Can I save bookmarks in Firefox? Are they saved to my HD?

Can I actually view files on my HD while booted from the live CD?

Many questions. Thanks.

Steve M.

---

### Post by Len on 2005-05-19
Since the LiveCD is meant to be as safe as possible it doesn't mount your harddisks, so you have to install Ubuntu to make full use of it. Bookmarks in firefox can be saved to a memory stick or so, and you can import bookmarks as well from such a removable device.
It is much easier though to post them somewhere on the web. Just open your bookmarks file in your browser and post it somewhere. Your webmail account, a private message in these forums to yourself, etc.
In safari, choose File -> Export to export your bookmarks to a HTML file viewable by any browser; in Firefox, choose Manage Bookmarks and then Export to again create a HTML file viewable by any browser. Safari and Firefox can also import these files.
This is a nice way to backup your bookmarks as well!


Mounting harddisks is a different story.
You can mount your harddisks with a terminal command. That is rather complicated though. 
First, you have to find out which partition is your HFS+ disk and then you have to mount it with a 'mount -t hfsplus /dev/hdx /somefolder' command, where "hdx" is your Linux harddisk name and "somefolder" is the path to the folder you want to mount it in.
I wonder if that works from the LiveCD. If you want to undertake this google and the ubuntu site will provide a lot of information about these things for you. 

As a linux newbie I'd just backup my OS X disk, partition the drive for OS X and Linux and install both. 
Disk Utility from the Mac OS X installer CD can help you partition the drive, choose 2 partitions, one for Mac OS X and one free space (ubuntu will create its partitions there automatically). Note that partitioning the drive will erase all data, so make that backup :). 
Of course you can also backup your files and decide to dump OS X and use only Ubuntu. No partitioning is needed for that.

---

### Post by sgmorr on 2005-05-20
Thanks Len!

---

