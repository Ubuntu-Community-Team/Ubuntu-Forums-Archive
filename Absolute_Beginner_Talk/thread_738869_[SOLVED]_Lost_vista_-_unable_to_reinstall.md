---
title: "[SOLVED] Lost vista - unable to reinstall?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by beckym@cincoed on 2008-03-29
oK so i did something VERY stupid and just assumed ubuntu would auto install for dual booting. my own fault then when it nuked vista and everything on my hard drive (bad times). however i did do a backup (good times) before i proceeded to delete the last 12 months of my life. 

so i used ubuntu LIveCD (gnome partition manager) and partitioned the drive. i booted into vista but it wouldn't reformat as ntfs, so i did this in Ubuntu LiveCD / gnome pm.  however, vista still won't reinstall - it sees the ntfs drive but when i try to install vista on it it says "Windows is unable to find a system volume that meets its criteria for installation". It is formatted as ntfs, size 73.8GB and type is primary - where am i going wrong? 

anybody who can help will be sooooooooooooo appreciated by me :)

---

### Post by mrpixels0 on 2008-03-29
Hi there BeckyM,

The only way I would do it would be to use a bootable windows CD/DVD of Vista and let its partion tools do all the work, basicly do a clean Vista install and whens that done, then boot a live cd install of Ubuntu and choose Manual at the prompt and resize the partion to the size you want and continue from there.

Sorry if that is not what you were looking for in the way of Info but windows must be in control from start to finish before Linux can install along side of it.


MP0

Note: if Windows Vista does not want to do this, you can use a copy of Freedos, from [www.Freedos.org](www.Freedos.org) to remove the Existing partions and make the whole drive Fat32 and just format it and leave it blank, then vista should have no problems converting that to it's version of NTFS.

---

### Post by beckym@cincoed on 2008-03-29
i have a vista reinstallation cd that came with my computer - is this the same thing - i would like to do a clean install using windows partitioning tools but i don't know how to do it - at the moment i am turning machine on - pressing f12 and booting into cd-rom then trying to do a vista install. it lets me choose my region, accept terms and conditions then gives me a screen where i choose which partition to put it on to - i choose the ntfs partition but get the error message i outlined above ...... i'm stuck ?????? and desperate to access the files i have sitting on my backup cds!

---

### Post by mrpixels0 on 2008-03-29
sounds like a special OEM version supplied by DELL or Comapq ect, so here is my solution to that:

1. use the partioning tools from ubuntu's live installer and make the windows partition fat32
2. after Ubuntu writes the changes to disk, hit the computers reset button and remove the ubuntu cd
3. put in the vista disk and reboot with that, it should see the Fat32 partition and install to that.

Note: NTFS Formats that linux uses are Slightly Diffrent from what Vista Expects so it wont work the same, No matter what anyone tells you.

---

### Post by beckym@cincoed on 2008-03-29
:-( i did that already and it didn't work :( thankyou for the suggestion though (and by the way, yes its a dell cd).  i am in the process of downloading freedos as you suggested - will it be pretty straightforward once i've installed that to unpartion and reformat?

---

### Post by mrpixels0 on 2008-03-29
Once you have freedos burned to a cd you can run it from the cd without installing it :), once there choose the option to run from cd command line.

Then type Fdisk and choose large disk support press enter
then you will see a menu from there choose the windows partion and give it a "true" fat32 partition
when thats done. press esc to exit the fdisk program. and reboot Freedos cd again as before run it from the cd. then this time from the command line type Format C: and tell it yes when it asks
when it is done, pull out freedos cd and reboot with Vista cd.

and that should work, if not the only fix is a Bestbuy near you could do it for about $50.00 a lot of money I know but worth it in the long run. If you lived near me I could just come over and fix it but I live in kansas  :) too far away.

let me know how it goes.

MP0

---

### Post by beckym@cincoed on 2008-03-29
thankyou so much for your help - i'll come back and tell you how i got on.....

---

### Post by mrpixels0 on 2008-03-29
no problem just wanted to help out a fellow user thats all :)i, I will look for a reply in a little while, got to get some sleep,  I work today at 2:00 PM, I will check the forums then. I hope you can get your Machine back in order soon good luck.

MP0

---

### Post by beckym@cincoed on 2008-03-29
Ok, so i get into fdisk, i choose large disk support then i get a menu which tells me the following and gives the following options (disk ddrive i is linux by the way):


Current fixed disk drive : 1

choose from following:

1. Create DOS partition or logical DOS drive
2. Set active partition
3. delete partition or logical DOS drive
4. display partition imformation




not sure what to choose?

---

### Post by jwalters on 2008-03-29
becky I did the same thing............I erased the whole drive unknowingly  and then tried to reinstall Vista with the Dell disc. There are (I believe) small partitions containing Vista code that allows Vista to reinstall. I erased them also,

 so (I'm guessing) you may need to get hold of a complete Vista OS in order to get it back ($$$$) on your computer.

I just went full bore Ubuntu and said the hell with windows all together..........had my writings on an exterior HD backup.

---

### Post by Sef on 2008-03-29
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by mrpixels0 on 2008-03-29
Hey there BeckyM

If Jwalters is correct and from talking to other people he most certainly is :(, then he is right you may have to buy a copy of Vista that is not tied to the machine. See the instructions I gave you work great for Reinstalling an XP OS, so I figured they would work as well for doing a Vista Install as well  :( sorry for getting you more lost than ever, However Self's Link to the test Disk looks very promiseing and could possibly help but there is no sure fix for this.

you see when you start mucking about with the partition tables data gets erased and rewritten numerous times in random places and sometimes data is not recoverable in all cases so again you maybe stuck at needing to buy a Vista OS disk or have DELL do a Complete Install for you that would be Cheaper in the long run (more so then buying Vista) but would Fix the problem either way.

Well I had better get back to work before i get in to trouble :), I will check back after work.

MP0

---

### Post by beckym@cincoed on 2008-03-30
thankyou so much for your advice - i eventually did it by by taking out both partitions using Ubunutu LiveCD and reformatting the whole drive as FAT32 (vista wouldn't even accept being the primary drive it wanted the whole thing before it would install!) - i then booted into vista installation and got vista to reformat the partition as ntfs, as soon as it had done this it happily installed itself. Now its back to getting ubuntu back on there, preferably without nuking vista this time :)

BTW sorry for posting this solution twice but i wanted to update the people who had helped me :)

---

### Post by mrpixels0 on 2008-03-30
Hey there BeckyM,

I am glad that you were able to get it back in order :), and now you know what to do next time ;) (hopefully there wont be a next time) and welcome to the wonderful world of open source freedoms ! :).


MP0

---

