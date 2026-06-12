---
title: "Which version do I have?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by PsiKloPx on 2006-11-08
Here's an absolute beginner question - I installed Ubuntu 6.06 from a DVD in a magazine, but my boot screen says kubuntu.  When I click the "about" selection it says ubuntu 6.10 (I'm guessing it updated through synaptic package manager?)  Not a big deal, just wondering!

Thanks!

---

### Post by Sef on 2006-11-08
To be sure answer this question:

1) Is your task bar on the top or bottom of the Monitor?  If it is on top, it would be ubuntu.  If on the bottom, it would be Kubuntu.

---

### Post by Blutack on 2006-11-08
Kubuntu and ubuntu have the same internals, share many programs, and will both run the same programs.  The only difference is that traditional ubuntu uses the Gnome desktop environment (the bit you see and click around in) and Kubuntu the (awesome) KDE.  Its a personal choice and I'm not going to add to the terabytes of arguments over which is better.  If it's brown its ubuntu, if its blue its probably kubuntu.  To change between open a terminal and type sudo apt-get install kubuntu-desktop or ubuntu-desktop depending on which one you want.  There's also XFCE, another desktop environment which is faster but a bit feature light - sudo apt-get install xubuntu-desktop.
hope that helps

Damn Sef, you beat me.

---

### Post by GStubbs43 on 2006-11-08
> **Blutack said:**
>  sudo apt-get install kubuntu-desktop ... sudo apt-get install xubuntu-desktop.


Use ```
sudo *[aptitude]("http://www.psychocats.net/ubuntu/kde")* install kubuntu-desktop
``` instead. :)

---

### Post by Blutack on 2006-11-08
Eeek...what have I been doing wrong all these years?  Apt-get has always worked for me.  I don't like aptitude, it doesn't have super cow powers.

---

### Post by Sef on 2006-11-08
> Eeek...what have I been doing wrong all these years? Apt-get has always worked for me. I don't like aptitude, it doesn't have super cow powers.

Actually apt-get don't have super cow powers.  Aptitude will remove all dependencies upon removal; apt-get won't.  (Removal of dependencies requires using aptitude to install.)

---

### Post by Blutack on 2006-11-08
...
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.  

So huh.
As the informative part of your post, I never knew that!  Many thanks, I always wondered why both apt-get and aptitude were included.  But surely when the system is initially installed (whenever I've used an alternate install cd) apt is used, not aptitude.

---

### Post by Blutack on 2006-11-08
Oh...try apt-get moo

---

### Post by bsussman on 2006-11-08
> **GStubbs43 said:**
> Use ```
sudo *[aptitude]("http://www.psychocats.net/ubuntu/kde")* install kubuntu-desktop
``` instead. :)

Just for all those new to linux (I am not one of them), why?

Please include dpkg, and synaptic and update-manager in your answer to make it helpful.

---

### Post by Blutack on 2006-11-08
It apparently automagically removes packages which aren't required by anything anymore, if they were installed through aptitude.  Means if he wants to go back to the other DE (say he's sick of how evil gnome is) it will remove all the unused gtk libs and save HD space.  I can't fit dpkg, update manager and synaptic into that explanation though, I'm sorry.  I'm used to apt-get but I can see why it would be useful.  Even if it doesn't have super cow powers.

---

### Post by PsiKloPx on 2006-11-08
Ok, now that I know that I have Ubuntu, I think I would like to try the KDE desktop.  But I am afraid of cows. Especially super ones.

So if I want to make sure that I can easily switch back to the Ubuntu desktop (on the outside chance that I don't care for the super-cow-powered KDE!), which command should I use - get or aptitude? :-k

---

### Post by PsiKloPx on 2006-11-08
I chose aptitude. But I got the following:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Luckily, no cows.

A quick check in synaptic package manager shows that both ubunto-desktop and kubunto-desktop are installed (I guess).  So how do I switch?
Thanks!

---

### Post by PsiKloPx on 2006-11-08
Ok, nevermind. A cow suggested that I log out and back in and select a new session from there.  

I am now grazin' on the blue desktop!

ThanX!

---

### Post by jeffster1970 on 2006-11-09
My understanding was that before you do a 'sudo aptitude install kubuntu-desktop' you should do a 'sudo aptitide update'  :-k  Just went to the website where i saw that...and...right..follow those above instructions...and it will all be good. :twisted:   No...just joking..about that face.  You should update before you install..and..don't say 'kde-desktop' do 'kubuntu-desktop' or whatever it was that you were going to install (ubuntu, xubunti or kubuntu)  Speaking of which..can you do a edubuntu?  8) Seems that you can...haha..now i have 4 sessions to play around with.  Ubuntu kicks :KS

---

### Post by Epperly on 2006-11-09
> **Sef said:**
> Actually apt-get don't have super cow powers.  Aptitude will remove all dependencies upon removal; apt-get won't.  (Removal of dependencies requires using aptitude to install.)
Yeah I installed Kubuntu once with apt-get and it sucked when I wanted to remove it. I did it again with aptitude and it was so much better, to remove you just did sudo aptitude remove whatever kubuntu is and it took everything that it installed it with (which is like 57 files)

---

### Post by Infamous Flame on 2006-11-15
Is there a terminal command to check your ubuntu version? I tried to update to a newer release, following instructions... somewhere... but I'm not sure if it's actually updated lol, nothing seems different.

---

### Post by macdo on 2006-11-15
aptitude does however have something mobile inside... 
Try aptitude moo
then aptitude -v moo
then aptitude -vv moo

then go on adding v's

---

### Post by Epperly on 2006-11-15
> **Infamous Flame said:**
> Is there a terminal command to check your ubuntu version? I tried to update to a newer release, following instructions... somewhere... but I'm not sure if it's actually updated lol, nothing seems different.
You go to System>About Ubuntu
or to check you Linux kernal version either view it in GRUB or in the terminal type ```
uname -a
```

---

### Post by Infamous Flame on 2006-11-26
> **Epperly said:**
> You go to System>About Ubuntu
or to check you Linux kernal version either view it in GRUB or in the terminal type ```
uname -a
```

Forgot to reply to this :eek: 

Thanks :)

---

