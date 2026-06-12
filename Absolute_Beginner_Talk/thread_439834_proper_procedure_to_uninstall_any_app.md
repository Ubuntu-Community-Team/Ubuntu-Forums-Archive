---
title: "proper procedure to uninstall any app?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-05-11
i installed Eclipse and i stored it in /usr/local/ directory. how would i go about uninstalling it? can i do a simple: rmdir ?

i can't use Application > Add/Remove. It is not there. I think it would be helpful if I learn on command line and some knowledge so next time I add and remove it be easier

---

### Post by justleen on 2007-05-11
it depends how you installed it. If you used the package manager, you can use ```
sudo apt-get remove eclipse 
``` to remove it.
If you installed it without that, you can remove the files with rm
to remove a dir, use ```
 rm -r 
```

to locate any other files you can use ```
locate eclipse 
```

---

### Post by benanzo on 2007-05-11
It is generally a good idea to stick to the software provided as .DEB files.  That is what you get in the Add/Remove Applications program.

How did you install Eclipse to begin with?  was it a .tar.gz file?

If it was a .deb file just open Synaptic, System -> Administration -> Synaptic Package Manager

and search for eclipse.  then you can uninstall it.  However, if that is not how you installed it, for instance if it was a tar.gz file you downloaded you don't want to install from synaptic without first removing the other version.  I would recommend you go to a terminal, Applications -> Accessories -> Terminal

and do:
```
whereis eclipse
```
take note of the directories it is installed in and check for an uninstall script in them, if there isn't one, just delete them.

I would recommend checking the repositories via Synaptic or Add/Remove for the app you want before installing a tar.gz.  It makes your system easier to manage.

---

### Post by mcduck on 2007-05-11
> **gotquestions said:**
> i installed Eclipse and i stored it in /usr/local/ directory. how would i go about uninstalling it? can i do a simple: rmdir ?

i can't use Application > Add/Remove. It is not there. I think it would be helpful if I learn on command line and some knowledge so next time I add and remove it be easier

Yes, it is there. Just change the dropdown menu in the top right corner to 'All available Applications' and you'll find it there. Alternatively, just use Synaptic (in System/Administration/Synaptic Package Manager). Synaptic will find *every* package in *every* repository you have configured. And Eclipse definitely is in Ubuntu repositories :)

If you still can't find it, go to System/Administration/Software Sources and enable Universe & MUltiverse repositories..

---

