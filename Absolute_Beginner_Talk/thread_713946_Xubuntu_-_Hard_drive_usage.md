---
title: "Xubuntu - Hard drive usage//"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by mltom on 2008-03-03
Just installed Xubuntu & thought I was doing okay, then noticed I'm only using about 30Meg of my hard drive .. (its at least 200meg, I think)

How do I claim the whole hard drive now?

The partition method I chose during installation was: Resize IDE3 master, partition #1 (ide3) & use free space.............................

tks
tom

---

### Post by Yoke &amp; Chung on 2008-03-03
You can boot your system using the Xubuntu LiveCD. The live CD contains Gparted (Named as Partition Editor) under Applications--> System.

You can delete the other partitions, and expand the Xubuntu partition using gparted. Be careful though, do not delete the wrong partition, and the partition expansion will take a very long time.

---

### Post by owbizi on 2008-03-03
Well, if the partition limit was set wrong, then you can resize it, using some program, like gparted.

edit: damn, posters are *really* fast here!

---

### Post by mltom on 2008-03-03
Xubuntu boots off my hard drive now.      What would be the 'terminal' command to have 'gparted' expand the existing partition to use the full hard drive?

tks
tom

---

### Post by taurus on 2008-03-03
You cannot resize your harddrive while you are still using it.  It has to be done from the LiveCD.  So, if you don't have Xubuntu LiveCD handy anymore, then you should consider using GParted LiveCD instead.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by mltom on 2008-03-03
I'v booted off my Xubuntu LiveCD & there are no options for 'application',-->'system',,nor are there any selection for 'gparted'.

Here are the selections on the CD:
  
  install in text mode
  OEM install
  install a command line
  install an LTSP server
  check CD for defects
  Rescue a broken disk
  memory test
  Boot from first hard drive

Still try to expand my existing partition ,,,,,,,,,,,,,,,,,,thanks again for your reply.

tom

---

### Post by michaelzap on 2008-03-03
AFAIK, the Xubuntu installer CD is not a Live CD (at least I've never seen one that is). A Live CD allows you to boot up the operating system without installing it. The Ubuntu desktop CD is a Live CD, but the Xubuntu one isn't.

So either download the Gparted Live CD or the Ubuntu Live CD and use it. The Gparted CD is a smaller download and designed to do specifically what you want to do, so that's probably the easiest bet. Plus the Ubuntu Gutsy Live CD has higher hardware requirements than you might meet (given that you're using Xubuntu, which is less demanding).

---

### Post by taurus on 2008-03-03
> **mltom said:**
> I'v booted off my Xubuntu LiveCD & there are no options for 'application',-->'system',,nor are there any selection for 'gparted'.

Here are the selections on the CD:
  
  install in text mode
  OEM install
  install a command line
  install an LTSP server
  check CD for defects
  Rescue a broken disk
  memory test
  Boot from first hard drive

Still try to expand my existing partition ,,,,,,,,,,,,,,,,,,thanks again for your reply.

tom

You have the alternate CD, not the LiveCD--desktop CD.

---

### Post by mltom on 2008-03-03
Please don't give up on me;         I now know how to find gparted program on the internet, but my Xubuntu pc does now have a writable cd, just read.
So I go to my XP pc find the file, do a download via 'open' & it goes to my 'temporary folder' on my XP pc.            But I can never find the file when I go to burn a cd.       Next I download via 'save' to a folder.     Then I burn a cd by dropping the file onto the cd.

Next I take the cd over to my Xubuntu pc & reboot.   ZIP happens, Apparently the file I burned to the cd is not bootable.

Now what?              Guess I'm starting to get tired.           Please help again.

tom

---

### Post by bodhi.zazen on 2008-03-03
You have to "burn" the iso to disk, not copy a file or program.

Try downloading and buringin the gparted CD:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

