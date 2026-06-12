---
title: "can't install Ubuntu as OS after downloading it to a CD"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by david bexhall on 2008-02-05
Hi

I downloaded Ubuntu 7.10 today and chose CD drive as the destination. It seems to have gone onto the CD OK (695MB), but Windows XP says it can't open the file.  How do I install Ubuntu?

TIA,

Dave

---

### Post by mike555 on 2008-02-05
You should save it to the desktop , then burn it as an .iso (not data) then you can use it

---

### Post by SPr on 2008-02-05
[Installation instructions](https://help.ubuntu.com/community/Installation)

---

### Post by LowSky on 2008-02-05
Windows cannot open the file. the file is an ISO which is a image of file. You need to create a bootable CD..  Follow these instructions...then reboot the computer and maake sure your computer can boot fromthe cdrom drive.

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by Nythain on 2008-02-05
lol... there seems to be a lot of that going around lately...

---

### Post by david bexhall on 2008-02-05
Thanks to SPr and LowSky for your suggestions. I've moved the .iso file and downloaded Infrarecorder, but the OK button on Infrarecorder is grayed out, so no joy.

There's only 128 MB of RAM on the PC I'm using, so less than the recommended minimum, however Windows XP runs fine.

I'm beginningto think Linux is as much of a pain in the backside as Windows.  Better the pain you know than the pain you don't.......

---

### Post by (((X))) on 2008-02-05
> **david bexhall said:**
> 
I'm beginningto think Linux is as much of a pain in the backside as Windows.  Better the pain you know than the pain you don't.......

Much less pain in the backside if you know how to use the terminal:)

---

### Post by stoodleysnow on 2008-02-05
But how do you know,and have a balanced opinion unless you've tried them both. Giving up at burning the CD is like saying 'I can't swim' because you got your toes wet.

Suggestion:
get more RAM. 512MB would not cost too much.
Use burnatonce to burn the ISO file [www.burnatonce.net](www.burnatonce.net)
Backup all your files and work
Reboot and press DEL, F2 or whatever. Make sure the boot order has CDROM before HDD0 or C
Put the Ubuntu CD in the drive
Reboot.
Enjoy.:)

---

### Post by stoodleysnow on 2008-02-05
> **(((X))) said:**
> Much less pain in the backside if you know how to use the terminal:)

Not all people like to use command lines. Many of us have only ever known and used GUIs.
PLEASE BEAR THAT IN MIND.

---

### Post by (((X))) on 2008-02-05
I think commandline is a very important part of linux, like it or not.
I understand, not everbody feels the same.
Ubuntu is good for both.:) imho

---

### Post by oldos2er on 2008-02-05
> **david bexhall said:**
> Thanks to SPr and LowSky for your suggestions. I've moved the .iso file and downloaded Infrarecorder, but the OK button on Infrarecorder is grayed out, so no joy.

There's only 128 MB of RAM on the PC I'm using, so less than the recommended minimum, however Windows XP runs fine.

I'm beginningto think Linux is as much of a pain in the backside as Windows.  Better the pain you know than the pain you don't.......

 The Live CD requires a minimum 384 MB RAM to run. You might want to try a lighter distro like DSL or Puppy.

---

### Post by yaknowwat on 2008-02-05
Ubuntu tends to be heavier on RAM than windows XP because of all the extra stuff.
though linux is far more efficient with RAM and CPU than any windows version.

XP uses 200 MiB of RAM on boot but at least 50MiB is unproperly handled junk.

Ubuntu uses 180MiB but thats the full thing (on first boot)
The LiveCD requires at least 320 MiB RAM though there is the alternative one.

With XP you can go and disable services etc and make it so windows use 80-120 MiB on boot with around 10 MiB junk.
For Ubuntu you can't do that very well if you want to keep nice usuability.

Sure you can switch to Xfce or Fluxbox Desktop Environments and save around 50 MiB of RAM but it still wont help as like I said Linux doesn't leak like Windows does so digging into swap is far slower than in windows (which will digg into swap even if you don't need to and cause unneeded load on your hard drive shortening its life.)

