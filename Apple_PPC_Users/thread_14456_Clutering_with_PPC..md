---
title: "Clutering with PPC."
date: 2005-02-07
forum: Apple PPC Users
---

### Post by FLeiXiuS on 2005-02-07
Hey guys this is my first time journeying onto the venture of power pc linux.  Welp it turned out a success but the probem is, I have 9 G4's which are doing absolutely nothing.  My idea was to cluster them together.  I began to look at Beowulf and Open Mosix.  I couldn't get either of them to work with the ppc kernel.  They are designated for i386 and a few others. 

If anyone has any ideas on what other options there are available please let me know.  I just want to do load sharing, no need for mirroring / backup services.  Load purposes is all that matters to me.  I would love to have them connected via network (gig-e)  

I'll give full recognition in the motd to the souls who can find a solution.   Then you can sit there and ssh to a super computer, wouldn't you feel special to see your name? ;-)

---

### Post by DJ_Max on 2005-02-07
With 9 G4's, why not send me a few of them :)

I did a quick search, and found [http://www.garbled.net/clusterit.html](http://www.garbled.net/clusterit.html)
Works on the PPC arch.

---

### Post by FLeiXiuS on 2005-02-08
Yeah, i was looking at that, and It didn't agree with network load sharing.  I'm attempting openmosix again.  The kernel is compiling this time, hopefully trying to get a good work around, perhaps prevail a unstable release for the PPC community.  I will follow up on this in a couple of hours maybe days.  Thanks for the reply.

---

### Post by FLeiXiuS on 2005-02-08
Welp just an update, the kernel is giving me some trouble.

```

nvram.c: In function `read_nvram':
nvram.c:41: error: parse error before "unsigned"
nvram.c:46: error: `i' undeclared (first use in this function)
nvram.c:46: error: (Each undeclared identifier is reported only once
nvram.c:46: error: for each function it appears in.)
nvram.c:48: warning: left-hand operand of comma expression has no effect
make[3]: *** [nvram.o] Error 1
make[3]: Leaving directory `/usr/src/kernel-source-2.4.26/drivers/macintosh'
make[2]: *** [first_rule] Error 2
make[2]: Leaving directory `/usr/src/kernel-source-2.4.26/drivers/macintosh'
make[1]: *** [_subdir_macintosh] Error 2
make[1]: Leaving directory `/usr/src/kernel-source-2.4.26/drivers'
make: *** [_dir_drivers] Error 2

```

Any one who may have some idea's please let me know.  Thank you.

---

### Post by FLeiXiuS on 2005-02-15
bump

---

### Post by WW on 2005-02-18
Have you checked out Apple's Xgrid?

[http://www.apple.com/acg/xgrid/](http://www.apple.com/acg/xgrid/)

It's not linux, but it looks like a nice clustering tool.

---

### Post by FLeiXiuS on 2005-02-19
Ahh Yes, I have; but I needed this to be linux.   Thank you though.

---

### Post by ewaldgroup on 2005-02-19
Check this out. Im not sure if it will work with G4s or not. but at least its a start.

[http://www.terrasoftsolutions.com/products/y-hpc/](http://www.terrasoftsolutions.com/products/y-hpc/)

TerraSoft used to have a distribution called Black Lab. If the above link doesnt work, you might try to find an iso for Black Lab.


-ewaldgroup

---

### Post by ewaldgroup on 2005-02-27
bump.

---

