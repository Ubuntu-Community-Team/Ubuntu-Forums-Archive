---
title: "Can Not Set Up Partitions"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-03-17
First and formost; 

Hello every one, I am trying to use a Linux based O/S For the very first time, To say I know nothing would be a grose understatement.

I am Currently running Windows XP Home edition on my alien with a pentium four.

I Downloaded the UBUNTU 6.10 burned it off and even ran it a little in live mode. Gotta say that isnt to much fun becouse of how slow it is, however id did seem rather interesting so I decided to give it a try.

Installation: 

I Clicked on the Install Icon and everything happend just little the artical from [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index") said it should.

Welcome to the Partitioning part of the process. Untill now I have tried the first option given, about resizing IDE1 master partition, this is the one Psychocats says is best suited for people who want the Dual-boot option but know nothing of setting one up.

Unfortinatly it just seems to stop and go nowhere, I have given this process most of an hour already with no results at all. It just sits there after clicking next and does nothing.

Now I have tried the last option "Manually edit partition table" GParted starts up and everything seems to go beutifully. So far I have set it to;

Resize 150 GB HD to 100 GB  NTFS
make a 15 GB Fat 32
Make a 1.95 GB Linux Swap. ( is this the virtual Memory?) 
and make a 39.13 GB EXT3 for Linux to run on

I am not absolutly positive if this is compleatly the best way to go or not, like I said I KNOW NOTHING! :)  BUT! here is my problem, when I tell it to exicute the command it comes back saying it can not resize my current partition. ( the 150 GB hard drive that windows is on ) 

Should GParted be able to resize this? Or should I be reinstalling windows and having it reformat and partition my hard drive?  I really dont want to reinstall windows its just kinda a pain in the bumm. reinstalling that, then all the periferals and what not ( HP Printers Hate me! ) 

Thank you for any information yea'll can give me
I know dealling with people who are even less than just noobies can be frustrating but thanks again

Sabar
:guitar:


My way of getting things to work right.
I installed an older Hard drive I had laying around. that way I still have windows separate from Ubuntu and I knew I wast messing windows up.

---

### Post by Kateikyoushi on 2007-03-17
Gparted should be able to do that and that's a good partition layout, you could actually use the ntfs drivers to read from ntfs in linux, and the ext [LINK]("http://www.fs-driver.org/") driver to read write your ext from windows. If the fat would be only to exchange data betweem the two.

As for the error, could you tell us the error message ?
I would recommend to do a disk check first then defragment few times and do backup of important data before you try again.

---

### Post by sad_iq on 2007-03-17
Ubuntu cannot resire the partition because it if formatted as ntfs (writting to ntfs is still buggy). And why should you reinstall windows? just boot to it, defrag your drives, resize your partition, then boot ubuntu and continue with manual partition, and yes...swap is virtual memory!!!

---

### Post by Sabar on 2007-03-17
Kateikyoushi

Unfortinatly I dont remember the error message word for word  I think it just said it could not resize partition.

sad_iq 

If I understand what you are telling me. I can resize the partition from windows. ( You mean with it running or off the boot disk? ) making a blank area then try to install Ubuntu? and it should work?

Like I said I realy dont know much of what I am doing. I know just enough to be really, really, dangerous ;-)  so please talk s-l-o-w  to the poor dumb redneck ;-)

Thanks for ansewring so quickly guys!

---

### Post by sad_iq on 2007-03-17
I meant with windows running...I don't remember any programs in windows about partitioning except Partition Magic( haven't used windows in ages :lolflag: ),just google about it. I don't know if the windows disc can resize partitions but you could give it a try...just **backup your data before proceeding** !!!
 The rest should work just fine!
 P.S. googled something about partitioning...found this [http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)

---

### Post by Sabar on 2007-03-17
Thanks sad_iq, I am googling now. I really dont think I have much to back up. Most everthing file I want to keep and not lose. Goes straight to a second Hard Drive.  I know how often I screw things up so whn I orderd my alien I got it with a second Hard drive to keep pictures, music and important files on. That way when I reformat ( atleast once a year. usually winter when I am actually home, bored, and doing things I know nothing about;-) )

I really doubt if system restore could fix a partition melt down

---

### Post by Sabar on 2007-03-20
Ok Guys I have had another brainiack idea. (maybe) 

Rather than trying to duel boot and worrying about partitioning I actually have a spare hard drive laying around here from an old computer. unfortunately the old computer is gone. so I can not just load Ubuntu onto that.

I have sent a message to Alien, Seagate, and Intel in the hopes that some one there can give me some Idea if this is possible and if it is how to do it.

Basically what it the message was, was a list of components

In my computer I have a 

Intel D945GNTLR Mother board

P4 3.2GHZ 640 2MB 800FSB LGA775 Processor

Deskstar 160 GB  8MB CACHE SATA System Drive  ( Windows XP home )

Deskstar 250 GB 8MB CACHE SATA Storage Drive ( Music, Pictures ) 

I also have a Seagate Barracuda ATA II Model ST330630A With an Ultra66 PCI card That I pulled from my old Dell, 

What I am wondering is, 

is it even Possible to add this Old 80 GB Hard Drive to my system 

What is the worse that can happen if I do?

What do I have to do every time to boot to the other O/S? Just F2, Bios, boot from HD 1 or 3?

Is this the dumb way to go about this?

This whole line of questioning is stemming from the fact that I don't want to mess up the hard drive with windows, and I can not seem to get GParted to partition my HD with XP on it.

Interested to hear any thoughts on this 
Sabar
:guitar:

---

### Post by Kateikyoushi on 2007-03-20
You can install to the 80GB Hdd automatically it would install grub and you boot that and select which OS to boot.
Grub can be easily deleted and the windows boot loader reinstalled by using a windows cd or downloading some few MB alternative ISOS.

You could also disconnect the other drives while you install so those are uneffected, unfortunately in this case you might not be able to boot if those drives change the drive order, then you have to edit grub from the live cd.

---

