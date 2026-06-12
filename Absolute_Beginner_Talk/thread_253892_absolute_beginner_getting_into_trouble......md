---
title: "absolute beginner getting into trouble....."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by pirate2001 on 2006-09-09
ok - so i found where to add a new post. Was up 'til 3am this morning (in Australia) and am still delerious as  to what I have done. 

I've destroyed the company laptop with ubuntu. I need some urgen assistance with re configuring partitions.

at the moment i can't boot anything from th ehard drive - error 15.

can only boot from ubuntu cd

can still see my c drive partition so would love to back that up as soon as i can!!!

can someone(s) please assist.....I will be screwed otherwise. ](*,) 
:sad:

---

### Post by Fingolfin269 on 2006-09-09
Hey, at least you didn't decimate your data like I just did.  Actually, come to think of it, the only thing I destroyed was a Windows XP Home I may not be able to recover but to be honest I don't think I really care.

Good luck man!

---

### Post by deadgobby on 2006-09-09
> **pirate2001 said:**
> ok - so i found where to add a new post. Was up 'til 3am this morning (in Australia) and am still delerious as  to what I have done. 

I've destroyed the company laptop with ubuntu. I need some urgen assistance with re configuring partitions.

at the moment i can't boot anything from th ehard drive - error 15.

can only boot from ubuntu cd

can still see my c drive partition so would love to back that up as soon as i can!!!

can someone(s) please assist.....I will be screwed otherwise. ](*,) 
:sad:
 Ehh you can say to your work. Oh I droped it and does not boot any more. Or if you got kids. Kids are great scape goat, the kid got a hold of it and tries to load this program called Ubie.. HEHE just kid....
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by YeahBuntu on 2006-09-09
Search these forums for error 15 I believe there is a large post about reinstalling GRUB.

---

### Post by indigoshift on 2006-09-09
This might help:

[http://ubuntuforums.org/showthread.php?t=43591](http://ubuntuforums.org/showthread.php?t=43591)

---

### Post by pirate2001 on 2006-09-09
thank you people,

i had a look at some of that stuff last night and it quite honestly lost me. I don't understand code at all!! I am a MAC person really!!

This whole thing started after I tried adjusting the screen res - everything just froze so I shut it down. It wouldn't reboot after that as, whilst i was adjusting the screen res, in the background, updates were installing. the comp crashed halfway through that!!

My main partition seems ok - /tmp/disks-conf-sda1 FILE SYSTEM: windows NTFS

and is flagged as boot.

the other three partitions are all screwed - i know this 'cause i tried to delete them!! I reckon (if I knew what I was doing!!) I could reconfigure the partitions correctly then reinstall ubuntu and presto - problem fixed.

the other thing I thought of, was if I re installed and manually configured the partitions correctly, then all would be ok.

Before I do this I wanted to backup the c drive (whilst I'm operating ubuntu OS)

As for the kids story - could come in handy!!

thank you for your continued support!!

---

### Post by bulldog on 2006-09-09
If I understand you correctly you only would be able to get into your windows  and Ubuntu isn't that important to you?

Well put in the windows cd rom and choose recovery console and then fixmbr.
This would replace grub with the normal windows boot.

Then you could delete your Ubuntu partitions in windows and do even a reinstall of Ubuntu if you want to.

When you want to reinstall grub and get it up and running you must have a little knowledge of your partitions and where your menu.lst and your fstab lives.
You can try the following when you boot from the live cd.

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

Don't forget to alter your menu.lst AND your fstab!!!! 

Your existing Ubuntu must not be destroyed of course when you try this but it gives you a fair chance to boot again.

For altering your menu.lst and your fstab you need to mount your existing Ubuntu install from the live cd.

sudo mkdir /mnt/recovery

sudo mount /dev/hda? /mnt/recovery

Where hda? stands for your partition where you installed your Ubuntu could be something else though on your computer.
Now go to the recovery dir and see if you can acces it and alter your menu.lst and fstab to get things right again.

---

### Post by pirate2001 on 2006-09-09
well bulldog - I have read your instructions. Thank you so much for taking the effort to be so concise. I'm about to drop off ubuntu for a short while and do what you've suggested/explained. WISH ME LUCK!! I'll let you know soon enough!

thank you and kind regards

pirate2001

---

### Post by pirate2001 on 2006-09-09
woo hoo - I am now logged onto this site as a windoze user!!!

thanks bulldog - I have a toshiba tecra A7 and the self burnt DVD recovery discs ask me a few questions and then they all lead me to destroying either all my partitions or the partition that had all my data on it!! So luckily i had a Dell disc and i thought "what's the worst that can happen!!!" so I get into the recovery thing and I stumble my way through the prompts and I'm thinking - is this where I type fixmbr? If only Bulldog was here beside me.....

So I type in fixmbr and the computer starts yelling at me saying - hey bozo, are you sure you want to do that - it could destroy your partitions. But I held strong and again i thought "what's the worst that could happen?!!!".... Then i just keep getting c:/windows

enter enter enter.... so I press the "OFF" button (if all else fails, right!)

restart and presto - I live to tell another tale. 

I'm not sure if I'm going to continue my research into pornography where nobody gets hurt and it feels good, or if I'm going to learn about hard drive partitioning and ubuntu....

I think the latter will put me in better stead for the future!!

Anyway - thank you all for your advice and support - the kids are safe and won't be told off by my boss. Partitions will be repaired, Ubuntu will be installed on the Dell, and I'll probably purchase the latest and greatest iMac 24" jobby and have years of trouble free, windows free computing!!!

thanks again

---

### Post by kurian on 2006-09-09
hi,

 Iam a new kubuntu user recently i accidently deleted the system accounts like root,........ Now iam unable login to the system 

kindly give any good solution to recover from this problem.......

I do only have a kubuntu live cd with me.......

---

### Post by bulldog on 2006-09-09
If you can't login your system,I wouldn't know how to change anything.

You need to be a root user so you could make another account.

I'm sorry I can't help you.

The best way I can think off is a reinstall.
But maybe there is a guru who knows another solution.

The best way is to start a topic off your own to have the best chance someone can help you.

---

### Post by kurian on 2006-09-10
Is there any method in kubuntu to reinstall the kubuntu without lossing the existing data and downloaded packages from kubuntu partition????

---

### Post by bulldog on 2006-09-11
When you do a reinstall choose to partition manually.

So you can mount your /home withouth formatting and keep all your stuff.
That's the only way I can think of.

---

