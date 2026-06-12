---
title: "Linux;  I need one to READ and WRITE to NTFS"
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by MrClarke on 2005-06-18
Which is the one for that?

i'm going to wake -up a new motherboard and partition its HDD and install an operating system.

and i want to DUAL BOOT.

---

### Post by Mez on 2005-06-18
[QUOTE=MrClarke]Which is the one for that?

i'm going to wake -up a new motherboard and partition its HDD and install an operating system.

and i want to DUAL BOOT.[/QUOTE]
 Reading and writing to NTFS is VERY UNSTABLE AND DANGEROUS within Linux.

If youwant to read write to NTFS, I suggest you use Windows.

I suggest if you want to share information between windows and Linux, then use a fat32 file system

---

### Post by MrClarke on 2005-06-18
[QUOTE=Mez]Reading and writing to NTFS is VERY UNSTABLE AND DANGEROUS within Linux.

If youwant to read write to NTFS, I suggest you use Windows.

I suggest if you want to share information between windows and Linux, then use a fat32 file system[/QUOTE]
 thank you for your reply.

so, for me if i want to use the NTFS ,which is really the best filing system for XP, then i should just use LINUX  to read and not write.

---

### Post by Mez on 2005-06-18
yes, Writing to an NTFS drive/partition in Linux is VERY unsafe, and can corrupt your data. Leaving Windows unable to boot. It's quite safe for read only, bue to write, dont.... You WILL encounter problems and MAY cause your windows partition to be irrevocably damaged.

---

### Post by MrClarke on 2005-06-18
[QUOTE=Mez]yes, Writing to an NTFS drive/partition in Linux is VERY unsafe, and can corrupt your data. Leaving Windows unable to boot. It's quite safe for read only, bue to write, dont.... You WILL encounter problems and MAY cause your windows partition to be irrevocably damaged.[/QUOTE]
 maybe i can boot from two different HDD on the same cable with one o/s on each drive.

i'll make some calls.

---

### Post by Vicsun on 2005-06-18
[QUOTE=MrClarke]maybe i can boot from two different HDD on the same cable with one o/s on each drive.

i'll make some calls.[/QUOTE]
If you *really* need to write to your Windows partition, you could use FAT32 for Windows.  You should be able to both read from and write to FAT32 file systems.

---

### Post by MrClarke on 2005-06-18
[QUOTE=Vicsun]If you *really* need to write to your Windows partition, you could use FAT32 for Windows.  You should be able to both read from and write to FAT32 file systems.[/QUOTE]
 thanks for the reply,
i'm staying with NTFS for XP.

---

### Post by theerga on 2005-06-18
If you want two os's on the same hd what you can do is create multiple partitions on one hd it is actualy best you put system files and other files on diffrent partitons but you probably already knew that

---

### Post by MrClarke on 2005-06-18
[QUOTE=theerga]If you want two os's on the same hd what you can do is create multiple partitions on one hd it is actualy best you put system files and other files on diffrent partitons but you probably already knew that[/QUOTE]

actually what i was thinking about was segregating the two operating systems and keeping them on their own drive units/ then there would be no conflicts.

---

### Post by Mez on 2005-06-18
You can keep them on the same drive if you want to... btu, writing to NTFS, whether on the same drive or not, is still VERY DANGEROUS.

I cannot stress that enough.... DO NOT try and write to an NTFS partition from Linux YOU WILL MOST LIKELY CORRUPT THAT PARTITION.

If you plan to not share between them, or just read from the NTFS partition then go ahead, and be my guest, that's perfectly safe,

If you want to share, i do suggest creating 3 partitions, one for windows, one for liux, and one for shared files, with the windows patition in NTFS, the linux in ext2/3 and the shared in fat32... This is how I do it. (I have a second hard drive with FAT32 for all my music)

---

### Post by MrClarke on 2005-06-18
[QUOTE=Mez]You can keep them on the same drive if you want to... btu, writing to NTFS, whether on the same drive or not, is still VERY DANGEROUS.

I cannot stress that enough.... DO NOT try and write to an NTFS partition from Linux YOU WILL MOST LIKELY CORRUPT THAT PARTITION.

