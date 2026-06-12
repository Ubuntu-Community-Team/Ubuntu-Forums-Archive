---
title: "The file format is invalid?? New theme install errors"
date: 2005-05-12
forum: Art &amp; Design
---

### Post by ntrsfrml on 2005-05-12
hey guys.. i was trying to install a theme to my Ubuntu install.. downloaded a famous GDM theme from this page [http://www.gnome-look.org/content/show.php?content=21492](http://www.gnome-look.org/content/show.php?content=21492)

Opened >> system>>pref>>Themes>>install new themes>>browsed to the 21492-cleanlinux.tar.gz >>HIt install button>> It gives me = The file format is invalid error :(

I followed the tips given in the help file:  To Install a New Theme

```
You can add a theme to the list of available themes. The new theme must be an archive file that is tarred and zipped. That is, the new theme must be a .tar.gz file.

To install a new theme, perform the following steps:

   1. Start the Theme preference tool.
   2. Click on the Install Theme button. A Theme Installation dialog is displayed.
   3. Enter the location of the theme archive file in the drop-down combination box. Alternatively, to browse for the file, click on the Browse button. When you have selected the file, click OK.
   4. Click on the Install button to install the new theme. 
```

what am i doing wrong here? please help :(

---

### Post by hazza96 on 2005-05-12
[QUOTE=ntrsfrml]hey guys.. i was trying to install a theme to my Ubuntu install.. 

what am i doing wrong here? please help :([/QUOTE]
Nothing I just tried to install the theme on Hoary as well and it failed, it works on Warty though.

I think that the theme is not compatible with the version of Gnome in Hoary.

---

### Post by ntrsfrml on 2005-05-12
[QUOTE=hazza96]Nothing I just tried to install the theme on Hoary as well and it failed, it works on Warty though.

I think that the theme is not compatible with the version of Gnome in Hoary.[/QUOTE]

aww..that sucks  :-x ..Is there a site with new/compatible with Hoary Gnome themes?

thanks  :razz:

---

### Post by hazza96 on 2005-05-12
[QUOTE=ntrsfrml]aww..that sucks  :-x ..Is there a site with new/compatible with Hoary Gnome themes?[/QUOTE]
Don't take my word that the themes are not compatible, the developers could have broken theme management in Hoary.

What needs to be done is the theme tested on another distro that has the same Gnome version of Ubuntu. If it works then Hoary is broken, if it doesn't then you can be reasonably sure that there are differences between the theme structures.

I don't see programmers of Gnome making it so that the theme management was not backwards compatible, then again it might not be possible.

As I said the theme needs testing on another Distro that uses the same version of Gnome, then we will know for sure.

---

### Post by ntrsfrml on 2005-05-12
seriously...i'm not really happy with my switch.. installed ubuntu over my windows xp pro and so far it has been a PITA to even install a simple proggy or a theme..why can't they make everything like .exe in windows and you can follow the install wizard. Nothing is compatible!!? I downloaded Firefox 1.0.4 today and tried everything still i can only run it in Terminal :(

TIme for me to go back to windows world..in my book Ubuntu or LInux = just another POS OS.

---

### Post by hazza96 on 2005-05-12
[QUOTE=ntrsfrml]TIme for me to go back to windows world..in my book Ubuntu or LInux = just another POS OS.[/QUOTE]
Do you use ADSL, then you use Linux, do you have an MP3 player, then you use Linux, do you have a set-top box, then you use Linux, do you have <insert embedded device here>, then you are (or soon will be) using Linux

I guess you are used to all viruses, spyware, security holes etc. If you make a computer so that stupid people can use it, guess who ends up using it? We can all see your level of understanding with this comment:
[QUOTE=ntrsfrml]why can't they make everything like .exe in windows[/QUOTE]
We can also judge your level of intelligence by you dissing Linux in a Linux forum.  Good luck and don't let the door hit your arse on the way out.

---

### Post by Alexander Kirillov on 2005-05-12
[QUOTE=ntrsfrml]hey guys.. i was trying to install a theme to my Ubuntu install.. downloaded a famous GDM theme from this page [http://www.gnome-look.org/content/show.php?content=21492](http://www.gnome-look.org/content/show.php?content=21492)

Opened >> system>>pref>>Themes>>install new themes>>browsed to the 21492-cleanlinux.tar.gz >>HIt install button>> It gives me = The file format is invalid error :(
[/QUOTE]
There are different kinds of themes. There is "desktop theme" which determines appearance of window  borders, scrollbars, etc, and then there is GDM theme which determnies the appearance of GDM login  screen. They use different formats, obviously, The instructions you were following are for installing **desktop** theme. 

To install GDM theme, go to system->Login screen setup.

---

### Post by ntrsfrml on 2005-05-13
[QUOTE=hazza96]Do you use ADSL, then you use Linux, do you have an MP3 player, then you use Linux, do you have a set-top box, then you use Linux, do you have <insert embedded device here>, then you are (or soon will be) using Linux

I guess you are used to all viruses, spyware, security holes etc. If you make a computer so that stupid people can use it, guess who ends up using it? We can all see your level of understanding with this comment:

We can also judge your level of intelligence by you dissing Linux in a Linux forum.  Good luck and don't let the door hit your arse on the way out.[/QUOTE]

I know LInux is used everyday day life gadget etc.. heck i have Motorola A780 cellphone using it. MY point is that i don't have to compile some source to install programs and utilities on the cellphone or other devices like Camera, MP3 players.. MOst of my Motorola utilities are pre-configured one-click apps. 

Are you trying to say that LInux has been safe cus it takes more than couple of clicks to install stuff? I'm sure the day more than 80% of the world's PC start using LInux.. there willbe more linux virus/vulnerabilities in wild compared to PC today.

I wonder if you even knew anything about keeping your windows box clean from spyware/virus and came linux way..? I'm not trying to diss anybody off.. only saying that it takes some brain storming to install a simple app on Ubuntu. and BTW is spelled ass..not arse..

---

### Post by hazza96 on 2005-05-13
[QUOTE=ntrsfrml]MY point is that i don't have to compile some source to install programs and utilities on the cellphone or other devices like Camera, MP3 players.. MOst of my Motorola utilities are pre-configured one-click apps.[/QUOTE]
Which Ubuntu are you using? I have not had to compile a single thing on mine, maybe you should try Hoary, it's the latest release.

[QUOTE=ntrsfrml]Are you trying to say that LInux has been safe cus it takes more than couple of clicks to install stuff? I'm sure the day more than 80% of the world's PC start using LInux.. there willbe more linux virus/vulnerabilities in wild compared to PC today.[/QUOTE]
Common misconception, that's like saying "When 80% of cars have seat belts they will less safe than the ones without them". One has safety and security built-in, the other does not.

Don't think that they haven't tried writing a virus for Linux. One of the reasons virus writers do what they do is for the prestige, how much cred do you think they would get if they were able to write the first Linux virus? There have been "proof of concept" viruses but they took too much work for anyone to be bothered to infect themselves.

[QUOTE=ntrsfrml]I wonder if you even knew anything about keeping your windows box clean from spyware/virus and came linux way..? I'm not trying to diss anybody off.. only saying that it takes some brain storming to install a simple app on Ubuntu.[/QUOTE]
I know **way too much** about keeping Windows clean of viruses and spyware, it's the main bread and butter of my business. I am thankful that Windows is so crap, I make a good living out of it. I use AVG, Spybot S&D, SpywareBlaster, Ad-Aware and aSquared on the Windows machines. If you keep them up-to-date they do a decent job of keeping Windows as safe as it can be.

[QUOTE=ntrsfrml]BTW is spelled ass..not arse..[/QUOTE]
In whose language? Is it spelt color or colour? Lite or light?

Look I am willing to help you with any problems you might have on Ubuntu. First you have to realise that to learn a different system that it will be .. ah... different. If you want your computer to be just like Windows then run Windows. Linux is Linux and Windows is Windows, they are different once you get over it and get used to it you will be thankful.

---

### Post by ntrsfrml on 2005-05-13
[QUOTE=hazza96]Which Ubuntu are you using? I have not had to compile a single thing on mine, maybe you should try Hoary, it's the latest release.


Common misconception, that's like saying "When 80% of cars have seat belts they will less safe than the ones without them". One has safety and security built-in, the other does not.

Don't think that they haven't tried writing a virus for Linux. One of the reasons virus writers do what they do is for the prestige, how much cred do you think they would get if they were able to write the first Linux virus? There have been "proof of concept" viruses but they took too much work for anyone to be bothered to infect themselves.


I know **way too much** about keeping Windows clean of viruses and spyware, it's the main bread and butter of my business. I am thankful that Windows is so crap, I make a good living out of it. I use AVG, Spybot S&D, SpywareBlaster, Ad-Aware and aSquared on the Windows machines. If you keep them up-to-date they do a decent job of keeping Windows as safe as it can be.


In whose language? Is it spelt color or colour? Lite or light?

Look I am willing to help you with any problems you might have on Ubuntu. First you have to realise that to learn a different system that it will be .. ah... different. If you want your computer to be just like Windows then run Windows. Linux is Linux and Windows is Windows, they are different once you get over it and get used to it you will be thankful.[/QUOTE]
 alright.. then please help me with some basics here. I tried to install to a firefox extension on my 1.0.3 release but everytime i click extention button firefox site forwards me to the newer version page 1.0.4. I downloaded the new version but can't install it :(..Its a Tar.
gz file. DO i have to compile the program first?  Here is a screen shot:

[[IMG]http://img244.echo.cx/img244/5841/firefoxinstall6pw.th.jpg[/IMG]](http://img244.echo.cx/my.php?image=firefoxinstall6pw.jpg)

TIA!

---

### Post by hazza96 on 2005-05-14
Personally I don't install anything from TAR balls, but from the look of the files in that one I would extract the files to a directory (say ~/tmp/firefox) and then run 'sudo firefox-installer' and follow the screen prompts.

---

### Post by ntrsfrml on 2005-05-14
[QUOTE=hazza96]Personally I don't install anything from TAR balls, but from the look of the files in that one I would extract the files to a directory (say ~/tmp/firefox) and then run 'sudo firefox-installer' and follow the screen prompts.[/QUOTE]
Alright I will try that.. also can run me a quick mini tutorial " how to compile/install programs from source"? I have tried following this link [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) but something always goes wrong : /

---

### Post by hazza96 on 2005-05-16
[QUOTE=ntrsfrml]but something always goes wrong : /[/QUOTE]
Man that's like saying "I wanted to drive down to the shop and buy an ice cream to eat, but *something* always goes wrong"

There are so many variables that it is impossible to help you without specifics, has the car got fuel, do you have the keys, is the battery flat, do you know how to drive, do you know the way to the shop, did you take money with you, did you forget your false teeth. The solution to the problem is dependant on which part of the LONG chain is broken.

I suggest reading the tutorial ["How to ask questions the smart way"](http://www.catb.org/~esr/faqs/smart-questions.html), you will get to know that bothering other sentient beings is the **last** step not the first.

---

### Post by ntrsfrml on 2005-05-16
[QUOTE=hazza96]Man that's like saying "I wanted to drive down to the shop and buy an ice cream to eat, but *something* always goes wrong"

There are so many variables that it is impossible to help you without specifics, has the car got fuel, do you have the keys, is the battery flat, do you know how to drive, do you know the way to the shop, did you take money with you, did you forget your false teeth. The solution to the problem is dependant on which part of the LONG chain is broken.

I suggest reading the tutorial ["How to ask questions the smart way"](http://www.catb.org/~esr/faqs/smart-questions.html), you will get to know that bothering other sentient beings is the **last** step not the first.[/QUOTE]

Wow.. i thought you were going to help me.. but you are getting low and low on the talk.. If you really don't wanna help me with Linux..just get outta my thread..aussie retard.

---

### Post by hazza96 on 2005-05-16
[QUOTE=ntrsfrml]Wow.. i thought you were going to help me.. but you are getting low and low on the talk..[/QUOTE]
Low and low? Here is something that might help [ explain my post.](http://dictionary.reference.com/search?q=analogy) 

[QUOTE=ntrsfrml]If you really don't wanna help me with Linux.[/QUOTE]
I do, but you make it ***so*** hard.

How exactly do you intend to stop me? Are you a moderator of this forum? Get a new forum ID because I intend to search the entire forum for posts by this one *every single day*. I just changed my home page to the search results so I don't forget.

I will post a link back to this thread (if I can figure out how the link will go directly to your last response), to warn anyone that might be inclined to respond exactly how you treat people that are genuinely trying to help you. It's not a threat, I just think that those people should know what to expect from you.

My last response may not have been the response you wanted, but it is certainly the response you needed.

---

### Post by hazza96 on 2005-05-16
I just found the exact section that you [need to read.](http://www.catb.org/~esr/faqs/smart-questions.html#id3002586)

---

### Post by dataw0lf on 2005-05-16
[QUOTE=ntrsfrml]Wow.. i thought you were going to help me.. but you are getting low and low on the talk.. If you really don't wanna help me with Linux..just get outta my thread..aussie retard.[/QUOTE]

This sort of behavior is not tolerated on these forums.  You might be frustrated, but let's not resort to name calling.

If people don't start cooling off, this thread will be locked.

---

### Post by hazza96 on 2005-05-16
[QUOTE=dataw0lf]If people don't start cooling off, this thread will be locked.[/QUOTE]
Ok, I will change my home page back to the [ Userfriendly](http://www.userfriendly.org/) comic and forget this guy even exists.

---

### Post by dataw0lf on 2005-05-16
Thank you Harry.

---

### Post by hazza96 on 2005-05-17
[QUOTE=dataw0lf]Thank you Harry.[/QUOTE]
Hey with his posts getting deleted and even *quotes* from the post being removed from my responses (by "bored2k"), it won't be long before everyone forgets that he exists.

---

