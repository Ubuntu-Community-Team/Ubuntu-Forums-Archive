---
title: "Man WTF?"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by Substance on 2005-08-04
heres my situation :(

My Spects are here for reference btw
[SIZE=1]**Mobo:** ASUS P4C800-E Deluxe Rev 2.0 (1022) :shades: 
**CPU:** Intel Pentium 4 3.2CGHZ 800FSB  
**Memory:** 1GB GamerPro DDR400 CL 2-2-2
**Storage:** 2x SATA 200GB Seagate Hardrive
**Storage:** 1 x EIDE  160GB Seagate Hardrive
**Storage:** 1 x EIDE  80GB Western Digital Hardrive
**Videocard:**Powercolor Radeon 9800SE @Pro
**Power:** Thermaltake 420Watt Powersupply (soon to be 500watts)
**OS:**Windows XP Professional w/SP2 Soon to be Dual Boot with Ubuntu :)
[/SIZE]

i have 2 200GB's SATA Seagate hardrives )seen as 187.99gb's in windows on 1 of my SATA Windows is There..
my other 200Gb sata is a storage drive it has some maps(ut2k4, cs:S) and porn ( im not going to lie lol: "naughty  [-X "

anyways i also have 2 backup drives i 160GB IDE Seagate Hardrive (<--my anime episodes are here :) naruto/bleach from 1-present at the moment anyways!!)

i also have 1 80GB Maxtor Hardrive, but its partitioned into 2 40GB's hardrives, i left 1 partition for Fedora 4, (plan on switching to ubuntu, but if FC4 wont work then whats the point right ) and my other partition has important files such as Documents and .psd's for photoshop. ive already back up these files to my 200GB drive but i also copied them back ok in the install of fedora i set everything up fine, but i specified it not to install to my SATA's MBR but to the linux drive in the first bootsector. Anyways i want to dual boot between XP and Linux i followed a tutorial about using M$ bootloader to boot both XP and Linux and i believe ive done everything correct

i used the rescue CD to boot into linux (didnt boot just got a command prompt) 
i typed: "grub-install /dev/hdc2/", then i typed dd if=/dev/hdc2 of=fc4boot.bin bs=512 count=1" ok it created the bin, but i was in a sitiution and couldnt copy the file over to another hardrive because all of my other paritions are NTFS. ok anyways i used my domain to upload the .bin by FTP and then i rebooted got into XP ok saved the bin to my C:\ and then added c:\fc4boot.bin="Fedora Core 4" to my boot.ini rebooted and wala the menu came up.I seleted Fedora Core 4 and all i got was this
[PHP]
GRUB _[/PHP]

im at a loss now, im not sure if its because i have 2 x SATA and then 2 x IDE or maybe i just have to many damn hardrives and its confusing Fedora Core's installer  =/ and seeing how alot of you guy's are knowledgeble and when i switch over to Ubuntu if i can ever this to work i might need more help so i decided to post here  :roll: oh yea when are my ubuntu cds' coming!! using ubuntu live was a thrill also but slow to boot (could have been my cd )

also i have a question for those who burn with Nero Burning Rom. do i select Track At Once or Disc-At-Once when burning .iso's?

---

### Post by Substance on 2005-08-04
[QUOTE=Substance]heres my situation :(

My Spects are here for reference btw
[SIZE=1]**Mobo:** ASUS P4C800-E Deluxe Rev 2.0 (1022) :shades: 
**CPU:** Intel Pentium 4 3.2CGHZ 800FSB  
**Memory:** 1GB GamerPro DDR400 CL 2-2-2
**Storage:** 2x SATA 200GB Seagate Hardrive
**Storage:** 1 x EIDE  160GB Seagate Hardrive
**Storage:** 1 x EIDE  80GB Western Digital Hardrive
**Videocard:**Powercolor Radeon 9800SE @Pro
**Power:** Thermaltake 420Watt Powersupply (soon to be 500watts)
**OS:**Windows XP Professional w/SP2 Soon to be Dual Boot with Ubuntu :)
[/SIZE]

i have 2 200GB's SATA Seagate hardrives )seen as 187.99gb's in windows on 1 of my SATA Windows is There..
my other 200Gb sata is a storage drive it has some maps(ut2k4, cs:S) and porn ( im not going to lie lol: "naughty  [-X "

anyways i also have 2 backup drives i 160GB IDE Seagate Hardrive (<--my anime episodes are here :) naruto/bleach from 1-present at the moment anyways!!)

i also have 1 80GB Maxtor Hardrive, but its partitioned into 2 40GB's hardrives, i left 1 partition for Fedora 4, (plan on switching to ubuntu, but if FC4 wont work then whats the point right ) and my other partition has important files such as Documents and .psd's for photoshop. ive already back up these files to my 200GB drive but i also copied them back ok in the install of fedora i set everything up fine, but i specified it not to install to my SATA's MBR but to the linux drive in the first bootsector. Anyways i want to dual boot between XP and Linux i followed a tutorial about using M$ bootloader to boot both XP and Linux and i believe ive done everything correct

i used the rescue CD to boot into linux (didnt boot just got a command prompt) 
i typed: "grub-install /dev/hdc2/", then i typed dd if=/dev/hdc2 of=fc4boot.bin bs=512 count=1" ok it created the bin, but i was in a sitiution and couldnt copy the file over to another hardrive because all of my other paritions are NTFS. ok anyways i used my domain to upload the .bin by FTP and then i rebooted got into XP ok saved the bin to my C:\ and then added c:\fc4boot.bin="Fedora Core 4" to my boot.ini rebooted and wala the menu came up.I seleted Fedora Core 4 and all i got was this
[PHP]
GRUB _[/PHP]

