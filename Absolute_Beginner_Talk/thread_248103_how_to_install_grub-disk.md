---
title: "how to install grub-disk ???"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by spoj on 2006-08-31
OK, I've done some searches, and even found the "homepage" of this grub-disk package I just installed, but **nowhere** can I find any **simple** (or otherwise) documentation on how to *use* it!

This seems to be a problem with a lot of little useful Linux packages - they make HUUUUUGE assumptions that everyone has decades of experience and instantly know how to "do things" !

So...  how do I get the "grub-disk" (grub-on-a-floppy-image) actually **onto** a floppy disk ?!?!??  There's no README / doc / info or man page in the package, just some changelogs and 2 gzipped images.  So how do I get either the iso or ext2fs image on a floppy ?   It's probably trivially easy (I suspect something like using the "dd" util), but I don't want to spend 2 hours reminding myself how to use dd - last time I looked was 20 years ago!

Sorry for the rant, but anyone connected with writing / producing / packaging that little package could have written a single sentence in a text file, but I've now spent an hour scanning for some hint and not found it!  (I suppose I am now much more informed on the various means of recovering a grub setup after the various ways of losing the grub setup, but...  :-(  )

---

### Post by TFX360 on 2006-08-31
Why would you want it on a floppy? Live-CD can do all that for you. What is wrong why you should need this.

---

### Post by spoj on 2006-08-31
Thanks TFX, I know :D - and in fact I'll try getting access to my grub setup etc from the live CD later...

