---
title: "Mounting .Iso file."
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-06-08
Hi all!

Im trying to mount an .Iso file. I get this error:

> aktiwers@ubuntu:~$ sudo mkdir /media/iso
aktiwers@ubuntu:~$ sudo modprobe loop
aktiwers@ubuntu:~$ sudo mount vista.iso /media/iso/ -t iso9660 -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

aktiwers@ubuntu:~$


What am I doing wrong?

Thanks

---

### Post by mostwanted on 2006-06-08
You're setting the file system type to *vista.iso*. AT least that's what I think the problem is.

---

### Post by aktiwers on 2006-06-08
[quote=mostwanted]You're setting the file system type to *vista.iso*. AT least that's what I think the problem is.[/quote]

Thanks, but what do you mean?

My iso file is called Vista.
I followed this guide:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)

isnt I suppose to change file.iso with my own iso file?

---

### Post by aktiwers on 2006-06-08
Bump

---

### Post by taurus on 2006-06-08
What does "dmesg | tail" say then???  I don't have any problem mounting ISO files so there must have been something wrong with your vista.iso then...

---

### Post by aktiwers on 2006-06-08
It says:

> aktiwers@ubuntu:~$ dmesg | tail
[4357500.084000] sdc: assuming drive cache: write through
[4357500.086000] SCSI device sdc: 7999487 512-byte hdwr sectors (4096 MB)
[4357500.087000] sdc: Write Protect is off
[4357500.087000] sdc: Mode Sense: 64 00 00 08
[4357500.087000] sdc: assuming drive cache: write through
[4357500.087000]  sdc: sdc1 sdc2
[4357500.121000] sd 2:0:0:0: Attached scsi removable disk sdc
[4357500.121000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[4357500.121000] usb-storage: device scan complete
[4357501.412000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
aktiwers@ubuntu:~$


Anything wrong there? I dont understand it :S

---

### Post by taurus on 2006-06-08
Have you checked to make sure vista.iso isn't corrupted?

---

### Post by aktiwers on 2006-06-08
No, how do I check that? I dont have a DVD burner, and its a DVD image.
Is there other ways I can check it?

Thanks a lot for your help

---

### Post by taurus on 2006-06-08
Most of the files or ISO images come with a checksum where you can check the integrity of the files with md5sum...

---

### Post by aktiwers on 2006-06-08
You mean like this?

> aktiwers@ubuntu:~$ md5sum vista.iso
b40b83bb7e02333b7fb1df0249e1aee1  vista.iso
aktiwers@ubuntu:~$

And does that mean the file is ok?

Thanks alot

---

### Post by taurus on 2006-06-08
Well, you now have to match that with the md5sum that comes with your vista.iso!!!  Most sites will give you the md5sum of the ISO files so you can them to make sure the integrity of the files are good...  And I will make a wild guess here.  You downloaded the beta version of Windows Vista (either legal or illegal, I don't want to know) and there is no md5sum to check.  Try this then.  Open k3b and go to Tools -> Burn DVD Image.  (Yes, I know you don't have a DVD burner on your system but we will use k3b to test out the integrity of that file.)  Navigate to where vista.iso is and click on it.  Then, k3b will test out the integrity of your vista.iso.  If it comes back with a green check mark, then it is good...  Otherwise, the file is corrupted during the transit!!!

---

### Post by aktiwers on 2006-06-08
Yes you guessed right! It is Windows Vista (Downloaded from there Public Beta Release page), and it does show up as green!

But then Im back on the old problem, why cant I mount it?

Thanks a lot for all your help :)

---

### Post by christhemonkey on 2006-06-08
This is how i would do it:

```
sudo mount -o loop -t iso9660 /wherever/iso/image/is/image.iso /media/iso/ 
```



EDIT: If the download is bad, then no matter how you try an mount it it wont work:)

---

### Post by taurus on 2006-06-08
Wait a second!  This is Window Vista that we are talking about and it's only 190MB!!!  I thought that sucker is over 3GB (not that I care); that's why you need to burn it to a DVD instead of a CD...  So, I think you may want to check on the size again.

---

### Post by aktiwers on 2006-06-08
[quote=taurus]Wait a second!  This is Window Vista that we are talking about and it's only 190MB!!!  I thought that sucker is over 3GB (not that I care); that's why you need to burn it to a DVD instead of a CD...  So, I think you may want to check on the size again.[/quote]

HolyShit!!!! You are right! Wget told me the download was done..!

Well that explains it! Thanks!

The surver was very unstable, so I set wget -r tries=9999999999 and went to bed. This morning it said it had downloaded all 3gb. Well the file is only 190 ](*,)

Thanks a lot, gonna download it agian then :)

---

### Post by taurus on 2006-06-08
Try using wget with "-c" option such as
```

wget -c http://blah.com/blab/blah_file

```

---