Windows Handles Graphics horribly tons of memory leaks appear in windows when it comes to graphics handling.

basically if you wanted Ubuntu you would want a 512MiB RAM stick or something.

There is a solution like puppy linux which would run nicely under 128 MiB but it not what I'd call a competitor to Windows XP in the usuability (win 98 or 2k yes i can call it a competitor) realm faster yes but easy to fully set-up unless you get Muppy Edition would probably be a pain for a normal person.

Puppy linux :
[http://puppylinux.org/user/viewpage.php?page_id=1](http://puppylinux.org/user/viewpage.php?page_id=1)

Muppy latest : 
[http://murga-linux.com/puppy/viewtopic.php?search_id=2139779599&t=25966](http://murga-linux.com/puppy/viewtopic.php?search_id=2139779599&t=25966)
Other puppy deriatives : 
[http://murga-linux.com/puppy/index.php?f=35](http://murga-linux.com/puppy/index.php?f=35)

People thinking command lines are hard there are lots of cammands for the linux command line but only a few you really need to use and they tend to be eaier than using a GUI thing.
All a GUI really does is communicate with the Command line and create visuals.

---

### Post by david bexhall on 2008-02-05
> **stoodleysnow said:**
> But how do you know,and have a balanced opinion unless you've tried them both. Giving up at burning the CD is like saying 'I can't swim' because you got your toes wet.

Suggestion:
get more RAM. 512MB would not cost too much.
Use burnatonce to burn the ISO file [www.burnatonce.net](www.burnatonce.net)
Backup all your files and work
Reboot and press DEL, F2 or whatever. Make sure the boot order has CDROM before HDD0 or C
Put the Ubuntu CD in the drive
Reboot.
Enjoy.:)
Well, StoodleySnow, thanks for the tip about burnatonce, as  I now have what appears to be a functioning Ubuntu CD.  So I won't take issue with you about your analogy of learning to swim.  Let me just say that for me a computer is a tool, not a hobby, and I just want it working quickly and simply.
What a lot of fascinating jargon there is on this forum, most of it over my head---if this is for absolute beginners I'm glad I didn't try the advanced forums.  Is a command line the same thing as we used to have to use with MS-DOS in the days before Windows? (You'll gather that I'm getting on a bit)

---

### Post by SPr on 2008-02-06
> **david bexhall said:**
> ... Is a command line the same thing as we used to have to use with MS-DOS in the days before Windows? (You'll gather that I'm getting on a bit)

It is exactly that. 

Thanks for the thanks :-/ (I know what I mean :))

---

### Post by jken146 on 2008-02-06
You should be able to run Ubuntu OK with 128MB of RAM, although if you find it too slow I'd suggest Xubuntu.

The Ubuntu Live CD requires more RAM than you have, so you'll need the Alternate CD [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) (tick the box at the bottom).


You don;t really need to use the command line for day to day use, so don't worry about it too much.  Don't be afraid of it either.

---

### Post by LowSky on 2008-02-06
the linux command line is simular to DOs but uses differnet commands..

also remember that Linux isn't a direct replacement to Windows.
Linux has replacement version to many peices of software, like OpenOffice can repleace MS Office almost entirely.

Just keep that in mind...

And you will need to learn some command line stuff, as the Graphic interface is good but can make some simple stuff confising

if you cant get the install working Send me a provate message and I will try to get you up and runnign asap.

---

### Post by yaknowwat on 2008-02-06
linux commands are far stronger than windows commands.

Yet at the same time simpler in a form.

You wont need to use the command line after everything is set-up actually
just to install some tarball apps but most tarballs have deb packages which auto installl.

People suggesting Xubuntu for 128 MiB of RAM that isn't a wise choice per say because in truth Xebuntu only saves about 50MiB of RAM compared to Ubuntu so the recommended requirement for it should be around 256 MiB RAM.

---

