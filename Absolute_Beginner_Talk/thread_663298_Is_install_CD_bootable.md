---
title: "Is install CD bootable?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by visigoth58 on 2008-01-10
I'm totally new to using Linux though I've read about it and heard its virtues extolled by friends. 

I downloaded the 7.10 ISO file, it checked out with MD5SUM, Nero burned and verified it.  But I can't get  my laptop to see it, use it, boot it.

Here's the rub: Got this IBM Thinkpad A22m (PIII, 512Mb RAM, 1 GHz chip ) with a crashed HDD. I replaced it with a 6 gig drive (salvaged from a junker) which checked out fine. I formatted it and attempted to install Suze Linux 10. Install disc no. 4 (of 5) had an error and the install aborted. Strangely, when I turned it on again Suze proceeded to boot up but it asked me for a login and pw. I don't have one b/c the installer never asked me to set one. Well, Suze's documentation and web support sucks so I gave up on it. That was a few months ago.

Recently a friend encouraged me to try Ubuntu. I am now trying to load the disc I made to this laptop. I press F12 and choose "boot from cd" and SUZE loads up. I press F1 and change boot order to boot cd first. Same thing, SUZE again. There is no other OS on this machine.

So, I want to know - Is cd I made bootable? If so does anybody have any suggestions. When SUZE loads, just before it launches GUI says "grub loading stage1.5."  Does that help any?

Thanks

---

### Post by thelatinist on 2008-01-10
Yes, the Live CD is definitely bootable.  If I understand you correctly, you have changed the setting in your CMOS to boot from CD.  I assume you have checked in CMOS to see if your BIOS is recognizing your CD drive?  If so, try disabling boot from HD entirely and see if it will boot from CD then.

---

### Post by mrphud on 2008-01-10
when I downloaded the ISO image I had to burn it to a cd to make a live cd. The only thing is I needed another program to make it a live cd. ISO images aren't usually detected by the drives. They need to be burned executable. I am looking for the burn program now.

---

### Post by mrphud on 2008-01-10
it looks like nero can burn the ISO but thelatinist is right you need to enter your bios and setup a cd rom boot if you want to try live cd.

---

### Post by the-edmeister on 2008-01-10
> **mrphud said:**
> when I downloaded the ISO image I had to burn it to a cd to make a live cd. The only thing is I needed another program to make it a live cd. ISO images aren't usually detected by the drives. They need to be burned executable. I am looking for the burn program now.
If you are on Windows:
[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

You can't just copy the image to CD, you need to "Burn Image" from the File menu in Nero or the Actions menu in Infra-Recorder.

---

### Post by visigoth58 on 2008-01-10
Sorry I took so long. The dog was barking and I had to walk him. After midnight. 29 degrees. Popsicle poop?

I forgot to mention that I downloaded, I guess you call it a text version. I clicked the box on the d/l page to create a desktop version because I thought it would be better for my situation. (I guess a laptop is not a desktop... though I think they were talking about PC as opposed to server.) Is a text-based version bootable? I guess I'm not clear on the concept "live cd."

Don't know how to fiddle with the CMOS. (Isn't CMOS hardware?)  On boot-up I press F1 to go to BIOS setup. That's where I change the boot order around. I tried **thelatinist's **idea and disabled the hard drive. I rebooted and, after checking RAM, another list flashes past in a nanosecond then it says something like:

" installing from (or with) Intel Boot Agent v. 4.0.17. " and "Network Boot Protocol RPL"

Then it lists network files, like Novelle Netware, then says:
 
"LAN adapter failed - Check cable & reboot." (I'm not using a network cable, there's no OS, but I could plug it in if it would help. Not much of a network administrator though.)

Then, after a second, it says:

"Exiting RPL loader" and then, after another second, says "OS not found" and then just hangs. When I press any key it repeats the process from "installing from Intel Boot Agent"

I went back to BIOS and disabled everything but CD (which BIOS describes as ATAPI [something something] CDROM) and only get the same thing.

---

