---
title: "I need an Expert, No.. I REALLY Do."
date: 2011-08-29
forum: Any Other OS
---

### Post by John Phoenix on 2011-08-29
This is about Zorin. Before anyone tells me to go to the Zorin forum for help, I have done that. They Cannot help. This is an Ubuntu Installer Grub problem. 

It's a long story so best you read the thread HERE: [http://www.zoringroup.com/forum/viewtopic.php?f=4&t=774&sid=f86b8248bd38c2d528b44ffc62883be6](http://www.zoringroup.com/forum/viewtopic.php?f=4&t=774&sid=f86b8248bd38c2d528b44ffc62883be6)

I need a solution to this and also to do what I suggested in my last post on page 3. 

I await your findings.

(Mod, I disagree with your choice to move this out of the Ubuntu Install forum as I feel no matter what the OS is called, This is directly related to an Ubuntu Installer problem therefore I deemed it to be in the correct place)

---

### Post by MAFoElffen on 2011-08-29
> **John Phoenix said:**
> This is about Zorin. Before anyone tells me to go to the Zorin forum for help, I have done that. They Cannot help. This is an Ubuntu Installer Grub problem. 

It's a long story so best you read the thread HERE: [http://www.zoringroup.com/forum/viewtopic.php?f=4&t=774&sid=f86b8248bd38c2d528b44ffc62883be6](http://www.zoringroup.com/forum/viewtopic.php?f=4&t=774&sid=f86b8248bd38c2d528b44ffc62883be6)

I need a solution to this and also to do what I suggested in my last post on page 3. 

I await your findings.

(Mod, I disagree with your choice to move this out of the Ubuntu Install forum as I feel no matter what the OS is called, This is directly related to an Ubuntu Installer problem therefore I deemed it to be in the correct place)
If you only knew the half of it... This subforum they moved this to is one they told me was in effect closed a few months ago.  LOL  And your question is basically just a Grub Question.

Grub2 is basically the same for all distro's that use it.  If you dl an Ubuntu LiveCD and followed these Grub2 install instructions:
[Reinstall Grub2 - Copy LiveCD Files]("https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files") 
That should do you.  Remember to install to the mbr of the drive and not to a partition.  (Translation of to /dev/sda; not to /dev/sda1) After the install, while still in a terminal, run:
```

sudo update-grub

```To run the os_prober and to generate the menu file (grub.cfg).

If you have troubles... post here (I'll try to keep an eye on it-- or start a thread in install (where I usually reside, with about 5 other friends that are handy with grub, but just mention it as a grub2 problem.

Sidenote-- Posted that way, we can and do take care of Grub Legacy, Grub2, LILO, PLOP, etc. issues.  There is quite a wealth of active community support here!

---

### Post by John Phoenix on 2011-08-29
Thanks.. I'll give it a shot. That was way more detailed info than anyone else has come up with.. is Grub2 often this problematic? Perhaps they shouldn't use it?

When you say, "After the install, while still in a terminal, run:

sudo update-grub 

Do you mean before the final reboot while I'm still in the live CD?

You do know I cannot do this with an Ubuntu live cd.. I need to use the Zorin live CD...

---

### Post by MAFoElffen on 2011-08-30
> **John Phoenix said:**
> Thanks.. I'll give it a shot. That was way more detailed info than anyone else has come up with.. is Grub2 often this problematic? Perhaps they shouldn't use it?

When you say, "After the install, while still in a terminal, run:

sudo update-grub 

[COLOR=Red]Do you mean before the final reboot while I'm still in the live CD?[/COLOR]

You do know I cannot do this with an Ubuntu live cd.. I need to use the Zorin live CD...
Yes... before yuo reboot.

Is Grub usually problematic?  Not usually, but many distro's use it in many ways for many hardware combinations.  Imagine trying to use something small and basic as "this: will work fro anything at all times...  Theres going to be situations where it will have to be tweaked to work.  There are install options that some assume wrong, then there is problems... If it cannot read or write to a file system, problems... Now it is tied more into passing info on to the kernel and to the graphics X-Session...

Is it usually ? No, but can happen and does.  When the config is then worked out, then "it's" sovled.

---

