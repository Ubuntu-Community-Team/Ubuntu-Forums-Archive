---
title: "Installing Ubuntu On Formatted Disk Help!"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by pinkfishe on 2006-11-26
Hey _**completely new**_ to forum and linux aswell so plz help out if you can :D

I think really this is a basic problem really, what i've done is formatted a machine that was running on 98SE that i had in my loft for ages and decided to mess about with.

Just now i have downloaded ubuntu linux disc image and burnt it using nero on my dell pc im using now and inserted it into my other pc's CD-ROM drive (After setting the bios to boot my CD-ROM first) and this comes up:-k :
 [IMG]http://i96.photobucket.com/albums/l182/pinkfishe/linuxproblem.jpg[/IMG] 

"Boot from ATAPI CD-ROM : Failure ...

Invalid system disk
Replace the disk, and then press any key"

I'm completely new to this kinda stuff so any help will be greatly appreciated.

Also i have the pc's spec (very rough idea of it) if this helps at all this definitely isnt 100% right if at all[LIST]
[*]Daewoo pc?[/LIST][LIST]
[*]Intel celeron 300mhz?[/LIST][LIST]
[*]196mb RAM?[/LIST][LIST]
[*]32x CD-ROM drive[/LIST]Thanks in advance anyway, would really like to learn more about Linux.:D (please note i dont have the 98se CD anymore only the ubuntu disc i burnt.

---

### Post by junglepeanut on 2006-11-26
Which cd are you using livecd or alternate, you should be using alternate. Also hopefully xubuntu or server to upgrade to gnome-core or icewm or something like that.

But alternate of anyf orm should at least get you started.
Did you check the cd was a good burn by verifying the md5sums?
Thanks

---

### Post by meng on 2006-11-26
The most common problems causing this are:
1) corrupted download (check the md5sum!)
2) bad burn (solve by reburning at lower speed)
3) wrong burn (e.g. simply copied the ISO file to a disk rather than using it to create a filesysteM)
Look here:
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

### Post by pinkfishe on 2006-11-26
I'm not sure which cd im using tbh i used this d'load link though

[http://www.mirrorservice.org/sites/releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso](http://www.mirrorservice.org/sites/releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso)

I went on the link from "meng" and read about md5sums but its kinda confusing me, i'm now running the md5summer program from that page will this create the iso's md5 file for me???:confused:

---

### Post by meng on 2006-11-26
The md5 is a way of checking that your download's integrity is intact.
The ISO you downloaded is the Live Desktop version. Given your system specs, I would recommend the Alternate CD version instead, but the Alternate version doesn't give you the "try-before-you-buy" functionality.

---

### Post by pinkfishe on 2006-11-26
Can you link me to the alternate version then plz?

---

### Post by Bartender on 2006-11-26
Pink -
Let's check the easiest thing first.  Do you have a working Windows PC?  With it up and running, toss the CD in the tray and open Windows Explorer.  Don't try to run the CD, right click on the drive and "Explore" it.  If you see one file, then you copied the .iso rather than converting it to a bootable CD.  If you see 7 or 8 folders and a handful of files, then you were successful at converting the .iso and you then need to go back and do the other things already suggested.
Yeah, with that amount of RAM the LiveCD probly won't even operate.  Don't let the alternate CD scare you off - it's the same text-based interface that was used for Breezy, and lots of us got thru that! :D

I typed in "Xubuntu download" and got to this [website]("http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/").  I'm in the Colonies, so I don't know what you'll get in the UK.  See the 4th download on this page?  That's the alternate install download for Xubuntu, which would probly be a better choice for your PC.  You'll find a very similar page if you google "ubuntu download".
Look a little further down the page, just past the download section.  See the list of files?  Right there on the top is "MD5SUMS".  Click on that, and copy those values to Word or Notepad or OpenOffice or whatever.  You want to check your download against the correct MD5.

See this line?

c0b54deca75e8e3a87988846c9ae1e44  xubuntu-6.06.1-alternate-i386.iso

That's the md5 for the Xubuntu i-386 alternate install .iso.  If you download the Ubuntu alternate install there will be a different .iso, available on the same place on that website.  Every download will have a different md5.

You'll then need a Windows md5 utility (I like md5Summer cause it's relatively easy) that can scan your download and generate an md5 hash.  You compare it to the one from the website to see if the download went OK.

---

### Post by pinkfishe on 2006-11-26
Nope i've already formatted the drive so when i run it just goes to the screen in my first post, i'm gonna try the alternative version and see if that makes a difference.

---

### Post by pinkfishe on 2006-11-26
Im just trying this iso now

does this look like it'll solve my problem? :D

[http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso](http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso)

---

### Post by Bartender on 2006-11-26
When I clicked on your link my PC got ready to start downloading an alternate install Ubuntu, so that looks like a good one!
Have you checked the CD in your Dell like I asked?  Need to know if you copied the .iso (wrong thing to do) or converted it to a bootable CD.

---

### Post by pinkfishe on 2006-11-26
I tried it in my dells drive but nothing happened :-k

Even though i'd checked the md5sums and i used burn disc image option in nero when i did it

It could have been because of how fast i burnt it 

I'll just wait and see with the alternative (currently 23%)

---

### Post by Bartender on 2006-11-26
How powerful is your Dell?  My Pentium 4 3GHz homebrew PC reliably converts .iso's at 8X.  I would burn them slower but NTI, the software accompanying my Sony DVD, doesn't give me an option below that and it's been working so I haven't had to download an alternative.
I'd suggest 2X if you can go that slow.  And don't do anything else with the PC while it's burning!  Oh, yeah, go into Settings and make sure you've turned power management to "Always On" so the PC doesn't go to sleep in the middle of the burn.

---

### Post by pinkfishe on 2006-11-26
Ok i'm using nero 6 so you know. I think you can burn pretty slow on it anyway so i'll try that with this.

Do you think the error coming up on my first post was to do with the disk being burnt badly then? because surely if the disc worked and my pc wasnt compatible it would say so instead :-k

My dell is a pentium 4 HT 2.8 ghz :-D

cheers for your help btw

---

