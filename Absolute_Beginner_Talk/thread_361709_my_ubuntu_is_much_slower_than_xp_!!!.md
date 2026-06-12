---
title: "my ubuntu is much slower than xp !!!"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-02-14
After I updated BIOS, windows is amazingly speedy. Firefox surfing is so quick that almost I get pages instantly as I click. opening files also, the system refreshed itself as if I bought the computer yesterday!

ubuntu is really slow!!! Even opening files. For example open office. The worst is pdf opening with adobe. I tried opening with native pdf viewers but it did not change much.

Do you have any idea why ubuntu is so slow compared to xp. I expect at least almost the same. 

thanks in advance
findik

---

### Post by Daveski on 2007-02-14
> **findik1 said:**
> After I updated BIOS, windows is amazingly speedy. Firefox surfing is so quick that almost I get pages instantly as I click. opening files also, the system refreshed itself as if I bought the computer yesterday!

What is the machine, and do you know what the BIOS bugfix/update was?

---

### Post by oilchangeguy on 2007-02-14
please advise your machines specs, ubuntu version, xp version.

---

### Post by Mba7eth on 2007-02-14
I really agree on that !!! 
Espceially the jvm . It is really really slow compared to java !!

---

### Post by Mba7eth on 2007-02-14
ok take me also .... 
Xp sp2, Ubuntu 6.10 .....
CPU 2.4 core2(4MB cache), MSI 975mx motherboard, 2 GB ram, 7300gt nvidia, FSB 1066, 
Please guys how can i speed up ?

---

### Post by findik1 on 2007-02-15
sorry being late to answer back but my internet connection was down...

To Daveski:

my machine is ibm thinkpad t60 laptop, dual boot with xp. so the same harware specs for both operating system.

BIOS update was the most recent one. I found out on ibm webpage. I did 2 weeks ago or so

---

### Post by findik1 on 2007-02-15
> **oilchangeguy said:**
> please advise your machines specs, ubuntu version, xp version.

ubuntu edgy, I installed last updates from ubuntu. xp is xp professional. I have not been using xp for a month, so trying to switch all to ubuntu. But when I used xp this week, it was amazingly speedy, as if trying to say stg :)

---

### Post by findik1 on 2007-02-15
I re tested, it took 16 sec to open a pdf file. My laptop specs, system monitor says: 

used memory 344 of 494.7mb.
used swap 243 of 635.3 mb 

it is a 1.66 GHz notebook.

any idea???

---

### Post by maddog39 on 2007-02-15
findik1: to me that looks like there is a bad spot on your RAM and since Ubuntu/Linux cant write there it resorts to the hard drive (swap) for memory. But I'm not totally sure about that, I may be wrong.

---

### Post by findik1 on 2007-02-15
do you think it is because of ubuntu system updates that ubuntu asks to install each time you login? 

win xp was also speedy when I bought the laptop but with time it degraded. After I moved most of the files to ubuntu and bios update, now xp is much more speedier than ubuntu.
best
findik

---

### Post by tronica on 2007-02-15
pop in your ubuntu install disc, and at the boot option menu run the memory test.

---

### Post by findik1 on 2007-02-15
> **maddog39 said:**
> findik1: to me that looks like there is a bad spot on your RAM and since Ubuntu/Linux cant write there it resorts to the hard drive (swap) for memory. But I'm not totally sure about that, I may be wrong.

maddog39: yes not having 512 mb ram made me suspicious too. but it was also same in xp too, when I originally bought the laptop.

---

### Post by Daveski on 2007-02-15
> **findik1 said:**
> my machine is ibm thinkpad t60 laptop, dual boot with xp. so the same harware specs for both operating system.

BIOS update was the most recent one. I found out on ibm webpage. I did 2 weeks ago or so

They don't say what the

[I]<2.09>
 - (New) Support Microsoft Windows Vista[/I]

actually does.
Is everything slow, or specifically loading apps, or internet browsing etc.?

---

### Post by dcstar on 2007-02-15
Do a forum search for "disable ipv6" and implement to recommended changes.

---

