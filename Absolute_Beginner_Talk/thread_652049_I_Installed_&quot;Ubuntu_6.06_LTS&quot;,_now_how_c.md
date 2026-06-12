---
title: "I Installed &quot;Ubuntu 6.06 LTS&quot;, now how can i Install &quot;Ubuntu 7.10&quot;"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Alsubiheen on 2007-12-28
Hello and welcome to my thread,

Unfortunately i have downloaded and installed the old version of Ubuntu by mistake.

And now i have downloaded the newer version which is 7.10

My questions is, how can i Install it :(

Because after i have burned the ISO file of the 7.10 on a CD,and re-booted the PC. it shows me the screen but when i click on Install Ubuntu.

it gives me some kind of error and tells me to type help to get more info.

ofcourse i do not need to tell you that i did not understood anything after i typed help.

anyone can help please, because the old version of Ubuntu has no Graphical Effects at all :(

Many thanks and appreciation in advance :)

Kind regards,
Bassim

---

### Post by toddward on 2007-12-28
Alsubiheen,

What version of Ubuntu did you install?  Was it 7.04?

If it was, [here]("http://www.ubuntu.com/getubuntu/upgrading") is a guide that describes how to upgrade from 7.04 to 7.10.

Also, if it isn't, I provided the link to Google which lists a whole bunch of guides for how to upgrade.

[http://www.google.com/search?hl=en&q=upgrading+ubuntu&btnG=Google+Search]("http://www.google.com/search?hl=en&q=upgrading+ubuntu&btnG=Google+Search")

---

### Post by kwacka on 2007-12-28
Could you let us know which version you have installed?

Possibly the easiest way is to let us know the name of the file that you downloaded, e.g. ubuntu-7.10-server-i386.iso  or ubuntu-6.06.1-desktop-i386.iso

As you don't have a graphical desktop it is possible that you have the 'server' version, if it is server 7.10 (and **_only_** this version) type:
 
sudo apt-cdrom add

and follow the instructions to add the new, 'desktop' cd. The type:

sudo apt-get install ubuntu-desktop

---

### Post by Alsubiheen on 2007-12-28
> **toddward said:**
> Alsubiheen,

What version of Ubuntu did you install?  Was it 7.04?

If it was, [here]("http://www.ubuntu.com/getubuntu/upgrading") is a guide that describes how to upgrade from 7.04 to 7.10.

Also, if it isn't, I provided the link to Google which lists a whole bunch of guides for how to upgrade.

[http://www.google.com/search?hl=en&q=upgrading+ubuntu&btnG=Google+Search]("http://www.google.com/search?hl=en&q=upgrading+ubuntu&btnG=Google+Search")

Hey there and thanks for replying :)

no unfortunately i downloaded and installed "[Ubuntu 6.06 LTS - Supported to 2009]("http://www.ubuntu.com/getubuntu/download")" 

and now iam trying to install "[Ubuntu 7.10 - Supported to 2009]("http://www.ubuntu.com/getubuntu/download")"

Can anyone help please :)

Many thanks and appreciation in advance :)

Kind regards,
Bassim.

---

### Post by kwacka on 2007-12-28
Ignore my previous post.

You cannot upgrade from 6.06 to 7.10, so you need to get rid of 6.06.

What are the messages you get after typing help?

---

### Post by toddward on 2007-12-28
I found a guide that may help.  In the comments someone said they went from 6.04 to 7.10 with this procedure.

