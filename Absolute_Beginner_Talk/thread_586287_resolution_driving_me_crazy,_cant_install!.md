---
title: "resolution driving me crazy, cant install!"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Kompresor on 2007-10-22
okay. im no computer dummy- fluent at windows, can find my way around a mac.

when i boot from cd, i try to change the resolution using the f4 prompt, it doesnt have my resolution listed, so i chose the 1400x1000 or something close to that, but when it boots, i'm stuck at 860x680 or something stupid like that. i cant change it, but i figure if i install it, i could update & install my nvidia graphics driver and stuff.

so i go to install it, and because of the resolution being stuck at 860x680 or whatever it is,  the install window is bigger than my  desktop area, and i cant click the "next" button. isnt that some stuff? 

any fixes on this?

i'm running an HP compaq with AMD 64 single core, 2.2ghz. nvidia GeForce 6150LE graphics card integrated into the motherboard just an average, inexpensive computer. i made my own *.iso of ubuntu feisty fawn and burned it, then did all the proper memory tests to make sure all the data was kosher. 

if i could just get it installed, maybe i could work with it better. oh and i beleive the reason is wont show up  on a normal 860x680 resolution monitor is because i have a 19" widescreen, and i dont think that resoluion setting is widescreen oriented.

---

### Post by Perfect Storm on 2007-10-22
See if this is something you can use:
Open the terminal (Applications tab ---> Accessories ---> terminal)

and type;
```
gksudo nvidia-settings
```

---

### Post by Kompresor on 2007-10-22
thanks....i'll try it....will respond in five minutes or less.....

---

### Post by forestpixie on 2007-10-22
also if that doesn't work try to hold down Alt and then click and drag the window - I've been looking because I've seen this before

Edit - I think if you use the alternate cd you don't get a GUI - it's a text based installer

---

### Post by Kompresor on 2007-10-22
> **Artificial Intelligence said:**
> See if this is something you can use:
Open the terminal (Applications tab ---> Accessories ---> terminal)

and type;
```
gksudo nvidia-settings
```

okay, when i used the terminal, it did nothing when i wrote in that code. literally. just had another command line right below it, like when ur in windows command prompt and just hit the enter button. 

and holding alt worked great! but now another roadblock: 

i've got two hard drives. both have data i dont want erased. 
hard drive one has windows recovery software in a 9 gig partition, then 150 gigs i guess is just storage and OS stuff.  

hard drive number two just has about 305 gigs of movies  on it.  its a 320 gig hard drive.

i'm looking at the partition editor, but not exactly sure what to do. am i able to make a say- 30 gig partition on the 150 gig space on hard drive #1, and then the 256 swap partition?  or will adding those partitions erase everything on there, anything on the 150gig paritition and the 9 gigs of windows recovery software? 


*sigh* i just really wanna see how this linux thing goes.....

---

### Post by Kompresor on 2007-10-22
[IMG]http://img90.imageshack.us/img90/8251/screenshotnj0.png[/IMG]

see, this is what i've got going on.....i've got the box opened up to edit that 150gig partition, and i changed the name to /media/sda3 from /media/sda1


...am i totally lost here?

---

### Post by forestpixie on 2007-10-22
you can resize partitions with the installer partioner - from waht you say you don't have windows installed - is that right? It seems to be the thing to make sure a drive's defragged before you resize it. What you're looking to do is resize the original drive - then with the unallocated space create a new partition which ubuntu can live on.

I personally use a gparted livecd, which you burn as an iso and boot with and do the partitioning separately - [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
before you install.

You can do it with the install partitioner obviously if you so wish.

Make sure you've got a backup of anything you really don't want to lose.

---

### Post by forestpixie on 2007-10-22
you're doing it the manual way - have you used the partitioner to resize, because you need to do that first - as it is I think you'll just lose all that partition, not sure though :(

once you've resized the partition then you will have unallocated space in which to create a new partition -  THEN you need to change the edit partitioner to file type ext3 and mount point /

does that make sense - if not say so :)

---

### Post by realvz on 2007-10-22
just folo this and this may help

goto terminal
and type
sudo gedit /etc/X11/xorg.conf

in the xorg.conf file

it should be something like this
Section "Screen"
	Identifier	"Screen0"
	Device		"S3 SuperSavage"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection	"Display"
		Depth	1
		Modes	"1024x768"
	EndSubSection

concentrate on this piece
[B]SubSection	"Display"
		Depth	1
		Modes	"1024x768"
	EndSubSection
[/B]

and type 
virtual 1024 768 
just below "Depth " line...if you have multiple...enter this multiple times. and then restart x
by pressing Alt+ctrl+basckspace

---

### Post by Kompresor on 2007-10-22
forestpixie- i do in fact have windows installed. heres how it is. hard drive one has windows on it. the 150gig parittion is the OS & user files. the 9 gig partition is this thing HP puts on the hard drive, a partition with recovery software if you screw up windows bad, you can simply run the software and it'll reinstall windows, and install all drivers simultaneously, in one application. 

and the 320 gig hard drive i just use a data storage. i was asking if i could chop up the 150 gig and  have two operating systems, and simply choose which one  at startup. 

dont get me wrong, i've been reading the install guides and such, so sorry for asking so many questions, but im trying to be as thorough and descriptive as possible for ya'll. 

thanks.

---

### Post by forestpixie on 2007-10-22
don't be sorry for asking questions - much better now than later - when it would be "I think I've lost windows" :)

If you've got windows this is what I would do, if you however have Vista completely ignore what I'm going to say and use the Vista disk management thing - I've never used it or seen it but I've read about it here

1 - Boot to windows and download and burn the gparted live cd that I mentioned above and burn it as an iso,( I just found it easier and more intuitive to use - I got confused by the install partitioner - didn't know what size would be which :( )


2 -  in windows clean up temp files and all that cleaning stuff you don't need to do very often in linux :), defrag a couple of times. When I did this I then turned off the page file and rebooted and defragged again (been free for nearly 6 mths - so I'm running on memory here).

3 - boot with the gparted disc - and use that to do the partitioning exercise, resize the windows partition - not the recovery one - to give enough room for Ubuntu. Format the new partition to ext3. 

4 - reboot with the ubuntu disc - when you get to the partitioning part, choose manual - pick the partition you made earlier, mount it as /

I hope that helps and don't worry about asking questions - I did the same when I was you :)

good luck

---

