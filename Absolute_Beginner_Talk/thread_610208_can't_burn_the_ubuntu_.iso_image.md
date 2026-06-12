---
title: "can't burn the ubuntu .iso image"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by lucamario on 2007-11-11
i tried to look up to some similar threads, but i couldn't find any similar case, so i hope i'm not doing something wrong. else, i'm really sorry.
anyway, i tried to burn the ubuntu image. but once i'm done with the burning process, following all of the steps indicated by a guide found on this website, i try to look at the cd icon and i can't see anything. so i try to open it and i find it empty.. nothing has been burned on it. somebody knows what happened??
thank you

---

### Post by rudeboyskunk on 2007-11-11
It is highly possible that the cd is damaged (yes, even if it is brand new!).  If you get a message while burning near the end that says something like "cannot fixate cd" or something along those lines, the cd is damaged.

---

### Post by antmenj on 2007-11-11
Ok...

Tell us what operating system and burning program you are useing.:)

---

### Post by lucamario on 2007-11-11
i don't receive any strange message.. during the process.. everything seems fine. anyway, i have XP and as program i use infrarecorder.

---

### Post by SunnyRabbiera on 2007-11-11
if its windows and you are just burning it straight off then its no wonder.
by default windows restricts burning iso's.
if you need a free program that can burn your iso semi decently there is burn4free though it has a lot of added on nonsense.

---

### Post by rudeboyskunk on 2007-11-11
or you can try temporarily installing nero burning rom, though it will take awhile to install and is a big hassle.  but it will burn *.iso files just fine.  Make sure when you burn you select "burn as iso" or "burn as cd image," otherwise it will not burn correctly.  If you cannot figure it out, ask someone who has done it before to show you.

---

### Post by lucamario on 2007-11-11
ok.. i'll try using nero burning rom. i have it so it's not going to take a long time.. i'll let you know if it works.. thank you by now!

---

### Post by gn2 on 2007-11-11
I've used this free utility many times and never had a coaster yet: [http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by oilchangeguy on 2007-11-11
and please read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Iceni on 2007-11-11
I tried to burn with infrarecorder recently and as far as I could tell it can't handle iso files:(

---

### Post by lucamario on 2007-11-11
i read it, and i tried doing exactly what it said and i still got nowhere..
i'm almost done with the nero burning process.. we'll see

---

### Post by lucamario on 2007-11-11
ok.. new question.. i've finally managed to burn the image.. and it looks alright, since i can see different files in the cd, but when i reboot the computer, nothing happens, and it goes back to windows xp.. does anybody know why?
thank you again for helping me.. i reallly appreciate it

---

### Post by mike555 on 2007-11-11
You might need to set your BIOs to boot from the CD first then the harddrive ............. you do this by pressing what ever your boot screen says to go into setup , usually F10 or Delete .......

---

### Post by lucamario on 2007-11-11
i tried but neither F10 nor delete seem to work..

---

### Post by oilchangeguy on 2007-11-11
> **lucamario said:**
> i tried but neither F10 nor delete seem to work..

pay attention when the computer starts to boot. you should see a prompt to press whatever key to enter setup. or shut down the computer. press and hold the esc key. start the computer (still pressing the esc key), you'll hear a beep, and an onscreen message about a keyboard error, press F1 to enter setup.

---

### Post by gn2 on 2007-11-12
> **lucamario said:**
> i tried but neither F10 nor delete seem to work..

Another two to try are F8 and F2

---

### Post by dnns123 on 2007-11-12
The defualt it delete, anyway, after entering Setup, go to Boot --> Boot priority
Make booting from the CD the top, save and exit, thats it!

---

### Post by lucamario on 2007-11-12
but how can i make it to the delete.. if it doesn't work? sorry for the stupid question, but really i know nothing at all.. 
anyway, i also tried using the holding esc and then F1.. a screen saying to boot using my cd-r.... apperead, but even though i chose that option it still started as wondows..

---

### Post by lucamario on 2007-11-12
also, i tried with the F2 or F8.. but still, even trying to change the boot device priority and everything, still it doesn't seem to work.. any other ideas? :confused:

---

### Post by jay1097 on 2007-11-12
Find out what kind of motherboard you have. then google your motherboards name and read the FAQ or google ur mobo's name and find out how to change the boot order like everyone has already said ecs,del,F10, F8, F2 are the common ones, but u have to press it as soon as your PC boots up. For example when my PC boots up i get a green ASUS splash screen and i have 3 seconds to hit ecs or F8 in order to boot to the BIOS. Goodluck and let me know how it went.

---

### Post by lucamario on 2007-11-12
the problem is that i could get there.. but once, i change the boot priority nothing happens.. i already got on those boot screens, using F2 and F8 and some others, but once there, nothing else..

---

### Post by Christmas on 2007-11-13
When you are in BIOS you have to set your CD-ROM (or DVD) to be the first boot choice, that means, your system will search for a boot record on the CD-ROM rather than on your Hard Disk, and will load Ubuntu setup instead of Windows. All you have to do is make sure you set your CDROM as the first boot choice. For example, for me it's something like "Primary boot option", "Secondary boot option". And I set Primary boot option as CDROM when I want to install Ubuntu. Your BIOS should be basically the same.

---

### Post by lucamario on 2007-11-13
what do you mean by bios?? can all those screens using F2-8-10, or anything else, be considered bios?? i'm sorry but i really don't know anything.. anyway.. if that's the case, i already did that.. else, could you explain how to get there?? thank you very much!!

---