[http://ubuntu-tutorials.com/2007/10/20/how-to-upgrade-ubuntu-704-to-ubuntu-710-on-ubuntu-server/]("http://ubuntu-tutorials.com/2007/10/20/how-to-upgrade-ubuntu-704-to-ubuntu-710-on-ubuntu-server/")

Still looking around for you though :-D.

Edit: this only works for server.

---

### Post by meindian523 on 2007-12-28
I don't think anyone would want to eat "messages",for there are other edible things in the world.... ;)...Please don't take it as an insult,just to cheer up the mood of the OP and the discussion around here

also,for the OP,if you have a separate /home partition,you can just install over the 6.06 you have installed by allowing it to format the / partition you created for 6.06

---

### Post by kwacka on 2007-12-28
Tutorial is for 7.04 to 7.10.  :(

Only way is to upgrade from 6.04 to 7.01 to 7.04 to 7.10 (or numbers might not be accurate, but you get the idea).

---

### Post by toddward on 2007-12-28
> **kwacka said:**
> Ignore my previous post.

You cannot upgrade from 6.06 to 7.10, so you need to get rid of 6.06.

What are the messages you get after typing help?

Unfortunately he's right.  Your best bet is to just start to download 7.10.

---

### Post by kwacka on 2007-12-28
Possibly best to just start all over.

Boot from 7.10 disk.

Go to 'Systems  -->  Administration --> Partition Editor (Gparted) and delete the ext3 & swap partitions. (If you are dual booting make sure you don't delete FAT32 or NTFS partitions). Click apply and the previous installation is gone.

Re-start and boot from CD again, click install and you should be OK.

NB you are deleting partitions on your harddrive - to be safe make sure you have done your weekly/daily backup first.

---

### Post by jken146 on 2007-12-28
> **Alsubiheen said:**
> Hello and welcome to my thread,

Unfortunately i have downloaded and installed the old version of Ubuntu by mistake.

And now i have downloaded the newer version which is 7.10

My questions is, how can i Install it :(

Because after i have burned the ISO file of the 7.10 on a CD,and re-booted the PC. it shows me the screen but when i click on Install Ubuntu.

it gives me some kind of error and tells me to type help to get more info.

ofcourse i do not need to tell you that i did not understood anything after i typed help.

anyone can help please, because the old version of Ubuntu has no Graphical Effects at all :(

Many thanks and appreciation in advance :)

Kind regards,
Bassim

Did you manage to start the live CD and get to the desktop?  If you did, please could you explain your problem with the installer a little more?

If not, there are a few things you can check.  First there is the md5sum of the iso you downloaded.  If this does not match you should download the iso again.  If the download was OK, you may have got a bad burn.  Try burning another CD at 4x speed or less.  Also try starting the CD in low graphics mode.
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso) may help you.

---

### Post by meindian523 on 2007-12-28
and then overwrite your 6.06 with it....because Ubuntu usually recommends a clean-install even when you are upgrading from one version to the immediate next(eg:7.04 to 7.10) since the apt-get dist-upgrade function is till not completely bug-free...

---

### Post by Alsubiheen on 2007-12-28
Ok first of all thanks for all your posts, i realy do appreciate them alot.

and regarding the issue iam facing. you should know that i have the Old 6.somthing installed of Ubuntu on.

now after downloading 7.10 and burning it on a CD as ISO. and then booting the PC ... i get the following.

the menu starts normally. so i click on Install Ubuntu ... then some loading happens then the issue pops :( ... it shows.

===========================================

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Build-in shell ( ash )
Enter 'help' for a list of built-in commands

(initramfs)

===========================================

after typing help a whole bunch of commands pop ofcourse ...

proplem is from the day god created the earth i was using Windows and DOS lol so i have not even 1% knowledge of whats going on.

so please in red caps letters i need some help :)


Many thanks and appreciation in advance :)

Kind regards,
Bassim.

---

### Post by Alsubiheen on 2007-12-28
Thanks checking my thread :)

ok to make it simple and clear, i have Downloaded and Installed "Ubuntu 6.06 LTS - Supported to 2009"

Now i Downloaded "Ubuntu 7.10 - Supported to 2009" and i want to install it. so i can get the Full Graphic Effects :)

however iam facing an issue :(

After downloading 7.10 and burning it on a CD as ISO. and then booting the PC ... i get the following.

the menu starts normally but ofcourse a MUCH BETTER looking logo than 6.06. so i click on Install Ubuntu ... then some loading happens then the issue pops  ... it shows.

===========================================

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Build-in shell ( ash )
Enter 'help' for a list of built-in commands

(initramfs)

===========================================

after typing help a whole bunch of commands pop ofcourse ...

proplem is from the day god created the earth i was using Windows and DOS lol so i have not even 1% knowledge of whats going on.

so please pretty please with a cherry on top i need some help :)

And kindly explain it like if you were explaining it to a 5 year old girl lol so it can be clear, you Ladies & Gents and pros and iam just a noob :)

Many thanks and appreciation in advance 

Kind regards,
Bassim.

---

### Post by Sef on 2007-12-28
Merged threads due to double posting.

---

### Post by jken146 on 2007-12-28
Well, it could be that your CD burned badly.  Did you check the md5sum of the download?  Did you do the CD integrity check?

---

