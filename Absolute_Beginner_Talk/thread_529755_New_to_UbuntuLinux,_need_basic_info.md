---
title: "New to Ubuntu/Linux, need basic info"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by jwfan81 on 2007-08-19
I want to repartition my HD for a dual boot for Ubuntu & WinXP Pro.  It's currently formatted in NTFS and I'd like to reformat so I can boot both OS's.  (Win XP Pro & Ubuntu)

I'm very much a newbie to Linux.  If anybody can direct me on how to do this, that would be great...

If there is a website dedicated to these questions, a link would be greatly appreciated.

My system is:  AMD Sempron 1.49Ghz with 1 Gb/RAM.  I have a 40 Gb HD, I use very little of it, currently under 6Gb used.

Do I need to download a copy of Ubuntu and have it burned to CD?  My CD-ROM is old and isn't a DVD.  

Thanks in advance for your help.

-Chris

---

### Post by Decatur on 2007-08-19
I know im a noob too.

---

### Post by Jimmyfj on 2007-08-19
Just install your XP Pro before you install Ubuntu. This is the easiest way around it. Install XP and do remember to defragment your drive before you install Ubuntu. Then let the Ubuntu installer repartition the drive for you. You can deside for yourself what size you want for the Ubuntu install from the installers disk partitioning program.

---

### Post by Tyke91 on 2007-08-19
start the ubuntu install. when you get to the disk partitioning stage, select manual


then shrink your windows partition (i hope you defragged before) and make new free space. 

set the file system on the free space to ext3 and mount it as    "/"  (also known as root)

create another partition (around twice the size of your ram) called swap




then you're good to go :D

---

### Post by Tyke91 on 2007-08-19
you can get a cd mailed to you for free (2-3 months wait)

or you can download the iso image of the cd, then burn it to a blank cd using the program imgburn

EDIT:  beat you     :)

---

### Post by moredhel on 2007-08-19
If you don't have a cd-writer drive then you can get the ubuntu cd posted to you for free:

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Or you can buy it commercially from virtually any online linux cd reseller.

EDIT: Beaten ^ >_<

---

### Post by jwfan81 on 2007-08-19
I'm currently defragmenting my HD as suggested.

I can burn a CD at work tomorrow no prob, should I wait until then until attempting this (since I'm completely new)  or do you guys/gals think I can successfully install tonight?

-Chris

---

### Post by Myglaren on 2007-08-19
> **Tyke91 said:**
> you can get a cd mailed to you for free (2-3 months wait)

or you can download the iso image of the cd, then burn it to a blank cd using the program imgburn

EDIT:  beat you     :)

My last ones (Feisty, a week after release) took ten days.

---

### Post by redfox1160 on 2007-08-19
What Exactly Is XP Pro?

---

### Post by jwfan81 on 2007-08-19
XP Pro - Windows XP Professional.

---

### Post by jgrabham on 2007-08-19
> **redfox1160@verizon.net said:**
> What Exactly Is XP Pro?

Microsoft's windows xp profesional

---

### Post by redfox1160 on 2007-08-19
I dont know why i didnt think of that,  lol..

---

### Post by jwfan81 on 2007-08-19
So, I'm thinking my best option is to burn Ubuntu at work on a CD and then let it repartition my HD so I can still keep Windows XP Professional for a dual boot?  

When I boot to Ubuntu, will the OS be able to load the drivers for the monitor, sound card, ethernet, etc...?    Also, will my DSL need to be reconfigured?  I have it now connected via USB and I'm pretty sure my ISP (Bellsouth) won't provide any support for anything but Windows.

Chris

---

### Post by Lithium17 on 2007-08-19
dual booting is a good plan, at least until you get everything working alright in Ubuntu, also yes it will handle your hardware for you, just as any other OS would. 

Ps

for your modem look up USB ADSL modem manager, it will act as the firmware for your modem, and it allows you to save your ISP details so that it connects on startup, it works perfectly.

---

### Post by Aishiko on 2007-08-19
> **jwfan81 said:**
> So, I'm thinking my best option is to burn Ubuntu at work on a CD and then let it repartition my HD so I can still keep Windows XP Professional for a dual boot?  

When I boot to Ubuntu, will the OS be able to load the drivers for the monitor, sound card, ethernet, etc...?    Also, will my DSL need to be reconfigured?  I have it now connected via USB and I'm pretty sure my ISP (Bellsouth) won't provide any support for anything but Windows.

Chris
well let's see your right bellsouth and most internet providers won't support anything but windows, my local Highspeed internet providers don't even support Macs.

as for dectecting everything, it should at least detect and get the basics working monitor, keyboard, mouse, the optionals like sound, ethernet, and wireless are not a sure thing however, only the wireless from what I've read and from the 1 person I know in person that has tried Ubuntu is the only thing that is likely to be a pain to get working if it works at all (her's was an interal wireless adapter).  Ati X series need a little coaxing to get everything working as do some of the Nividia cards, but then even in the windows and mac worlds you need to go and download specail software to get everythign working if it didn't come with a CD or DVD with the software on it.  Just putting it in perspective. 

Though I've not had any real issues yet but so far I'm only using lowend baisc parts, that should be in any OS driver data base the only thing that could have been a problem is the 2 P3 CPUs so I got help before I did anything.

---

### Post by skyjacker on 2007-08-19
Hi, Just went through this 2 weeks ago. If your pc has a partition for recovery to original , you may not be able to partition manually because you can have only 4 partitions on the HDD. You need 3 for Ubuntu /, /home, & swap. If this is your case try one of the partition options during install. I shrunk the windows partition and then picked the option to use the avalable free space for Ubuntu.  It creates all three partions automatically for you.  Good Luck

