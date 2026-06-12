---
title: "Can't mount dvd volume"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by timberdc on 2007-06-23
Help please! I'm trying to install my NWN DVD, and I get the message "cannot mount volume _DVD " Also. Nautilus is showing a cd drive and a DVD drive. I don't have a cd drive. Any help would be greatly appreciated!

---

### Post by isaacj87 on 2007-06-23
Okay.. I had this same problem...first off, are you using the lastest and greatest kernel??
If not, I have a solution for you...

> **Inxsible said:**
> found a solution :
1) Go to the /dev folder and look for all the cd related icons /files there. I had cdrw cdrom dvdrw and dvdrom
```
ls -l | grep dvdrw
```
The output will be somthing like this```
lrwxrwxrwx 1 root root           3 2007-06-06 17:44 dvdrw -> hda

```
2)Replace dvdrw with the ones that you found in /dev. Most likely they will all map to the same device name. For me all of them had an alias of hda

3) Then I changed the /etc/fstab entry from```
 /dev/sda /media/cdrom0 udf,iso9660 user,noauto 0 0
```
to ```
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Now I have only one drive in the new kernel.

Note the change from /dev/sda to /dev/hda ...guess -16 recognizes devices in some other way.

Tell me if this works/helps

---

### Post by timberdc on 2007-06-24
> **isaacj87 said:**
> Okay.. I had this same problem...first off, are you using the lastest and greatest kernel??
If not, I have a solution for you...



Tell me if this works/helps

Hi! Thanks for replying. I'm sorry, but I have no idea what to do with the solution you posted. What is fstab? I found my drives in the /DEV folder, but now what?
When I enter this code, nothing happens.( ? ) 
ls -l | grep dvdrw 
I'm sorry, I am totally new to this....

---

### Post by atria on 2007-06-24
Basically, ubuntu cannot automount discs with UDF filesystems automatically because of a minor bug.

The dummy method to mount the cd temporary would be:
```
sudo mount -t auto /dev/cdrom /media/cdrom
```
and browse to /media/cdrom

Also replace /dev/cdrom with your drive name.

When you're done with it
```
sudo umount /media/cdrom
```

---

### Post by timberdc on 2007-06-24
"Also replace /dev/cdrom with your drive name."

How do I do this?

---

### Post by atria on 2007-06-24
Just use /dev/cdrom then, it should default to your drive correctly.

---

### Post by timberdc on 2007-06-24
does it matter if I mount it as cd or dvd rom? Also, I'm still unclear on how to "Just use /dev/cdrom then". Is this something I need to do physically? Argghhh. This is driving me nuts! Thanks for your patience with me...

---

### Post by Malta paul on 2007-06-24
Hi, ' Sudo Fdisk -l '        Typed into the terminal, accessed from Applications>Terminal. will list your disk partitions that the system detects.  A good reference is [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) Have a read it should help -I hope
Have fun and keep asking if you still have problems ;)

---

### Post by isaacj87 on 2007-06-24
Oh I'm sorry timberdc...I should of made it a bit clearer..I'll post a better explanation a little later today. One question though...can you not mount a CD/DVD if you put one in the computer?

Also can you post of pic of what you're looking at when you stick a DVD in your computer?

thanks and I'll get back to you.

---

### Post by timberdc on 2007-06-24
> **Malta paul said:**
> Hi, ' Sudo Fdisk -l '        Typed into the terminal, accessed from Applications>Terminal. will list your disk partitions that the system detects.  A good reference is [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) Have a read it should help -I hope
Have fun and keep asking if you still have problems ;)

This is what is returned:

timber@dc1:~$ sudo fdisk -l
Password:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9553    76734441   83  Linux
/dev/sda2            9554        9964     3301357+   5  Extended
/dev/sda5            9554        9964     3301326   82  Linux swap / Solaris
timber@dc1:~$ 

I don't even see an optical drive listed. But Nautilus shows that I have a cd drive and an dvd drive, but there is no physical cd drive attached to my computer, just a dvd drive/burner

---

### Post by timberdc on 2007-06-24
> **isaacj87 said:**
> Oh I'm sorry timberdc...I should of made it a bit clearer..I'll post a better explanation a little later today. One question though...can you not mount a CD/DVD if you put one in the computer?

Also can you post of pic of what you're looking at when you stick a DVD in your computer?

thanks and I'll get back to you.

Here is a sreenshot:




When I double click on the dvd icon in file browser I get the message: "The folder contents could not be displayed"

When I double click on the cd icon I get the message: "Unable to mount the selected volume"

Thanks for your help, guys!

---

### Post by isaacj87 on 2007-06-24
Ah sweet thanks I went through the same problem...do me a quick favor..

go into terminal and type this

sudo cat /etc/fstab

(it should ask for your password)

and post your results.

---

### Post by timberdc on 2007-06-24
> **isaacj87 said:**
> Ah sweet thanks I went through the same problem...do me a quick favor..

go into terminal and type this

sudo cat /etc/fstab

(it should ask for your password)

and post your results.

Looks like this:

timber@dc1:~$ sudo cat /etc/fstab
Password:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f98dfc59-6962-47dd-917e-4abfd99dd33b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=364e1ba0-2fbf-4027-8702-49b5be50dead none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
timber@dc1:~$

---

### Post by timberdc on 2007-06-24
Bump, 'cause I would REALLY like to install my NWN without having to go back to Windows :(

---

### Post by isaacj87 on 2007-06-25
> **timberdc said:**
> Looks like this:

timber@dc1:~$ sudo cat /etc/fstab
Password:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f98dfc59-6962-47dd-917e-4abfd99dd33b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=364e1ba0-2fbf-4027-8702-49b5be50dead none            swap    sw              0       0
**/dev/hdd **       /media/cdrom0   udf,iso9660 user,noauto     0       0
timber@dc1:~$

Whoa....that last part where I bolded? I think it's incorrect. And I think we've found your problem....hopefully.

Open up terminal, type 

```
cd /dev 
```

then type (i'm assuming you have a dvdrw drive...if you don't I think you just type dvd at the end instead of dvdrw...but i'm not sure):

```
ls -l | grep dvdrw 
```

Now it should give you an output, here's mine for example:

```
lrwxrwxrwx 1 root root             4 2007-06-24 23:30 **dvdrw -> scd0**
```

See that last part? **dvdrw->scd0** that's the name of my drive (sorry i don't know terminology).

Remember that...now in Terminal type:

```
sudo gedit /etc/fstab
```

at the last line where yours says "/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0" Replace **hdd** with whatever your dvd drive name was. Here's mine for example:

```
/dev/**scd0 **      /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Save, close and tell me if this works. Definitely, make a back up of fstab so that you don't mess up your comp if this doesn't work. Now, when you find your drive name, if it is indeed called **/dev/[B]hdd**[/B] I really don't know what to do...So let's hope this is the solution for you!!

