---
title: "Unmount windows Share"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Bigbird999 on 2007-11-05
I can mount a windows share from terminal in 3 ways 
```
sudo mount //192.168.0.14/BTV /media/BTV -o user=ernie,password=xxx

```
or
```
sudo mount -t smbfs //192.168.0.11/E /media/MediaonErniepc -o user=ernie,password=xxx
```
or, as I discovered by accident, put the above code in a text document on the desktop, click open and choose run in terminal and the drives mount.

I have put the automount lines at the end of  /etc/fstab like this
> //192.168.0.11/E /media/MediaonErniepc smbfs user=ernie,password=xxx but it doesn't mount when I boot, Probably because it tries to execute before my wireless connection is made (just a guess on my part).  After booting i can mount the share by 
```
sudo mount -a
``` 

 If I want to unmount from the desktop by right clicking the mount, it says only root can do that.  I searched and found that I could  unmount the share by 
```
sudo umount /media/MediaonErniepc
``` 
This is an issue because, when I shutdown without unmounting my windows shares, my laptop hangs after the shutdown splash and I have to remove the battery to complete the shutdown.  If I unmount the shares before choosing shutdown, it performs properly.

So, what do I have to do to unmount my shares from the desktop, ie I want to be able to right click and choose unmount?  

I just want the ability to single click to unmount a share, is this possible?

BB

---

### Post by anaconda on 2007-11-05
You could write a script and that would unmount it, (just like you did with the txt-document, which was a simpple script.) Then just make a launcher for that script.

The only problem is that you would have to type your sudo password. Each time you run the script.

---

### Post by BillGod on 2007-11-05
not a 100% sure on this one.. but couldn't you add a script to rc.local to run umount??

Side note..  if you hold in the power button on your laptop for 5 seconds it should ALWAYS power off.. you should never have to pull the batter.


edit damn anaconda beat me by like 30 seconds.

---

### Post by Bigbird999 on 2007-11-05
When I check the properties of the mount, it shows the owner as root, so I guess the question really should be, how do  I mount a share with the owner as user?

It must be possible, or else why is there an unmount option when the mounted drive is right clicked?  There must be a way!!

I have seen postings about chown, which I presume means change ownership, but for this Noob it is beyond me.

BB

---

### Post by filips01 on 2007-11-05
I think you'll just need to change the ownership of the folder you are mounting to.

```
sudo chown username /path/to/folder
```

---

### Post by Bigbird999 on 2007-11-05
> ernie@LinuxLaptop:~$ sudo chown ernie /media/MediaonErniepc
chown: changing ownership of `/media/MediaonErniepc': Operation not permitted


Now what?

BB

---

### Post by daengbo on 2007-11-05
You should try adding the share to /etc/fstab. The entry will be formatted similarly.

//192.168.0.11/E /media/MediaonErniepc smbfs noauto,user,user=ernie,password=xxx

You'll need to have the smbfs package installed (you should look into using CIFS, instead, though). The drive will appear in your Nautilus side-pane. Double-clicking should mount it for you and you will be able to right-click to unmount.

---

### Post by daengbo on 2007-11-05
Oh, also consider moving the password and user to a file that's not world readable and using the ?smbpassfile? option. Not sure about that option right now, and don't have it installed.

This general method works for NFS shares, too, which can't normally be mounted through Nautilus.

---

### Post by daengbo on 2007-11-05
OK. One more time. Look at this page:
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Consider adding the noauto and user options to allow for on-demand mounting.

---

### Post by Bigbird999 on 2007-11-05
I put this in /etc/fstab
> //192.168.0.11/E /media/MediaonErniepc smbfs user=ernie,password=xxx,uid=1000,umask=000,user   0 0 per a how to, it then mounts the drive when i do ```
sudo mount -a
``` and the properties say it is now owned by user, but only root can unmount it.  Then I found an obscure thread the said to change user to users```
//192.168.0.11/E /media/MediaonErniepc smbfs user=ernie,password=1206,uid=1000,umask=000,users   0 0
```  this mounts the drive when I suso mount -a and I can unmount it with a right click and unmount  HOORAY!!!!!!

When I changed fstab to > //192.168.0.11/E /media/MediaonErniepc smbfs noauto,user,user=ernie,password=xxxit placed a folder in Nautilus like you said but when I right ckick and select mount it says Unable to mount selected volume  -under details session setup failed errdos:no access (access denied)

FWIW, I can't believe how hard it is to get something this simple working.  I'm trying hard to LUV Linux but stupid things like this are pushing me back to Windoze.  

BB

---

### Post by Bigbird999 on 2007-11-06
So how do I go about using CIFS instead of Samba

BB

---

### Post by Bigbird999 on 2007-11-07
> So how do I go about using CIFS instead of Samba
Bump!!

---

