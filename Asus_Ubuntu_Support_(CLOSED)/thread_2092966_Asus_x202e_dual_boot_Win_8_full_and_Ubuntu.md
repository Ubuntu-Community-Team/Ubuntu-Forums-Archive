---
title: "Asus x202e dual boot Win 8 full and Ubuntu"
date: 2012-12-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Somewhat Newbie on 2012-12-09
When does anybody think that Ubuntu (Linux) experts can get around the UEFI boot problem? I' have a new Asus VIVOBOOK x202e Laptop with no Optical drive and it has 4 factory installed partitions with Win 8 preloaded, its not RT and it has a touch screen. Can't install ubuntu. I know how to shrink HDD and how to use USB drives to install but still no luck.

I have included a Photo of factory partitions they were not created by me and I do not want to erase them. Only thing I will try is shrinking of C drive.please feel free to show photo to all your friends that may help and thanks to all.

---

### Post by Bluekanoodle on 2012-12-09
You need to use a USB disk with 64 bit Ubuntu on it. the 32 bit version does not include UEFI support from what I understand

 I just picked up the same laptop yesterday and have it running with one small problem. Namely, after installing Ubuntu the windows 8 doesn't load, so I used boot repair to fix that.

---

### Post by Somewhat Newbie on 2012-12-09
[SIZE=3]Still don't know how to use this site that much, it said for quick reply pick from post and for the life of me I have no idea where post is, all I see is new reply, anyway: Question does your Ubuntu set-up have Touch capabilities are they working alright since you said you got the very same one. 

And how to use boot repair with usb since the system does not have Optical drive...Another usb or same?

Please also does yours came with factory install and four partitions that you did not touch, I image it so since you just got it. I know I sound stupid asking but need more info since I'm kind-da new.[/SIZE]

---

### Post by oldfred on 2012-12-10
Please do not use large fonts, I will adjust. It seems like you are shouting at us.

Not sure about touch screens.
But you do have to use 12.10 64 bit version and from your UEFI menu boot in UEFI mode.
Windows 8 uses gpt not MBR so there is no real partition limit.(ok really 128 max)

Use Windows to shrink the Windows NTFS partition and reboot a couple of times so it can update its own settings. 12.10 will install on some systems with secure boot on. Others require secure boot off. 
If you have a fast boot or quick boot setting turn that off also.

If you have Ubuntu on a USB flash drive, you can just download Boot-Repair into the flash drive to run it.

       GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    different model but Asus:
       Windows 8 & Ubuntu  ASUS K55A 
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Somewhat Newbie on 2012-12-10
old fred before I read your advice, I've decided to reply as quickly as possible because of what you said at the beginning of your help.

By no means will I ever shout at anyone in this forum, My english skills are limited, so maybe, just maybe I' fail to put my words as I' write in a more correct manner, but please accept my apologies if and when you feel I have offended you, not my intention at all.

I' write english in a very basic manner and it can come across as shouting or disrespectful in some way but since I try to be as concise with as few words as possible, this is what happens when english is not your primary language, so again I' m sorry for how I sound in writing.

If I' fight with you in these forums at all please enjoy it as a friend, it will never be personal I' assure you.

Friends sometimes scream at each other and even if I'm new at these Linux (Ubuntu) forums I consider all Linux users friends, don't know exactly why.

Maybe, cuz we are all rebels I' think, rebels in a good way, I' believe in such a thing. OK now to my post...#0002

have a Popcorn on me :popcorn::mad::wink:

---

### Post by Somewhat Newbie on 2012-12-10
Please mark this thread as SOLVED, because with my current level of expertise in terms of eventually doing what I'm trying to do, it will take some time to resolve. Yet the reason why I' started the thread have already been solve by you and the first responder to the thread, it's just a question of me getting the nerve to actually doing it, and its too bad you could not tell me more regarding touch screens, not your fault.

Will keep up with the Ubuntu community until someone reports what happens with Ubuntu 12.10+ when installed in a dual boot scenario with Win 8 Pro in a touch screen computer. I have no desire at all to dual boot Win 7 or Win 8 with Ubuntu in regular non touch laptops: done that been there. For my reg. laptop and desktop I' only use Ubuntu triple booting with Zorin and Mint and trash Windows totally out of those computers, but must keep Win 8 in touch laptop so I can learn it as best I' can. Also I just can't wait for Dell and Cononical to come up with a 7" or 10" touch pad if they ever do. I' know about the ultrabook server edition but thats not for me even if it comes out in a non server edition. Ok so thank you and the rest of you guys and girls for all your help. I' need a Youtube video link that features a dual boot between Win 8 pro (non dev. edition but the retail edition or that came preloaded with the laptop as you would normally would buy it with the healthy restore partitions that come from the factory that can numbered up to 4) and Ubuntu 12.10(UEFI), all just to use Ubuntu in touch if possible, maybe its just that Linux cannot be use as a touch interface, don't know, it might be because of the bios or something. I just don't have much knowledge but my ignorance is not going to keep me from enjoying Linux.

Too bad the web is full of videos of dual boot Ubuntu and Win 8 developer editions and not videos of how to deal with 4 factory install partitions you may or may not want to get rid of.

Sorry for the lengthy of the post but it might help others as well. It seems that I'm making a problem were there is non, because if I just follow the advice you have already given me, problem truly solved, but in regards to touch screens I need more. If you know of any links to videos that can take me by the hand, it will be very helpfull indeed. I'm like V'ger (a child) lol.

Thanks you all, very greatfull!!!!

---

### Post by oldfred on 2012-12-10
No problem, it was just the large type.

Does liveUSB boot ok? That at least is a test if it will work. 

I have a variety of threads of successful installs, only a few are the new Windows 8 with secure boot. Some of the new Windows 8 have worked without issue, some have had issues but worked around them, and a few are still having issues. So if at all concerned, there is no issue in not modifying a system you want to make sure keeps working.

---

### Post by Somewhat Newbie on 2012-12-10
Oh ok

Negleted to notice your ware only referring to the large fonts, I guess I' can't deny I'm new to the concept of forums, plus since the website gave me that option I use it, without considering how it would look to others. oop's

Yea! the usb worked but at the log on or better said choose which to boot from it wouldn't allow it; to boot on the Ubuntu OS button, just above the reg. Win 8 clicker that when I press it, it (win 8) booted perfectly. 

I' just know I' not the only one that will encounter this particular set of variables, so someone will eventually put up a video somewhere regarding how to. So if anybody knows of such please let know the rest of us.

Just in case:

Video should show Win 8 Reg. dual booting with Ubuntu 12.10 on a touch screen and demonstration of Ubuntu on said touch screen being use, Just saying...

As Friend Old Fred stated in regards to touch screens he can't help me there, Yet, But I'm sure its just a question of time before you all will want to try any Linux flavor on a touch screen and some will be on the new computers with the UEFI bug.

If I'm not making sense please somebody just tell me, promise I' won't get upset about it.

I' have loads of patience and will be able to wait for future videos on Youtube and other places about this. I can't help but to think that my problems with wanting a video to take me by the hand as I stated before, its because almost everybody that has already made such a video, has done so with the free download of win 8 that came out some time ago and as far as I' know its not the same thing as  preloaded version of win 8 with all the partitions that Asus has put into them and also have not seen Ubuntu being use on a touch screen. I' know I'm repeating myself, I ask all to allow me just a bit.

