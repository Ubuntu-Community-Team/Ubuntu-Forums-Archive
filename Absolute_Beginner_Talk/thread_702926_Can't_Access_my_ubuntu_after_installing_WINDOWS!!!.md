---
title: "Can't Access my ubuntu after installing WINDOWS!!!!!"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Tachions on 2008-02-20
I installed Ubuntu first on my desktop, and eventually took the plunge to M$ XP for whatever reason, wishing I didnt, but now grub wont show up, only boot to xp. any way to fix that without getting rid of the partition my ubuntu setup is installed on, bc I have a lot of important files, like pictures and music i do not want to get rid of.. please say I didnt mess it all up. thanks in advance!

---

### Post by overdrank on 2008-02-20
> **Tachions said:**
> I installed Ubuntu first on my desktop, and eventually took the plunge to M$ XP for whatever reason, wishing I didnt, but now grub wont show up, only boot to xp. any way to fix that without getting rid of the partition my ubuntu setup is installed on, bc I have a lot of important files, like pictures and music i do not want to get rid of.. please say I didnt mess it all up. thanks in advance!

HI and this link should help
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Tachions on 2008-05-01
bump

Hi still having trouble booting into Ubuntu, I even downloaded super grub disk and it worked to boot me into Ubuntu, but then if I want to boot back into Windows, either it is a struggle or I can then I dont have a boot manager or do you call it grub to give me the option to boot back into Ubuntu, what am I doing wrong? any ideas?!? thanks a lot for yout time.

---

### Post by Aearenda on 2008-05-01
Did you try the suggestion overdrank gave you? It seems to solve your problem to me.

---

### Post by cybercookie72 on 2008-05-01
I am having grub prob too...error 22...I was wondering-> I have 3 drives and I think sdb is where linux is and sda (removable drive)...

well my question is what is the hierarchy

what does sda or sdb mean compared to the whole (hd1,0) or (hd0,0)??
and whats up with the mnt vs media folders?

I went to the site listed above and did what was suggested and it doesn't work in my case.

on the find I get (hd1,0)....

the other night when i got the error 22 ::press any key I went to edit the root entry and for no reason I changed it to (hd0,0) and booted in to linux...but next boot I was back to error 22.  

My cat thought pepsi looked cool on my keyboard and I had to pick up a usb one...but it doesnt work when I get to the error 22 msg (not sure why...it works to make changes to the bios).  I am getting a keyboard like the old one Fri and will try the (hd0,0) thing again.  

but I would like to know I guess how grub is set up?  Thanks for any help...

-----------------------got it fixed----------------------------------
I booted in to the livecd  
mounted the drive /media (what is the diff between mnt and media?)
cd /media/disk/boot/grub and "sudo gedit menu.lst)
went to the bottom of the file and changed the entries for all 3 things from "(hd1,0)" to "(hd0,0)"
rebooted and woots it works

I still dont understand how grub works..anyone got a website?
or 
what the diff between mnt and media?

---

### Post by Aearenda on 2008-05-01
cybercookie72: Grub uses different notation from Linux for the disk drives.
Drive sda is usually (hd0) in grub.
Partition sda1 is then (hd0,0) in grub.
Partition sda2 is (hd0,1)
Partition sda3 is (hd0,2) and so on.

If you have a second drive, Linux will call it sdb, with sdb1, sdb2, sdb3 etc for partitions. The Grub equivalent will depend on where it is connected, but it will probably be (hd1) with partitions (hd1,0), (hd1,1), (hd1,2) and so on.

/mnt is the place for manual mounts
/media is where automatic mounts happen

To make changes to Grub settings permanent, you need to edit the file /boot/grub/menu.lst when Ubuntu is running. Look for the hd(x,y) entries. Make a backup of the file first, and don't mess with the '#' markers!

I suggest you start a new thread with details of your problem if this doesn't get you going - your issue is different from Tachions'. Post your /boot/grub/menu.lst and /etc/fstab, and the output from sudo fdisk -l /dev/sdx for each of your drives, replacing 'x' with 'a', 'b' etc.

---

### Post by bumanie on 2008-05-02
post the output of > sudo fdisk -l and > cat /boot/grub/menu.lst (that's a lower case L)

---

### Post by Aearenda on 2008-05-02
And it should be 'fdisk' not 'fdsik' - sorry!:redface:

---

### Post by bumanie on 2008-05-02
> **Aearenda said:**
> And it should be 'fdisk' not 'fdsik' - sorry!:redface:

Thanks for pointing out the typo. I have corrected it.

---

### Post by cybercookie72 on 2008-05-03
thank you both aearenda & bumanie for your reply

aearenda THANKS for the run down... things are much more clear now!!!

like I said I got it fixed... not from any knowledge on my part....
I just figured I really couldn't hurt things more (I wasn't able to get in to linux as was)

one more question...
menu.lst was on the drive were I reinstalled ubuntu 
why didn't reinstalling ubuntu fix the problem?
wouldn't reinstalling ubuntu have written the menu.lst again after everything was nuked?

thanks again for all your help

---

### Post by Aearenda on 2008-05-03
Glad it's all ok now.

See [http://www.ibm.com/developerworks/linux/library/l-bootload.html](http://www.ibm.com/developerworks/linux/library/l-bootload.html) for a rundown on Linux bootloaders, and [http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html) for gory detail on Grub.

I don't know why reinstalling didn't fix it. It does rewrite menu.lst. I'm wondering if there is something odd on your PC (as with several others on these forums) where adding removable drives changes Grub's view of where things are, so leading to failures to boot when such drives are (or are not) present at boot time compared to install time.

---

### Post by Tachions on 2008-05-04
hey guys when i use the outline, after i run the live cd and use a termianl, and access  into grub with the commands, after the third command i input, right after (root (hd0,1), i type in setup (hd0) I get the error 17: cant mount selected partition...

any ideas why?!? thanks

---

### Post by cybercookie72 on 2008-05-04
when you are in the livecd...where you get error 17...do you have your drive mounted??  I ask this cuz I have like 3 diff drives and got a mounting error once while trying to mess with menu.lst

---

### Post by Tachions on 2008-05-04
> **cybercookie72 said:**
> when you are in the livecd...where you get error 17...do you have your drive mounted??  I ask this cuz I have like 3 diff drives and got a mounting error once while trying to mess with menu.lst

I figure it is mounted, unless there is a special command i need to type in, i just figure it is because i boot my computer to the live cd. does that work?!? thanks

---

### Post by Aearenda on 2008-05-04
For Grub Error 17, maybe the steps in this thread will help: [http://ubuntuforums.org/showthread.php?p=3518911#post3518911](http://ubuntuforums.org/showthread.php?p=3518911#post3518911)

---

### Post by Tachions on 2008-05-04
Hey guys the step by step guide ended up working for me, i was typing in the wrong (hd0,1) when my computer specs were (hd0,0), it just boots me into ubuntu with the option of pressing the "esc" to access Windows, I dont prefer it like that, my laptop is dual booting but shows up a menu to pick ubuntu or windows... any way to get it to look like that?!? thanks for your time.

---

### Post by Aearenda on 2008-05-04
Yep, you need to backup and then edit /boot/grub/menu.lst, add a '#' before 'hiddenmenu' and change the timeout value to something a bit longer.

```
gksudo gedit /boot/grub/menu.lst
```

Find the bit shown below and adjust to your liking:
```


## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	 10	

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue


```

Take care not to change anything else!

---

