---
title: "will my new computer work with linux?"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by coolrunn on 2006-03-01
hi,
I'm getting a new computer and excited about using linux instead of windows. However some have told me to check that linux will be compatible. (also I am hoping that the windows isn't pre-installed and that the ubuntu disks don'tr take two years to arrive)

my computer is a DELL. 

specs: dimension 5150 pentium 4 processor 630 with HT technology
160GB 7200rpm SATA hard drive 

Hopefulluy someone can help me, do you need more info. I don't know what to type. 

(PS not that its that important to me but will games ever get linux ports?)

---

### Post by knalle on 2006-03-01
you got to dig up the **geek names** of your motherboard, soundcard and graphics card

---

### Post by Brunellus on 2006-03-01
[QUOTE=coolrunn]hi,
I'm getting a new computer and excited about using linux instead of windows. However some have told me to check that linux will be compatible. (also I am hoping that the windows isn't pre-installed and that the ubuntu disks don'tr take two years to arrive)

my computer is a DELL. 

specs: dimension 5150 pentium 4 processor 630 with HT technology
160GB 7200rpm SATA hard drive 

Hopefulluy someone can help me, do you need more info. I don't know what to type. 

(PS not that its that important to me but will games ever get linux ports?)[/QUOTE]
if you can, go ahead and download & burn an ubuntu disk for yourself--no diferent from waiting for the shiny pressed disks, unless you have no interent access.  You might want to join your local Linux User Group mailinglist and ask politely if any of the members have any spare disks they'd like to give you. You'll probably get one very quickly then.

As far as compatibility:  I can almost guarantee that the modem (that is, for dial-up) won't work.  Most modems shipped in computers these days are WinModems, and support for those is notoriously bad in Linux.  

We will need a more complete spec sheet to tell for sure, but so far I can see no real reason why your computer should not work with Ubuntu.

---

### Post by tadashi on 2006-03-01
I did a google and only saw people using Redhat and SUSE so I do not think you will have a problem with Ubuntu or Kubuntu.  I recommend you rezising your partition as soon as you get it if you want to dual boot.  I used SUSE's v10 install disk 1 to do this.  They had a very nice utility.  I created a vfat drive that each would share, a swap, and linux partition.  I kept my windows partition on there just in case I broke my linux, but I have only booted it once or twice since getting the computer. :p

The one issue I see people having problems with Linux and the 5150 is getting the DVI working.  Good luck.

---

### Post by coolrunn on 2006-03-02
what specs are important?

it has:

ati radeonx600 256mb hypermemory graphics card.
integrated sound blaster audigy advanced hd
v.92 data fax modem uk

PS I 'burnt' a live CD file onto a blank CD (it took nearly 2 hours) and the blasted thing didn't work!!

I really would like to try out ubuntu afore installing it. Is there any formal or authoritative/respected literature I can read up on about linux or ubuntu before hand?:-k

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=coolrunn]
PS I 'burnt' a live CD file onto a blank CD (it took nearly 2 hours) and the blasted thing didn't work!![/QUOTE]

Did you burn it as a CD image? What burning program did you use? There should be an option for burning an .iso file. It's not the same as simply putting the .iso on a CD as your would any piece of data, it has to be made bootable. After you can put in your cd drive, boot up, and make your system boot from CD.

---

### Post by carlosqueso on 2006-03-02
2 things to check.  First, you can't just burn the file onto a cd.  You need to burn it as a disk image.  Go into your favorite CD burning software and find a command like "burn image" or "write image to disk" [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto) will help if you need it.  

Second...you may need to go into your BIOS and make sure you are booting from the CD.

---

### Post by coolrunn on 2006-03-02
thanks for the help. BUt it all looks too complicated and I can't be arsed. I'll just go ahead with windows for now and when my ubuntu disks arrive I might give it a whirl.

In the meantime is there any illustrated book/ user guide for ubuntu that tells me all about it which I can read through?

---

### Post by coolrunn on 2006-03-02
also if I do decide to install ubuntu how easy is it to uninstall windows?

---

### Post by Coelocanth on 2006-03-02
[QUOTE=coolrunn]also if I do decide to install ubuntu how easy is it to uninstall windows?[/QUOTE]

If you decide togo right to Ubuntu and give up Windows altogether, you can just format your whole drive when you instal Ubuntu. Bye-bye Windows.

For some guides, try the wiki link at the top of the page as well as some of the following:

[Linux Commands](http://www.ss64.com/bash/)

[Tuxfiles](http://www.tuxfiles.org/)

[Terminal For Beginners](http://www.ubuntuforums.org/showthread.php?t=73885&highlight=linux+commands)

[Learning The Shell](http://www.linuxcommand.org/learning_the_shell.php)

[Linux Documentation Project](http://tldp.org/index.html)

I'm still learning and still browsing through some of these, so don't know how useful they'll be to you. You can also find a lot of stuff by doing a google search. Good luck!

---