---

### Post by timberdc on 2007-06-25
Okay, now we are getting somewhere. There is no longer a cdrom drive listed, but I still cannot mount my dvd drive. When I try to mount, I get the error details:

mount: block device /dev/scd0 is write protected. mounting read only.
mount: not a directory

---

### Post by Inxsible on 2007-06-25
EDIT: Too late. :rolleyes:

I see that you have already got rid of your extra cd rom. I missed the second page before posting.

---

### Post by Inxsible on 2007-06-25
Another way to get rid of the phantom CD-ROM 1 icon is to completely remove the entry for the cdrom from fstab. That way, even if the next kernel changes the way it reads CD drives, you will still be safe from having phantom drives listed.

A cd drive is mounted under /media and should be auto-mounted anyway.

As for your current problem of not being able to mount your cds, did you change any folders under /media. I think there is one called cdrom and a symlink for it called cdrom0

---

### Post by timberdc on 2007-06-25
> **Inxsible said:**
> Another way to get rid of the phantom CD-ROM 1 icon is to completely remove the entry for the cdrom from fstab. That way, even if the next kernel changes the way it reads CD drives, you will still be safe from having phantom drives listed.

A cd drive is mounted under /media and should be auto-mounted anyway.

As for your current problem of not being able to mount your cds, did you change any folders under /media. I think there is one called cdrom and a symlink for it called cdrom0

I did not make any other changes. Do I need to? I really appreciate you guys helping me with this...

---

### Post by isaacj87 on 2007-06-25
Still didn't work!? wow...was I correct about the drive having the wrong name?

You know...maybe your DVD is corrupted?? Because when I looked at your picture it looks like  you've got a DVD in there???

Do other discs work? Like a DVD movie? or audio CD?

---

