---
title: "removing programs question"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-11-13
I want to take off some programs off my computer.  For example I want to take of Sound Juicer.  But when I go to synaptic and try to remove that, it says that it will then remove the Ubuntu Desktop also.  Does that just mean it is taking out a program that came with the Ubuntu Desktop and that it will not be complete like a stock setup or does it mean I am taking the WHOLE Ubuntu desktop off.  

Basically I have other programs that do a better job than the ones that came with Ubuntu and I do not need the normal Ubuntu ones.  I am worried that I am having too many dependency crosses by having redundant programs.  SO I want to thin down my program list.

Like I have K3B and it is FAR superior so I don't want Sound Juicer.

Is there any where you can point me for answers or is there anyone who can help?

Thanks

---

### Post by Inxsible on 2007-11-13
you can remove sound-juicer. However, this will also remove ubuntu-desktop (which is only a meta-package).

ubuntu-desktop defines a set of apps that come with the default ubuntu installation.
You can remove it without any worries. 

The only catch is that if and when you try to upgrade the OS from lets say Gutsy to Hardy Heron,  you will have to re-install ubuntu-desktop and then perform the upgrade. If you plan NOT to upgrade, or if you are going to do a clean install (like me) then it won't be a problem at all

I too have removed sound-juicer, rhythmbox, evolution etc which I never used.

---

### Post by mcduck on 2007-11-13
Removing the ubuntu-desktop package doesn't remove your desktop.

It's just an empty package that has all the programs included on default Ubuntu install as it's dependencies. So when you install ubuntu-desktop it will bring along everything included in the default setup. But removing it will remove nothing else, as no other package depends on ubuntu-desktop.

The only thing is if you later on plan to upgrade to new Ubuntu version you should install ubuntu-desktop again to make sure you get all the new stuff included in the new Ubuntu version.And after the upgrade you can remove it again if you want.

---

### Post by overdrank on 2007-11-13
> **nynoah said:**
> I want to take off some programs off my computer.  For example I want to take of Sound Juicer.  But when I go to synaptic and try to remove that, it says that it will then remove the Ubuntu Desktop also.  Does that just mean it is taking out a program that came with the Ubuntu Desktop and that it will not be complete like a stock setup or does it mean I am taking the WHOLE Ubuntu desktop off.  

Basically I have other programs that do a better job than the ones that came with Ubuntu and I do not need the normal Ubuntu ones.  I am worried that I am having too many dependency crosses by having redundant programs.  SO I want to thin down my program list.

Like I have K3B and it is FAR superior so I don't want Sound Juicer.

Is there any where you can point me for answers or is there anyone who can help?

Thanks

HI and I really hate to do this after what has happened on the forums today.
[http://ubuntuforums.org/showthread.php?t=611908](http://ubuntuforums.org/showthread.php?t=611908)
But you can try the command ```
sudo apt-get remove sound-juicer
``` I just tried it on my gutsy install and it only removed two packages. good luck!

---

### Post by nynoah on 2007-11-13
Thanks for the answers.  I have a lot of programs I want to get rid of.  None of them are part of the main Ubuntu architecture.  More just user programs.  I will start to thin out my computer some.  I have too many things on here.  Ubuntu has some nice programs out of the box.  But most of the Ubuntu programs are too simplistic for me.

Example - I can not configure Sound Juicer to rip a different bitrate.  But with K3B I can change the bitrate to anything I want through a graphical interface.  Its hidden but it is there and can be changed.  I have K3B ripping Cds at a V0 (the highest variable bit rate available)

I don't use pidgen because it can not use a web cam with it.  But I can with Kopet.  

The only audio program I use is Amarok......so I don't need the Ubuntu one.

If Kubuntu worked better I would use that, but Ubuntu is just more stable now since the arrival of 7.10 Gutsy.  Thank god they got the mounting of hard drive issues worked out.

Now if only I can get to see an image file when I am trying to upload it online.  I really hate having to go by tag alone.

Thanks for the fast response.

---

### Post by stchman on 2007-11-13
> **nynoah said:**
> I want to take off some programs off my computer.  For example I want to take of Sound Juicer.  But when I go to synaptic and try to remove that, it says that it will then remove the Ubuntu Desktop also.  Does that just mean it is taking out a program that came with the Ubuntu Desktop and that it will not be complete like a stock setup or does it mean I am taking the WHOLE Ubuntu desktop off.  

Basically I have other programs that do a better job than the ones that came with Ubuntu and I do not need the normal Ubuntu ones.  I am worried that I am having too many dependency crosses by having redundant programs.  SO I want to thin down my program list.

Like I have K3B and it is FAR superior so I don't want Sound Juicer.

Is there any where you can point me for answers or is there anyone who can help?

Thanks

Make sure and use the autoremove in apt-get

```
sudo apt-get -y autoremove sound-juicer
```

This will remove any unused dependencies.  Make sure to clean and residual config files from synaptice after you are done.

---

### Post by nynoah on 2007-11-13
well it is ok for me to just go to synaptic and just do it as "mark for complete removal"  or do I need to do something else?

---