PS. I' just realize that I've move to what looks like a different subject and I' got my answer regarding UEFI, It works. Just not for me Yet...

---

### Post by Bluekanoodle on 2012-12-10
To answer, your other question, yes the touch screen does work. To be honest though, getting this unit to dual boot Win 8 and Ubuntu has been a total pain. I ended up giving up on Windows 8 and putting a new SSD drive on it and only installed Ubuntu. 

I picked up this machine only to run Linux on, but your needs may be different.

---

### Post by Somewhat Newbie on 2012-12-10
Thank you so much Bluekanoodle, I just new that I was not the only one having the pain as you so plainly said. But you are right in other regards, I have other needs I will not allow Microsoft to dictate to me that I have to use my equipment as they see fit. I will dual boot Win 8 and Ubuntu touch someday somehow and now that I know touch works fine I will get it done more so.

I refuse to have to erase Win 8 which I was force to pay for because nobody has built laptops at reasonable price with Linux, Canonical and others need our help in terms of money. I' think they would get it (money) if they just built them and be honest to consumers about it ( Just state if you buy this computer you will be able to get into the internet including all your favorite social sites and you will be able to use this computer for your your childs school research but its not windows ( IN BIG RED LETTERS) and this computer at this price is for gutsy buyers only.

If need be make them only available via linux websites so they too can get funding although It might not be cost effective, don't know. Plus if its at the lowest price possible they will come: Linux is ready, does not need fixing anymore, its time to sell computers with it at a lower price then Microsoft period. Well I' guess I'm just upset and I' know this forum is for helping solve problems not us giving opinions.

Back to the my Asus problem Thanks again and will be checking out the net for video how to's .

Thank you ----more on page 2

---

### Post by Somewhat Newbie on 2012-12-10
Bluekanoodle you mention that you replace the drive with an ssd drive.

Question was it easy to find and remove since this computer is one of those that does not show the compartment for memory and/or drive clearly pinpointed.

In other words it seems like you have to take out the entire back cover to access the hdd, did it fall apart on you or was it very easy, I' just might go your route after all; After all. All I' want is to keep Win 8 since I' paid it after all.

I' love english, even if I can't spell, lol

want to keep win 8, I know, sounds sick. lol

---

### Post by ubunik on 2012-12-17
I have this Asus laptop, mine now dual boots to a point.

I deleted the Windows D: partition and installed Kubuntu 12:10 into this space. My first attempt was with the DCD from linux format magazine This seemed to install but would not boot. I had to enable a legacy emulation mode in the BIOS to be able to boot this DVD. Obvioysly if it is in legacy emulation it will not see the EFI information on the disk.

Second attempt was using an ISO downloaded from the net with which I created a bootable USB drive. This was done with "Universal USB Installer" within windows. I asked the Kubuntu installer to write the boot loader to the install partition (/dev/sda4 I believe)

Once installed I found that I could select to Boot either Windows 8 or Linux within the system setup utility.

I eventually found the boot selector menu by hitting <ESC> while booting.
Now "System Setup" is configured to boot Linux and a press <ESC> during boot when I occasionally run Windows

Hope this helps
Nick

---

### Post by jpmolla on 2012-12-17
Hi ubunteros !
I don't know if someone has really resolved this point but it is a paine for sure. I really like the x202e and as I need to discover Windows 8 for work, I would never have my computer without Linux and not just in virtual env.

I had problems with 2 first laptops that went back to the shop for replacement. I think that was not an ASUS problem but a shop problem ! Anyway... I had time to try Ubuntu / Windows 8 dual boot with some little success, but not complete.

First of all, without power on the computer, I do a ghost of all the disk with Clonezilla. For that, I use Hiren's Boot CD from a... USB key :-). As soon as I switch on the laptop button, I press the DEL button (closer) or the F2 (no defference) to enter to the BIOS. Disable "Security boot", save, reboot and come back imediatly to the BIOS to select the USB without EFI as first boot. If you miss the BIOS menu, don't panic, just wait the Windows 8 langage menu, press the power button and stay pressed during more than 5 sec until the battery light switch off (it means that's not just hibernation). Then try again. When you start on the Hiren's boot USB, start MagicParted and use Clonezilla. Tutorials can explain how to use it (I am not gonna do that)

Now that everything is backup up I can play with the computer.

First of all the partitions from Windows (need to change the BIOS to default values). What I have done is the installation of Windows 8 and as soon as I am connected, I use the Computer Management program to resize the wondows partition. Doing this from Ubuntu has made error which needed to repair the partition. I have let 110 Go for Windows I think that it is suffisant enough...

Then I switch off COMPLETELY the computer (power button > 5 sec). I insert the Ubuntu 12.10 x64 USB key then play again with the BIOS to disable Security Boot  and select the right USB. I have read several things about creating a boot partition but it didn't worked for me. What I have done is to create the SWAP (4GB) as use the empty space for "installing Ubuntu alongside windows". That really is the easy way which worked. As soon as everything is installed, a new entry appear in the BIOS (yes ! that's an entry installed and detected in the first partition of the disk : the EFI partition) You can select it to boot to Ubuntu but without EFI (secure boot = false)

When you're log into Ubuntu, look at the Unity menu at the left and select "repair boot" (or something like that) then you have to enable the EFI option. After that you can boot to Ubuntu in UEFI mode (secure boot = enabled) 

Now... At this point is there a problem to boot from windows 8 to Ubuntu from a boot menu ? From Ubuntu no, it works; from Windows 8 yes ! Many forum refer to EasyBCD to dual boot from windows beautiful blue menu, but to me it never worked and I have given up. I can do that from Ubuntu menu so that's great.

I am sorry, my english is kind of poor and I wrote that very quickly because I am in hurry but I just tried to bring some interesting informations (if that is) and that with you.

If some points are wrong or not clear, please tell it and correct me ! And if someone has a better understanding of all of this to make it work in a better way, please share it !

Thanx a lot ! and happy dual boot !

---

### Post by Somewhat Newbie on 2012-12-18
Thanks for the info. Question I' assume "D" Partition was your healthy recovery partition that was preloaded by factory and now you could never restore your machine to factory specs, If not how did you overcome this, if indeed it was a restore partition?

You didn't mention what kind of partition was it that you erase, as per my photo at the start of this tread I' can only see partition "C", I' will try to identify the rest, since I'm on patience mode waiting for future videos on the net regarding this subject, I' haven't done so yet. I' saw one video and it said that the restore partition had to go because Windows would never allow more then 4 partitions on the HDD, yet I' was under the impression that since we are talking about GPT and not MBR, then it would not matter.

---

### Post by Somewhat Newbie on 2012-12-18
Mr Molla your english is fine, You have guts and all it took was two trips back to the store and you found a way. Well I' find your solution a bit complicated for me, but if this is the only way then I'm going to be thinking long and hard as to how to proceed, so I'm assuming that your instalation is on Partition "C" and you have not erase any partition at all thus you have 5 or 6 partitions in your HDD and/or you intalled Ubuntu on swap space, did not know that was possible, but even if it is your ended up with very little room for Linux. I'm a little confuse as to how your set-up is, is it possible for you to include a photo, if not thanks for for input.

