---
title: "[SOLVED] Desktop Effects with e-GeForce 8500 GT"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by djknorr75 on 2007-09-15
Hello all,
I'm trying to enable desktop effects on my pc here, but only get a white screen when I do so, and the only thing I can do is hit the escape key to get out.  I read somewhere that beryl helped with this, so I have installed it, but it doesn't seem to have made any difference.  It probably doesn't help that when I open the Beryl Setting Manager, I have no idea what to do in there.

Do you think perhaps I am missing the nVidia driver?  Could anybody point me in the direction to enable desktop effects (trying to show Ubuntu off to my wife, and I want it to look super-cool:))

TIA

---

### Post by moredhel on 2007-09-15
Do you have the propreitary driver for your graphics card?

You can get it via the restricted drivers manager.

---

### Post by djknorr75 on 2007-09-15
Thanks for the quick response!  When I go to the restricted drivers manager, it just tells me  "Your hardware does not need any restricted drivers".

But I think it does....:(

---

### Post by djknorr75 on 2007-09-15
Woo hoo!  I happened to stumble across [this thread]("http://ubuntuforums.org/showthread.php?t=551636") a couple minutes ago, and found out about [Envy]("http://albertomilone.com/nvidia_scripts1.html"), which is probably about the coolest app I've come across.

Thanks to Alberto Milone, the creator of Envy!  My desktop effects rock, and now I can impress the little lady!:biggrin:

---

### Post by w4ett on 2007-09-15
If you REALLY want to impress her...install the Compiz-Fusion.  Here is a great how-to:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

---

### Post by djknorr75 on 2007-09-15
I've already got Beryl up and running on my machine, and I see that according to the link you provided that Compiz-Fusion is a merge of Compiz and Beryl, but basically each of them on steroids.

My question is:  Do I need to uninstall Beryl before installing Compiz-Fusion, or does the clean-up provided in the guide take care of that?

I think I'm going to try following the guide now without un-installing Beryl, just to see what happens.  Will post back here with the results.

Thanks for the extra tip btw!  I love this forum.

---

### Post by w4ett on 2007-09-15
I'd purge the Beryle install (can't remember if that guide provides for that, BTW)......plus the guide provides for the install of the Emerald packages too,  

Have fun!

---

### Post by djknorr75 on 2007-09-15
I did it without uninstalling Beryl, and found that after the last command was run in the 'Clean-Up Section', all the Beryl components were uninstalled.  It asked me to confirm in the terminal at that point, and I saw all of them listed there.

All went well with the install, except for some reason when I try to open the CompizConfig Settings Manager, nothing happens....no errors at all, but no window opens either.  

Am going to reboot and see if that fixes it.

---

### Post by w4ett on 2007-09-15
> **djknorr75 said:**
> 

All went well with the install, except for some reason when I try to open the CompizConfig Settings Manager, nothing happens....no errors at all, but no window opens either.  


Is this before or after you ran:

```
compiz --replace
```

in the terminal...?

---

### Post by djknorr75 on 2007-09-15
Uh oh...things are going downhill..   :(  I maybe should have quit while I was ahead....

Now my Alt+F2 hotkey to the 'Run Application' dialog doesn't work, and I receive this error
```
Error: BrokenCount > 0
``` upon booting into the system.  

I went to Synaptic Manager and filtered for broken packages, and Compiz was the only one there.  When I tried to reinstall and fix from there, I received the error shown below:

```
E: /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070912+3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
```

Any ideas?  I think I will probably try to uninstall it now and get back to where I was before, unless somebody knows what that means?

---

### Post by djknorr75 on 2007-09-15
Oops...sorry, I just saw your response.  That occurred after I had run ```
compiz --replace
```

---

### Post by djknorr75 on 2007-09-15
Okay, after having done some more research I think the problem has something to do with the compiz-decorator (see bold in code below).

```
sudo aptitude install compiz compiz-gnome \
> compizconfig-settings-manager compiz-fusion-plugins-extra \
> compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  compiz-core compiz-plugins libdecoration0 
The following NEW packages will be installed:
  compiz-gnome 
0 packages upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/167kB of archives. After unpacking 1073kB will be used.
Writing extended state information... Done
(Reading database ... 114598 files and directories currently installed.)
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.5.5~git20070912+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070912+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070912+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of compiz:
[B] compiz depends on compiz-decorator; however:
  Package compiz-decorator is not installed.[/B]
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz

```

When I try to install the compiz-decorator, I receive this:```
derek@homegrown-pc:~$ sudo aptitude install compiz-decorator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
"compiz-decorator" is a virtual package provided by:
  compiz-gnome compiz-kde 
You must choose one to install.
The following packages are BROKEN:
  compiz 
The following packages have been kept back:
  compiz-core compiz-plugins libdecoration0 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
compiz-gnome [1:0.5.5~git20070912+3v1ubuntu0 (feisty)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  compiz-gnome 
The following packages have been kept back:
  compiz-core compiz-plugins libdecoration0 
The following NEW packages will be installed:
  compiz-gnome 
0 packages upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/167kB of archives. After unpacking 1073kB will be used.
Do you want to continue? [Y/n/?] y

```
Upon hitting enter at this point, I get back to the original error in the first box.  It seems like a pretty vicious circle....compiz-gnome won't install without compiz-decorator, and compiz-decorator won't install without compiz-gnome!!  Help please!  

How can I uninstall compiz-fusion and get back to Beryl?

---

### Post by w4ett on 2007-09-16
At this stage, I would (using Synaptic) remove and purge the compiz, GLDesktop and Beryl packages and re-install Compiz Fusion being sure that all the repositories are correct.

Use the search function to id the installed packages to mark them for removal, then follow the guide for installation.  

As somebody once said  "Sumthin funny is goin on here"  :confused:

---

### Post by djknorr75 on 2007-09-16
I'm going to mark this one as solved...I was able to get compiz-fusion uninstalled last night, and have Beryl up and running again (it took a while, but perseverance paid off!).

Here is a [link to a separate thread]("http://ubuntuforums.org/showthread.php?t=533201") with instructions for purging the compiz-fusion install.  For some reason, selecting any and everything that had to do with it in Synaptic still didn't remove all files.  It was only once I ran the second piece of code in this other forum that my system was clean again.

PS.  The missus does think it's pretty cool looking!  I don't think it's convinced her to give up Windows yet, but we're gaining ground at least! :)

---

