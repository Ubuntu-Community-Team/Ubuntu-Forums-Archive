---
title: "Getting packages without an internet connection"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by eisenstein on 2007-08-31
I know this question keeps coming up in various guises, but after several hours of searching I still can't find the right "how to."  If someone can help me sort this out,  I'll do my best to write a clear guide for others.

The problem is: How to find and download deb packages on a windows machine that has an internet connection, and install them on an Ubuntu machine that does not have an internet connection.  The packages in question are not on the distro CD. I know how to transfer and install the .deb packages once I've got them on the windows machine.  The problem is finding all package dependencies and the locations of the corresponding .deb files in the archives.  

In my case (X11 development files) it's a complicated dependency tree.  On packages.ubuntu.com I can find the packages and their dependencies by hand, but I can't see how  to download the .deb files for each package, or find where they're located in the repositories.  It gives me an option to download the source files for each package, but trying to compile from source is just asking for more trouble.  Am I missing something here?  How can I go from package names to actual locations of .deb files in repositories?

Note: I can't use synaptic or apt-get to do this for me, because the linux machine is not connected to the internet and so can't find the  repositories where the packages are located.  Is there some web site somewhere that can generate download scripts from package names?  Or even just a list of package locations for manual download?

One idea I've read is to find a linux box that is connected to the internet, generate the download script from it, and use that to download onto the windows box.  That would work except I honestly don't know of any other linux machines around here.  Mine would be connected except I can't get my wireless working with firefox.  But if someone wants to take pity on me, they could generate the download script from synaptic for the following packages: libx11-dev and xlibs-dev (plus anything else I might be needing?)  That would solve my problem now but I think we should still come up with a clear solution that doesn't depend on this workaround.

Thanks for any help on this--

Ben

---

### Post by louieb on 2007-08-31
Break out your credit card. Heres a list of online stores that sell the Ubuntu repositories on DVD. [http://www.ubuntu.com/getubuntu/purchase](http://www.ubuntu.com/getubuntu/purchase) I looked at a couple price was 30 - 35 US dollars. Seems reasonable to me.

---

