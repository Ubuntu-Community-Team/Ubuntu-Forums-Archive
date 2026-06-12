---
title: "Feisty Fawn, It is not what people say, at least for me."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-01
Hi
Today i finally installed Ubuntu from Its DVD but.....

1- why there is no package selection during installation? I have install it from a 4GB DVD nad it give me the same system that was shown in live demo. 

2-Why it has no Graphical boot loader? 

3-Even with installing restricted drivers it does not support higher resolution for my monitor (OpenSuse 10.2 does) It just allows 1024*768 on 50HZ (it has up to 55 Hz which 55Hz is not stable)

3-Where are netbeans, glassfish and sun java sdk? I used its package manager to search for them with no luck (searching DVD as software source)

---

### Post by Inxsible on 2007-05-01
> **legolas_w said:**
> Hi
Today i finally installed Ubuntu from Its DVD but.....
 
1- why there is no package selection during installation? I have install it from a 4GB DVD nad it give me the same system that was shown in live demo. 
 
2-Why it has no Graphical boot loader? 
 
3-Even with installing restricted drivers it does not support higher resolution for my monitor (OpenSuse 10.2 does) It just allows 1024*768 on 50HZ (it has up to 55 Hz which 55Hz is not stable)
 
3-Where are netbeans, glassfish and sun java sdk? I used its package manager to search for them with no luck (searching DVD as software source)
 
As for 3), not everyone requires netbeans and Sun Java SDK. You can always get those from synaptics manager or aptitude

---

### Post by jpatton on 2007-05-01
You have #3 listed twice, so I will take a stab at the second #3.

sudo apt-get install glassfish

worked for me, jdk is downloaded as part of glassfish.

sudo apt-get install netbeans

haven't tried that, but it's most likely something along that vein. You may also try

sudo aptitude

and then search for netbeans, as it may not be "called" netbeans, if you follow.

As to the first #3, I think you can do something like

sudo dep-pkg reconfigure xserver-xorg

or something similar, can't remember if that's the correct syntax.

As for #2, I thought grub was a gui boot loader, perhaps you can modify it's configuration file, also, if you only have ubuntu on the disk, it may not appear by default. I know when I was dual-booting Windows/Ubunut on this box it would display an interface on boot that allowed me to pick.

#1, the only .iso I've found for ubuntu is a cd-image, so I don't really know what to say about the dvd image you have. But I noticed that as well, that you really didn't get much of a choice as to what you wanted or didn't want by default. But I believe that lack of choice is _by design_

Someone more in the know than I may wish to chime in here as well.

---

### Post by starcraft.man on 2007-05-01
1) Never used the DVD I prefer downloading and adding exactly what I want. Someone else explain this please.

2) Why would you want a graphical bootloader, they take more time to load... GRUB boots in 1 second. Not to mention all boot loaders do is switch the OS you boot, thus GRUB fullfills its purpose well. If you MUST have a graphical bootloader, go look at GAG in sourceforge.

3) I am not sure exactly why this is, I still prefer the envy script installer to the automatic restricted manager. It probably just needs a small edit in the xorg.conf file. 
Might try running:

```
sudo dpkg-reconfigure xserver-xorg
```

Long as it detects your monitor it should give you right resolution.

4)You likely don't have all the repos in your sources list because I installed sun java first thing days ago. (dunno about glass fish or netbeans).
Try these repos: [Link.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

No one ever said Feisty would be perfect. Hope that helps.

Edit: Heh, I guess I took too long... was multitasking :)

---

### Post by Sef on 2007-05-01
> 1- why there is no package selection during installation? I have install it from a 4GB DVD nad it give me the same system that was shown in live demo.

Because it's not the way Ubuntu is set up.  If you want to install all your packages then a distro like Gentoo or Slackware would be better.

---

### Post by Zalbor on 2007-05-01
For netbeans, you can just download an installer which works great.

---

### Post by jamesstansell on 2007-05-02
> **Zalbor said:**
> For netbeans, you can just download an installer which works great.
Or, if the installer bothers you this post might be of interest.  Note that it means adding an additional software repository to your system.

"If you would to take advantage of this fix right away (so you don't have to download the tarball separately) here's how:"

[http://blogs.sun.com/tmarble/entry/netbeans_in_ubuntu](http://blogs.sun.com/tmarble/entry/netbeans_in_ubuntu)

---

### Post by huggy77 on 2007-05-14
i love fiesty - i am configging glassfish from apt now...  if i could play midievil2 total war on ubuntu i would dump my windows machine in a second...  That and visio are the only things i use my windows box for...

---

