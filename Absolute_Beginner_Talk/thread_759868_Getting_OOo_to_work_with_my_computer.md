---
title: "Getting OOo to work with my computer"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-04-19
No matter what the distro, OOo will not work properly on my xubuntu amd64 machine.  I want OOo because it is a full office suite that is MS Compatible.  OOo for all xubuntu, ubuntu, kubuntu, and fluxbuntu, and even openSUSE failed.  When I used the windows version with WINE, it worked for a while but then starting having problems after a few reboots.  My main problem is that when using OOo black lines appear all over my desktop.  Don't suggest KOFFICE or AbiWord because they don't work for me.  I had a problem installing symphony which I posted in another thread but as symphony is based on OOo, it probably will have the same problem.  Someone recomended:


> 
If you want OO2.4 and you have 64bit OS you will need to build OO2.4 from source. You can get the source here.

[http://download.openoffice.org/2.4.0/source.html](http://download.openoffice.org/2.4.0/source.html)

Maybe OO will start making 64bit debs soon.


How do I do this?  I am relatively new to linux and don't know how to program.

---

### Post by hikujk123 on 2008-04-19
Help!

---

### Post by calc on 2008-04-19
This sounds like a problem with your video driver. What version of Xubuntu and what video driver are you using?

---

### Post by hikujk123 on 2008-04-19
I am using xubuntu 7.10 Gutsy Gibbon.  What do I type in the terminal/do in order to tell what video driver I am using????

---

### Post by Xiong Chiamiov on 2008-04-19
You don't have to know how to program to compile from source.  I actually did it a few times before I realized I had!

If you absolutely have to end up building it yourself, take a look [here]("http://monkeyblog.org/ubuntu/installing/#source").

---

### Post by hikujk123 on 2008-04-19
Can someone help me out in a specific way?  I am pretty new to linux.  Thanks for the link, but I still need help.

If it is a driver problem and I can fix it, that would be better than having to compile because then I could just use the package.

---

### Post by calc on 2008-04-19
> **hikujk123 said:**
> I am using xubuntu 7.10 Gutsy Gibbon.  What do I type in the terminal/do in order to tell what video driver I am using????

I'm not sure if there isn't a better way but this should work:

$ grep -A5 'Section "Device"' /etc/X11/xorg.conf 

For me it shows this:

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

---

### Post by hikujk123 on 2008-04-20
```

Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection

```

Okease help me figure this out.  I would be **SO** happy if OOo worked.

---

### Post by calc on 2008-04-20
Does this problem only show up when using OpenOffice.org? Not with compiz or anything else? Does disabling compiz if it is enabled help resolve the problem?

Also what does this say:

$ grep OPENGL_SUPPORT /etc/openoffice/soffice.sh

---

### Post by hikujk123 on 2008-04-20
I have had this exact problem when using two programs.  It happens when I use OOo and when I used Kopete when I used to use kubuntu.  I have noticed some other GUI programs that are not exactly the same (eg. randoms a windows that had been closed 5 minutes ago will appear in when I open another progam).  Problems are heightened when I use transperancy (I can only use this xubuntu, none of the other buntus even let me enable effects).  Right now, I am not using any effects.  Let me install OOo and try your command.

Edit:  Compiz is not even installed.  I think I tried it when I used regular ubuntu with gnome and don't think I could get anything to work.

---

### Post by calc on 2008-04-20
It sounds like it is a driver issue, you probably should file a bug against xorg in launchpad and have the Xorg maintainer help you debug the issue some more. I have heard about the OOo black lines issue before, but since it sounds like it happens in other programs as well it is likely an Xorg driver problem of some sort.

---

### Post by hikujk123 on 2008-04-20
```

# the setting if OPENGL_SUPPORT has no effect.
OPENGL_SUPPORT=no

```

How should I do that?  How do I fix it NOW?

---

### Post by hikujk123 on 2008-04-20
Have you heard the solution to the black line problem?

---

### Post by hikujk123 on 2008-04-20
Both OOo 1.03 and 2.0 work perfectly with WINE, which means that it there is an issue with the later ones/ubuntu metapackage.  I can't install from the website directly because I have amd64 arch.  I have tried but the terminal says I can't.  Anyway, I still what to run it natively with the latest edition.  My computer is only four years old, so it should be able to handle it.

Edit 1: Never mind, I get the black lines with impress 2.0, but not writer 2.0.

Edit: Actually, even 1.03 has problems with impress.

The more recent OOos have problems with all.

---

### Post by calc on 2008-04-20
> **hikujk123 said:**
> I have had this exact problem when using two programs.  It happens when I use OOo and when I used Kopete when I used to use kubuntu.  I have noticed some other GUI programs that are not exactly the same (eg. randoms a windows that had been closed 5 minutes ago will appear in when I open another progam).  Problems are heightened when I use transperancy (I can only use this xubuntu, none of the other buntus even let me enable effects).  Right now, I am not using any effects.  Let me install OOo and try your command.

Edit:  Compiz is not even installed.  I think I tried it when I used regular ubuntu with gnome and don't think I could get anything to work.

I'm not sure what you want me to do. You claim in this post that you are having problems in multiple programs but you seem to refuse to file a bug about your X driver in launchpad like I recommended. Just because the Windows version of OOo works does not mean it is the linux version of OOo that is buggy. Especially since you see related graphical problems in numerous other programs. This problem hardly ever shows up and I think I have ever only heard of one other user with this problem (it might have even been you, I don't know for certain).

---

### Post by calc on 2008-04-20
See this thread: [http://ubuntuforums.org/showthread.php?t=728147](http://ubuntuforums.org/showthread.php?t=728147)

---

### Post by hikujk123 on 2008-04-21
The windows version does not work properly.  I just wanted to test it.  I want to know how to fix the driver problem and/or how to get rid of the black lines.  I clicked the link but am still not sure to do.  Everyone in that thread says something different.

---

### Post by hikujk123 on 2008-04-21
Should I do this?

```

sudo apt-get purge xserver-xorg-video-sis
./configure --prefix=/usr
make
sudo make install

```

I don't want to run it without knowing if it is okay to do so.

---

### Post by hikujk123 on 2008-04-22
bump

---

### Post by calc on 2008-04-22
That might work, I don't know. You probably should file a bug in launchpad about your video driver like I told you before. The Ubuntu Xorg maintainer may be able to give you better advice about what to do that I can.

---

### Post by hikujk123 on 2008-04-22
> **calc said:**
> That might work, I don't know. You probably should file a bug in launchpad about your video driver like I told you before. The Ubuntu Xorg maintainer may be able to give you better advice about what to do that I can.

How do you do this?

---

### Post by hikujk123 on 2008-04-22
When I type in that code.  I get the following output:

```
 Command line option --prefix=/usr is not understood 
```

---

### Post by calc on 2008-04-22
> **hikujk123 said:**
> How do you do this?

Here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/")

---

### Post by hikujk123 on 2008-04-23
I updated to the hardy release candidate and writer now works fine for the most part.  I do get black lines when trying to set a background though.  Also, impress is just as bad as it was before.  Can anyone tell me what was wrong with that command I put in?

---

### Post by hikujk123 on 2008-04-24
When I type:
```

sudo apt-get purge xserver-xorg-video-sis
./configure --prefix=/usr
make
sudo make install

```

I get:

```

 Command line option --prefix=/usr is not understood

```

How do I fix this?

---

