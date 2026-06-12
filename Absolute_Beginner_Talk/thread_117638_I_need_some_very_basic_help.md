---
title: "I need some very basic help"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Dazza81 on 2006-01-15
Hey guys, 

I am trying to have a look at Ubuntu Linux and cant seem to make it work. I downloaded it and opened the file using isobuster and burnt the files on a CD. Now when I restart, its not working. Heres a screenshot of what I get when I open isobuster:

[IMG]http://i4.photobucket.com/albums/y122/Dazza81/isobuster.jpg[/IMG]

 Can anyone tell me which files Im supposed to extract and burn, just to make sure that Im doing it right? How many files (approx) should there be on the CD? Any help would be really appreciated. Please keep in mind that Im not too good when it comes to technical computer stuff, so assume that Im a complete idiot when explaining please :D ;) Thanks a lot :cool:

---

### Post by deNoobius on 2006-01-15
Welcome!  The problem is that you're burning the individual files as data.  You need to burn the .iso as a disk image.  I don't know about the particular software you are using, but you need to look for a command or help item relating to "burn as image" or "disk image" or something like that.

---

### Post by Dazza81 on 2006-01-15
I'm using Nero to burn the CD. So this icon is what I should be burning?:

[IMG]http://i4.photobucket.com/albums/y122/Dazza81/ubuntu_icon.jpg[/IMG]

If yes, all I have to do then is run Nero, select "Copy and Backup" ---> "Burn Image to Disc" and run that?

---

### Post by Vladimirm on 2006-01-15
I dont knwo if that owuld work, what i did was simply
Go onto nero express, and i think it was at the bottom of the list it says something about image, just click on that adn tehn it'll ask you for the file you want, make sure you select show all files, and click on the thign you want to make an image to. that should work fine, then change yourbios settings to boot from cd and you'll be fine

---

### Post by deNoobius on 2006-01-15
Yeah, there should be a "burn image" option right in the file menu.

---

### Post by Dazza81 on 2006-01-15
[QUOTE=Vladimirm]I dont knwo if that owuld work, what i did was simply
Go onto nero express, and i think it was at the bottom of the list it says something about image, just click on that adn tehn it'll ask you for the file you want, make sure you select show all files, and click on the thign you want to make an image to. that should work fine, then change yourbios settings to boot from cd and you'll be fine[/QUOTE]
Nero Image Drive is the one, right? Ok, so I click on that and select all the files I have extracted and burn those?

---

### Post by Dazza81 on 2006-01-15
[QUOTE=deNoobius]Yeah, there should be a "burn image" option right in the file menu.[/QUOTE]
So I should select that option and then burn the Iso file? Thats just one file right?

---

### Post by deNoobius on 2006-01-15
Maybe this will help.  Also, please tell us which version of Nero you're using.


[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by Dazza81 on 2006-01-15
[QUOTE=deNoobius]Maybe this will help.  Also, please tell us which version of Nero you're using.


[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)[/QUOTE]
Nero Express 6.

Thanks, Ill have a look at that :)

---

### Post by deNoobius on 2006-01-15
[QUOTE=Dazza81]So I should select that option and then burn the Iso file? Thats just one file right?[/QUOTE]

I believe so.  I don't use Nero, but normally you would simply burn the .iso as a single file.

---

### Post by Vladimirm on 2006-01-15
you shouldnt of extracted any files, how/ where did you download it from??
No distro that ive ever downnloaded has ever come like that

---

### Post by Dazza81 on 2006-01-15
[QUOTE=Vladimirm]you shouldnt of extracted any files, how/ where did you download it from??
No distro that ive ever downnloaded has ever come like that[/QUOTE]
From Ubuntulinux.org I think. It was a single file (the icon I posted here earlier on) and extracted the files from that one using IsoBuster. Thats how I got a bunch of files. I downloaded a single file though, which I am in the process of burning :) Ill let you know how this goes (hopefully well!! :D )

---

### Post by deNoobius on 2006-01-15
ISObuster is sort of the exact opposite of what you wanted to do.  It extracts files from a disc image, whereas you want to preserve the disk image intact.
Basically, what you're making is a bootable CD, and it will only work if the computer recognizes it as such, which it won't do if you burn it as a bunch of separate data files.  If the computer can't boot from the disk, you never get into Ubuntu.

I'm not saying this to be critical, but to explain so you'll understand what's going on and know for future installs if you decide to stay with Ubuntu.

---

### Post by Vladimirm on 2006-01-15
lol, with a bit of luck he'll be alright. fingers crossed

---

### Post by Dazza81 on 2006-01-15
Hey guys, thanks a real lot for all your help. I managed to run it at last :D Dont worry deNoobius, thanks for your explanation regarding isobuster. 

Now, do I have to configure my email and internet settings in order to use the internet, since I couldnt connect to any website while using it. Any other "beginners tips" would be appriciated too :cool:

---

### Post by deNoobius on 2006-01-15
Well, if you ever actually install instead of using the live CD, I would suggest you consider using Automatix (search for it, also see the "configuration tips and tricks" topic) to do your initial setup.  Of course, you can learn all about manually adding software and tweaking, but while you learn you should have a well-configured system without headaches.

---

### Post by Dazza81 on 2006-01-15
[QUOTE=deNoobius]Well, if you ever actually install instead of using the live CD, I would suggest you consider using Automatix (search for it, also see the "configuration tips and tricks" topic) to do your initial setup.  Of course, you can learn all about manually adding software and tweaking, but while you learn you should have a well-configured system without headaches.[/QUOTE]
Yeah, I do plan on installing it eventually, (dual-boot system, since I still need Windows), but I'd rather learn more about it before and get to know it better. I might buy some sort of manual tomorrow (Linux for Dummies, hehe). Is there a way for me to use the internet while Im still using the Live version so, or do I have to install it in order to go online?

---

