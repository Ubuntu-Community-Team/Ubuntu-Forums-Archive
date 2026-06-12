---
title: "Arctic Fox, a new web browser is available for Linux PPC"
date: 2019-02-11
forum: Apple Hardware Users
---

### Post by xeno74 on 2019-02-11
Hi All, 

Arctic Fox **27.9.15** has been released! :) 

Arctic Fox is a fork of Pale Moon 27.9.4 that was released by Moonchild  Productions. The goal is to add security updates and bug fixes to keep  this browser updated for as long as possible for Intel OSX and PowerPC  Linux based systems. Arctic Fox is not affiliated with Pale Moon. It  based on an optimized layout engine (Goanna). Further information about  Goanna: [http://www.moonchildproductions.info/goanna.shtml](http://www.moonchildproductions.info/goanna.shtml) 

Requirements: PowerPC machine with at least a G3 CPU and Ubuntu 12.04.0 PowerPC or higher.

Change Log: [github.com/wicknix/Arctic-Fox/wiki/Change-Log](https://github.com/wicknix/Arctic-Fox/wiki/Change-Log) 

Support:  [forums.macrumors.com](https://forums.macrumors.com/threads/arctic-fox-web-browser-for-10-6-32-64-bit.2133051/) 

Downloads: 

Download 27.9.15 32-bit PowerPC G4/G5 (Ubuntu16/Debian9) Linux:  [arcticfox-27.9.15.linux-powerpc.tar.bz2](https://drive.google.com/file/d/11UKSwynpzgf6MKi0PN-ULgPpEAHXZAGe/view?usp=sharing) 

Download 27.9.15 32-bit PowerPC G3 (no altivec) Linux:  [arcticfox-27.9.15.linux-powerpc-g3.tar.bz2](https://drive.google.com/file/d/1bfp-LNvRQOe5UeB1n57_olBUm6A098MZ/view?usp=sharing) 

Download 27.9.15 32-bit PowerPC (no altivec - Ubuntu14/Debian8) Linux  (contributed by xeno74):  [arcticfox-27.9.15.linux-non-altivec-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.15.linux-non-altivec-powerpc.tar.bz2)

Download 27.9.15 32-bit PowerPC (no altivec - Ubuntu12/Debian8) Linux  (contributed by xeno74):  [arcticfox-27.9.15-ubuntu12.04-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.15-ubuntu12.04-powerpc.tar.bz2) (Additionally you need the **libatomic1** package. Download: [libatomic-ubuntu12.04-powerpc.tar.bz2](http://www.xenosoft.de/libatomic-ubuntu12.04-powerpc.tar.bz2) - Please copy the file '**libatomic.so.1**' to '**/usr/lib/powerpc-linux-gnu/**')

Download 27.9.15 64-bit PowerPC (Fedora/OpenSuse/Debian) Linux  (contributed by xeno74):  [arcticfox-27.9.15.linux-powerpc64.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.15.linux-powerpc64.tar.bz2)

Screenshots:

[[IMG]https://i.pinimg.com/564x/7b/2f/1c/7b2f1c2344feae13ccd669124bda42eb.jpg[/IMG]]("https://i.pinimg.com/originals/7b/2f/1c/7b2f1c2344feae13ccd669124bda42eb.png") [[IMG]https://i.pinimg.com/564x/d9/64/4b/d9644b74d17e985a2e0d11beade963c1.jpg[/IMG]]("https://i.pinimg.com/originals/d9/64/4b/d9644b74d17e985a2e0d11beade963c1.png")

[[IMG]https://i.pinimg.com/564x/16/dc/03/16dc036ed38c5dc3075153c71d77c0a8.jpg[/IMG]]("https://i.pinimg.com/originals/16/dc/03/16dc036ed38c5dc3075153c71d77c0a8.png") [[IMG]https://i.pinimg.com/564x/29/2c/0f/292c0f63e88f6aba88275d850234631c.jpg[/IMG]]("https://i.pinimg.com/originals/29/2c/0f/292c0f63e88f6aba88275d850234631c.png")

Please test Arctic Fox.

Thanks,
Christian

---

### Post by conaljardine on 2019-02-11
Amazing! For the first time in years I can use Youtube and BBC iPlayer smoothly in the same browser on my G5 PowerMac, instead of juggling Firefox and Qupzilla.

Plus I also have a 32-bit intel Mac running OSX 10.6, which I have been looking (unsuccessfully) for a maintained browser for.

Now to test it on the old G3 iMac...

This is perfect!

Thanks for sharing!

---

### Post by gsahli on 2019-02-11
Working well on my G4 MDD w/ Ubuntu 16.04. Thanks!

---

### Post by xeno74 on 2019-02-13
Hi All,

I was able to compile Arctic Fox **27.9.15** on Ubuntu **10.04.4** LTS PowerPC today! :-)

I had to add the GCC 4.8 and the libatomic1 via the repository 'ppa:ubuntu-toolchain-r/test'. Additionally I had to compile Python 2.7 because Arctic Fox depends on Python 2.7. Now, Arctic Fox 27.9.15 works on a nine years old Linux system! :-) I will test it and after that I will try to release it.

[[img]https://i.pinimg.com/564x/75/39/5a/75395ae58f779d28abdb67b5b01dfeb5.jpg[/img]](https://i.pinimg.com/originals/75/39/5a/75395ae58f779d28abdb67b5b01dfeb5.png) [[img]https://i.pinimg.com/564x/8a/d3/89/8ad389bd2c6deb5ee7314a937f09e9c4.jpg[/img]](https://i.pinimg.com/originals/8a/d3/89/8ad389bd2c6deb5ee7314a937f09e9c4.png)

Cheers,
Christian

---

### Post by xeno74 on 2019-02-14
Hi All,

I released a test version of **Arctic Fox 27.9.15** for **Ubuntu 10.04.4 LTS PowerPC** (Lucid Lynx) today. Maybe it works on Debian 6 (Squeeze) too.

Please note: It doesn't work on Ubuntu 10.04.0. You need Ubuntu 10.04.4. Unfortunately '**mach package**' doesn't work on Ubuntu 10.04.4 so I had to create the package manually. That means, the package is much bigger than the default package. However, Arctic Fox 27.9.15 works fantastic on Ubuntu 10.04.4. The default old web browser Firefox can't access many websites anymore. Arctic Fox is faster and brings Ubuntu 10.04 back to the web. :-)

Download: [arcticfox-27.9.15-ubuntu10.04-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.15-ubuntu10.04-powerpc.tar.bz2)

Additionally you need the **libatomic1** package.

Download: [libatomic-ubuntu10.04-powerpc.tar.bz2](http://www.xenosoft.de/libatomic-ubuntu10.04-powerpc.tar.bz2)

Please copy the file '**libatomic.so.1**' to '**/usr/lib/**' with the following command:

```
sudo cp libatomic.so.1 /usr/lib/
```

Maybe you need **Python 2.7** as well. I had to compile Python 2.7 because Arctic Fox depends on Python 2.7 but it wasn't difficult to compile it.

Compiling Python:

```
./configure --prefix=/usr
```

```
make
```

```
sudo make install
```

After that you can start Arctic Fox with:

```
./arcticfox
```

Screenshot of Arctic Fox 27.9.15 on my refurbished Ubuntu 10.04.4 LTS (GCC 4.8.1, Python 2.7.3, kernel 5.0-rc6 etc):

[[img]https://i.pinimg.com/564x/bb/1e/08/bb1e084edd655afd154885eb7aa9ef18.jpg[/img]](https://i.pinimg.com/originals/bb/1e/08/bb1e084edd655afd154885eb7aa9ef18.png)

Cheers,
Christian

---

### Post by xeno74 on 2019-02-28
Hi All,

I was able to solve the problem with **mach package** last week.

**Arctic Fox 27.9.15** works on **Ubuntu 10.04.0 LTS PowerPC** (Lucid Lynx) now! You don't need Ubuntu 10.04.4 as a requirement anymore!

I successfully tested it on the Ubuntu 10.04.0 Live DVD today.

You don't need to install **Python 2.7** anymore but you need to install the **GCC 4.8** and the **libatomic1** via the repository '[ppa:ubuntu-toolchain-r/test](http://ubuntuhandbook.org/index.php/2013/08/install-gcc-4-8-via-ppa-in-ubuntu-12-04-13-04/)'. 

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

```
sudo apt-get update; sudo apt-get install gcc-4.8 g++-4.8
```

Download: [arcticfox-27.9.15-2-ubuntu10.04-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.15-2-ubuntu10.04-powerpc.tar.bz2)

After that you can start Arctic Fox with:

```
./arcticfox
```

Screenshot of Arctic Fox 27.9.15 on the Ubuntu 10.04.0 Live DVD:

[[img]https://i.pinimg.com/564x/96/da/7d/96da7d6300bcc1b30470d2102f0a18e7.jpg[/img]](https://i.pinimg.com/originals/96/da/7d/96da7d6300bcc1b30470d2102f0a18e7.png)

Cheers,
Christian

---

### Post by xeno74 on 2019-02-28
Hi All,

There is an issue with WebP on PowerPC. Sometimes you get washed out images. Wart Hog Matt has a workaround for this issue.

I tested it today and it works! :-)


[LIST=1]
[*] ```
about:config
``` 
[*] I confirmed '**I promise to be careful!**' 
[*] I searched for '**image.http.accept**' 
[*] I double-clicked on '**image.http.accept**' 
[*] I set the value of '**image.http.accept**' to '**image/jxr,image/png,image/;q=0.8,/;q=0.5**' 
[*] I reloaded the problematic website. It's very important to reload the website because if you don't do it, then it only opens the website from the cache. 
[/LIST]


I successfully tested it on the following Linux PPC distributions:


[LIST]
[*] Fienix PowerPC 32-bit (X1000) 
[*] MATE PowerPC Remix/ubuntu MATE 17.04 32-bit (X1000) 
[*] openSUSE Tumbleweed 20170924 PPC64 (X1000) 
[*] ubuntu MATE 16.04.5 LTS PowerPC 32-bit (X1000 and X5000) 
[*] Fedora 27 Server PPC64 (X5000) 
[*] Ubuntu 10.04.4 LTS PowerPC 32-bit (X1000 and X5000) 
[*] Debian Sid PowerPC 32-bit (X1000) 
[/LIST]


Many thanks to Wart Hog Matt for this workaround! :-)

[[IMG]https://i.pinimg.com/564x/81/9a/75/819a756e9b761e021437430533c9db79.jpg[/IMG]]("https://i.pinimg.com/originals/81/9a/75/819a756e9b761e021437430533c9db79.png")

Cheers,
Christian

---

### Post by eastone on 2019-03-17
It works really well on my G4 2x1.25Ghz and G5 2x2.3Ghz with Mate 16.04.6

---

### Post by xeno74 on 2019-03-22
Hi All,

Arctic Fox **27.9.16** is available. :)

Download: [arcticfox-27.9.16.linux-powerpc.tar.bz2]("https://drive.google.com/file/d/1nt_XAW_AqgxEESiJsHdPMVHlbXZjfGsg/view?usp=sharing")

Source code: [v27.9.16.tar.gz]("https://github.com/wicknix/Arctic-Fox/archive/v27.9.16.tar.gz")

ChangeLog: [v27.9.16]("https://github.com/wicknix/Arctic-Fox/releases/tag/v27.9.16")

I released the new Arctic Fox 27.9.16 for _older_ Linux PPC distributions like Ubuntu **10.04** LTS or higher today.

Download: [arcticfox-27.9.16-ubuntu10.04-powerpc.tar.bz2]("http://www.xenosoft.de/arcticfox-27.9.16-ubuntu10.04-powerpc.tar.bz2")

For Ubuntu **10.04 - 12.04**: You need to install the **GCC 4.8** and the **libatomic1** via the repository '**ppa:ubuntu-toolchain-r/test**'.

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

```
sudo apt-get update; sudo apt-get install gcc-4.8 g++-4.8
```

Sometimes you need only the **libatomic1** package.

Download: [libatomic-ubuntu12.04-powerpc.tar.bz2]("http://www.xenosoft.de/libatomic-ubuntu12.04-powerpc.tar.bz2")

Please copy the file '**libatomic.so.1**' to '**/usr/lib/powerpc-linux-gnu/**' with the following command:

```
sudo cp libatomic.so.1 /usr/lib/powerpc-linux-gnu/
```

Screenshots of the new Arctic Fox 27.9.16 on the Ubuntu 10.04 PowerPC live DVD and on the Lubuntu 12.04 PowerPC live DVD (PowerMac G3):

[[IMG]https://i.pinimg.com/564x/ce/f6/11/cef611cff6830e5802712b3bae64d9f1.jpg[/IMG]]("https://i.pinimg.com/originals/ce/f6/11/cef611cff6830e5802712b3bae64d9f1.png") [[IMG]https://i.pinimg.com/564x/b1/f1/4e/b1f14e153b394b094aadb8f7e6894d47.jpg[/IMG]]("https://i.pinimg.com/originals/b1/f1/4e/b1f14e153b394b094aadb8f7e6894d47.png")

Compiling Arctic Fox **27.9.16** on Ubuntu **10.04.4** LTS PowerPC (PowerMac G4):

[[IMG]https://i.pinimg.com/564x/12/40/cb/1240cbeb2cbe8886827dac51bfd87f75.jpg[/IMG]]("https://i.pinimg.com/originals/12/40/cb/1240cbeb2cbe8886827dac51bfd87f75.png")

Arctic Fox **27.9.16** on Ubuntu **10.04.4** LTS PowerPC (AmigaOne X1000):

[[IMG]https://i.pinimg.com/564x/79/d3/9f/79d39f8069f863e50457f70333989fbf.jpg[/IMG]]("https://i.pinimg.com/originals/79/d3/9f/79d39f8069f863e50457f70333989fbf.png")

Please post some photos of your old PowerMac with a running Arctic Fox 27.9.16 on an old Ubuntu or Debian PPC32 distribution.

Thanks,
Christian

---

### Post by xeno74 on 2019-03-24
Screenshot of Arctic Fox **27.9.16** on the Ubuntu 12.04.5 PowerPC Live DVD:

[[img]https://i.pinimg.com/564x/f3/37/e0/f337e09e930101cedb599beda5e7282b.jpg[/img]](https://i.pinimg.com/originals/f3/37/e0/f337e09e930101cedb599beda5e7282b.png)

---

### Post by csae2608 on 2019-04-14
Hello , thank you very much , this is highly appreciated!

Hope to test this soon on a MacMini G4 with Debian Squeeze if i still get it up and running.

Question: would it be possible to release also a i386 version of this for an older Pentium M Mobile or Pentium 4 Computer?
ONly inhibitor for running Debian Squeeze was in fact the outdated browser.

---

### Post by xeno74 on 2019-05-13
Hi All,

Arctic Fox **27.9.17** has been released.

Download: [github.com/wicknix/Arctic-Fox](https://github.com/wicknix/Arctic-Fox/wiki/Downloads?fbclid=IwAR2QAPzbaFfST5zYxmnXjMceqihOOuP5MsK-R27awuNAJFEg9J0hkIxx7rw)

Change Log: [github.com/wicknix/Arctic-Fox/releases/tag/v27.9.17](https://github.com/wicknix/Arctic-Fox/releases/tag/v27.9.17?fbclid=IwAR2dtyiW0ofzv4MzC4qVsgzYoBK8AOf5FGcY6JhyzwVJPhCHzjZqn2p71lc)

I released Arctic Fox 27.9.17 for old Linux PowerPC distributions like Ubuntu 10.04 or higher today.

Download: [arcticfox-27.9.17-ubuntu10.04-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.17-ubuntu10.04-powerpc.tar.bz2)

For Ubuntu 10.04: You need to install the **GCC 4.8** and the **libatomic1** via the repository '**ppa:ubuntu-toolchain-r/test**'.

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

```
sudo apt-get update; sudo apt-get install gcc-4.8 g++-4.8
```

For Ubuntu 12.04: You need the **libatomic1** package. Download: [libatomic-ubuntu12.04-powerpc.tar.bz2](http://www.xenosoft.de/libatomic-ubuntu12.04-powerpc.tar.bz2)

Please copy the file '**libatomic.so.1**' to '**/usr/lib/powerpc-linux-gnu/**' with the following command:

```
sudo cp libatomic.so.1 /usr/lib/powerpc-linux-gnu/
```

Screenshot of Arctic Fox 27.9.17 on Ubuntu 10.04.4 LTS PowerPC:

[[img]https://i.pinimg.com/564x/cf/6d/52/cf6d529075aa0379ece09c8ee21b608c.jpg[/img]](https://i.pinimg.com/originals/cf/6d/52/cf6d529075aa0379ece09c8ee21b608c.png)

Cheers,
Christian

---

### Post by xeno74 on 2019-08-07
Hi All,

I released Arctic Fox **27.9.18a1** for old Linux PowerPC distributions like Ubuntu 10.04 or higher today.

Download: [arcticfox-27.9.18a1-ubuntu10.04-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.18a1-ubuntu10.04-powerpc.tar.bz2)

For Ubuntu 10.04: You need to install the **GCC 4.8** and the **libatomic1** via the repository '**ppa:ubuntu-toolchain-r/test**'.

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

```
sudo apt-get update; sudo apt-get install gcc-4.8 g++-4.8
```

For Ubuntu 12.04: You need the **libatomic1** package. Download: [libatomic-ubuntu12.04-powerpc.tar.bz2](http://www.xenosoft.de/libatomic-ubuntu12.04-powerpc.tar.bz2)

Please copy the file '**libatomic.so.1**' to '**/usr/lib/powerpc-linux-gnu/**' with the following command:

```
sudo cp libatomic.so.1 /usr/lib/powerpc-linux-gnu/
```

Screenshot of Arctic Fox 27.9.18a1 on Ubuntu 10.04.4 LTS PowerPC:

[[img]https://i.pinimg.com/564x/cb/e4/b5/cbe4b59339796e1b92fd15fee8304931.jpg[/img]](https://i.pinimg.com/originals/cb/e4/b5/cbe4b59339796e1b92fd15fee8304931.png)

Cheers,
Christian

---

### Post by xeno74 on 2019-09-11
Hi All,

Arctic Fox **27.9.18** has been released for Ubuntu PowerPC. :-)

Download: [arcticfox-27.9.18.linux-powerpc.tar.bz2](https://drive.google.com/file/d/1n-WQJfuabr_K69XrdlRWE1MzoWKc5g1S/view?usp=sharing) (For Ubuntu 16.04 PowerPC or higher)

Change log: [https://github.com/wicknix/Arctic-Fox/releases/tag/27.9.18](https://github.com/wicknix/Arctic-Fox/releases/tag/27.9.18)

Additionally there is Arctic Fox **27.9.18** for old Linux PowerPC distributions like Ubuntu 10.04 or higher.

Download: [arcticfox-27.9.18-ubuntu10.04-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.18-ubuntu10.04-powerpc.tar.bz2)

For Ubuntu 10.04: You need to install the **GCC 4.8** and the **libatomic1** via the repository '**ppa:ubuntu-toolchain-r/test**'.

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

```
sudo apt-get update; sudo apt-get install gcc-4.8 g++-4.8
```

For Ubuntu 12.04: You need the **libatomic1** package. Download: [libatomic-ubuntu12.04-powerpc.tar.bz2](http://www.xenosoft.de/libatomic-ubuntu12.04-powerpc.tar.bz2)

Please copy the file '**libatomic.so.1**' to '**/usr/lib/powerpc-linux-gnu/**' with the following command:

```
sudo cp libatomic.so.1 /usr/lib/powerpc-linux-gnu/
```

Screenshots of Arctic Fox 27.9.18 for old Linux distributions:

[[img]https://i.pinimg.com/564x/07/3a/61/073a610da8e7788f3a791f24fc05e081.jpg[/img]](https://i.pinimg.com/originals/07/3a/61/073a610da8e7788f3a791f24fc05e081.png)

[[img]https://i.pinimg.com/564x/d6/10/e5/d610e5a8499709a119d6eb01182fe686.jpg[/img]](https://i.pinimg.com/originals/d6/10/e5/d610e5a8499709a119d6eb01182fe686.png)

[[img]https://i.pinimg.com/564x/12/9a/a5/129aa5c937352ab3cbb64b880aba73f7.jpg[/img]](https://i.pinimg.com/originals/12/9a/a5/129aa5c937352ab3cbb64b880aba73f7.png)

Cheers,
Christian

---

### Post by Dev'olution on 2019-09-11
Will this work within a PowerPC VM?

---

### Post by xeno74 on 2019-09-11
> **Dev'olution said:**
> Will this work within a PowerPC VM?

It works on QEMU (PPC64 and PPC with or without KVM/KVM PR).

---

### Post by este.el.paz on 2019-09-21
@xeno74:

I was playing around a bit with the last of my running PPC units today, my iBook G4 with 656MB of RAM . . . running Lu 16.04 . . . it has a hard time with the resource demanding "web" provided by Ten4Fox . . . .  From what I'm seeing in this post it looks like you are mostly using your Arctic Fox browser for 10.04 - 12.04???  Any reason to try it out in 16.04 PPC?  And that would be more or less the same commands to add into repos first??  Or, something completely different?  I was going to try to play with it in the iBook but the fan motor was blowing so much with a browser open that the computer becomes "overwhelmed" and "dysfunctional" . . . even Qupzilla isn't too much better . . . .

eep

---

### Post by xeno74 on 2019-09-24
@[**[COLOR=#000000]este.el.paz[/COLOR]**]("https://ubuntuforums.org/member.php?u=1228965")

I use Arctic Fox on ubuntu MATE 16.04 too. ;-) It's the best web browser currently.

---

### Post by xeno74 on 2019-09-24
[IMG]http://sebaro.pro/viewtube/logo.png[/IMG]

**YouTube videos in HD with ViewTube and Arctic Fox**

Installation instructions for ubuntu MATE 16.04.6 PowerPC

[LIST=1]
[*] Install VLC and the VLC browser plugin with the following command:
```
sudo apt-get install browser-plugin-vlc
``` 
[*] Start Arctic Fox and install the add-on [Greasemonkey version **3.31.4**]("https://github.com/janekptacijarabaci/greasemonkey/releases/tag/3.31.4Fork") 
[*] Restart Arctic Fox 
[*] After that, add the [ViewTube script]("http://isebaro.com/viewtube/?ln=en") to Greasemonkey 
[*] Then you have to activate the VLC plugin. You can activate it via Menu Tools - Add-ons - Plugins. 
[/LIST]

Screenshots of ViewTube on ubuntu MATE 16.04 PowerPC:

[[IMG]https://i.pinimg.com/564x/24/82/c3/2482c3553cd3d00e5f886f36a60389a6.jpg[/IMG]]("https://i.pinimg.com/originals/24/82/c3/2482c3553cd3d00e5f886f36a60389a6.png") [[IMG]https://i.pinimg.com/564x/d5/78/52/d578524a689a3567e046477fb089e12c.jpg[/IMG]]("https://i.pinimg.com/originals/d5/78/52/d578524a689a3567e046477fb089e12c.png")

---

### Post by este.el.paz on 2019-09-25
@xeno74:

Thanks very kindly for the thorough instructions . . . appreciate it, I'll give it a try and let you know . . . .

---

### Post by este.el.paz on 2019-09-28
@xeno74:

Tried to get your package, but I must be doing something wrong . . . tried to search for it in synaptic and nothing showed up for "arctic fox" so I downloaded your link for 16.04 and got the .tar.bzxx file into Downloads on my screechingly slow iBook . . . then I tried to get GDebi Package installer to install it, but it said, "This is not a debian file and can't be installed."  So then I tried to "extract" it and tried GDebi again on the "Arctic Fox" directory and that time it said, "File is either corrupted or you don't have permission to install it, check permissions."  So I changed all the permissions to "anyone" and that didn't work either.

I then tried to get my old Powermac to get the packages, but there I only have a TTY . . . GUI is refusing to show up and go to work . . . .  Where might my error be, or did somehow the .tar.bz file did get damaged in the download??

---

### Post by xeno74 on 2019-10-04
@[**[COLOR=#000000]este.el.paz[/COLOR]**]("https://ubuntuforums.org/member.php?u=1228965")

Sorry for my late answer. You don't need to install it with GDebi. You can start it with **./arcticfox** in the "arcticfox" folder.

---

### Post by este.el.paz on 2019-10-04
> **xeno74 said:**
> @[**[COLOR=#000000]este.el.paz[/COLOR]**]("https://ubuntuforums.org/member.php?u=1228965")

Sorry for my late answer. You don't need to install it with GDebi. You can start it with **./arcticfox** in the "arcticfox" folder.

@xeno74:

Thanks for the follow up, I'll check it and see if it's "obvious" . . . I did go into the folder and clicked on a few items . . . I'll see what happens if I click more "assertively" . . . ????

---

### Post by xeno74 on 2019-10-04
> **este.el.paz said:**
> @xeno74:

Thanks for the follow up, I'll check it and see if it's "obvious" . . . I did go into the folder and clicked on a few items . . . I'll see what happens if I click more "assertively" . . . ????

Please start Arctic Fox with **./arcticfox** in a terminal.

```
cd arcticfox/
```

```
./arcticfox
```

---

### Post by este.el.paz on 2019-10-04
> **xeno74 said:**
> Please start Arctic Fox with **./arcticfox** in a terminal.

```
cd arcticfox/
```

```
./arcticfox
```

@xeno74:

OK, that makes more sense, I think I tried ```
arcticfox
``` as my attempt in the terminal, missed the "cd" and then the "./" . . . be a day or so before I get back over to the PPC world . . . .

---

### Post by xeno74 on 2019-12-18
Hi All,

Wicknix has released Arctic Fox **27.9.19**. :-)

[Change Log](https://github.com/wicknix/Arctic-Fox/releases/tag/v27.9.19?fbclid=IwAR1p_nJDdK251jTvQDH_Nop4gb60cuJT4WCXV5pdb2xIYjKZyGLxoFlLL0Q)

Downloads:

[list]
[*] For 32-bit PowerPC G3/G4/G5 (Ubuntu16/Debian10) Linux: [arcticfox-27.9.19.linux-powerpc.tar.bz2](https://drive.google.com/file/d/1NWIO34HXnqWrl9eZLmUWU81M0uge__0t/view?usp=sharing)
[*] For older 32-bit distributions like Ubuntu14/12/10 and Debian8/9 (G3/G4/G5): [arcticfox-27.9.19-ubuntu10.04-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.9.19-ubuntu10.04-powerpc.tar.bz2)
[*] [Source code (zip)](https://github.com/wicknix/Arctic-Fox/archive/v27.9.19.zip)
[*] [Source code (tar.gz)](https://github.com/wicknix/Arctic-Fox/archive/v27.9.19.tar.gz)[/list]

Support thread: [forums.macrumors.com](https://forums.macrumors.com/threads/arctic-fox-web-browser-for-10-6-32-64-bit.2133051/)

For Ubuntu 10.04: You need to install the **GCC 4.8** and the **libatomic1** via the repository '**ppa:ubuntu-toolchain-r/test**'.

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

```
sudo apt-get update; sudo apt-get install gcc-4.8 g++-4.8
```

For Ubuntu 12.04: You need the **libatomic1** package. Download: [libatomic-ubuntu12.04-powerpc.tar.bz2](http://www.xenosoft.de/libatomic-ubuntu12.04-powerpc.tar.bz2)

Please copy the file '**libatomic.so.1**' to '**/usr/lib/powerpc-linux-gnu/**' with the following command:

```
sudo cp libatomic.so.1 /usr/lib/powerpc-linux-gnu/
```

Screenshot of the new Arctic Fox 27.9.19 on Ubuntu 10.04.4 LTS Lucid PowerPC (A-EON AmigaOne X5000/40):

[https://i.pinimg.com/564x/9b/7d/50/9b7d50205e6cb1b1ed4008260df83ade.jpg](https://i.pinimg.com/564x/9b/7d/50/9b7d50205e6cb1b1ed4008260df83ade.jpg)

Screenshot of the new Arctic Fox 27.9.19 on Ubuntu 10.04.4 LTS Lucid PowerPC (Apple PowerMac G4):

[https://i.pinimg.com/564x/a7/09/8f/a7098fd222f94ab96c1858ed5a5b1151.jpg](https://i.pinimg.com/564x/a7/09/8f/a7098fd222f94ab96c1858ed5a5b1151.jpg)

Screenshot of the new Arctic Fox 27.9.19 on the Ubuntu 10.04.0 Live DVD PowerPC (Apple PowerMac G3):

[https://i.pinimg.com/564x/23/2a/1e/232a1efdc4cfca0d6135765b4e5715e3.jpg](https://i.pinimg.com/564x/23/2a/1e/232a1efdc4cfca0d6135765b4e5715e3.jpg)

Cheers,
Christian

---

### Post by xeno74 on 2020-03-12
Hi All,

Wicknix has released Arctic Fox **27.10.1**. :-)

[Change Log](https://github.com/wicknix/Arctic-Fox/releases/tag/v27.10.1?fbclid=IwAR3DNbXK1DwqPqo4U9Zoqpgb20oCWfUivmZWMbnyewGiQV2jh0SasUdjbmY)

Downloads:

[list]
[*] For 32-bit PowerPC (Ubuntu 12 / 14 / 16, Debian 8 / 9 /10 / Sid and Void-PPC/glibc version): [arcticfox-27.10.1-linux-powerpc.deb](https://drive.google.com/file/d/1A_QDBFbHBwwKRsBWrTyx4QBSOTUdtpk8/view?usp=sharing)
[*] For older 32-bit distributions like Ubuntu 10.04: [arcticfox-27.10.1-ubuntu10.04-powerpc.tar.bz2](http://www.xenosoft.de/arcticfox-27.10.1-ubuntu10.04-powerpc.tar.bz2)
[*] [Source code (zip)](https://github.com/wicknix/Arctic-Fox/archive/v27.10.1.zip)
[*] [Source code (tar.gz)](https://github.com/wicknix/Arctic-Fox/archive/v27.10.1.tar.gz)[/list]

Support thread: [forums.macrumors.com](https://forums.macrumors.com/threads/arctic-fox-web-browser-for-10-6-32-64-bit.2133051/)

For Ubuntu 10.04: You need to install the **GCC 4.8** and the **libatomic1** via the repository '**ppa:ubuntu-toolchain-r/test**'.

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

```
sudo apt-get update; sudo apt-get install gcc-4.8 g++-4.8
```

[[img]https://i.pinimg.com/564x/2e/1e/28/2e1e28940c17cdc969c8b6c62b98c150.jpg[/img]](https://i.pinimg.com/originals/2e/1e/28/2e1e28940c17cdc969c8b6c62b98c150.png)

Cheers,
Christian

---

### Post by este.el.paz on 2020-03-12
Thanks for posting this update . . . did just hear about wicknix distros, and your linked forum . . . it's possible that my PM3,1 might be returned from the dead enough to be able to use this information . . . seemed like there was a hardware problem . . . might still be there . . . it's now running 17.04 with busted backports . . . no browser was installed in the recent install . . . have to see if it will accept Arctic Fox . . . at some point.

---

### Post by csae2608 on 2020-07-15
Hello,

for some reason i would need to run on my computer Debian Squeeze (powermac g4) and Debian Wheezy (Powermac G5).
Is it not possible to get these browser running also on Debian?
It is my understanding that Ubuntu is based on Debian, just some packages are newer/different.

Thank you Christian.

---

### Post by xeno74 on 2020-08-03
> **csae2608 said:**
> Hello,

for some reason i would need to run on my computer Debian Squeeze (powermac g4) and Debian Wheezy (Powermac G5).
Is it not possible to get these browser running also on Debian?
It is my understanding that Ubuntu is based on Debian, just some packages are newer/different.

Thank you Christian.

Yes, it could be that it works with Debian Squeeze and Wheezy 32-bit PowerPC.

```

17.04  zesty      stretch / sid
16.10  yakkety    stretch / sid
16.04  xenial     stretch / sid
15.10  wily       jessie  / sid   - 8
15.04  vivid      jessie  / sid
14.10  utopic     jessie  / sid
14.04  trusty     jessie  / sid
13.10  saucy      wheezy  / sid   - 7
13.04  raring     wheezy  / sid
12.10  quantal    wheezy  / sid
12.04  precise    wheezy  / sid
11.10  oneiric    wheezy  / sid
11.04  natty      squeeze / sid   - 6
10.10  maverick   squeeze / sid
10.04  lucid      squeeze / sid

```

@All
Here is the Alpha of Arctic Fox 27.10.2 (32-bit) for testing.

Download: [arcticfox-27.10.2a-ubuntu10.04-powerpc.tar.bz2]("http://www.xenosoft.de/arcticfox-27.10.2a-ubuntu10.04-powerpc.tar.bz2") 

[[IMG]https://i.pinimg.com/564x/bb/29/82/bb29822a64df6eb754008e62176e3ba8.jpg[/IMG]]("https://i.pinimg.com/originals/bb/29/82/bb29822a64df6eb754008e62176e3ba8.png")

---

