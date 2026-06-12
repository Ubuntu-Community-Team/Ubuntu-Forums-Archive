---
title: "Gnomesward2 module manager won't write to the proper directory."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by gkiteguy on 2008-02-17
I am a mentally challenged  UBUNTU user. 

I have installed Gnomesword2 using the Synaptic package manager.  It went without a hitch. When first starting it is supposed to prompt for new packages from the Sword Project, but it didn't, it only had arabic. I tried to download English packages and they all fail.  I thought I would try to do it manually. I went to the web site and downloaded the Raw File and unzipped it onto the desktop.  I determined the files and folders needed to go to USR/share/sword/modules/texts. I then went there and tried to drag the appropriate files.  It said "You do not have permissions to write to this folder."

I suppose I could copy the folder and files etc from the root, but it is really painful. I also think that is why the Module Manager failed.  Is there anyway to give this program permissions to write to the root file system?

I will keep slogging in His name

Gkiteguy

---

### Post by Kilz on 2008-02-17
> **gkiteguy said:**
> I am a mentally challenged  UBUNTU user. 

I have installed Gnomesword2 using the Synaptic package manager.  It went without a hitch. When first starting it is supposed to prompt for new packages from the Sword Project, but it didn't, it only had arabic. I tried to download English packages and they all fail.  I thought I would try to do it manually. I went to the web site and downloaded the Raw File and unzipped it onto the desktop.  I determined the files and folders needed to go to USR/share/sword/modules/texts. I then went there and tried to drag the appropriate files.  It said "You do not have permissions to write to this folder."

I suppose I could copy the folder and files etc from the root, but it is really painful. I also think that is why the Module Manager failed.  Is there anyway to give this program permissions to write to the root file system?

I will keep slogging in His name

Gkiteguy

simply start nautilus in admin mode. open up a terminal and type ```
gksudo nautilus
```. Then you can drag and drop the module files. But there are a few modules in synaptic, i know there is a kjv and a few others.

---

