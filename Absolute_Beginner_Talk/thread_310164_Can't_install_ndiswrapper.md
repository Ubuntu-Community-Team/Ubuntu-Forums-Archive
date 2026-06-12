---
title: "Can't install ndiswrapper"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by towync on 2006-11-30
Hey everyone:

I'm trying to install ndiswrapper following the instructions:

1. download latest version of ndiswrapper
2. tar zxvf ndiswrapper-1.30.tar.gz 
3. go to ndiswrapper-1.30 directory
4. run following command: (sudo) make uninstall
5.                  then: make
6. then log in as root and run: make install

I get stuck on step 4 and the error msg is:

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/bin/rm: cannot remove '/lib/modles/2.6.17-10-generic/kernel/drivers/net/ndiswrapper': Is a directory
make: *** [uninstall] Error 1

I'm not sure what to do now to set up ndiswrapper, any help is greatly appreciated :) .

I opened my ndiswraper-1.30 unzipped folder and the contents are: driver (folder), utils (folder), then the files: Authors, ChangeLog, INSTALL, loadndisdriver.8, Makefile, ndiswrapper.8, ndiswrapper.spec, README.

Is there some other way to install ndiswrapper w/o following step 4 and onward?

Also for step 6, does log in as root just mean: cd / ? Why would I be doing that if everything is in the ndiswrapper-1.30 folder? Thanks a bunch.

---

### Post by towync on 2006-11-30
Hi folks, and just to follow up: Under the ndiswrapper-1.30 folder I have two more folders that I mentioned above: 1) utils 2) drivers. 

In the utils folder I have these files: loadndisdriver.c, Makefile, ndiswrapper, and ndiswrapper-buginfo. 
In the drivers folder I have a bunch of .c and .h files.

So does this mean to get ndiswrapper working I wouldn't have to do the make uninstall, make, make install business, and all I had to do was to work with the files under utils? If that's the case, what sequence do I need to click on the files under utils folder to get ndiswrapper to install? Thanks.

---

### Post by sunexplodes on 2006-11-30
have you tried installing it with Synaptic?

---

### Post by towync on 2006-12-01
Hi, thx for the suggestion, but I can't find Synaptic on my Kubuntu 6.10 Edgy OS, I guess Synaptic is just for Ubuntu. I read online somewhere that there's Kynaptic for Kubuntu, but I can't find Kynaptic either, and I'm guessing Kynaptic is for older versions of Kubuntu? 

I think I can get to adept manager and adept installer (add and remove programs), but I'm not sure how to use those to install ndiswrapper, my desktop has no internet access (trying to set it up using ndiswrapper), so I don't really understand how I could use apt-get on the desktop. (Wouldn't I need internet connection on desktop before I can use apt-get?)

Anyway, I played around a bit more with the files in unzipped ndiswrapper-1.30 folder, but I couldn't get any of them to install ndiswrapper. Please help :) , and thx alot.

---

