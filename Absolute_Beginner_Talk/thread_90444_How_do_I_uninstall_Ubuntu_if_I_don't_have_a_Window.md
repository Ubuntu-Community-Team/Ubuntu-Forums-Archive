---
title: "How do I uninstall Ubuntu if I don't have a Windows disk?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by Schmoopie on 2005-11-15
I've got a similar question with one addition.  I would like to get rid of Ubuntu from my dual boot system (I just want to get rid of it, and put it back on later if I like), but I do not have a Windows disk for my laptop to take care of fixing the boot.  My laptop is rented through the university, but our tech support staff are Nazi's, and frown on anything other than what was on the laptop when they gave it to us.  

I tried just deleteing the Ubuntu partitions with partition magic, but there was still GRUB on the system, and when I restarted, it had an error and locked up - obviously if Ubuntu wasn't there to be on the list.  So I ended up putting Ubuntu back on.  I would just like to go back to plain old Windows.  HELP!!

---

### Post by aysiu on 2005-11-15
I think you should just ask the university tech support if they can lend you a Windows CD so you can repair your Windows installation. Frankly, you shouldn't have been toying with an installation on a rented system if you didn't know how to return it to its original state, but what's done is done, I guess.

---

### Post by Schmoopie on 2005-11-15
Our laptops are essentially ours - the techsupport reformats the entire laptop when we turn them in at the end of our two-year lease.  That is why some of us goof around with them.  For whatever reason, our tech support is very unreceptive of anyone who might appear to know more than they regarding computers.  Nine times out of ten, the tech. support staff doesn't really have any technical background, but are students that got on the job training.  I've inquired before for help with Ubuntu, but got a very snotty lecture with the general idea being, "We know what is best for your laptop, even if we can't give you any proof or reason why."  I will ask though for a Windows CD (they made us throw out the copies that came with the laptops at the start of our lease), but I doubt I'll get any assistance.  

Kuecker a.k.a. Schmoopie

---

### Post by Kvark on 2005-11-15
If they are anything like the tech guys was at my high school then mess up the whole hard drive and ask them for help, they'll go "wtf, it doesn't even boot... oh well I'll just reformat it" and give you a fresh Windows install.

---

### Post by quietglow on 2005-11-15
If you want to zap GRUB off and you have an XP disk: restart with disk in and choose the "recovery mode." At the command line type: fixmbr

That'll rewrite the boot area with XP stuff.

---

### Post by Rackerz on 2005-11-15
[QUOTE=quietglow]If you want to zap GRUB off and you have an XP disk: restart with disk in and choose the "recovery mode." At the command line type: fixmbr

That'll rewrite the boot area with XP stuff.[/QUOTE]

Thats exactly what i did when getting rid of Mepis GRUB boot loader.

---

### Post by Chayak on 2005-11-15
You can also use a live linux CD go into the command line with root and type ```
install-mbr /dev/hda (should be the right drive though I've seen some newer laptops with serial ata use sda)
``` It will point the mbr to the first partition on the drive.

---

### Post by xequence on 2005-11-15
I think some windows versions can make boot floppies that might work to get rid of grub.

And yea, it does get annoying that grub messes up if there is only one OS.

---

### Post by Chayak on 2005-11-15
[QUOTE=xequence]I think some windows versions can make boot floppies that might work to get rid of grub.

And yea, it does get annoying that grub messes up if there is only one OS.[/QUOTE]

Grub works fine for me.  I use it for different kernel versions when testing and I've had only one a number of times.

---

### Post by Darrin on 2005-11-15
I tried recovery mode in winxp, but it kept asking for a administrative password. I dont remember ever putting one in. So am I stuck there? 

(Im keeping ubuntu, but trying to remove linspire grub on a second computer)

---

### Post by davmac on 2005-11-15
You could try downloading the Ultimate Boot CD from [www.ultimatebootcd.com](www.ultimatebootcd.com) and starting up the disk tools. Within there you'll find Ranish Partition Manager. As well as being able to faff about with partitions you can also use it to restore the MBR.

Hope this helps,

Dave Mac

BTW: I always keep a copy of Ultimate Boot CD and Knoppix close to hand. so far (touch wood) they've managed to get me our of every corner I painted myself into.

---

### Post by cbudden on 2005-11-15
If you can get a windows 98 boot floppy/cd , you can do a fdisk /mbr to fix the mbr.  [www.bootdisk.com](www.bootdisk.com) has them i think.

---

### Post by bryan986 on 2005-11-15
[QUOTE=Darrin]I tried recovery mode in winxp, but it kept asking for a administrative password. I dont remember ever putting one in. So am I stuck there? 

(Im keeping ubuntu, but trying to remove linspire grub on a second computer)[/QUOTE]

Can you just press enter without entering a password?

---

### Post by Schmoopie on 2005-11-15
I've got a few queries about the past entries:

[QUOTE=Darrin]I tried recovery mode in winxp, but it kept asking for a administrative password. I dont remember ever putting one in. So am I stuck there? [/QUOTE]

I think the last time I messed up my laptop, & the tech support reimaged the C:\ drive, I believe they changed the administrator password to my current login.  (But this could change, shady tech. support and all.)  I'd like to know how it turns out, I may be able to get a windows XP disk and fix the boot, but I don't want to get stuck half-way with an in-operable OS and no known admin password.  
-----------------------------------------------

[QUOTE=Chayak]You can also use a live linux CD go into the command line with root and type

```

install-mbr /dev/hda (should be the right drive though I've seen some newer laptops with serial ata use sda)
```

