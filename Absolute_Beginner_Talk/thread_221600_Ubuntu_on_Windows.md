---
title: "Ubuntu on Windows"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by Wotcher on 2006-07-23
Ok, I burned the Live CD and I rebooted with it in the CD drive.

Everything goes well, it boots up, I see the welcome screen and the options.

I choose the option "Start or Install"

Then everything goes well, but then while it's doing its thing, the screen suddenly goes black and starts saying this:

Uncompressing Linux... Ok, booting the kernel. pci_eisa : could not register EISA root
[ "a whole bunch of numbers here"] Buffer I/O error on device hdc, logical block 293524

It keeps repeating second message with different numbers in between the [...] and then at the end it has 293--- with different numbers at the end every time it says the message again.

Is there something wrong with my computer? I run windows fine on it. I have an Intel Celeron processor 2.20GHz

Please help! I've never use Linux before, and I'm not a techbuff.

-Danny

---

### Post by xXx 0wn3d xXx on 2006-07-23
> **Wotcher said:**
> Ok, I burned the Live CD and I rebooted with it in the CD drive.

Everything goes well, it boots up, I see the welcome screen and the options.

I choose the option "Start or Install"

Then everything goes well, but then while it's doing its thing, the screen suddenly goes black and starts saying this:

Uncompressing Linux... Ok, booting the kernel. pci_eisa : could not register EISA root
[ "a whole bunch of numbers here"] Buffer I/O error on device hdc, logical block 293524

It keeps repeating second message with different numbers in between the [...] and then at the end it has 293--- with different numbers at the end every time it says the message again.

Is there something wrong with my computer? I run windows fine on it. I have an Intel Celeron processor 2.20GHz

Please help! I've never use Linux before, and I'm not a techbuff.

-Danny

At what speed did you burn the cd ? What arch is it for ? (i386, ppc, 86_64) and please post more hardware specs.

---

### Post by Wotcher on 2006-07-23
I burned it at supposedly 40x but the real speed was around 2-5x.

The file I downloaded says: ubuntu-6.06-desktop-i386.iso

What hardware specs?

---

### Post by xXx 0wn3d xXx on 2006-07-23
> **Wotcher said:**
> I burned it at supposedly 40x but the real speed was around 2-5x.

The file I downloaded says: ubuntu-6.06-desktop-i386.iso

What hardware specs?

Try re-burning the cd at 2 or 4x.

---

### Post by Wotcher on 2006-07-23
> **Wotcher said:**
> I burned it at supposedly 40x but the real speed was around 2-5x.

The file I downloaded says: ubuntu-6.06-desktop-i386.iso

What hardware specs?

Ok, I'll try that. How will that help the problem though?

What do those error messages mean?

---

### Post by Wotcher on 2006-07-23
> **Wotcher said:**
> Ok, I'll try that. How will that help the problem though?

What do those error messages mean?

BUMP

---

### Post by catlett on 2006-07-23
```
Buffer I/O error on device hdc,
```hdc is your cd drive. Most likely the cd didn't burn correctly and the iso got corrupted. Burning at a slow speed will make it less likely for the burn to have an error. Fast burns are more likely to have errors so the suggestion to burn at 2 or 4x is just a good option to try without knowing anything else about the download or burn.
 The scrolling text is normal although the error isn't. Windows chooses not to show the system activity on boot but Linux does. 
You should do a md5sum check of the download before you burn it to disk to make sure the download didn't get corrupted. This is a great guide for downloading and burning the iso.[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)
There is also a "check the CD for defects" option where you chose "start or install" you may want to boot to your CD again and select that option to verify if there is something wrong with the CD before you burn another one.

---

### Post by Wotcher on 2006-07-23
> **catlett said:**
> ```
Buffer I/O error on device hdc,
```hdc is your cd drive. Most likely the cd didn't burn correctly and the iso got corrupted. Burning at a slow speed will make it less likely for the burn to have an error. Fast burns are more likely to have errors so the suggestion to burn at 2 or 4x is just a good option to try without knowing anything else about the download or burn.
 The scrolling text is normal although the error isn't. Windows chooses not to show the system activity on boot but Linux does. 
