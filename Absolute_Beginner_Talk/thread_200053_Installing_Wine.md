---
title: "Installing Wine"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Danyl on 2006-06-19
Hi again y'all

Trying to get Wine installed so I can start devoting my entire home PC experience to Linux and not Windows.

I've tried to download and install Wine as per the directions on their site for Ubuntu:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

however I'm not having any luck. When I enter this repository deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main into Synaptic Package Manager, I get the following error:

[http://wine.budgetdedicated.com/apt/dists/breezy/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/breezy/main/binary-amd64/Packages.gz:) 404 Not Found

Can any one tell me what's up with this?

I want to install Wine but being a newb to Linux, I want to stay away from using the source packages/the terminal as this scares me!!!

Thanks heaps in advance guys.

---

### Post by Winblowz on 2006-06-19
Just open up the terminal and type "apt-get install wine". That should be all you need to do.

---

### Post by Drakkor on 2006-06-19
Intrested in trying Wine also,after  sudo apt-get install wine
where's the program?? Thanks

---

### Post by r4ik on 2006-06-19
In a Terminal type winecfg

Good luck !

---

### Post by skale on 2006-06-19
You don't just click on it and some window opens up. 

Change settings and all with
> winecfg
To install something(like a .exe file) type
> sudo wine sndvbsdhvchksdcvks.exe
you will find all your files in the .wine directory in your home folder.
> ls .wine
You can check it out windows-style, also, type
> winefile

I think that's pretty much it. Their website has some good stuff.

---

### Post by Drakkor on 2006-06-19
Thanks,but that just sounds like too much hassle for what it's worth and I don't even know if it'll run COD2,and Unreal Tournament 2004, and then from what I have read it takes a big performce hit when running. Guess I just continue to
reboot to XP for those.  Thanks

---

### Post by Danyl on 2006-06-20
[QUOTE=Winblowz]Just open up the terminal and type "apt-get install wine". That should be all you need to do.[/QUOTE]

Thanks Winblowz but I encountered the following problem:

[B]Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate[/B]

Do you think it has something to do with the fact I'm running an Athlon64?

---

### Post by spaceman07 on 2006-06-20
You will need to enable the  universal setting in synaptic installer.

I had similar problem.. and that resolved it.

---

### Post by mostwanted on 2006-06-20
Wine is only for x86.

---

### Post by Torquemada28 on 2006-06-20
[QUOTE=mostwanted]Wine is only for x86.[/QUOTE]

Oh FFS. ](*,)

---

### Post by Danyl on 2006-06-20
[QUOTE=spaceman07]You will need to enable the  universal setting in synaptic installer.

I had similar problem.. and that resolved it.[/QUOTE]

Nope, this didn't work either. Geez according to the Wine site its so simple, yet why no luck?

Any more advice?

---

### Post by Danyl on 2006-06-23
:-k 

Hmmmm has anyone got a clue as to solving this problem?

Surely someone out there has successfully installed Wine on an AMD64 machine?

---

### Post by BoyOfDestiny on 2006-06-23
[QUOTE=Danyl]:-k 

Hmmmm has anyone got a clue as to solving this problem?

Surely someone out there has successfully installed Wine on an AMD64 machine?[/QUOTE]

Well you can do it via chroot, but you can try this solution:

Wine on 64-bit AMD / Ubuntu
[http://www.winehq.com/?issue=317](http://www.winehq.com/?issue=317)

"David Anderson wrote in with a step-by-step guide to getting Wine to build on an AMD-64 system using Kubuntu 6.06 (Dapper Drake):"

---

### Post by muxecoid on 2006-06-23
How do you enable DirectX in wine?

---