But there's this little floppy image, which from the description sounds like a useful floppy to have, but there's no clue with the package on how to use it! [-( 

I'm sure if I search with enough combinations of "image" "floppy" "write" and other keywords, I'll eventually find something that'll clue me in, but it just kinda aggravates me that there's a package without any instructions on how to *use* it !  Look - I just found the Ubuntu page on it, where you can even see the HUUGE list of files (ok - just 5 ;) ) - see [http://packages.ubuntulinux.org/hoary/admin/grub-disk](http://packages.ubuntulinux.org/hoary/admin/grub-disk)

... but **how** do I get either image onto a floppy ? I assume assume a .iso is a CD image (only?) so that's pretty pointless, as the .iso is 400K - as you say, far better to use the Live CD.  So if it's the .ext2fs file, which is 1.4 Mb when un-gzipped, **how** do you write a floppy image to a floppy disk ???

When I do find this out, I think I may have to raise a "bug" on this, or even  :shock:  write the README file and get it added to the package!

---

### Post by bodhi.zazen on 2006-08-31
Try this:
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

---

### Post by nickpaton on 2006-08-31
And this:

[http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy")

---

### Post by spoj on 2006-08-31
Thanks Nick and Bodhi (very useful references for other grub stuff), but ...

I'm actually asking how to get the grub-disk image onto a floppy, as the package itself doesn't say! :confused: 

So let's cut out all the extra "guff" - I have this file:

[INDENT][FONT="System"] grub-0.97-i486-pc.ext2fs[/FONT][/INDENT]

which is 1.4Mb in size, and apparently a floppy ***image***, so how do I get it on the floppy ?

---

### Post by bodhi.zazen on 2006-08-31
[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

---

### Post by nickpaton on 2006-08-31
Apologies spoj for not reading the post properly.

yeah I see your problem, and no I unfortunately don't know.

Will continue to watch with interest to see if someone has the answer.

Good luck!

---

### Post by bodhi.zazen on 2006-08-31
If you must:

Put floppy into drive.
do not mount

```
sudo dd if=grub-0.97-i486-pc.ext2fs of=/dev/fd0 bs=1024 conv=sync ; sync
```

---

### Post by jediborger on 2006-08-31
Ok so it sounds like you have a floppy image you want to put on a disk right? Ok the command for that is:

*I recommend formatting the floppy first using the command

gfloppy

dd if=*the_file_name* of=/dev/fd0

This will write the image to the disk. Also you can make a grub disk using the grub package already installed in ubuntu with these instructions:
[http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy")

Hope this helps.

---

### Post by spoj on 2006-08-31
There you are! I knew it'd be a "dd" command...

I'll try out the examples tomorrow (too late now).

But still - why wasn't this **in** a README in the package!?

Thanks all  - later!

---

### Post by TFX360 on 2006-08-31
> **spoj said:**
> There you are! I knew it'd be a "dd" command...

I'll try out the examples tomorrow (too late now).

But still - why wasn't this **in** a README in the package!?

Thanks all  - later!

Lol, spoj,

To document or not to document, makes root feel root again (like 15 years ago). w00t. Something only "we" know. Like "for Human Beings" means you automatically know copying a simple image to a disk is simply using ```
sudo dd if=grub-0.97-i486-pc.ext2fs of=/dev/fd0 bs=1024 conv=sync ; sync
``` maybe Dr. Spock can find the logic here. A well I don't have a disk drive. So probably haven't got the need for it.

Can make an iso of a dvd / cd though with dd, never done it though. Sound handy.

Rehehehealy,


I'm going to:


```
sync; sync; sleep 10; sudo shutdown -h now
```


Byebye.

---

### Post by spoj on 2006-09-10
OK, time to conclude this thread...

This appears to be the way to "use" or install or setup the **grub-disk** package:-[LIST=1]
[*]Insert a scratch floppy disk (do not mount)
[*]Uncompress the ext2fs package:
```
sudo gunzip /usr/share/grub-disk/grub-0.97-i486-pc.ext2fs.gz
```
[*]Write image to floppy:
```
 sudo dd if=/usr/share/grub-disk/grub-0.97-i486-pc.ext2fs of=/dev/fd0 bs=512
```
[*]Mount floppy and [FONT=System]cd[/FONT] to grub area on floppy:
```
mount /media/floppy
cd /media/floppy/boot/grub
```
[*]Write grub stage1 to boot sector:
```
sudo grub
grub> root (fd0)
grub> setup (fdo)
```
This will eventually report a "disk write error", but still seems to do the job, and also reports the stage1.5, stage2 and menu.lst files that are present on the floppy.[/LIST]**However:** I have to say, now I've got it to work, I *really don't think it's worth the effort* !   :rolleyes:

Far better is almost certainly either to use the Ubuntu Install / Live CD, or if you need a grub floppy, probably [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") is a far better option. Now the floppy image of *this]* includes the grub loader already in the image, and so it literally just has to be copied to a floppy as above. However it is so comprehensive that it is rather painful using from a floppy disk :-)  Far better to use the CD image instead... I suppose it's quicker to boot than the live CD.

So thanks for the hints and suggestions from all posters; I got the information in the end!

---

### Post by catlett on 2006-09-10
Just out of curiousity, did you reboot to the floppy disk yet? Did your computer acknowledge it and boot or did you get an error "no filesystem found?" Just curious because grub floppies are a pain and if this worked it is pretty simple (believe it or not).

---

### Post by spoj on 2006-09-10
Didn't my last post imply that? ;-)

Anyway - yes - the steps for installing grub-disk give a bootable floppy, and the super-grub-disk is available as a floppy, CD or flashdisk image; I tried the floppy image and it is a bootable grub floppy straight from the image.

---

### Post by catlett on 2006-09-10
Just wanted to make sure because aloy of times it doesn't boot. I hav a couple of grub how tos and wanted to see if this was worth posting in one of them.
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

---

### Post by bodhi.zazen on 2006-09-10
> **catlett said:**
> Just wanted to make sure because aloy of times it doesn't boot. I hav a couple of grub how tos and wanted to see if this was worth posting in one of them.
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

I would second the idea of a GURB how-to on the Ubuntu site. Willing to collaborate.

Here are two sites I use, you probably know them both:
[Geodsoft How-to dual boot](http://geodsoft.com/howto/dualboot/grub.htm)
[Linux Journal GRUB](http://www.linuxjournal.com/article/4622).

---

### Post by catlett on 2006-09-11
> **bodhi.zazen said:**
> I would second the idea of a GURB how-to on the Ubuntu site. Willing to collaborate.

Here are two sites I use, you probably know them both:
[Geodsoft How-to dual boot](http://geodsoft.com/howto/dualboot/grub.htm)
[Linux Journal GRUB](http://www.linuxjournal.com/article/4622).

I am all for it. It is definately an ongoing issue. I'll make a short list of areas to cover and I'll pm you tonight. Any one else is welcome to input.

---

