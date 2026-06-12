---
title: "Using the ubuntu guide for kubuntu"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by tcollogne on 2006-07-10
Hi all,

I have worked some time on ubuntu with gnome and now I want to try kubuntu with kde. 

I found this guide [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) very use while trying ubuntu. But will the howto's in this guide also work under kubuntu?
For example installing firefox mplayer plugin or installing multimedia codecs?

---

### Post by aysiu on 2006-07-10
Yes. Ubuntu and Kubuntu use the same repositories and have the same packages available to them.

The only thing you might have to modify is when you're asking to ```
sudo gedit
``` something. You should do ```
kdesu kwrite
``` instead.

---

### Post by tcollogne on 2006-07-10
But in the guide is explained how to add extra repositories in ubuntu. But the package manager in kubuntu is another one, so how do I add new repositories under kubuntu?

---

### Post by Jucato on 2006-07-10
Here's a quick guide for editing repositories in Kubuntu using Adept:
[https://help.ubuntu.com/kubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/kubuntu/desktopguide/C/extra-repositories.html)

The repositories for Ubuntu and Kubuntu are the same, and the procedures are also practically the same, except for some minor details.

However, there is one major difference between Ubuntu and Kubuntu, and that's with regards to the restricted multimedia codecs. In Ubuntu, you need to install numerous GStreamer plugins/codecs. In Kubuntu, all you need is to install *libxine-extracodecs* from the Multiverse repository, and you're set to go. (Of course there will be other special codecs like w32codecs, DVD codecs, etc.)

You might want to keep this link as a reference, too:
[http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

---

### Post by aysiu on 2006-07-10
I don't think you can do it through Adept, to be honest. I use Synaptic even in KDE.

You can follow these instructions, which are desktop environment-independent:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Jucato on 2006-07-10
> **aysiu said:**
> I don't think you can do it through Adept, to be honest. I use Synaptic even in KDE.

Adding extra repositories? Yes you can. See the link I gave. Adept menu > Manage Repositories. You can even add it on the toolbar, right beside Fetch Updates, for an easier, more logical workflow.

(I rearranged my toolbar to go like this:
Manage Repositories   Fetch Updates | Preview Changes  Undo   Redo | Apply Changes   Safe Upgrade   Full Upgrade)

---

### Post by aysiu on 2006-07-10
I stand corrected. Thanks, Fenyx.

---

