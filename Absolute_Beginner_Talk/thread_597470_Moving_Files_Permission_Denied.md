---
title: "Moving Files/ Permission Denied"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-10-30
edit: title should say invalid parameters not permission denied. 

I'm new to Linux and learning what I can along the way. When I try to tranfer files to my usb drive I get a "invalid parameters" error. What is the easiest any easy way around this? Thanks.

---

### Post by nick_h on 2007-10-30
How are you trying to transfer the files?

---

### Post by 449 on 2007-10-30
I've only tried dragging and dropping documents from the "documents" folder to my external hdd.

---

### Post by twiceasworn on 2007-10-30
Well it could still be a permissions issue, though who knows.  I would check your logs first off.  Open up your favorite terminal and then navigate to /var/log.  From there I would look at messages and syslog.

What I think might work is invoking the nautilus file manager as root

```
gksudo nautilus
```

It will prompt for your password and then you will have root privileges when you are dragging and dropping.

Otherwise I would just do it from the terminal with the mv command.  Look at the manpage for mv for the syntax, basic overview is: 

```
sudo mv /file/to/move /path/to/move/to
```

---

### Post by 449 on 2007-10-30
> Well it could still be a permissions issue, though who knows. I would check your logs first off. Open up your favorite terminal and then navigate to /var/log. From there I would look at messages and syslog.
 

I'm still learning command prompts, but I tried typing ls /var/log and this is what it gave me:
 
acpid            daemon.log      fsck        pycentral.log
apparmor         daemon.log.0    gdm         samba
apport.log       debug           installer   scrollkeeper.log
apport.log.1     debug.0         kern.log    syslog
apport.log.2.gz  dist-upgrade    kern.log.0  syslog.0
apt              dmesg           lastlog     udev
aptitude         dmesg.0         lpr.log     unattended-upgrades
auth.log         dmesg.1.gz      mail.err    user.log
auth.log.0       dmesg.2.gz      mail.info   user.log.0
bittorrent       dmesg.3.gz      mail.log    wtmp
boot             dmesg.4.gz      mail.warn   wvdialconf.log
bootstrap.log    dpkg.log        messages    Xorg.0.log
btmp             faillog         messages.0  Xorg.0.log.old
cups             fontconfig.log  news

I'm pretty clueless to what to look for. Also the gksudo nautilus code did not work.

---

### Post by 449 on 2007-10-30
bump

---

### Post by nick_h on 2007-10-31
You can view log files using System->Administration->System Log if you find it easier.

The suggestion to copy a file from the command prompt was a good one.

Try:
```
cd ~/Documents
ls
cp filename /media/<mount point>
```
where mount point where your drive is mounted.

If that doesn't work add *sudo* in front of the cp command.

---

### Post by timcredible on 2007-10-31
what format is the drive you're writing to?  ntfs, fat, ext3, etc?  if it's ntfs, i don't think there's any module for writing to ntfs loaded by default.  if it's ext3, then you just don't have persmission to write to that drive.  if it's fat, maybe the drive is full?

---

### Post by drumstin on 2007-10-31
If possible, just a shot, try reformatting your usb drive.

---