### Post by ERSchrager on 2007-02-15
After reading your post, I ran my own tests in XP and Ubuntu 6.10.  Under XP, the file took 5 seconds to load the first time, after that it took 1-2 seconds on reloads.  Under Ubuntu, it took 3 seconds every time using Evince Viewer.  

I would suspect that with the odd number you are showing for RAM, that you might have a memory problem, and XP is just handling it better.  Another possibility is that the difference in Ram is being used by your system for something else, BIOS acceleration possibly?  Again, XP may just be handling your system better.

Maybe your laptop just need some tweaking.  Check the Tips and Tutorials Forum for performance tweaks.

Roger

---

### Post by findik1 on 2007-02-15
> **tronica said:**
> pop in your ubuntu install disc, and at the boot option menu run the memory test.

I did Memtest86 from grub menu

it gave Memory 502 M  
Block move, 64 moves
No errors
Pass 1


I will also follow the other treads as suggested and will let you know the outcome

---

### Post by riggits on 2007-02-16
just a guess, you mentioned moving a bunch of files from your XP partition to Ubuntu?
could be that XP was horribly fragmented, and now your Ubuntu partition is too full.  
how much space do you have on your disks.

---

### Post by gigaferz on 2007-02-16
I installed ubuntu  and then kubuntu on an used harddrive i got for $18.

The first month with ubuntu went well, then later its started slowing down. like an windows machine loaded with crapware,slow boot times , some freezing, slow.

I reinstalled evrything again, this time I went kubuntu. and after 2 or 3 days it was taking forever to boot , like 8 minutes, while both xp I use boot in a minute, and a kubuntu in a 80mhz boots in a minute too (well maybe a li more), 

anyway, I noticed  after a weekend , the next monday, I turn the computer and try kubuntu, It loads super fast, all the apps, files, media are in turbo mode , but for the rest of the week i dont really feel like waiting 10 minutes to boot kubuntu.

After all this I think its the hard drive.

But also might be some hardware in the machine because ,the computer iw working all day (I had to go back to windows for the printing capabilities), and in my lunch break I try to boot kubuntu and it takes forever in loading restricted drivers.....  Even when I have not used the linux hard drive at all.... so it can be something else, its rare, every monday after the weekend runs fast, then  during the week, it s performance is extremely poor.

anyway, it could be your hard drive or soem other hardware.

I dnt think its software related (but the again Ive been using linux for 6 mothd only)

---

### Post by findik1 on 2007-02-16
> **riggits said:**
> just a guess, you mentioned moving a bunch of files from your XP partition to Ubuntu?
could be that XP was horribly fragmented, and now your Ubuntu partition is too full.  
how much space do you have on your disks.

To riggits: yes ubuntu partition is almost full but still there is ~5GB space. See the attachment

---

### Post by findik1 on 2007-02-16
to gigaferz:

my ubuntu boot is pretty OK and booting time is stable.

But I also see that if ubuntu is on for a long time, then program speed slows. If you reboot it it seems like ubuntu refreshes itself and it seems the programs get more speedy.

---

### Post by findik1 on 2007-02-16
> **dcstar said:**
> Do a forum search for "disable ipv6" and implement to recommended changes.

dcstar: indeed it speed it up the internet (firefox) enermously! Everybody should try, thanks.

However, on the gnome, the issue is somewhat different. For example if you want to close  a program, say .pdf file, it is so slow that they system send out "Force to kill" sign, thinking there is stg wrong with the program. But if you wait enough .pdf closes by itself, only the program is so slow to close it (or open it). So I am not sure whether it is related to ipv6 issue. I need more testing, then come back

---

### Post by hoctro on 2007-02-20
I have duo boot of XP and ubuntu, Well Ubuntu still quite fast.
If you update the BIOS then try reinstall Ubuntu 6.10 then the speed can be faster.
gl

---

### Post by jvc26 on 2007-02-20
I'm not honestly sure why its being slow compared to XP. My Ubuntu install hasnt slowed down at all in about 4-5 months of constant use, so I'm not sure why yours is - it may well either be RAM, or it could be a problem with having an increasingly full harddrive.
Il

---

