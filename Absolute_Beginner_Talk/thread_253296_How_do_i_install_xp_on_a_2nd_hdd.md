---
title: "How do i install xp on a 2nd hdd"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by dannythomas13 on 2006-09-08
hi everyone, i have been using ubuntu for a few months now but i need windows  to run kids games, mrs software etc etc so i thought it would be easier to have xp on a 2nd hdd rather than sharing the same.
so in this case i now have a hdd installed with ubuntu on it and i want to install a 2nd 160gb drive and have xp on it.
can anyone talk me through this as what i tend to see on the net is that people already have cp and want to install linux, however i am the other way round =)
i am not even sure if both need to be set to primary, that's how much i need help.
thanks in advance to anyone who replies.
Danny =)

---

### Post by dannythomas13 on 2006-09-08
ps, i dont know much about mbr's so i wouldnt like to keep repairing it if there is another way
thanks

---

### Post by Bud P on 2006-09-08
Hi:
I had a ton of problems trying to get 2 hard drives going, grub gave me fits so what I do is I got 2 hot plug hard drive bays and just jumpered both hard drives as master, when I want windows i just shut the machine off swap the hard drives and I am up and running with no problems. Of course one of the drive bays is just used to store the other drive that is not being used.

Bud P

---

### Post by dannythomas13 on 2006-09-08
thanks for the reply but this is not an ideal situation for me.

---

### Post by leftwing on 2006-09-08
> **Bud P said:**
> Hi:
I had a ton of problems trying to get 2 hard drives going, grub gave me fits so what I do is I got 2 hot plug hard drive bays and just jumpered both hard drives as master, when I want windows i just shut the machine off swap the hard drives and I am up and running with no problems. Of course one of the drive bays is just used to store the other drive that is not being used.

Bud P

That sounds quite strange to me. I have 3 hard drives (2 SATA and 1 old ATA) and everything works: I have several operating systems on the drives and GRUB can boot all...

---

### Post by dannythomas13 on 2006-09-08
hi, what i ahve done is connect my new hdd to sata1, the old one with ubuntu on to sata2, i have installed windows on the new hdd and windows works fine. however there is no choice of os when i startup.
so:
i used my ubuntu boot disc, got to the desktop, opened a terminal and typed:
sudo grub
at grub prompt i then typed
find /boot/grub/stage1
and i received hd(1,0)
so i then typed:
root (hd1,0)
then setup(hd1)
quit
sudo reboot

but still it boots straight into windows, can anyone help?
thanks

---

### Post by dannythomas13 on 2006-09-09
can anyone please help with this issue?? my pc boots straight into windows without giving me a choice at all. i dont really want to reinstall ubuntu though onto the second hdd as i can then just see more problems with mbr =(

---

### Post by bulldog on 2006-09-09
You installed grub on your Ubuntu hdd and you boot from your windows hdd so you won't see grub :D 

If yo have the choice,and most modern machines have,you can choose which hdd you want to boot by a setting in the BIOS or even by F11 or something like that by booting up.

If you gonna change it in your BIOS you have to set the path to your windows in grub manually in your menu.lst

If you can choose which hdd you wanna boot by F11 or something like that [you can see that when memory checks when booting up at the bottem of your screen]
you simply choose which hdd you want to boot from.

I have a simular setup and I boot from the Ubuntu hdd with grub and put in my menu list the following.

title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by slimdog360 on 2006-09-09
okay, did you set your windows hdd to master and Ubuntu as a slave drive (or maybe the other way around). Or did you just put the extra hard drive in there without setting the jumpers.
You will have to edit the grub to recognise Windows from your Ubuntu hard drive as grub will be installed on there. Hence you will have to (or it is easier to) set the jumpers on the hard drives. Ubuntu as the master and Windows as the slave.
 If you dont know how to do this just take out the hard disks and look at the top of them. There will be some writing on there telling you how to do this.
Then set your bios to boot from the Ubuntu hdd first. This will get you booting Ubuntu but not windows. Now all you have to do is edit your grub to recognise The other hdd.

here is an example of what how you can edit your grub [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/19644-how-add-windows-2k-xp-grub.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/19644-how-add-windows-2k-xp-grub.html")
you should put that bit of code just under the Ubuntu part in the grub, you will know it when you see it.

---

### Post by bulldog on 2006-09-09
> **slimdog360 said:**
> okay, did you set your windows hdd to master and Ubuntu as a slave drive (or maybe the other way around). Or did you just put the extra hard drive in there without setting the jumpers.
You will have to edit the grub to recognise Windows from your Ubuntu hard drive as grub will be installed on there. Hence you will have to (or it is easier to) set the jumpers on the hard drives. Ubuntu as the master and Windows as the slave.
 If you dont know how to do this just take out the hard disks and look at the top of them. There will be some writing on there telling you how to do this.
Then set your bios to boot from the Ubuntu hdd first. This will get you booting Ubuntu but not windows. Now all you have to do is edit your grub to recognise The other hdd.

here is an example of what how you can edit your grub [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/19644-how-add-windows-2k-xp-grub.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/19644-how-add-windows-2k-xp-grub.html")
you should put that bit of code just under the Ubuntu part in the grub, you will know it when you see it.

Sata drives are not controlled by jumpers anymore,but they are loaded in which connection they are eg. sata1 sata2 etc.
Because of that there must be an option in the BIOS to choose which hdd must be used to boot.

---

### Post by dannythomas13 on 2006-09-09
ok, i changed which hdd to boot from and i saw grub but now no os will load from grub however if i switch back to booting from windows hdd first it will go straight into windows

---

### Post by bulldog on 2006-09-10
That's correct.
You have to find out on which hdd Ubuntu is installed en the same for Windows.
Then alter your menu.lst and your fstab with the new settings and it will work.
For example do,

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. 
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next  commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

So you have found the settings for your Ubuntu in menu.lst and fstab.
If your windows is on a secondary hard-disk then you want to add these lines to the end of your /boot/grub/menu.lst -file

title Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

And if your windows is on the main hard-disk then add these lines:

title Windows NT/2000/XP
rootnoverify (hd0,0)
makeactive
chainloader +1

Actually you can add both of these and try booting with both of them.. and later delete the one, which didn't work...

---

