---
title: "Getting errors trying to mount"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Cubedude04 on 2007-06-26
Hey, I made a topic before asking how to mount my /home drive i can't do it and the ways i try i am getting errors and is really frustrating me oh well =D hear i go

I have set up partitions 

/=the root and is 10gb

/swap=Swap and is 2 gb

/usr=this was an accident i made but it is 5gb

/home=39gb this is where i want to store my files 

When i start up i assume it automatically is using the / root partition. I want to mount my home partition to save all my work to but i don't know how 

I tried using the df -h command which gives me 

/dev/hda1             9.9G  2.2G  7.2G  24% /
varrun                253M  116K  252M   1% /var/run
varlock               253M  4.0K  253M   1% /var/lock
procbususb            253M  108K  252M   1% /proc/bus/usb
udev                  253M  108K  252M   1% /dev
devshm                253M     0  253M   0% /dev/shm
lrm                   253M   34M  219M  14% /lib/modules/2.6.20-16-386/volatile
/dev/mapper/hda4       39G  241M   37G   1% /home
/dev/mapper/hda3      5.0G  2.0G  2.7G  43% /usr

Then i typed 

sudo mount /dev/mapper/hda4 /mnt 

from what i understand as a new user that should make the mnt folder my /home partition or drive. It appears to because when i get the properties to the file it says 39 gb. but when i try and copy files to the folder by dragging and dropping it gives me an error

Error while copying to "/mnt".
You do not have permissions to write to this folder.

What am i doing wrong?

If i am not doing this correctly can someone please give me a step by step idiot's guide to mounting the /home drive

I am still trying my 100% best to learn linux and am grateful for any assistance i might receive

Thankyou in advance :D

---

### Post by aJayRoo on 2007-06-26
I may be missing your point entirely but I don't think you need to mount your home partition. the output of 'df -h' shows that you have 39GB of space mounted at /home. This means that your home partition is already mounted. I feel you may be confused as to the way this all works and are expecting your home partition to show up as a separate disk. This is not the case, when you click on places -> home (menu on gnome panel) you are in your personal home directory which appears to be a seamless part of the filesystem however all data you save there will be written to the partition you specified for /home.

In conclusion I don't think anything actually needs to be done here! It may look as though /home is not mounted but in actual fact it is. I'm not very good at explaining things like this so post back if you are unsure or I'm missing the point!

---

