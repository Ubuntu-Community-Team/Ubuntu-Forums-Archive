---
title: "thinking of trying compiz fusion......but......"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-06-28
ok, ive been doing some reading and found out that beryl and compiz are re-joining, ive never tried compiz, been using beryl.
so what i want to know is how stable is compiz fusion ? some feed back on people running it with nvidia cards would be helpful.
im presuming that its best to remove beryl before installing the new one ?
im dying to try it from the little ive read, but i know ill brake my system, i will most likely break it anyway (if it aint broke fix it till it is, thats my motto )  :D 
how different is it from beryl and compiz, is it kind of like the best of the 2 applications ?
like i said im dying to try it, but ive just got my system running perfectly.
cheers

---

### Post by insane_alien on 2007-06-28
make a full backup of your system while you have it working good.

now, compiz fusion isn't the most stable of all the software out there (my attempt borked) and there is a very big chance that it will just plain not work.

if you want to try it however, this link gives a pretty easy to follow tutorial,

[http://forums.opencompositing.org/viewtopic.php?f=51&t=758#p6435](http://forums.opencompositing.org/viewtopic.php?f=51&t=758#p6435)

---

### Post by Acglaphotis on 2007-06-28
I just installed and it works great... but i cant put pictures in the top side of the cube... but it runs WAY faster than beryl. Nvidia Go 6150.

---

### Post by rfurman24 on 2007-06-28
I did not notice any instability but in order to keep it and beryl at the same time I had to upgrade beryl to the svn with the newest emerald all from trevino repositories. That version of beryl was buggy. The cube caps in (lack of) in compiz annoyed me and I could not get some of the animations to work. I ended up uninstalling and going back to bery 2.1rc3.

---

### Post by techno-mole on 2007-06-28
so it might be worth a bash, just for the hell of it.
just out of interest, how does one make a system back up with ubuntu, its something i have been meaning to find out about for a while, and it probably have saved me alot of time if i had backed up earlier.
cheers

---

### Post by joep on 2007-06-28
I was running Beryl but I just done a fresh install so thought I give Compiz Fusion a try and it runs great lot more features to play around with. I use Avant with it no problems. My Nvidia card is a
GeForce FX  5600XT.

---

### Post by zero244 on 2007-06-28
Think about it bro........you have beryl running nice now. Dont mess with it........the new features in Compiz are not worth the hasslle of breaking your current setup.
Wait for Compiz to come out of beta.......if it ever does.

As far as backups.......there are some pretty good backup programs for Linux.
I personally use Paragon Disk Manager for Windows.
I dual boot with XP...........so I go into Windows and backup my Ubuntu stuff from there onto a extra harddrive.
I have beryl running pretty darn good at the moment and I dont want to mess it up for some extra cool new effects.
Like you say........if you like what you have and its not broke................DONT FIX IT!

---

### Post by overdrank on 2007-06-28
> **techno-mole said:**
> so it might be worth a bash, just for the hell of it.
just out of interest, how does one make a system back up with ubuntu, its something i have been meaning to find out about for a while, and it probably have saved me alot of time if i had backed up earlier.
cheers

Hi I tried it and did not care for it as much as Beryl. It was easy to install though so if you want to go for it sure why not!;)
I have to edit this statement because I installed it the first time on a laptop and it was ok but then I install it on a my desktop and WOW cool stuff!
I stand corrected!!!!!

---

### Post by speaker219 on 2007-06-28
I definately reccomend compiz fusion over beryl. it is a merge of beryl and compiz and is replacing beryl. i find it to be much smoother and more stable than beryl already. give it a try ;)

---

### Post by shifty_powers on 2007-06-28
If ya want to back up in linux, mole, have a look at [ghost4linux](http://sourceforge.net/projects/g4l). Meant to be quite good...

---

### Post by techno-mole on 2007-06-28
cheers for that shifty, i shall have alook, and seeing as how im quite likely to kill my system soon anyway :D it may well come in handy.
ive often found this with things like beryl and the like, although they are beta's they are stable on my system, i guess its like anything, for some it'll be problem free and for others it may mean alot of hassle re-installing everything, all good fun though, the only problem ive had with beryl was missing window decorations, which is easily solved with a line in xorg.conf.
i think i shall have ago with compiz fusion, and if nothing else i can give the project some feed back if it either goes well or completely stuffs my system :D
cheers

---

### Post by techno-mole on 2007-06-28
i swear ill never learn to leave things alone, ive killed it again, i can still use my system, but i cant install compiz fusion, i followed the instructions and all it does is load up some effects, but i dont get window decorations, i cant rotate the cube, and wobbly windows and such like dont work.
the installation process returned a load of errors, like not being able to varify the key and cant find this package and cant find that package, i know its in its early stages but from that little experience i shall be sticking with beryl for a while, at least until the installation goes a little smoother.
ive now got to figure out how to fix things, i cant update the system anymore, if for example i use the update manager i get - 
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

if i run sudo apt-get install -f i get this - 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  beryl-core beryl-settings-bindings libberylsettings0 beryl-settings
  beryl-plugins emerald libemeraldengine0 beryl-plugins-data
  libberyldecoration0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? 

so i hit "y" and then enter and i then get the following - 

(Reading database ... 123827 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070627~3v1ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070627~3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070627~3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

so if anyone has any ideas about this i would appreciate it.
cheers.
:D

---

### Post by overdrank on 2007-06-28
HI did you skip the first command *sudo apt-get -y remove compiz-core desktop-effects* I did and got all kinds of errors. Ok first you have to repair the broken packages in synaptic and it should tell you to search for them I had too. Then when you get that fixed then you can move and remember to not skip the first command because compiz is in feisty by default. Hope this helps!:(

---

### Post by techno-mole on 2007-06-28
no i followed the commands from start to finish, never mind.
i did try to fix the broken packages in synaptic but it wouldnt have it, so i figured if it was me trying to install compiz, then id try uninstalling it, so i removed all the checked compiz related items using synaptic and then re-installed beryl, restarted x and all is well now, thankfully.
i wont give up though, i do tend to get a little obsessive about these types of things, so im determined to get it to work now :D
cheers for the help though.
:D

---