### Post by Alsubiheen on 2007-12-28
> **jken146 said:**
> Well, it could be that your CD burned badly.  Did you check the md5sum of the download?  Did you do the CD integrity check?

Give me one min, ill boot and check on both the Integrity & the low Graphics option too :)

ill be back "Not in a Schortzinager voice" lol :P

Kind regards,
Bassim.

---

### Post by overdrank on 2007-12-28
> **Alsubiheen said:**
> Give me one min, ill boot and check on both the Integrity & the low Graphics option too :)

ill be back "Not in a Schortzinager voice" lol :P

Kind regards,
Bassim.

And if the checksum returns good then you can
 when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the -- then press enter. When you receive the error again type modprobe piix then hit enter and then type exit then hit enter again this should continue the livecd to boot.

---

### Post by Alsubiheen on 2007-12-28
> **overdrank said:**
> And if the checksum returns good then you can
 when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the -- then press enter. When you receive the error again type modprobe piix then hit enter and then type exit then hit enter again this should continue the livecd to boot.

Ok iam back :)

both gave the same error message :(

but btw just to check on the CD, iam trying ti right now on my Laptop. and it went through to the Log in page ... true that it is asking me for a User Name and Password lol !?!? allthought it is the first time iam trying it on my Laptop ..

any idea whats that all about ?

and regarding the Desktop.

Could you kindly please. explain what you said again please but in an easier non programing way >.< 

after i get the option menu for Ubuntu ill {{ Press F6 }} and edit some kind of Krenel !? line and remove the Quiet splash ... which i have no idea what is that to be honest lol  add break=top before the -- then press Enter and when i get the same error i should type { modprobe piix } then type { Exit } ?

Ok ill try that lol ... if i dont come back then my pc is dead and iam formating lol

Thanks for the post and the reply :)

Much appreciated,

Kind regards,
Bassim.

---

### Post by Alsubiheen on 2007-12-28
Ok iam back on the laptop ofcourse lol

after i removed the quite splash and added break=top then ENTER

it went and did alot of lines and all, then it gave me the same error messgae, only this time it "Froze" i couldnt type anything or do anything .. not even type help .. it was like the Keyboard froze :(

i did this like 5 times so iam sure.

any hints ? or anything i can do ?

Many thanks for your time sir i really do appreciate it :)

Kind regards,
Bassim.

---

### Post by overdrank on 2007-12-28
> **Alsubiheen said:**
> Ok iam back on the laptop ofcourse lol

after i removed the quite splash and added break=top then ENTER

it went and did alot of lines and all, then it gave me the same error messgae, only this time it "Froze" i couldnt type anything or do anything .. not even type help .. it was like the Keyboard froze :(

i did this like 5 times so iam sure.

any hints ? or anything i can do ?

Many thanks for your time sir i really do appreciate it :)

Kind regards,
Bassim.

Ok did you check the cd for errors and md5sum as asked previously? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Alsubiheen on 2007-12-28
> **overdrank said:**
> Ok did you check the cd for errors and md5sum as asked previously? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Ok I checked the CD on my laptop. when the option screen pops. i selected "Check CD Integrity"

{ Check Finished: errors found in 1 files }

Iam so embaressed >.< ill download it again and see what happens :)

Thank you SO MUCH Gents for your time and help, i really do Appreciate it alot :)

Kind regards,
Bassim.

---

### Post by overdrank on 2007-12-28
> **Alsubiheen said:**
> Ok I checked the CD on my laptop. when the option screen pops. i selected "Check CD Integrity"

{ Check Finished: errors found in 1 files }

Iam so embaressed >.< ill download it again and see what happens :)

Thank you SO MUCH Gents for your time and help, i really do Appreciate it alot :)

Kind regards,
Bassim.

No problem, please post back if any issue arise. Good luck! :)

---

### Post by meindian523 on 2007-12-28
and this time burn it at 4x or next slowest speed possible,higher speeds have corrupted a great many CDs

---

### Post by Alsubiheen on 2007-12-28
Ok iam back hehe

I downloaded the file "Again" lol

and here is the Status when i tried to install it on both my Laptop and my Desktop ...

============================================
** Desktop ** PC Has Windows XP & Ubuntu 6.60 **

