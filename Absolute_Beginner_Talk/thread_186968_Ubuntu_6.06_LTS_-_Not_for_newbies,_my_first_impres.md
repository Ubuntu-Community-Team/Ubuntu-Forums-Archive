---
title: "Ubuntu 6.06 LTS - Not for newbies, my first impressions.."
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by kayrune on 2006-06-02
First off, I first tried Ubuntu when Flight2 was released, and has used it as my primary desktop since. I did a complete reinstall of Flight6 32bit and 64 bit for testing. 

Now with the final version released it was time for a fresh install again. 
I downloaded ubuntu-6.06-desktop-i386.iso booted it, and ran the "install". I only formated the / partition, I have /boot and /home on seperate partitions, and did not make changes to them. I did however create a new user, to start with a clean install. No problems, no errors... But after a reboot the "problems" begin..

First thing I notice is that my bootup reads Xubuntu (I had xubuntu installed before, maybe that's because I didn't format the boot partition) not really a problem... but...

1. I'm not connected to the internet! During setup, no questions where asked about my internet connection, it just assumed DHCP. In my case I have a static IP. On Flight install I was asked about my network connection.

2. I have no sound! This was not an issue with Flight installation. I don't know where to start. As I am a little familiar with linux I did try "sudo apt-get install alsa-utils" but it's already installed.. ](*,) 

3. Where are my NFS shares? when I try to mount a nfs share I get "mount: unknown filesystem type 'nfs'" This allways worked on flight install, although it was really slow on some of the flight until I notice portmap was not installed.

4. What about my screen resolution ? On Flight install I got to choose, now it just default to 1280x1024, and that's not nice on my native 1680x1050 display. The "change resolution" program doesn't give me 1680x1050 as an option

the first problem I resolved due to some previous experiences with ubuntu, the next 3 issues I will start searching the internet for a solution after a reboot (as I previous windows user, you allways try a reboot first) If I had no previous experience with Linux I'm guessing my windows cd would be in the drive about now...

---

### Post by meborc on 2006-06-02
NFS? ;) 

NTFS maybe...

---

### Post by kayrune on 2006-06-02
The saga continues....

A closer look at the Xubuntu issue gave me some ideas... maybe it was booting an "old" kernel.

By default it was booting the 2.6.15-23-K7 kernel, I guess this is a leftover from my flight days... So I changed it to 2.6.15-23-386 and it booted with ubuntu screen rather than Xubuntu... It was slower... But on the upside I now have sound.

odd thing though. Ubuntu 6.06 did not install a new kernel, probably because the one I had is the current one ? I will try to reinstall the K7 kernel now and see what happens...

This is so much fun...

---

### Post by kayrune on 2006-06-02
[QUOTE=meborc]NFS? ;) 

NTFS maybe...[/QUOTE]

No not NTFS, the NTFS drive is disconnected just to be sure ;) 

I'm talking about networking !!

I will look into your guides!

EDIT:

Reinstalling the K7 kernel (still dated may 23) and I now have sound and NFS working. Screen resoultion though... did not help installing nvidia-glx "nvidia-glx-config enable" does not work either.. however changing the driver manual from nv to nvidia and adding 1680x1050 in the xorg.conf did the trick... 

Now... the next mission is to get mouse and keyboard working perfect... I expect problems...

---

### Post by Dr. Nick on 2006-06-02
The sound issue is because of the new user, I had this before, only the 1st user gets sound. To remedy go to system- adminstration- groups in gnome and add the new user into the audio group and you should be fine, may have to hit the checkbox to show all groups.

Number 4 will require a edt to your xorg.conf file, open it and add the desired res in the same way the others appear

---

### Post by Klaidas on 2006-06-02
> 2. I have no sound! This was not an issue with Flight installation. I don't know where to start. As I am a little familiar with linux I did try "sudo apt-get install alsa-utils" but it's already installed..

Had this problem when I installed. Turns out my sound device was set now right. Everything works fine now ;)

> 4. What about my screen resolution ? On Flight install I got to choose, now it just default to 1280x1024, and that's not nice on my native 1680x1050 display. The "change resolution" program doesn't give me 1680x1050 as an option

Resolution/Refresh rate problems can be found on most of the distros. You have to set them manually if you don't find the proper one in the list :)

I think Dapper is way friendlier than previous releases ;)

---

