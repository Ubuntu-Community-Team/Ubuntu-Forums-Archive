---
title: "Trying to install Warcraft III. Don't undersand part of install instructions..."
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-07-30
I'm trying to follow instuctions on this site:
[http://appdb.winehq.org/appview.php?iVersionId=1177&hideAll=Limit+to+5+Tests](http://appdb.winehq.org/appview.php?iVersionId=1177&hideAll=Limit+to+5+Tests)

I get stuck when it says :

```

In ~/.wine/dosdevices you must make a symbolic link to the corresponding device node of your CD-ROM like the following:

lrwxrwxrwx 1 jesse users 10 2005-12-28 13:35 d: -> /mnt/cdrom
lrwxrwxrwx 1 jesse users 8 2005-12-28 13:35 d:: -> /dev/hdc

If you don't have d:: then run a command similar to this (use your own paths):

$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:

Make sure that your user account has read access to your cdrom device. ie: if /dev/hdc is your cd-rom

bash-3.00$ ls /dev/hdc -l
brw-rw---- 1 root cdrom 22, 0 2005-12-30 08:53 /dev/hdc
bash-3.00$ grep cdrom /etc/group
cdrom::19:jesse

If you use the HAL method of mounting discs please contact me and send test reports!

```

In that site. Please give more newbie friendly directions. Thanks a bunch.

---

### Post by Charco on 2006-07-31
Sigh... bump...

---

### Post by NewWithoutClue on 2006-07-31
Howdy, basically it wants you to link /dev/hdc to /home/your_user_name/.wine/dosdevices/d:: and /mnt/cdrom to /home/your_user_name/.wine/dosdevices/d:
It also asks you to make sure you have read access to the devices' mount point (/mnt/cdrom). And I know if youre using the user that you first had when you installed Ubuntu, that you do, in fact, have read rights. 

To do this, issue these commands
```

ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
ln -s /mnt/cdrom ~/.wine/dosdevices/d\:

```

However, those above commands may not be needed, because perhaps when you installed wine (you did install wine, right?) it did all that for you. To check to see if you need to issue the above commands, execute this and check the output:
```

ln ~/.wine/dosdevices

```

If you see something like:
> 
lrwxrwxrwx 1 jesse users 10 2005-12-28 13:35 d: -> /mnt/cdrom
lrwxrwxrwx 1 jesse users 8 2005-12-28 13:35 d:: -> /dev/hdc

then you DO NOT need to issue the first set of commands I listed.

Regards,
Paul

---

### Post by Charco on 2006-07-31
Thanks so much for the reply! I think I don't have permissions even though I AM on the account I first created!

```


charco@charco-desktop:~$ ln ~/.wine/dosdevices
ln: `/home/charco/.wine/dosdevices': hard link not allowed for directory
charco@charco-desktop:~$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
charco@charco-desktop:~$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
ln: creating symbolic link `/home/charco/.wine/dosdevices/d::' to `/dev/hdc': File exists
charco@charco-desktop:~$ ln -s /mnt/cdrom ~/.wine/dosdevices/d\:
ln: creating symbolic link `/home/charco/.wine/dosdevices/d:/cdrom' to `/mnt/cdrom': Permission denied


```

That's why it doesn't work! Ahhh!!! What now?

(I really really appreciate your help :) )

---

### Post by Charco on 2006-07-31
Bump.

---

### Post by verbatim210 on 2006-07-31
hey charco want to play warcraft together?

---

### Post by Charco on 2006-07-31
:( I can't get it to work. Do you know how to fix permissions?

---

### Post by verbatim210 on 2006-08-01
i have 2 computers 1 windows i use everyday and 1 linux for server. i didn't know you could install warcraft on linux cause it is windows native with the .exe and all.

i do all my day to day stuff using windows, i would like to migrate completly into linux but its a tough task.  too many incompatibilies and options i need that i cant do in linux.

---

### Post by verbatim210 on 2006-08-01
oh and **sudo chmod 777 foldername** will fix your file permissions.  let me know if you get warcraft to work.

---

### Post by NewWithoutClue on 2006-08-09
oops... did i say ln ~/.wine/dosdevices? i meant ls ~/.wine/dosdevices

Paul

---