When i tried to install the CD it gave me the same Error message :(


** Laptop ** PC Has Windows XP

When i tried to install the CD it went through normally and went into the Desktop of Ubuntu.

However when i tried to do the Integrity Check on the CD. it gave me the same issue. as in { Check Finished: errors found in 1 files }.
============================================

So i don't really need to tell you how confuzed iam right now lol 

whats going on ? why isnt it installing 7.10 on 6.60 ? why is it installing normaly on my laptop ? if its installing correctly then why is it still showing 1 Error file ?

iam so confuzed lol, any ideas guys ? hints ? or should i just forget about it and embrace Windows XP haha

Kind regards,
Bassim.

---

### Post by overdrank on 2007-12-28
> **Alsubiheen said:**
> Ok iam back hehe

I downloaded the file "Again" lol

and here is the Status when i tried to install it on both my Laptop and my Desktop ...

============================================
** Desktop ** PC Has Windows XP & Ubuntu 6.60 **

When i tried to install the CD it gave me the same Error message :(


** Laptop ** PC Has Windows XP

When i tried to install the CD it went through normally and went into the Desktop of Ubuntu.

However when i tried to do the Integrity Check on the CD. it gave me the same issue. as in { Check Finished: errors found in 1 files }.
============================================

So i don't really need to tell you how confuzed iam right now lol 

whats going on ? why isnt it installing 7.10 on 6.60 ? why is it installing normaly on my laptop ? if its installing correctly then why is it still showing 1 Error file ?

iam so confuzed lol, any ideas guys ? hints ? or should i just forget about it and embrace Windows XP haha

Kind regards,
Bassim.

Ok I have read through the thread again and see no system specs. So let pick one system and go from there. If you are still getting errors when checking the cd and the checksum is right then you may try to burn the cd slower and with a different system and program. So lets just pick one system specs and go from there. :KS

---

### Post by Alsubiheen on 2007-12-28
> **overdrank said:**
> Ok I have read through the thread again and see no system specs. So let pick one system and go from there. If you are still getting errors when checking the cd and the checksum is right then you may try to burn the cd slower and with a different system and program. So lets just pick one system specs and go from there. :KS

Hey there :)

i tried installing the CD on both my Desktop and my Laptop and with the "Slowest" speed available lol and still its the same.

Isn't there any way to actually "Un-Install" Ubuntu ? or delete it ? because i couldnt find it even when i loged to XP ... so i can Delete it and then install it again.

Because logically its installing correctly till now on my laptop, because my laptop has only XP on it ... but my Desktop has Ubuntu 6.60 thus its not allowing it to continue .. ofcourse iam not sure iam just a assuming lol iam not a pro like you Gents :)


PS. if any one wants some damaged CD's for decorations please let me know haha


Kind regards,
Bassim.

---

### Post by Alsubiheen on 2007-12-28
I mean for Windows XP, i simply put the CD in and boot from it and i can Format and Un-Install windows XP

WHat about Ubuntu 6.60 ? how can i Uninstall it from my PC ? or even delete it or Format the area where its installed ?

so i can Install Ubuntu 7.10 as a freash copy and not face any errors :)

Any idea please ?


Kind regards,
Bassim.

---

### Post by overdrank on 2007-12-28
> **Alsubiheen said:**
> I mean for Windows XP, i simply put the CD in and boot from it and i can Format and Un-Install windows XP

WHat about Ubuntu 6.60 ? how can i Uninstall it from my PC ? or even delete it or Format the area where its installed ?

so i can Install Ubuntu 7.10 as a freash copy and not face any errors :)

Any idea please ?


Kind regards,
Bassim.

Hi and if you would like to uninstall Ubuntu and keep windows I would look at this link
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Good luck!

---

### Post by Alsubiheen on 2007-12-29
> **overdrank said:**
> Hi and if you would like to uninstall Ubuntu and keep windows I would look at this link
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Good luck!


Ok i red that link and may i say WoW !! its not as easy as i thought lol mainly because i couldnt understand what he said lol

i remember uninstalling Windows wasn't that hard ! .. simply pop in windows CD and re-boot ... and then Uninstall and Install the freash copy and your done :)

with Ubuntu, i saw some words that were totaly new to me >.<

any how iam downloading Ubuntu 7.10 again and twice too ! from UK & Singapore lol one of them should be a good file "Crossing Fingers" :)

and will update if everything goes as planed.

regarding the Uninstall of Ubuntu. is that the only way to uninstall Ubuntu ? because its not that simple.

how about if i pop Windows CD and delete the whole drive, and then create a new section and start from scratch, as in install Windows XP and then install Ubuntu :) ?