---

### Post by jwfan81 on 2007-08-19
Thanks for all of the help you guys & gals.  This sounds like it will be a bit of a challenge, probably a project I should take on next weekend.  

I'm seriously considering getting another HDD for this project, as I'm worried something will go wrong and I'll be dead in the water.

I've been using Windows for years 95, 98 (sucks) and Win2k (no crashes - great) along with Windows XP (no crashes - great again).  Now, it's time for me to start really having fun and experimenting.

Since I can't go a single day without internet access due to work, I think another harddrive is necessary due to the high probability of hardware needing tweaking as a result of installing a Linux version.

If anybody can say that for sure once I start the Ubuntu install  from CD (that I"ll download and burn at work) that it will keep my Windows XP even if I shrink the partition, in tact, I'd prefer to purchase a backup HDD and experiment there just to be safe.

-Chris

---

### Post by zeehat on 2007-08-19
Make sure you burn the CD as an 'image'; if you burn it as plain data, it will not work.

---

### Post by jwfan81 on 2007-08-19
By the way, if I were to use the same HDD, why is it so important that I defragment it?   Just curious.

I put images onto Compact Flashes (Windows NT 4.0 and Windows XP Embedded) at work all of the time.   At home, I never defrag my HDD and never have any problems.   

Why is it so important to defrag if I want to install Ubuntu using the same HDD?

Thanks,

Chris

---

### Post by huggies15 on 2007-08-19
when u burn the cd image it will most probably be a live cd as well... this mena u can boot into the cd, try out ubuntu and play with settings without affecting anything on the hard drive. its how i started as i was too scared to repartition my system too, but once i was pretty sure of how the basics work ie. wireless and office programs, i took the plunge. the install from cd is really easy, and gives a lot of help along the way.

edit: u need to defrag as the windows data will be scattered over the hdd, u need it all in one bit so linux can use the other part. its a bit like having a grid 10x10 and having every other square filled, then tryng to put a 50square square in it, would nt work coz there wa sno space :)

---

### Post by jwfan81 on 2007-08-20
Thanks Huggies15, as well as the rest of you.

I didn't get a chance to burn a CD at work today but it's on my list as something of high priority.

@ zeehat:  Do you have any specific instructions as to burning the CD as an image as opposed to just "data"?  I'm sure that this may sound absolutely rediculous, but I don't have a CD burner in my box and as strange as it may sound, I've never burned a CD.

Try not to laugh to hard, I am in the "Absolute Beginner Talk" section of the forum.  

Chris

---

### Post by nowshining on 2007-08-20
hi [jwfan81]("http://ubuntuforums.org/member.php?u=365377") you need either a CDR or CDRW burner to burn a cd or even better a DVD R and RW that will also burn CDR and CDRWs.

CDR - Compact Disk Rightable - can only burn to once and uses about 800mb and below disks
CDRW is the same as a CDR, but with a CDRW cd you can write as many times as you want until the cd itself wears out.

DVDR is the same as a CDR but you use a blank DVD disc as opposed to a blank CD which can only hold up to 800mbs of data, a DVD disc is able to store  Way beyond that amount.

DVDRW same as CDRW and DVDR but is again Re-writable.

If you do not have or have access to a DVDr or DVDRW or CDr or CDRW drive then you can order the CDs like I did, even tho I have access to a CDRW I have 56k as my modem speed and yes it took months for me to receive them so be patient you'll also get some ubuntu branded/logo stickers to go with the CDS..

shipit.ubuntu.com

or optionally if you have a flash drive you can probably run it from there as I am not sure tho and the computer would have to boot up from the usb disk, as it might work and you can try that.

---

### Post by clickquick on 2007-08-21
I also need to know how to burn as an image file.

---

### Post by A$h X on 2007-08-21
As long as you have a CD/DVD burner, then d/l a program called Infrarecorder and burn the .iso image onto a CD/DVD. Make sure you get the .iso from this forum as I used an image from somewhere else and it wouldn't boot ubuntu properly.

---

### Post by emanresu on 2007-08-21
Clickquick,

most cd/dvd burning applications have function for "data" CDs. click on that and there should be an option for .ISO (and at least one other option, but i can't remember what it is right now). select that option. you should then see .ISO files with the name of the distro you downloaded. after you get your image in the right place for burning, start the process. 

hwfan1,
when you repartition your HD, you should try to make sure you leave about 15 GB for the XP partition. i've read that XP needs that much to avoid crashes. don't ask me why. [and don't ask me why i believe everything i read either ;) ] 
i'm pretty new to most of this myself. i repartitioned my laptop after a month of fretting, i finally decided i had the restore disks, i can fix it if i have to. the first installation was actually openSUSE. i had space left on the HD, so i added Ubuntu also. i like both distros, but i updated the kernel in SUSE and now it doesn't want to play. so, i'm trying to figure what happened. i think it's a grub problem. anyway. i used systemrescuecd's partitioning tool, gparted i think, the 1st time and after i got the partitions the way i wanted them, i installed SUSE. i repartitioned after that on the extended drive again. my XP crashed last week for no reason i know, but the other stuff worked well. 
one last thing. this is entirely up to you and i'm willing to bet the people who know more may say this is a bad idea, but i have a FAT32 drive. it will hold files that you can read in M$ and linux. i use that as my /home more or less. it's probably not secure, but then, my computer is a dual boot and that probably ruins the idea of security to begin with. my partition scheme is:
sda1 - XP
sda2 - XP restore
sda3- "/home"
sda4 - extended
sda5 - swap
sda6 - openSUSE
sda7 - Ubuntu

just make sure you've back edup your stuff and then go at it. 

e

---

