---
title: "livecd ubuntu 7.04 won't boot on a macbbok core2 duo"
date: 2007-05-30
forum: Apple Intel Users
---

### Post by davidek on 2007-05-30
Hi all,

I would like to installe ubuntu 7.04 on my macbbok core2 duo 2.0Ghz, I just installed osx and windows... and now is time for linux. What I do is to download ubuntu 7.04 desktop and alternate cd, burned it (2x) put it on my pretty new macbbok and start it (with rEFIt), but won't boot. The live CD started but on the menu I can't do anything, the keyboard doesn't work anymore, I have to shutdown the mac. The version I downloaded is the standard i386.

Any suggestions? Thanksssssssssss

---

### Post by LittleNate on 2007-05-30
I'm trying to do exactly the same thing and have exactly the same problem. I want a dual boot of Mac OSX and Ubuntu but every forum thread goes on about having a triple boot. Pluuueeeze! No Windows, just Ubuntu!

I'm halfway through an install and the blame prog just stops. I go to the triple boot cheat sheet  to make and mount a swap disk and the partition instructions do not apply for a dual boot. Does anyone have a simple methodology to install from a CD of the downloaded ISO Ubuntu? I am using Boot Camp - which works effortlessly in the partitioning mode, unlike clumsy cmd line work which is fraught with danger - and refit, which also ensures a simple boot choice. But I'm about to give up on Ubuntu, I've wasted many hours on this and it's a shame the allegedly best OS does not install simply on the allegedly best notebook, MacBook Pro Dual Core pocket rocket. 

Just a link will do!
:(

---

### Post by gracie36 on 2007-05-30
> **davidek said:**
> Hi all,

I would like to installe ubuntu 7.04 on my macbbok core2 duo 2.0Ghz, I just installed osx and windows... and now is time for linux. What I do is to download ubuntu 7.04 desktop and alternate cd, burned it (2x) put it on my pretty new macbbok and start it (with rEFIt), but won't boot. The live CD started but on the menu I can't do anything, the keyboard doesn't work anymore, I have to shutdown the mac. The version I downloaded is the standard i386.

Any suggestions? Thanksssssssssss

Try again and as soon as you choose the Live CD in rEFIt press the down arrow key. When the menu shows up this time the keyboard should work. It did for me anyway. 

I found that answer here somewhere and I was going to link to it but my search skillz are lacking this morning.

Good Luck!

btw, my Macbook Pro is a 6 month old Core 2 Duo.

edit: I found the post about it [here.]("http://ubuntuforums.org/showthread.php?p=2403093&highlight=down+key+refit#post2403093")

---

### Post by ronocdh on 2007-05-30
> **gracie36 said:**
> Try again and as soon as you choose the Live CD in rEFIt press the down arrow key. When the menu shows up this time the keyboard should work. It did for me anyway. 

I found that answer here somewhere and I was going to link to it but my search skillz are lacking this morning.

Good Luck!

btw, my Macbook Pro is a 6 month old Core 2 Duo.

edit: I found the post about it [here.]("http://ubuntuforums.org/showthread.php?p=2403093&highlight=down+key+refit#post2403093")
Thanks for bothering to post the original, where you found that trick. As I understand it, this is a firmware issue with rEFIt, and the context (as your link shows) was trouble on the GRUB menu, but I hadn't heard of an unresponsive keyboard on the Live CD.

As for the OP and comrade, sorry you guys have had such trouble so far. Currently I am myself triple booting, so I'm sorry if my advice is off target, but I'll give it a shot anyhow.

I see you've used the Boot Camp GUI partitioning tool to create space for Ubuntu. This is cool, as I understand it, and I've read that even the Boot Camp bootloader will recognize Ubuntu, although it'll label it as Windows. ;) This is reason enough to use rEFIt, in my mind!

Once you've installed rEFIt and then installed Ubuntu (I recommend using the alternate CD for all MacBook Pros, given the X server failure problem; the MacBooks can use the regular desktop/live CD; both MB and MBP should choose 32-bit or 64-bit depending on whether they have a Core Duo or a Core2 Duo, respectively), make sure you remember to sync your partition tables on the rEFIt main menu! I think this step is necessary even for dual booters (you've probably seen it on triple boot guides) given the GPT/MBR discrepancy.

As for a link, [this guide]("https://help.ubuntu.com/community/MacBook") is the best I can offer right now. I used it with Edgy to install... on Feisty, the whole kludge with command line entries to get GRUB to install are not necessary. But IIRC, the whole guide is oriented toward dual booters, with occasional helpful tips for triple booters. Good luck!

---

### Post by davidek on 2007-05-30
thanks for all the info you give me... but the cd doesn't boot on my machine:

macbook core2 duo 2.0Ghz
2GB Ram
100GB HD Sata 7200rpm

