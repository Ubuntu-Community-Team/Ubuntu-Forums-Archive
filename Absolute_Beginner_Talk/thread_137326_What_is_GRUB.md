---
title: "What is GRUB?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by oz8ball1 on 2006-02-27
Hi, 

My question is, what is GRUB? Do I need it? and, What do I do next?  

I have an older computer that I want to install Ubuntu 5.1 on and after installing, finding problems, reinstalling, finding more problems, reinstalling again and again I find myself stuck. I've been able to get through the installation process off the disk, had the disk eject and restart, but then it stops just as it is loading.

The screen is displaying :
[INDENT]GRUB Loading stage1.5.


GRUB loading, please wait...[/INDENT]

and there it has stayed. I googled GRUB and learned that it is a multiboot boot loader, but the thing is, I dont want to multiboot, I just want to run Ubuntu on this machine. Is there a way to disable the GRUB? or something like that?

Thanks, and if you need some more info I will be happy to tell you everything I can, I just don't really know what to tell. Thanks again.

---

### Post by taurus on 2006-02-27
It doesn't matter if you have one OS or ten OSes on your machine, you need GRUB to boot your system.  Besides GRUB, LILO can do it too.  Now, when you installed Ubuntu, how did you partition your harddrive and where did you tell GRUB to install itself.  Make sure you tell it to install on MBR...

---

### Post by oz8ball1 on 2006-02-27
[QUOTE=taurus]It doesn't matter if you have one OS or ten OSes on your machine, you need GRUB to boot your system.  Besides GRUB, LILO can do it too.  Now, when you installed Ubuntu, how did you partition your harddrive and where did you tell GRUB to install itself.  Make sure you tell it to install on MBR...[/QUOTE]

well i dont quite know how i partitioned the hard drive, to be honest I don't really know what happened, I popped in the install disk and clicked continue mostly, I'm pretty sure that I had it erase the entire disk (IDE1 master (hda)). And after that it went on its merry way without asking me anything about the GRUB install. 

I am totally open to instaling it again, as I have done so countless times in the past day and a half, so if you (or anybody) thinks it would be easier to fix this by a guided install thats totally cool with me.

---

### Post by taurus on 2006-02-27
Well, if you have a Ubuntu LiveCD, you can boot with that and mount your partitions.  Then post both of your /etc/fstab and /boot/grub/menu.lst.  And as far as I know, you should get a window that asks you where you want to install the bootloader and which one do you want to use, GRUB or LILO.  You want to use GRUB and have it install on MBR...  So, look for that when you re-install Ubuntu again!!!  I promise it is there.

---

### Post by oz8ball1 on 2006-02-27
ok, so i do have a LiveCD, how do I mount the partitions? and also, where would this window come up in the installation? cause, I am quite sure I haven't seen that screen. Though, since you promise that it is there, I must have skipped through it with out noticing, or maybe its in the disk partition and I just didn't notice?

---

### Post by oz8ball1 on 2006-02-27
ok, so I booted up with the LiveCD and opend the disk manager and clicked on the partitions tab and noted that when partition 1 was selected the properties read:
[INDENT]Device:        /dev/hda 1
Filesystem:   Extended 3
Access Path: none[/INDENT]

when I clicked Swap Partition from the Parition List and the properties read:
[INDENT]Device:        /dev/hda5
Filesystem: Memory Swap[/INDENT]

also, I went through with File Browser and through Terminal and I dont have a grub folder within boot, i.e. /boot/grub/: No such file or directory
and I opened the fstab file and it read as follows:
[INDENT]/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0[/INDENT]

I dont know if this affects anything, but the computer that I'm installing this on is not connected to the internet.

I am now going to try to re install again and try to see that screen about the bootloader you mentioned.

---

