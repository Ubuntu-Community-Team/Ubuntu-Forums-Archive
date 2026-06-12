---
title: "Ubuntu Plus Addon"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by eight. on 2008-02-23
Does anybody have this? I need this addon to get my wireless network card to work (I think)
The website that distributes it seems to be down, and has been for a few days

Could somebody put it up on sendspace for me?

---

### Post by glennric on 2008-02-23
What is Ubuntu Plus Addon?  As far as I can tell from Googling it is a debian repository cd for those with slow internet connections.  It doesn't seem to have anything on it that is not in the repositories to begin with.  

What is your network card?  Is it wireless?

---

### Post by eight. on 2008-02-23
I'm not really sure what Ubuntu Plus is. But this post "[here]("http://ubuntuforums.org/showthread.php?t=228176")" says that it would be what I require. I'm new to linux, so the information that that poster first gave sort of flies over my head. I might get some linux books from the library though.

Should i follow the instructions on that post?

---

### Post by glennric on 2008-02-23
What that post says to do is install ndiswrapper-utils and ndisgtk.  Those packages are in the repositories.  The reason they probably say to get the ubuntuplus addoncd is to get those packages to a computer that does not have internet access.  You will also have to locate windows drivers for your video card.  Ndiswrapper is a wrapper to use windows drivers in linux.

---

### Post by eight. on 2008-02-24
Right. I still don't think I understand. My computer, when I'm on linux, does not have internet access, because I don't have the drivers for my wireless network card. 
Where do I find the repositories? Are they built in within Ubuntu?

---

### Post by glennric on 2008-02-24
In "Synaptic Package Manager" go to settings->repositories.  You can enable, disable, add, and remove repositories from there.  Also, look in the file /etc/apt/sources.list to see the file that the GUI in synaptic refers to.  

If you don't have internet access from the computer you are trying to install from you will have to download the packages you need on another computer and transfer them some other way to the laptop.  I don't recommend downloading that entire Ubuntu Plus AddonCD as that is going to be at least 600MB and you most likely need only a few MBs of packages.  You will need the files 
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb)
and
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb)

---

### Post by eight. on 2008-02-24
Excellent, thanks very much for your help. I'll try this soon

---

### Post by oedha on 2008-02-24
> **eight. said:**
> I'm not really sure what Ubuntu Plus is. But this post "[here]("http://ubuntuforums.org/showthread.php?t=228176")" says that it would be what I require. I'm new to linux, so the information that that poster first gave sort of flies over my head. I might get some linux books from the library though.

Should i follow the instructions on that post?

the link...was 2006.....
what you need just internet connection to get ndiswrapper.....

---