### Post by isaacj87 on 2007-06-25
> **Inxsible said:**
> Another way to get rid of the phantom CD-ROM 1 icon is to completely remove the entry for the cdrom from fstab. That way, even if the next kernel changes the way it reads CD drives, you will still be safe from having phantom drives listed.

A cd drive is mounted under /media and should be auto-mounted anyway.

As for your current problem of not being able to mount your cds, did you change any folders under /media. I think there is one called cdrom and a symlink for it called cdrom0

I think you're the one that helped me find a solution to my problem! Did you know when the newest kernel upgrade came out it completely fix my problem and removed the ghost drive? It definitely made my day...

---

### Post by timberdc on 2007-06-25
> **isaacj87 said:**
> I think you're the one that helped me find a solution to my problem! Did you know when the newest kernel upgrade came out it completely fix my problem and removed the ghost drive? It definitely made my day...


I noticed on Betanews that there is a new kernel. Can I just install  that?

[http://fileforum.betanews.com/detail/Linux_Kernel/1144175077/1]("http://fileforum.betanews.com/detail/Linux_Kernel/1144175077/1")

---

### Post by timberdc on 2007-06-25
> **isaacj87 said:**
> Still didn't work!? wow...was I correct about the drive having the wrong name?

You know...maybe your DVD is corrupted?? Because when I looked at your picture it looks like  you've got a DVD in there???

Do other discs work? Like a DVD movie? or audio CD?

The reason it shows that is because I had just re-booted, and it randomly puts an icon on my desktop as if it were mounted when I re-boot with a disk in the drive. But it still will not read anything from it. The extraneous cdrom drive is gone, however. :D I just can't mount my dvd drive..

---

### Post by isaacj87 on 2007-06-25
> **timberdc said:**
> I noticed on Betanews that there is a new kernel. Can I just install  that?

[http://fileforum.betanews.com/detail/Linux_Kernel/1144175077/1]("http://fileforum.betanews.com/detail/Linux_Kernel/1144175077/1")

I'd try it...it's worth a shot right? Just go to the Update Manger and see if it gives you the new kernel.

---

### Post by timberdc on 2007-06-25
> **isaacj87 said:**
> I'd try it...it's worth a shot right? Just go to the Update Manger and see if it gives you the new kernel.

Okay, I'll give it a shot when I get home tonight. Again, I really appreciate all the help you guys have given me. Thank you! I'll post up later and let y'all know how it works..

---

### Post by timberdc on 2007-06-25
uggghh.. I give up. I guess I'll hang out as long as I can without an optical drive, but I'm going to have to go back to Microcrap . I'm so discouraged.  I just don't know what else to do. I was going to try to update my kernel, but I'm not sure I can do it without having to do another re-install. blehh.

---

### Post by isaacj87 on 2007-06-25
> **timberdc said:**
> uggghh.. I give up. I guess I'll hang out as long as I can without an optical drive, but I'm going to have to go back to Microcrap . I'm so discouraged.  I just don't know what else to do. I was going to try to update my kernel, but I'm not sure I can do it without having to do another re-install. blehh.

I know it's annoying...but never ever go back to microsh*t!! Do you know what version your kernel is and did you optical drive ever work after installing Ubuntu?

---

### Post by timberdc on 2007-06-25
> **isaacj87 said:**
> I know it's annoying...but never ever go back to microsh*t!! Do you know what version your kernel is and did you optical drive ever work after installing Ubuntu?


Believe me, I don't want to go back to M-soft. I really like Ubuntu so far. I did have a working drive on my first install. ( I had to re format and re-install after I lost my desktop trying to get Beryl working ) ;) But for some reason, this go around I don't have a working drive. I have kernel  ~.16

---

### Post by isaacj87 on 2007-06-26
Yeah...I'm guessing you're having kernel problems..

Two things you could do...

1) Reformat/reinstall...yeah I know...doesn't sound like the best option. But if you had a working drive back when you did an install, then the kernel included on the CD is a good choice for you and you probably should disregard the update when you finish the reformat. Or you could downgrade kernels..which I don't know how to do and it seems messy.

2) You know when you're booting and it says something about GRUB? Hit escape and choose a previous kernel.

Sorry I can only recommend stuff that's work for me...I'm not a linux wizard...at all...I couldn't honestly tell you if it really is kernel troubles. I hope you can find a solution so you don't have to go back to Micropoop.

---

