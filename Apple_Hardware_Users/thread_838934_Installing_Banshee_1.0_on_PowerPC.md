---
title: "Installing Banshee 1.0 on PowerPC"
date: 2008-06-24
forum: Apple Hardware Users
---

### Post by alpine4 on 2008-06-24
Has anybody had any luck installing Banshee 1.0 on a PowerPC Mac?  Even by compiling from source?

I've tried adding the repo to my software sources, and the only thing I'm getting is version 0.13.2.  

Cheers!

---

### Post by EXCiD3 on 2008-06-24
Is this what you put in your sources.list file? if not then this is what you should use instead: ```

deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
```

Then run these in terminal for your new banshee:

```
sudo apt-get update
sudo apt-get install banshee-1
```

You may have to edit the menu because the icon for banshee usually launches "banshee" and not the final version which is "banshee-1"

---

### Post by alpine4 on 2008-06-24
> Is this what you put in your sources.list file? if not then this is what you should use instead: ```

deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
```

Yep, that's exactly what I had.  And each time I try to install, apt tells me it can't find banshee-1

---

### Post by EXCiD3 on 2008-06-24
I just looked through the repository manually (just type the url into your browser and look through 'pool') and it looks to me like there are no powerpc builds available. You will probably have to compile from source. It should be fairly easy as instructions are on their website but it looks like they do not create binary builds for powerpc unfortunately. :(

---

### Post by alpine4 on 2008-06-24
> **EXCiD3 said:**
> I just looked through the repository manually (just type the url into your browser and look through 'pool') and it looks to me like there are no powerpc builds available. You will probably have to compile from source. It should be fairly easy as instructions are on their website but it looks like they do not create binary builds for powerpc unfortunately. :(

Had a feeling that was going to be the case, thanks for the help!

---

### Post by EXCiD3 on 2008-06-24
Yeah :( kinda surprising they dont have a build for it, but then again its only a couple of guys writing the software, if they dont have a mac cant really expect them to release a build. All the more reason you should jump in to help the project and make a deb package for powerpc to be put into their repos! ;)

---

