---
title: "Complete PC image possible? Mac4Lin and Compiz nOOb-safe?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by TheNorthWaves on 2007-12-24
I am happy to say that my dual-boot vista/7.10 was successful on a Lenovo T61. Hooray for winter break and the people on this forum!

A few questions I have now, and hopefully I can be pointed in the right direction. Keep in mind, I've used the terminal maybe 3 times in my life.

1) After all of this work, I'd really like to make an exact image of my computer in case something gets completely messed up. I have an external drive with enough space - does something exist that would allow me to make a COMPLETE image, so I could easily restore the computer with both the installs? Free is desirable.

2)I have read about Compiz/xgl and the mac4lin desktop. I am interested in trying these setups, but at this stage is it all noob-friendly to set up (major customization being another topic), or should I chill out for a while and learn due to serious risks/terminal usage/etc?

Thanks again everyone.

---

### Post by Capricori on 2007-12-24
Regarding your first question - no idea :) But I would imagine that software exists that would allow you to make an iso of your current setup in its current state. If not, you could just copy everything into a folder and archive/compress it into a .tar.gz (something like .zip on Windows). If something should happen and you wanted to restore it, you could probably get away with uncompressing the folder and copying everything back. There are probably circumstances where this wouldn't work though.

As for your second question, I don't know how much command-line stuff is involved with those setups, although a lot of things tend to be quicker if you can cope with a terminal :) Plus, if something goes badly wrong, its always good to be able to drop back into a terminal, so I would recommend learning a little bit first :)

Regards,
 
Capricori

---

### Post by LaRoza on 2007-12-24
See the link in my sig for CloneZilla. It can do partitions and whole drives and restore them.

It will take a while, but it works.

It is a bootable disk.

---

### Post by TheNorthWaves on 2007-12-25
yikes - clonezilla screenshots sure have scary quality of english! But if it does the job, it''s PERFECT. I ran through the steps/screenshots but I'm honestly not confident as to what selections I'm supposed to choose. Does anyone mind providing a quick lowdown on what to select?
 
Goal: entire HDD (containing NTFS, FAT32, EXT3 and linux-swap partitions, Vista, 7.10 and data) needs to be imaged in its entirety including settings and personal stuff, and backed up to a partition on an external HDD (this partition can be formatted as desired). I need to be able to use that image to restore my computer to its last-imaged state and start using it again, if a major failure occurs. 

Thank you all so much!

---

### Post by lamalex on 2007-12-25
do you want to image it to an iso file so you can move it later maybe? or a direct copy to the blocks so theoretically you could boot to your back ups?

---

### Post by rkd on 2007-12-25
I agree -- those screen shots didn't explain anything.

I found an article that seems to give sensible directions for using Clonezilla here:

[http://www.linux.com/feature/115208](http://www.linux.com/feature/115208)

Of course, what seems clear when just reading it might turn out to be not so clear when you are in the middle of the process.  When you do it, go slow, read the article carefully, and if you get confused, stop the process and post your question.  You'll probably get through it without problems, though.

---

### Post by TheNorthWaves on 2007-12-25
I have an excellent warranty on the laptop so i'm not worried about having to boot from an external drive - they'll overnight me a new HDD if it fails. What is more important to me is the ability to then completely copy that image back over to a new HDD and use it with little problem.

---

### Post by torgrot on 2007-12-25
At the risk of bringing down the linux absolutes, might I suggest Acronis True Image Home.  It will backup up the entire system if you want.  It has a bootable disk that runs linux and it can back up your entire system while running windows, which is much faster as they have better drivers.  It costs about $50, but it will do all that you ask.

torgrot

---

### Post by LaRoza on 2007-12-25
> **torgrot said:**
> At the risk of bringing down the linux absolutes, might I suggest Acronis True Image Home.  It will backup up the entire system if you want.  It has a bootable disk that runs linux and it can back up your entire system while running windows, which is much faster as they have better drivers.  It costs about $50, but it will do all that you ask.

torgrot

So will CloneZilla. I used it with no problem.

---

### Post by onero on 2007-12-25
I don't have experience with 1), but regarding Compiz, it should be pretty noob-friendly since it comes with Ubuntu 7.10 by default :) Go to Appearance (under System > Preferences), then go to Visual Effects to enable compiz fusion (choose normal or extra). If your graphics card is supported, basic effects should be enabled now. To further customize your visual effects, install compizconfig-settings-manager from synaptic.

Regarding Mac4Lin, here's a detailed guide: [http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

---

### Post by TheNorthWaves on 2007-12-25
With clonezilla, if my HDD fails and I have an image on the backup drive...
I put in a new hdd, boot from clonezilla CD, transfer image from extl hdd to new hdd, and voila? Or must I run gparted first? I noticed there's a livecd with both.

I don't really care how much time it takes to transfer, I'll let it sit for a day or two if I have to. It's not a major issue for me, it doesn't have to be a completely recent backup - just something to get me up and running quickly again after a failure. All of the data on my laptop is pretty much identical to what i've got on my mac desktop with time machine (ie: my data is safe anyway).

---

### Post by ijason on 2007-12-25
i give my vote to Partimage. it makes an image file (and can even compress it with gzip) of any partition you choose, and even only records used data, so you don't have to make an image the same size as the physical drive. 

google partimage to get their website, and download their system rescue cd. once you burn the disk, you boot off of it and then mount your computers hard drive and run partimage. it has a real easy gui and works very quickly. like, 4 minutes to back up 6 gigs.

---

### Post by ijason on 2007-12-25
**@ northwaves :** yes. the standard procedure is going to be you make a backup image of your drive, and hang onto it. then, when something breaks you'll boot the machine off a live-cd with a partition manager (gparted is very good) and reformat the drive if the data on it has become entire corrupt, but the device is still good. if the drive physically has failed, you'll format the new drive with gparted. then you'll reboot using the rescue cd and whichever program you choose to restore the image to the drive.

---

### Post by LaRoza on 2007-12-25
> **ijason said:**
> i give my vote to Partimage. it makes an image file (and can even compress it with gzip) of any partition you choose, and even only records used data, so you don't have to make an image the same size as the physical drive. 

google partimage to get their website, and download their system rescue cd. once you burn the disk, you boot off of it and then mount your computers hard drive and run partimage. it has a real easy gui and works very quickly. like, 4 minutes to back up 6 gigs.

CloneZilla has two compression algorithms and one uncompressed, including gzip.

(CloneZilla partially based on Partimage)

---

