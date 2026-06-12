---
title: "fsck"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2007-07-13
My computer is misbehaving. after a forced check tihing which i was told is normal for ubuntu. Now the PC said there error with the fsck or something to that effect. It says the fsck must be done manually. this is the second time this happens. the first time I reinstalled the OS and it worked fine untill the forced check which requires me to do the manual fsck thing. I know nothing about programming and I dont mind reinstalling ubuntu i have everything on disc but this will keep happening and i dont like it. sorry for any ambiguity. I can provide any system infomation if anyone can help. 

I think it is a back up i did with Nero when i was still using windows xp. 

Thank you for your valuable time. 
:mad:

---

### Post by twiceasworn on 2007-07-13
Could you do me a favor a post not only your system specs but also the contents of your /var/log/messages?  You can do this by entering 

```
sudo gedit /var/log/messages
```

Then just copy and paste what is in there.  Also, this forced check you are speaking of, what exactly is that?  I don't remember ever having my system do that.

---

### Post by lunamystry on 2007-07-13
> **twiceasworn said:**
> Could you do me a favor a post not only your system specs but also the contents of your /var/log/messages?  You can do this by entering 

```
sudo gedit /var/log/messages
```

Then just copy and paste what is in there.  Also, this forced check you are speaking of, what exactly is that?  I don't remember ever having my system do that.

okay the forced check happens after a certain number of re-starts it think. 27 on my pc. em... my system specs, let me see. 

its an intel Pentium 4, with a 80 gig hard drive 512 ram and uhm... I dont really know passed that, like i said  this is my furst pc and i only knew the minimum things that it should have are those so thats what i got. I cant do the sytem log thing because i am using a friend's PC, mine is on the black and white screen.  like terminal. 

this is what is wrote:
fsck 1.40-wip(14 NOV 2006)
/dev/sda1/contains file system with errors system check forced

/dev/sda1:UNEXPECTED INCONSISTENCY; RUN fsck manually (ie without -a or -p option)
fsck died with exit status 4

if there is more you need i can check. i'll tryto check it.

---

### Post by twiceasworn on 2007-07-13
Could you post the logs from /var/log/messages?

---

### Post by Atomic Dog on 2007-07-13
you can go into a shell (terminal) and type:
```
sudo shutdown now -F
```
Not sure if you need to use sudo, but it won't hurt.

This will force a disc check on startup.  It may give you some instructions upon restart, and prompt you to accept repairs (it has been a while since I had to do this).  If you disc has errors you might as well accept the prompts, very likely it will fix your problems.

---

### Post by lunamystry on 2007-07-13
okay, when i use the gedit /var/log/message command. i am told gedit is not installed and when i include sudo in any command it say command not found.

---

### Post by lunamystry on 2007-07-13
sorry for replying like this, i'm using opera mini. Anyway. When i use the shutdown now command, i get this: could not start the x server due to internal error. Please restart GDM when problem is corrected.

---

### Post by lunamystry on 2007-07-13
i must say, i'm kinda enjoying this. I was expecting linux to do this when i first installed it. I can't wait till i can make my own ubuntu base operating system. :-D

I have just installed fedora and it looks the same as ubuntu. I&#314;l go back to ubuntu tomorow. I know the problem with the hard drive is gonna be back so i am hoping to get a solution before i install ubuntu again. The same error came up as i was insatlling fedora. If it is the Nero thing does anybody know how I can solve it?

thank you for your valuable time.

---

### Post by 2scoops on 2007-07-13
Hi,
Pretty new to Ubuntu and have also received this error last night.
I had just installed 7.04 ran Synaptic Package Manager d/l updates - installed OK and required a restart.
Upon restart I received the same error message saying a manual fsck will need to be run. It won't go any further without the fsck command being run. 
When I run it it keeps asking me do I want to ignore the error or repair - At the moment I'm only half way throught the HD but *'ll keep you posted*

I believe there is something wrong with the filesystem, as mine personally is an Old HD it could be something to do with that..

SPEC:-
Laptop Toshiba SP6000
PIII 1066
20 Gb
512 RAM

