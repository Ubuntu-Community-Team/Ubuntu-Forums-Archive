---
title: "No Internet connection"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Askari-za on 2006-01-26
Im brand new to Ubuntu so help would be appreciated.

I have installed Ubuntu (Breezy) on a spare 64bit Intel box which is as yet without a net connection.

1) How do I install deb file which I downloaded and burnt to CD  in Windoze XP? 
2) Image Viewer (Eye of Gnome) does not support jpegs etc and I believe there is a plug-ib or something? Is it the file libjpeg62_6b-10_amd64.deb

That is actually the deb file I want to use to update EOG if it is indeed the correct file. But generally how would one do this as well.

Thanks

---

### Post by ubuntuuser on 2006-01-26
[QUOTE=Askari-za]
1) How do I install deb file which I downloaded and burnt to CD  in Windoze XP? 
[/QUOTE]
Type ```
sudo dpkg -i nameOfFile.deb
``` to install a single package. I can't help you with your second question, sorry.

---

### Post by bscbrit on 2006-01-26
My copy of Image viewer works fine with jpegs.  

Try the following on the command line:

eog <file.jpg>

Obviously, insert a real file for <file.jpg>. If there is a problem you should see an error message. Let me know what the results are please.

---

### Post by Askari-za on 2006-01-26
@ ubuntuuser:
I have tried sudo dpkg -i nameOfFile.deb (with the correct filename)

How do I specify a targer like hda or cdrom etc? I tried your command with the cd in the drive and I tried it after i copied the deb file i want to install to the var/cache/apt/archives. Neither worked.

@bscbrit:
You say try eog <file.jpg> but do I also need to specify a location ie cdrom or folder ? Lets say I have a cdrom in the drive which has jpgs on it.

---

### Post by bscbrit on 2006-01-27
What version of Ubuntu are you using? Is it an installed version or a live disk?

---

### Post by bscbrit on 2006-01-27
When installing programs in linux you do not have to specify which drive it should be installed on - linux is not windows and has a completely different file system and file organisation.  The various parts of the program (binary, configuration file etc) will all be placed in the appropriate directories.

If you need to specify where the 'deb' file that you are trying to install is located, then you must state the full path

e.g.   /media/cdrom/myfile.deb      or    /mnt/hda1/myfile.deb    or   eog /media/cdrom/myfile.jpg

---

### Post by Askari-za on 2006-01-28
Thanks Brit

Think I understand a little better now. Seems I had that deb installed as it happens. My cdrw-dvdrw drive has now become 'unmounted' and I cant get it mounted again (I sound like a dog breeder:p )

---

### Post by bscbrit on 2006-01-28
Try the following on the command line:

sudo mount /media/cdrom (or whatever your device is called)

If it doesn't work you should at least see a useful error message.

Just as an aside, you will note that many solutions to problems seem to end up by issuing commands on the commandline.  There are several reasons for this.  Every GUI utility you use is only a front-end to a command that can be invoked from the commandline.  The commandline variant often has more options.  The commandline variant will often give you useful error messages.  If you are using the commandline, you know that it is not a faulty GUI that is causing the problem. :-D

---

### Post by Askari-za on 2006-01-28
[QUOTE=bscbrit]Try the following on the command line:

sudo mount /media/cdrom (or whatever your device is called)

If it doesn't work you should at least see a useful error message.
[/QUOTE]

I did sudo mount /media/cdrom0 (in fstab it shows as that)
Response I get is : block device /dev/hdb is write protected, mounting read-only.

I have the following configuration:
IDE HDD with XP Pro on
SATA HDD where Ubuntu is installed
Samsung DVD/CD Rewriter
64bit Intel system.

I had fiddled in fstab before while following some how-to about mounting the XP drive and mounting a shared FAT32 folder. It didnt work so I reverted (tried to) to the original fstab which I had backed up. Problems started then as cd rom was mounted/visible/working before that.

---

### Post by bscbrit on 2006-01-28
I suspect that you have inadvertantly changed the access permissions for mounting the cdrom.

Can you show us the contents of fstab please?  The reference to hdb is to a hard disk drive, not your CDROM.

---

### Post by Askari-za on 2006-01-28
Have to type this manually as havent got the connection working between my laptop and the box.

My fstab looks like this after the 3 lines that start with #:
proc          /proc       proc       defaults     0        0
/dev/mapper/Ubuntu-root  /     ext3    defaults,errors=remount-ro 0   1
/dev/sda1         /boot     ext3    defaults     0   2
/dev/mapper/Ubuntu-swap_1   none     swap     sw    0    0
/dev/hdb        /media/cdrom0   udf,iso9660    user,noauto    0    0
/dev/fd0        /media/floppy0   auto     rw,user,noauto        0     0


Shouldnt I have a reference to hda?? Also I dont have a floppy drive yet its referenced.

Thanks for your time and help!

---

### Post by bscbrit on 2006-01-28
```

/dev/hda2       /boot           ext3    defaults        0       2
/dev/hdb5       /data           ext3    defaults        0       2
/dev/hdb1       /home           ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /win            ntfs    rw,user,noauto  0       0

```

My fstab is shown above - note that my CDROM is set to 'ro' whereas yours is not.  You have a serial (SATA) drive - hence sda is shown rather than hda which indicates that my drive is PATA, I think.  You can remove the reference to fd0 but it will do no harm leaving it there.

---