### Post by oz8ball1 on 2006-02-28
i dunno, I re-installed again, and I still didn't see anything about GRUB. Is there a certine place I should be looking? 
I googled around somemore and found this install guide , [https://wiki.ubuntu.com/Installation/I386]("https://wiki.ubuntu.com/Installation/I386") and I followed the steps, but it didn't match up to how it worked for me. According to that guide, the second part of the installation-configuring the timezone, user account and password, also the installation of additional packages-happens after you eject the disk and hit enter to restart; but for me I do all of that before the disk ejects. I dont know if this all means that there's something wrong with the disk I burned, I dunno, but it was something I noticed and was wondering if anyone knew what to do. 

P.S. After this reinstall I am still getting the same hang up on "GRUB loading, please wait..."

---

### Post by oz8ball1 on 2006-02-28
ok, this is just a call to anyone, if anyone can see the answer to whats going on for me, please write, or anything, show me a link to something. I just don't know what to do, I've reinstalled it dozens of times, and nothing, the same screen with the same loading message every time. Anything, anybody, please.

---

### Post by munga_bill on 2006-02-28
Try the [hermanzone]("http://users.bigpond.net.au/hermanzone/") website, it's about dual booting really, but it has a lot of useful information in it for just installing Ubuntu by itself too. You might be able to see how your install differs from that and see something wrong. I don't remember if you see the option to install [GRUB]("http://www.gnu.org/software/grub/") when you single-boot, it might just do it automatically without telling you.

Have you checked the integrity of your .iso you downloaded? Have you invested in a good qualtiy CD-ROM, not just a cheap one that's only good for music? Have you burned at a slow speed like less than 4X?

What about checking your BIOS and making sure all the settings in there are normal? (You do have it set to boot from your hard disk as one of the boot devices don't you?)

How about your hard disk? Is it brand new or has it had something on it before? Would a virus of some kind be lurking in your BIOS or in the first track of your hard drive and keep overwritting the MBR on your before you get a chance to boot? Maybe we can nuke it with a 'dd' command for you, or try some tricks like removing the BIOS battery to reset the BIOS, or doing a BIOS flash. (Save these last few ideas for the last though, only if you really , really have to).

Is the hard disk new and it's not set up properly in your BIOS maybe, (the disk geometry might be all wrong, maybe it can't find the first sector properly?)

Let us know how you are getting along, I'll keep an eye here for you to post back.
Good Luck from munga_bill

---

### Post by munga_bill on 2006-02-28
> I have an older computer that I want to install Ubuntu 5.1 on and after installing, finding problems, reinstalling, finding more problems, reinstalling again and again I find myself stuck. I've been able to get through the installation process off the disk, had the disk eject and restart, but then it stops just as it is loading.
More ideas: Is your hard disk old and on its way out? You can test it with the live CD with the command:
```
sudo badblocks /dev/hda1
```
New hard disks are not all that expensive now and as easy to change as a light bulb, but make sure you get one to match your BIOSs capabilities if it is an older computer. Many older computers have a 5.0 GB or and 8.0 or a 32.0 GB limit in their BIOS. If it is a brand new hard disk, have you got one that does not exceed your BIOS's limit?

Some old computers get misbehaving after a while and they just need opening up and cleaning, and things like the RAM and the CPU unplugged and then plugged back in again ('reseated'). Lots of times just unplugging and plugging things back in again (one at a time) after blowing with compressed air will restore an old computer to 'as new' performance again without spending a single cent! It might be too dangerous to do that yourself though, depending on who you are and what skills you have. This is not adviseable for beginners or children, or adults who have not been trained in this,  or at least obtiained all the expert advice they can first, and be extremely careful !!!

---

### Post by lazyleg on 2006-03-02
I had the same problem on a old pc (475mhz cpu 64mbram 2gig harddrive) in the bios in IDE HDD AUTO DETECTION i changed a setting to normal on MBR to solve this problem. Im running the server vs of breezy badger, and when i tried to install the desktop vs it gave me the same error.

---

### Post by oz8ball1 on 2006-03-02
Thank you very much munga_bill for the reply.
Well I tried the thing to check my harddrive, 
> sudo badblocks /dev/hda1
and I can only assume that it worked because I didn't get any errors, its sat there for a while, I could hear it working, and then returned to normal, where I could type again. I ran it a few more times, and the same thing happend each time, so I assumed that meant it was ok. 
I went to the website, and you're right it was for dual booting, but looking through it I saw a few things (including a link to this page [ubuntu]("http://www3.telus.net/linux4u/ubuntu.html") which went over the steps a little slower) and they were pretty helpful, explaining what they were doing, along with screen shots. But it didn't work, I reinstalled once, and got a GRUB Error 15, and then I reinstalled again and got the same loading screen that never changed (I did this right before I went to sleep and when I woke up it was still on that screen). 
Now, to address your questions in the first post,
> Have you checked the integrity of your .iso you downloaded?...Have you burned at a slow speed like less than 4X?

I can't remember if I did, which probably means I didn't, I first burned the .iso off of my mac laptop and it finshed with errors, so when I tried to install from that disk and it didn't work I wasn't too surprised. I burned my next copy with a windows desktop using [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm") and I believed I burned it at 2x, to answer the next question.
Since I've been at this for almost four days I think I'm going to burn another disk and hit myself repeatedly if that works.
> What about checking your BIOS and making sure all the settings in there are normal? (You do have it set to boot from your hard disk as one of the boot devices don't you?)
Yeah, I've checked the BIOS and once I set it back to boot from the hard disk first, to see if that changed anything and it didn't.

You mentioned my harddrive a couple of times, and its integrity, and before I tried to install it was running windows fine, slow, but fine.

And I've read about people installing GRUB from the LiveCD? Is that right or did I misunderstand? Right now, to me, its seems as if it is just that problem with GRUB; but I dont know really at all, and I could be totally wrong.

---

### Post by oz8ball1 on 2006-03-03
Ok, since I figured that all my problems stemmed from the GRUB, considering that was what was on my screen when it didn't change. So I searched around for a lot of different stuff on how to install GRUB, most of which required me to open a root terminal from a liveCD, and in the two LiveCDs that I burned, neither of them seemed to have a root terminal option, or at least not where other people had said they were. I finally found out how to get it randomly while searching for something else, ( # sudo -s -H). Well I get the root terminal and think thats just great, now I can do the grub-install and get everything fixed. But no, of course not. I get the error 
> casper-snapshot does not have any corresponding BIOS drive
whatever that means, (note: if anyone knows what that means and can tell me what to do to fix it I will be very greatful). So I googled that and came up with some more stuff, and finally I stumbled on this page [RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") and it gives a few 'good' ideas about reloading GRUB, one of which being the [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"). Now this got me excited, the whole page listing options on how to install GRUB 'again.' So I downloaded the Super Disk, booted it up, followed the instruction (very simple, press "Auto") and boom, errors up the wazoo, well really the same error 73 times i guess. (selected Disk does not exist)

So another option was the install from the install disk, so I tried that.
 boot: rescue; 
then pick which partition is your root partition (off of a list), well I went through em all, the first (dev/discs/disc0/part1) being the only one that fit the suggested format without giving me a red warning/error screen. But that didn't work, when I got to the part where I was supposed to type in the grub-install commmand, it was 'not found'. So I tried again, this time choosing my fourth option, /dev/Ubuntu/root
but here the grub-install command was recognized, and nearly worked too, except for the fact that "The file /boot/grub/stage2 not read correctly"

So, I guess, my question still remains, "Can someone tell me what to do? Point me in the right direction? Show me what's wrong? What's happening?" I've looked at all these posts where people have similar problems, and I don't really understand the solutions for the most part, I try to duplicate what they did, but it doesnt work out, probably because I don't know what I'm doing. 

P.S. I was in GRUB and ran the setup and this is what it gave me:
> grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/iso9660_stage1_5" exists... yes
Running "embed /boot/grub/iso9660_stage1_5 (hd0)"... 19 sectors are embedded. succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+19 p (hd31)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 31: File is not sector aligned

P.P.S.
Above someone asked me about where my boot loader was and how my drives were partitioned, and really, I don't care. I am devoting this machine to Ubuntu, the entire harddrive, everything, so if you know how a single OS Ubuntu should be installed, teach me please.

---

### Post by Herman on 2006-03-03
oz8ball1,    ...can you please try again with the 'Breezy' live CD and this time open up a terminal and type:```
sudo fdisk -l
```That should give you a list of your (probably only two partitions, probably /dev/hda1, your main / partition, and /dev/hda5, your swap area).
Then, if /dev/hda1 is your main partition, ( / ), then type this:```
sudo mkdir /media/ubuntuinstall
``` and press enter, then```
sudo mount -t ext3 /dev/hda1 /media/ubuntuinstall
```and after pressing enter you should get an icon on your desktop called 'ubuntuinstall'.
Go into 'ubuntuinstall', (which should be your incomplete last installation attempt), and see if you see anything like the illustrations on [this page]("http://users.bigpond.net.au/hermanzone/p15.htm") in there. There are three illustrations on the top of that page that show what you should see. Anything? ... You might even be able to open the /boot/grub/menu.lst with the text editor (just right-click on it and click 'open with text editor'.
I don't know how we can help you yet, but it would be interesting to know what is there if anything, and what is missing possibly. Please compare with the illustrations and make sure all the files that are supposed to be there are there. Maybe we can find out something that will help us tracl this problem down. Thanks, :-D (Herman).

---

### Post by oz8ball1 on 2006-03-03
Herman, I'm up for anything right now. I'm closing in on a week of working on this same problem so I'm ready for anything. (bytheway, if thats is your site that you have listed [ubuntu dual boot]("http://users.bigpond.net.au/hermanzone/") I want to thank you, its awesome).  
(I have posted all my screenshots (to match those listed on the site) up on [this page]("http://oz8ball1.googlepages.com/ubuntuscreenschots"). if that helps any)
ok,
```
sudo fdisk -l
```
I have three partitions, /dev/hda1 ; /dev/hda2 ; /dev/hda5 ; (Under the system column it lists "Linux" ; "Extended" ; "Linux LVM" ; respectivly) with the boot asterix listed next to /dev/hda1.
> Go into 'ubuntuinstall', (which should be your incomplete last installation attempt), and see if you see anything like the illustrations on this page in there. There are three illustrations on the top of that page that show what you should see.
-When I click on the ubunutinstall icon on my desktop I go to a folder that looks like the second picture (2grub). In that folder everything looks the same, same files and folders, but I have an additional folder named "lost+found".
-I went to the folder of the first picture (1 grub) (home then up twice) and I am missing the "debootstrap" folder.
-Picture three (3 grub) of the grub folder matches exact, all the same files.
-On the site, it describes getting to the grub folder throught the boot folder, but that doesn't work for me. My /boot folder does not have the folder  /grub within it. It shows all the other files listed in the picture (2grub) but it doesnt have the grub folder. Whereas my /media/ubuntuinstall folder (now on my desktop as well?) looks just like the boot folder, but as I said with the addition of the "lost+found" folder.

-Following the directions on the page I should open the menu.lst file in gedit, through the terminal, but from /boot/grub/menu.lst (after making a backup). So, compaired my 'menu.lst' to the one on the site, but mine is take from my ubuntuinstall folder, not /boot/grub/menu.lst
--I noticed a few inconsistencies: in 1 grub of the menu.lst 

---my timeout is 3 instead of the listed 10 and my hiddenmenu is not commented out

---in 3 grub (I have a screen shot) my "#kopt=root=/dev/mapper/Ubuntu-root ro" instead of "#.../dev/hda2 ro"
and then 3 lines down, 

---my "#groot=(hd0,0)" instead of "#groot=(hd0,1)"

--4grub is the same, 

---in 5 grub (I also have screenshots, I couldnt get it all in one frame) my "root" and "kernel" and "initrd" are different. Also I dont have that last bit about other OS, which makes sense to me because I only have/want the one.

----------
-well the only things that I can think to change are the timeout (to 10) and too comment out the hiddenmenu. possibly change the roots and such, but I dont know what to change in it because, its not in the /boot/grub location. I was wondering if I should just copy and paste my grub folder (from ubuntuinstall) into the /boot folder?

-also I have a few little questions, just about syntax; What does hd0 mean? hda? (hd0,0)? ect. 
--My guess is that hd stands for harddrive (I think I saw a site somewhere that listed some of the acronymes, but I have since lost it), but what does the 0 or a stand for?

(I have posted all my screenshots (to match those listed on the site) up on [this page]("http://oz8ball1.googlepages.com/ubuntuscreenschots"). )

---

### Post by Herman on 2006-03-03
Hey oz8ball1, you have done really, really well, you will make an extremely good Ubuntu user as soon as we can get you away from the start barrier!:D

I think that mostly looks like Grub itself is okay, but right from the beginning the thing about your install that's different is you used LVM. That's okay, if you really wanted that. It's actually something really good, that more advanced computer users seem to like, but it isn't something I know about yet.
Did you really want LVM? It might make things a lot simpler to just do the install again, and looking at illustration 8 in the fat32 install, use 'Erase entire disk: IDE master (hda)- 41.1 GB ...' and go through the rest of the install the normal way. In your case you can ignore the partitioning part.
If you want to keep LVM, there's a link under that no.8 fat 32 illustation all about LVM, but I must admit I haven't looked into it very much. If you want to keep the LVM, you might be able to find some instructions in there to set it up. It looks too complicated for me though. 
Well, it's up to you, I'm not saying LVM is a bad thing, just something I don't know about yet. Everything might just work if you re-install without it, I hope. 
Unless someone comes along that can help you with the LVM, it's my guess that that's got something to do with your trouble but I don't exactly know what. 
What do you think, oz8ball1?

---

### Post by munga_bill on 2006-03-03
> -also I have a few little questions, just about syntax; What does hd0 mean? hda? (hd0,0)? ect.
--My guess is that hd stands for harddrive (I think I saw a site somewhere that listed some of the acronymes, but I have since lost it), but what does the 0 or a stand for?(Hd0) is Grub's way of designating the first hard disk drive. (Fd0) would be your floppy disk drive. 
Grub's partition numbering begins with 0 also, so (Hd0,0) means your first hard disk, and your first partition on that disk. 
(Hd1,1) would mean your second hard disk's second partition.
[http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html#Naming-convention](http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html#Naming-convention)

You shouldn't have to learn that yet at this stage though, just have fun with Ubuntu. A really good introduction to Ubuntu that you can use to get aquainted with all you need to know to begin with is: [Ubuntu User Guide PDF]("http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf") by aysiu. I highly recommend you download yourself a copy and keep it and refer to it. It will help you a lot!

---

### Post by oz8ball1 on 2006-03-04
first, thanks munga_bill for that, next, thanks herman.
(again, I posted [pictures]("http://oz8ball1.googlepages.com/ubuntuscreenshots2"))
Ok whoa, so I did the reinstall, like you suggested, just wiped the disk, no LVM. But when I ran the LiveCD and #sudo fdisk -l it still showed me three partitions, though the last one (hda5) was now listed under system as "Linux swap / Solaris" 
But the wonders didn't stop, I went through your (Herman's) previous post, and followed the steps with ```
sudo mkdir /media/ubuntuinstall
sudo mount -t ext3 /dev/hda1 /media/ubuntuinstall
```
and the folder that was created on my desktop was totally different than the last one. Instead of looking like the /boot folder, it now resembles the / root directory with the only difference being the addition of a "lost+found" folder.
well i went to check my actual root folder, but it looked like the same as before, same but missing the "debootstrap" folder, also in the /boot folder, the grub folder is missing, but both of these are in my ubuntuinstall folder. So I dont know what that means. 
    Could I just copy and paste these folders? Or is it a bit more complicated?

on to the menu.lst (I'm reading from the one in the ubuntuinstall folder, because /boot/grub/menu.lst doesn't exist.)
Well, it looks the same as my old one for the most part, but 3 grub picture shows > # kopt=root=/dev/hda2 ro
and mine is:
# kopt=root=/dev/hda1 ro
...and further down...
# groot=(hd0,1)
and mine is:
# groot=(hd0,0)
for the 5 grub picture
> root    (hd0,1)
and mine is:
root    (hd0,0)
...
kernel     /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash 
and mine is:
kernel     /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash 
 
^ and that goes on down the page. 

So still, when I boot up I still get the "GRUB loading, please wait..." so I was wondering, what do I do now? I mean, I took out the LVM and it seems as if I did get closer to the answer, but I still don't understand why my GRUB isn't working right, why I dont have a "debootstrap" folder or a /boot/grub folder?

---

### Post by Herman on 2006-03-04
oz8ball1, 
Your sudo fdisk -l looks okay, you have one partition, /dev/hda1 for your operating system and files, plus a swap area called /dev/hda5 which is inside an extended partition called /dev/hda2. That's all normal now. Good.

That folder you are creating called ubuntuinstall has to do with how we use a livecd to look at any partitions on your hard disk. We 'mount' them (sort of like a rider mounts a horse, that's how I like to think of it anyway. Once it's mounted, we have control of it more or less, and are looking down on it). So that folder is like a saddle in a way. Or you could think of it as a window that we look through and can 'see' inside the partition.
What you are seeing inside there now is your new filesystem, that's what you should be seeing, good, it looks a lot more normal now.
I can't see anything wrong with your menu.lst either, it looks okay to me. The only reason the illustration on the grub page of the dual boot site has different numbers is because it's the second partition after the Windows partition in the dual boot. Yours is a single install, so those numbers are right for your installation.

Why doesn't it boot now? WHY?

---

### Post by Herman on 2006-03-04
Okay, I'm determined we will make this operating system boot one way or another!!!
You mentioned you have a 'Super Grub Disk', oz8ball1, we'll try this from another different angle now, if you'll persevere with me. (I'm sorry this is taking so long and is so complicated, it isn't normal, you'll be an expert already before you get started).

So here's what I did, in my test computer I used a 'terminal' command to move my /boot/grub/stage2 file to my /home/herman folder and thus make my system unbootable. I get 'GRUB loading, please wait... Error 15'

I put in my 'Super Grub Disk',and pressed ctrl + alt + delete to reboot my test computer.
As soon as the CD is running I pressed 'c' for a command line.
At the grub>_ prompt I typed: ```
root (hd0,0)
``` After I press 'enter',Grub replies```
 Filesystem type is ext3, partition type is 0x83
``` Then I type:```
kernel /vmlinuz root=/dev/hda1
``` I press 'enter' agian and Grub tells me > [Linux-bzImage, setup=0x1c00, size=0x124cec] Next I type just part of the next command -don't press enter yet-:```
initrd /boot/init
``` ...now I am not sure what the rest of the file name is supposed to be exactly here, so I do a trick, I press my 'Tab' key. Grub tells me > Possible files are:initrd.img-2.6.12-9-386 initrd.img-2.6.12-10-386 Yours will probably just be initrd.img-2.6.12-9-386 and it might just auto complete your command for you. In my case I only need to add the two digits 1 and 0 and press 'Tab' again and it auto-completes. So the full command is something like:```
initrd /boot/initrd.img-2.6.12-9-386
``` probably for you, (mine was initrd.img-2.6.12-10-386 because I have recieved a new updated kernel since I installed.) Then I press 'enter'
Grub gives me:>  [Linux-initrd @ 0x79e1000, 0x50e927 bytes] Finally, I type ```
boot
``` and press 'enter'
Lots of white type scroll up the black screen for quite some time, pausing now and again momentarily, then racing up the screen again. This continues until the screen blacks out, blinks, winks, a white spot appears whirling in the center, the sound of a drum roll is heard, and the monitor turns golden tan color, and I'm at my login screen!
See what happens when you try!
This bypasses the MBR, and the Super Grub Disk has its own Stage2 eltorito, so it has to boot!
Try that! Yours might take longer because it should still have to complete the installing as soon it it re-boots.

By the way, these commands work for any Grub CLI, whether someone ends up with a Grub CLI from a floppy disk or hard drive or whatever. :-D (Herman)

---

### Post by oz8ball1 on 2006-03-04
thanks herman, its nice to know I got someone backin me with this computer.
First I want to point out that I wasn't getting the "Error 15 message," my computer was just get 'stuck' right before any error message would pop up, > GRUB Loading stage1.5.


GRUB loading, please wait...
in any case I tried your idea with the Super Disk, and I guess mine is not quite as super because once I typed in:
> kernel /vmlinuz root=/dev/hda1 it just stood there. I didn't leave it for an extended period of time, but I couldn't see or hear anything working, and this is an old semi-cheap computer so you can hear it when it's working. 
Now when I had typed > grub > root (hd0,0)I got a different response, > Filesystem type is ext2fs, partition type 0x83which is different than you listed (it adds '2fs')

Well you mentioned Grub from a floppy disk and I remember in the grub manual a page about [Creating  GRUB boot floppy]("http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating-a-GRUB-boot-floppy") so I thought I'd give that a try, try to follow those instructions see how far I got, if it didn't work I'd go back to the Super Disk and just hope that it was Super Slow and not Super not working.

---

### Post by oz8ball1 on 2006-03-04
ok, so I believe I have narrowed down the problem to that GRUB hates me and refuses to load no matter what I do. It is just that simple. No, I'm kidding, but seriously though, GRUB just freezes/hangs/stops responding, whatever you call it, it just stops. There are no blinking lights, no wurring sounds other than the fan, it just stops.

---

### Post by oz8ball1 on 2006-03-04
So I just tried to use the Install CD to fix the GRUB, by typing in "rescue" at the boot, then selecting my root partition
```
dev/discs/disc0/part1
```and then typing:
```
grub-install /dev/hda1
```
I got a...weird error message, not really an error message.
> Due to a bug in the xfs_freeze, the following command might produce a segmentation fault when /boot/grub is not in an XFS filesystem. This error is harmless and can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect, fix it and re-run the script 'grub-install'.

(hd0)     /dev/hda1
but it looked as though there were no errors, so I booted up my computer again, and nope. It got to the > GRUB loading, please wait... screen and it stayed there.
Now I don't know, maybe this is normal? Maybe I just need to let it boot for 7 hours?

---

### Post by Herman on 2006-03-04
:-D Well I don't think Grub has anything personal against you. I can tell by the way you are handling things this far that you are really going to like Ubuntu and Ubuntu is really going to like you, once we get over this one big hurdle at the start. 

Now... what would spock do in a situation like this?

We need to come up with more experiments to try to keep narrowing down the possible causes of the problem. By using a Grub CD, and maybe a Grub floppy disk, we should have bypassed any problems with your MBR on your hard disk.
It seems to me as if either your BIOS and grub can't find the kernel, or there's something wrong with your kernel.
There's a nice explanation about how a Linux computer boots in [Rute User's Tutorial and Exposition]("http://rute.2038bug.com/index.html.gz"), chapter 31. It's actually about Lilo, the boot loader that Grub replaces, but the theory is still good reading.
Basically, our kernel needs to be found by the BIOS and loaded into the memory and uncompressed and run.
Does reading that give you any ideas? I think your memory should be alright, you can run the Live CD, that is memory intensive. 
Your BIOS? The kernel? 
There's an interesting paragraph 31.4 about copying the kernel to a floppy disk to make a boot floppy, or 'RAWRIT.EXE' if you only have Windows. I might try that and see what happens.
I'm not sure whether having the feedback ex2fs rather than ext3 means anything or not, actually I have reiserfs, but I was trying to make it less confusing for you by substiting what I guessed your feedback should be.
Not finding the kernel seems to be the problem, but you showed the kernel in your first screen caps. You could have another look with the Live CD and check there's a kernel there for sure. Is it complete and fully functional I wonder?

We never did properly [verify the integrity]("http://www.users.bigpond.net.au/hermanzone/p17.htm") of your downloaded .iso did we?

Another idea, presuming your kernel is okay, is to try [installing Lilo to your Ubuntu partition]("http://ubuntuforums.org/showthread.php?t=96920"), and use [GAG bootloader]("http://gag.sourceforge.net/") to boot Lilo. It would seem like a lot of trouble, and whether that works or not still depends on your kernel. Since Lilo functions differently than Grub, it might be worth a try. I have mostly been able to install Lilo and Grub both in the same operating system but sometimes it doesn't work. More help with GAG is [here.]("http://users.bigpond.net.au/hermanzone/p12.htm")

Thanks for sticking with me so far, for me it's interesting like a puzzle, It's making me look things up and learn more. I still hope we can solve it right away for you though. It would be better if you were having fun customising Ubuntu and things you like. :-D (Herman)

---

### Post by oz8ball1 on 2006-03-06
*sigh* Well I have several boot cd's because I of unsuccessfull / iffy burns, and then slower burns, and well I wasn't sure which one was burned from what .iso, so I verified the one I had, it checked out, and I reburned it and reinstalled it and still had the grub loading screen. Well I had to go back to school so there wont be anything I can do about anything untill next weekend. But in the mean time, I'm wondering if I can use this time to do a little research, give me a general knowlege of what I'm doing. 
First of all, why wouldn't my BIOS/GRUB not be able to find the kernel? and speaking of kernels, what is a kernel? 
Also, what were those commands that you were asking me to run? What was the difference of running ```
grub> root (hd0,0)
grub> setup (hd0,0)
```
What does "Filetype" mean and why did I get a different one than you?
I tried to copy and paste the files from /media/ubuntuinstall to the actual locations in the root directory (/debootstrap and /boot/grub). What did that do? Were they just removed after I logged out of the live CD?
Any more ideas? I mean right now we can only guess, I have to go home and try these things but, thinking about a problem before trying stuff cant hurt.

---

### Post by Herman on 2006-03-06
Okay, I'm a little pressed for time right now myself, [here's a nice link]("http://users.ameritech.net/gholmer/booting.html") about how grub is supposed to boot our computers.
Lots of times some of these explanations seem hard to understand until you know what all the parts they are talking about look like. One thing that helped me a lot was having been given an old broken down computer that had been 'fried', and could be taken apart. Then I googled for information about each different part, and read all I could about the BIOS, the memory, the CPU, the motherboard, hard drive, and everything, while having some real parts in front of me on the table to compare with the pictures and explanations on websites. I'll bet there would be someone in your town who would be happy to give you an old broken computer to take apart and learn from. It helps a lot!
Only thing is I'm still learning things and I don't know when it will ever end, but it's a lot of fun. I still feel as if I don't know very much! :-D 
I will attempt to answer the questions you asked properly as soon as I get time, right now I'm waiting for a phone call and then I'll have to go for a while and I don't know how long for. You are asking very good questions, good! (Herman).:-D

---

### Post by munga_bill on 2006-03-07
> One thing that helped me a lot was having been given an old broken down computer that had been 'fried', and could be taken apart.[COLOR="Red"]Make sure you get someone to remove the power supply for you first if you go poking around in any old computers, and never touch anything inside the power suppy even when it is unplugged, it can still contian stored electricity.[/COLOR]

Here's an excellent explanation from the Ubuntu Wiki about what a file system is:  [https://wiki.ubuntu.com/LinuxFilesystemsExplained](https://wiki.ubuntu.com/LinuxFilesystemsExplained)

That is really weird that has given you feedback indicating an [ext2fs]("http://en.wikipedia.org/wiki/Ext2") one time, and mentioned an[ xfs]("http://oss.sgi.com/projects/xfs/") filke system another time.The Ubuntu installer makes an [ext3]("http://en.wikipedia.org/wiki/Ext3")filesystem by default, that's what you should expect to find.

Your [kernel]("http://www.bellevuelinux.org/kernel.html") is that thing in your /boot directory called vmlinuz-2.6.12-9-386
It's right there in your screencaps you took, it has an icon like a page with a footprint on it. Your [kernel]("http://en.wikipedia.org/wiki/Kernel_(computer)") is the main nucleus of the whole operating system, it takes over from the BIOS after your computer boots up and loads the operating system. The whole operating system depends on the kernel. Without that, (as you are well aware by now), nothing happens.

---

### Post by oz8ball1 on 2006-05-07
Hey, well I finished with school and I figured I should try to get the computer working and I did, but not for the reasons I had thought.
 While I was at school my disks from Ubuntu came in so when I got back I tried installing from that, just in case it was my disk after all. But no, same problem. So my next idea was that the hard drive might not be set up correctly, i.e. not a master. But no, it was set up right. Well before I posted again and started asking people to tell me what they had already told me, I figured it would be a good idea to read up on the old posts. While doing that I came across this one, which I had originally ignored because I thought that it wasn't really what was wrong with my computer.
[QUOTE=lazyleg]I had the same problem on a old pc (475mhz cpu 64mbram 2gig harddrive) in the bios in IDE HDD AUTO DETECTION i changed a setting to normal on MBR to solve this problem. Im running the server vs of breezy badger, and when i tried to install the desktop vs it gave me the same error.[/QUOTE]
But I tried it anyway and even when I did it didn't look right, I never saw something that said "MBR" but it looked like I need to do something, as if it had reset it self when I clicked it. I don't recall exactly what it was that I changed but it worked. after I exited the set-up it restarted like normal and started right up. 

Well thank you everyone who helped me, I'm sure I'll be back with more questions, but hopefully after I've exhausted my google-ing abilities.

---

