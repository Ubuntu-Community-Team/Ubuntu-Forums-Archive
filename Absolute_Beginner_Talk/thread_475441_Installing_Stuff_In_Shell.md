---
title: "Installing Stuff In Shell"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by UbuNewbie123 on 2007-06-16
When installing stuff in shell, must the .gz files be moved to a particular folder before it will run?

Are there similar stuff like .exe files that can install programs in shell like windows?

If my file is in a CD-ROM drive, how do I copy the file to my linux computer?

---

### Post by Jimmyfj on 2007-06-16
When trying to install new programs from terminal I always use .deb files, it's easier and faster.

---

### Post by r4ik on 2007-06-16
Try,

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Good luck !

---

### Post by gilgongo on 2007-06-16
Don't forget that one of the many, many advantages of using Ubuntu over something called Microsoft Windows (or even a system made by a company who name themselves after a very boring fruit - I forget what they're called now) is that you can install (or remove) almost anything without having to worry about running installer files or wonder about where to put things. Once installed, they also then get monitored for updates automatically. Once you understand this model, you'll wonder why the hell people think Windows is anything worth using.

Simply go the Applications menu and choose add/remove. Or for more sophisticated control over what you want, use System > Administration > Synaptic Package Manager.

---

### Post by UbuNewbie123 on 2007-06-16
I am running Ubuntu Server and there is no GUI, am I right?

---

### Post by Phixion on 2007-06-16
> **UbuNewbie123 said:**
> I am running Ubuntu Server and there is no GUI, am I right?

Right, unless you choose to install either GNOME, KDE, Fluxbox, Openbox etc

---

### Post by UbuNewbie123 on 2007-06-16
Anyway, back to my original questions... How do I copy stuff from a CD rom to my ubuntu in shell?

---

### Post by aktiwers on 2007-06-16
Drag and drop just like in Windows.

If you dont have permission go to terminal and type:
```
gksudo nautilus
```

And navigate to the folder you want to drop the files.

---

### Post by UbuNewbie123 on 2007-06-17
My Ubuntu server does not have both the gksudo and nautilus commands. Any more ideas? I tried searching on Google for tips on how to copy stuff from CD to the unbuntu server but I have not been able to find anything.

---

### Post by Malibu Illusion on 2007-06-17
```
cp /media/cdrom/file /path/to/hddlocation
```

---

### Post by Gimpy_Rob on 2007-06-17
Hey, I run ubuntu server aswell, actualy using it as a footrest as well (Ubuntu is very versatile). 

Anyways, nautilus and gksudo are commands that need an X display to work, and you don;t have that.  Ubuntu server is great because it isn't bogged down with any display to worry about, or anything like that.

So, copying files from CD to hard drive right?

Do you know the path that the CD is mounted?  Usually a good bet is ```
 /cdrom
``` this is a pointer to /media/cdrom which is a pointer to main cd drive, mounted in /media (usualy /media/cdrom0)

ok, so you can copy the files onto computer (into home directory, represented by ~) by ```
cp [your file] ~
```

Now, if you aren't familiar with cp, you might need help installing whatever it is...  Feel free to post here whatever you are confused about next.  Sounds like you need to uncompress the file (gz is a kind of compression) then install whatever is inside.  Might be best to list files inside for us to determine next step.

---

### Post by UbuNewbie123 on 2007-06-17
I found a great tutorial here:

[http://linux.about.com/od/linux101/l/blnewbie4_2_2.htm](http://linux.about.com/od/linux101/l/blnewbie4_2_2.htm)

Just add "sudo" in front of the commands and it should work. Phew!

---

### Post by UbuNewbie123 on 2007-06-17
I will try your method. The tutorial I found was very long-winded.

---

### Post by UbuNewbie123 on 2007-06-17
I entered cd /media/cdrom0 , cd /cdrom and it works. But when I enter ls, I see nothing listed.

---

### Post by UbuNewbie123 on 2007-06-17
> **Malibu Illusion said:**
> ```
cp /media/cdrom/file /path/to/hddlocation
```

This gives me an error like no such file or directory.

---

### Post by Gimpy_Rob on 2007-06-17
Ok, if you type ```
ls
``` while IN that folder, and get nothing, then your computer is not seeing what's on the CD... I always assumed it would auto mount with server... let me play a bit with mine... 
and  Malibu Illusion was giving what is called psuedo code, and you were meant to substitute in your own directories and files...  Can be confusing when used in the 'code' tag.j

---

### Post by UbuNewbie123 on 2007-06-17
The tutorial link I posted earlier worked. I had to mount a CD ROM drive from /dev/hdd => 2nd IDE, Secondary Drive, which was where my CDROM drive was attached to.

The rest of the commands did not work..  I guess in the server mode, we have to mount drives.

---

### Post by Gimpy_Rob on 2007-06-17
ok, well, glad you can see the drive, and files within  (I was playing with my server... aparently I forgot to re-connect the cdrom drive last time I had case open)

anyways, if it is mounted, you should be able to copy files around.  cp is the copy command.

if you are in the cdrom directory, type 

cp [your file] ~

to copy to your home directory in /home

you will need to type ls first to find the file you want to copy...
(btw, play with tab-auto installed 6.10 but forgot I set the upgrade to 7.04 last night just before going to bed completion, (start typing, then just push tab) it is one of the single greatest features)

---

### Post by hyper_ch on 2007-06-17
install midnight commander:

```

sudo apt-get install mc

```

and then run it:
```

mc

```

That gives you a 2-pane directory view where you can simply copy from one side to the other.

---

### Post by UbuNewbie123 on 2007-06-17
- sudo mount -t auto /dev/DRIVE /cdrom where "DRIVE" is the corresponding drive in the list below:
		- hda: The master drive of the first IDE interface.
		- hdb: The slave drive of the first IDE interface.
		- hdc: The master drive of the second IDE interface.
		- hdd: The slave drive of the second IDE interface.

I did the above... Then I went to cd /cdrom to install the stuff I wanted directly from the CDROM.

---

