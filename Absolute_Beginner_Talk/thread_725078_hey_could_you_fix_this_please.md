---
title: "hey could you fix this please"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by sanjay.srikanth on 2008-03-15
hey guys please help me out....i have installed 7.10 and updated the synaptics package manager ....then installed the all the package contents...then it asked to restart my system.when i restarted it gives me an err.....it used to boot normally when i didnt update ubuntu...but now it comes till the ubuntu loading and then after 3 min it falls out into a bw screen with the message poping..the err isBusyBox 

v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) :confused::confused:


hey please dont tell me to re install ubuntu....

---

### Post by glennric on 2008-03-15
After you updated synaptic, you say you installed all of the package contents.  What does you mean by that?  Do you mean you installed all of the updates?

Anyway, try exiting the busybox (by typing exit, then enter) and see if it continues booting.  If that doesn't work you will need to boot to a live cd to fix it.

---

### Post by sanjay.srikanth on 2008-03-15
yaah i tried buy givin the exit command many a times but it did nt work...
can u tell me how to fix the problem usin the live cd.....and could u also tell me how to login as a root...

---

### Post by glennric on 2008-03-15
You don't need to log in as root.  Just use "sudo" in front of any command that needs root access. 

Now boot to a live cd.  Then you will have to mount the root partition of your hard disk.  So create a directory to mount it somewhere.  Then type 
```
sudo mount /dev/??? /path/to/mount/directory
```
You will of course have to figure out what partition is your root directory, and know where you created the mount directory.  
Then type
```
sudo chroot /path/to/mount/directory
```
Then try
```
sudo update-initramfs -u
```
Then type "exit" and to be safe "sudo umount /dev/???"
Then reboot and see if that helped.

---

### Post by sanjay.srikanth on 2008-03-15
thanks man...i guess this is the solution....i ll check it out

---

### Post by sanjay.srikanth on 2008-03-15
hey could u give me step by step instructions...actually i dont know anything....like i have done booting...but i dont know how to find the root partition(what is this exactly...is it the drive in which i had installed ubuntu or the cd rom in which i have inserted the cd or the windows partition..)...if its the drive in which i have installed ubuntu then..its like this
/dev/sda2...........extended
        /dev/sda5.....ext3
        /dev/sda6.....linux-swap
please give me the exact instructions....please.....:confused:

---

### Post by glennric on 2008-03-15
Yeah, it looks like your root is on /dev/sda5.  So make a mount point, for example
```
sudo mkdir /media/disk
```
Then mount with
```
sudo mount /dev/sda5 /media/disk
```
Then
```
sudo chroot /media/disk
sudo update-initramfs -u
exit
sudo umount /dev/sda5
```
Then reboot.

---

### Post by cdinz on 2008-03-15
You have an Acer 4520.... So just do this:
At Grub prompt, press 'e'
Select kernel and press 'e' again.
Now add the kernel option "all_generic_ide" after "splash"

After booting, you can edit the same in /boo/grub/menu.lst

---

### Post by sanjay.srikanth on 2008-03-15
thanks dinesh...it worked

---

