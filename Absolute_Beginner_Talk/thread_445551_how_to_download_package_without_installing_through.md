---
title: "how to download package without installing through synaptic"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by sefir on 2007-05-16
Hi everyone,

Is it possible to download a package through synaptic, copy the files to a flash drive, and place them on a computer with no internet access, and then install the package on that computer?  

I ask this b/c I have a computer set up in a place with no internet access.

Thanks.

---

### Post by tippit78 on 2007-05-16
Synaptic gives you the option to download without installing, and all the packages it downloads are available in /var/cache/apt/archives/

Then you should be able to copy the ones you want and use the debi installer (you'll probably be able to just double click on the packages). Just make sure you have all the dependencies, and you install them first, and you should be fine.

---

### Post by FuturePast on 2007-05-16
Or just visit [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

---

### Post by sefir on 2007-05-16
thanks tippit,

are all the packages I have ever installed found at /var/cache/apt/archives/?  If so, a lot of programs seem to be missing.  

Also, if I were to install these packages on the disconnected computer by clicking on the .deb files, will synaptic recognize them as installed packages?

Thanks again.

---

### Post by tippit78 on 2007-05-17
Well, if you've used clean or autoclean at any time, it'll get rid of some of the packages. If you've got the room on your hard drive, I would try not to do that. But I think if you're missing anything, all you have to do is mark the desired package for re-installation, and in the 'Apply' dialog, select 'Download selected packages only.'

Once you get them installed, synaptic will list them as 'local or obsolete' files. It just means that they weren't installed from repositories. I have two packages from getdeb that are listed here, and they don't create any sort of problems.

Glad to be of some help!

---

### Post by zvacet on 2007-05-17
You can try this page,but be sure to download all dependencies

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by ugm6hr on 2007-05-18
I'm just installing all the packages I want for Xubuntu.  So presumably, a good idea would be to backup /var/cache/apt/archives/ to allow reinstallation from an external HD (or even CD) without having to download everything?  Having come from the Windows world where a full reinstall took over 3 hours, it would be nice to have it all up and running pretty quick.  Presumably Xubuntu doesn't have the same problem with things slowing down unbearably as things fragment, unexpected programs start on start-up etc... which I suppose would reduce the need...  Sorry, just thinking aloud now!

---

