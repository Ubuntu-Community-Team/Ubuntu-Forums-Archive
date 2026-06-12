---
title: "Lubuntu 12.04 on Ibook g4 a1134 general final fix"
date: 2015-02-11
forum: Apple Hardware Users
---

### Post by wassuprocker0 on 2015-02-11
Hello everyone,

[I]I made my first linux install after 10+ years of heard about linux os but never needed.
The point was to revival an old ibook g4. I'm no glad that apple don't make easy access to the battery cells : they are all 18650, and maybe only one don't work, but i purchase a new battery because the battery was down. If i had access, i could just change a 18650 cell for 5$.
But, hopefully, in computer, it's different. It's not like battery. If inside, something work bad (mac os 10.4), i can change the OS to linux and make it work better, or even good.

So, maybe one day, i will learn that open a cell and changing the chemical (lithium phosphate for example) is as hard as modify by yourself a kernel.
But now, i'm just learning that lubuntu is debian based with lxde and some pre-configuration to work. Maybe ubuntu is debian based with others pre-conf and an other GUI.[/I]

This is my focus : **make my ibook g4 A1134 works well**. 

On some point, mostly common but with my research didn't get any end, i need HELP ! For example, the main problem, sound, my last readed thread was [http://ubuntuforums.org/showthread.php?t=2169795](http://ubuntuforums.org/showthread.php?t=2169795), but i don't have snd A on my lib, but i have a lot of sound referance, and linux generic need superutilisateur and i think that the person write "you will have a long list of thing" and i have it so it's ok. Just to point people that i really made long research with a trying to be "smart and patient mind", but they gave no end. 

***_What's why i will ask you a lot of question, maybe in a years or two i will fix the issues and have a 10 years old labtop who work almost as well as the 1000$ labtop of today, for basic application._***

[SIZE=4]**SOUND**[/SIZE] = it's work under mac os, and boot sound work.

-I try to follow a lot of step, from ubuntu help wiki to debian mailing list, passing by a lot of others forum.
Main thing repeated every time are the etc/modules to modify, are delete, as the blacklist file. I try to delete some snd-powerpc and let some as it was advice, delete the one i want to the blacklist file, delete both of this two files, keep only one with what i want, etc, etc.. Never got a sound.

-- Is ubuntu 12.04 the same as ubuntu for this kind of thing ? are lubuntu is not only ubuntu without some packet, and with a GUI lighter ?
----> this way maybe debian forum will give me some help

[SIZE=4]VIDEO[/SIZE]

- I heard the video can work better, it's now being very slowly on youtube, what can i do ?

[SIZE=4]BATTERY[/SIZE]

-- I heard that i can make a "administration" by linux of the battery better, what can i do for ? will it give me longer time battery ?

[SIZE=4]SOFTWARE[/SIZE]

-I want to connect on a vpn, for that reason i download openvpn client, but all GUI interface i try to download to connect easily was not working, do you know one, light, who can work ?

[SIZE=4]RUNNING PROCESS[/SIZE]

-sometimes, i try to install software and the step by step process on the webpage i found, say to install a lot of package. Sometimes too much, will this package run while i use my computer for basic things, and make it working slower ? i guess maybe some of them only, so what can i do to see what is not suppose to run in the monitor and what can i do to long time delete them ?

[SIZE=4]LIGHTER CONFIGURATION[/SIZE]

-Is there a way to modify things in lubuntu 12.04 that make it runnung faster ?


I will slowly update this post to make a clean guide to setup lubuntu 12.04 on ibook g4 a1134 model.

Thanks a lot for your time, your answers, and the help of linux newbies owner of this particular labtop.

---

### Post by mörgæs on 2015-02-12
Good initiative but Lubuntu 12.04 is out of support so better to install 14.04.1 or 14.10.

---

### Post by wassuprocker0 on 2015-02-20
I guess 14.04 work slower on such a computer.
 i found solution for sound, 
i'm looking to have the battery indicator now
the wifi card is fully compatible with injection / monitoring and works very well with linux
problems are with videos : right click needed when mooving from full screen to half size etc.;
also with flash : don't know how to run an alternative version of flash player that can make run flash under firefox (know something exist)

for the rest, all works very well.

about hardware, for some interested, i wonder if buy a pata ssd worth it. also if changing the ram from 512mb to 1go worth it. also if i really need to open it and clean it. it make a lot of noise, diy solution was to put plastic things with something like blue ice in under the labtop. 

could be good to actualise such  a page, for people who need basic applications. can find it for 50$ + maybe 30$ for a new battery, and you have a great machine. 
amazing like downloading with an old computer doesn't make any problem. will probably use it like a server, when i'll now how to do (like a NAS). 
i got it for free, but i guess for 80$/100$ you can have a rpi with screen labtop and mouse, who works as well as this old machine !

thanks for your answer

---

### Post by este.el.paz on 2015-02-24
> **mörgæs said:**
> Good initiative but Lubuntu 12.04 is out of support so better to install 14.04.1 or 14.10.

I have 12.04 Xu installed on a G4 Powermac that I just recently "revived" . . . and just got some updates on it yesterday . . . it's got 450 MHz processor, so I'm not wanting to hassle the upgrade to 14.04 on it . . . 12.04 is fine, especially for a first time experience--no video card issues, no xorg.conf needed.

@OP:

I also have a G4 iBook, and recently I upgraded it to Ubun Mate 14.04 . . . from Xubunt/Lu 12.04, then did the upgrade to Xu 14 using Software Services rather than burning the DVD, etc . . . .   With 12.04 on the iBook I had no problems, sound worked, video worked, scrolling and moving windows went smoothly.  In 14.04, suddenly the radeon driver was not supported and I needed boot params to get into a read-able GUI, scrolling was rough and dragging windows rough . . . GUI would "freeze" until I made an xorg.conf file . . . and, sound, "gone."  And, I like MATE, but similar issues with the iBook . . . in 14 . . . fan blows loudly . . . really 12.04 PPC was "better" . . . .

In terms of things to do on your iBook . . . possibly not worth it, as PPC is getting less attention in the linux realm . . . I recently got a "BTI" replacement battery for it on eBay awhile back, much less than I paid for one new 4 years ago . . . seems to be holding up OK.  On my "new" G4 desktop with the 450 MHz processor, I'm thinking about upgrading the RAM to 2 GB and see if that makes things "work" a little smoother . . . the 1 GB lets me do "one app at a time" and "one action" . . . the iBook is 933 MHz . . . it's fine enough for checking emails and web surf . . . .  I'd suggest using it as is to learn about differnt Ubuntu installs or whatever, but don't throw too much $$$ at it . . . .

e.e.p.

---