---

### Post by Somewhat Newbie on 2012-12-18
JPMOLLA  reposted you post, I hope you don't mind, just in case someone may be confuse as to your unorthodox method which apparently worked for you,


if I've neglected something special that needs to be clarified then I'll remove it if I' can.

[SIZE=5]
[/SIZE]
[SIZE=5]I do a ghost of all the disk with Clonezilla. For that, I use Hiren's Boot CD from a... USB key. As soon as I switch on the laptop button, I press the DEL button Disable "Security boot", save, reboot and come back imediatly to the BIOS to select the USB without EFI as first boot.When you start on the Hiren's boot USB, start MagicParted and use Clonezilla. 

First of all the partitions from Windows (need to change the BIOS to default values).  I use the Computer Management program to resize the wondows partition. 

I insert the Ubuntu 12.10 x64 USB key then [/SIZE][SIZE=5]back[/SIZE][SIZE=5] again [/SIZE][SIZE=5]to[/SIZE][SIZE=5] the BIOS to disable Security Boot and select the USB. What I have done is to create the SWAP (4GB) a[/SIZE][SIZE=5]nd use[/SIZE][SIZE=5] the empty space for "installing Ubuntu alongside windows". That really is the easy way which worked. As soon as everything is installed, a new entry appear in the BIOS (yes ! an entry in the first partition of the disk : the EFI partition) You can select it to boot to Ubuntu but without EFI ([/SIZE][COLOR=#0000ff][SIZE=5]**secure boot = false **[/SIZE][/COLOR][COLOR=#0000ff][SIZE=5]**or desabled**[/SIZE][/COLOR][SIZE=5])

When you're log into Ubuntu, look at the Unity menu at the left and select "repair boot" then [/SIZE][COLOR=#ff0000][SIZE=5]**you have to enable the EFI option**[/SIZE][/COLOR][SIZE=5]. After that you can boot to Ubuntu in UEFI mode ([/SIZE][COLOR=#0000ff][SIZE=5]**secure boot = enabled**[/SIZE][/COLOR][SIZE=5]) 

[/SIZE][SIZE=5]P[/SIZE][SIZE=5]roblem[/SIZE][SIZE=5]s[/SIZE][SIZE=5] to boot from windows 8 to Ubuntu from a boot menu? [/SIZE][SIZE=5]_From Ubuntu _[/SIZE][COLOR=#ff0000][SIZE=5]_**no**_[/SIZE][/COLOR][SIZE=5]_, it works_[/SIZE][SIZE=5]; from Windows 8 [/SIZE][COLOR=#ff0000][SIZE=5]**yes**[/SIZE][/COLOR][SIZE=5]! Many [/SIZE][SIZE=5]in the [/SIZE][SIZE=5]forum refer to EasyBCD to dual boot from windows, but [/SIZE][SIZE=5]for[/SIZE][SIZE=5] me it [/SIZE][SIZE=5]has [/SIZE][SIZE=5]never worked. [/SIZE][COLOR=#ff0000][SIZE=5]_**I can**_[/SIZE][/COLOR][SIZE=5] do that [/SIZE][COLOR=#ff0000][SIZE=5]_**from Ubuntu menu**_[/SIZE][/COLOR][SIZE=5].[/SIZE]

---

### Post by ubunik on 2012-12-18
> **Somewhat Newbie said:**
> Thanks for the info. Question I' assume "D" Partition was your healthy recovery partition that was preloaded by factory and now you could never restore your machine to factory specs, If not how did you overcome this, if indeed it was a restore partition?

You didn't mention what kind of partition was it that you erase, as per my photo at the start of this tread I' can only see partition "C", I' will try to identify the rest, since I'm on patience mode waiting for future videos on the net regarding this subject, I' haven't done so yet. I' saw one video and it said that the restore partition had to go because Windows would never allow more then 4 partitions on the HDD, yet I' was under the impression that since we are talking about GPT and not MBR, then it would not matter.

My Laptop, from amazon.co.uk came with C: and D: NTFS partitions. The D: had nothing on it. I created two USB Windows recovery disks before I started. The limitation of 4 partitions has been removed with UEFI boot. It is something like 128 or 256 now. There is no need to loose the recovery partition. I wish I had videod the process now or at least taken some screen dumps.

I have found problems booting when quickboot is enabled in BIOS.

---

### Post by Somewhat Newbie on 2012-12-18
> **ubunik said:**
> My Laptop, from amazon.co.uk came with C: and D: NTFS partitions. The D: had nothing on it. I created two USB Windows recovery disks before I started. The limitation of 4 partitions has been removed with UEFI boot. It is something like 128 or 256 now. There is no need to loose the recovery partition. I wish I had videod the process now or at least taken some screen dumps.

I have found problems booting when quickboot is enabled in BIOS.

I' hear you and totally understand what you are saying, I' heard about the max being now 128, but my laptop I' think is not the same as yours, it has no DVD drive and I've yet to buy an external one, don't really want to use USB for installation, so I' think after buying the ext. CD/DVD drive I'm going to give it a go. Your have touch screen?

---

### Post by ubunik on 2012-12-18
> **Somewhat Newbie said:**
> I' hear you and totally understand what you are saying, I' heard about the max being now 128, but my laptop I' think is not the same as yours, it has no DVD drive and I've yet to buy an external one, don't really want to use USB for installation, so I' think after buying the ext. CD/DVD drive I'm going to give it a go. Your have touch screen?

I first tried with a DVD but the ASUS wouldn't boot from it in UEFI mode. If you want to dual boot I think that this is going to be a must. It is possible that other DVD drives will be seen. Go on, give the USB thumb drive boot a go.

Yes I have touch screen in Linux, but also added "Grab and Drag" to Firefox.

Nick

---

### Post by Somewhat Newbie on 2012-12-18
> **ubunik said:**
> I first tried with a DVD but the ASUS wouldn't boot from it in UEFI mode. If you want to dual boot I think that this is going to be a must. It is possible that other DVD drives will be seen. Go on, give the USB thumb drive boot a go.

Yes I have touch screen in Linux, but also added "Grab and Drag" to Firefox.

Nick
So as I've been informed touch works fine with Ubuntu on this type of bios, so I'll see if a Usb install will work this time and Yousr is the same Laptop vivobook x205e?

No need to answer me, I will post results but it might take me sometime, I' ve got too many other things to do. You can advice me at any time, I regularly check back here. 

Plus to anyone; Does anybody know if the mbr in our case the gpt needs to be fix when removing the install?

---

### Post by oldfred on 2012-12-18
gpt drives have what is called a protective MBR so old MBR utilities will see that it is formatted with gpt. It has one partition entry for the entire gpt drive.

You can install a grub boot loader to the protective MBR's boot area, if booting in BIOS mode with Ubuntu, but then you need a bios_grub partition. 

Windows will not boot from a gpt partitioned drive with BIOS so it cannot use MBR.

---

### Post by ubunik on 2012-12-18
> **Somewhat Newbie said:**
> So as I've been informed touch works fine with Ubuntu on this type of bios, so I'll see if a Usb install will work this time and Yousr is the same Laptop vivobook x205e?

No need to answer me, I will post results but it might take me sometime, I' ve got too many other things to do. You can advice me at any time, I regularly check back here. 

Plus to anyone; Does anybody know if the mbr in our case the gpt needs to be fix when removing the install?

My laptop is an s200e however I beleieve that this is called the x202e in other markets.

---

### Post by Somewhat Newbie on 2012-12-18
> **ubunik said:**
> My laptop is an s200e however I beleieve that this is called the x202e in other markets.
Yea its the same in some regards like style and options, only you have Intel pentium and I' have Intal core i3 from I can find in the net. The Same "period",  what gets to me is why you only had two partitions were is I' have four and I have believe that a partition that has nothing in it, could actually have the restore files, but can't be seen, yet they are there, well You are most like right and I'm not, I to new to all this. Lets see what I do eventually, thanks again.  

I'm going to reply to oldfred the moderator cuz he has been very helpful but I'm lost regarding GPT AND just new stuff all together.

---

### Post by ubunik on 2012-12-18
> **Somewhat Newbie said:**
> Yea its the same in some regards like style and options, only you have Intel pentium and I' have Intal core i3 from I can find in the net. The Same "period",  what gets to me is why you only had two partitions were is I' have four and I have believe that a partition that has nothing in it, could actually have the restore files, but can't be seen, yet they are there, well You are most like right and I'm not, I to new to all this. Lets see what I do eventually, thanks again.  


This one is an i3

```
nick@nick-asus:/$ cat /proc/cpuinfo | head -5
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 58
model name      : Intel(R) Core(TM) i3-3217U CPU @ 1.80GHz

```

I didn't say that I only had 2 partitions, I said that I had 2 NTFS partitions. There was definitely a recovery partition or two.

---

### Post by Somewhat Newbie on 2012-12-18
> **oldfred said:**
> gpt drives have what is called a protective MBR so old MBR utilities will see that it is formatted with gpt. It has one partition entry for the entire gpt drive.

You can install a grub boot loader to the protective MBR's boot area, if booting in BIOS mode with Ubuntu, but then you need a bios_grub partition. 

Windows will not boot from a gpt partitioned drive with BIOS so it cannot use MBR.
OldFred have you looked at the attach photo in the start of this tread? It has 4 partitions any way of knowing which one is the MBR?

My Old reliable way with 2 partions from the store:: 

A) First Partition about 100 MB's for Windows 7 marked  *

B) Second "C" Drive Partition  = from here I' take 80 GB's on a 500 GB HDD

C) I" take 3 GB's for Swap from the 80 marked /

