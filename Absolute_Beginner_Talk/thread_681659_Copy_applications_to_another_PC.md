---
title: "Copy applications to another PC"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Robin2 on 2008-01-29
Hi, I haven't been able to find info on this - maybe I don't know the right keywords to search with.

I can download applications to my Gutsy using Synaptic manager - it all works fine. However I have two PCs with Gutsy and it would be great to install the applications on the second PC without having to download them again.

If it was a Windows application it would download as an EXE or MSI file which I can copy to the other PC and execute.

But with Gutsy it is not obvious what happens in the background when Synaptic manager operates - does it download a single file (like Windows does) and if so, where does it save it? And if I copied that file to the same location on the second PC how would I tell Synaptic manager to install it?

Thanks

---

### Post by spiderbatdad on 2008-01-29
there is a new program out called aptoncd. Install in with sudo apt-get install aptoncd. 
It will allow you to burn an iso of the programs and their dependencies from your system to install on another. You should look into the documentation a little to see how it works, but basically it adds itself to the sources list on pc #2...then you would temporarily disable the other sources and install from synaptic with aptoncd as the source...something like that. 

What you referred to before as a method isn't very practical. Simply copying the binaries of the programs from their directories would not work because you would have to have all the appropriate libraries as well.

With aptoncd it installs itself in System>>Administration>>Aptoncd. I installed the tarball and had what seemed like a working GUI, but it did nothing. Finally I did sudo apt-get install aptoncd and I had a working program. I have used it and was pleased.

---

### Post by yota on 2008-01-29
Hi,

Ubuntu uses the debian package management system which uses .deb files (called packages) which contains a single program or library.
An application that has a functional meaning from the user's perspective can be composed by more than one .deb, since, for instance, one program can depend on two libraries.
All needed .deb files are automatically downloaded by synaptic and stored on /var/cache/apt/archives
You can copy the content of that folder to the second computer on the same location and use synaptic as usual, or you can just click on a .deb file to install it; in the latter case you will have to handle dependencies by hand though.

Hope this helps!

---

### Post by Robin2 on 2008-01-29
Thanks for both replies - looks like a solution.

---

### Post by space_man619 on 2008-02-06
Small problem with mine. My friend has Ubuntu 7.10, and no internet connection. He wants some of the games I have on my Ubuntu box, especially Armagedtron. However, Armagedtron goesn't show up in APTonCD. If I knew where .deb files got downloaded to, I could add them to APTonCD.

Thanks

---

