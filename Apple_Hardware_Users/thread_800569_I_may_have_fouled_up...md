---
title: "I may have fouled up.."
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by deamon_knight on 2008-05-20
I'm running a PowerBook G3, dual booting Ubuntu and OSX 10.3. I had bad luck with 7.10 and was eager to try 8.04. I've had a lot of success with Hardy, I've been running since the Beta and been happy, however, I think I may have been making trouble for myself. I couldn't find the Beta release of Xubuntu, so I installed Ubuntu and tried a **sudo apt get install xubuntu-desktop** and switched sessions to Xfce, and I thought this would be the same as simply loading Xubuntu. I've had some configuration problems since then, specifically: I've tried to mount my OS X partition and I although I can get it to attach to the filesystem, the desktop Icon for a different file system doesn't show up. Recently I've also noticed that I seem to be getting updates for the ubuntu-desktop and nautilus, and isn't right either. On a guess I ran nautilus from the terminal and my desktop switch to the Gnome Heron desktop background and Both the filesystem Icon AND the Mac OSX partition icon appeared. I must conclude that I haven't been clever enough to change an Ubuntu install into an Xubuntu system, and that the Xfce session isn't using the configuration files like I want it to (however perhaps GNOME is?), so where do I go from here? Is it better to wipe my Linux partition and install from an Xubuntu Alt install or can I get to where I want to be (normal Xubuntu) from where I am?

Thanks

---

### Post by stream303 on 2008-05-20
To get back to a pure Gnome (or xubuntu or kde), I have used this before:
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

I had to use the cut-n-paste method.

Great site.  I once had an install that had Gnome, KDE, AND Xubuntu installed.  What a nightmare. :)

At least you can get back to square one without reinstalling....

---

### Post by mchladek on 2008-05-20
I used this same method to get Xubuntu installed.  I didn't have have the same problems you did, but noticed some oddities until I uninstalled gnome using the method from psychocats that stream posted.

There must be some config files that get stuck in limbo between gnome and xfce, but I wasn't clever enough to get them sorted out.  Unless you really need both xfce and gnome, it will probably be best to just stick with a pure installation of one or the other.

---

### Post by stream303 on 2008-05-20
I'm wondering why Xubuntu still hasn't provided a current post-beta release of Hardy for ppc.

Could it be that they would rather we install by using the xubuntu-desktop option, or maybe they lost interest altogether?

I guess I'd have to ask, but I'm fearful of being met by silence. :)

---

### Post by avtolle on 2008-05-20
I'm beginning to think there is a distinct lack of interest on the PPC side of things by the Xubuntu folks.

---

### Post by deamon_knight on 2008-05-20
Still not sure on my best strategy then, should I revert back to pure Gnome as listed on psychocats and then use Aptitude install xubuntu-desktop? Or should I erase the Linux partition and use the Alt Xubuntu PPC install:

[http://cdimage.ubuntu.com/xubuntu/ports/daily/current/](http://cdimage.ubuntu.com/xubuntu/ports/daily/current/)

Thanks!

---

### Post by avtolle on 2008-05-20
> **deamon_knight said:**
> Still not sure on my best strategy then, should I revert back to pure Gnome as listed on psychocats and then use Aptitude install xubuntu-desktop? Or should I erase the Linux partition and use the Alt Xubuntu PPC install:

[http://cdimage.ubuntu.com/xubuntu/ports/daily/current/](http://cdimage.ubuntu.com/xubuntu/ports/daily/current/)

Thanks!
FWIW, I think if it were I who was making this decision, I'd revert back to pure Gnome and then install the xubuntu-desktop via Aptitude, as described in Psychocats. I went to the daily build xubuntu site you linked, and the age, if one will, of the xubuntu alternate for ppc was troublesome to me.

EDIT: Strike that final comment; I missed the date on the iso, my bad. So, given that it is more current than it seemed to me originally, I might take a chance on installing the xubuntu alternate iso and see how it does. Long day is my story, and I'm sticking to it. :-)

---

### Post by stream303 on 2008-05-21
I installed using that just before release and it worked.  It will be interesting to see if you notice any major difference between the xubuntu-beta followed by upgrades, vs the xubuntu-desktop install removing ubuntu afterwards. :)

Perhaps they are waiting for the point-release 8.04.1 before releasing an xubuntu for ppc...

---

### Post by deamon_knight on 2008-05-21
OK, I'll try the wipe and reload method. Maybe I can ask for a bit more advice though. I have this unit set as a split partition to dual boot the mac OS & linux, and I don't want to reinstall the Mac partition. I could boot to the live CD and use the partition editor, but thats rough since this system has very low overhead. I've used the ALT install several times with the "use largest contiguous free space" , but I don't know how to wipe and existing partition (actually 3, the Yaboot, Swap, and Primary Linux partitons) from within the alt installer. Any suggestions?

---

### Post by stream303 on 2008-05-22
In this case, I think the easiest thing to do is when you get to guided partitioning, manually delete the linux partitions,  and let it write the changes to the system, but then use the "go-back" feature in the partitioner and just install to the new free-space you have freed up. :)

I use the "go-back" all the time in the partitioner with this method.

---

### Post by deamon_knight on 2008-05-25
Wiped and reloaded, no major difference except the splash screen matches. I'm still reconfiguring so I'll post back when I know if changes to FSTAB work. Meanwhile, I'm having a new problem. I installed Openoffice.org by way of sudo aptitude openoffice.org and while it installed, I've got a broken dependecy error cropping up now whenever I add packages. Here is the error:

E: openoffice.org-writer2latex: subprocess post-installation script returned error exit status 1
E: openoffice.org: dependency problems - leaving unconfigured

anyone know what this means?

---

