---
title: "I have 2 questions"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by kathera lockharte on 2007-06-26
I know how to burn ISO images, but Ubuntu has more then just the ISO image, it has a bunch of files, so how do I burn them as well as the ISO image on to the cd, my os is debian and I wish to have multiple operating systems on my computer, so how would I do that as well?

---

### Post by kathera lockharte on 2007-06-26
I know how to burn ISO images, but Ubuntu has more then just the ISO image, it has a bunch of files, so how do I burn them as well as the ISO image on to the cd, my os is debian and I wish to have multiple operating systems on my computer, so how would I do that as well?

---

### Post by kathera lockharte on 2007-06-26
I know how to burn ISO images, but Ubuntu has more then just the ISO image, it has a bunch of files, so how do I burn them as well as the ISO image on to the cd, my os is debian and I wish to have multiple operating systems on my computer, so how would I do that as well?

---

### Post by kathera lockharte on 2007-06-26
I know how to burn ISO images, but Ubuntu has more then just the ISO image, it has a bunch of files, so how do I burn them as well as the ISO image on to the cd, my os is debian and I wish to have multiple operating systems on my computer, so how would I do that as well?

---

### Post by kathera lockharte on 2007-06-26
I was having some issues with my computer and well it caused some odd behaviour, so here are my questions.


 I know how to burn ISO images, but Ubuntu has more then just the ISO image, it has a bunch of files, so how do I burn them as well as the ISO image on to the cd, my os is debian and I wish to have multiple operating systems on my computer, so how would I do that as well?

---

### Post by bodhi.zazen on 2007-06-26
You just burn the .iso.

I am not sure what file(s) you are asking about.

Edit : I merged you threads & deleted a few duplicates.

---

### Post by kathera lockharte on 2007-06-26
> **bodhi.zazen said:**
> You just burn the .iso.

I am not sure what file(s) you are asking about.

Edit : I merged you threads & deleted a few duplicates.

sorry about that, I was experiencing some difficulties, but thank you for that, oh and the files I am talking about I have a screen shot of them [IMG]http://i111.photobucket.com/albums/n128/Samus_Aran978/Screenshot2-1.png[/IMG]

I don't know what they are for, but if all I need to do is burn the ISO then I will do that.

---

### Post by Inxsible on 2007-06-26
You would have to dual boot for multiple OS'es
 
Check [this ]("http://www.psychocats.net/ubuntu/installing")link for more info

---

### Post by Shazaam on 2007-06-26
The multiple posts arent caused by you. The powers that be are working on the forums and I guess they haven't finished yet.
Usually you would burn an ISO Image direct to cd/dvd. If you have more than just a single file the image is getting unpacked somehow.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by kathera lockharte on 2007-06-26
hmm, does that mean I can;t burn the ISO image, or are the files still intact within the ISO Image?

---

### Post by bodhi.zazen on 2007-06-26
> **kathera lockharte said:**
> hmm, does that mean I can;t burn the ISO image, or are the files still intact within the ISO Image?

You can check the integrity of the iso with md5sum.

```
cd $HOME/Desktop
md5sum -c md5sum.txt
```

Assuming the md5sum.txt on the screen shot is for Ubuntu.

Otherwise, yes you can just burn the .iso

It looks like you extracted the iso with say xarchiver, that does not damage the iso.

---

### Post by kathera lockharte on 2007-06-26
> **Inxsible said:**
> You would have to dual boot for multiple OS'es
 
Check [this ]("http://www.psychocats.net/ubuntu/installing")link for more infowell the link you gave me was to do a dual boot from windows, is it possible to do a dual boot with any OS, since I am running debian, and I want to run more than one distro.

---

### Post by kathera lockharte on 2007-06-26
> **bodhi.zazen said:**
> You can check the integrity of the iso with md5sum.

```
cd $HOME/Desktop
md5sum -c md5sum.txt
```

Assuming the md5sum.txt on the screen shot is for Ubuntu.

Otherwise, yes you can just burn the .iso

It looks like you extracted the iso with say xarchiver, that does not damage the iso.
yes I did extract it with xarchiver, infact I tried to do it when I was running windows and winzip did the same thing, so I guess archiving programs tend to unpack the ISO's I understand now, and thank you for helping me, I just need to know if its possible to dual boot from any OS since I ditched windows for debian, and I want to beable to compare differant forms of linux so I can choose to either keep it or switch to another or simply have two distro;s on my computer and use live cds is I need to.

---

### Post by bodhi.zazen on 2007-06-26
Cool.

Well, welcome to Ubuntu then.

Yea, it is confusing to many that the .iso is recognized by zip/archive. I have seen a number of folks try to extract the individual files and then burn the files as a data CD :(

Dual booting + is easy with Linux. Watch out for the BSD and Microsoft, they can be a little tricky.

---

### Post by FleetAdmiral74 on 2007-06-26
If you go to the download section, you just download the ISO. Sure, *it* has multiple files, but you can just burn the iso like normal.

Once you make sure you have room to install ubuntu by repartitioning if needed, then just install it and it should auto set-up the dual boot.

---

### Post by arvevans on 2007-06-26
An .iso image usually contains all the files necessary to install and start an operating system.  Once you have the system installed (from the bootable .iso) you can then use the package manager to download and install additional applications that you might need.

Your question regarding how to run multiple operating systems needs some clarification:
[LIST]
[*]Do you mean that you want to dual-boot Linux and some non-Linux system?
         or
[*]Do you mean that you want to install multiple kernal versions with the same Linux distribution, 
         or
[*]Do you mean that you want to multiple-boot more than one Linux distribution?
[/LIST]

If you want to dual-boot Linux with a Microsoft OS, you need to install the Microsoft OS first, then install the Linux OS using Grub as the boot loader.  That should automatically find and configure your system for dual-boot of Linux and the non-Linux OS.  To do this you will need to make suitable partition adjustments or use a separate drive for the different OS installs.

To install multiple Linux distributions you do much the same thing, but it does not matter which is installed first.  The last one installed should find the others and configure Grub for multi-boot of each.
_._

---

### Post by kathera lockharte on 2007-06-26
well I am done the installation, though I was unable to do a dual boot. Oh well I guess I can try again another time.

---

### Post by bodhi.zazen on 2007-06-26
Bah, dual booting should be a snap.

Just edit /grub/boot/menu.lst and add the appropriate entry (I don't know if you need to add Ubuntu or Debian).

here is a link to grub, although it is a little overkill ;)

Best Guide: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Supergrub : [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)


Edit: well, looks like two links, but they are sooo good :)

---

### Post by yui chan 18 on 2007-06-26
ok, hold up there...i've been having problems with not having enough space on the cd to burn the image, does this mean that all i have to do is burn the isolinux folder onto a cd after i extract the files?

---

### Post by bodhi.zazen on 2007-06-26
> **yui chan 18 said:**
> ok, hold up there...i've been having problems with not having enough space on the cd to burn the image, does this mean that all i have to do is burn the isolinux folder onto a cd after i extract the files?

No. It means you are trying to copy the .iso to a CD as if it were a data disk. You need to burn the iso, totally different ;)

[https://help.ubuntu.com/community/CdDvdBurning](https://help.ubuntu.com/community/CdDvdBurning)

From Windows : [http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by yui chan 18 on 2007-06-26
well, someone just helped me out with this on another thread i posted. apparently if i plug my laptop into my dsl, i can install the ubuntu studio programs and not need any cd. and yes, i did burn it as an iso. i selected "burn image", not data file. :-D i think the problem is my dvd burner.

---

