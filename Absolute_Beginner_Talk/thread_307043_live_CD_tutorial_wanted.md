---
title: "live CD tutorial wanted"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Rooinek on 2006-11-26
I have read in several linux forums that I can use a live CD for system recovery, but any instructions are written in geek-speak and make no sense to me. I have not had good luck with installing Ubuntu, as it destroys all of my other bootloader entries. I need my XP to be able to keep up with everything I normally do, and I have some things saved on the Beatrix partition that I would like to keep also.

I have a Beatrix 2005 live CD which shows the different "disks" or partitions, but am unable to access it in any way so as to be able to change any of the Grub entries. I right clicked on the "disk" and selected "mount volume" but I still cannot change anything in the /boot/grub/menu.list. Speaking of that, is there a file somewhere that I have to edit to make the bootloader read from the Beatrix menu.list instead of the newest install of Ubuntu 6.06LTS? That way, if a newer (edgy) Ubuntu install wipes out my grub again, with the help of the tutorial and the answers to these "dumb questions", I will be able to refer the bootloader to the Beatrix list in order to have at least one stable grub list. 

I hope I have used the right terminology here, as I am becoming very confused with this Ubuntu Linux thing which has cleaned out my computer several times now, and it has been Ubuntu (Hoary Hedgehog,Breezy Badger,Dapper Drake etc.)that has messed up, not Beatrix! The only two that have remained rock solid are Windows and Beatrix, but now, once again I cannot get to them, and do not want to have to re-install them for the umpteenth time!

Since Beatrix is based on Ubuntu, I was hoping that someone here can point me to a step-by-step tutorial on how to use the Ubuntu or Beatrix live CD to be able to get back my bootloader (Grub) with these entries : hda1 is Windows, hdb7 is Beatrix, hdb 8 is /home, hdb10 is Linux swap, and hdb 11 is Ubuntu 6.06LTS. 

I am using the Beatrix CD right now to be able to write this request. Yes, I have been told already that my grub is a mess, but I'm still trying to learn, little by little. 

I am not a geek, so the tutorial must be written for a Linux illiterate ](*,) ](*,) .

---

### Post by kelbizzle on 2006-11-26
I've had to do it before. The cheap way is installing the windows cd. Then when it asks you to remove the cd and reboot. You'll have the microsoft boot loader. 

I've done it that way and the following way.

Boot into the LiveCD.
Open a Terminal Session and become root by typing this:
```
 sudo su -
```

Now let’s launch grub.
```
grub
```

We’re going to find out where Grub should boot from.
```
find /boot/grub/stage1
```

Your output should look something like this (it’s what I get) (hd0,2). That’s your hard drive/partition. Once we’ve got that info, we can tell grub where your root directory is, and where the MBR should be.
```
root (hd0,2)
setup (hd0)
```
Now all that’s left is to quit grub and restart
    ```
quit
```
   ```
shutdown -h now
```
Once your machine restarts, you should see the grub menu again and you can go on your merry way.

---

### Post by Rooinek on 2006-11-26
Thanks, I'll give that a try and get back to you! ;).:)

---

### Post by Rooinek on 2006-11-27
```
setup (hd0)
``` got this response ```
error 27 unrecognized command
```
 So that didn't work ..... and I tried it with both Ubuntu and Beatrix live CD's.

---

### Post by kelbizzle on 2006-11-27
I'm sorry I don't know more about what I'm talking about. I only make notes with every problem I encounter to try and help. I just did a quick google search for "fix grub from live cd" I found this [http://ubuntuforums.org/archive/index.php/t-89898.html](http://ubuntuforums.org/archive/index.php/t-89898.html)

I was thinking you could also reinstall grub from the live cd or just edit the file. (this is my theory) I'm willing to learn with ya though.

---

### Post by kelbizzle on 2006-11-27
I found a guy who said this 
>  xp
xp will kill your grub but you can fix that
boot into ubuntu live cd and type

```

sudo /sbin/grub-install /dev/hda
```



That should fix it.

---

