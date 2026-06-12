---
title: "quick fix, resoluton issues! cannot view ubuntu :("
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by mark. on 2008-04-19
okay, so this problem i have is that i tried to run something in wine, and the program said that my screen depth had to be 16 bits. 
so i went into the config file and changed it from 24 to 16. when i rebooted the gui, no visuals would show :(

i made a backup called xorg.conf.known-to-work before i changed it, and i just have to go into recovery mode to replace the file (im guessing). but i honestly dont know how to do that. can someone help me? 

thx in advance m8s :)

---

### Post by nicedude on 2008-04-19
you could boot with a live cd then type "sudo gedit /etc/X11/xorg.conf" without the quotes in a terminal window - that will open the file with root authority in an editor window, then just change it back and save it. Restart and remove live cd, This will not work though if your Ubuntu cd is the alternate install type only if its the standard live type. when you reboot make sure to remove the cd so your system can boot from your hard drive.

---

### Post by Google Spider on 2008-04-19
```
cp /path/to/file1 /path/to/file2
```


Copies the contents of file1 into file2. If file2 does not exist, it is created; otherwise, file2 is overwritten with the contents of file1.
[http://linuxcommand.org/lts0050.php#cp](http://linuxcommand.org/lts0050.php#cp)


**OR**

 you could do

```
dpkg-reconfigure -phigh xserver-xorg
```
This will change xorg.conf to the defaults.

---

### Post by mark. on 2008-04-19
okay, so i went into recovery mode and tried to

1 edit the file manually
2 replace with the backup file

but it said that the drive was mounted in read-only :/. so i was not able to edit it.

i also booted onto my live disk and opened the file itself, but the drive was still (for some weird reason) read only, so the screen depth is still at 16 instead on 24 :/. also, it said that i needed root permissions.

anyone know how to solve this? i am not sure on how to change a drive to be readable.

---

### Post by nicedude on 2008-04-19
When you booted with the live CD did you then open a terminal window ( Applications -> Accessories -> Terminal ) and then type or paste the command I said exactly like this

sudo gedit /etc/X11/xorg.conf

This should open the file in question with a text editor & give you root permission to it.
If you did do that command in terminal after the live boot then I don't know.

---

### Post by mark. on 2008-04-19
i did do that, and it said that my default depth was 24, so my only guess was that was the config file for the cd.

(when i manually went to the directory X11 in "disk", and opened xorg.conf it said 16 for default depth. and when i tried to change it to 24, it said it was read-only and that i didnt have permission.)

---

### Post by ryanhaigh on 2008-04-19
> **nicedude said:**
> When you booted with the live CD did you then open a terminal window ( Applications -> Accessories -> Terminal ) and then type or paste the command I said exactly like this

sudo gedit /etc/X11/xorg.conf

This should open the file in question with a text editor & give you root permission to it.
If you did do that command in terminal after the live boot then I don't know.

This will not open the file on his hard drive (real install) only the xorg.conf for the livecd session which will obviously not make any difference to the real install. You could do this from the livecd by mounting your root partition and then editing the file but there is little point in adding this complexity.

The easiest method was given before, you will need to boot into recovery mode and use ```
cp /etc/X11/xorg.conf.known-to-work /etc/X11/xorg.conf
```. The disk should NOT be read only if it is thats another issue, posting the output of dmesg and mount may help.

---

### Post by mark. on 2008-04-19
> **ryanhaigh said:**
> The disk should NOT be read only if it is thats another issue, posting the output of dmesg and mount may help.

so it is unrelated to my issue? 

also, how would i go about finding the dmesg and mount?

---

### Post by ryanhaigh on 2008-04-19
They are just commands you run and get the output from, but of course you need to be able to copy that output and given that you are running console only that may be a little tough. You could redirect the output to a file like this
```

dmesg > dmesg.txt
mount > mount.txt

```
But you would need to figure out a way to get those off your system and onto somewhere you could upload them here.
Perhaps if you have a look at the output of dmesg youself or even watch the text that is shown during startup you might be able to see what is going wrong with your filesystem.

---

### Post by mark. on 2008-04-19
^well actually i am running from my live cd, so i could upload anything or run a test code if needed, i just dont know how to get the "dmesg"s and such.

---

### Post by ryanhaigh on 2008-04-20
If your running from the livecd then the commands won't work because the output will have nothing to do with the installed system.

Running from the livecd you need to workout which partition is your / (root) filesystem. Open the terminal (applications>accessories>terminal) and use the following command to get a list of all partitions:
```
sudo fdisk -l
```
Post the output here if you cannot work out what partition is your /,

The next step will be to mount the partition (im using /dev/sda1 as and example for your / filesystem it may be different). In the terminal do this:
```
sudo mount /dev/sda1 /mnt
```

That will mount the partition and you can see whats on it and edit xorg.conf by pressing alt-f2 and entering ```
gksudo nautilus
``` which will open a filebrowser window as root so be careful! Find your xorg.conf file (should be at /mnt/etc/X11/xorg.conf) and replace it with your backup by copying and pasting (so you keep your backup). You can then restart your computer and boot into your normal system.

---

### Post by Saint Angeles on 2008-04-20
you don't need a live CD... i've done this plenty of times.

start up your computer in recovery mode. then change your xorg from there...

am i missing something?

---

### Post by mark. on 2008-04-20
^yeah, the problem was that my drive was in read-only.


the gksudo nautilus code worked, and i was able to change the screen depth. but when i restarted my computer, the logon window STILL didnt show up on my screen :/. 

is there anything else i can do?

---

### Post by ryanhaigh on 2008-04-20
Ok why don't you copy the xorg.conf.known-to-work file back over to xorg.conf?

---

