---
title: "burning iso in Kubunto"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-24
Is it quite possible to burn a further ubunto iso in kubunto with the software that comes with it....
Ive messed my ubunto/xp up with a grub loading error 17(or 21 if i unplug ubu hd)

I was messing about trying to put a further hd in that eventually went fine ...all detected and i formatted it to ext3 then i went to "discs" and made a mount point in /mount and enabled it.
I rebooted knowing i`d need to do it properly with fstab etc but just needed to put pc back together but when i rebooted again it was kanackered....unplugged new hd again and get the above errors at grub.

So reckon i need ubunto iso(which i gave to friends who i cant get hold of).......I TRIED....lol

I had a similar prob yesterday that i managed to fix BUT not this


EDIT:clicking 3 buttons in cd burner xppro was as far as ive ever got burning iso`s

---

### Post by nudnik on 2006-08-24
I assume you want the install CD for Kubuntu, if that is correct, you can either download it from the Ubuntu website, or request a free CD.

For burning I would reccomend K3b, a KDE program which will work in either Gnome or KDE enviroments.  

Ubuntu and Kubuntu are based on the same core but feature different interfaces, KDE for Kubuntu and Gnome for Ubuntu.

---

### Post by xpod on 2006-08-24
sorry you dont understand.......I HAVE ubunto already on a dualboot with xp....Ubunto is on slave hd.

I installed a new hd that worked fine ,was detected in ubunto and all was well...i never added /mount to fstab at this point but turned the pc off to put it back together and when i rebooted i had the grub saying..
GRUB LOADING:ERROR 17(or error 21)

I have another pc with kubunto so need to get the "Ubunto" iso but am not sure about burning iso`s on Kubunto as i used xp previously...

I gave my Ubunto ISO to friend so need to burn new one

---

### Post by nudnik on 2006-08-24
Access the Ubuntu website on the functional PC, download the latest version of Ubuntu suitable for the PC on which you intend to reinstall or repair Ubuntu and then use K3b (a burning program) to burn the ISO to disc.

K3b is very much like Nero, a Windows program. 

Alternatively, you could order the free CD.

---

### Post by xpod on 2006-08-24
Thats all i needed to know my friend...im used of using "cd burner xppro"
 and am just starting out with ubunto and kubutno so was`nt sure about iso burning on kubunto.

Im not even sure what i could have done to the ubunto/xp sys?
it just gets to grub loading and says error17 or 21....

All i did was plug a new hd in...go to discs and mounted it at /mnt...Then i switched off to put pc back together,rebooted and got that error?

What i`ll do once i get the iso again is still not too clear but it will be a start......typical,i give my iso away THEN i need it (sods law)

Thanks

---

### Post by xpod on 2006-08-25
Well....it`official...IM A PLANK
I left my kubunto downloading the ubunto ISO last night...Got up this morning only to realise the bloody kubunto pc dosent have cd burning abilitys...mmmmmmmm:rolleyes: 

Plus the connection must have died during the download as the iso was only 515mb or something like that so some of it was obviously missing.

Well ive took the easy option NOW and my mates bringing the original copy of ubunto back later on......Well,i was spreading the "word" after all.

Now when i switch my ubunto/xp on i get
   
       GRUB LOADING stage1.5 read error

So if anybody can give me an idea of what i need to do ONCE i get the live cd later.......I never edited anything or nothing like that..
All i did was insert the new hd,mount it at /mnt in "discs"THEN turned the pc off to put it back together.....I was going to do all the permanent mouting (fstab etc)once i`d rebooted.....

Any ideas for a plank in need folks?

EDIT:the grub manual says to press ctrl-alt-del but that dont do no good 
  
EDIT2:Just found this thread by catlet....is this what i need to do to fix MY prob(dont want to make it worse)?

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Sorry for asking but i have made enough mess here playing about with stuff that i THOUGHT i knew ok but i obviously THOUGHT WRONG...lol

---

### Post by nudnik on 2006-08-25
The "Alternative" install CD gives you the option of reinstalling grub simply. I stopped using the live CDs as they were buggy for a time, and I am unsure whether the problem was ever resolved.

At any rate, good luck with your endeavours, and as for being a plank, we're all a bit wooden from time to time.

:D

---

### Post by xpod on 2006-08-25
Hi......Th](*,) e 4 months i was with windows was the same BUT it was usually infection probs or someother nonsense i`d need to go find some obscure security program for.
Now though it`s mainly just my pc ignorance that puts the stoppers on for me.

It now says GRUB Loading stage 1.5read error.
IM getting the cd i installed ubunto with later on so surely i`ll be able to load it and then do something or edit something to get me back to how i was.