D) I' take the rest as /home

now I may be missing info like logical and primary and other stuff but you get the idea...

OK so here is the problem I now have 4 partitions lets just call them Partitions

P1

P2 

P3
 
P4

in p1 its the MBR lets say

in p2 is a recovery dare not erase

in p3 the "c" drive I will make space to install Ubuntu 12.10 64 Bit and swap space and everything else I'll follow advice as how to do this right from many videos on Youtube.

in p4 more recovery again dare not touch

back to the how to's

get into bios, turn off quick boot, set boot from USB reboot into usb run live and install from live unto a set-up (the partition /home ) that I create during the install, now I' don't have to erase non of my factory partitions and now all I need is how to set the boot in MBR and not GPT and turn quick boot on again, as you can see I' don't know what the crap I'm doing but if this helps somebody else in Ubuntu forums that will make me happy and I'll keep waiting, you see I must not damage this computer iti's the only with touch screen for the moment  that i have and I' must keep Win 8. 

Lets just say that if something goes wrong and I have to delete the partition were Ubuntu is located, well I' loose the proper boot sequence for Win 8 and I'm barely now learning how to fix the MBR for Windows 7, now I' have to learn how to fix GPT, I' don't even know if it can be fix. So just do a restore from the factory partitions would be my only chance, that is why I'm taking my time with this. Thanks and hope others can benefit from these writings.

---

### Post by ubunik on 2012-12-18
My partition table if it helps (From gdisk)

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  EFI system partition
   2          616448         1845247   600.0 MiB   2700  Basic data partition
   3         1845248         2107391   128.0 MiB   0C01  Microsoft reserved part
   4         2107392       392816639   186.3 GiB   0700  Basic data partition
   5       926654464       934809599   3.9 GiB     8200  
   6       934809600       976773119   20.0 GiB    2700  Basic data partition
   7       392816640       926652415   254.6 GiB   0700  

```

also mount

```
/dev/sda7      262728796 5704468 243678436   3% /
udev             1953488      12   1953476   1% /dev
tmpfs             786544    1024    785520   1% /run
none                5120       0      5120   0% /run/lock
none             1966352     148   1966204   1% /run/shm
none              102400      12    102388   1% /run/user
/dev/sda1         303104   50096    253008  17% /boot/efi

