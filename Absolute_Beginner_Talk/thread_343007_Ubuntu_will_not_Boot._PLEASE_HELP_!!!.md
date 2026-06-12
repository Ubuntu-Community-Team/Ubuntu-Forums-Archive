---
title: "Ubuntu will not Boot. PLEASE HELP !!!"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by AdyE on 2007-01-20
When I try to boot Ubuntu (Dapper), the screen goes black and says amongst other things "segmentation fault"

under that it says

"mounting /root/dev on /dev/.static/dev failed : no such file or directory"
"mounting /sys on/root/sys failed : no such file or directory"
"mounting /proc on/root/proc failed : no such file or directory"
"Target file system dosen't have /sbin/init"

What on earth is going on. PLEASE HELP if you can.
Thank you
AdyE.

---

### Post by meng on 2007-01-20
I take it you had a working installation previously. What have you done recently in terms of making changes - installing, removing, etc.?

---

### Post by tommy1987 on 2007-01-20
Could be a hard drive problem, segmentation fault can be imposed by a faulty hard drive, can you try and boot from another hard drive, to rule it out?

---

### Post by AdyE on 2007-01-20
> **meng said:**
> I take it you had a working installation previously. What have you done recently in terms of making changes - installing, removing, etc.?

Yes, it has been working for the past three days. I have only installed Automatix2, Turboprint, Nvu and Opera.
Both firefox and opera keep crashing and wont restart until I reboot, it was after one such reboot that this problem occured.
I have tried booting into recovery but get the same error messages.

---

### Post by AdyE on 2007-01-20
> **tommy1987 said:**
> Could be a hard drive problem, segmentation fault can be imposed by a faulty hard drive, can you try and boot from another hard drive, to rule it out?

It is a brand new hard drive :-(

---

### Post by Paerez on 2007-01-20
can you post your "/etc/fstab" file?

You can boot the live cd to view it.

---

### Post by AdyE on 2007-01-21
> **Paerez said:**
> can you post your "/etc/fstab" file?

You can boot the live cd to view it.

have put this request in after booting from live cd,,the message reads permission denied.
tried command with sudo in fromt of it and got message command not found.
thanks

---

### Post by medley on 2007-01-21
> **AdyE said:**
> have put this request in after booting from live cd,,the message reads permission denied.
tried command with sudo in fromt of it and got message command not found.
thanks


After booting from the live cd, try 'sudo nano /etc/fstab/. nano is a text editor. This should at least let you post the contents for others to help you.

---

### Post by AdyE on 2007-01-21
> **medley said:**
> After booting from the live cd, try 'sudo nano /etc/fstab/. nano is a text editor. This should at least let you post the contents for others to help you.


It says

"unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0"


Should I just re-install Ubuntu?

---

### Post by candtalan on 2007-01-21
It is possible to quickly check if the hard drive is ok by use of disk check tools from one or other of the hard drive manufactureres sites. I have used seagate tools and found it tio  be very useful.
It is usually a quick download  - and also a quick check is often available, longer check with choice.

[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

I have had new hard drives fail well inside their warranty period :-(

good luck

---

### Post by Paerez on 2007-01-21
ok it seems that your /etc/fstab is messed up.

From the live CD you can run "sudo gedit /etc/fstab" to get a better view, but we'll do that later.

For now, can you post the output of:
```
sudo fdisk -l /dev/sda
```

---

### Post by AdyE on 2007-01-21
> **candtalan said:**
> It is possible to quickly check if the hard drive is ok by use of disk check tools from one or other of the hard drive manufactureres sites. I have used seagate tools and found it tio  be very useful.
It is usually a quick download  - and also a quick check is often available, longer check with choice.

[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

I have had new hard drives fail well inside their warranty period :-(

good luck

I have used a disc scanner from the manufacturers site and used the full scan. All is well with the HD, no errors detected. So we can conclude the HD is not the cause of the problem :-)

---

### Post by AdyE on 2007-01-21
> **Paerez said:**
> ok it seems that your /etc/fstab is messed up.

From the live CD you can run "sudo gedit /etc/fstab" to get a better view, but we'll do that later.

For now, can you post the output of:
```
sudo fdisk -l /dev/sda
```

ok, here is what it says ...

disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

device             boot        start        end       blocks                       id            system
/dev/sda1         *               1         30023     241159716                83            linux
/dev/sda2                         30024    30401    3036285                    5              extended
/dev/sda5                          30024   30401      3036253+               82             linux swap / solaris

---

### Post by AdyE on 2007-01-22
Should I just re-install Ubuntu as this problem seems to have people stumped :-(
Thanx to all who replied to my problem, you rock :-)
Thanx,
Ady.

---

