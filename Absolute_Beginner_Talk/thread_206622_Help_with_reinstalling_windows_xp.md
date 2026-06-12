---
title: "Help with reinstalling windows xp"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Dav0087 on 2006-06-30
hello i have just installed ubuntu about two days ago and i liked it, but it wasnt for me. i told a few friends who were more into that stuff and liked it. but i would like to switch back to windows xp. but when i put in a manufacterers cd recovery tool cd that came with my computer, it erased my drives and installed windows back. but when i restarted my computer the grub loader showed up and gave me an error 71. i didnt partition my drive when installing ubuntu, but instead it erased everything and installed ubuntu. is there a way to fully get back windows xp? thank you for your help.

---

### Post by jrattner on 2006-06-30
One method, but by no means the best would be to make a windows boot floppy disk.  Include the program fdisk.exe on it.

Then run the following command:
```
fdisk mbr 
```

This will remove grub, and assuming you have windows installed now, it will now boot properly.

---

### Post by Dav0087 on 2006-06-30
i dont have a floppy drive on my laptop. is there another way to do it. and i am sorry fo being a complete newb

---

### Post by raptros-v76 on 2006-06-30
do you have a copy of windows? if not, youll need either quite a bit of money, or an illegal copy. do you still have the recover disks from when you bought the computer? use those

[EDIT] I see you already did that... instead of using a floppy, get a windows bootable CD

---

### Post by Dav0087 on 2006-06-30
yes i have the recovery disk, but when i start it. it works and installs windows back, but when i restart the computer the grub shows up and gives me an error and nothing starts. what should i do?

---

### Post by raptros-v76 on 2006-06-30
...wait. WHAT? it didnt remove the grub?  installing windows always gets rid of the grub!

---

### Post by Dalai Calama on 2006-06-30
Try booting from your recovery disc, and going to the Recovery Console (press R, IIRC). There, try using the commands fixboot, and fixmbr.

Not sure, but might help...

---

### Post by Dav0087 on 2006-06-30
it didnt , it just gives me error 71 and nothing happens. everytime i restart the computer it gives me the same thing

---

### Post by Dav0087 on 2006-06-30
thanks ill give it a try , but are there any more helpful ideas? this community is the best with help:D

---

### Post by raptros-v76 on 2006-06-30
i dont remember anything from windows, sorry i cant help

---

### Post by ravenproject_two on 2006-06-30
[QUOTE=Dav0087]hello i have just installed ubuntu about two days ago and i liked it, but it wasnt for me. i told a few friends who were more into that stuff and liked it. but i would like to switch back to windows xp. but when i put in a manufacterers cd recovery tool cd that came with my computer, it erased my drives and installed windows back. but when i restarted my computer the grub loader showed up and gave me an error 71. i didnt partition my drive when installing ubuntu, but instead it erased everything and installed ubuntu. is there a way to fully get back windows xp? thank you for your help.[/QUOTE]

