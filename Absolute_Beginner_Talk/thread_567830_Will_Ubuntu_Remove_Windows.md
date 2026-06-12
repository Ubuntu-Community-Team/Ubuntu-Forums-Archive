---
title: "Will Ubuntu Remove Windows?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by jofwooster on 2007-10-05
I am very interested in switching from Vista to Ubuntu and actually being able to utilize the specs on my notebook. 

My question is this: If I choose to do so, will the install remove Vista so that I can use the massive gigs of disk space of space it takes? Will that space now be available, or will Windows still be there? If Ubuntu can remove Windows, is that a standard process in the installation? Thanks everyone!

I did a search, and didn't find this specific question (or I didn't recognize that it was the same).

---

### Post by BrendanM on 2007-10-05
You can choose to have Ubuntu remove Vista if you want. During the install process, IIRC, when it asks you about Partitioning, select "Automatic - Use entire disk" or something along those lines. This will wipe out Vista (and any data on that partition too, so back that up somewhere first) and give the whole drive to Ubuntu.

You can also install Ubuntu alongside Vista and dual boot them, which is a great option if you're still learning and not ready to go whole-hog Linux yet. Or if you want to play games now and then.

---

### Post by molly_001 on 2007-10-05
Use the Alternate Install CD (not Live CD) to install Ubuntu and make your life easier.  One nice option is to use the "Live CD of GParted" first -- boot up the machine with the GParted Live CD, and go in and shrink the existing Vista partition to a smaller size (leave, say, 20GB for Linux).

Then install Ubuntu using the Alternate Install CD and have it install "into the largest free space" (which you just created for it, using GParted) and you'll have a dual boot system in a jiffy.

---

### Post by Jimmyfj on 2007-10-05
If you are able to start Ubuntu from the Live Cd I'll second that you use that install method. The alternate install Cd is great but you need to know more about partitioning in order to use that. Just use the Live Cd, and when Ubuntu runs click the install icon. Follow the instructions and be sure to choose "Use entire disk" when the partitioning program comes up. This way your disk will be formated into EXT3 file system and your Vista will be gone from the disk.

---

### Post by hyper_ch on 2007-10-05
Btw: Use the Windows Vista partitioning tool to resize your VISTA partition (if you don't have any free unpartitioned space).

And also: Before changing partitions and such make a BACKUP...

---

### Post by jofwooster on 2007-10-05
Thanks for all the helpful information!

I'm not ready to do this yet, but that was one of the questions I had. I fully intend to go Ubuntu after I've 1.) tested it with the live CD, and 2.) dual booted and am satisfied with its capabilities.

My notebook should be blazing fast, but Vista is hogging everything, and all I need my notebook for is internet, word processing, music and photos, etc (ie: no gaming).

When I first got my notebook, I checked the available hard drive space, and 70 of my 160 gb were already used. Am I correct to assume that most of that (aside from other minimal programs) was used by Windows Vista? I am really interested in the extra space I'll have with using Linux.

Once again, thanks for all the helpful info!

---

### Post by russell.h on 2007-10-05
Windows Vista is definitely not 70 gigs. A full install with all of its media and stuff I think is less than 20, closer to 10 (maybe even a bit less?). But when my mom got her new laptop from HP it came with 50 gigs used by various crapware that was installed, and it wasn't even all that many individual items that were installed.

What specific laptop model do you have? Laptops are still more problematic for Linux in terms of hardware support than desktops, so if you tell us what model it is we should be able to give you some idea of whether or not everything will work properly.

---

### Post by jofwooster on 2007-10-07
Sorry it took so long to reply...

My computer is a Toshiba Satellite Widescreen Notebook Computer With Intel Pentium Dual-Core Processor T2080. DVD W/RW.

What other specs would you need to know? 

Thanks for all the help!

---

### Post by por100pre1 on 2007-10-07
> **hyper_ch said:**
> Btw: Use the Windows Vista partitioning tool to resize your VISTA partition (if you don't have any free unpartitioned space).

And also: Before changing partitions and such make a BACKUP...

Hyper_ch's suggestion is a good one, use Vista's own Disk Manager to shrink Vista's partition. Use Disk Defragmenter, Disk Cleanup and delete all but the last Restore Point if necessary. To use other tools is quite risky.

---

### Post by jofwooster on 2007-10-09
> **russell.h said:**
> What specific laptop model do you have?

I replied earlier, but did not have full access to my specs. Here's what I have:

> 
Toshiba Satellite A135-S4727
Processor Type * : Pentium® dual-core processor   Processor Number * : T2080   Processor Speed * : 1.73GHz   Front Side Bus * : 533MHz  
Operating System **
Genuine Windows Vista® Home Premium (32-bit)
Memory Size *
2048MB
Memory Speed
PC4200 DDR2 533MHz SDRAM
Display Size *
15.4" widescreen
Display Type *
WXGA with TruBrite® Technology
Display Resolution *
1280x800
Graphics Engine *
Intel® Graphics Media Accelerator 950
Graphics Memory *
8MB-256MB dynamically allocated shared graphics memory
Hard Drive Size *
160GB
Hard Drive Speed
5400rpm
Optical Drives *
DVD-SuperMulti drive (+/-R double layer) supporting up to 11 fomats

[http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=383411&seg=HHO]("http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=383411&seg=HHO")


Thanks in advance for any help or suggestions in my quest for Linux. I'm downloading the live CD right now...

---

### Post by jofwooster on 2007-10-11
I ran the Live CD.

Vista didn't allow it to boot up on its own so I had to hit F12 to bring up the CD.

I connected to our WIFI with no problem, but there was no sound. I'm assuming this is something I could fix if I dual boot and installed the proper...drivers?

---

### Post by por100pre1 on 2007-10-11
Possibly yes but, please post your sound card specs so others can give you some advice.

---

### Post by jofwooster on 2007-10-11
Does anyone here know how to bring up my specs on Vista?

---

### Post by hyper_ch on 2007-10-12
is the soundcard a pci device?

If so, boot LiveCD, open a terminal and type:

```

cd ~/Desktop
lspci > output.txt

```

Then you have a output.txt on your desktop where you can search for it.

---

### Post by corowakid on 2007-10-12
Here's a great site for learning how to dual boot, as well as many other MS/Linux solutions. Highly recommended!

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by mivo on 2007-10-12
> **jofwooster said:**
> Does anyone here know how to bring up my specs on Vista?

Aida32 is no longer developed, but it *should* still work even with Vista. It gives you more information than most programs, and you can download it [here]("http://majorgeeks.com/download181.html").

---

### Post by Indefual on 2007-10-12
Two points:

1) If you totally blow away your Windows Vista partition, you will lose Vista and all the programs that came with your computer.

2) You will also lose all data (MP3s, books marks, email, documents, pictures, and so on).

---

