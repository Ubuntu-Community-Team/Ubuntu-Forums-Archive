---
title: "Noob to Linux and have some questions."
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by waterskill on 2008-03-30
Hey everyone. I'm like a HUGE noob to linux and I just installed the Hardy Heron thinking that the beta couldn't be too bad. I haven't had anything go wrong so far but I was just going to ask if I should stay with the beta or not and if not then how do I downgrade to Feisty? Also, I want to ask a few noob questions.

1) What is a "Terminal"(Well I just found the Terminal while going through "Applications", so the question now is how do I use it?)
2) How do I install programs that I download for Ubuntu?
3) What are "Packages" and do I need one?
4) Can Linux Distros still run emulators for GBA and SNES/NES?
5) Where can I get a Firefox flash plugin that will enable me to hear sound on flash players
 (Ex. Youtube)?

Many thanks to whoever can help me.

-waterskill

---

### Post by Inxsible on 2008-03-30
> **waterskill said:**
> Hey everyone. I'm like a HUGE noob to linux and I just installed the Hardy Heron thinking that the beta couldn't be too bad. I haven't had anything go wrong so far but I was just going to ask if I should stay with the beta or not and if not then how do I downgrade to Feisty? Also, I want to ask a few noob questions.

1) What is a "Terminal"(Well I just found the Terminal while going through "Applications", so the question now is how do I use it?)
2) How do I install programs that I download for Ubuntu?
3) What are "Packages" and do I need one?
4) Can Linux Distros still run emulators for GBA and SNES/NES?
5) Where can I get a Firefox flash plugin that will enable me to hear sound on flash players
 (Ex. Youtube)?

Many thanks to whoever can help me.

-waterskill
1) Gusty is an upgrade to Feisty, so if you ever downgrade it should be to Gutsy. I have seen a lot better features in Gutsy compared to Feisty. Hardy is going to be released end of April,  so it might just be better for you to keep Hardy, if its not giving you any problems.

1) Terminal is a place where you enter unix commands to do stuff. Its a command line. Sorta like the DOS prompt ( I am going to get killed for saying that)

2) There are many ways to install programs in Ubuntu a)Synaptic Package Manager b) Applications>>Add/Remove c)```
sudo aptitude install program-name
``` d)```
sudo apt-get install program-name
```Now the 2 commands that I just gave you, that's what you would enter in the Terminal.
3) a package is a collection of code (so to speak) that you can install. You do not need to install any "packages" as such. When you install any software, the appropriate packages get installed automatically
4) Someone else might be of more help here
5) you can install flash by ```
sudo aptitude install flashplugin-nonfree
```You will have to enable the universe and multiverse repos for that. You can do that by going to System>>Administration>>software Sources. Then select the checkboxes for universe and multiverse.


Oh ! and welcome to Ubuntu !!!! You will love it just the way we all do :)

---

### Post by SaikoRonin on 2008-03-30
I am kind of new to linux myself,  And i had to sort through those same questions myself. 

Gutsy gibbon is the first one ive tried and it is the newest...

The terminal reminds me of dos if you know anything about that of course its completely different...  You enter all your text commands in this.  Gnome is the environment that you click stuff in.  That sits right on top of your Terminal pretty much.  Think about it like this, every time you click something its sending a command to the terminal for you to do something...  You'll have to talk to another member for more information on using it such as the command language.

You can install almost any program you'd need from the synaptic package manager, in gutsy it is listed under System/Administration/Synaptic Package manager

Or you can go to Add/Remove Programs under applications (also gutsy)

yes there are various emulators available run a search in one of the package managers.

When I installed flash I went to a site that used flash and then when a video did not run a notification popped up saying i needed additional plugins.  You click that and it will open an install screen.  It will offer flash or another program.  The other program doesnt work quite properly yet so install regular flash.

hopefully a more experienced member will help

---l- Ronin

---

### Post by waterskill on 2008-03-30
> **Inxsible said:**
> 1) Gusty is an upgrade to Feisty, so if you ever downgrade it should be to Gutsy. I have seen a lot better features in Gutsy compared to Feisty. Hardy is going to be released end of April,  so it might just be better for you to keep Hardy, if its not giving you any problems.

1) Terminal is a place where you enter unix commands to do stuff. Its a command line. Sorta like the DOS prompt ( I am going to get killed for saying that)

2) There are many ways to install programs in Ubuntu a)Synaptic Package Manager b) Applications>>Add/Remove c)```
sudo aptitude install program-name
``` d)```
sudo apt-get install program-name
```Now the 2 commands that I just gave you, that's what you would enter in the Terminal.

