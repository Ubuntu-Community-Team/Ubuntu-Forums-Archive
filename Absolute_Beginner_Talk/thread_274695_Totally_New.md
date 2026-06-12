---
title: "Totally New"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Dededina on 2006-10-10
I am totally new to the Ubuntu thingie. Have no idea what I am doing. All I know is, I can not download and install a couple of the programs I normally use. Plus, it will not recognize my cd-rom, nor will it let me run the installation program for my DVD drive. I do not understand all that tech-type talk of putting all those codes in and where they go. I don't want to sound totally stupid here, but guess I really am. I had no problem whatsoever with windows. There are some aspects of this program I really love. I guess I am just lost.
Any help will be greatly appreciated. Thank you and have a great day!!!!

---

### Post by bigken on 2006-10-10
Have you downloaded the [ISO]("http://www.ubuntu.com/download") file if so you need to burn it to a disc use [this ]("http://isorecorder.alexfeinman.com/isorecorder.htm")
then boot from the cdrom ;)

---

### Post by sKuarecircle on 2006-10-10
Welcome, and just stick to forums when you get stuck, I can promise you will get it all sorted. I personally can't help on this particular post.Just ging a bit of encouragement.

---

### Post by tronica on 2006-10-10
sounds like you already got ubuntu installed, heres a great and easy to understand guide on how to install pretty much everything you will need

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by bigken on 2006-10-10
and please if you any important data in windows back it up you will also need to defrag windows if you are going to duel boot ;)

---

### Post by dannyboy79 on 2006-10-10
> **Dededina said:**
> I am totally new to the Ubuntu thingie. Have no idea what I am doing. All I know is, I can not download and install a couple of the programs I normally use. Plus, it will not recognize my cd-rom, nor will it let me run the installation program for my DVD drive. I do not understand all that tech-type talk of putting all those codes in and where they go. I don't want to sound totally stupid here, but guess I really am. I had no problem whatsoever with windows. There are some aspects of this program I really love. I guess I am just lost.
Any help will be greatly appreciated. Thank you and have a great day!!!!

first, please be more specific about exactl what programs you are downloading and trying to install. next, we need to see if your fstab has a cdrom entry in it. open up a terminal by going to applications, accessories, then click on terminal. then type in sudo gedit /etc/fstab it will bring up a box asking for a password, just enter your password, this is going to give you root privalages momentarily. the please copy and paste everything that is in that file. IMPORTANT, make sure you don't change anything yet. In fact, lets make a copy of it immediately. in the terminal, type in cp /etc/fstab /etc/fstab-backup. what this has done is created a backup file of your fstab file and it is called fstab-backup. this way if you ever screw up you fstab file so bad, you can always do a mv /etc/fstab-backup /etc/fstab and then what this will do is overwrite the screwed up fstab with the backup we created. can you also inform us what ide channel it is on, like is it hooked up as a slave or a master, are you using cable select? is it hooked to the primary ide channel or secondary? let't start by answering ALL these things and we'll go from there. we'll work on the dvd thing after we get this stuff worked out.

---

### Post by anaconda on 2006-10-10
It sounds to me that you are trying to install your favourite WINDOWS programs to your new ubuntu installation. 

They wont work, (just like you can't run linuxprograms in windows) but there is a way to run some windows programs using wine windows emulator..

The DVD-drive should work just fine, and no, it doesn't need installing windows-drivers

PS. Good luck. Ubuntu can be a bit hard in the beginning, but after that you will see that it is actually better that what you are used to..

---

### Post by Minyaliel on 2006-10-10
Dededina, I just googled up a list for you on which Linux programs might replace those you used in Windows. Check this: [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html). Now, if you find what you're looking for, tell us which ones you want and then it should be much easier to help you.

---

### Post by Dededina on 2006-10-10
Well, here goes. 1 of the programs I usually download runs in the background of the puter, and it also helps to make me a few dollars every month. To me, it is important. I did a total clean install of Ubuntu, so I have no Windows installed on this. My DVD drive is also set as a master along with the hard drive. I have gone into the System programs and tried to mount it and the cd-rom, but it won't let me. And, I did not thru the Administrator thing too. This all seems so darn complicated. Makes me want to cry. Also, maybe I have an older version of Ubuntu. I ordered it thru e-bay to check it out. Can't find Applications nor Accessories. Okay, I am going to cry. I have helped so many other people to install programs, fix their hard drives, install new hardware, all that kind of stuff and was so darn proud of myself. Hah, now I am just a totally lost granny LOL
I will keep trying though. I do NOT give up easily. So, here goes. Thank you, thank you!!!

---

### Post by Minyaliel on 2006-10-10
Okay... I can't help ou with your hardware problems... but you're talking about this program "running in the background", as you say. You might want to try running it in WINE, I can't guarantee it's going to work, but it's the best chance you've got for making it work. It's important though, to know which version of Ubuntu you're using. I can't help you if I don't know whether you're using the current version or an older one.

---

### Post by HereInOz on 2006-10-10
If the programs that you want to run are designed to work with Windows, they will not work with Ubuntu.  Like trying to use diesel fuel in a petrol engine.   If you need to use these programs, and they are for Windows, with no Linux versions, you may well be stuck with Windows.

There are several ways to run Windows programs with Linux, but perhaps not for you yet, as you seem to be having enough trouble as it is.

Remember though, that Linux is not Windows, it is different.  Sometimes better, sometimes not.  Horses for courses - use the system that does it best for you.

---

### Post by dannyboy79 on 2006-10-10
> **Dededina said:**
> Well, here goes. 1 of the programs I usually download runs in the background of the puter, and it also helps to make me a few dollars every month. To me, it is important. I did a total clean install of Ubuntu, so I have no Windows installed on this. My DVD drive is also set as a master along with the hard drive. I have gone into the System programs and tried to mount it and the cd-rom, but it won't let me. And, I did not thru the Administrator thing too. This all seems so darn complicated. Makes me want to cry. Also, maybe I have an older version of Ubuntu. I ordered it thru e-bay to check it out. Can't find Applications nor Accessories. Okay, I am going to cry. I have helped so many other people to install programs, fix their hard drives, install new hardware, all that kind of stuff and was so darn proud of myself. Hah, now I am just a totally lost granny LOL
I will keep trying though. I do NOT give up easily. So, here goes. Thank you, thank you!!!


i hate to be so harsh, but i can't help you if you if you don't help me help you! You didn't answer ANY ONE of the things I asked of you so I can't provide you with any help. I want to but it seems as though you are going to use other means of help and that is fine. Good luck

---

### Post by Dededina on 2006-10-10
Thank you all again for your help. I will not give up, cause I like this OS. I will eventually figure it out. It's just great to know you all are here to help. Take care and have a great day!!!!

---

