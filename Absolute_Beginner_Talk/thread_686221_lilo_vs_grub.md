---
title: "lilo vs grub"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by davidwrocklage on 2008-02-03
hello, 
   I am wanting to install Zenwalk 5.0 as a dual boot and I understand that it uses Lilo.  I tried to load slackware and add it to GRUB without any results. My questions are
1. how do I add Zenwalk to my Grub?
2. If this isn't possible can I use both Grub and Lilo? 
3. if that isn't possible how do I us Lilo to load Ubuntu? will I need to get rid of Grub? 

  On a different note all together I am tired of blindly cutting and pasting terminal commands. What recommendations of threads and or websites do you have, that are good, ground up tutorials on terminal use? I have looked at quite a few and they seem to assume that the user knows what a bash is and how to change directories, etc. I'm look for something that starts at the very beginning please and if there is a book about terminal use or just a book that you found invaluable as a beginner in the world of Linux feel free to throw that in the mix as well.  I really do enjoy learning about this system and I really just want some direction as to how to start, Linuxland seems to be vast and a little intimidating.  Thank you in advance

---

### Post by Herman on 2008-02-03
Hello davidwrocklage,
Ubuntu can be booted with either GRUB or LiLo, but GRUB seems to far the more popular with most Ubuntu users.

I have a web page about how to boot Ubuntu with LiLo, here, [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html"). You can use LiLo if you want, but there is a complication. These days our /etc/fstab files use file system UUID numbers for identifying the partitions, and LiLo hasn't been upgraded to match, or at least it wasn't the last time I checked. If you want to boot Ubuntu with LiLo these days, you will need to edit your /etc/fstab file and revert it back to the old fashioned style, just using Linux notation to designate partitions. That is explained in the page I linked you to. 
The other disadvantage of using LiLo is that when there is a kernel update, you need to run Liloconfig, whereas GRUB will be updated 'automagically'.
Nevertheless, some people still like LiLo, maybe because they are used to it. One thing LiLo does that is kind of nice is automatically make a backup of your MBR for you if you install it to MBR.

A better thing to do would be to install LiLo to the first sectors of the partitions that belong to the other operating systems you want to use LiLo for booting. GRUB can boot any other bootloaders such as LiLo or NTLDR by 'chainloading' the other bootloader in the boot sector. Here's a web page to explain how to use GRUB with Ubuntu, [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm").

So you would install Ubuntu and install GRUB to MBR, Probabably Ubuntu will detect the presence of your other operating systems and automatically add an entry for each of them to your new GRUB menu. You might not need to do anything more, especially for Windows if one of your other operating systems happens to be a Windows installation.
If it's another Linux and you want to boot it by LiLo in it's boot sector, just take a look at your  /boot/grub/menu.lst file and see what kind of commands are in the boot entry, you might want to change it to a chainloader command manually if it's important that it boots with LiLo.

Don't worry about anything too much if you feel it's all too complicated at first, there are lots of people here to help you, and we can explain things in more detail if you just ask questions about anything you can't understand.
Lots of us around here just love to help.
>  1. how do I add Zenwalk to my Grub?It'll probably be added automatically, but you might need to change to a 'chainloader' command later.
>  2. If this isn't possible can I use both Grub and Lilo? Yes, it is certainly possible to use both, I have even used them both in the same operating system, they get along fine with each other and sometimes you can use the other as a spare 'emergency' means of booting if your main boot loader has a problem.
>  3. if that isn't possible how do I us Lilo to load Ubuntu? will I need to get rid of Grub?  You would install GRUB to the first sector of your Ubuntu partition if you wanted to boot with LiLo from Zenwalk and add some kind of a boot entry to your Zenwalk LiLo config file to boot either Ubuntu directly, or boot Ubuntu via GRUB. However I don't think that way would be the easiest or best, it is possible though.

To be continued....

---

### Post by Herman on 2008-02-03
> On a different note all together I am tired of blindly cutting and pasting terminal commands. What recommendations of threads and or websites do you have, that are good, ground up tutorials on terminal use?   '[Terminal For Beginners]("http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners")' ,- by kryal of Ubuntu Web Forums would be a great start. It's a very informative Ubuntu Web Forum thread. Some Linux tutorials are more specific to other distros and some of the commands work a little differently, so it's nice to see an good all-Ubuntu tutorial, thanks to Kryal!

[UNIX Tutorial for Beginners]("http://www.ee.surrey.ac.uk/Teaching/Unix/") - This one's about Unix, which is the language that Linux is based on. Linux uses unix commands, plus some extra ones that Unix might not have. There are a few things here that might not directly apply to Ubuntu, but it's a great tutorial. This is the first one I began learning from, and I still refer to it. 

Here are a few more, they're all good,

[Linux Command.org ]("http://www.linuxcommand.org/")
 
 [Linux Online - Linux courses]("http://www.linux.org/lessons/")
 
 [The Linux Tutoria]("http://www.linux-tutorial.info/index.php")[l]("http://www.linux-tutorial.info/index.php")
 
 [A Hands on Guide]("http://tldp.org/LDP/intro-linux/html/index.html")  by Machtelt Garrels
        
              [_Rute User's Tutorial and Exposition_]("http://rute.2038bug.com/rute.html.gz") by Paul Sheer

[TLUG CS Student Linux Users Guide]("http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User%27s_Guide")

I wouldn't necessarily force myself to learn all those or even maybe any of them all the way through right away. If you begin one or two and you're enjoying them, well and good go as far as you feel comfortable. Feel free to quit though as soon as you get tired of that kind of thing, there's no need to make it into a chore, learning Linux should be fun.

You only need to learn a little to get started with and then you'll pick a lot up by yourself as you play around with your operating system and have fun following getting your system set up. You'll learn Linux without even trying while you have fun [Customizing Your GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst") maybe or using the [Ubuntu:Gutsy -Guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") to install software and customize your Ubuntu. There are all kinds of other interesting and fun how-tos around that you will be able to follow and learn Linux while doing things that are accomplishing some fun task and teaching you at the same time.

---

### Post by Herman on 2008-02-03
>  1. how do I add Zenwalk to my Grub? Getting back to your first question again, you could install your Zenwalk's LiLo to the first sector (boot sector) of your Zenwalk partition and then install Ubuntu.

After you install Ubuntu, post a copy of the bottom part of your /boot/grub/menu.lst file here along with a copy of the output from 'sudo fdisk -lu' and I or someone here will help you with the chainloader command if you need any help.
```
gksudo gedit /boot/grub/menu.lst
```
```
sudo fdisk -lu
```

Regards, Herman :)

---

### Post by davidwrocklage on 2008-02-03
All I can say is wow. Thank you Herman for the time and effort you put into your replies. It's after midnight so I'll be trying some of your ideas tomorrow, I'll have to do some research as I have no idea about boot sectors. When I installed Ubuntu I filled my entire drive, I used Gparted to repartition my hard drive. Sda3 and Sda4 were going to be for trying out other distros, at the moment the partition structure is a  little weird  sda1 is ubuntu, sda3 is free, sda4 is free, sda2 was set up during the Ubuntu installation as a swap drive. This is the order they appear when I view them in Gparted.

sda3 is about 15g and sda4 is about 80g in size and both are formatted to ext3

Thanks again Herman, I'll be using your advice and visiting some of your links tomorrow. It's hard to believe that less than a month ago I had only used windows operating systems,  had never partitioned a hard drive and had never even heard of a terminal. A lot can change in 3 weeks. I even wrote, compiled and ran the "Hello World" program today, can't really understand what all of it meant but it was a victory non the less and a little exciting.  It's nice to know there are people like you to help newcomers like myself.

PS you can just call me David, I am one that has never seen a need to hide behind off the wall screen names.

---

### Post by Herman on 2008-02-03
Okay then David, I understand that you'll need a little time to read a little and take that all in. No problem. 
I try to make a quick visit at least twice a day on weekdays and on weekends or  holidays I am able to spend more time here. If I'm slow replying on a weekday it's probably because I'm not near a computer.
There are lots of great people here who love to help. There is plenty of time for you to have fun and learn all you like around here. We all hope you will like Ubuntu as much as we do.

Another excellent website is [Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php"), you might find that helpful as well.

A boot sector is the first sector of a partition, often it has code in it to make it 'point to' a boot loader inside the partition's  file system.

A MBR is a hard disk's Master Boot Record. There is only one Master Boot Record for each hard disk, they are in the first sector of the hard disk. Many people think use the terms 'mbr' and 'boot sector' synonymously, but they are two different things. 

Regards, Herman  :)

---

### Post by davidwrocklage on 2008-02-03
um ..I decided to try installing Zenwalk again, good news is that I can access Zenwalk, bad news is I can't access Grub or Ubuntu, I know Ubuntu is still there but... I'm not sure how to get to it. I'll work on it and keep you posted.

ok I have found this by searching the forums would this be a fix for my problem?

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I'm not sure how to implement step 4, I have 4 partitions would Ubuntu is installed in SDA1 and I assume this is were Grub is as well, so would I type "root (hd0,0)" ?

Thanks again for your help. For your info I prefer to use Grub over lilo So as an end result I want a grub menu with Ubuntu and Zenwalk on i, hope this helps

Ok I have my GRUB Back (yeah!) now to add my Zenwalk to my GRUB.

---

### Post by davidwrocklage on 2008-02-03
SO I used my Ubuntu Live cd to reinstall Grub to my MBR, so now Grub was back and I used the following to add Zenwalk to GRUB

# Zenwalk Linux
title Zenwalk Linux
root (hd0,2)
kernel (hd0,2)/boot/vmlinuz root=/dev/hda3 vga=0x31A video=vesafb:mtrr,ywrap splash=silent
initrd (hd0,2)/boot/initrd.splash

So now when I reload Zenwalk is in my Grub and Launches.... Kind of

Zenwalk gets to the splashsceen that say to "press f2 to enter Verbose mode" and hangs

I thought well maybe this has something to do with switching from Lilo to Grub so I re-installed Zenwalk skipping the Lilo step and re-loaded again Zenwalk hangs at the same splashscreen. I really liked Zenwalk as I was playing around today and would like to get it back up and running.

any ideas??

Thanks in advance

---

### Post by Herman on 2008-02-03
You might have no entry in your /boot/grub/menu.lst file at all for Zenwalk, so here's what you can do,
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Zenwalk Linux
root        (hd0,2)
savedefault
makeactive
chainloader    +1
``` It' s improtant that your Zenwalk entry is below the line that says 'END OF DEBIAN AUTOMAGIC KERNELS LIST'.
The 'savedefault' command is optional, but I think LiLo likes the partition to be marked active, so the 'makeactive' command is probably a good idea. It won't do any harm anyway. The chainloader command should chainload LiLo for you and then you should be able to boot Zenwalk with LiLo.

Try that and see if it works. It should work providing you have LiLo installed to the boot sector of the Zenwalk partition.

Regards, Herman :)

---

### Post by davidwrocklage on 2008-02-03
found out how to load Zenwalk without the splashscreen and found out what the kernel panic was 

had to change hda3 to sda3

title           Zenwalk Linux 
root            (hd0,2)
kernel          (hd0,2)/boot/vmlinuz root=/dev/sda3

this worked in the debian area, thank you so much

---

### Post by andrew.46 on 2008-02-04
Hi,

 You have described my own setup:

> **Herman said:**
> 
You would install GRUB to the first sector of your Ubuntu partition if you wanted to boot with LiLo from Zenwalk and add some kind of a boot entry to your Zenwalk LiLo config file to boot either Ubuntu directly, or boot Ubuntu via GRUB. However I don't think that way would be the easiest or best, it is possible though.

and despite your doubts it works beautifully :-) I take the liberty of describing this setup on a little more detail, although I see you have already pretty much set yourself up:

I have a 100+ gig drive partioned as follows:

[LIST=1]
[*]hda1 = 80 gig Slackware
[*]hda2 = 30 gig Ubuntu
[*]hda 3 = swap
[/LIST]

I have Lilo installed to the MBR and I *chainload* the Ubuntu partition as follows:

```
# Slackware on hda1
image = /boot/vmlinuz-generic-smp-2.6.21.5-smp
  initrd = /boot/initrd.gz
  root = /dev/hda1
  label = Slackware
  read-only
# Ubuntu Hardy on hda2
other=/dev/hda2
    label= Hardy
    table=/dev/hda
```

When installing Ubuntu I took great care to install grub to (hda0,1) which is of course its own partition. This means I don't have to constantly adjust Lilo boot parameters for the ever changing Ubuntu kernel. Mounting one partition from inside the other I do manually but of course entering the details into /etc/fstab is an option.

It is a rock solid setup that is worth a little initial fiddling but of course there are many different ways of doing this. Is this any help to you, or have you settled on the alternatives that I have read through?

             Andrew

---

### Post by Herman on 2008-02-04
Cool, andrew.46! :)
It looks like you know waht you're doing with LiLo. LiLo's a good boot loader. Nice website too!
Regards, Herman :)

---

### Post by andrew.46 on 2008-02-06
Hi,

 Thanks for that:

> **Herman said:**
> Cool, andrew.46! :)
It looks like you know waht you're doing with LiLo. LiLo's a good boot loader. Nice website too!
Regards, Herman :)

 Well, I am actually fairly new to Lilo but I learn fast :-) Came to Lilo when I started with Slackware and I have always been impressed at what a rock solid piece of software it is. Grub of course does more but like a well-trained Slackware user I distrust automation and Grub does a lot without being told.

But I think people just 'click' with one or the other?

               Andrew

---

