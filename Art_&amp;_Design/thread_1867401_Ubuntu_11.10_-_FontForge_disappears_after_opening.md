---
title: "Ubuntu 11.10 - FontForge disappears after opening"
date: 2011-10-22
forum: Art &amp; Design
---

### Post by bluesmodular on 2011-10-22
Hello all, I tried to open FontForge on Ubuntu 11.10, and it loads up to the point where I can either open an existing file or make a new one, but after I click "New" or open a previous file, the windows disappear completely with no (visible) error messages or pop-up. 

My FontForge version is 0.0.20110222-1build1, and I'm running an AMDx64 machine. This problem did not occur on Ubuntu 10.10... did anyone else have this problem and somehow fixed it? Thanks for the input!

---

### Post by pcar916 on 2011-10-23
> **bluesmodular said:**
> Hello all, I tried to open FontForge on Ubuntu 11.10, and it loads up to the point where I can either open an existing file or make a new one... did anyone else have this problem and somehow fixed it? Thanks for the input!

Ditto... I have the same issue on my new 11.10 installation yesterday. It worked in 10.04. I was just about to post to ask if this was a Fontforge or an 11.10 issue. I have not yet gone to a Fontforge forum.

---

### Post by prokoudine on 2011-10-23
> **bluesmodular said:**
> Hello all, I tried to open FontForge on Ubuntu 11.10, and it loads up to the point where I can either open an existing file or make a new one, but after I click "New" or open a previous file, the windows disappear completely with no (visible) error messages or pop-up.

If you run it from console, it will tell you there was a segmentation fault. I guess GWW just needs to release a new version, because it could be either a build issue or something that's been fixed in upstream ages ago.

---

### Post by pcar916 on 2011-10-24
Ah. The author stated that he'll no longer provide platform specific images. So to make this work we'll (best I can tell) have to compile it on our machines. I don't know how to do that yet so it's back to the documentation for me and hope there's a tutorial handy.

Thanks

---

### Post by 0x0065 on 2011-10-29
> **pcar916 said:**
>  So to make this work we'll (best I can tell) have to compile it on our machines. I don't know how to do that yet so it's back to the documentation for me and hope there's a tutorial handy.

Wow! Has it come to this? Compiling software on a binary distribution? Eeeek, Sigh! I'm having a 90s flashback.

What pcar is saying is that the Ubuntu build of fontforge appears to have not been re-build when libraries that it depends upon where upgraded to a non-compatible version... ...this means that, if you want fontforge today, you'll have to build it yourself. Here was my experience. Yours may vary.

[LIST=1]
[*]Download the source from [http://sourceforge.net/projects/fontforge/files/fontforge-source/](http://sourceforge.net/projects/fontforge/files/fontforge-source/)
[*]cd /tmp
[*]uncompress with tar -xvjf [filepath][filename]
[*]cd fontforg..... [tab completion]
[*]./configure
[*]make
[*]WHEN the build breaks because some binary package maker for Ubuntu decided they couldn't POSSIBLE bear the weight of a few header files in their package, look at the last error message and try to work out which lib[somePackage].dev packages you need to install with Synaptic (in my case, "python-all-dev" appears to have sorted it, but fontforge has lots of image library dependencies, so your mileage may vary markedly)
[*]once you've installed the build dependencies you need, run make again...
[*]repeat until make exits cleanly
[*]sudo make install
[*]check that /usr/local/bin is in your path
[*]meditate as long as you can bare on how you hope to ever upgrade, remove or maintain the software you just installed
[*]google: "man emerge" and sigh a quiet sad sigh...
[*]google: "man revdep-rebuild" and sigh again, then shake your head a little...
[/LIST]

Then run "fontforge" on your lovely binary distro that is still just a little too convenient to really give up, at least on a production workstation, and cut out all that sighing already!

---

### Post by 0x0065 on 2011-10-29
Ohhh!!! (>_<) and you should probably un-install the package manager's version of fontforge before you build your own...

---

### Post by pcar916 on 2011-10-29
Excellent! I'll give this sequence a try in the next couple of days. Thanks for the step-by-step. I'll report back on the outcome.

---

### Post by prokoudine on 2011-10-29
> **0x0065 said:**
> 
[LIST=1]
[*]WHEN the build breaks because some binary package maker for Ubuntu decided they couldn't POSSIBLE bear the weight of a few header files in their package, look at the last error message and try to work out which lib[somePackage].dev packages you need to install with Synaptic (in my case, "python-all-dev" appears to have sorted it, but fontforge has lots of image library dependencies, so your mileage may vary markedly)
[*]once you've installed the build dependencies you need, run make again...
[*]repeat until make exits cleanly[/LIST]


I hereby upgrade you to level 60 of APT wisdom by revealing 'sudo apt-get build-dep $package$' command. It finds and install all packages required to build $package$ from source code.

---

### Post by pcar916 on 2011-10-29
> **prokoudine said:**
> I hereby upgrade you to level 60 of APT wisdom by revealing 'sudo apt-get build-dep $package$' command. It finds and install all packages required to build $package$ from source code.

I saw this in the reference guide. Wouldn't the Unity software center application do this by default, or is the superuser status required to get all of them? If so why would that be?

---

### Post by Nalle Berg on 2011-10-30
Bug report has been filed (not by me):
[https://bugs.launchpad.net/ubuntu/+source/fontforge/+bug/872070](https://bugs.launchpad.net/ubuntu/+source/fontforge/+bug/872070)

If you don't desperately need it today, I'd just wait till they've fixed the bug, if I were you. But if you can't wait however....


./nalle.

---