---

### Post by macogw on 2007-07-14
Is your hard drive OK?  If Ubuntu and Fedora are both giving you fsck errors, you may have a few bad blocks on your hard drive, which isn't really something fixable (as far as I'm aware), though it something that warranties cover.

2scoops, you can do fsck with -y and the -y will automatically tell it "yes" to all of the repairs.  Or hold down enter like I did when I didn't know -y worked for fsck after Vista ate my filesystem.

---

### Post by ramjet_1953 on 2007-07-14
Your HDD may be on the way out.

It may be worth getting hold of a non-destructive HDD recovery package.
These are usually stand-alone iso's that you burn to a CD and then boot the system from it.

I use [COLOR="Blue"]SpinRite[/COLOR], but there are others available.

These packages will tell you exactly what is going on with your HD, whether it is recoverable, or that you are on borrowed time with the HDD.

Regards,
Roger :cool:

---

### Post by lunamystry on 2007-07-14
> **macogw said:**
> Is your hard drive OK?  If Ubuntu and Fedora are both giving you fsck errors, you may have a few bad blocks on your hard drive, which isn't really something fixable (as far as I'm aware), though it something that warranties cover.

2scoops, you can do fsck with -y and the -y will automatically tell it "yes" to all of the repairs.  Or hold down enter like I did when I didn't know -y worked for fsck after Vista ate my filesystem.

What causes these bad blocks?

OH! and thank you for you valuable time

---

### Post by lunamystry on 2007-07-14
> **ramjet_1953 said:**
> Your HDD may be on the way out.

It may be worth getting hold of a non-destructive HDD recovery package.
These are usually stand-alone iso's that you burn to a CD and then boot the system from it.

I use [COLOR="Blue"]SpinRite[/COLOR], but there are others available.

These packages will tell you exactly what is going on with your HD, whether it is recoverable, or that you are on borrowed time with the HDD.

Regards,
Roger :cool:

SpinRite is pricey, I am in south africa with the money to buy spin right I could just get a new hard drive.  Thank you any way. I'll serach for possible alternatives.
 thank you for your valuable time

---

### Post by macogw on 2007-07-14
> **lunamystry said:**
> What causes these bad blocks?

OH! and thank you for you valuable time

bad blocks are hardware defects. the hard drive is physically bad.  i suppose dropping it could do it if the platters get smacked by the head or something, but seeing as they're something that's covered by warranty, i think it has a bit to do with whether your hard drive was good quality or a piece of crap to begin with

---

### Post by lunamystry on 2007-07-14
> **macogw said:**
> bad blocks are hardware defects. the hard drive is physically bad.  i suppose dropping it could do it if the platters get smacked by the head or something, but seeing as they're something that's covered by warranty, i think it has a bit to do with whether your hard drive was good quality or a piece of crap to begin with

That made sense to me :-O wow!!! I am really learning computers, hopefully by December i will be able to make my own Ubuntu based Linux :guitar: Oh yeah. 

[COLOR="DarkSlateBlue"][SIZE="3"]Thank you very much for explaining that. [/SIZE][/COLOR]

---

### Post by 2scoops on 2007-07-14
OK so I ran fsck and it returned a load of errors which it has fixed & now I can boot to the desktop - hurrah!

ANother question - when I choses restart the laptop closes down but not fully & doesn't actually reboot...

2scoops - i'll keep you posted

---

### Post by lunamystry on 2007-08-11
I found a way to change the number of system checks: 

sudo tune2fs -c 50 /dev/hda1 

The 50 and hda1 having to be changed to what applies to me. i changed the 50 to 0 so that no checks are done on my hard drive, Why do this even though its not advised? because i know my hard drive has errors. 

I am running ubuntu fine at the moment.I have two hard d rives now.  I am dual booting ubuntu ultimate( on the hard drive with errors) and on a separate hard drive I am running kubuntu 7.04. The hard dirve with errors I use to test things i am not sure about such as ubuntu ultimate and I had gusty gibbon recently. 

My question is, what is the worst that can happen to my system by making the hard drive check 0?

---