I can tell you what I did that worked for me-I am a real newbie too and screwed up aa fedora installationa couple of days ago.  My windows xp home would not boot from cd....so I figured I was screwed right because the Linux installation was not finished when it crashed (The burned ISO wasn't complete-thanks fedora)...I was p'd man 'cos I thought-there goes like a 100 bucks to get xp from the store (I have the xp home upgrade cd)  but what I did was put in a windows '98 cd...I booted the cd and paritoned/reformatted/went through the install alll the way until it asked me for my license key (Which I did not have 'cos I lost docs for that dinosaur long ago.)  At the License key screen I turned my cpu off manually, waited a few, turned it back on, inserted my xp upgrade cd and booted from that-because windows 98 had changed the boot loader; it worked....I am a cpu moron though-I am 24 and have been using cpus for four months and just installed ubuntu (My first Linux that worked) two days ago...not my place to say but I said screw windows and dual boot-I am staying single boot Linux so that I have to learn it ride or die!!!  Hope that helps-sorry if I am stupid and can't help....The RavenProjectO:) ****

---

### Post by Dav0087 on 2006-06-30
thats all right. i really appreciate you taking the time to help

---

### Post by raptros-v76 on 2006-06-30
what you probably dont want to have to do is pay for a futching expensive new xp disk

---

### Post by Dav0087 on 2006-06-30
i know, that is my last option if i cant get it to work. but if i do buy a new windows xp cd, will it fix this problem it if install it?

---

### Post by raptros-v76 on 2006-06-30
it will fix it. it will get rid of the grub. it will cost more than 500 dollars

---

### Post by ravenproject_two on 2006-06-30
[QUOTE=Dav0087]hello i have just installed ubuntu about two days ago and i liked it, but it wasnt for me. i told a few friends who were more into that stuff and liked it. but i would like to switch back to windows xp. but when i put in a manufacterers cd recovery tool cd that came with my computer, it erased my drives and installed windows back. but when i restarted my computer the grub loader showed up and gave me an error 71. i didnt partition my drive when installing ubuntu, but instead it erased everything and installed ubuntu. is there a way to fully get back windows xp? thank you for your help.[/QUOTE]

[B]This is what I did when my fedora installation screwed up and I was left with a partial nstall...I am a dummy though-got ubuntu two days agoo and have only used cpus for four months...Do you have an older copy of Windows?  I took the Win '988 installation cd (Because my xp was only a home edition upgrade cd-not the actual new install...I took'98 and re-partioned over Linux Completely, redormatted, ran the installation through all the way until it prompted me for the License key-the I shut my cpu off manualy and restarted with my xp home upgrade in the drive-it booted from cd and started the win xp home install process...I reformatted/repartioned and installed xp home-as soon as I had xp again I went and got a ubuntu live cd and haven;t needed win yet...Hope I helped but I am just a dummy-only been learnng for months...Good Luck-I wish everyone on these awesome forums the best-you are all awesome poeple
_The Raven ProjectO:) [/B]

---

### Post by Dav0087 on 2006-06-30
damn thats alot of money for something i already have. does anybody have other tips? i would really appreciate it.

---

### Post by Dav0087 on 2006-06-30
no i dont have an older copy. just the recovery disk that came with my laptop, and no your not a dummy. everyone makes mistakes. i have made quite a few in my life

---

### Post by ravenproject_two on 2006-06-30
Sorry I couldn't help-and I am sorry I posted twice buddy Imy first one didn't show up-do you ahave a friend you can obtain an older win '98 full install cd from and do it that way?

---

### Post by Dav0087 on 2006-06-30
i could probably get one, but if do install windows 98, will i be able to upgrade back to xp with my recovery cd?

---

### Post by raptros-v76 on 2006-06-30
...not really. basically youll just wipe the disk again, but grub wont mess you up

---

### Post by mevan on 2006-06-30
I had the same problem, and it did not get solved till I repartitioned my hard disk with a utility from the disk's manufacturer (Seagate seatools)... And I had a genuine XP Pro disk!

---

### Post by Dav0087 on 2006-06-30
really what did you do?

---

### Post by Apple 101 on 2006-07-01
What kind of Recovery Disk is it?  To solve the floppy disk problem, I created a boot CD with the Windows 98SE startup disk on it, and added an NTFS partition reader.

---

### Post by Just4 on 2006-07-01
One thing that would most definately work to erase the GRUB menu is to download Dariks Boot and Nuke and zero-out the drive. [http://dban.sourceforge.net/](http://dban.sourceforge.net/) - And as people have asked before, what kind of restore discs are they?

---

### Post by Herman on 2006-07-01
Wait, before you do anything potentially destructive, try downloading yourself a copy of GAG Boot Manager, it's free, only a small download, and will boot Windows. It runs from from a CD or floppy disk, and you can also install it to your MBR from the CD or floppy and overwrite your MBR with it whenever you are ready.
Heres's a How-To on GAG Boot Manager, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm")
And this is GAG's homepage, where you can download GAG Boot Manager, [*Click Here.*]("http://gag.sourceforge.net/")
Regards, Herman :D

---

### Post by Dav0087 on 2006-07-01
i really want to thank you guys for all your help. the recovery disk i have is labeled toshiba recovery and applications/drivers DVD

---