### Post by ugm6hr on 2008-01-10
You need to clarify *how* your burnt the CD (did you copy the iso file and paste into the CD, or did you write a *CD image*.  Also - let us know *where* you got the iso file from.

Have you got a working computer?  If so - boot in that, and open the CD.  You should see lots of files in it.  If there is only a single iso file - you've done it wrong.

---

### Post by visigoth58 on 2008-01-10
Oh sorry.

I used Nero burning rom. I clicked on new and chose "create ISO." I set it to the slowest speed it provided which was 8X. (I did read through these forums before I gave it a go.)

The Ubuntu install help (BurningIsoHowto) said to d/l and use InfraRecorder but I was reluctant because I keep downloading stuff right and left and I worry about viruses and having to learn apps and I already had bought and paid for Nero and thought it should be able to do the job. I will d/l InfraRecorder if you think that will help.

---

### Post by visigoth58 on 2008-01-10
Should I have used "CD-ROM (boot)" or "CD-ROM (UDF/ISO)?"

---

### Post by visigoth58 on 2008-01-10
> **ugm6hr said:**
> You need to clarify *how* your burnt the CD (did you copy the iso file and paste into the CD, or did you write a *CD image*.  Also - let us know *where* you got the iso file from.

Have you got a working computer?  If so - boot in that, and open the CD.  You should see lots of files in it.  If there is only a single iso file - you've done it wrong.

I got the file from Ubuntu.com Get Ubuntu page. Used a mirror at Wayne State Univ. (I'm in Ohio)

This computer I'm using now good - lots of speed, RAM and hard drive space. You say, "boot in that." Do you mean launch the cd and boot up this computer in Ubuntu? Like a dual boot state. Or just explore the disk in the Explorer? (Using WXP SP2)

Just looked at it. Explorer gives the name of the disc in F: drive and to the right shows that there is one file called "unbuntu-7.10-desktop-i386.iso" which is 712,508 KB.

---

### Post by Paqman on 2008-01-10
> **visigoth58 said:**
> 
The Ubuntu install help (BurningIsoHowto) said to d/l and use InfraRecorder but I was reluctant because I keep downloading stuff right and left and I worry about viruses.

Infrarecorder is open source software, so you can be sure it won't contain anything nasty. 

I don't know much about Nero, but if you burn your image following the instructions on [this page](https://help.ubuntu.com/community/BurningIsoHowto) then we can pretty much guarantee you'll end up with a working LiveCD.

If that still doesn't work, then I guess it's time to start fault-finding on the laptop.

---

### Post by ugm6hr on 2008-01-10
> **visigoth58 said:**
> Just looked at it. Explorer gives the name of the disc in F: drive and to the right shows that there is one file called "unbuntu-7.10-desktop-i386.iso" which is 712,508 KB.

That is the problem.  You have *Created* an iso in Nero, which has merely put the file on the CD-R.

You need to *Burn Image* instead (or something like that).  Nero doesn't use iso by default (from memory - it uses .nrg images), but it should be able to burn iso images.

EDIT:
Just googled - and Nero cab burn iso discs: [http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)
[http://www.bay-wolf.com/burnimage.htm]("http://www.bay-wolf.com/burnimage.htm")

I would recommend disc-at-once and Finalize CD modes.

PS: I think you have downloaded the LiveCD (not text-based installer), since the "text-based" installer is usually called XXX-alternate-i386.iso (I think).

---

### Post by visigoth58 on 2008-01-10
Just returning to this task. Thanks to Paqman and ugm6hr's Avatar  	
ugm6hr for your suggestions. Am going to use NERO again with its "burn image" option. Actually I clicked "create cd (bootable)" and the next dialog box asked me which file to use to "burn image."  Will do md5sum.

While I was typing this Nero burned the disc and eject it. When I reinserted to run the md5sum Ubuntu launched a browserbox telling me I could boot the disk "without affecting your system." That's on this pc, not the laptop. I think I'll try it here then try to install on the LT.

---

### Post by NovaAesa on 2008-01-10
> **visigoth58 said:**
> Should I have used "CD-ROM (boot)" or "CD-ROM (UDF/ISO)?"
You should use CD-ROM (UDF/ISO)

---

### Post by thelatinist on 2008-01-10
> **visigoth58 said:**
> Just returning to this task. Thanks to Paqman and ugm6hr's Avatar  	
ugm6hr for your suggestions. Am going to use NERO again with its "burn image" option. Actually I clicked "create cd (bootable)" and the next dialog box asked me which file to use to "burn image."  Will do md5sum.

While I was typing this Nero burned the disc and eject it. When I reinserted to run the md5sum Ubuntu launched a browserbox telling me I could boot the disk "without affecting your system." That's on this pc, not the laptop. I think I'll try it here then try to install on the LT.

No, don't use Nero to create a bootable CD.  The disk image itself is bootable.  Just use "Burn Image."

---

