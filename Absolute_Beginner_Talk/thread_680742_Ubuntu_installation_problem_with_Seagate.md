---
title: "Ubuntu installation problem with Seagate"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by cooltrigger on 2008-01-28
hi guys,
it seems that my seagate's HDD dont like ubuntu. the installation works on my other 2 desktops and on my laptop fine but not on my desktop where i have the seagates in it. cant find anything helpfull to solve this problem. someone have any ideas?

---

### Post by espressopigeon on 2008-01-28
What does Ubuntu say when it fails? When does it fail?

---

### Post by cooltrigger on 2008-01-28
right after i click the installation the indicator starts runing and then i end in a shell command line which says:
udevd-event[2326]:run program: '/sbin/modprobe' abnormal exit

---

### Post by espressopigeon on 2008-01-28
What are your hardware specs?

---

### Post by cooltrigger on 2008-01-28
i am running a AMD athlon XP2500+ (1.83Ghz) , 512Mb RAM, NVIDIA Geforce4 MX 440 with AGP8x, 1X seagate 80Gb, 1x seagate 40Gb

---

### Post by bumanie on 2008-01-28
You should have continued the same post. Anyway, did you try to edit the /boot/grub/menu.lst? as shown in the second post?
It worked for a couple of people. To open the lsit for editing, in terminal type
sudo gedit /boot/grub/menu.lst
Find these lines and add the cloured section as here
root (hd0,0)
kernel /vmlinuz-2.6.22-14-386 root=UUID=... ro quiet splash[COLOR="Red"]_all_generic_ide[/COLOR]
initrd /initrd.img-2.6.22-14-386 and then save
If that doesn't work you can return to to the gedit list and delete what you have added.
No harm in trying.

---

### Post by cooltrigger on 2008-01-28
hi bumanie,
sorry forget the other post :-) i am totaly new to that so i dont know how i can edit the boot line. please can you give me a step by step info?
should i enter this after the shell windów appears? and how can i save anything in that window?

---

### Post by Sidewinder1 on 2008-01-28
CoolTrig, just so that you don't get discouraged, I recently installed ubuntu onto, what used to be my 'F:" drive in Windoze, and it went without a hitch. The drive? Seagate 80 Gig, may even be the same as yours. Hang in there...

---

### Post by bumanie on 2008-01-28
Applications--> Accessories-->  terminal
Interminal type 
sudo gedit /boot/grub/menu.lst (that is a lower case L) --> hit enter
put in your password when asked, then the gedit list will appear.
The trick will be to find the lines as pointed out above (I am at work on windows machine, so can't look at my list to help you - sorry)
When you find the lines mentioned, type in the ones in red. Then there is a save icon at the top of the gedit box. Click that and you're done.
If it doesn't work repeat the process of 
sudo gedit /boot/grub/menu.lst (that is a lower case L) --> hit enter put in your password when asked, then the gedit list will appear.
Remove the lines you added and save again and you will be back where you started ie no changes to your system.
You have nothing to lose by trying, because you can reverse your changes if they don't work.

---