I would like to thank you Gents and specially **overdrank** for your time and help, i really do appreciate it :)

Kind regards,
Bassiml.

---

### Post by meindian523 on 2007-12-29
The way to uninstall Ubuntu is to delete it's partitions or format them,so you might do this:

Right click My Computer,Disk Management

You can format/delete at your option the partitions which Windows cannot recognize,ie the ones without drive letters and whose filesystem fields are blank,those would be your Ubuntu partitions provided you haven't installed any other OS on your box.

Then reboot from your Windows XP CD and go to the recovery console and type ```
fixmbr
``` and you are done...Ubuntu has been removed from your system.

After that,you can use the md5 sum of the ISO on the server and verify whether it downloaded correctly and THEN reboot with it and install the 7.10 to the free hard disk space(if you deleted the Ubuntu partitions) or just use the formatted partitions(if you formatted the Ubuntu partitions) and install 7.10 to them...

---

### Post by Alsubiheen on 2007-12-29
> **meindian523 said:**
> The way to uninstall Ubuntu is to delete it's partitions or format them,so you might do this:

Right click My Computer,Disk Management

You can format/delete at your option the partitions which Windows cannot recognize,ie the ones without drive letters and whose filesystem fields are blank,those would be your Ubuntu partitions provided you haven't installed any other OS on your box.

Then reboot from your Windows XP CD and go to the recovery console and type ```
fixmbr
``` and you are done...Ubuntu has been removed from your system.

After that,you can use the md5 sum of the ISO on the server and verify whether it downloaded correctly and THEN reboot with it and install the 7.10 to the free hard disk space(if you deleted the Ubuntu partitions) or just use the formatted partitions(if you formatted the Ubuntu partitions) and install 7.10 to them...

Ahhh ill try that once iam back from work :)

Many thanks ** meindian523 ** :)


Kind regards,
Bassim.

---

### Post by Alsubiheen on 2007-12-29
Ok iam at home, and i think i just nuked my pc lol

Windows is dead, and now when i put in the Windows XP CD and try to install, i can't because there are some other partetions that it can't understand. which is the Ubuntu Partetion ...

on the other hand, i FILANLY got a good CD with correct information :)

so now when iam booting from the WIndows XP cd. how can i DELETE the Partetion of Ubuntu ? any line i should type or do ? 

or even can i do it from Ubuntu ?

please with a cherry on top help me :)


Kind regards,
Bassim

---

### Post by meindian523 on 2007-12-29
So basically,we need some answers:

1]Is there some data in Ubuntu which you want to save?
2]Do you want to start with a blank slate and install XP+Ubuntu 7.10 as a dual boot?

---

### Post by Alsubiheen on 2007-12-29
> **meindian523 said:**
> So basically,we need some answers:

1]Is there some data in Ubuntu which you want to save?
2]Do you want to start with a blank slate and install XP+Ubuntu 7.10 as a dual boot?

Nope the Ubuntu installed is 6.60 so i want it deleted lol

and i want to format C Compleatly then Install Windows XP as a Primary OS

and then install Ubuntu 7.10 as an additional OS :)

please tell me what to do :)


Kind regards,
Bassim

---

### Post by meindian523 on 2007-12-29
Ok,then what you have to do is to delete all your partitions on the HDD,to get a clean HDD

Warning:This will destroy completely and forever any data you have on the HDD.
So,boot with the Ubuntu CD,go to System>>Administration>>Partition Editor.

Delete all partitions you see on the disk and commit them.Then reboot with the XP CD and follow this graphical tutorial:

[Dual boot Windows XP and Ubuntu Feisty 7.04]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

Hopefully,nothing should go wrong.

---

### Post by Alsubiheen on 2007-12-29
Iam terribly sorry sir .... but i want to thank you VERY MUCH for you help

but what you said is 100% correct .... unfortunately iam not a normal person lol

you see everything in the world is lining up to screw me lol

so now when i start the PC with the UBUNTU CD it gives me the old error when i click on Start/Install ....

and when i start the PC withought any CD's it gives me 

GRUB Loading Stage1.5.

GRUB Loading, please wait...
Error 18

lol so basically iam pretty much screwed ? lol

The only CD i can boot from and works fine is the XP CD lol ...


I understand if u ignore the thread and never post again hahaha i don't blame you sir :)

