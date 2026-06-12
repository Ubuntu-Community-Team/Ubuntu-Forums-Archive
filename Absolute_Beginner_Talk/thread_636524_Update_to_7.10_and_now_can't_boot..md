---
title: "Update to 7.10 and now can't boot."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by zeddock on 2007-12-09
I have been on 7.10 for a while now.
This evening I saw that updates were available and tried to install.  Earlier I think a new kernel was updated too.

Either way, the update did not seem to finish. It complained about partial update.  Eventually I rebooted and very little happens.  ..Blank screen with cursor in upper left.

Usually if I had trouble like this I would hit Escape on the boot and select the older kernel, but the is only 1 kernel and a recovery!

Right now I am on a CD boot.  I can see my stuff on the HD but when I tried to copy those folders and files the archive and copy failed because I do not have permissions.

Can someone help me either boot or copy my files to my external drive so after I reinstall 7.10 I can recover my data?

Thanx,

zeddock

---

### Post by nikoPSK on 2007-12-09
I have never tried this before but I know r means recursive. It will get everything in the folder and the folders therein. 

(This is just a guess, but it most likely could work.)
EDIT: it does.

Goto recovery mode:

```
cd ..
```
(this will bring you to your home directory,
```
cp -r myfile1 directory/
```

---

### Post by jonward690 on 2007-12-09
Well if you no your root password you could boot into recovery mode and try finishing the update up through the command line.

---

### Post by nikoPSK on 2007-12-09
by doing this:

```
sudo apt-get update
```

(you always need to explain;))

---

### Post by jonward690 on 2007-12-09
Thanks I forgot about that my bad.You have to do these commands.First
```
sudo apt-get update
```
Then to do the upgrade
```
sudo apt-get upgrade
```

---

### Post by zeddock on 2007-12-09
It does not boot!  So I can't do anything... not even command-line stuff.

zeddock

---

### Post by jonward690 on 2007-12-09
Nothing does any errors pop up?

---

### Post by nikoPSK on 2007-12-09
well, you my friend have a screwed system. Bring it into your local pc shop? :)

---

### Post by jonward690 on 2007-12-09
Well now hold on it has to be working to be able to run off a live cd.He would be better off fixing it his self cause I don't no a lot of places that work on linux boxes.

---

### Post by nikoPSK on 2007-12-09
well, here in victoria they can all do linux....:guitar:

---

### Post by jonward690 on 2007-12-09
Well if you can't boot I would just put all my information on a external hardrive or usb sticks or whatever you have to hold the files and do a reinstall.

---

### Post by nikoPSK on 2007-12-09
sound fine. As long as you have nice fat juicy USB sticks. I have 2 one gig ones, a 128 Meg one, a 4 gig one and an 8 gig one. :lolflag:

---

### Post by zeddock on 2007-12-09
Hang on folks.

1. We are gunna figure this out.
2. I don't think my system is screwed, I think either Grub is scrwed or the kernel is not compatable with other things.
3. If you don't KNOW, then say so because we are commenting on things which CAN seriously screwup new user's systems.

Finally, There are NEW users on Linux, Mac, and Windows, among other OSes.  This forum is for Linux... specifically Ubuntu.

I am not as new as others but I am new enough to post for help and to follow suggestions.  So, anybody have ideas?

zeddock

---

### Post by jonward690 on 2007-12-09
Well you might try restoring grub all have to look into it and find you a article on how to do that.

---

### Post by zeddock on 2007-12-09
> **jonward690 said:**
> Well if you can't boot I would just put all my information on a external hardrive or usb sticks or whatever you have to hold the files and do a reinstall.

I think this might be the best answer for me...
I am currently copying by way of this command:
```
ubuntu@ubuntu:/home$ sudo cp -r /media/disk/home "/media/My Book/Saved120907"

```

Crap!
Just failed the cp... Got this:
===
```
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.kde/cache-latlap': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.kde/socket-latlap': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.kde/tmp-latlap': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/arrowhd_en-GB.soe': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/palette_en-US_en-ZA.soc': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/modern_en-US_en-ZA.sog': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/arrowhd_en-US_en-ZA.soe': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/styles_en-GB.sod': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/classic_en-US_en-ZA.sog': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/modern_en-GB.sog': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/hatching_en-GB.soh': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/styles_en-US_en-ZA.sod': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/hatching_en-US_en-ZA.soh': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/classic_en-GB.sog': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.openoffice.org2/user/config/palette_en-GB.soc': Operation not permitted
cp: cannot create special file `/media/My Book/Saved120907/home/jim/.adobe/Acrobat/8.0/Synchronizer/Commands': Operation not permitted
cp: cannot create special file `/media/My Book/Saved120907/home/jim/.adobe/Acrobat/8.0/Synchronizer/Notification': Operation not permitted
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/.adobe/Acrobat/8.0/Cert/curl-ca-bundle.crt': Operation not permitted
cp: cannot create regular file `/media/My Book/Saved120907/home/jim/Desktop/vc ': Invalid argument
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/Desktop/Documents': Operation not permitted
cp: cannot create directory `/media/My Book/Saved120907/home/jim/Desktop/o jmk      ': Invalid argument
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/Pictures': Operation not permitted
File size limit exceeded (core dumped)
ubuntu@ubuntu:/home$ 

```


If I cannot copy my home directory to the external HD, I can't reinstall!

What now?

zeddock

===

---

### Post by zeddock on 2007-12-09
> **jonward690 said:**
> Well you might try restoring grub all have to look into it and find you a article on how to do that.

Please do.

zeddock