### Post by jay1097 on 2007-11-13
The bios is the screen you get to when u hit F12 or ESC or whichever button. From their u can change the boot order. Check out this link it seems to be very good [http://www.whitecanyon.com/how-to-change-boot-order.php](http://www.whitecanyon.com/how-to-change-boot-order.php)
anyway good luck

---

### Post by peterjohn on 2007-11-13
I answered the fixed problem, and about the BIOS go to  [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)  that should help
-peter

---

### Post by gupta_sumesh63 on 2007-11-13
imgburner for windows is the best for burning iso's. Try that as mentioned above.

---

### Post by mc4man on 2007-11-14
As previous posted just install I_mgBurn_ It's guaranteed to make a proper boot disk from the iso. You may have burned the iso as a file instead of a boot disk.

---

### Post by lucamario on 2007-11-17
ok.. i solved the previous problem.. i had to download another version, because i had downloaded the wrong version.. anyway, now, i've downloaded the new version, checked it with m5d sum and it's perfect.. i burned it on a cd.. i reboot the computer, but once i choose "start or install ubuntu...", it starts booting and it stops.. it appears a long list of errors.. i push Esc to go back adn it gets back to the main menu.. i decide to check the cd, using cd integrity.. and it ends saying that i have many different errors on the cd.. does anyone know how to make it work, please?

---

### Post by Sef on 2007-11-17
1) Did you burn it at 4x or less?  Faster may corrupt the burn.

2) The disk was bad.

---

### Post by lucamario on 2007-11-17
i burned it at 4x.. and it seems fine, because when i put it in the computer, a launching browser program appears (live cd probably, but i'm really ignorant, so i'm not sure..)
it just gives problem when trying to start it after the ubuntu main menu just turning the computer on

---

### Post by FrankIOM on 2007-11-17
if you downloaded the ISO file from the Ubuntu site under the download button is some help this link [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")  should answer your question. It worked well for me. Windows does not burn ISO's and I found I could not get NERO to do it, though I think this is because I have a cut down version of the software

---

### Post by lucamario on 2007-11-17
thank you but i already checked that page and using my version of nero it worked..or at least, it seems so..

---

### Post by lucamario on 2007-11-17
nobody knows what might have happened?
like if it was just a case or anything like that?

---

### Post by oilchangeguy on 2007-11-17
wow! a week, 4 pages, and over 30 posts on how to burn an iso file. you've been given all of the info you need to get it done. maybe you should just stick with windows. trying to install a new operating system is just not your thing.

---

### Post by mc4man on 2007-11-18
it may be helpful at this point (assuming your still interested) to post some info 
what pc are you using and how old
what brand of media are you burning on

otherwise you could send away for a live cd or try using someone else's pc to burn a disk (with decent media)

---

### Post by lucamario on 2007-11-18
it's not burning the cd anymore the problem.. it's the fact that once i get to the cd menu and i try to start ubuntu, a list of errors, like "buffer I/O erron on device..." appears and when i check the cd integrity it says i have a few problems.. anyway, my computer is a sony vaio laptop PCG-8R1M..

---

### Post by justsomedude on 2007-11-18
> when i check the cd integrity it says i have a few problems...

You have to make sure the CD is burned properly first, then we can have a look at your boot problems (if they are still present then).


-Be sure to verify the md5sum of your download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Hashes can be found here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

-Burn the .iso file as slow as possible.

-Do an integrity check of your burned CD:

[https://help.ubuntu.com/community/In...IntegrityCheck](https://help.ubuntu.com/community/In...IntegrityCheck)


If you cannot burn a CD that checks fine on your own, you also have the possibility to order a Ubuntu CD for free:

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

How much ram do you have?

---

### Post by Niedzwiedz on 2007-11-18
Well, I am a few days late and a dollar short as "Justsomedude" have what I got thinking, in all this.
Do a Check Sum on the ISO to be sure it downloaded good. It may not happen often, but, it can happen you get a bad download. Any little glitch during a download could cause a corrupt file. Use the link "Justsomedude" gave;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
This what I would check first. Then burn slow, I burn ISO files at 2X and go drink a cold beer and it done when the beer is. \\:D/
I should add. I have used Nero, Infrarecorder and the regular Right Click deal Unbuntu use and all have worked when the Check Sum was good.

---

### Post by lucamario on 2007-11-19
i had already checked with md5 sum.. and it is perfect.. i also burned it at 4X with nero (as slow as possible) and it seems to work.. at least, when i put it in the computer,when it is still on, the live cd starts) but just when i try to make ubuntu start from the cd menu i have problems.. 
and when i try cd integrity, it says that i have something like 248 errors, or something like that.. do you think i should just try to burn it again or there some other problem?

---

### Post by louieb on 2007-11-19
> **lucamario said:**
> ... it says that i have something like 248 errors, or something like that.. do you think ...
 
Zero defects is what you want. You might get away with one or two, then again you might not.  Since  the checksum  is good  I 'm going to assume your download is good.   You say you burned at 4x thats good.  

Are you using  CD-R? thats what you need - not CD-RW. 
At this point I suspect its your CD drive. Might try to clean the lens with Isopropyl alcohol  and a q-tip.  Or it may be it time for a replacement.

---

### Post by Achetar on 2007-11-19
> **lucamario said:**
> ok.. i'll try using nero burning rom. i have it so it's not going to take a long time.. i'll let you know if it works.. thank you by now!
NO DONT INSTALL NERO!!!!!!!!!!!!!!!!!!!!
Go for ISO Recorder, it is good and free, and don't install garbage. Works great for me! I have used it for multiple ISOd CDs, never failed

---

### Post by lucamario on 2007-11-19
how can i replace it?? i have a laptot.. sigh.. okay, i'll try again burning a new cd, if it doesn't work i'll kill myself.. or more likely stay with windows, which i hate so much..:mad:

---

