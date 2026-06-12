---
title: "Help; I can no longer boot (after update 15 sept?)"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by lorre on 2006-09-16
When I try to boot I get 
```

root(hd1,0) 
 Filesystem type is fat, partition type 0xb
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash

Error 15: File not found

Press any key to continue...
```

When I press a key I see the GRUB boot menu, every option (normal, recovery or memtest) gives the error described above.

I did nothing special yesterday, I do remember a 'computer must be restarted for updates' notification icon, but I did not do that and finished what I was doing and booted the computer this morning.

One other thing I notice is that when booting my pc I now get a grub loading screen just before the error. I had never seen this screen before.

What can I do to fix this?

---

### Post by petri on 2006-09-16
Grub error 15 means: [B]File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. [/B]
according to [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)

Check the previous grub menu at /boot/grub/menu.lst_backup (?) and compare it with the present menu.lst 

You can post them here too. 

My other pc does that sometimes. I reboot and then it works :confused:

---

### Post by lorre on 2006-09-16
Thanks I got it fixed, the kernel update incorrectly modified my menus.lst; the backup file could not fix that because it had the same incorrect modifications (hd0,0 became hd1,0 and sda1 became sdb1). When changing it all back all was good.

---

### Post by petri on 2006-09-16
Nice :) 

Do you have several kernels (Ubuntus) on your hd? I have and the latest installed is the grub thats working at boot. I don't use the latest installed  så often but I do do the updates when they are available and then I got these changes yu write about and grub stopped working.
I resolved it with installation of grub to that partition which I use most but everytime I update the others I do have to change the grub menu.lst manually.

---

### Post by lorre on 2006-09-16
It might have something to do with the way I installed ubuntu; first I had windows XP on sda and ubuntu on sdb. I removed windows XP, and moved ubuntu to sda. Anyway I'm glad it's all working again.

---

### Post by lorre on 2006-09-16
Since I no longer dual boot, I guess I no longer need Grub. Is it safe to uninstall it with synaptic? Will the MBR be ok and boot Ubuntu after removing Grub?

---

### Post by LadyDoor on 2006-09-16
> Since I no longer dual boot, I guess I no longer need Grub. Is it safe to uninstall it with synaptic? Will the MBR be ok and boot Ubuntu after removing Grub?

Grub doesn't take up a ton of room. It'd be better all around if you just kept it--if it's not broken, don't fix it, you know?

--Door

---

### Post by petri on 2006-09-16
You want grub to vanish? That's the default in systems with only one OS. Type this (copy) in terminal
```
gksudo gedit /boot/grub/menu.lst
```
Find line **timeout   10** and change it to for example to **1**

Find line **#hiddenmenu** and delete the **#**-sign. As you can see you have to hit **Esc** if you want the menu to reappear for example if you need to  get the **recovery boot**.

Save the file and exit. Reboot to see if it works. If it doesn't boot with LiveCD and yell at me. :-\" 

But that should do it.

---

### Post by lorre on 2006-09-16
> **LadyDoor said:**
> Grub doesn't take up a ton of room. It'd be better all around if you just kept it--if it's not broken, don't fix it, you know?

--Door

I know but apparently (automatic) kernel updates mess up my grub configuration, I don't know how often these updates occur but it's quite a hassle to manually fix the menus.lst every kernel update.

I leave it for now and go with Petri's suggestion.

Thnx for all the help.

---

### Post by petri on 2006-09-16
The hazzle you got at the first place was that you had removed a partition and moved the harddisks whithout modifying menu.lst. You have only one kernel for now and only one /boot so your menu.lst should be ok with the kernel updates.

[Here]("http://ubuntuforums.org/showthread.php?t=224351&highlight=howto+install+grub") is one guide how to reinstall grub if something goes wrong sometime.

---

### Post by bernied on 2006-09-16
If you read your menu.lst file, you will find the following:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdb5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)
```...etc...

That last line above (starting with '# groot=') determines which partition grub-update (which is run when you install a kernel update) uses for kernels. That will match with the 'root (hd1,1)' lines (or whatever yours is) in the ubuntu boot entries. Change that option, without uncommenting it, then the next time you install a new kernel, you will not have to update the menu.lst manually.

Check out the other automagic options while you're there.
Note that this is not part of grub per se, it is an automatic updater built by Debian, which was the Ubuntu base.

---

### Post by petri on 2006-09-16
Oh, that's nice bernied. Thanks :)

---

### Post by lorre on 2006-09-17
I did edit the menus.lst (and fstab) after moving ubuntu from sdb to sda; otherwise I would have gotten an error because sdb was empty after the move (during the kernel update I only had one kernel, sdb did not have an ubuntu installation). We'll see what happens next time..

---

### Post by petri on 2006-09-17
Ok, sorry I should have read better. :rolleyes: 

Then it must be as bernied says. I have changed all menu.lst files in my /boot's and eagerly waithin for next kernelupdate :biggrin:

---

### Post by lorre on 2006-09-17
Thanks bernied, I've updated #groot menus.lst with the correct setting. Bit strange it uses an outcommented setting when updating but if it works you don't hear my complain.

---

### Post by bernied on 2006-09-17
I's commented out because it is meant to NOT be read by grub. I repeat this is not a grub feature. The whole Automagic area is defined by:
```
### BEGIN AUTOMAGIC KERNELS LIST
.
.
.
### END AUTOMAGIC KERNELS LIST
```
This area gets altered by the grub-update script. Only the commands for grub are left uncommented. Within this area so-called comments with one '#' are actually commands for grub-update. A real comment in this area has '##' at the beginning.

This is the same reason why your Windows entries get deleted when you get a kernel upgrade, because they are inside this area. Leave them outside that area and grub-update will leave them alone.

Woah, sorry, I think it might be called update-grub, not grub-update. There's some more info here:
[http://www.penguin-soft.com/penguin/man/8/update-grub.html](http://www.penguin-soft.com/penguin/man/8/update-grub.html)

---

### Post by lorre on 2006-09-17
Thanks for clearing that up, knowing this all makes sense.

---

