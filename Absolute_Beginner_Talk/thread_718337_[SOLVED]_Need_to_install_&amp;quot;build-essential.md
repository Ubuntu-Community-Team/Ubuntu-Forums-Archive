---
title: "[SOLVED] Need to install &amp;quot;build-essential package&amp;quot;, not on cd"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-03-08
I am trying to set up broadband PPPoE on my gutsy laptop, and since it didn't work in the standard way someone else gave me a howto which requires the "build-essential package" from the Gutsy installer disc. But when I tried to install it from the Gutsy installer cd,  it says it is not on that disk, and please install the "Gutsy 386 installer disk"-- although that IS the cd I have put in my cdrom. That is the very cd I used to install Gutsy. So I cannot advance in the PPPoE setup instructions until I get this package. I do have access to another computer which can go online, it is a WinXP computer. Can I used it to download the "build-essential package" and then bring it over to the gutsy computer with a pen drive and thereby install it? Please give me some guideline.

---

### Post by logos34 on 2008-03-08
I believe this is what you're looking for:

> [   ] build-essential_11.3ubuntu1_i386.deb    20-Jul-2007 15:03  6.9K  

[http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/)

Here's the description with more info on dependencies (disregard the 'arch: amd64'--my machine)
> $ apt-cache show build-essential
Package: build-essential
Priority: optional
Section: devel
Installed-Size: 48
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Architecture: amd64
Version: 11.3ubuntu1
Depends: libc6-dev | libc-dev, gcc (>= 4:4.1.1), g++ (>= 4:4.1.1), make, dpkg-dev (>= 1.13.5)
Filename: pool/main/b/build-essential/build-essential_11.3ubuntu1_amd64.deb
Size: 7070
MD5sum: fae45f5db735011a6940b32bedd08ef7
SHA1: 3dc0f941f54ebc63ebc3c6b2b0747f4e1c202ac1
SHA256: b11e0794932e8b2e9ad3c80f52c9b26c47caa443df64f9fa4c797063fbaf72b6
Description: informational list of build-essential packages
 If you do not plan to build Debian packages, you don't need this
 package.  Moreover this package is not required for building Debian
 packages.
 .
 This package contains an informational list of packages which are
 considered essential for building Debian packages.  This package also
 depends on the packages on that list, to make it easy to have the
 build-essential packages installed.
 .
 If you have this package installed, you only need to install whatever
 a package specifies as its build-time dependencies to build the
 package.  Conversely, if you are determining what your package needs
 to build-depend on, you can always leave out the packages this
 package depends on.
 .
 This package is NOT the definition of what packages are
 build-essential; the real definition is in the Debian Policy Manual.
 This package contains merely an informational list, which is all
 most people need.   However, if this package and the manual disagree,
 the manual is correct.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


You might also want to get the **ppoeconf **pkg:

> $ apt-cache show pppoeconf
Package: pppoeconf
Priority: standard
Section: net
Installed-Size: 340
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Gregory Colpart (evolix) <reg@evolix.fr>
Architecture: all
Version: 1.16ubuntu1
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95)
Recommends: locales
Suggests: xdialog
Filename: pool/main/p/pppoeconf/pppoeconf_1.16ubuntu1_all.deb
Size: 22526
MD5sum: ba83eae47ee3e61489f36144c6bbaae0
SHA1: bf9004d6ef41e8c6e5d125c1e52bef610e6d234a
SHA256: 555ef209f90675606c49acc8e5a37344df227a0215860bc730c5f58116aa7575
Description: configures PPPoE/ADSL connections
 User-friendly tool for initial configuration of a DSL (PPPoE) connection.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: standard

---

### Post by swarup on 2008-03-08
> **logos34 said:**
> I believe this is what you're looking for: 



[http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/)

Here's the description with more info on dependencies (disregard the 'arch: amd64'--my machine)



You might also want to get the **ppoeconf **pkg:

Many thanks. That should help a lot. My question now is, once I download it using my XP computer, will I be able to install it easily in the Gutsy computer? I saw that you mentioned a list of dependencies. Are there other applications I will need in order to make "build essential" work?

Here below are the instructions I received for setting up the PPPoE. Please keep in mind that I cannot go online with the Gutsy computer. Whatever I get online, I have to get via the XP computer, then bring it over with a pen drive onto the gutsy computer. Any tips greatly appreciated, as I do not have experience with this.


1) Go to System --> Administration --> Synaptic Package Manager
2) Check whether build-essential package is installed. If it is not, install it using the ubuntu CD/DVD.
3) Since you do not have internet access on ubuntu, use your alternate OS or your friend's PC to download [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)

