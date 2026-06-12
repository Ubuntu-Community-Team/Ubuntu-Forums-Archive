---
title: "OS conversion"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by roseynose on 2006-02-21
Okay, i have mastered all of the Windows XP,  and I have been a long time Mandrake Linux user off and on for several years. Because money is tight through Mandrake (Mandriva, whatever you want to call it), I am deciding to switch over to Ubunto Linux (Madriva wants you to join their club for updates are software that you need).  I am cautious about compatibility.  I am currently running Windows XP and Mandriva on the same system on a i386 system (Madriva calls it i586, either way it's a x86 system).  I have to stick to Windows XP due to a few programs that cost me 4k that I am not willing to quite give up. Here are my set of questions, feel free to answer them individually:

When it comes to packages, do deb files act the same way as rpm files? Most rpm files install directly from my desktop which is a plus (I'm hoping deb files do the same). I don't know much about programming unless it is in a step by step howto - and even then, I don't always get it right.

Even though I will back up all of my data, will I be able to keep all of my programs and use them on the same partition or do I need to to start all over from scratch by installing the packages individually?

I am accustomed to KDE, but like to switch to different desktops every once in awhile (Gnome, ICE, winmaker, etc.).  Am I able to, for example, add KDE to Ubuntu and be able to switch desktops? 

Finally, Mandriva has it where I can use Gnome applications on a KDE desktop. Would I be able to do the same on a Gnome desktop (open KDE applications on a Gnome desktop)? I believe a desktop is based on personal preference and shouldn't matter, but I want to be sure.

I am in the process of waiting for the Ubuntu disks in the mail, so I guess most of the questions I have that are not listed here would be answered once I pop in the CD. Thanks.

---

### Post by aysiu on 2006-02-21
[QUOTE=roseynose]
When it comes to packages, do deb files act the same way as rpm files? Most rpm files install directly from my desktop which is a plus (I'm hoping deb files do the same). I don't know much about programming unless it is in a step by step howto - and even then, I don't always get it right.[/quote] KPackage can sort of do this with .deb files, but mainly, you can install them from the command line ```
sudo dpkg -i *packagename*.deb
``` And that won't resolve dependencies. Fortunately, Ubuntu has a *huge* set of online repositories, so you can install things with apt-get (instead of urpmi)--you never even see the .deb files you download.

> 
Even though I will back up all of my data, will I be able to keep all of my programs and use them on the same partition or do I need to to start all over from scratch by installing the packages individually? You need to start from scratch.

> 
I am accustomed to KDE, but like to switch to different desktops every once in awhile (Gnome, ICE, winmaker, etc.).  Am I able to, for example, add KDE to Ubuntu and be able to switch desktops?  Yes. You install the *kubuntu-desktop* package and then you have KDE. You can also install IceWM, Fluxbox, and XFCE4.

> 
Finally, Mandriva has it where I can use Gnome applications on a KDE desktop. Would I be able to do the same on a Gnome desktop (open KDE applications on a Gnome desktop)? I believe a desktop is based on personal preference and shouldn't matter, but I want to be sure. Yes. You can use any application on any desktop environment.

---

### Post by eylisian on 2006-02-21
"When it comes to packages, do deb files act the same way as rpm files? Most rpm files install directly from my desktop which is a plus (I'm hoping deb files do the same). I don't know much about programming unless it is in a step by step howto - and even then, I don't always get it right."

Slightly different =) I don't know about installing from your desktop but there are excellent package management tools available. It's all built on dpkg, apt, aptitude and the GUI Synaptic. 

"Even though I will back up all of my data, will I be able to keep all of my programs and use them on the same partition or do I need to to start all over from scratch by installing the packages individually?"

Hmmmm. what will depend is the version level of the apps you were using on mdk. I commonly back up my entire home dir and just restore from that using rsync after a rebuild. That could be kind of screwy depending on where mdk keeps things but it might work for you. For apps utilizing db's or conf files you will need to have good copies of said db's and conf's to mv into place.

"I am accustomed to KDE, but like to switch to different desktops every once in awhile (Gnome, ICE, winmaker, etc.). Am I able to, for example, add KDE to Ubuntu and be able to switch desktops?"

Yes. Without much pain either.

" Finally, Mandriva has it where I can use Gnome applications on a KDE desktop. Would I be able to do the same on a Gnome desktop (open KDE applications on a Gnome desktop)? I believe a desktop is based on personal preference and shouldn't matter, but I want to be sure."

Every Linux distro I have tried (debian, ubuntu, suse/novell, gentoo, mdk and fc) seems to allow for running Gnome apps under KDE and vice versa.

" I am in the process of waiting for the Ubuntu disks in the mail, so I guess most of the questions I have that are not listed here would be answered once I pop in the CD. Thanks."

IMHO you'll like the change.

---

### Post by heimo on 2006-02-21
Hi! Welcome to Ubuntuforums!


If I were you, I'd backup my files and make a fresh install of Ubuntu. You probably want to keep your homedir, but trying to keep any application settings (other than firefox bookmarks and such) can be difficult (may cause unexpected problems because of different versions of software).

Debian packages (.deb) are wonderful and dependencies work very well. There's no need to download packages individually, you should stick to using Synaptic Package Manager (or Kynaptic), or apt-get to install all the software. You can check what's available in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but the idea is to use your package manager to do all the work.

This forum is excellent place for asking any questions you may have. Also check [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/) which contains lots of information. 

Aysiu was fast - so I won't repeat some of the answers he already gave about running KDE/Gnome applications.

---

### Post by abhaysahai on 2006-02-22
Go ahead an install Ubuntu. 
Installing new applications is very easy with synaptic.. 
as for KDE,  install kubuntu-desktop ( again in synaptic). 
If you are able to install packages in Mandriva, you will find synaptic equally easy. 

And yes Ubuntu is and will always remain FREE -- no subscription.

---

