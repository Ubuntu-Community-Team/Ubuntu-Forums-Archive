---
title: "Some questions from a new user..."
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by yeahyeahyeah on 2005-11-27
Hello all.

I just installed Ubuntu on my laptop, and I have two preliminary questions:

1. This is an IBM Thinkpad. I've had it for a year, and every few months I "ghost" my XP install using Rapid Restore (which came with the machine) so a few months out I can re-image the machine with a clean install. Everytime I "ghost", I include more of the changes I've made since the last time. The result is that now, when I re-image, I'm using a very optimized XP install.

I've put Ubuntu on it now, dual-booting with XP. So far everything is fine. Before I start going crazy with the customization, I'd like to know if it's possible to clone my Linux install so I don't have to start fresh every few months.

So I guess question (1a) is are there any IBM users out there that are using Rapid Restore to "ghost" their entire machine, including Linux partitions?

If not, then (1b) what are my options? Is it easy to just backup my home directory, blow away my machine, re-install Umbuntu, and then copy my home directory back? Will that do the trick? Or will it do the trick mostly? Is there a clone program for Linux that will work in my situation?


Question #2: Are there any issues opening the automatic package installer to the unofficial community repository? This morning I wanted to install "Scorch 3D", but it was not available with the default settings. A message popped-up saying that it was available in the "universe repository", or whatever. So I enabled that, and installed a few games. Then the auto-updater told me there were some new updates for my system (I had performed an update recently, so I only assume that these were updates from the "universe repository"). I tried removing the unofficial repository from the search, but the "new" updates kept coming back. So I just installed them all (there were 13 or 14).

Is there any danger or dis-advantage to using the universal repository? I sort of understand what it is, I just don't know if I should be using it.

Thanks in advance.

---

### Post by Joey French on 2005-11-27
Have you gone down [this]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse") path to enabling the sources.list?
If so, then with the expanded (Universe, Multiverse, etc...)repositories you may download at will. It is not recommended that one use UNofficial repos on a regular basis. I have a few repos in my sources.list that are commented out, so that I may use them ONLY for the odd program I can't get otherwise. Beware, though- Using unofficial repos on a regular basis can and will break your system.

Joey French

---

### Post by ssam on 2005-11-27
i back up my home and /etc directories. when a new ubuntu comes out i usually do a clean install and only copy back what i need.

it depends what customisations and changes you make.

if you start installing new programs from source then you might want to back up your source folder. but if you only do this to get hot new versions of stuff, and the new version is in the next ubuntu, then you be better off with ubuntus build.

some people never do a clean install but just keep on tweaking and updating for years. i think you have to be very neat, organised and knowledgeble to do this.

i tend to have made a mess after 6 months and a clean up is good.

---

### Post by yeahyeahyeah on 2005-11-27
Thanks to both of you.

Most of the customizations, I think, would be related to my user, so I think that backing up my home directory should do the trick.

The rest of the stuff (i.e. making it so my XP directories show up in Ubuntu) should all be in /etc, I guess, so that should cover the rest.

As a side question: If I install stuff like games and apps...where are those kept? Or would I need to re-install any games/apps when I re-installed Ubuntu (this gets back to my cloning question).

Also, if I dual-boot with XP (NTFS, existed prior to Ubuntu), is there a way to run or emulate XP (i.e. Virtual PC for the Mac)?

Thanks again.


[QUOTE=ssam]i back up my home and /etc directories. when a new ubuntu comes out i usually do a clean install and only copy back what i need.

it depends what customisations and changes you make.

if you start installing new programs from source then you might want to back up your source folder. but if you only do this to get hot new versions of stuff, and the new version is in the next ubuntu, then you be better off with ubuntus build.

some people never do a clean install but just keep on tweaking and updating for years. i think you have to be very neat, organised and knowledgeble to do this.

i tend to have made a mess after 6 months and a clean up is good.[/QUOTE]

---

### Post by Joey French on 2005-11-27
You could try VMWare, I have used it before. Someone with more experience in that department should chime in, though. Wine works (it is now beta), but it is not the greatest solution. I have successfully gotten it to run some programs after some tweaking.

---

### Post by jackmacokc on 2005-11-27
[QUOTE=yeahyeahyeah]).

Also, if I dual-boot with XP (NTFS, existed prior to Ubuntu), is there a way to run or emulate XP (i.e. Virtual PC for the Mac)?

Thanks again.[/QUOTE]

sure is
[http://www.ubuntuforums.org/showthread.php?t=39513&highlight=vmware]("http://www.ubuntuforums.org/showthread.php?t=39513&highlight=vmware")

---