```

---

### Post by oldfred on 2012-12-18
With UEFI/gpt you do not have to worry about MBR. All the boot loaders are in the efi partition. If you delete a system, you can still go into the UEFI menu and boot anything that still is installed. 

With BIOS you can only have one boot loader in the MBR and you delete the system using the MBR then you cannot boot anything until you repair MBR.

With gpt all partitions are primary and there is no 4 primary partition limit. So no conversion of one primary to extended to create logicals. 

You can do like ubunik and post these or review yourself to see what is used. Often the vendor partitions are labelled & I suggest labelling partitions.

       sudo parted /dev/sda unit s print
    or
       sudo gdisk -l /dev/sda
    and 
mount
or 
df -h

---

### Post by jpmolla on 2012-12-18
@Newbie
Yep the story about twice back to the store is not really the subject. What was interesting was the install/uninstall processes without problems (but not always...).

As I come back to my post I realise something : doing things fastly is unproductive ! Some points really needs much more explanations, You're right.

So, First of all, the point on the partitions (in unix langage) given by Clonezilla.
Here is my disk :
sda (500GB_ST500LT012)

And here are the partitions of that disk:
sda1 (315MB_vfat_NO_NAME) --> The EFI partition
sda2 (629MB_ntfs_Recovery)
sda3 (134MB_Microsoft) --> A specific Windows format 
sda4 (200GB_ntfs_OS) --> The "C:" drive under Windows
sda5 (278GB_ntfs_Data) --> the "D:" drive under Windows
sda6 (21.5GB_ntfs_Restore)

So I will not speack about "C" or "D" but about sdaX, because C and D are just the visible part of the iceberg... from Windows :).

__What are my plans__ ?

First : backup the whole disk in case you need to go back to the original configuration. That is the reason of my explanation about Clonezilla, but I agree that this is not the main subject and could be more confusing. Nevertheless the ability to restore original things seems important to me. So keep in mind.

About the partition, here is what I have decided (this is my choice but you could make another one) : I keep the sda5 partition as it is (so that I can use it as an "exchange" part between both systems), and i reduce the size of the sda4 partition to free space for Ubuntu.

I wanna reduce the windows system partition from 200GB to 110GB. I will not reduce this partition from Linux because it is a Windows one, and Windows doesn't like that others touch to its parts (I wonder why...). From Windows it is easy to do that (from the command line : "diskmgmt.msc", then select the part and reduce).

Then from the Ubuntu live disk (not yet installed) I can launch Gparted to prepare the work for the Linux part. I just create a 4GB of SWAP space at the end of the free space (that's my choice to do that by myself - I love playing with partitions :-D). Since EFI doesn't worry about the previous 4 primary partitions limitation of the MBR it is not a problem. Then Ubuntu will use the rest of the UNALLOCATED SPACE to create an Ext4 partition (so it will not be installed on the swap part, as you wrote, but will just use it for its swap needs). Later, I will reduce the "/" mount point and move the "/home" to a new partition I will create (that's the choice I made too), but this is not a really important point.

__About the POST (Power-On Self Test)__ :

I use it first as a pivot for my booting process, especially until EFI support is later installed under Ubuntu. You can switch from Windows partition to the Ubuntu one (or the opposite) from the BIOS menu directly. That is kind of magic to me : You install a distro on your machine witch install a boot file (grub2) on the EFI partition. Then, from the BIOS, you can select this declared partition as it used to be for a physical drive in the MBR BIOS version. That's really great !

But as I don't wanna enter to the BIOS each time I wanna switch, I'd like to do that from an OS boot menu. So when Windows/Ubuntu respectly boots (after the POST) I would find great to access to a menu where I can select Ubuntu or Windows. That is the point where I succeed to do that with Ubuntu but not with Windows (and EasyBCD).

I hope things are much more clear to your mind :-)

Special thanx to oldfred for your explanation about EFI. That's real instructive! THANX ! (I am not shouting :-))

---

### Post by Somewhat Newbie on 2012-12-18
> **jpmolla said:**
> @Newbie
Yep the story about twice back to the store is not really the subject. What was interesting was the install/uninstall processes without problems (but not always...).

As I come back to my post I realise something : doing things fastly is unproductive ! Some points really needs much more explanations, You're right.

So, First of all, the point on the partitions (in unix langage) given by Clonezilla.
Here is my disk :
sda (500GB_ST500LT012)

And here are the partitions of that disk:
sda1 (315MB_vfat_NO_NAME) --> The EFI partition
sda2 (629MB_ntfs_Recovery)
sda3 (134MB_Microsoft) --> A specific Windows format 
sda4 (200GB_ntfs_OS) --> The "C:" drive under Windows
sda5 (278GB_ntfs_Data) --> the "D:" drive under Windows
sda6 (21.5GB_ntfs_Restore)

So I will not speack about "C" or "D" but about sdaX, because C and D are just the visible part of the iceberg... from Windows :).

__What are my plans__ ?

First : backup the whole disk in case you need to go back to the original configuration. That is the reason of my explanation about Clonezilla, but I agree that this is not the main subject and could be more confusing. Nevertheless the ability to restore original things seems important to me. So keep in mind.

About the partition, here is what I have decided (this is my choice but you could make another one) : I keep the sda5 partition as it is (so that I can use it as an "exchange" part between both systems), and i reduce the size of the sda4 partition to free space for Ubuntu.

I wanna reduce the windows system partition from 200GB to 110GB. I will not reduce this partition from Linux because it is a Windows one, and Windows doesn't like that others touch to its parts (I wonder why...). From Windows it is easy to do that (from the command line : "diskmgmt.msc", then select the part and reduce).

Then from the Ubuntu live disk (not yet installed) I can launch Gparted to prepare the work for the Linux part. I just create a 4GB of SWAP space at the end of the free space (that's my choice to do that by myself - I love playing with partitions :-D). Since EFI doesn't worry about the previous 4 primary partitions limitation of the MBR it is not a problem. Then Ubuntu will use the rest of the UNALLOCATED SPACE to create an Ext4 partition (so it will not be installed on the swap part, as you wrote, but will just use it for its swap needs). Later, I will reduce the "/" mount point and move the "/home" to a new partition I will create (that's the choice I made too), but this is not a really important point.

__About the POST (Power-On Self Test)__ :

I use it first as a pivot for my booting process, especially until EFI support is later installed under Ubuntu. You can switch from Windows partition to the Ubuntu one (or the opposite) from the BIOS menu directly. That is kind of magic to me : You install a distro on your machine witch install a boot file (grub2) on the EFI partition. Then, from the BIOS, you can select this declared partition as it used to be for a physical drive in the MBR BIOS version. That's really great !

But as I don't wanna enter to the BIOS each time I wanna switch, I'd like to do that from an OS boot menu. So when Windows/Ubuntu respectly boots (after the POST) I would find great to access to a menu where I can select Ubuntu or Windows. That is the point where I succeed to do that with Ubuntu but not with Windows (and EasyBCD).

I hope things are much more clear to your mind :-)

Special thanx to oldfred for your explanation about EFI. That's real instructive! THANX ! (I am not shouting :-))
Ubunik thank you.

oldfred in a moment please.

jpmolla: Thanks, yes It's clearer, now let me see Ubuntu will later come out with 13.4 13.10 and dual booting will be made simpler with UEFI and GPT's and Efi partition which I' think is the same as UEFI, maybe not. In other words they are working on it.

So for now leave everything as is just reduce my "C" drive and do everything as normally just make sure to boot from mbr and disable quick boot also making sure to install; GRUB 2 to the EFI/UEFI partition. I wonder how to tell which one is the EFi Partition in my HDD. Will look again with Gparted on a live cd

---

### Post by Somewhat Newbie on 2012-12-18
> **oldfred said:**
> With UEFI/gpt you do not have to worry about MBR. All the boot loaders are in the efi partition. If you delete a system, you can still go into the UEFI menu and boot anything that still is installed. 

With BIOS you can only have one boot loader in the MBR and you delete the system using the MBR then you cannot boot anything until you repair MBR.

With gpt all partitions are primary and there is no 4 primary partition limit. So no conversion of one primary to extended to create logicals. 

You can do like ubunik and post these or review yourself to see what is used. Often the vendor partitions are labelled & I suggest labelling partitions.

       sudo parted /dev/sda unit s print
    or
       sudo gdisk -l /dev/sda
    and 
mount
or 
df -h
Ok UEFI/GPT and EFI are all the same thing, I forget about MBR because I' might have repair the same MBR later, so just install grub2 on the EFI partition and Ubuntu on the "c" drive thats it.

Boot with quick boot disabled, you know what gets confusing is when others say to go back and enable quick boot again  and still others that have made videos dual booting WIN 8 DEV edition and Ubuntu 12.10 and they go on and on about setting logicals and primarys and all the same as before, before restricted boot I' mean. You know they talk about booting from bios and not regular booting, they also mention the pain involve in dual booting win 8 and  Ubuntu. 

Correct me if I'm wrong Canonical will soon come out with an Ubuntu that will recognize the EFI partition and ask you if you want to install next to Win 8.

Is ubuntu working on having the installer recognize GPT?

---

### Post by oldfred on 2012-12-18
I think I mentioned very early on. If you use the 64 bit version of 12.10 it will install with Windows 8. Some have reported it works even if secure boot is on, but you may have to have it off to install. Some have had issues and a few have major issues which seem to be more with UEFI bugs. 

Some also have incorrectly installed Ubuntu in BIOS mode where it uses MBR, but Boot-Repair will fix by uninstalling grub-pc (for BIOS) and installing grub-efi (for UEFI). Your install of Ubuntu is not different other than a couple of minor settings.

The only remaining major bug is that grub2's os-prober still creates BIOS chain load entries to boot Windows which will not work. Boot-Repair will add entries that do work.

It is my understanding that grub2 2.00 that is currently with 12.10 will also then be included in 12.04with next point release in Jan. so it will boot with secure boot systems. Current 12.04 will install to UEFI, but not secure boot (although I did just see some updates to grub2 1.99 that said something about secure boot?).

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by Somewhat Newbie on 2012-12-19
[SIZE=3]Oldfred[/SIZE]
  

  [SIZE=3]Yes you did mention that Ubuntu 12.10 64 bit is the one to use and that is why I' have repeated as much as possible that fact about how to proceed...[/SIZE]
  

  

  [SIZE=3]the rest of your input is just helping me and I think others to totally understand GPT/UEFT and restricted  boot, so for slow to understand Ubuntu users like myself  it's  been very helpful your continued advice...I' read everything you say and then I' try to make it compute in my brain, so I' learn not just get it done..I' go to every link you provide and read and also try to get it cemented in my head.[/SIZE]
  [SIZE=3]Like [COLOR=#0000ff][SIZE=6]_Question #1_[/SIZE][/COLOR]? When installing all to EFI mode do the requirements for what use to be “/” and “/home” and “swap” all gets put in it's place automatically even when we choose “something else” during the install. You know stupid questions like this one, well no question is stupid when you simply don't know right? Answers to this types of basic newbie questions are the bread and butter of site's like this one in my opinion. I' will accept any opinion to contrary or in favor.[/SIZE]
  

  

 [SIZE=6]_I' do not consider these large fonts to be shouting_[/SIZE]
 

  [SIZE=5]just making sure we all see that we need answers to these questions and also to help people see very important info they must not miss.[/SIZE]
 

 [COLOR=#0000ff][SIZE=6]_Question #2_[/SIZE][/COLOR]
 [SIZE=6]_What is the best way to tell whether your Win 8 Pro is install on Efi partition or Legacy?_[/SIZE]
 

 

 [SIZE=5]I'm not a member of the moderators group, I' practically have no knowledge, so take my advice lightly.[/SIZE]
 

 

  [SIZE=5]To install Ubuntu in EFI mode: [/SIZE] 
 
[LIST]
[*]Use a 64bit disk of Ubuntu ([32bit 	installer does not detect EFI]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))  	
[*]Use the last version of Ubuntu.  	
[*]Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") 	appeared in 12.10.  	
[*]Setup your firmware (BIOS) to boot the 	disk in UEFI mode,
[*] 	Then:  	

[LIST]
[*]nothing special is required use 		the manual partitioning ("Something else"), the 		difference is that you will have to create and use an EFI 		partition, on how to do this I'm still finding out or maybe my 		store bought win 8 factory preloaded laptop already has this 		partition I' need to find this out also before proceeding.  		
[*]
[/LIST]
 
[/LIST]
 We must have patience in this things _**who cares if we don't see our beloved Ubuntu on our new computer with restricted boot for a week or more, things must be done right and even still there is no guaranty that we won't have issues.**_
 

 

 Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below:  
 
[LIST]
[*]if the other 	systems (Windows 8, Linux...) of your computer are installed in EFI 	mode, then you must install Ubuntu in EFI mode too.  	
[*]if the other systems (Windows, 	Linux...) of your computer are installed in Legacy (not-EFI) mode, 	then you must install Ubuntu in Legacy mode too.  	
[*]if Ubuntu is the only operating system on your computer, then 	it does not matter, you can install Ubuntu in EFI mode or not your 	choice.  	
[/LIST]
 [COLOR=#0000ff][SIZE=6]_Question #3_[/SIZE][/COLOR]
 [COLOR=#ff0000][SIZE=4]_**Pay attention to the word “mode” not partition.**_[/SIZE][/COLOR]
 [SIZE=6]**Is efi mode and efi partition the same? **[/SIZE] [COLOR=#ff0000]_We must find out..._[/COLOR]
 


 ** Identifying if the computer boots the HDD in EFI mode**

  This is possible only if you have already installed Ubuntu on the HDD, or by looking at the BIOS setup (see paragraph below).  
 From an Ubuntu installed on the HDD [COLOR=#ff0000][SIZE=5]**(neither live CD nor liveUSB)**[/SIZE][/COLOR], open a terminal (Ctrl+Alt+T), then type the following command:  
  [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"  
 Remark: if the result is "Legacy boot on HDD", then either the BIOS is not UEFI type, or the BIOS is not setup to boot the HDD in UEFI mode.  
 


 


 ** Identifying if the computer boots the CD in EFI mode**

 Warning: [COLOR=#ff0000][SIZE=5]**even if your PC boots the CD in EFI mode, it might boot the HDD in Legacy**[/SIZE][/COLOR][SIZE=4]_** mode (**_[/SIZE][COLOR=#0000ff][SIZE=4]_**and the **_[/SIZE][/COLOR][SIZE=4]_**contrary). **_[/SIZE] 
 [SIZE=6]**When booting on a **[/SIZE]**[SIZE=6][B]64-bit**[/SIZE][/B][SIZE=6]** Ubuntu disk:**[/SIZE]  
 [COLOR=#0000ff][SIZE=4]_- If the BIOS is setup to boot the CD in EFI mode_[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=4]_You will see the screen in purple/black with the choices to choose which OS to boot, the Ubuntu /grub2 screen not the blue from Win 8_[/SIZE][/COLOR]
 

 [COLOR=#0000ff][SIZE=4]_or If the BIOS is NOT setup to boot the CD in EFI mode _[/SIZE][/COLOR] 
 [COLOR=#0000ff][SIZE=4]_you will see just the purple/black  screen from Ubuntu but no choices for OS's just the keyboard Access logos at the bottom of the screen_.[/SIZE][/COLOR]
 

 ** Setup the BIOS in EFI [SIZE=3]= [/SIZE][SIZE=3]Remember these writing that almost all I've copy and pasted are my attempts to fully understand how to dual boot a preloaded Win 8 with Ubuntu 12.10 64bit and your case can be different if you install Win 8 yourself.[/SIZE]**

 

 

 this setting is located in the "Boot order" tab of the BIOS of  my and maybe your computer
 

 

 

 Some other firmwares (BIOS) propose an "UEFI/Legacy Boot:" option with the following choices: [Legacy only], [UEFI only] or/and [Both]. This last one boots in EFI mode when possible, then in Legacy mode if no EFI files are detected. 
 

 

 

 

 **Once Ubuntu is install to find out if you installed Ubuntu in the right place/EFI ** 
 An Ubuntu installed in EFI mode can be detected the following way:  
 
[LIST]
[*]its 	/etc/fstab file contains an EFI partition (mount point: /boot/efi)  	
[*]it uses the 	grub-efi bootloader (not grub-pc)  	
[*]from the 	installed Ubuntu, open a terminal (Ctrl+Alt+T) then type the 	following command:  	
 	[ -d /sys/firmware/efi ] && echo "Installed in EFI 	mode" || echo "Installed in Legacy mode"  	
[/LIST]
 


 


 **Converting Ubuntu into EFI mode**

 
[LIST]
[*] 	Start [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), 	click on "Advanced options", go to the "GRUB 	location" tab.  	
[*]If you do 	not see a "Separate /boot/efi partition" line, this means 	that your PC does not have any EFI partition. In this case, exit 	Boot-Repair, then create an EFI partition (see the "Creating an 	EFI partition" paragraph above).  	
[*]If you see 	a "Separate /boot/efi partition" line, tick it then click 	the "Apply" button.  	
[*]Setup your BIOS so that it boots the HDD in EFI mode (see the 	""[Setup 	the BIOS in EFI or Legacy mode]("https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode")"  Remember your Ubuntu must 	be in the same partition that your Win 8 is = if win 8 is in legacy 	your Ubuntu must be in legacy or old stuff as I' like to call it, 	however if  win 8 preloaded not installed by you is in new efi then 	you must install Ubuntu 12,10 the latest  in efi also), I will not 	be held responsible for damages to your preloaded win 8 and backup 	of your files are necessary always, you have been giving advice as 	to how to protect yourself against the lost of your system
[*]If you do end up lost remember that you can do a restore to 	factory state, assuming you didn't erase your healthy restore 	partitions, remember new win 8 with GPT can have many partitions.  	
[/LIST]
 Also trying all this is better and safer if you have another computer to access the Ubuntu forums just in case.
 

 So the solution to any big problem will be rebooting Win 8 so you can get back to the reset to factory area of course if your win 8 isn't booting then don't get bent out of shape and start deleting stuff, Don't delete anything not Ubuntu (nothing), let the restore from factory take care of that, just work on getting your win 8 to boot.
 

 

 [SIZE=6]**Just in case: **[SIZE=5]see below for when Ubuntu is install and booting fine, just maybe not your Win 8 factory preloaded, knowing what to do via Ubuntu to find out stuff so the foru[/SIZE][SIZE=5]m[/SIZE][SIZE=5]s can help you and also remember I'm not a member of the moderators group, I' practically have no knowledge, so take my advice lightly, [/SIZE][SIZE=5]yea, yea, yea we get it...[/SIZE][/SIZE]
 **Converting Ubuntu into Legacy mode [COLOR=#ff0000](not sure why I' would want to do this). [/COLOR][COLOR=#0000ff]But maybe it's a must in some cases.[/COLOR]**

 
[LIST]
[*] 	If Ubuntu is installed on a GPT disk (you can check it via the 'sudo 	parted -l' command), use [Gparted]("https://help.ubuntu.com/community/Gparted") 	to create a BIOS-Boot partition (1MB, unformatted file system, 	bios_grub flag) at the start of its disk.  	
[*]Start [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), 	click on "Advanced options", go to the "GRUB 	location" tab.  	
[*]Untick the 	"Separate /boot/efi partition" option  	
[*]Click the 	"Apply" button.  	
[*]Setup your BIOS so that it boots the HDD in Legacy mode (see 	the ""[Setup 	the BIOS in EFI or Legacy mode]("https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode")" paragraph above).  	
[/LIST]
 


 


 

 **SecureBoot**

  "[Secure Boot]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot")" is a new UEFI feature that appeared in 2012, with Windows8 preinstalled computers. The support for this feature has started with Ubuntu **12.10 64bit** (see [this article]("http://web.dodds.net/%7Evorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")), but it is not fully reliable yet, so you may need to disable it in order to be able to boot Ubuntu.  
 

 

 OK so secureboot and quickboot are not the same I' wonder which one is restricted boot, must be the secureboot or non of the above, still learning...
 

 

 

 

 

 **[SIZE=5]I'm not a member of the moderators group, I' practically have no knowledge, so take my advice lightly.[/SIZE]**
 

 

 

 

 **Re: [Boot-Repair] Graphical tool to repair the PC boot in 1 click!**  
 

  **Boot-Repair** is a simple tool to repair frequent boot issues you may encounter in Ubuntu like when you can't boot Ubuntu after installing Windows or another Linux distribution, or when you can't boot Windows after installing Ubuntu, or when GRUB is not displayed anymore, some upgrade breaks GRUB, etc.  
 Boot-Repair lets you fix these issues with a simple click, which (generally reinstall GRUB and) restores access to the operating systems you had installed before the issue.  
  


 **@all:**
**quick explanations about how to use Boot-Repair on UEFI systems:**


**First of all, try the "Recommended Repair" button.**
- B-R will automatically detect if grub-pc or grub-efi (or grub Legacy) is needed
- if grub-efi is needed, it will automatically detect if a signed boot is needed or not (SecureBoot)
- by default, the "Backup and rename EFI files" option is ticked. As explained [here]("http://ubuntuforums.org/showpost.php?p=12379441&postcount=637"), this option duplicates grubx64.efi in 2 places: /EFI/Microsoft/Boot/bootmgfw.efi and /EFI/Boot/bootx64.efi . This allos to be sure that the BIOS will boot into GRUB at next reboot, even if the BIOS doesn't allow to boot on /efi/ubuntu/grubx64.efi , and by commodity this avoids the user to modify the BIOS. Of course, if these files already existed, B-R renames them first (by adding them a .bkp extension).

After the Recommended Repair, the user reboots its PC, and sees the GRUB menu with access to Ubuntu, and generally 2 additional entries:
- Windows UEFI (/EFI/Microsoft/Boot/bootmgfw.efi.bkp)
- Windows Boot UEFI ( /EFI/Boot/bootx64.efi.bkp)

Generally, these 2 entries boot Windows without any problem. 

But on some systems, they don't boot Windows. Example: [http://forum.ubuntu-fr.org/viewtopic...9311#p11879311]("http://forum.ubuntu-fr.org/viewtopic.php?pid=11879311#p11879311") . In this case, here is what to do:
**1) **if your PC has/had Windows8 preinstalled, go into the BIOS, and , if possible, **disable the [SecureBoot]("http://doc.ubuntu-fr.org/efi#activerdesactiver_le_secure_boot") and the [QuickBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9")**. Then redo the Recommended Repair of Boot-Repair. This often works (example: [http://ubuntuforums.org/showpost.php...&postcount=686]("http://ubuntuforums.org/showpost.php?p=12403320&postcount=686") ).
If still none of the 2 Windows entries work, continue next steps.

**2) **restorer the bkp via Boot-Repair --> Advanced options --> untick "Backup and rename EFI files" --> **tick "Restore EFI backups"** --> Apply . This will restore the 2 bkp files to their original place (/EFI/Microsoft/Boot/bootmgfw.efi et /EFI/Boot/bootx64.efi ) , and this will update the 2 Windows entries in GRUB:
- Windows UEFI (/EFI/Microsoft/Boot/bootmgfw.efi)
- Windows Boot UEFI ( /EFI/Boot/bootx64.efi)

**3)** then reboot the PC. If the BIOS hadn't been changed (it is setup to boot on /EFI/Microsoft/Boot/bootmgfw.efi or /EFI/Boot/bootx64.efi ), this will directly boot Windows.

**4)** then setup the BIOS so that it boots on the Ubuntu entry (/efi/ubuntu/grubx64.efi) . This will make the GRUB menu appear, with access to Ubuntu and the 2 Windows entries:
- Windows UEFI (/EFI/Microsoft/Boot/bootmgfw.efi)
- Windows Boot UEFI ( /EFI/Boot/bootx64.efi)

**5)** If you can't boot Windows via these GRUB entries, but that you can boot Windows directly via the Windows entry of the BIOS, then it is probably a security of Windows that doesn't like to be booted via GRUB  :sad: , in this case I can't do anything, and you need to setup your BIOS each time you want to boot another OS.

---

### Post by oldfred on 2012-12-19
I think you pretty well have it. How you boot hard drive does not have to be way to boot install DVD or flash drive and that can then lead to issues.

If you use manual install you have to specify partitions. The auto install options all only create / (root) & swap. In BIOS those are the only partitions you see, but with UEFI it will create a efi partition for boot files, or if only Ubuntu on gpt drive it will create a bios_grub partition (old versions did not do either, it was all manual). 

If using manual install you need to create partitions your self just like you would with BIOS install. It depends on how you want to use computer. If just starting out you can use smaller allocations and just / & /home. Then if allocating more space a speparate /home may make sense. But if dual booting then a shared NTFS data partition may make sense as Windows does not like too much writing into its system and with Windows 8 always hibernating that will automatically create issues.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Somewhat Newbie on 2012-12-19
I' manage to see and play with Ubuntu 12.10 64 BIT remix = notice it's the remix!
 Why the remix? When regular 12.10 64 bit also should work fine!
 

 Well, cuz it has boot repair already on the live CD/DVD, did not want a separate USB with boot repair yet.
 

 As I' was saying I' booted Ubuntu 64 with a USB on a TOUCH screen laptop with restricted boot.
 

 First things first: I' don't like the current Ubuntu on touch devices, will explain later on these writing's.
 

 Will try Bod-hi next, but I think Bod-hi does not have UEFI support yet, they only have a version for the ARM processor and that is good for everybody, looks like people are working for the RT version of Windows 8 already very good, very good indeed
 

 On my laptop it's new.  
 

 In the bios screen after pressing delete to access it during the boot process.
 

 1) On the “MAIN” I' did nothing.
 

 2) On the “ADVANCE” under USB configuration I' did nothing and was default Legacy USB support [enabled]
 

 XHCT Pre-Boot mode was default at [auto], this has to do with USB 3.0 pen drives.
 

 3) I' jump to “SECURITY” and on Secure Boot Control, I' change it from [enabled] to [disabled],
 

 then........
 

 

 

 

 4) I' went to “BOOT” and under Boot Configuration I' change [enabled] to [disabled] the fast boot.
 

 

 

 5) On Boot Options Priorities
 

 A) Boot option #1  [windows boot ------] becomes #2
 

 B) Boot option #2  [UEFI: USB Drive] becomes #1, notice the uefi/ EFI/GPT and the reversal of the numbers.
 

 BOOT OPTION #1 IS NOW THE UEFI USB PENDRIVE, THE ONE THAT WILL BOOT FIRST.
 

 If you remove the usb pen drive the system will set itself back to windows boot first and if you look at the bios then you will see only one boot option set as #1 and it will be the win 8.
 

 if you re-install the same usb with Ubuntu inside and even if you plug it in the same usb out port the system will still be set to boot option #1 win8, there must be a simple way of fixing this I' just have not done it yet myself.
 

 

 I' did not set the HDD with win 8 to disabled, just place it in second sequence.
 

 OK now by doing these steps in my computer, yours might be a bit different, but should very similar.
 

 I' was on the desktop of Ubuntu in live and I' was able to test current Ubuntu 64 on a touch screen, the experience was not that good, Unity worked great (should have more options when you use touch; What it does is normal, I' want more things available when I' use touch devices.
 

 Everything else in Ubuntu is sort of wasted under touch, can't moves pages up or down with your finger because the space provided is not wide enough for touch.
 

 Dash work's better but again, once you access it then you really can't move things to your desktop like you would in Android.  
 

 I fail to see why Ubuntu for android if it's the same as this one, would be a good thing, yes sure your phone becomes a Tower to hook up a keyboard to your phone?
 

 I' know I'm missing some info regarding Ubuntu for devices, I' must be....
 

 Ubuntu needs more then one OS, it does not need KDE, it needs Desktop with two choices Unity or Mate and Ubuntu Touch a very different OS set-up. With a look and function like a mix of Android, Modern (Metro) and Joly and in all of them include some version of Unity, LOL but make it so people can hide it if they want to. Make Ubuntu touch or better said make Ubuntu touch a very custom friendly    OS, being able to change colors and such. You know some men like gray like in Mint but some Woman want pink like my sister, she hates Mint only because it's gray by and when you make it pink its not natural enough for her, well.....
 

 I’ve decided (maybe) not install Ubuntu and just use it on the USB in this laptop, my other laptops have Ubuntu and other Linux inside, so I' still have Linux, just not touch. Can't wait to see the future touch friendly distros from all who love Linux.
 

 If anybody wants any info I do come by this solved post once in a while, until I' can't no more for whatever reason. OK keep up the joy of freedom and thanks to all especially:
 

 OLDFRED
 BLUKANOODLE
 UBUNIK and
 JPMOLLA, thanks to all if I forgot somebody I'll try to edit later. BYE for now.

---

### Post by Somewhat Newbie on 2012-12-23
Matthew Garrett, ex-power management and mobile Linux developer at Red Hat, proudly announced last evening, November 30, that a usable release of the Secure Boot bootloader is now available for download.
 

 Dubbed shim, this software is designed for all Linux-based operating system that want to support secure boot and that do not want to get in cahoots with the greedy Microsoft Corporation.
 

 “As of 17:00 EST today, I am officially (rather than merely effectively) no longer employed by Red Hat, and this binary is being provided by me rather than them, so don't ask them questions about it."
 

 "Special thanks to everyone at Suse who came up with the MOK concept and did most of the implementation work - without them, this would have been impossible.” said Matthew Garrett in the blog announcement.
 

 Therefore, if you are a Linux distribution developer and want to include the Secure Boot bootloader in your operating system, get the shim archive from here, rename the shim.efi file to bootx64.efi and drop it in the /EFI/BOOT folder from your UEFI install media.
 

 Moreover, you will also need to put the MokManager.efi file in the /EFI/BOOT folder as well, while making sure that the name of your boot loader binary is grubx64.efi, which should also be placed in /EFI/BOOT.
 

 After that, you will need to generate a certificate and drop the public half as a binary DER file on your UEFI install media.
 

 “On boot, the end-user will be prompted with a 10-second countdown and a menu. Choose "Enroll key from disk" and then browse the filesystem to select the key and follow the enrollment prompts.”
 

 “Any bootloader signed with that key will then be trusted by shim, so you probably want to make sure that your grubx64.efi image is signed with it.” continued Matthew Garrett in the announcement.

---

