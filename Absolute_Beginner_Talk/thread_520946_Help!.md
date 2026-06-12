---
title: "Help!"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-08-08
Can anyone please post their /usr/share/icons directory I corrupted mine by trying to remove all distributor-logo.* files and accidently removed almost everything, i need this directory back!

---

### Post by Al3xK3aton on 2007-08-08
Why don't you just go back to a backup? I'm sure that you know to back up all your data every month or so.

---

### Post by amrclutch1 on 2007-08-08
No I don't but when this is fixed I definitely learned my lesson and will create an automatic backup script!

---

### Post by Dr Small on 2007-08-08
I archived everything in the /usr/share/icons directory, and it's 43 MBs...
Please explain some reasonable way I could transfer them :P

---

### Post by Al3xK3aton on 2007-08-08
Why not use email? As it turns out, GMail supports huge attachments. Or you could mail him a CD with the contents, or 40 floppy disks.

---

### Post by amrclutch1 on 2007-08-08
Don't be unreasonable, maybe you could use rapidshare.com?

---

### Post by Dr Small on 2007-08-08
I think I'll just break down the package into separe files, that way it reduces my upload, as my upload is rather slow anyhow.

Give me time, I'll upload them to my website, so you can download them.
I'll PM you the links when I'm finished.

Dr Small

---

### Post by Al3xK3aton on 2007-08-08
Rapidshare has nasty terms of service. You could share it on a Yahoo group though. Or you could zip the files up, rename the zip to .jpg, put it on a MSN image group, and then download it from there, rename it back to .zip, and unzip it.

---

### Post by amrclutch1 on 2007-08-08
Dr Small, you sir, are a god.

---

### Post by Dr Small on 2007-08-08
> 
For as I passed by, and beheld your devotions, I found an altar with this inscription, TO THE UNKNOWN GOD. Whom therefore ye ignorantly worship, him declare I unto you.
God that made the world and all things therein, seeing that he is Lord of heaven and earth, dwelleth not in temples made with hands;
Neither is worshipped with men's hands, as though he needed any thing, seeing he giveth to all life, and breath, and all things;

Acts 17:23-25

So, please do not think me a god...

---

### Post by amrclutch1 on 2007-08-08
Ok then you are a nice person.

---

### Post by bigboy_pdb on 2007-08-08
Uploading the file to rapidshare would take a while. Have you tried looking for the icons on the live CD?

**EDIT:** I'm guessing you could run the live CD, mount a USB key, and then attempt to copy them to the USB key (or perhaps a CD-RW)

---

### Post by Dr Small on 2007-08-08
Don't worry about it... I'm uploading all of the archives right now...

---

### Post by bigboy_pdb on 2007-08-09
amrclutch1, this is in response to your e-mail which stated that not all of the icons that you had are present. If you've installed any icon packages then you may need to get them again.

I would recommend trying to get the icons from your Ubuntu Live CD. To do this do the following:

**NOTE:** Before you do this if you cannot access the internet from the CD it might be a good idea to save this information to a text document on a disk or USB key.

Boot from the Ubuntu Live CD.

Open a "File Browser" (Places -> Home Folder) and click on "File System" in the "Places" section on the left side of the File Browser. Find the partition that has your home folder from your hard drive installation of Ubuntu in the "Places" section on the left side of the File Browser (your hard drives and partitions should be listed in the "Places" menu). Once you've found the "home" folder from your Ubuntu hard drive installation look at the "Location:" text field to find out where the partition has been mounted to (it will be something like "/media/disk")

Open a terminal (Applications -> Accessories -> Terminal) and type:
mount | grep 'partition_folder'
partition_folder is the folder where the partition was mounted to (i.e. "/media/disk")

In the beginning of the line that is printed you will see the device for the parition (it will be something like "/dev/sda3" or "/dev/hda4"). Type "sudo umount partition_device" where partition_device is the partition device (i.e. "/dev/sda3" or "/dev/hda4"). Now type "sudo mount partition_device /mnt" where partition_device is the partition device (i.e. "/dev/sda3" or "/dev/hda4"). Type "sudo nautilus". A file browser will have opened.

Click on "File System" in the "Places" section on the left side of the File Browser. Go to the "/usr/share" directory and copy the "icons" folder. Go to "/mnt" which is where the partition with your home folder has been mounted and paste the "icons" folder into your user's documents folder.

Restart your computer, remove the Live CD, and boot into your regular Ubuntu installation. Open a terminal (Applications -> Accessories -> Terminal) and type "sudo nautilus". You will be asked for your password and after correctly typing it a file browser will have opened. Find the "icons" folder that you copied off the Ubuntu Live CD. Move it to "/usr/share".

Hopefully, now you should have your icons back (I haven't tried the last step because I don't want to mess up my icons, but it should work).

---

