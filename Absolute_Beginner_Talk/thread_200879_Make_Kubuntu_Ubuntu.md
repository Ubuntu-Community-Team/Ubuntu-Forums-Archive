---
title: "Make Kubuntu Ubuntu"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Sitix on 2006-06-20
Hey,

I have been running Kubuntu, Ubuntu, Edubuntu and Xubuntu all on my computer to test everything to see what I like most. But I installed Kubuntu, and I want to switch to Ubuntu. Now that's not a problem, aptitude install ubuntu-desktop did the trick for me. I even got it to show the Ubuntu splashscreen when loading the OS... but it's not a real Ubuntu system.

Is there a way I can throw all those systems off my computer to install only the Ubuntu system on the base system, but while keeping my home folder. (If possible, an easy way O:) ) Or do I really need to make a different partition for my home folder, then copy my home folder there, install Ubuntu Linux on the earlier partition and then put my home folder back to where it belongs? I really hope there is a simpler solution... I don't like working with stuff like fstab... 

I have about 6,5GB in my home folder, and I don't feel like burning 8 CD's to keep it all... :P So the actual question is: how can I make my system a 'fresh' Ubuntu system with keeping my /home folder. I don't care about the programs by the way.

Can someone help me with that?

---

### Post by siccness on 2006-06-20
I'm not sure, but for future reference you could have /home as a separate partition.

---

### Post by jimrz on 2006-06-20
[QUOTE=Sitix]Hey,

I have been running Kubuntu, Ubuntu, Edubuntu and Xubuntu all on my computer to test everything to see what I like most. But I installed Kubuntu, and I want to switch to Ubuntu. Now that's not a problem, aptitude install ubuntu-desktop did the trick for me. I even got it to show the Ubuntu splashscreen when loading the OS... but it's not a real Ubuntu system.

Is there a way I can throw all those systems off my computer to install only the Ubuntu system on the base system, but while keeping my home folder. (If possible, an easy way O:) ) Or do I really need to make a different partition for my home folder, then copy my home folder there, install Ubuntu Linux on the earlier partition and then put my home folder back to where it belongs? I really hope there is a simpler solution... I don't like working with stuff like fstab... 

I have about 6,5GB in my home folder, and I don't feel like burning 8 CD's to keep it all... :P So the actual question is: how can I make my system a 'fresh' Ubuntu system with keeping my /home folder. I don't care about the programs by the way.

Can someone help me with that?[/QUOTE]

you already have the real ubuntu system...

GNOME / KDE / XFCE / et al are merely windows managers...

the underlying system remains the same whichever one(s) you choose to use

---

### Post by Sitix on 2006-06-20
Yeh, maybe that's best anyways... but I actually don't feel comfortable with partitioning it again, since I tried something similar last time and it screwed up my Linux. It's almost five o clock in the morning and I didn't sleep yet... I think a mistake is easily made :P

But I'll try it then, it's better to do it directly, else I won't do it anyway because 'things work'... :) if you don't hear from me in the upcoming few hours you know I either fell asleep or my computer has repeated the festivity of crashing because of me making a stupid mistake. ;)

Thanks :)

@jimrz: I know I am running the ubuntu base system, but it's not clean anymore because I used all those different window managers. It just doesn't work properly anymore, and I want to fully switch to Ubuntu with a clean system, and a system running ONLY Gnome. Now, I can't remove KDE for example. ;-)

---

### Post by glotz on 2006-06-20
See [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by fritz_monroe on 2006-06-20
And if you wanted to go back to **just** Ubuntu, you could remove KDE and XFCE.  Ubuntu makes use of Gnome.

---

### Post by Sitix on 2006-06-20
[QUOTE=fritz_monroe]And if you wanted to go back to **just** Ubuntu, you could remove KDE and XFCE.  Ubuntu makes use of Gnome.[/QUOTE]

That's the problem, it won't allow me to uninstall KDE :mad: I thought root could do what he wants [-(

@glotz: I'm gonna try that, it looks like it will work.

---

### Post by Sitix on 2006-06-21
[QUOTE=glotz]See [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)[/QUOTE]

Thanks! This worked! I had to do it twice though because I couldn't delete kdm with gdm running since there was some instance of kdm running or something... I don't know and actually not feeling like trying it out, but for the rest it worked perfectly!

Thanks ^^

---

### Post by glotz on 2006-06-21
:)

---

