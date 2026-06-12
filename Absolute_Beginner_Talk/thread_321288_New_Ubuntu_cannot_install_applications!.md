---
title: "New: Ubuntu cannot install applications!"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Kazna on 2006-12-18
Hi everyone

I installed Ubuntu 6.10 Edgy Eft and it works fine. 

I have one **major problem** with the screen as my eyes are sore, red and watery now. No idea till now how to fix it. Whatever anyone has so far stated has failed. Would like some help there as otherwise its unusable for me :(

The main thread problems:

[COLOR=Blue] 1:[/COLOR] I installed Automatix2 to get some apps. I get errors now as below:

[COLOR=Red] a)[/COLOR] When I try creating a bin to be an executable in the Terminal I get:
[FONT=Times New Roman]
[COLOR=DimGray] home@home-desktop:~$ chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory[/COLOR][/FONT][COLOR=DimGray]
[/COLOR] 
[FONT=Times New Roman][COLOR=DimGray] home@home-desktop:~$ sudo ./RealPlayer10GOLD.bin
sudo: cannot access `RealPlayer10GOLD.bin': No such file or directory

[/COLOR][/FONT] while its on my desktop! :confused:

[COLOR=Red] b)[/COLOR] Extra installations also fail:
 
[FONT=Times New Roman][COLOR=DimGray]home@home-desktop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR]

[FONT=Verdana]Now I can't install anything through it, I always get this problem! 

[COLOR=Red]c)[/COLOR] Followed this[COLOR=DimGray]: [FONT=Times New Roman]http://java.com/en/download/help/5000010500.xml#selfextracting[/FONT][/COLOR] and it never worked! error.
[/FONT][/FONT] 
[COLOR=Blue] 2:[/COLOR] I installed 7-zip or p7zip as it maybe called in Linux, and it isn't showing up anywhere. I have that, yes. After installation through SPM, of the -full, when I go into check my programs installed, I get no mention of it anywhere. Yet going back into SPM gives me the option of removing and its highlighted with the checkbox removed to portray that its installed. [IMG]http://www.techsupportforum.com/images/smilies/1-confused.gif[/IMG]

[COLOR=Blue]3:  [/COLOR]Is there any "place" to check for all the recent history (i.e. logs, docs, pics, net history)? 

I'm aware of the Recent Documents option under Places. I'm after the explorer sort of location rather.

[COLOR=Blue]4:[/COLOR] I've had 4 crashes today whilst I was in the middle of something. I lost everything with 4 bug reports in it already! GIMP was one that crashed them... and my desktop rearranged itself, lost wallpaper etc. Just what I didn't expect and it was on the first attempt.


Dear need o help here please :( Thanks fro all the help!

---

### Post by lamego on 2006-12-18
a) You must "chdir" to the directory where the real player installer was downloaded
b) On the terminal run: sudo dpkg --configure -a

---

### Post by Kazna on 2006-12-18
> **lamego said:**
> a) You must "chdir" to the directory where the real player installer was downloadedI have, haven't I? Desktop..
> b) On the terminal run: sudo dpkg --configure -aDone. I get:
[FONT=Times New Roman]
home@home-desktop:~$ sudo dpkg --configure -a
Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

home@home-desktop:~$

[FONT=Verdana] Should it be all ok now?[/FONT]
[/FONT]

---

### Post by meng on 2006-12-18
Chdir this way (I'm guessing)
cd Desktop

then run the RPinstaller

as for the sudo apt-get thing, you should now try it again now you've done the dpkg --configure-a thing.

---

### Post by Kazna on 2006-12-18
Sorry to bear bad news, but both of those options didn't work.

Secondly I'm getting frequent crashes and my CPU is very unstable many times jammed @ 100% for no apparent reason.

I don't play games and there's no videoing/media work going on.

Also the entire applications and desktops are freezing, showing the right-click menu everytime I click on anything else such as a link.. and opening up everywhere until I double click elsewhere and then have to click the link required again, before an command is processed.

Like here for instance, I have to click the box 3 times to be able to choose something or reply. Doing so once brings up the loading icon, twice makes it click elsewhere and 3rd time  gets it right to here where I chose.

I'd love some help with this please :sad:

---

### Post by meng on 2006-12-18
Okay, as an extreme measure, have you considered installing 6.06 instead of 6.10? Perhaps your system doesn't like the edginess of Edgy. Also I wonder whether you may be better off NOT using automatix2 and just manually installing the multimedia etc. you require. If you tell us what you need we can point you in the right direction. Generally there are only one or two commands required for each driver/set of codecs/firefox plugin you need.

---

### Post by Kazna on 2006-12-18
> **meng said:**
> Okay, as an extreme measure, have you considered installing 6.06 instead of 6.10? Perhaps your system doesn't like the edginess of Edgy. Also I wonder whether you may be better off NOT using automatix2 and just manually installing the multimedia etc. you require. If you tell us what you need we can point you in the right direction. Generally there are only one or two commands required for each driver/set of codecs/firefox plugin you need.

Many thanks meng. I've resolved most issues now. Its in connection with the software I've installed. The minute I delete it everythings fine.

I have 6.06 too BTW :cool: Thats on a separate drive..

I'll get rid of the Automax2 now aswell, just to check.

As for now, I need serious help with the screen resolution and display please.
The monitor I have displays best picture @ 1024x768 96DPI.

In Edgy and Dapper, I only get 60 and 75Hz as the options and it pains my eyes badly, as well as the picture being really bad.

Please can you assist how I can go about this?

Chipset is SiS740 on the computer I'm using for those OS's.


I've tried the xorg reconfigure commands, but I was stuck at what to type where.

Appreciate your help :mrgreen:

---

### Post by Kazna on 2006-12-19
Hi Does anyone have any idea's? or is this a bug/flaw in Ubuntu?

Please help if you do know.

Thanks.

---

### Post by macogw on 2006-12-19
What do you mean the refresh rate hurts your eyes?  Is it too slow or too fast?  The reason the options are 60 and 75 is probably that 60-75 is what the range your video card/screen can use.  If you go outside their capabilities, you can damage the hardware.

---

### Post by Kazna on 2006-12-19
> **macogw said:**
> What do you mean the refresh rate hurts your eyes?  Is it too slow or too fast?  The reason the options are 60 and 75 is probably that 60-75 is what the range your video card/screen can use.  If you go outside their capabilities, you can damage the hardware.Eye strain is caused causing a bloodshot eye, thats what I mean. My video is on board shared. I use 90Hz in Win installations and that works just fine! So thats not a valid reason here.

Any other idea's?

---

### Post by riven0 on 2006-12-19
> **Kazna said:**
> Eye strain is caused causing a bloodshot eye, thats what I mean. My video is on board shared. I use 90Hz in Win installations and that works just fine! So thats not a valid reason here.

Any other idea's?

Wait a minute. Maybe I'm not reading this right, but when you did a sudo dpkg-reconfigure xserver-xorg, did you manually put in the 90hz when it gave you the option to do it? If not, that's the first thing you should try. Then restart the comp and see what happens.

---

### Post by helmeteye on 2006-12-19
I think your eyes hurt because the font resolution in firefox on dapper and edgy really sucks.  They always look fuzzy until you mess with things for a while to figure them out.

---

### Post by macogw on 2006-12-20
Doesn't require too much messing.  Just turn off anti-aliasing.  Go to System > Preferences > Font and set it to "best contrast" and see if that helps.  If you have an LCD, try sub-pixel smoothing.

---

