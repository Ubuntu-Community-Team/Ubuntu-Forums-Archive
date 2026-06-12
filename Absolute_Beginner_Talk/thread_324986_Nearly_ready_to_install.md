---
title: "Nearly ready to install"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by WebJoel on 2006-12-24
I have been asking about installing Ubuntu to my secondary HDD as a duel-boot system and have received some good replies.

 (my pc: 256MB-RAM, two IDE drives, Win-XP on C:\(80-GB),  E:\ is 'available' for Linux(20-GB), 2.4GHz Celeron processor, boot order:floppy/CD-rom/HDD)

 I had tried to install Ubuntu on my E:\ drive, -it failed to install as it 'just hung' at the part of entering city and time-zone for the longest time (freezing-up the pointer-tool so I had to bail-out)... now, the Linux distro "puppy linux" that *was* on E:\ is 'messing up' and some programs on it aren't working... No great loss, but this is not a confidence-building first expierience with the Ubuntu LiveCD....
  Ultimately, I want Ubuntu on E:\. I was just using 'puppy' because it could be installed 'cleanly' on a Win-system without killing anything on C:\ (Windows, etc.)

  Reading up on how my motherboard takes the IDE drives, I am not so sure I quite understand how to 'swap' the MASTER "Windows" drive and the SLAVE "wanna-be Linux" drive, either. If I change the MASTER for the SLAVE and install Linux on the now-MASTER, and then swap the MASTER/SLAVE order back around, how would Windows and Linux know of each other's presence? -I should end up with a Windows-XP bootable ("C:\") but want the choice to boot Linux-on-E:\ on start-up.
  Before I start swapping cables in my computer, I need to be sure I understand what this does. According to my interpetation of the manual that came with the motherboard and how-to install secondary (IDE2) drives, it says that *the configuration is the same as IDE1*. Okay... now I *am* confused again. ](*,) 
 It appears that there is a plug-in slot for the cable that supplies IDE1 ("MASTER"), **and**:
it appears that there is **another** plug-in slot for the cable that supplies IDE2 ("SLAVE"). 
 -What would it do to just REMOVE my MASTER disk (unplug it **and** it's power cord) and plug IDE2 into the "master" slot, install Ubuntu that way, and then change it back. -Would either drive 'see each other' and know that there is another OS present on the other? I want this to start-up by default to "C:\" Windows-XP, *but have the option* of starting up on E:\"Linux", if I wanted it to. I do not have any pressing need at the moment for either drive to 'see' each other but I suppose that they would need to, in order to be bootable from a menu-list at startup, yes?

 I have deleted all the TEMP, trash and junk that I do not want on my MASTER ("C:\") drive, DeFragged it, -got it 'tight' again. I have about 75% of my C:\ "FREE" again. -What if I just installed Ubuntu on the same HDD as Windows-XP? There'd be no 'HDD-swapping' involved. I'd want to use gparted first to make a suitable partition, or can this be done with the LiveCD installer disk? I am just panicked that trying to install this Ubuntu is somehow, someway, going to insult Windows-XP and make it refuse to play nicely with my other OS...

 I have repeated some parts of this request for help, I am sure, -but be patient with me. ](*,)  Explaination would be nice. The links given me last time were a good read and are probably quite explainative but haven't fully convinced me what to do next. :-k 
 -Joel

---

### Post by RanDinCarolina on 2006-12-24
Let me clear up the IDE1 and 2. On your motherboard you have two IDE channels, IDE1 and IDE2. This enables you to have 4 IDE devices. Each channel has Master and Slave. Each device has switches which select master, slave, and cable select. The master device should have it's switch set as master and is on the end of the cable.The slave device should have it's switch set as slave and is in the middle of the cable. This is applicable to both channels. When I installed a dual booted system, the partitioner asked me which drive I wanted to install to. Your system drives should show up as HD(A), HD(B), HD(C) and so on. Your windows installation should be on HD(A), so you would have the partitioner install to HD(B). Grub should recognize your XP installation and place it where it need to be.

See more about Grub to change your boot order. I usually choose what I want to boot from the menu.

Where on your IDE buss is your optical drive located?

---

### Post by WebJoel on 2006-12-26
After re-reading the manual that came with the motherboard (regarding how-to install HDD, etc), I do see that you are correct. The "IDE1" takes one HDD as "MASTER" and 'slaves' a second from that. A THIRD hard-disk can be installed on the available IDE2, with a 'slave drive' coming off of *that* as well (for a total of four). That explains the mysterious one-line statement that 'the configuration is the same as IDE1' that I was mis-interpreting. BOTH of my two current HDD are, in essence, coming from IDE1 (correct?).

 So I guess that the best course is to open up my computer case and swap the MASTER / SLAVE switches (and vice-versa on the 2nd drive), install UBUNTU cleanly onto then-current MASTER "E" where it would otherwise be the default loading OS. 

And since I want Windows-XP to be 'default', merely swap MASTER/SLAVE SLAVE/MASTER settings back again, -right? Since BOTH "HD(A)" and my "HD(B)" would both be recognized by GRUB at install, swapping them back as before, would make **Windows on HD(A)** boot by default but let me **choose/recognize** to otherwise boot Ubuntu?

 [B]HD(A) is my "C"-drive
 HD(B) is my "E"-drive
 HD(C) is my optical drive ("CD-rom drive").[/B]

 -I am sure that this must seem so redundant to keep asking clarification questions but I have to be sure.

---

### Post by RanDinCarolina on 2006-12-26
I would install without opening the case. GRUB will see your XP installation and add it to the boot menu. That allows you to choose which OS you wish to boot. Just make sure that you don't install over the NTFS partition as that is your XP . I found out how to dual-boot by reading the posts. 

Basically, allow the partitioner to install to a different drive than the NT one. GRUB will install to the MBR, see your XP and add it to the boot menu. If you then want to change the boot order, cut and paste will be your friend.

---

### Post by WebJoel on 2006-12-26
I just read another post, -"Almost Ready To Install" and it has *almost exactly* my very same situtation, and from it, earned a bit more confidence. It *really helps* when reading the OP's words that *I* was nearly saying *in my mind* the same things that the follow-up posts did...
 
 -I really, really *do not* want to open my pc case, folks! Anything more than installing more DIMMs or vacuuming out the dust and it begs a risky proposition for me although I have modest training to CLEAN computers inside and out, removing/installing componants and setting DIP or jumper switches...*terrifies me*. :-#  (I had a bad experience once, cleaning a co-worker's i386 computer. My Data-Vac vacuum unbeknownst to me at the time, sucked a loose jumper-switch off of her third HDD and it failed to boot as start-up time... I figured out what was the problem and spent about three hours sifting thru my vacuum bag's dust, -looking for a infinitesimally-small little plastic jumper-switch. -I Found it and got her pc working in time and she never found out!) So, ...leaving the hard-drives _alone_ works for me and I will trust Ubuntu to SEE and inform me of what to do...

 But I think that I am ready to wing-it and give this Ubuntu thing a try... :mrgreen: 

btw, -this Forum is GREAT! Much appreciated.
 -Joel

---

### Post by iPirates on 2006-12-26
This really isn't related, but can some mother boards support more than 4 IDE devices?

---

### Post by Duck2006 on 2006-12-26
> This really isn't related, but can some mother boards support more than 4 IDE devices?

No not that i have seen. Four is it for IDE

---

