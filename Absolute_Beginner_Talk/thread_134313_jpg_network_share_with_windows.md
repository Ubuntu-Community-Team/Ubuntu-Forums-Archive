---
title: "jpg network share with windows"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by 7018 on 2006-02-21
I really like ubuntu.
It is a great stepping stone from Windows into linux. My hats off to all those involved in the development etc and those involved here...

As I am just starting to get to know ubuntu I have a question regarding 
jpgs.

What do I need to do to be able to view jpgs stored on my xp desktop from my ubuntu laptop.

I can see and surf into my desktop from my laptop no problem.
But everytime I click on a jpg I get image file format not recognized.
I can copy files over to ubuntu and view that way but I can't seem to view those same files stored on desktop.
I have installed gimp, digikam, and other image viewers but I'm having a hard time trying to solve this problem.

I'm guessing there is a simple solution... I just haven't found it yet.

Please enlighten,

Thanks,

---

### Post by kaamos on 2006-02-21
Hello!

The best way (in my opinion) is to mount the shares so they look to the system like any other folder. Then all applications can use the files. 

Look here: [http://ubuntuguide.org/#automountnetworkfolders](http://ubuntuguide.org/#automountnetworkfolders)

---

### Post by 7018 on 2006-02-21
Ok, thank you for the quick response.

I tried to follow the instructions but I get the following error when mounting fstab

"mount: wrong fs type, bad option, bad superblock on //3GIG/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I did try other versions of  mounting besides //3GIG/
including 198.168.0.100/D instead of 198.168.0.100/linux as shown in how to.
but my link on my ubuntu laptop to access my desktop has smb://3GIG/ as url so I tried that as well

Desktop ip is 198.168.0.100

I should mention my "3GIG" is my windows desktop.  I have two drives c: and d: .  I have set permissions to share some folders from c and the whole d: drive on the xp machine. The desktop is formatted ntfs.

I'd be happy with just mounting the d drive and it's folders from my ubuntu laptop so I could see jpgs.

Any help is appreciated.

---

### Post by jjf on 2006-02-21
The guide kaamos posted is for Ubuntu Hoary (5.04).  If you have Breezy (5.10, the latest version), use this guide instead:

[http://easylinux.info/wiki/Ubuntu#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read](http://easylinux.info/wiki/Ubuntu#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read)

Great guide.  If the particular item within that guide isn't what you're looking for, scroll back up to the top and see if one of those looks promising.

(Actually, I just compared the two and mounting shared folders is exactly the same in both guides.  Sorry. )

---

### Post by 7018 on 2006-02-21
anyone?

---

### Post by 7018 on 2006-02-23
Well I managed to remedy the problem.

I think there maybe a bug in nautilus. 

For future reference

I installed konqueror and I can view the jpgs on my windows desktop via network.

Now to nail down thumbnails.

---

