---
title: "Putting linux distro on old laptop: which distro will be best?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-07
Hello everyone,
I wanted to try a linux distro on my old laptop, just to get a sense of how linux works. Someone told me he thought Ubuntu 7.04 would be quite slow on it (My laptop is 10 GB HD, celeron 433 mhz chip, RAM 288 MB [at 100 mhz]). So I started looking around for more suitable distros to try. Someone else told me that I would be better off with Xubuntu 7.04. I googled it, and found that some said for old laptops the previous version of Xubuntu (6.06 -- "Dapper") is faster. And searching further, still others have said that best is "Puppy". They have written that Puppy takes the least memory to run and goes by far the fastest. So I need your help: which distro will be best for me to try out on my laptop?

Also, if I want to do a dual boot with Windows 98, then do the download CDs of the above distros have in their installer the setup for dualbooting and partition set-up etc, or do I need to use "grub" first before I put in the linux cd?

Thanks,
Swarup

---

### Post by tgalati4 on 2007-05-07
Don't forget Damn Small Linux.  It will run completely in RAM and fly on that hardware.

---

### Post by spikester on 2007-05-07
for your laptop i'll go to Linux- yellow dog.Its for low power and older pc.:lolflag:

---

### Post by Sef on 2007-05-07
Check out [Xubuntu]("http://xubuntu.org").  It is made for older machines.

---

### Post by Bachstelze on 2007-05-07
If you want an Ubuntu-based distro : Xubuntu
If you wand Gnome and/or KDE : Debian

Gentoo would also be an option if you have another machine on the network you can use to do the compiling work, as it would take days on that hardware.

---

### Post by easyease on 2007-05-07
Puppy linux also runs just in hard memory......though i dont see  why dapper wouldnt install on and be useable on any laptop.

---

### Post by Bachstelze on 2007-05-07
Dapper would be OK too, but it's a bit outdated now...

---

### Post by swarup on 2007-05-07
Thanks for everyone's suggestions! I got four replies and four different answers-- so I guess that leaves me with some options. If Xubuntu really will run fine on my machine, then that would be convenient because I've already got the CD. Otherwise I could download the Puppy or Damnsmall linux.

But one important question: to set it up as a dual boot with Windows 98, do I need any extra software such as "Grub"? Or will the linux distro CD have everything on it I need to set up a dual boot?

Thanks,
Swarup

---

### Post by Wiebelhaus on 2007-05-07
> **Sef said:**
> Check out [Xubuntu]("http://xubuntu.org").  It is made for older machines.


Installed & working on an IBM 2645 with p2 333mhz & 128mb Ramm , runs great

recommended.

---

### Post by Bachstelze on 2007-05-07
The CD has everything you need (you need a bootloader to boot Linux anyway, even if you're not dual-booting). However, your specs might be a bit short to run a Live CD, if you want go with Xubuntu, you might have to get an Alternate CD.

---

### Post by Wiebelhaus on 2007-05-07
> **swarup said:**
> Thanks for everyone's suggestions! I got four replies and four different answers-- so I guess that leaves me with some options. If Xubuntu really will run fine on my machine, then that would be convenient because I've already got the CD. Otherwise I could download the Puppy or Damnsmall linux.

But one important question: to set it up as a dual boot with Windows 98, do I need any extra software such as "Grub"? Or will the linux distro CD have everything on it I need to set up a dual boot?

Thanks,
Swarup

Points up , your hardware is better so....

Yea , the xubuntu will do it for ya basically.

---

### Post by easyease on 2007-05-07
ah if you are planning on a dual boot system i think you would be best getting a alternative install disc of one of the ubuntu clan downloaded and burnt, so you can set up partitions yourself rather letting it run automatically. grub comes with the ubuntu install disc!

---

### Post by stee on 2007-05-07
When I stayed at my father's house in Easter, he asked me if I could disconnect and store away the old stationary computer he has. It was a Pentium 4, I think, with about 20 GB hard drive and 128 MB ram. I thought that I'd check out if I could make Win XP run faster on it, since it was horribly slow. Took about 15 mins to finish booting! After a lot of trouble and cleaning, I got it faster, but only from swimming in quicksand to swimming in syrup. It still took 8 mins to fully boot.

So I thought I'd try Ubuntu Edgy on it. However, installing from the live CD was impossible, because there wasn't enough ram. The alternate cd was perfect though! After installing the system, I had some trouble getting the usb wi-fi and the lpt printer to work, but sorted it out in the end. (I think it would have been much easier with feisty). My father couldn't believe the change! Suddenly everything responded instantly, and he could even have more than one program running at the same time :lol:

So my advice is to try any of the X/K/ubuntu versions, but remember to use the alternate cds.

(And yes, the dual boot thing... I think I actually used Partition Manager from windows first to resize the Win partition, then used the ubuntu cd to create everything else).

---

### Post by swarup on 2007-05-07
When I went to the Xubuntu website to download the CD, it said there that to use the alternate CD you need to have a high-speed internet connection when you go to install the OS. So I thought, since I only have a dial-up connection at my house and the 288 RAM and 433 celeron chip exceeds what they said I need for the live CD, then I just took the live CD. I hope it works.

But one question: I put the CD in my CD rom just now to see what would happen, and it just sits there. I mean, no installer screen comes up or anything like that. Once you put the Xubuntu CD into the computer's CD rom drive, THEN what do you have to do???

---

### Post by Bachstelze on 2007-05-07
You obviously need to reboot your machine so it boots from it. You cannot instal an OS while another OS is running...

---

### Post by fakie_flip on 2007-05-07
I agree. Use Damn Small Linux or Fluxbuntu.

---

### Post by bsell on 2007-05-07
You wlll need a high-speed connection to download either the alternate install CD or the LiveCD. It will take more than 5 days to d/l either CD with dial-up. I don't think you have either ISO image on CD. 

Your hardware will run Ubuntu with Gnome. I recommend you use the alternate Ubuntu insaller (text-based) and then install XFCE4 from the repositories:
```

sudo aptitude install xfce4
```

It's been my experience that Xubuntu doesn't always detect hardware or configure as easily as Ubuntu. IMO, Xubuntu isn't that much faster. You might shave 10 seconds off your boot time using Xubuntu over Ubuntu with Gnome, but switching to the XFCE desktop after intalling Ubuntu will make your boot times about the same as using Xubuntu. 

Win98 with a minimum of apps will take up about 1.5 GB of your hard drive. The Ubuntu install with the XFCE desktop will take a little more than 2 GB. 

One caveat: If you install Ubuntu (or any Linux distro), your internal modem will probably not work with it.

---