It will point the mbr to the first partition on the drive.[/QUOTE]

So just to clarify - I can tell grub to only go to Windows (the first partition) this way?  What if I wanted to delete the Ubuntu partition thereafter, will GRUB still have errors in starting since there would only be Windows left on the system?  Also, does this work reliably?
-----------------------------------------------

[QUOTE=devmac]You could try downloading the Ultimate Boot CD from [www.ultimatebootcd.com](www.ultimatebootcd.com) and starting up the disk tools. Within there you'll find Ranish Partition Manager. As well as being able to faff about with partitions you can also use it to restore the MBR.[/QUOTE]

I may try this one, it sounds (from what I hear) to be the easiest (and safest?) way to go about restoring the boot record.  I assume it will then get rid of GRUB as well?
-----------------------------------------------

Thanks for the help!  I love the Ubuntu community, and how easy it is to get answers - keep up the good work!

Kuecker a.k.a. Schmoopie

---

### Post by Schmoopie on 2005-11-15
[QUOTE=davmac]You could try downloading the Ultimate Boot CD from [www.ultimatebootcd.com](www.ultimatebootcd.com) and starting up the disk tools. Within there you'll find Ranish Partition Manager. As well as being able to faff about with partitions you can also use it to restore the MBR.[/QUOTE]

Are you using the Windows ultimate boot cd, or the one referenced in your link?  The leads to a page that mentions a windows version and a link to it therein.  

Schmoopie

---

### Post by Darrin on 2005-11-15
[QUOTE=bryan986]Can you just press enter without entering a password?[/QUOTE]
Tried it but it didnt work.

---

### Post by TeraDyne on 2005-11-15
[QUOTE=Darrin]I tried recovery mode in winxp, but it kept asking for a administrative password. I dont remember ever putting one in. So am I stuck there? 

(Im keeping ubuntu, but trying to remove linspire grub on a second computer)[/QUOTE]

If there's no Admin pass, just hit enter. It should let you through.

---

### Post by sjh on 2005-11-15
The default password for admin in windows xp is blank.  Just hit return.

---

### Post by Darrin on 2005-11-15
Ok Ill try that later on. Thanks.

So basically, go to recovery mode, for admin password just hit enter, then type fixmbr?

---

### Post by Chayak on 2005-11-16
[QUOTE=Schmoopie]I've got a few queries about the past entries:



I think the last time I messed up my laptop, & the tech support reimaged the C:\ drive, I believe they changed the administrator password to my current login.  (But this could change, shady tech. support and all.)  I'd like to know how it turns out, I may be able to get a windows XP disk and fix the boot, but I don't want to get stuck half-way with an in-operable OS and no known admin password.  
-----------------------------------------------



So just to clarify - I can tell grub to only go to Windows (the first partition) this way?  What if I wanted to delete the Ubuntu partition thereafter, will GRUB still have errors in starting since there would only be Windows left on the system?  Also, does this work reliably?
-----------------------------------------------



I may try this one, it sounds (from what I hear) to be the easiest (and safest?) way to go about restoring the boot record.  I assume it will then get rid of GRUB as well?
-----------------------------------------------

Thanks for the help!  I love the Ubuntu community, and how easy it is to get answers - keep up the good work!

Kuecker a.k.a. Schmoopie[/QUOTE]


If you do the install-mbr it will remove Grub and install a mbr that points to the first partition.

---

### Post by Darrin on 2005-11-16
[QUOTE=sjh]The default password for admin in windows xp is blank.  Just hit return.[/QUOTE]
It did work. I thought I tried that before and it didnt work for me.....:???:  Maybe I did a typo

---

### Post by zerhacke on 2005-11-16
[QUOTE=cbudden]If you can get a windows 98 boot floppy/cd , you can do a fdisk /mbr to fix the mbr.  [www.bootdisk.com](www.bootdisk.com) has them i think.[/QUOTE]
No, this wil not fix the MBR.  This will wipe out the MBR and give you no bootloader at all.

---

### Post by davmac on 2005-11-17
[QUOTE=Schmoopie]Are you using the Windows ultimate boot cd, or the one referenced in your link?  The leads to a page that mentions a windows version and a link to it therein.  

Schmoopie[/QUOTE]

I downloaded the zipped up iso file, unzipped it and burnt it onto a cd. There a mix of windows, dos and linux stuff on the cd. The direct url for the file is [http://www.planetmirror.com/pub/ubcd/3.3/ubcd33-basic.zip](http://www.planetmirror.com/pub/ubcd/3.3/ubcd33-basic.zip)

Hope this helps,

Dave Mac

---

### Post by wh0rd on 2005-11-19
[QUOTE=Chayak]You can also use a live linux CD go into the command line with root and type ```
install-mbr /dev/hda (should be the right drive though I've seen some newer laptops with serial ata use sda)
``` It will point the mbr to the first partition on the drive.[/QUOTE]

I used Ubuntu Live Cd and typed in that command but it said that:

root@ubuntu:/home/ubuntu # install-mbr /dev/hda
bash: install-mbr: command not found

I searched for install-mbr, i couldn't find it.

---

### Post by Schmoopie on 2005-12-09
[QUOTE=wh0rd]I used Ubuntu Live Cd and typed in that command but it said that:

root@ubuntu:/home/ubuntu # install-mbr /dev/hda
bash: install-mbr: command not found

I searched for install-mbr, i couldn't find it.[/QUOTE]

On a whim, I tried the ```
install-mbr /dev/hda
``` code in my installed version of Ubuntu, and got the same results, are you sure that you are using the Live CD, like recommended?

Schmoopie

---