### Post by timberdc on 2007-06-26
> **isaacj87 said:**
> Yeah...I'm guessing you're having kernel problems..

Two things you could do...

1) Reformat/reinstall...yeah I know...doesn't sound like the best option. But if you had a working drive back when you did an install, then the kernel included on the CD is a good choice for you and you probably should disregard the update when you finish the reformat. Or you could downgrade kernels..which I don't know how to do and it seems messy.

2) You know when you're booting and it says something about GRUB? Hit escape and choose a previous kernel.

Sorry I can only recommend stuff that's work for me...I'm not a linux wizard...at all...I couldn't honestly tell you if it really is kernel troubles. I hope you can find a solution so you don't have to go back to Micropoop.

I might just do that. I don't really mind re-installing, it's just a p.i.t.a. to do once everything is up and going. Thank you very much for your help!

---

### Post by isaacj87 on 2007-06-26
I definitely know what you mean...when I first installed ubutntu I was re-installing left and right.

---

### Post by Spydax on 2007-06-26
I'm on my fifth install,  pretty happy where I have it now, and really don't want to re-install again.  However I'm having the exact same issue.  I can see the CD-rom - it's installed internally on my laptop, but everytime I try and mount it I get the "unable to mount the selected volume.  -  mount:  Special device /dev/scd0 does not exist"  I've tried the 74 different solutions I've found on the forum to no avail.  I've tried real DVD's, burned DVD's, real CD's, and burned CD's.  Fail.  Meh, I'll just wait until I get back to the states.  I can wait until then.

---

### Post by isaacj87 on 2007-06-26
oh check the 2nd or 3rd page...I posted a proposed solution...see if it works for you.

---

### Post by timberdc on 2007-06-26
> **isaacj87 said:**
> oh check the 2nd or 3rd page...I posted a proposed solution...see if it works for you.

Nada. I think I'm going to go ahead and re-install. Hopefully, I'll have good news in a couple of hours. :rolleyes:

---

### Post by Spydax on 2007-06-27
I've read every thread and tried everything here.  Though I will try again as I downloaded some 80 something updates when I had the chance to hook my linux box up to the internet the other night.

---

### Post by timberdc on 2007-06-27
Okay, now this is getting to be a REAL head scratcher.. did a complete low level format last night, re-installed a fresh copy and STILL have the same problem! No updates installed or anything. I am going to try a different distro and see what happens. I just don't get this. All of my hardware worked fine on my first install. I wonder what would happen if I created a different partition during set up and tried mounting to that. Could anyone tell me if this would work, and maybe help me set it up?

---

### Post by isaacj87 on 2007-06-27
I can understand this. You did the reformat and still your drive doesn't work? Perhaps Ubuntu did auto updates while the installation was performed...

EDIT: can't**

---

### Post by timberdc on 2007-06-27
> **isaacj87 said:**
> I can understand this. You did the reformat and still your drive doesn't work? Perhaps Ubuntu did auto updates while the installation was performed...

I'll try again disconnected form thi network and see what happens, but I don't think any updates were installed..

?                                                                                                                                                                              ?

---

### Post by timberdc on 2007-06-28
UPDATE: I installed Mandriva Spring 2007 last night, DVD mounted fine. Something definitely broken in Ubuntu. I re-formated my hard drive again last night, and I'm going to re-write a new MBR to the disk, just to make sure everything is clean, then install disconnected from the i-net and see what happens.

---

### Post by timberdc on 2007-06-28
Update: Well, I had to go back to Windows. I just want to say thanks to eveyone who posted in this thread trying to help me out. Unfortunately, I have to have an optical drive and I just couldn't get mine to work, even after three fresh installs.

---

### Post by isaacj87 on 2007-07-02
I'm sorry to hear it...Well I think everyone on this forum can probably agree that Ubuntu is a pain in the behind to some degree. Hopefully, when Gutsy comes out, your optical drive issues will be resolved. Sorry, you couldn't find a solution. :(

---

### Post by timberdc on 2007-07-02
> **isaacj87 said:**
> I'm sorry to hear it...Well I think everyone on this forum can probably agree that Ubuntu is a pain in the behind to some degree. Hopefully, when Gutsy comes out, your optical drive issues will be resolved. Sorry, you couldn't find a solution. :(

Thanks, I'm going to give it another shot when Gutsy comes out. I really like the Ubuntu distro, I hope it works!

---

