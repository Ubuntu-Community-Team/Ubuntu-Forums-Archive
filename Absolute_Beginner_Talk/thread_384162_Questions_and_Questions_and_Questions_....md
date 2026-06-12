---
title: "Questions and Questions and Questions ..."
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by thoeng on 2007-03-14
Hi All,

I have been using this OS for a while and its great piece of work
however questions are:

1. i am using monitor LCD Acer AL1916W (19" widescreen) and there is no option to 1440X900 (native resolution), i have tried configuring xserver-xorg and put the resolution but there is still nothing happen.

2. i would like to have my MP3 with HD capability to work here :(, i need it to move files between office and home

3. How do i install automatix2 ? tried to but it always halted at "retrieving keys" and error saying keys can't be retrieve.

4. how do i make the font look better ? or its caused by wrong resolution ??

I thank you for the support of this wonderful OS


Erin.

---

### Post by slimdog360 on 2007-03-14
1.when you set the resolution did you go the advanced option and set the horizonal and vertical refresh rates by hand? Thats what I have to do.

2. don know what your on about

3. I think automatix is going through some problems, try visiting the unofficial ubuntu starter guide.

4. It may be the screen resolution but you can still change it easily, someone else will have to say where as Im not on Ubuntu at the moment.

---

### Post by AtrejuT on 2007-03-14
Hi thoeng!

as to the resolution: What graphics card are you using? Intel? There then is a tool called 915resolution to set the proper resolution. see e.g.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

what mp3 player do you use? anythin I tried so far just worked (tm) - plug it in and the icon for your drive appears on the desktop. (ipod, sony network walkman, various usb sticks etc)

fonts: this might be due to the wrong resolution, but you could also try installing the microsoft truetype fonts:
```

sudo aptitude install msttcorefonts

```

good luck

atreju

---

### Post by thoeng on 2007-03-14
slimdog:

i tried before on medium setting. since the resolution available was 1440X900@100Hz  i chose it and rebooted. .. Resulted Crash. i think i chose wrong refresh rate.
After fix it, i tried simple and choose 1440X900 but there is nothing happen.

I haven't tried advance, perhaps you could give directions to achieve the resolution.

Also i read forum about herd5, what is it ? does it do what automatix does ?

---

### Post by thoeng on 2007-03-14
Hi atreju

I have managed to get my MP3 work now its been great !!
BTW my Video card is GeForce FX 5700VE 128MB
i am on major update (223) after clean install i will install the font afterwards 


Thanks !!

---

### Post by thoeng on 2007-03-14
Ow btw i forgot very important questions is:

i seems can't alter any of my file (excel, PPT, or word) simply because it is open at read only.

Is there any solution ? or should i login as root user ? if so please help

---

### Post by nalmeth on 2007-03-14
If your docs are stored on an NTFS drive then you won't be able to write to them. 

Are they indeed on a windows partition? Or are they on Ubuntu?

---

### Post by Tomosaur on 2007-03-14
> **thoeng said:**
> Ow btw i forgot very important questions is:

i seems can't alter any of my file (excel, PPT, or word) simply because it is open at read only.

Is there any solution ? or should i login as root user ? if so please help

This could be a problem, depending on what the situation is:

If these files are on an NTFS partition, then the solution is simple:
1: Either copy them to your home folder.
2: Or Install the necessary NTFS support driver: [Website](http://www.ntfs-3g.org/)

Where are these files? If they are in a linux partition, for example in your home folder, then you may have messed up the file permissions somehow. Open up a terminal (Applications > Accessories > Terminal) and type:
```

ls -l

```
This assumes the files are in your home directory. If they're not, you need to change to the right directory using the 'cd' command:
```

cd ~/path/to/directory

```
And then do the ls command.

The files should NOT be outside of your home directory. That is, they can be in folders inside your home directory, but they should not be in a 'lower' directory.

Copy and paste the output here, so we can see what's wrong.

---

### Post by thoeng on 2007-03-14
howyy sh*t ... i have just checked and it is NTFS !!
is that means i won't be able to write anything on my "data" partition ?? is there anyway to change file type NTFS to FAT32 without losing my data ?

---

### Post by thoeng on 2007-03-14
okay so i have moved my work documents to home folder and its writeable

but my linux partition is only 10G and my NTFS "data" partition is over 100G.

I guess i am need to change from NTFS to FAT32, how can i do this :(

---

### Post by astrolabio on 2007-03-14
You don't need to change. As a previus poster said there's NTFS support.

It's not included by default because is still beta, but the only problem i ever got from it is that it takes a lot of processor when you move large file into it. That's a known problem and they are working on it. But for the rest it seems to works fine.

To install it you have just to do the usual
sudo apt-get install ntfs-3g

And then change your filesystem type from ntfs to ntfs-3g in your /etc/fstab file, and then reboot or if ou don't want to reboot just umount and remount the partition. 

If you do a little research about ntfs-3g you should find plenty of more detailed step by step tutorial.

---

### Post by Drakkor on 2007-03-14
You can read/write to ntfs partitions, have a look here:
[http://www.ubuntuforums.org/showthread.php?t=373935&highlight=write+ntfs](http://www.ubuntuforums.org/showthread.php?t=373935&highlight=write+ntfs)
I have dual boot Ubuntu/XP and it's called fuse, available in synaptic. I have 3 nffs/fuse
partitions and can read/write to all. :)

---

