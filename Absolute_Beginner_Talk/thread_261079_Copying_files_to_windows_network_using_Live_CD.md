---
title: "Copying files to windows network using Live CD"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by MartyNg on 2006-09-19
Greetings. My sister has a botched install of Windows XP that won't boot. The machine boots fine to the Ubuntu 6.06 Live CD though.

The machine is one of several Windows machines on a Windows network under workgroup MSHOME. Is there a **simple** way to boot into Ubuntu, then connect to another machine on the network? My goal is to move needed personal files to a working machine, reinstall Windows on the busted machine, then move the personal files from the working machine back to the fresh install of Windows XP. I realize I could put another hard drive in the busted machine, or use a USB external hard drive, but don't have spares at the moment.

Any pointers would be appreciated! I'm quickly getting addicted to Ubuntu! If I can get this procedure down, I'm sure it will come in handy for those people that can't find out how to botch windows without trying! Thank you!

---

### Post by bluefrog on 2006-09-20
boot ubuntu livecd.
open nautilus (file explorer)
edit it's preferences and change behaviour (I believe) to have it show always the address entry (instead of little tabs showing you where you are)

then in the address bar write

smb://ip-of-another-xp-box/d$  and hit enter  (replace d by whatever partition letter available on this xp box of course..)

it will ask you the xp administrator name (administrator) and it's password.

then it's just a matter of mounting your xp hard drive ( open a console and write   sudo mkdir /media/xp    then    sudo mount -t ntfs /dev/had1 /media/xp )and do some copying using nautilus.

To mount your drives you could go thru system > administration > disk manager I believe as well)

James

---

### Post by MartyNg on 2006-09-20
Fantastic! I will try this. Thank you. :D

---

### Post by MartyNg on 2006-09-20
> **MartyNg said:**
> Fantastic! I will try this. Thank you. :D

Awesome! It worked! It took a long time to copy many gigabytes to my laptop, but I was able to do it and get the files back onto a fresh install of XP! Thank you so much for your help! Being succesful in this process makes me want to use Ubuntu even more!  :D

---

