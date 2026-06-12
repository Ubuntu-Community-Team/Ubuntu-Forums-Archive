---
title: "Help!!!!!!!!!!!deleted My Admin Acount+bootvirus"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by pugofdestiny on 2008-03-24
hello i have a major problem i love ubuntu as my os but im going to go back to windows because there are no virus's for ubuntu i know that much but i got a virus for my boot screen sadly so heres what happened...

i was deleting file folders from my home directory so i went to terminal and was typeing things like sudo rm -r filefolder /home/teko

but nowthat somehow deleted my administrator account so im stuck using my son's non-administrator account i cant boot cd's from my boot screen i don't have access to the user account editor or the partition manager and i cant boot from cd's on my boot screen so what do i do now?
is there something i can type in terminal that will completely format my harddrive?that will remove ubuntu and every single file (including the annoying virus) so that i can install windows???

if its any help i can get on root from my son's terminal because i know the password and i have fakeroot installed? anyone know what i do know to completely format my harddrive, remove ubuntu, and every othe file, from my son's ubuntu account. im pretty sure there was a command i could type in terminal but now i cant remember...

thanks in advance.

---

### Post by Paqman on 2008-03-24
OK, first of all, I don't think you have a  virus. When you say you can't boot from a CD, have you checked the BIOS for the boot priority? Is it set to boot from CD before the hard drive?

---

### Post by pugofdestiny on 2008-03-24
I'm almost positive its a virus i know this because i cant even go into and edit my bios settings because i cant even press any keys at my startup menu plus it says to boot from cd press any key but i cant press any key because of the boot virus.
so is there a terminal command i can use to format my hard drive?and delete ubuntu safely removing every file on my hard disk on the way? basically giving me a fresh virus free hard disk?

---

### Post by Jerry N on 2008-03-24
If you have a virus that is keeping you from accessing the BIOS, a new HD is not going to help!  Are you sure the BIOS hasn't been password protected?  You might try clearing the CMOS memory using jumpers as shown in the motherboard manual or by removing the CMOS backup battery for several minutes.  On a laptop computer, there might be a reset button, maybe in the battery compartment.  

Jerry

---

### Post by JoshuaRL on 2008-03-24
I would also like to support the opinion that it probably isn't a virus.  For all of Linux, there are less than 100 confirmed malware programs, and all of those have been patched out of being a threat.

Sincerely, it probably isn't a virus.

And there are ways to create a new sudo-level user, or to change the password of ones there so you can get into your system.  We can help you rescue your system, a full wipe and reinstall is not necessary.

---

### Post by jken146 on 2008-03-24
You don't have a Linux virus, don't worry.

You shouldn't use sudo to delete to files withing /home/yourUser.  You don't need to.

If the only thing that you did to disable your user was **sudo rm -r /home/teko** then you should do the following:

Boot into recovery mode (select this at the GRUB menu).  Type ```
mkdir /home/teko
``` then ```
chown teko:teko /home/teko
``` then ```
reboot
```

---

### Post by pugofdestiny on 2008-03-24
well thats the problem i can't boot into revoery mode because i dont have control over any keys at startup or in the boot menu thats my problem. so what can i type in terminal to completely wipe my hd 
?

---

### Post by JoshuaRL on 2008-03-24
Well, if you can't get into root or recovery mode, than you proabably can't type anything like that from the terminal in a non sudo account.

Do you by any chance have either a USB or wireless keyboard?  That might be the issue.

---

### Post by pugofdestiny on 2008-03-24
i have a ps2 keyboard and yes i can get into root i was in root and able to get my user account back but i still want to get rid of the boot virus so now that im on my admin account and can get into root what do i do now too completely remove everything off my hard drive?

---

### Post by JoshuaRL on 2008-03-24
Okay, what besides the keyboard issue tells you that you have a boot virus?  Have you tried the suggestion of Jerry N to pull out the CMOS battery?

In case I wasn't clear before, **I am 99% sure you don't have a virus.**  I'm not sure why you think thats what the issue is, but as Jerry N pointed out, if it's a boot virus or rootkit that's affecting the BIOS, then reformating the drive won't work.  It just won't, since it's affecting your computer before the hard drive even boots up.  But the problem with getting a rootkit or boot virus in Linux is that it would first need a security flaw in the OS to get down to that level.  The computer doesn't allow continual access to that area normally.

Now, please since you added a sudo user, get out of root.  If you're worried about getting hurt, this is the way.  Sudo and limited user priviledges are the primary security measure of Linux.

---

### Post by Rocket2DMn on 2008-03-25
OK.  There is no boot virus, let us put that to rest and be done with it.  If you are hitting the correct key to get to the BIOS/Setup or the Boot Menu from your initial boot up screen with the manufacturer's logo, then it's because your keyboard is not enabled yet.  USB and/or wireless keyboards are often a cause for this since many older computers do not enable USB until later in the boot sequence.  Common keys for getting to BIOS or Boot Menu are F2, F4, F8, F12, DEL, and ESC - you have to press them VERY quickly, and possibly repeatedly at the very first screen that appears when you turn on the computer, you only get a second to do it (literally).
You should see if you can get your hands on another keyboard to use if you still can't get to the BIOS to change the boot sequence, or scroll through the GRUB menu to get to the recovery kernel.

You can't wipe your hard drive from within Ubuntu since you can't format a mounted partition.  You will need your windows cd to install windows anyway, so you should pop that in.  Otherwise you can format the drive using the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) - obviously you can't use this unless you can boot from CD, at which point you might as well just overwrite it all from the windows install disc.  Either way, there's the option.

You can get a BIOS upgrade from your manufacturer if that will make you feel better, though this requires you to boot from a CD, floppy, or USB flash drive.

---

### Post by pugofdestiny on 2008-03-25
Just tell me what command formats my hard drive i heard someone mention it before but i dont know what it is.

---

### Post by Rocket2DMn on 2008-03-25
> **pugofdestiny said:**
> Just tell me what command formats my hard drive i heard someone mention it before but i dont know what it is.

Again, your drive cannot be reformatted while you are booted into linux.  You simply cannot change a partition that is mounted, and your root partition is mounted when you are inside linux (or any other OS for that matter).
The ONLY WAY to reformat your drive is to have it unmounted, that is why we use LiveCDs.  THAT means that you HAVE to be able to change your boot sequence to select to boot from the LiveCD, or from your Windows install disc.

You should see if you can get your hands on another keyboard that works during the early bootup sequence so that you can access your BIOS.  To be frank, if you can't do this, you are out of luck.

---

