---
title: "Hard Drive - format, created short cut on desktop - how plz?"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-05-25
Hi, my Ubuntu box has 2 HDDs, 10GB and 80GB. Ubuntu is on the 10GB HDD and the FAT is Extended 3. My 80GB HDD has Windows NTFS.

I want to:

1. Format my 80GB HDD to use it for all my data. How do I do this and what should I use if I have an option, Extended 3? This 80GB HDD will only have data.

2. Create a desktop link to my 80GB HDD.

3. Re-locate my "Home Folder" onto my 80GB HDD. So that all data is on the 80GB HDD.

I don't know how to do this.

Thanks.

---

### Post by joshrobinson on 2006-05-25
[QUOTE=u.b.u.n.t.u]Hi, my Ubuntu box has 2 HDDs, 10GB and 80GB. Ubuntu is on the 10GB HDD and the FAT is Extended 3. My 80GB HDD has Windows NTFS.

I want to:

1. Format my 80GB HDD to use it for all my data. How do I do this and what should I use if I have an option, Extended 3? This 80GB HDD will only have data.

2. Create a desktop link to my 80GB HDD.

3. Re-locate my "Home Folder" onto my 80GB HDD. So that all data is on the 80GB HDD.

I don't know how to do this.


Thanks.[/QUOTE]

you can install gparted in synaptic package manager , then load it to find and format your disc

ive never moved the home folder but it should work if you copy your home folder to a different location, then delete it as root, and once your disc is formatted as ext3 you can set its mount point as /home/ then copy your user folder onto the drive so it would be viewed as /home/userfolder

to create a link to the drive, once its mounted you can click places on the panel at the top then click and drag the shortcut inthere to the desktop and it will copy it

the hardest part will be to mount the drive as /home

you need to sudo gedit /etc/fstab  when that opens you have to set in the devices name from the /dev location, followed by its parititon number
example:  /dev/hda1    1 being the partition number on device hda
so your fstab would look like

/dev/hda1    /home   ext3  defaults 0 0

then you can mount it by doing

sudo mount /dev/hda1
or it should automount when you reboot

hope that wasnt too advanced or confusing for you if your new

---

### Post by hezral on 2006-05-25
wouldnt that make the harddisk writeable for root only? because i did it like that but instead mount it in /media/hda4 but couldnt write files to the drive withou root.

---

### Post by joshrobinson on 2006-05-25
[QUOTE=hezral]wouldnt that make the harddisk writeable for root only? because i did it like that but instead mount it in /media/hda4 but couldnt write files to the drive withou root.[/QUOTE]

well you can write to it as long as the fstab is correct,  you might have to add something after defaults like umask=0000 but im not sure

i personally would mount it in /media/hda4 (or other name) also, since the home folder is already there and has settings in it

but if he really wants it as /home it can be done.. but i agree with you

---

### Post by zappafrank on 2006-05-26
Yes, you can do this. First partition the 80GB drive with fdisk or gparted, then format it using the ext3 filesystem: 

**sudo mkfs.ext3 /dev/hdb1**

(this assumes your 80GB drive is connected as secondary master, and has only one partition) After that is done you can mount it: 

**sudo mount /dev/hdb1 /media/hdb1**

This mounts the disk to /media/hdb1 - we'll change that later. you can now move your users' home directories to this place (*). When you move the directories you should not be logged into kde, gnome or the likes, because some files cannot be moved then. So if you haven't, _end your gnome/kde session now_ and login to the console to move the home directories! You can do that as root only (or as sudo user)! However, these directories belong to their user. you can make that sure by typing

**ls -l /media/hdb1**

You should see that each home directory is owned by the respective user, so they won't have any problems writing there. 

Now add a new entry in the /etc/fstab file, it should look like this:

**/dev/hdb1 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 0**


Make sure the directory /home/ is empty now, and mount the new harddrive there: 

**sudo umount /media/hdb1**
**sudo mount /home**

now you can test everything, and if all is ok, reboot! 

----------


* [SIZE="1"]Here's a tip to make you feel more safe when doing this:
Don't move the users' directories to the new hard drive, instead copy them. then move your /home to /home-safe and make a new /home

cd /
sudo mv /home/ /home-safe
sudo mkdir /home

If anything goes wrong you can rename it back. [/SIZE]

---

### Post by u.b.u.n.t.u on 2006-05-26
zappafrank thanks.

I downloaded and installed gparted. I formated the entire 80GB HDD to ext3.

sudo mkfs.ext3 /dev/hdc1

and

sudo mount /dev/hdc /media/hdc1

didn't work. I get the error message:

"does not exist"

I also didn't find fdisk, though gparted did the trick.

In "Disks Manager"

"Partition Properties
Device: /dev/hdc1
Filesystem: Extended 3
Access Path: None
Status: Inaccessible (Enable)"

I click enable and nothing.

I guess I am stuck as to how to mount the HDD.

Thanks.

---

### Post by zappafrank on 2006-05-26
"Access Path: None"

i guess you must set the access path before you can enable it (i never used the diskmanager, only just looked at it)


You said that you got an error "does not exist" - what is it that doesn't exist? My guess is that it's the mount point (same as "access path" in disk manager). if that's the case then see if /media/hdc1 is there, and if it's not create it. 
If it's the device that doesn't exist then check for typos. It must be there, gparted found it.

---

### Post by u.b.u.n.t.u on 2006-05-26
I worked out how to mount a HDD.

With the HDD properly formated, eg to ext3 with Gparted.

Open System / Administration / Disks

Then click on your HDD image in the left hand column and select the "Partitions" tab, top right.

Where it says "access path" click "change".  You should now see "Select New Mount Point Path" as the heading of that window. 

I created a folder "80gb_hdd" in "File System". No need to reboot.

Your HDD should now be ready to browse via that location.

Now how to create launcher? (short cut) to my HDD.  I have no idea. I have no easy one click way to access my 80GB HDD.

Suggestions are welcomed.

---

### Post by diogenes_3 on 2006-07-07
Hiall,

I am me-tooing myself to this thread, as I have quite the same situation. I have a box with 2 HDDs, the large one for data. I came over from XP, and of course immediately noticed that NTFS was not a good idea. Backed up the data, formatted the data HDD, mounted it, all after some belly-ache. 

But I can only access it as root! I appear to be too darn stoopid to write up the correct line for /etc/fstab. 

I don't even want to move home, I want a directory with shared data accessible by all users (me and my family), like the, err, "Gemeinsame Dateien" (all users' files???) in Windows. That's where the family pix and digicam videos will go.

Please, I have dug my way out of some weird holes already (proper screen resolution, got WLAN to work...), and this one should be simple, shouldn't it?

---

### Post by diogenes_3 on 2006-07-07
Arrgh, that was *so* stupid (bangs head against wall). I just read on a bit and found the answer sitting right here, and man was it simple: nothing's wrong with my /etc/fstab, I rather have to change my rights with *chmod 777* - how very, very obvious! I mean, while I have to say to my excuse that I have no routine using Unix commands in a console, it is not as if I had never, ever done it. 

So now I have solved my first three probs. The machine is humming and all. Let's see if it makes me a Ubuntu user...

---

### Post by ser1alsn1per on 2006-09-12
also i couldnt write to the hdd even though i had added it to the fstab file 


i found another thread saying they needed to be in colums just like the ones already in the fstab file 

line them up save it then reboot if needed and it should work

---