[Download gparted live CD](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by FrozenFox on 2008-03-03
Apologies, it's a little hard to understand you, so take this advice with a grain of salt. It sounds like you are burning the iso file to the cd itself, which is not correct. You need to burn the cd iso as an image. Perhaps an explanation of sorts will help understand:

An .iso file contains all of the contents of a cd packaged up into a single file, essentially.

This is what you are doing: If you copy the .iso file to a cd and burn it, what you are basically doing is putting a file -containing- the contents of one cd on ANOTHER cd. You end up with a cd within a cd within a single file. Your machine doesn't know what to do with that when you reboot. Ie, you are copying a compressed CD file onto another cd.

This is what you need to do: If you use a program set to burn a cd in the form of an .iso image, the program (like Nero for instance) will read what's contained within the .iso in order to structure and burn a cd containing the files it's supposed to. Ie, it will open the .iso, see how the actual CD is supposed to be, and then create the cd from this information.

If you (or anyone else clueless with similar issues) still don't understand, let me give a really stupid analogy: Say you know a kid having a birthday and you set out to give them a good party (comparison to running your cd). You want to decorate their house, first and foremost. To do so, you go out and buy a whole lot of party decorations and put them in the box (the box filled with stuff is our .iso file). What you've just tried to do is walk into the kid's house and set the box of decorations in the middle of the room then called the kid home for his party (it sucks! dont copy an iso file to cd. that's not correct.). What you should've done is have someone decorate the room from the stuff that's in the box and then called the kid home (ie have a program read the iso and create a cd from it).

[http://theos.in/windows-xp/how-do-i-burn-iso-images-to-a-cd-using-windows-xp2000/](http://theos.in/windows-xp/how-do-i-burn-iso-images-to-a-cd-using-windows-xp2000/)

This web page might help you get the program and info to do it the right way ;)

(Note: Don't take offense, the reason for the thorough and silly explanation is this: completely understanding what you're doing is far more important than simply following directions.)

---

### Post by mltom on 2008-03-03
bodhi.zazen,,,,,,,,,,,,,,,,,,,,,

my issue now is on my XP pc when I try to retrieve gparted it gives me a option of 'open' or 'save to disk'.
If I choose 'save to disk' , it won't work if I burn the file to a cd.
If I choose 'open', XP puts gparted into 'temporary folder', which I cannot locate when the download is finished.

I'v tried several times all during this day & have received many messages from your team trying to help me. Thanks.
I guess I don't know how to download this program. I'v never had trouble before & I'm 65 yrs now.
I'm at the point where I don't want to bother you guys anymore. I hate wiping out my Xubuntu install which is working great, but at least I would use the 'entire disk option', next time.

thanks again
tom

---

### Post by FrozenFox on 2008-03-04
Ok, lets try this then.

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

Follow the instructions on this web page starting at ISO Recorder Power Toy (Freeware) and stop before the Nero section (IE follow steps 1-5). It includes pictures you can click on and such to help you.

Remember you must [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)  visit the web page given and download/install the appropriate utility first before the 5 steps. In your case, it's probably ISORecorder V2 - for Windows XP SP2 and Windows 2003 (including 64-bit OS).

---

### Post by bodhi.zazen on 2008-03-04
It is no bother, actually I had the same problem when I started.

It is as FrozenFox explained. When you make a CD, there are different types of CD's, for example a data CD where you save pictures or text files, vs a music CD.

So, starting at the beginning, download the iso and save it to disk. 

Here is a direct link :

[gparted-livecd-0.3.4-11.iso](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-11.iso?modtime=1197927842&big_mirror=0)

Save this iso to say your desktop as "gparted-livecd-0.3.4-11.iso" (without quotes)

================================================

OK, now you need to make a bootable CD from that iso.

What CD burning software are you using ? You should be able to right click the file and select something like *burn iso to CD* (rather then a data CD).

See this link :

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If your software does not do this , there are several free options

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by mltom on 2008-03-05
Thank You, Thank You, Thank You,
Thank You, Thank You, Thank You,
Thank You, Thank You, Thank You,
Thank You, Thank You, Thank You,

Hopefully my next question, I won't be so hard to comprehend...... Actully I've never burned a bootable cd before.

tom

---