Sweet, thanks a lot :) I'll be sure to give you some thanks.
Also, does it matter which code to use to install?

> **SaikoRonin said:**
> I am kind of new to linux myself,  And i had to sort through those same questions myself. 

Gutsy gibbon is the first one ive tried and it is the newest...

The terminal reminds me of dos if you know anything about that of course its completely different...  You enter all your text commands in this.  Gnome is the environment that you click stuff in.  That sits right on top of your Terminal pretty much.  Think about it like this, every time you click something its sending a command to the terminal for you to do something...  You'll have to talk to another member for more information on using it such as the command language.

You can install almost any program you'd need from the synaptic package manager, in gutsy it is listed under System/Administration/Synaptic Package manager

Or you can go to Add/Remove Programs under applications (also gutsy)

yes there are various emulators available run a search in one of the package managers.

When I installed flash I went to a site that used flash and then when a video did not run a notification popped up saying i needed additional plugins.  You click that and it will open an install screen.  It will offer flash or another program.  The other program doesnt work quite properly yet so install regular flash.

hopefully a more experienced member will help

---l- Ronin

Thanks, also I'll give you +thanks. :) But one thing, I installed the plugins when I first got the OS but when I try to view flash videos it plays the video but no sound. I researched it and MANY others had this problem but I'm the first one I've seen to have it with Hardy so far.

---

### Post by Inxsible on 2008-03-30
No you can use either of the commands. I just wanted to let you know that there are multiple ways. the apt-get and aptitude are more or less the same thing.

Does your sound work for everything else ? If the flash videos work, then I think it might be a problem with your sound card rather than flash

---

### Post by waterskill on 2008-03-30
> **Inxsible said:**
> No you can use either of the commands. I just wanted to let you know that there are multiple ways. the apt-get and aptitude are more or less the same thing.

Does your sound work for everything else ? If the flash videos work, then I think it might be a problem with your sound card rather than flash

Yeah, it works with everything else. The only problem I've had is with flash.

So how would I do the commands with installing wine?

---

### Post by Inxsible on 2008-03-30
> **waterskill said:**
> Yeah, it works with everything else. The only problem I've had is with flash.

So how would I do the commands with installing wine?
The same command just replace "program-name" with "wine"

---

### Post by waterskill on 2008-03-30
> **Inxsible said:**
> The same command just replace "program-name" with "wine"

Oh ok. So how do I install programs that I download? It only gives me a folder and theres no instructions. x.x I'm just so used to Windows. :(

---

### Post by Inxsible on 2008-03-30
> **waterskill said:**
> Oh ok. So how do I install programs that I download? It only gives me a folder and theres no instructions. x.x I'm just so used to Windows. :(
That totally depends on the type of the file that you downloaded. If its a .deb file then you can simply double click it. If its a tarball, then its a bit complicated. I would suggest that you keep away from those until you get familiar with the OS.

Most programs you need will be in the repos and you can use any one of the 4 methods i told you earlier.

---

### Post by waterskill on 2008-03-30
> **Inxsible said:**
> That totally depends on the type of the file that you downloaded. If its a .deb file then you can simply double click it. If its a tarball, then its a bit complicated. I would suggest that you keep away from those until you get familiar with the OS.

Most programs you need will be in the repos and you can use any one of the 4 methods i told you earlier.

Okie doke ^_^ All my questions are answered so far except the sound one. :/

---

### Post by Inxsible on 2008-03-30
For the sound, try this
type in ```
alsamixer
``` in a terminal and then put all the volumes to max level and then try.

---

### Post by waterskill on 2008-03-30
> **Inxsible said:**
> For the sound, try this
type in ```
alsamixer
``` in a terminal and then put all the volumes to max level and then try.

Ok lemme try.

---

### Post by Shazaam on 2008-03-30
While you are in alsamixer if you see this- M- under each one that means it muted. Move to the one you want to unmute and hit M on your keyboard. It should then change to 00.

---

### Post by waterskill on 2008-03-30
Woooo.. Wtf? It works. :) THANKS! :D

---

### Post by Inxsible on 2008-03-30
> **waterskill said:**
> Woooo.. Wtf? It works. :) THANKS! :D

Sweet !!!

Enjoy the world of Ubuntu !!!

---

### Post by waterskill on 2008-03-30
> **Inxsible said:**
> Sweet !!!

Enjoy the world of Ubuntu !!!

:)

---