iam gonna keep looking for more solutions :) and i would REALY appreciate your help if you can :)

Kind regards,
Bassim.

---

### Post by meindian523 on 2007-12-29
Do you have Windows installed?
Then you might want to try fixing your MBR so that atleast you have one functioning OS,to do that

1]Boot into Windows XP CD
2]Go into the recovery console and type fixmbr

and then you can boot into Windows and follow the tutorial I suggested.

---

### Post by meindian523 on 2007-12-29
Bassim,I've got to wake up at 5:30 am today to get to college and it's already 1:00 am here,I regret I wouldn't be able to help further right now,I'm sure I will get back to this thread today when I'm back home.

---

### Post by Alsubiheen on 2007-12-29
> **meindian523 said:**
> Bassim,I've got to wake up at 5:30 am today to get to college and it's already 1:00 am here,I regret I wouldn't be able to help further right now,I'm sure I will get back to this thread today when I'm back home.

Oh Iam terribly sorry so so so sorry >.<

yeah yeah man go to bed, iam gonna be way too long here lol

Apparently what i said is true lol

Iam cursed to suffer lol ... apparently the Main HDD Drive was Corrupted ...... so now i lost 300GB ... and iam gonna go and buy a new Hard Disk tomorrow in order to start from sqaure Zero lol

thats why it wasnt letting me install or do anything and couldnt verify that area for me to Format it lol

but any way all is good now at least i know whats the problem :)

Many many many Thanks you :) I really appreciate it alot sir :)


Kind regards,
Bassim.

---

### Post by overdrank on 2007-12-29
> **Alsubiheen said:**
> Oh Iam terribly sorry so so so sorry >.<

yeah yeah man go to bed, iam gonna be way too long here lol

Apparently what i said is true lol

Iam cursed to suffer lol ... apparently the Main HDD Drive was Corrupted ...... so now i lost 300GB ... and iam gonna go and buy a new Hard Disk tomorrow in order to start from sqaure Zero lol

thats why it wasnt letting me install or do anything and couldnt verify that area for me to Format it lol

but any way all is good now at least i know whats the problem :)

Many many many Thanks you :) I really appreciate it alot sir :)


Kind regards,
Bassim.

Hi and the drive may not be faulty, the live cd should boot on a system without a hard drive and it will just not install for obvious reasons.

---

### Post by Alsubiheen on 2007-12-29
> **overdrank said:**
> Hi and the drive may not be faulty, the live cd should boot on a system without a hard drive and it will just not install for obvious reasons.


Hi there :)

Well, the issue is that even if it still boots i still cant install it lol ... because Ubuntu 6.60 is installed and it refuses to install 7.10

and i can't delete or format the partetion for Ubuntu lol and after i tried it several times .... i ended up wirth a dead PC

so bye bye my Animation movies bye bye my Programs bye bye my games bye bye World of Warcraft and all those updates ive done lol damn iam gonna cry hahaha :P

now when i restart my PC and click DELETE to check on the IDE, i find Primary as "NOT DETECTED" .... this is when i pulled out a ciggaret and lit it and smiled ..... hahah


Oh well, tomorrow iam gonna go and buy a new Hard Disk, iam thinking maybe a 500GB one, and Start All over from Square one :)


Thanks for the Reply and time and intrest in this Radiated Post of Nuklear explosions lol


Much appreciated :)

Kind regards,
Bassim.

---

### Post by meindian523 on 2007-12-30
I think you should download the GParted live CD,burn it and use it to delete your partitions and I didn't get it,how can the BIOS refuse to detect the HDD?

GParted live CD:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Alsubiheen on 2007-12-30
> **meindian523 said:**
> I think you should download the GParted live CD,burn it and use it to delete your partitions and I didn't get it,how can the BIOS refuse to detect the HDD?

GParted live CD:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Oh hey there :)

lol well i have no idea why isnt the Bios not detecting the Main HDD lol .. but now it doesnt matter actually lol

i just bought a New Hard Disk 320GB, and iam now on my Desk Top live from Ubuntu, downloading Updates as i type :)

i really didn't care much after my PC got nuked haha ... i lost 900GB of Very important data lol so it doesn't matter any more :)

I really do appreciate it alot that you care and still posted in my thread :) 

Many thanks man :)


Kind regards,
Bassim.

---

### Post by meindian523 on 2007-12-30
Um,so you installed Ubuntu on your new 320 GB and everything is fine now?

---