im at a loss now, im not sure if its because i have 2 x SATA and then 2 x IDE or maybe i just have to many damn hardrives and its confusing Fedora Core's installer  =/ and seeing how alot of you guy's are knowledgeble and when i switch over to Ubuntu if i can ever this to work i might need more help so i decided to post here  :roll: oh yea when are my ubuntu cds' coming!! using ubuntu live was a thrill also but slow to boot (could have been my cd )

also i have a question for those who burn with Nero Burning Rom. do i select Track At Once or Disc-At-Once when burning .iso's?[/QUOTE]
 BUUUUUUUUM
P

---

### Post by Knome_fan on 2005-08-04
Well I never tried to use the MS bootloader to dual boot exactly because it is known to be a major PITA.
I think the easiest way would be to simply use Grub for both Windows and Fedora. If you for some reason want to get rid of grub again, you just need to boot from your windows CD, enter Rescue mode (I think that's what it's called) and run fixmbr from there. This should give you back your windows bootloader. (Don't absolutely rely on me here, I didn't do this for a long time now, it's probably best to ask google if this is right)

Hope this helps.  :grin:

---

### Post by Substance on 2005-08-04
[QUOTE=Knome_fan]Well I never tried to use the MS bootloader to dual boot exactly because it is known to be a major PITA.
I think the easiest way would be to simply use Grub for both Windows and Fedora. If you for some reason want to get rid of grub again, you just need to boot from your windows CD, enter Rescue mode (I think that's what it's called) and run fixmbr from there. This should give you back your windows bootloader. (Don't absolutely rely on me here, I didn't do this for a long time now, it's probably best to ask google if this is right)

Hope this helps.  :grin:[/QUOTE]

Thanks man, i was just worried about using GRUB because.... i did use google.com and search for an answer :( but i kept getting results that showed "OMFG i installed GRUB to my Windows MBR and i cant boot Windows or Fedora anymore!!! what am i to do" or the oh so popular i tried Fixmbr and it wont work wtf do i need to format"

Speaking of Formatting do i have to make a parition on my Windows Drive so GRUB has a place to install ?!!? if so wouldnt resizing a partition thats being used and has information on it a sure way to Corrupt important windows .dlls and files 

Thanks For an Answer \\:D/

---

### Post by Knome_fan on 2005-08-04
No, you don't need to make an extra partition for Grub, it will simply be installed in the MBR. I'd suggest just following the Fedora Installer, it's pretty streight forward and in my experience works well.

That said, it's of course always a good idea to back up your important data before installing a new OS, and by important data I don't really mean your porn (though that of course depends  on how important it actually is to you) ;-) , but things that really might get you in trouble if you loose them.

Have fun!  :grin:

---

### Post by Substance on 2005-08-04
[QUOTE=Knome_fan]No, you don't need to make an extra partition for Grub, it will simply be installed in the MBR. I'd suggest just following the Fedora Installer, it's pretty streight forward and in my experience works well.

That said, it's of course always a good idea to back up your important data before installing a new OS, and by important data I don't really mean your porn (though that of course depends  on how important it actually is to you) ;-) , but things that really might get you in trouble if you loose them.

Have fun!  :grin:[/QUOTE]

I lack DVD's and CD's to burn anything at the moment, but i would like to know do you know any good programs that can Backup a Hardrive to a .iso so i can put it on one of my backup hardrives?

I tried Copying and Pasting lol but that seems dumb seeing how i have alot of hidden files and folders. Nero however has a Backup utility but when i select hardrive it wants me to burn to DVD. bah Once again Thanks  :grin:

Edit: BTW, i have 4 hardrives like stated but it doesnt see my SATA as Primary only the IDE drives are primary so even if i install grub to my SATA/XP mbr would that even matter wooooot if this works ill just Boot up ubuntu and install over fedora core ubuntu is growing so fast and i want to be a part of that  \\:D/

---

### Post by Knome_fan on 2005-08-04
Well, from personal experience I'd always recommend to use CDs/DVDs to backup your important stuff. That way it's off your computer, so if anything goes wrong, or your harddrives fail, or the computer suddenly bursts into flames, you'll at least have your data. So if there's any chance of getting some CDs/DVDs to back up your stuff, I'd suggest to get them.

Sorry, I don't use Windows very often, so I can't really recommend a good backup utility, however searching on tucows.com I'm sure you'll find something.

I also don't have any SATA drives and I don't have Fedora, so I can't really tell you if Fedora and SATA are in anyway problematic.
Maybe do a search or ask on [http://fedoraforum.org/](http://fedoraforum.org/), I'm sure they'll be able to help you out there.

Have fun!  :grin:

---

### Post by Substance on 2005-08-04
Yea, ive been posting there admins keep removing my threads :(

---

### Post by Knome_fan on 2005-08-04
[QUOTE=Substance]Yea, ive been posting there admins keep removing my threads :([/QUOTE]

Huh? I'm sure there is a misunderstanding or something. Are you sure they didn't simply move your thread to a different section for example?
Also, did you try to contact them and ask what was wrong?

---

### Post by Substance on 2005-08-04
[QUOTE=Knome_fan]Huh? I'm sure there is a misunderstanding or something. Are you sure they didn't simply move your thread to a different section for example?
Also, did you try to contact them and ask what was wrong?[/QUOTE]

yep, i guess its because i kept spamming my own thread (eheheehe no one answered so i kept posting my message in the same thread though) Guess it was a  [-X  [-X no no


Bah screw it im installing ubuntu now. \\:D/

---