I just dont understand why i got a prob unless the grub changed something automatically after i inserted the new hd.It all worked fine till i rebooted.

NOW would be a good time to "killbill" permanantly but i really do still NEED the xp.......I even tried unplugging the ubunto hd to see if XP would load but i never followed THAT procedure when i first installed so i cant just unplug ubunto.

I`ll wait till pal gets down with cd....I just needed to know that it is all sortable and that i aint killed it all permanantly:confused: ](*,)

EDIT2:Was asking "catlet" about his grub fix tutorial and he says I need to have the drive that "grub" was installed to for his fix to work...
as thats where the grub will be...i.e Ubunto hd
But im not so sure THATS where my grub is....When i first installed ubunto i followed "Aysiu`s" guide but not the one with XP HD unplugged for safety.I fillowed the one with the XP HD still connected SO is`nt that where my grub will be located??Surely i`d be able to still boot XP if i unplugged Ubunto if that was the case.
Unfortunately catlet is away to work so im not sure where i stand at the moment

---

### Post by xpod on 2006-08-25
Just an update in the hope the further info tells a story?
Im still waiting on the live cd getting here but i had gparted on anther cd so put that in to see what it said.All my settings are exactly as they were in the bios when things last worked but gparted says

/dev/hda1(with a little "!" next to it) is my xp and it looks fine...it has "boot,iba" under the flag tab

But when i go look at the small ubunto hd it had../dev/hdb1 unknown 2.86 GiB
                                                  /dev/hdb2 extended 164.73mb
                                                /dev/hdb5 linux swap 164.70mb

It has "boot" under the flag tab on the unknown 2.86gb partition.
That WAS my ext3 partition with the main Ubunto on it so how it is now listed as "unknown" i`ll never know.

ALL i did when i put the new harddrive(hdc) in was select it in "discs" then pessed "format" to make it ext3 and made the mount at /mnt.

I never touched the ubunto hd and i never even mounted the new one permanantly via fstab etc etc.I was going to do all that once id put things back together.So nothing was edited or suchlike.
I NEVER went into gparted and said "change my ubunto partition to "unknown" so how could this happen..

Please help me get out of this mess someone.....Ive read loads of threads and was sitting waiting for the my ubunto live cd to get here from my friend, thinking it was just my grub menu/bootloader(?)that had got messed up with a new "filesystem" being added.But now i sit here and look at the partition tables via gparted it looks like something a bit MORE serious than a simple grub problem,

Even if i have to reinstall ubunto will it RE-find xp and fix whatever grub menu etc it need s to?...I dont have an XP cd to play about with so i need to work entirely from ubunto and/or live cd..........CHEERS PEOPLE

---

### Post by confused57 on 2006-08-25
Are all of your hard drives "enabled" or set to "auto" in your bios?
Jumper settings correct on your hard drives(master, slave, cs)?

You may be able to restore your Windows mbr using this method:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Basically, since you don't have the Windows install cd, maybe you could download the Windows 98SE OEM bootdisk for floppy as described in the above link.  My mistake, I think you'd need Windows to execute the bootdisk file & burn to floppy.

I "believe" if you reinstall Ubuntu, grub will find XP and reinstall to the mbr enabling you to boot XP or Ubuntu.

---

### Post by xpod on 2006-08-25
This gets better...
                Things are exactly as they were and everything is fine in the bios.I never went near any hd`s in "discs" OTHER than the hdc i had just put in.
I messed about with the bios settings(just the boot order ones)after i relised the gub was having probs and i had took the new hd back out.

Now that im looking at the xp hd on the gparted cd it has the same "main" fat32 plus smaller"unallocated" partitions it did before BUT there is no yellow shaded area that usually denotes the space xp is actually taking up.

Im not really fussed about anything BUT how the hell could that possibly be??
Is it just cause things are muddled up OR does that mean XP aint there no more?????
Thats ON TOP of the main ubunto partition now being black and unknown....

Nothing is as it should be but i never done or used anything that could have decided on it`s own to go mess my Ubunto AND XP up.......I know i can get a bit muddled at times but NEVER that bad .All i did was put a new hd in then take it out again

It`s looking grim eh.....:rolleyes:

EDIT:Gparted cd list a BUFFER I/O error on device hda    Logical block..as it starts which is the XP disc so mabey its just not reading it or something?..im just guessing but dont really have a clue:confused:

---

