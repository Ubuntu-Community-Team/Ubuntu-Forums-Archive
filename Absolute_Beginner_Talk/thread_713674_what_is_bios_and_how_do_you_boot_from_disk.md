---
title: "what is bios and how do you boot from disk"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by ebony_vbac on 2008-03-03
i'm having so many problems i have a new os with nothing on it but dos, i got some linux disks from ebay but cant install them i'm trying ubuntu first cuz i hear its the easiest, but not for me.  help!

also how do you pronounce ubuntu???

---

### Post by smartboyathome on 2008-03-03
When your computer boots, before anything else, it should say "Press blah for boot options", press the key and select the disk to boot from the disk, and then it should boot it. Also, ubuntu is traditionally pronounced "oo-boon-too", but I pronounce it "oo-bun-too".

---

### Post by bumanie on 2008-03-03
Bios basically contains all the necessary information (**B**asic **I**nput/**O**utpu **S**ystem) that primes your computer to have everything running in synchronisation prior to the OS being loaded.
To get into bios there is a message on your post screen which will say to press delete or F12 (or some other key) to enter setup. Once you have found that you need to navigate to the boot order and ensure that the primary boot device is cd-rom. Then you should be able to boot the live cd (I'm assuming the disc you have got is a live cd).

---

### Post by zxscooby on 2008-03-03
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

your bios is located in a chip on the main board , it has a program in it that starts your 
computer up, it looks for another program on your hard disk that starts your operating system (linux , windows , etc.) .  

if you are trying to boot from a C.D. but cant then you might have to set your bios to try booting from the C.D. first.  

I suggest using the live C.D. from the link above.

---

### Post by zxscooby on 2008-03-03
yea , what he said :lolflag:

---

### Post by Stef11 on 2008-03-03
When you are in bios look for a title called boot order. It isnt normally on the first screen you see.
Once you have found it change the order to:
Boot of CD ROM first
Then 2nd boot floppy
3rd boot HD 0
This causes the bios to check for a bootable cd first.
regards Stef11

---

### Post by ebony_vbac on 2008-03-03
i know this sounds weird but i dont think i have a bios. when i reboot a screen flashes really quick and it said something about deleting or something. but the main screen just sais microsoft windows 98 and theres the c:/> does it mean anything that it only takes 9 seconds to reboot? that means its totally empty right? and i cant download any versions cuz i have no way to save them i have no cd burner or anything on this old computer, my floppy drive is broken and the new pc doesnt have a floppy that's why i bought these linux cds online

---

### Post by soapytheclown on 2008-03-03
yep that flashy screen is what yr after, pressing delete will take u into your bios menu ;;)

---

### Post by SunnyRabbiera on 2008-03-03
unusual, as you normally get a bios with all computers...
see what pressing f2 does when you turn on your computer, this is what usually brings up the bios editor.
the only time I never seen a bios come up is if the system used a american megatrends bios that sometimes doesnt pop up on load.

---

### Post by Officer Dibble on 2008-03-03
When you say old computer... how old are we talking?

Do you know how much memory this computer has, or what processor?

If the computer is old as in "old", then you may have problems running Ubuntu in its typical form on that computer.

Let us know all you can about this computer please - for example, if it is a branded computer (Dell, Compaq, or HP, etc) then it may well have model name and number.

---

### Post by ebony_vbac on 2008-03-03
its an hp pavillion i think. i bought it from compusa when they went out of business. it was a fixtures item, i think they used it in their office or something.  it didnt come in a box or anything how do i find out the ram and proccessor info? when i type dir it says how much memory is available, let me doublecheck

---

### Post by Dieselguts on 2008-03-03
just insert he disk and restart or compuer and it should auomaically start the cd

---

### Post by soapytheclown on 2008-03-03
did you try pressing delete as soon as the pc boots? ....

---

### Post by ebony_vbac on 2008-03-03
that doesnt work

---

### Post by ebony_vbac on 2008-03-03
yeah in that 9 seconds i have i pressed it once and a bunch of tymes

this is what it says when i type dir

volumn in drive c has no label
volume serial number .....
directory of c:\

command com 93,890 4-23-99 10:22
1 files 93,890 bytes
0 dirs 39,057.67 mb free

so i guess it's a least 8 years old? althogh i thought it was newer than that

---

### Post by SunnyRabbiera on 2008-03-03
like I said give F2 a shot when booting

---

### Post by jviscosi on 2008-03-03
Different systems have different keys for getting into the BIOS; it's not necessarily DELETE.  I've seen function keys used fairly often for this, so try those, especially F1, F2, F3, and F10.

It's possible they did something to the machine to prevent users from getting into the BIOS.  If that's the case, you might need to open it up and find a jumper on the motherboard for resetting the BIOS.  If you're lucky the inside of the computer will have a map of the motherboard showing if there's such a jumper and where it is.  (It's a tower, right?)

All that dir is showing you is that the version of command.com is from 1999.  That doesn't mean the computer is that old; they might've wiped it and installed some old OS on it.  The machine itself could be newer.

---

### Post by ebony_vbac on 2008-03-03
i pressed f2 while it was booting and it looked in the cd drive and made noise like it was using the cd drive but i guess it didnt find what itwas looking for cuz it went to the floppy drive and didnt find anything there then it went to dos c:\> it must be my disk, i'm going to try another one. i hope they arent all bad

---

### Post by ebony_vbac on 2008-03-03
now im getting all different kinds of results.  one time i put 2 disks in and it said i couldnt boot from that disk and needed cd2 or to change the bios but it didnt say how to do this, i noticed fedora is a dvd and ubuntu and pc07 are cdroms so i put them in the correct drives and with pc07 i got just the regular dos with the fedora i now have a blinking cursor in the left top corner but no prompt and noway to imput anything

---

### Post by Jerry N on 2008-03-03
If this was an office system, they probably had the BIOS password protected and probably also removed everything but a minimal DOS from the HD.  You might have to clear the BIOS RAM either with a jumper change or by removing the battery for several minutes.  If you don't know much about the innards of computers you should probably find yourself a guru to show you how that stuff is done.

Jerry

---