4) Open it with ubuntu's archive manager and extract the folder within to your desktop
5) There will be a file within the folder known as ./go. Open Applications --> Accessories --> Terminal. Write sudo and drag and drop the file in the terminal and press enter. If all goes well RP-PPPoE would be installed successfully. 
Provide all the details RP-PPPoE setup requires. 

6) Type sudo pppoe-start in the terminal to bring up the connection and sudo pppoe-stop to shut the connection.
7) If you want to bring up the connection at boot time, you will have to edit the rc.local file. Open the Terminal and type sudo gedit /etc/rc.local. Insert the line pppoe-start just before exit and save the file. Done.

---

### Post by swarup on 2008-03-08
> **logos34 said:**
> You might also want to get the **ppoeconf **pkg:

Can I download this also using my Win XP machine, and bring it over with a pen drive to the gutsy machine? If so, then if you could let me know the download site for this ppoeconf that would be fantastic. Thanks.

---

### Post by swarup on 2008-03-08
As per the instructions I pasted above, I also need the following file:

[http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)

I have tried to go to this website dozens of times with my XP machine, but cannot open the window. Does anyone know of another site where this file can be gotten? Or how to get it from the above listed site?

---

### Post by logos34 on 2008-03-08
Correction--it IS on the ubuntu cd...jeez I should have checked.  But for the life of me I don't know why it doesn't get installed automatically (!)

/media/cdrom0/pool/main/b/build-essential

**gcc** is there too. 

Did you add the ubuntu install disc as a source in synaptic?  (Settings>repositories>ubutnu SW tab>installable frm cdrom)

now you can try your howto again.

pppoeconf is at same place in the online archives, but under pool/main/p/

---

### Post by swarup on 2008-03-08
> **logos34 said:**
> Correction--it IS on the ubuntu cd...jeez I should have checked.  But for the life of me I don't know why it doesn't get installed automatically (!)

/media/cdrom0/pool/main/b/build-essential

**gcc** is there too. 

Did you add the ubuntu install disc as a source in synaptic?  (Settings>repositories>ubutnu SW tab>installable frm cdrom)

now you can try your howto again.

pppoeconf is at same place in the online archives, but under pool/main/p/

Yesterday I tried it, and it didn't work! Just now I went to synaptic to add the ubuntu install disc as a source as you suggested, and found that it is already installed as such. So I tried the disc again, and it worked! Don't know why it didn't work yesterday. Great, that part is done. Now, in the instructions which I pasted above, it calls for [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)  That is, it calls for "rp-pppoe", in the case that pppoeconf does not work. I used pppoeconf yesterday in another howto, but it did not do the job for me. That is, gutsy goes on line but for some strange reason is only able to go to google and do searches there. It cannot go to ANY other website. Isn't that odd? So I've been struggling for the last 24 hours, trying to get it to go to other websites. But it won't go. So pppoeconf for some reason did not do the trick for me. So I want to try this fellow's howto which uses "rp-pppoe" -- but I can't open the download site!!! Any tips or suggestions?

BTW, what is gcc?

---

### Post by seshomaru samma on 2008-03-08
gcc is a set of compilers 

i can email you rp-pppoe if you wish ,send me a private notice with your email

---

### Post by logos34 on 2008-03-08
> **swarup said:**
> Yesterday I tried it, and it didn't work! Just now I went to synaptic to add the ubuntu install disc as a source as you suggested, and found that it is already installed as such. So I tried the disc again, and it worked! Don't know why it didn't work yesterday. Great, that part is done. Now, in the instructions which I pasted above, it calls for [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)  That is, it calls for "rp-pppoe", in the case that pppoeconf does not work. I used pppoeconf yesterday in another howto, but it did not do the job for me. That is, gutsy goes on line but for some strange reason is only able to go to google and do searches there. It cannot go to ANY other website. Isn't that odd? So I've been struggling for the last 24 hours, trying to get it to go to other websites. But it won't go. So pppoeconf for some reason did not do the trick for me. So I want to try this fellow's howto which uses "rp-pppoe" -- but I can't open the download site!!! Any tips or suggestions?

BTW, what is gcc?

I get a permissions denied for that roaringpenguin tarball.  Try main page:

[http://www.roaringpenguin.com/products/pppoe](http://www.roaringpenguin.com/products/pppoe)

You might click on network-manager applet on your panel and check the settings (DNS and Host tabs).    Someone else will have to help you on networking issues, though (not my strong point). 

I mentioned gcc because it's listed as a dependency of build-essential.

---

### Post by swarup on 2008-03-08
Thank you so much, for the help here. Someone on another thread sent me a download site for rp-pppoe which did work for me. If anyone else has trouble with it, they should try here:

[http://www.sfr-fresh.com/linux/misc/...oe-3.8.tar.gz/](http://www.sfr-fresh.com/linux/misc/...oe-3.8.tar.gz/)

Thanks again!

---