when it start I have the first screen where I can make my choice (install, options, ...) but the keyboard doesn't work.. I tried to boot and type the down arrow key more times but no way.. I'm not so lucky :-(

any advice? thankssssssssssssss

---

### Post by Chrisj303 on 2007-05-30
Sometimes my keyboard is unresponsive on the ubuntu LiveCD menu screen.

It shouldn't be an issue though, as if your wanting to start/install ubuntu you can just wait for the menu to time-out (30 secs) and the first menu item ('Start or Install Ubuntu') will be selected by default.

---

### Post by ronocdh on 2007-05-30
> **Chrisj303 said:**
> Sometimes my keyboard is unresponsive on the ubuntu LiveCD menu screen.

It shouldn't be an issue though, as if your wanting to start/install ubuntu you can just wait for the menu to time-out (30 secs) and the first menu item ('Start or Install Ubuntu') will be selected by default.
Exactly! Yeah, my keyboard is rarely responsive on the main menu, either, but Chrisj is right, there's the helpful time out. However, if these guys are using the alternate CD... no such luck. =/ Sorry guys, you'll just have to keep rebooting until it works. You can try holding down the C key during boot, which might bypass rEFIt and go straight to the CD. Maybe that'll help. Either way, it's going to take several tries. Don't give up!

---

### Post by davidek on 2007-05-30
that's right.... I use the alternate cd... but with some luck and more tries now I have ubuntu installed on my macbook :-D yeahhhhhhhh

just another question, when I have to choose between Windows and Linux there is the bootloader (GRUB) and I have to choose with one, if I choose windows with rEFIt then I have to choose windows into GRUB, and more times the keyboard doesn't work, that's right?

thankssssss

---

### Post by ronocdh on 2007-05-30
> **davidek said:**
> that's right.... I use the alternate cd... but with some luck and more tries now I have ubuntu installed on my macbook :-D yeahhhhhhhh

just another question, when I have to choose between Windows and Linux there is the bootloader (GRUB) and I have to choose with one, if I choose windows with rEFIt then I have to choose windows into GRUB, and more times the keyboard doesn't work, that's right?

thankssssss
Right. In rEFIt, choosing either Ubuntu or Windows will land you on the same GRUB screen. On the GRUB screen, the 10 second timeout will sweep you into Ubuntu, and you're correct, the keyboard is more often than not unresponsive on that screen. =/ You'll likely develop some kind of voodoo keystroke dance to get the keyboard to respond on GRUB, but be ready for multiple hard reboots.

Installing ELILO is supposed to bypass this, but it's extra setup time I haven't bothered to spend, because I am extremely lazy. I think Benanzo here was able to do it, so maybe he'll be kind enough to post a walkthrough at some point. Also, you can edit your grub conf file to change the countdown from 10 seconds to about 3. I do this because I so rarely use Windows.

*Edit: I meant that installing ELILO will allow rEFIt to go straight into Ubuntu without displaying the GRUB screen. I'm not sure how this affects WinXP's boot, but I believe it allows WinXP to have its own MBR back intact. If you install ELILO and remove GRUB, you'll likely have to use the **fixmbr** command on the WinXP installer CD to repair the MBR and get things all happy again. And don't forget to sync your tables in rEFIt!*

---

### Post by gracie36 on 2007-05-31
> **ronocdh]Thanks for bothering to post the original, where you found that trick. As I understand it, this is a firmware issue with rEFIt, and the context (as your link shows) was trouble on the GRUB menu, but I hadn't heard of an unresponsive keyboard on the Live CD.[/QUOTE]

If I spoke out of turn I apologize. I don't think I could have gotten Ubuntu installed on my Macbook without the assistance of this forum and when I saw a post requesting help with a problem I had just dealt with, I wanted to help if I could.


[QUOTE=Chrisj303 said:**
> Sometimes my keyboard is unresponsive on the ubuntu LiveCD menu screen.

It shouldn't be an issue though, as if your wanting to start/install ubuntu you can just wait for the menu to time-out (30 secs) and the first menu item ('Start or Install Ubuntu') will be selected by default.

It was an issue for me when I tried installing Ubuntu from the alternate cd because the install wouldn't move along after the 30 second timeout. But pressing the down key as soon as I chose the Linux cd option in rEFIt "woke up" the keyboard and allowed the install to progress.

And now I'll shut up. :-?

---

### Post by ronocdh on 2007-05-31
> **gracie36 said:**
> If I spoke out of turn I apologize. I don't think I could have gotten Ubuntu installed on my Macbook without the assistance of this forum and when I saw a post requesting help with a problem I had just dealt with, I wanted to help if I could.
My thanks for your posting the original thread wasn't sarcastic; I genuinely found it helpful! I, too, was just trying to pile on what little I knew of the situation. Thanks, again!

---

### Post by davidek on 2007-05-31
OT, the new macbook core2 duo 2.16 has a xt1600 and the core2 duo 2,0 a i985, right?

---

### Post by gracie36 on 2007-05-31
Mine is the Macbook Pro C2D 2.16 and it does have the ATI X1600. The first computer I've ever had that didn't have integrated Intel graphics and the Ubuntu install made me want to fling it across the room because of that graphics card.

@ronocodh: Thanks and sorry I misunderstood your original post.

---

### Post by ivesjd on 2007-05-31
All macbooks have intergrated graphics, All macbook PRO's have the x1600. Too bad the macbooks didnt have the x1600's though.... And Im surprised to hear of all the problems with the C2D, I barely had any problems at all with my CD.

---

### Post by themoebius on 2007-06-01
Yeah I also have the problem with the unresponsive keyboard at boot and the blank screen when it tries to start X. This is with the final release of Feisty for i386. I think I tried it once with the amd64 version and it worked, but perhaps that was just luck? I'm going to try the alternative CD for i386 now because I don't want to deal with 64bit compatibility issues.

---

### Post by davidek on 2007-06-01
I had the same problem with the 32bit and 64bit version desktop and alternate... You just need a bit of lucky ;)

---

### Post by tehmacuser on 2007-06-01
Here you go everybody! Found my old tut' on Feisty Fawn and OS X, NO WINDOWS! :)

[http://macmentor.org/forums/viewtopic.php?t=8758](http://macmentor.org/forums/viewtopic.php?t=8758)

have fun with that!

---