You should do a md5sum check of the download before you burn it to disk to make sure the download didn't get corrupted. This is a great guide for downloading and burning the iso.[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)
There is also a "check the CD for defects" option where you chose "start or install" you may want to boot to your CD again and select that option to verify if there is something wrong with the CD before you burn another one.

Ok, I don't know what a md5sum is.

And I did select the option to check the CD for defects; after a while it went to the same black screen and presented the same error, over and over and over and over.

---

### Post by Wotcher on 2006-07-23
> **Wotcher said:**
> Ok, I don't know what a md5sum is.

And I did select the option to check the CD for defects; after a while it went to the same black screen and presented the same error, over and over and over and over.

EDIT: Ok, I'll go over your instructions, thanks for that.

---

### Post by Wotcher on 2006-07-23
> **catlett said:**
> ```
Buffer I/O error on device hdc,
```hdc is your cd drive. Most likely the cd didn't burn correctly and the iso got corrupted. Burning at a slow speed will make it less likely for the burn to have an error. Fast burns are more likely to have errors so the suggestion to burn at 2 or 4x is just a good option to try without knowing anything else about the download or burn.
 The scrolling text is normal although the error isn't. Windows chooses not to show the system activity on boot but Linux does. 
You should do a md5sum check of the download before you burn it to disk to make sure the download didn't get corrupted. This is a great guide for downloading and burning the iso.[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)
There is also a "check the CD for defects" option where you chose "start or install" you may want to boot to your CD again and select that option to verify if there is something wrong with the CD before you burn another one.

THANK  YOU so much catlett!

It worked, I followed your instructions and used the programs on the website you gave me and I am now running Ubuntu from the Live CD. It's running VERY slow because it's running live.

I'm a little hesitant about installing it on my hard drive and making a partition and everything. I've never partitioned my hard drive. It's 40GB and Windows is using about 20GB. How much space should I give to Ubuntu? How does the partitioning work?

Thanks again for your help.

-Danny

---

### Post by theratster on 2006-07-23
I also have a 40GB harddisk. In reality, it comes to about 38.5 GB, so when I partitioned it, I just put 7.5 GB for Ubuntu, and 1GB for the swap. It leaves lots of room to install stuff and play around, in both linux as well as windows.

---

### Post by TravisNewman on 2006-07-23
depends on how much you want to add to it later. 10 gigs should do you just fine for most cases. You only need about 2 for the default install, but you'll most likely add more later and it's always a good idea to have a lot of extra. :)

---

### Post by Wotcher on 2006-07-23
> **panickedthumb said:**
> depends on how much you want to add to it later. 10 gigs should do you just fine for most cases. You only need about 2 for the default install, but you'll most likely add more later and it's always a good idea to have a lot of extra. :)

So, that means that I'll have to choose the third option and do the partition manually? Like choose how much goes where and stuff?

-Danny

---

### Post by Sef on 2006-07-23
> So, that means that I'll have to choose the third option and do the partition manually? Like choose how much goes where and stuff?

Read this excellent tutorial on [How to Dual Boot.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by theratster on 2006-07-24
Yup. that is the best way.

---

### Post by lapsey on 2006-07-24
there are plenty of partitioning tools with which to resize partitions on the fly, like gparted

---

### Post by catlett on 2006-07-24
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) This is the installation part of the link I gave you earlier. The site was created by Aysiu. If you stay around the forums a bit you can't miss Aysiu and the site is just great.
You can choose the first option. I attached the frame from Aysiu's site below.
That option will resize your partition, make partitions for ubuntu and then install.

---

### Post by GuitarHero on 2006-07-24
I would give Ubuntu about 10 at least.  Make sure to defrag windows a couple times before you do it and back your files up.  Partitioning just makes separate sections of your harddrive.  Its kinda like splitting your hard drive up into separate hard drives, but just not in a physical sense.

---

### Post by Wotcher on 2006-07-24
> **theratster said:**
> I also have a 40GB harddisk. In reality, it comes to about 38.5 GB, so when I partitioned it, I just put 7.5 GB for Ubuntu, and 1GB for the swap. It leaves lots of room to install stuff and play around, in both linux as well as windows.

What's a swap?

