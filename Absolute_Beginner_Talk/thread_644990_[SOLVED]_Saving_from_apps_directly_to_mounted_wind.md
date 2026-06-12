---
title: "[SOLVED] Saving from apps directly to mounted windows shares"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Zoltarp on 2007-12-19
If I can get to and save to mounted windows shares that would be very helpful indeed. For example when downloading drivers I want to save directly to the mounted windows share but I cant seem to find a link to it when browsing for a location. Obviously the windows share is there because it appears on my desktop, but where else is it?

Thanks,
Bruce

---

### Post by reckless2k2 on 2007-12-19
check your /etc/fstab folder for where it mounts your windows share but it's usually in /media

---

### Post by Zoltarp on 2007-12-19
I looked and that folder does not appear under etc is it hidden to me?

---

### Post by reckless2k2 on 2007-12-19
i'm sorry...it's not a folder....it's a file.

just do this at the terminal:

```
cat /etc/fstab
```

---

### Post by Zoltarp on 2007-12-19
This is what it says. 

bhillier@bhillier-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=80658158-bd54-48c3-8ffe-68445aeab464 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=68308d70-bad0-425a-93c2-75f03bfe8c84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//merrell/images$    /media/images  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//merrell/bhillier   /media/home  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//merrell/music      /media/music  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//merrell/production /media/production  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//merrell/supply     /media/supply  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//merrell/shared     /media/shared  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//semore/e$          /media/adminshare cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//stimpy/install$    /media/install cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

bhillier@bhillier-desktop:~$ 



I added the shares in there in an effort to get them all permanently mounted under /media I followed these [these]("http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares") instructions but  got this when I got to the sudo mount -a part was permission denied when it tried to mount them using the known good credentials in the credential file I made.

---

### Post by reckless2k2 on 2007-12-19
i guess i'm confused because it looks like you have quite a few things in /media mounted which is for that windows mount. 

```
//merrell/images$ /media/images cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0
//merrell/bhillier /media/home cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0
//merrell/music /media/music cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0
//merrell/production /media/production cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0
//merrell/supply /media/supply cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0
//merrell/shared /media/shared cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0
//semore/e$ /media/adminshare cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0
//stimpy/install$ /media/install cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0
```

i would assume that stuff is your windows shares. are you saying that you don't have access to it? 

ok..ok...i see that is your problem. you have to add a uid= and or a gid= to specify you in these fstab settings so you can gain access. 

i think that's what your talking about. otherwise...only root can access them. you understand?

---

### Post by Zoltarp on 2007-12-19
Ohh so each of those should read:

uid= //stimpy/install$ /media/install cifs credentials=/root/.smbcredentials,iocharset=utf8,f ile_mode=0777,dir_mode=0777 0 0

like that?

---

### Post by reckless2k2 on 2007-12-19
here is a quick and dirty cifs guide that i use. your uid and gid have to be in the code. 

[http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/](http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/)

that should help you out. if you are stuill having problems i can post your exact code for you.

---

### Post by Zoltarp on 2007-12-19
Thanks I'll give it a shot

---

### Post by reckless2k2 on 2007-12-19
```
//stimpy/install$ /media/install cifs credentials=/root/.smbcredentials,uid=<yourusername>,gid=<yourusergroup>,file_mode=0770,dir_mode=0770 0 0
```

i think you would be fine with that. if not, i can check my code real quick on mine.

---

### Post by Zoltarp on 2007-12-19
I tried this per that articles instructions but got this error:


//stimpy/install$ /media/install cifs rw,_netdev,user=sytexltf/administrator,password=**********,uid=<uid>,gid=<gid> 0 0


bad user name "<uid>"

I guess that uid and gid is what I am not getting.

I stared out the real password I didn't actually put stars in the file :)

EDITED AND ADDED LATER

I just re-read the entire post and realize now that the UID and GID are values I need to supply and not some archaic switch or something (LIGHTBULB!)
So what exactly is it looking for there? bhillier and workgroup or something different?

---

### Post by Zoltarp on 2007-12-20
> **Zoltarp said:**
> I tried this per that articles instructions but got this error:


//stimpy/install$ /media/install cifs rw,_netdev,user=sytexltf/administrator,password=**********,uid=<uid>,gid=<gid> 0 0


bad user name "<uid>"

I guess that uid and gid is what I am not getting.

I stared out the real password I didn't actually put stars in the file :)

EDITED AND ADDED LATER

I just re-read the entire post and realize now that the UID and GID are values I need to supply and not some archaic switch or something (LIGHTBULB!)
So what exactly is it looking for there? bhillier and workgroup or something different?

Can anyone please explain this UID and GID thing? I'm so close to having this work.

Thanks

---

### Post by Zoltarp on 2007-12-20
I now figgured out what those to things are GID and UID are the things you see in the command prompt mine say bhillier@bhillier so GID=bhillier and UID=bhillier in my case.
Hope that helps others understand what is probably a very basic linux term.  

Thanks reckless2k2 for your help.. it now works fine when i insert bhillier for those values.

---

### Post by reckless2k2 on 2007-12-20
yeah i put the whole uid=<yourusername> thing and i thought you understood. sorry i wasn't more clear and glad you got it working.

---

