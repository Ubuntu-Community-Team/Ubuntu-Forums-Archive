---
title: "x server says its not configured on fiesty"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Kedster on 2007-09-03
OK its the first time iv posted on the forums  
I am having a problem with the Xserver when i boot up the Feisty kernel it says that the xserver is not configured and has been turned off (NOT AN EXACT QUOTE)

I am using a duel boot system with windows and Feisty on it. I had just installed dapper on Saturday 1 sept. then on Sunday. i upgraded to Edgy then to Feisty then i booted it up and played for a bit then i booted windows and back to Ubuntu and the did the same again for reasons that i had to do stuff in window but wanted to play around in Ubuntu but after booting into Ubuntu a few times i and this happened.

I tried to configure it by using the command 
> sudo dpkg-reconfigure xserver-xorg 
but it didnt work i don't now what setting i need to use so. 
i lloked around the threads and it sied to install beryl because it reconfigures the xserver but i think that it was a bogass post cuz it didn't work 

i have a del inspiron 1150 with an Intel(R) 82852/82855 GM/GME Graphics Controller

PS: i am a pure beginner please explain

---

### Post by taurus on 2007-09-03
If you are not sure about answers to questions when you run that command to reconfigure your X, just use the default and try to use **vesa** driver for now until you get X up and running again.  Then, install the driver for your graphic card.

p.s.  For now, stay away from beryl.

---

### Post by Kedster on 2007-09-03
i tried vesa do u have to do anything after the config is done cuz i might not be doing it right

---

### Post by taurus on 2007-09-03
When it's done, just see if X runs with

```
startx
```
And if you get an error message, post the whole thing here.

p.s.  What's the spec of your machine, especially the video card, anyway?

---

### Post by Kedster on 2007-09-03
i tried vesa do u have to do anything after the config is done  sorry it so long thing happended

---

### Post by Kedster on 2007-09-03
please

---

### Post by taurus on 2007-09-03
Do you have a LiveCD and does it work on your machine?

Otherwise, post your /etc/X11/xorg.conf here.

---

### Post by Kedster on 2007-09-03
umm i have a cd but it of dapper

---

### Post by taurus on 2007-09-03
That's fine too.  Now, does Ubuntu run from the CD with Gnome--window manager?  If it does, maybe you just have to copy /etc/X11/xorg.conf from the CD to your harddrive and see if everything is working then.

---

### Post by Kedster on 2007-09-03
ok ill try it il reply in a bit

---

### Post by Kedster on 2007-09-03
well the cd wont let u mount the hard drive

---

### Post by taurus on 2007-09-03
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That would be lower case letter L, not 1.

---

### Post by Kedster on 2007-09-03
disk /dev/sda: 60.0 60011642880
255 heads, 63 sectors/track, 7296 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

   divice boot      start        end         blocks  id   system
/dev/sda1           3433         3466        273105  82   linux swap
/dev/sda2  *        6            1917      15358140   7   hpfs/ntfs
/dev/sda3           1918         3432      12169237+  83  linux
/dev/sda4           3467         7296      30764475   b   w95 fat32

partiion table entries are not in disk order

---

### Post by Kedster on 2007-09-03
umm just so u no all that comes up ob=n the screen ever is the teminal its like dos for windows but its command line in ubuntu

---

### Post by taurus on 2007-09-03
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda3 /mnt/ubuntu
sudo cp /mnt/ubuntu/etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf.bak
sudo cp /etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf
sudo umount /mnt/ubuntu
```
Reboot and remove the CD.  Now, see if X is running this time from your harddrive.

Line 1.  Create a mount point.
Line 2.  Mount your Ubuntu which is on /dev/sda3
Line 3.  Make a backup copy of your original /etc/X11/xorg.conf on your harddrive.
Line 4.  Copy xorg.conf from the CD to your harddrive, replacing the old one.
Line 5.  Unmount your harddrive.

---

### Post by Kedster on 2007-09-03
noooooooooooooooooooo it never worked
 well thank very much for trying
is there any thin else that could be done

---

### Post by Kedster on 2007-09-03
help

---

### Post by nowshining on 2007-09-03
well i ur screenshot shows that u never did download the vesa driver - i didn't read all, but try again because you got a connection reset by peer error meaning that the connection from the repositories to you was interrupted by them..try re-downloading..
 
and is your video card exactly the same one as in my sig.. if all else fails since your so new to feisty - a format and re-install might help at this point which is solveable..



edit: or best would be is to wait a month for Gutsy to start using ubuntu which will have newer drivers incl. numerous bug fixes..

---

### Post by Kedster on 2007-09-03
well ill try it but i live in a smaller town i can only get a dapper disk and then upgrade to Feisty  
but im goin to look to see if i can get 7.04 
im 14 and my dad got me dapper because the guy at the store sied it had long term support so he got that one (my dads fixes comp he nows lot about how windows works but he want me to lern ubuntu and then teach him lol) but he doesent remember if the 7.04 disk was there but if not then ill re-install dapperand upgrade the same way i did the first time

---

### Post by nowshining on 2007-09-03
actually you can get a cd for FREE you pay NOTHING except your time to wait and that's why i also still suggest to wait for Ordering Gutsy.. :) 'cause it MAY take awhile to get them...it took me about 3months or so to wait..
 
shipit.ubuntu.com
 

:)



edit: of if you have a FAST INTERNET connection you can download an iso and burn it to a CD/DVD and do it from there...

---

### Post by Kedster on 2007-09-03
fast net but bad berner and i already did a re-instal of dapper
THANK TO EVERY ONE

---