I'm terrified of messing around with my HD. I'm seriously considering buying an extra HD. What happens when I partition my HD? What if I want to take Linux off and have the whole HD for Windows only again? (In other words have it the way it was before I created a partition for Linux.)

-Danny

---

### Post by Wotcher on 2006-07-24
> **GuitarHero said:**
> I would give Ubuntu about 10 at least.  Make sure to defrag windows a couple times before you do it and back your files up.  Partitioning just makes separate sections of your harddrive.  Its kinda like splitting your hard drive up into separate hard drives, but just not in a physical sense.

Should I defrag Windows even though it tells me not to? I choose the Analyze option and it tells me that I don't need to defragment.

---

### Post by catlett on 2006-07-24
Go to ebay and but a used hard drive. It is a simple,safe and easy way to install ubuntu. Then you put the second hard drive in and install ubuntu to that drive and you don't touch your main drive.
Here is just a random drive from ebay. Not the best but good enough for a first time linux install [http://cgi.ebay.com/FUJITSU-10-2GB-5400RPM-IDE-HD-MPE3102AT_W0QQitemZ200010796591QQihZ010QQcategoryZ16178QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/FUJITSU-10-2GB-5400RPM-IDE-HD-MPE3102AT_W0QQitemZ200010796591QQihZ010QQcategoryZ16178QQrdZ1QQcmdZViewItem)
As you can see it is only $9.98 delivered.
There are even more to choose from [http://listings.ebay.com/Drives-Controllers-Storage_Hard-Drives-Internal_W0QQfrisZ2QQfrppZ50QQfsooZ1QQfsopZ3QQmaxrecordsreturnedZ300QQsacatZ56083QQsbrsrtZdQQsocmdZListingItemList](http://listings.ebay.com/Drives-Controllers-Storage_Hard-Drives-Internal_W0QQfrisZ2QQfrppZ50QQfsooZ1QQfsopZ3QQmaxrecordsreturnedZ300QQsacatZ56083QQsbrsrtZdQQsocmdZListingItemList)

---

### Post by Wotcher on 2006-07-24
> **catlett said:**
> Go to ebay and but a used hard drive. It is a simple,safe and easy way to install ubuntu. Then you put the second hard drive in and install ubuntu to that drive and you don't touch your main drive.
Here is just a random drive from ebay. Not the best but good enough for a first time linux install [http://cgi.ebay.com/FUJITSU-10-2GB-5400RPM-IDE-HD-MPE3102AT_W0QQitemZ200010796591QQihZ010QQcategoryZ16178QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/FUJITSU-10-2GB-5400RPM-IDE-HD-MPE3102AT_W0QQitemZ200010796591QQihZ010QQcategoryZ16178QQrdZ1QQcmdZViewItem)
As you can see it is only $9.98 delivered.
There are even more to choose from [http://listings.ebay.com/Drives-Controllers-Storage_Hard-Drives-Internal_W0QQfrisZ2QQfrppZ50QQfsooZ1QQfsopZ3QQmaxrecordsreturnedZ300QQsacatZ56083QQsbrsrtZdQQsocmdZListingItemList](http://listings.ebay.com/Drives-Controllers-Storage_Hard-Drives-Internal_W0QQfrisZ2QQfrppZ50QQfsooZ1QQfsopZ3QQmaxrecordsreturnedZ300QQsacatZ56083QQsbrsrtZdQQsocmdZListingItemList)

Would an external hard drive do? I wouldn't know how to put in an internal hard drive into my tower. And if I do put it onto an external hard drive, how would I make it so that when the computer starts I get to choose which drive to start from?

---

### Post by Wotcher on 2006-07-24
Bump

---

### Post by Wotcher on 2006-07-25
Bump

---

### Post by gigaferz on 2006-07-25
Hello..Im curious about  the errors you were describing at the begining..i used ubuntu live cd on a computer fine..then after an few hours,,I turned it off..then when i turn the computer on again .. I get all those mesages about errors and blocks..and numbers...But it was working fine...

Also On other computer I finally got Kubuntu to work with internet and remote desktop connection..after 10 hours of work ...I decided to  boot on windows to check an old mail ..but!!!!  windows was not working!!!!It showed a screen with that...
Windows has encountered a problem..choose your option to boot..(safe mode , last god config..)...and when i hit the up arrow or down...it stopped responding...!!!
it happened like 3 times a...after a couple of times trying everything  was black...not even the windows warning......
then after turning the computer on and off..and unplugin  the electrical cord...It finally worked..!!!

Has anybody had the same problem??

---

### Post by Wotcher on 2006-07-25
> **gigaferz said:**
> Hello..Im curious about  the errors you were describing at the begining..i used ubuntu live cd on a computer fine..then after an few hours,,I turned it off..then when i turn the computer on again .. I get all those mesages about errors and blocks..and numbers...But it was working fine...

Also On other computer I finally got Kubuntu to work with internet and remote desktop connection..after 10 hours of work ...I decided to  boot on windows to check an old mail ..but!!!!  windows was not working!!!!It showed a screen with that...
Windows has encountered a problem..choose your option to boot..(safe mode , last god config..)...and when i hit the up arrow or down...it stopped responding...!!!
it happened like 3 times a...after a couple of times trying everything  was black...not even the windows warning......
then after turning the computer on and off..and unplugin  the electrical cord...It finally worked..!!!

Has anybody had the same problem??

The error I was getting was because my CD was not burned properly. I burned it at speed that was too fast, so the CD got corrupted. So, I reburned the iso file onto another CD, using CDBurnerXP (I downloaded it because I was recommended it) and I followed instructions on Aysiu's website. [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by Drakkor on 2006-07-25
Also,since I don't think I've heard this mentioned, You have an option,below
Start or Install Disk to check or verify the disk, try that. It happened on my first burn even though the md5 was ok,the install froze at 68%, verified the disk,and sure enough had 1 checksum error ,reburned it, and it installed fine ! :)

---

### Post by gigaferz on 2006-07-25
ill get a hard drive this next thursday..what are my options to check the cd,s I burn?

Besides doing it at a lower speed..??

"even though the md5 was ok,the install froze at 68%, verified the disk,and sure enough had 1 checksum error ,reburned it, and it installed fine ! "

How you verified the disk? (assuming you did not use md5),

---

### Post by punx45 on 2006-07-25
> **Wotcher said:**
> Would an external hard drive do? I wouldn't know how to put in an internal hard drive into my tower. And if I do put it onto an external hard drive, how would I make it so that when the computer starts I get to choose which drive to start from?

I second the notion of getting a second "scratch disk" to mess around with.   thats how i did it.  that way you dont even touch a windows drive.

I have 3 internal hard drives (even though there was only room for 2) one (hdb) is devoted to Windows XP, hda is devoted to ubuntu, and the third (hdc) is my general music/video drive.

i would say avoid an external because it will most likely use USB and you are just asking for more complications there.

---

### Post by deadgobby on 2006-07-25
check out the on line video.
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

---

### Post by Drakkor on 2006-07-25
Ok,gigaferz when you boot from the live cd you will be given 4 options:
1. Start or Install Ubuntu
2. Check CD for defects
3. Memory Test
4. Boot from first harddisk
Select option #2 to check the disk, even though,when I checked my md5sums,which were correct,so it was a good download,something happened in the burning to cause 1 checksum error,so upon reburning and checking for defects again.it was fine ! Then the install went without a hitch !! :p
Edit: I did my Ubuntu install also on a different hard drive,but wrote the grub boot loader to my mbr,master boot record,So now when I boot I have the option to start Ubuntu (default) or XP,which is nice because if you write the grub to your other hard disk,you will constantly have to change the bios to tell it which disk to boot.The XP mbr can easily be renewed with the XP disk,
if you have one, and can all be reversed. :mrgreen:

---

### Post by gigaferz on 2006-07-26
ok..
The thing is tha most of the big brands on the computers..Are not  providing a  Xp installation disk... 

Can you believe it?? 

So the discs I made i did those using a Recovery system software..

have you seen a post that might explain how to dual boot with 2 drives?

thank you!!

---

### Post by Drakkor on 2006-07-26
Ok,remember to mount grub on your 2nd drive,and you will have to change your bios settings each time to boot to the other OS,leaving your 1st drive and windows untouched ! Good Luck ! :) 
[http://www.ubuntuforums.org/showthread.php?t=119892](http://www.ubuntuforums.org/showthread.php?t=119892)

---

