---
title: "fedora core 5/xp dual boot (2 hard drives)"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by slade on 2006-08-20
a while ago when my computer died i installed ubuntu on another computer, which i used for some time.  that was when i joined ubuntu forums.  when i got a new computer it came with windows XP preinstalled, and regretably thats what ive been using since.

i recently decided i wanted to get back into the linux world (particularly after dealing with window's indian tech support to address the fact that it keeps saying my copy of windows is not genuine, despite the fact that it came preinstalled).  anyway, i tried a few different boot discs and finally installed a copy of fedora core 5.  i have 2 200GB SATA hard drives on my computer, so i unhooked the windows hard drive and installed fedora.  i was planning to just play around with it since ive always had one or two problems with linux, and maybe install a dual boot later.  but fedora is running fine so i decided to heck with it, ill make it a dual boot now.

the problem is ive already installed fedora (and grub) so after i hooked up the windows hard drive, grub didnt list windows xp.  i had planned to just reinstall fedora and set up grub to recognize windows, but since it recognizes that fedora is already installed the installation doesnt go through.

so, my question is, do i have to reformat the hard drive and reinstall fedora, or is there an easier way to just reconfigure grub?

also, i have a few other questions relating to fedora:

i think i recall hearing that fedora core 5 comes with both gnome and KDE, but it always boots in gnome.  how do i switch to KDE?

once i do get a dual boot set up, is there a way that i can keep things like firefox bookmarks or trillian/GAIM logs as a single file that each OS uses?

i would ask about getting mp3 support, but im sure i can figure that out on my own fairly easily.

---

### Post by DC@DR on 2006-08-20
Have you already asked yourself which linux distro this forum is dedicated to? It's for Ubuntu/Kubuntu and not FC at all...By Googling I found this link that I think it might be the right place for your question --> [http://www.fedoraforum.org/](http://www.fedoraforum.org/) ...Good luck with FC and if one day you dislike FC, think about Ubuntu/Kubuntu as an alternative, but not Windoze again. Don't make mistake again to pay any hard-earned pennies to Sir. Bill Gates any more, his Microsoft is already so damn rich :)

---

### Post by shoot2kill on 2006-08-20
if u dont mind formatting ur HDD. then install windows then install linux... dont know ins and outs cos i only worked with ubuntu (hense the ubuntuforums..)

u could try a forum dedicated to fedora...

---

### Post by slade on 2006-08-20
> **DC@DR said:**
> Have you already asked yourself which linux distro this forum is dedicated to? It's for Ubuntu/Kubuntu and not FC at all...By Googling I found this link that I think it might be the right place for your question --> [http://www.fedoraforum.org/](http://www.fedoraforum.org/) ...Good luck with FC and if one day you dislike FC, think about Ubuntu/Kubuntu as an alternative, but not Windoze again. Don't make mistake again to pay any hard-earned pennies to Sir. Bill Gates any more, his Microsoft is already so damn rich :)

i thought it would go without saying that 1) im already a member here, 2) the majority of people here have worked with multiple OSes, and 3) since the problem is with grub and booting the system, its not an OS specific issue anyway.  im sure the same thing would have happened had i installed ubuntu instead.

i might as well sign up for fedora forums too, i guess.

and yes, while i have had problems with linux before, none of those problems have been asking me to pay $100 for a copy of software i already legally use.  i only used it because it was preinstalled, but i want to keep it because of software.

> **shoot2kill said:**
> if u dont mind formatting ur HDD. then install windows then install linux... dont know ins and outs cos i only worked with ubuntu (hense the ubuntuforums..)

u could try a forum dedicated to fedora...

i cant format my hard drive, since windows came preinstalled.  and theres no reason to do that anyway, since i have 2 hard drives.  all im asking is if theres an easy way to reconfigure grub to recognize windows.

---

### Post by louieb on 2006-08-20
Just goggle dual-boot. I had fendora at one time also. and xp on my second hdd. my grub.conf entry looks like this: 
```
title Win XP Home
                map (hd0) (hd1)
                map (hd1) (hd0)
                rootnoverify (hd1,0)
                chainloader +1
                makeactive
                boot
```
If windows is on the first hdd remove the map lines and change the drive number on the rootnoverify line. 

As a note the Gentoo forum has a great grub error collection thread.

---

### Post by bodhi.zazen on 2006-08-20
DC@DR Why so hostile?

slade: I for one use multiple OS and would be glad to help, but louieb beat me to it.

louieb: Nice.

---

### Post by seshomaru samma on 2006-08-21
> **slade said:**
> 

i think i recall hearing that fedora core 5 comes with both gnome and KDE, but it always boots in gnome.  how do i switch to KDE?

once i do get a dual boot set up, is there a way that i can keep things like firefox bookmarks or trillian/GAIM logs as a single file that each OS uses?

