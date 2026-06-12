---
title: "Where do I find ntfs-cofig tool on SPM?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ken_38 on 2007-05-28
This will show how new I am - but please help. 
I am trying to mount Windows partitions [for the time being] using Third Party NTFS-3g document as guideline. ntfs-3g I can find OK on Synaptic, but the doc also talks about installing ntfs-config.
My problem is -from where????? I can't find it listed even under All - and yes, I do have Restricted enabled.
I'm sure it's straightforward, but I can't see how. Reason is I think I "need integration in gnome", and am still a bit nervous about manual installing in case I mess it up. Thanks in anticipation.

---

### Post by Kobalt on 2007-05-28
Hello,

The ntfs-config package is available from Ubuntu 7.04. If you're still under 6.10, you need to follow [these steps]("https://help.ubuntu.com/community/MountingWindowsPartitions").

---

### Post by bmagyarkuti on 2007-05-28
It's easier to use the command line.

Just choose Applications-->Accesories-->Terminal, and type
```
sudo apt-get install ntfs-config
```

---

### Post by ken_38 on 2007-05-28
Thanks for prompt reply Kobalt.
Trouble is - I've also printed the doc you mention. It _also_ talks about something called ntfs-config for me to download. Perhaps I wasn't clear. I can't find this package listed by name anywhere, though I can find ntfs-3g.
Yes, I am using Edgy by the way. I think I'm clear on the procedure - its just the wherewithal to do it that I can't locate on SPM - hence the problem.

---

### Post by Kobalt on 2007-05-28
It is mentioned you need to add other repos to be able to download ntfs-config, did you add them  ? If not then it's normal you can find it in Synaptic... 
> Alternatively, a stable version of NTFS 3G for older versions of Ubuntu can be obtained from a third-party software repository - see [using a third-party NTFS 3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G").

---

### Post by gn2 on 2007-05-28
Another way is to use the NTFS/Fat32 Auto-mounter available through [www.getautomatix.com](www.getautomatix.com)
This will automatically mount NTFS partitions/drives and make them writeable.

---

### Post by Kobalt on 2007-05-28
I would not suggest Automatix at all. See [this]("http://ubuntuforums.org/announcement.php?f=13").

---

### Post by gn2 on 2007-05-28
> **Kobalt said:**
> I would not suggest Automatix at all. See [this]("http://ubuntuforums.org/announcement.php?f=13").

As far as I can see, that's just a legal disclaimer, aimed at distancing Ubuntu from Automatix in case of litigation in the "Land of the Free" over certain software that Automatix provides easy access to.

There is no information there that would cause me to have any worries whatsoever about using Automatix, which is an excellent utility.

---

### Post by Kobalt on 2007-05-28
Automatix runs *killall -9 dpkg* in order to be able to use apt-get. This can simply corrupt your dpkg database and prevent you from using apt-get at all. Meaning a complete crash of the system...

---

### Post by gn2 on 2007-05-28
Why use apt-get when Synaptic Package Manager is available?

In eight months of using Automatix, I've yet to have a single problem with it.

I'm of the opinion that terminal commands should be treated like a parachute, i.e. a lifesaver when all else fails.

---

### Post by Kobalt on 2007-05-28
> **gn2 said:**
> Why use apt-get when Synaptic Package Manager is available?
Synaptic is a frontend of apt-get : it provides you a graphical way of using these commands. 
You had no problems, then it's just fine, but I've read many threads about people having troubles and a few one having a complete crash of their system...

---

### Post by gn2 on 2007-05-28
> **Kobalt said:**
>  I've read many threads about people having troubles and a few one having a complete crash of their system...

I've read many news stories about car crashes, but I still drive my car...........

Thanks for the info though, if I start having problems, then perhaps I'll know where to look. :)

---

### Post by ken_38 on 2007-05-28
Thanks everyone for your input - PROBLEM SOLVED -  up and running with total access.

Looks like I stirred up an unexpected debate! I'll take a closer look at it later. There's more than one way of skinning a herring outside Windows\\:D/. Seems like the future's exciting.

---

### Post by Kobalt on 2007-05-28
You're welcome.

---

### Post by arnieboy on 2007-05-28
> **Kobalt said:**
> Automatix runs *killall -9 dpkg* in order to be able to use apt-get. This can simply corrupt your dpkg database and prevent you from using apt-get at all. Meaning a complete crash of the system...
are you completely sure you understand every word of what you are saying?

---