---

### Post by jonward690 on 2007-12-09
Well I think it is loading the files into your ram and freaking out and dumping them,I am going to see if I can find out how to copy files on a live cd.

---

### Post by lavinog on 2007-12-09
if you have free space on your hard drive I would repartition it with the live cd.
install linux on the new partition. (it doesn't need but 2 gigs) you can use this as a backup partition in case of failures like this one.
use this partition to backup your files to cd.
then go ahead and reinstall linux from scratch.

This is one option...there are more available that don't involve wiping your system, but you have to give some sort of information.
see if you can post your /boot/grub/menu.lst file and a listing of the files in the boot folder for a start.

---

### Post by jonward690 on 2007-12-09
Here I found that.


This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.

---

### Post by lavinog on 2007-12-09
> **zeddock said:**
> I think this might be the best answer for me...
I am currently copying by way of this command:
```
ubuntu@ubuntu:/home$ sudo cp -r /media/disk/home "/media/My Book/Saved120907"

```

Crap!
Just failed the cp... Got this:
===
```

cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/Desktop/Documents': Operation not permitted
cp: cannot create directory `/media/My Book/Saved120907/home/jim/Desktop/o jmk      ': Invalid argument
cp: cannot create symbolic link `/media/My Book/Saved120907/home/jim/Pictures': Operation not permitted
File size limit exceeded (core dumped)
ubuntu@ubuntu:/home$ 

```


If I cannot copy my home directory to the external HD, I can't reinstall!

What now?

zeddock

===

I don't think you want to use that to do your backup.
i think tar would be a better way to backup up your home folder
i think cp skips some files
also how is your external hard drive formated.
if it isn't ext3 i think that is why you are having problems copying symbolic links

---

### Post by zeddock on 2007-12-10
This HD prolly has Fat or NTFS.

How do I show my menu.lst file?  pasting txt here?

zeddock

---

### Post by zeddock on 2007-12-10
> **jonward690 said:**
> Well I think it is loading the files into your ram and freaking out and dumping them,I am going to see if I can find out how to copy files on a live cd.



Please do.
Thanx!


zeddock

---

### Post by zeddock on 2007-12-10
> **lavinog said:**
> if you have free space on your hard drive I would repartition it with the live cd.
install linux on the new partition. (it doesn't need but 2 gigs) you can use this as a backup partition in case of failures like this one.
use this partition to backup your files to cd.
then go ahead and reinstall linux from scratch.

This is one option...there are more available that don't involve wiping your system, but you have to give some sort of information.
see if you can post your /boot/grub/menu.lst file and a listing of the files in the boot folder for a start.

here is a list of my boot folder:
```
total 10075
drwxr-xr-x  2 root root     186 2007-10-15 23:37 .
drwxrwxrwt 31 root root     280 2007-12-10 13:22 ..
-rw-r--r--  1 root root  424317 2007-10-15 01:39 abi-2.6.22-14-generic
-rw-r--r--  1 root root   75311 2007-10-15 01:39 config-2.6.22-14-generic
-rw-r--r--  1 root root 7124250 2007-10-15 23:26 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  823535 2007-10-15 01:39 System.map-2.6.22-14-generic
-rw-r--r--  1 root root 1764280 2007-10-15 01:39 vmlinuz-2.6.22-14-generic
```

---

### Post by zeddock on 2007-12-10
> **jonward690 said:**
> Here I found that.


This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

...SNIP...

Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.


Thanx.

It looks to me as though GRUB is working just fine.  It is set to 0,0.

It does load grub properly because I get to select from 3 entries.
Memtest, kernel and safe.

So, I guess this is a huge issue with the kernel version?

zeddock
PS. So I still need to copy or tar my HD to the external.

---

### Post by lavinog on 2007-12-11
> **zeddock said:**
> This HD prolly has Fat or NTFS.

How do I show my menu.lst file?  pasting txt here?

zeddock

how did you show your boot folder listing?
you could try:
```
cat /boot/grub/menu.lst
```


as for backing up your stuff, try:
```
tar -cvvzf backup.tar.gz /home
```
replace /home with whatever folder you want to backup
then cp backup.tar.gz to your usb drive

---

### Post by zeddock on 2007-12-11
This backup approach is not dependable.

It stops after complaining about not having permissions to the files/folders that are in home.  And because of this I cannot open the archive created from it without getting an unexpected EOL error.

There is much talk in forums about tar not being dependable, and hard to figure out.  For instance, if I tell it to ==exclude="SomeFolderName" it will exclude ALL forders and files with that in its path/name!  I cannot afford that.

zeddock

---

### Post by zeddock on 2007-12-11
Here are some screen shots (via digital camera) of what errors I am getting.

Any help appreciated.

zeddock

---

### Post by zeddock on 2007-12-11
Is there a way to reinstall this kernel image? or the last? Maybe the DL was corrupt?

zeddock

---

### Post by natehall on 2007-12-11
i think cp skips some files

If you make that  cp  -rL  it should follow the symbolic links. ( Symbolic links allow files to sit in different places and still get used.)

---

### Post by natehall on 2007-12-11
> **zeddock said:**
> Is there a way to reinstall this kernel image? or the last? Maybe the DL was corrupt?

zeddock
I'm still learning this stuff . Let me know if this link helps you.
[http://rute.2038bug.com/node34.html.gz](http://rute.2038bug.com/node34.html.gz)

---

### Post by zeddock on 2007-12-11
Don't you either use Lilo or Grub?

I am pretty sure it is one or the other, and mine is definitely Grub.

zeddock

---