If you plan to not share between them, or just read from the NTFS partition then go ahead, and be my guest, that's perfectly safe,

If you want to share, i do suggest creating 3 partitions, one for windows, one for liux, and one for shared files, with the windows patition in NTFS, the linux in ext2/3 and the shared in fat32... This is how I do it. (I have a second hard drive with FAT32 for all my music)[/QUOTE]


ok.
i got it.
i think i need a bit more caffeine molecule so i gotta go make some.

---

### Post by Mez on 2005-06-18
sorry if i seem forceful, but that point needs to get across :D even if it already has, someone out there might read it and it might get it through to them :D

---

### Post by MrClarke on 2005-06-18
Hey,MEZ.
you and me are OK.
COOL YOUR JETS, I UNDERSTAND.

---

### Post by TristanMike on 2005-06-18
[QUOTE=Mez]sorry if i seem forceful, but that point needs to get across :D even if it already has, someone out there might read it and it might get it through to them :D[/QUOTE]

Like me  :)  I'm glad you did, cause I can see my father on the network and he wanted a couple files I had and I was just gonna dump them on his XP drive, that woulda sucked.  So now I'll just go the "long" way around it by dumping them on my FAT32 drive, then pull them to XP, then give them to him.  It may be longer, but now I know it's the safetst way.
Cheers.
TristanMike

---

### Post by theerga on 2005-06-19
anyways you will need software like project ntfs to do it and they on there site will tell you that it is unstable

---

### Post by MrClarke on 2005-06-19
[QUOTE=theerga]anyways you will need software like project ntfs to do it and they on there site will tell you that it is unstable[/QUOTE]

Erga,
let me have a link so that i can go there????

---

### Post by theerga on 2005-06-19
[QUOTE=MrClarke]Erga,
let me have a link so that i can go there????[/QUOTE]
 [http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/)

here you go but you have to have ubuntu installed first and i wont be any help downloading it i just stumbled upon it like a few months ago

---

### Post by MrClarke on 2005-06-19
[QUOTE=theerga][http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/)

here you go but you have to have ubuntu installed first and i wont be any help downloading it i just stumbled upon it like a few months ago[/QUOTE]
*******
it says it isnt supported any longer.
too bad.
i wish i could help these kids that write the code but i don't do that .
*************
This website is not currently maintained.
Welcome to the Linux-NTFS Project
Search Linux-NTFS


	

file system support 	  	
Website is not maintained

What is happening?
    The developers of NTFS have decided to stop looking after this website and answering general questions in the help forums. They will continue to fix bugs and develop the NTFS driver, but with fewer distractions. Any significant developments will be announced here. 
Why?
    Because they don't have the time. There are only three people working on the NTFS driver and they all have other commitments. NTFS is just a hobby for them. Helping beginners use the NTFS driver is a very rewarding, but it is not the best use of their limited free time. If they get some more helpers, then the website will reopen. 
How can I help?
    Although coders would be useful, someone with web skills would be more useful. The Forums contain a lot of very useful information, but it's hard to find. A PHP Wiki might be more appropriate. If you'd like to help, write to the development mailing list: [email]linux-ntfs-dev@lists.sourceforge.net[/email]

---

### Post by allforcarrie on 2005-06-19
you can change NTFS back to Fat32 just google it.

---

### Post by sas on 2005-06-19
There's always [Captive NTFS](http://www.jankratochvil.net/project/captive/), I can't vouch for it's quality though.

---

### Post by phrozen on 2005-09-23
im glad that i read this coz i was trying to write to an ntfs, and that would have been  baaaaaad

---

### Post by brallan on 2006-04-23
The dire warnings in this thread may be out of date. As of February 2006, the reverse-engineers at [www.linux-ntfs.org]("http://www.linux-ntfs.org/") seem to have introduced write support for NTFS in ntfsprogs. READ the [FAQ]("http://wiki.linux-ntfs.org/doku.php?id=ntfs-en") and also check out ntfsprogs in  Dapper: [[https://wiki.ubuntu.com/Lkraider/NtfsFuse]](https://wiki.ubuntu.com/Lkraider/NtfsFuse])

---

