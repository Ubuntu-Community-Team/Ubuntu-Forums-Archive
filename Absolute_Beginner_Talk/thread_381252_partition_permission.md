---
title: "partition permission"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by stardusk on 2007-03-10
How do I change the permissions of a partition? I have a partition called /data that I have to type in 'sudo' everytime I move or copy something in it. Thanks.

---

### Post by overdrank on 2007-03-10
> **stardusk said:**
> How do I change the permissions of a partition? I have a partition called /data that I have to type in 'sudo' everytime I move or copy something in it. Thanks.

Hi this may help, good luck! :) 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29)

---

### Post by sad_iq on 2007-03-10
Are you sure it's a partition or is it just a folder? If it's a folder you could do sudo **chown -R** *your_user_name* /data and **chgrp** *your_user_name* /data  ...don't know about the partition part (I don't think there is such a thing)

---

### Post by wj32 on 2007-03-10
Do **not** use sudo without a password...

1. *sudo gedit /etc/fstab*
2. Look for the line with "/data" in it. e.g:
        /dev/hdb1 /data ext3 **silent,locale=en_US.utf8,no_def_opts,allow_other** 0 0
3. In that stuff in bold, add **,umask=0**. So, now it should read (for example):
        /dev/hdb1 /data ext3 silent,locale=en_US.utf8,no_def_opts,allow_other,**umask=0** 0 0

Hope that helps!

---

### Post by dstew on 2007-03-10
Does your mount point directory give you write privleges? Go to the root directory and look at the output of ls -l. If the privleges look like this:

drwxr-xr-x  21 root root  4096 Dec 31 19:21 data

then you can only write in this directory if you have root privleges. To give users write privleges, do:

sudo chmod o+w /data

---

### Post by HdK on 2007-03-10
hdk@hdk-desktop:~$ sudo chmod o+w /data
Password:
chmod: cannot access `/data': No such file or directory
hdk@hdk-desktop:~$

---

### Post by stardusk on 2007-03-10
This is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7fe3fd77-121d-4f9e-86a4-5f8cdd904d1c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=cc943196-43dd-48e0-a9bb-d46ee7afdd8e /data           ext3    defaults        0       2
# /dev/hda6
UUID=ff0697e7-8169-44c4-ac3d-2b0d039b96e7 /home           ext3    defaults        0       2
# /dev/hda5
UUID=cba10675-dccd-476a-b9d8-de49e97b34a4 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

[quote='wj32']Do not use sudo without a password...

1. sudo gedit /etc/fstab
2. Look for the line with "/data" in it. e.g:
/dev/hdb1 /data ext3 silent,locale=en_US.utf8,no_def_opts,allow_other 0 0
3. In that stuff in bold, add ,umask=0. So, now it should read (for example):
/dev/hdb1 /data ext3 silent,locale=en_US.utf8,no_def_opts,allow_other,umask=0 0 0

Hope that helps!
[/quote]

I cant find the "silent,locale=en_US.utf8,no_def_opts,allow_other" Do I still add "unmask=0"?

I tried typing "sudo chown -R [myusername] /data" into the terminal and I can use the directories inside /data without root permission, but I still cant copy things into /data (that are not inside another directory) without using "sudo."

---

### Post by taurus on 2007-03-10
```
sudo chown -R **username**:**username** /data
sudo chmod -R 755 /data
ls -la /data
```

---

### Post by stardusk on 2007-03-10
Thanks for the replies. I typed in what taurus suggested and solved the problem.

---