.

Look for sessions in your GDM screen , does it have a KDE option?
If not you will need to download KDE ,probably something like:
```
yum groupinstall "KDE (K Desktop Environment)"
```
make sure to run su root first
but you better check with Fedora forums first. I'm not sure . I use FC4

I think there is no way you can get Windows and Linux to share a firefox file. You could of course export your bookmarks , put it on a shared partition and import it again from the other OS , but you will need to do it everytime you change your bookmarks. 
I might be wrong though

For MP3 support , look for fedorafaq.org

---

### Post by slade on 2006-08-21
hmm, so i reinstalled linux on the second hard drive and then linux wouldnt boot at all...  it would give me an error message and then give me a screen asking which OS i wanted to boot with, and i would get an error message if i chose either windows or linux.  i switched the hard drives and booted in windows, and a message came up telling me that the software i tried installing has not passed window's compatability check or something like that.  i guess windows XP is screwing everything up, and keeping me from properly installing grub?

---

### Post by slade on 2006-08-21
well, you guys should be happy...  i decided to boot up my ubuntu computer to work from while i try to work this issue out.

i just realized, my windows hard drive is a NTFS hard drive...  would that keep me from installing grub on it?  or does the boot loader have nothing to do with whether the hard drive is NTFS or FAT32?

does it really matter where grub is installed, or only that its configured properly?  i take it it has to be on the first drive (since i cant get the bios to boot from the second drive) but does it matter if that drive is linux or windows?  i could try switching the drives so linux is the first drive, and installing fedora and grub on the first drive...  i take it windows doesnt like me messing with it.

---

### Post by slade on 2006-08-22
okay, i think im getting a bit closer.  i reinstalled fedora with XP on the second drive.  now when the computer boots it shows an option for fedora and an option labled "other".  fedora boots fine, but if i select "other" the result i get is:

```
rootnoverify (hd1,1)
chainloader +1
```

what does (hd1,1) mean?  im not sure i understand the system and what the different numbers refer to.

louieb:  thanks for the help, but first of all, how do you get to the grub.conf entry?  and can someone explain what things like map and rootnoverify mean?

seshomaru samma:  what is the GDM screen?  if its the screen where you log in upon booting the computer, i looked under sessions and KDE wasnt there, maybe ill install it later to check it out.

thanks everyone.

---

### Post by bodhi.zazen on 2006-08-22
> **slade said:**
> okay, i think im getting a bit closer.  i reinstalled fedora with XP on the second drive.  now when the computer boots it shows an option for fedora and an option labled "other".  fedora boots fine, but if i select "other" the result i get is:

```
rootnoverify (hd1,1)
chainloader +1
```

what does (hd1,1) mean?  im not sure i understand the system and what the different numbers refer to.

louieb:  thanks for the help, but first of all, how do you get to the grub.conf entry?  and can someone explain what things like map and rootnoverify mean?

seshomaru samma:  what is the GDM screen?  if its the screen where you log in upon booting the computer, i looked under sessions and KDE wasnt there, maybe ill install it later to check it out.

thanks everyone.

Very good questions. The answers are longer then I want to type so....

[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

[http://www.tldp.org/HOWTO/Multiboot-with-GRUB.html](http://www.tldp.org/HOWTO/Multiboot-with-GRUB.html)

---

### Post by slade on 2006-08-22
> **bodhi.zazen said:**
> Very good questions. The answers are longer then I want to type so....

[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

[http://www.tldp.org/HOWTO/Multiboot-with-GRUB.html](http://www.tldp.org/HOWTO/Multiboot-with-GRUB.html)

thanks, too late to look at it tonight though.  ill check out the links tomorrow.

i fixed the mp3 issue with the walkthrough on [www.fedorafaq.org](www.fedorafaq.org), in case any other new user wants to know how to get MP3 support.  i also figured out how to install KDE, all the GUIs are just under Applications>add/remove programs.

---

### Post by slade on 2006-08-23
^_^ updating to say thanks for the links bodhi.zazen, ive figured out the problem, and i think anyone else with a sony VAIO computer will have the same issue.

i completely forgot, because the operating system and software came preinstalled, sony had a first (hidden) partition of everything you need for the installation.  (hd1,1) refers to the second drive, first partition, so instead of booting in windows XP, grub is trying to boot from essentially a backup software partition.

so a bit more reading and i should be able to figure out how to change grub fairly easily.

thanks everyone!  although i like fedora so much, i probably wont even boot Windows much.

oh, and i got a girl i know through geek camp to install ubuntu.

*edit* err, my mistake, i thought partitions were counted from 1, they start at 0.  so that was right.  i found grub.conf though, and it was missing the map, makeactive, and boot lines.  this should work then.

---

