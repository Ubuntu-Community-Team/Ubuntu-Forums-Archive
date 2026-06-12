---
title: "install slows to a stop......I think"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by acerhedge on 2006-09-01
Hi & Help & ??

Trying to install the latest Linux CD just received. Get as far as 'Welcome' -- i click on 'english'--- wait ages for the cursor & 'forward' to light up -- click on that & wait & wait & wait ... & give up.

yes I went into BIOS & changed to boot from CD.

yes i have plenty of space on the harddrive

PC is an Acer Travelmate 2350 with XP pro 


Shall i give up now? - if i can't master how to install the operating system then I will have no chance making my Repeat IT 'wifi hotspot booster' function!:sad: .............& all i wanted was a Gates-free zone:-( :-( :-( 

Thxs
Hedge (online twice a week..........adsl? ... rural portugal? .... no chance)

---

### Post by eternalis on 2006-09-01
How much RAM does your laptop have?
If its a bit on the low side, you might want to try use the alternate install CD.

---

### Post by SkyNet2029 on 2006-09-01
If this is the first time Linux is installed on your machine, then you probably don't have any swap space allocated yet, which you could remedy by way of the cd using either qtparted or gparted, shrinking your ntfs partition and then creating a swap file for linux to use, reboot and the cd will automatically detect and use that swap, which should speed things up quite a bit.

---

### Post by xyz on 2006-09-01
A little **psychocats** never hurt anybody as far as I am concerned:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

It's very well done,clear with pictures and all. It's helped me a lot to get the hang of installing.
Hope it helps you,too.

---

### Post by acerhedge on 2006-09-02
Thxs guys
I used safe mode & all went fine, but despite being careful (I thought) I now cannot get Windows back. (hence I am in a public library). Why do i want it? Well I got fed up with the Linux "Cannopt display" sign for Pentax camera, Sitecom wireless card, & more. So I thought I will just go back to XP.....Joke, It's not there, or is stuffed.
 So I try the foolproof Acer recovery discs which worked fine the one time I needed them before, but now I am screwed. I just get "grub error 17" after what I thought was a successful recovery.
Yes you can tell I dont know what I am doing but I was encouraged to try unbuntu more than once as it was supposed to be idiot proof?.....well, this idiot is about to reluctantly buy a new laptop out of an apparent necessity. --- maybe Windows is good for us plug & play merchants? ;) 
I am sure ubuntu is great IF you have a lot of IT knowledge, but some of us dont want that & I think the systems you are using should carry one big health warning.
 Sorry & best wishes to all.
Sincerely
Hedge --- well offline

---

### Post by xpod on 2006-09-02
You might just need to sort your mbr.....I had a lot of problems recently with wiping out XP and Ubu......and encountered the grub error 17 on my
travels.

I cant believe you feel you`d need to go buy a new computer just to resolve
a simple "Major Failure"........

I cant give you step by step instructions my friend as i just usually stumble along and fall upon my fixes but your problem is easily fixed i believe...

EDIT:..Ubunto is far from "idiot proof"...IN fact it leaves me feeling like MORE of an idiot at times BUT boy do i feel superior when i kick it`s butt
into touch

---

### Post by acerhedge on 2006-09-02
:D ---- In the bin seems *so* much easier xpod.............esp. as i have no idea what mbr is:( 

I should have left well alone....but it was the lure of an anti-virus this, detection/protection that world that once appealed so much......alas, no more

---

### Post by Rui Pais on 2006-09-02
Hi, may i suggest that you read some of [this documention]("https://help.ubuntu.com/community/GrubHowto?action=fullsearch&context=180&value=windows&titlesearch=Titles")? scpecially [this one]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo").

MBR is the first sector of your hardisc. Is from where boot loader boots.

Linux uses Grub (usually) as boot loader. It allows you to boot either Linux or Windows. 
Windows use they own boot loader. 

At your point either you [recover Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and add an entry to Grub Menu to your WindowXP - so you can choose which OS you can use... Or use some Windows tool (Like Windows Install/Recover CD) to reinstall Window boot loader and clean the Ubuntu installation.

---

### Post by acerhedge on 2006-09-05
Thxs for your advice guys:-)

Work in progress....slowly....between headaches:confused:

---

### Post by xyz on 2006-09-05
> **acerhedge said:**
> Thxs for your advice guys:-)

Work in progress....slowly....between headaches:confused:
Hang in there! Good luck.

---

### Post by acerhedge on 2006-09-06
& lo....after much messing around getting nowhere he left his mighty pc to itself installing ubuntu once more, & went out.
 When he returned it was all there neatly partitioned & both ops available......error 17 had vanished!:D 
One happy boy ............but with no idea why it all now works:confused: :confused: :confused: 

Next trick will be making the wireless work,,,,,,,,,,,maybe in a month or two!

Thxs to all

---

