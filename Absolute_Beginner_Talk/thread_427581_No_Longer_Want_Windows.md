---
title: "No Longer Want Windows"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2007-04-29
i dual boot on my laptop and realized i do not need windows anymore.

now im wondering if there is a way to use the space windows is taking up in my harddrive and convert it for use in ubuntu. im happy with the way i have feisty set up now and everything is workin perfect so id rather not have to reinstall anything.  so 

can i shove windows out the window and use that space it was wasting and merge it with my preexisting ubuntu partition? 

thanks in advance:KS

---

### Post by oilchangeguy on 2007-04-29
you can use gparted. which is on the live cd.

---

### Post by Hmarroqu on 2007-04-29
can i install it on my system and not have to boot from the live cd?

---

### Post by supersonicdarky on 2007-04-29
delete windows partition > resize ubuntu parition

done.

---

you can install it, but you cant resize the ubuntu partition while logged in. you need to do it from the live cd.

---

### Post by Nythain on 2007-04-29
yes, you can install it on your system and dont need to use live cd... sudo apt-get install gparted should do the trick

---

### Post by oilchangeguy on 2007-04-29
no real need to install it. simply run the live cd, use gparted to resize the ubuntu partition. this will remove windows from the computer.

---

### Post by annda on 2007-04-29
however, you will not be able to resize the mounted partition - which is exactly what you want to do after deleting windows - supersonicdarky is right.

---

### Post by Billy McCann on 2007-04-29
> **Hmarroqu said:**
> i dual boot on my laptop and realized i do not need windows anymore.

congratulations! 

:guitar: 


Just follow the instructions these kind folks have given you.  You know, there *is* a Gparted LiveCD.  you don't have to go all the way into the Ubuntu LiveCD just to use Gparted.  

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I'm sure to always have this handy.  This and the Super Grub Disc, which comes in real handy when and if GRUB ever gets borked.

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

---

### Post by lepz on 2007-04-29
You can also use your windows install disk as a coaster, stops tea/coffee/beer stains on your tidy desk. :)

---

### Post by finferflu on 2007-04-29
You might mount that partition as your /home, so that in the occasion you wanted to reinstall Ubuntu, you wouldn't lose any of your settings. 
To do that you need to format it, gparted is fine, and give it a file system compatible with linux (ext, reiserfs, and so on), then you'll need to add to your /etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda6       /home           ext3    defaults        0       2

```
where <file system> is your device (in my case was /dev/hda6) and <type> is the file system you chose.
At reboot your home will be mounted on the new partition, if I can remember correctly..

If somebody could assure me of this last step I would feel more secure... my memory is quite bad, so I can't remember whether you had to move all your files from the old /home to the new one...

---

### Post by Hmarroqu on 2007-04-30
> **finferflu said:**
> You might mount that partition as your /home, so that in the occasion you wanted to reinstall Ubuntu, you wouldn't lose any of your settings. 
To do that you need to format it, gparted is fine, and give it a file system compatible with linux (ext, reiserfs, and so on), then you'll need to add to your /etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda6       /home           ext3    defaults        0       2

```where <file system> is your device (in my case was /dev/hda6) and <type> is the file system you chose.
At reboot your home will be mounted on the new partition, if I can remember correctly..

If somebody could assure me of this last step I would feel more secure... my memory is quite bad, so I can't remember whether you had to move all your files from the old /home to the new one...



i want to do this but i dont understand the adding to "/etc/fstab:" i dont have that...?

---

### Post by finferflu on 2007-04-30
> **Hmarroqu said:**
> i want to do this but i dont understand the adding to "/etc/fstab:" i dont have that...?
It's not possible, you should have /etc/fstab.
Just type in a terminal:

```
sudo gedit /etc/fstab
```

And you should be able to see the list in the Gedit text editor.

And since I've remembered the correct procedure, here you go. 
In the end you need to move your home folder (the one that bears your usename) in the new partition.

If you need more assistance, just ask ;)

---

### Post by Hmarroqu on 2007-05-02
im about to get to doing that but i have a precautionary question.  i notice that after i reformated that partition, one my grub still shows windows on there and two, it never auto mounts, i wonder if taht would be a problem with having that as my home folder?  also... mr finferflu, i followed ur link to jamendo and thats a very nice find i must say.:guitar:

---

