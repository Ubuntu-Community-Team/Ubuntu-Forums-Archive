---
title: "Repository Format For CD"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Frederick J. Harris on 2007-05-03
I had been wondering if it was possible to create a repository myself on a CD and load it with the deb files
required by various packages.  I figured Synaptic might require directories ordered or organized in a certain way to recognize such a CD as a repository, but I wasn't sure.  So as a test I burned the entirety of the xorg-dev meta-package to a cd (almost 200 deb packages, what with all the dependencies) and  then targeted it with Synaptic.  As I kind of expected, Synaptic threw an error and informed me that the cd didn't appear to be a 'repository'.  Meaning, of course, that 'repositories' must have some specific structure.  My question is...What is that structure???

Next I put a Ubuntu installation CD in and looked for packages, that is, deb files.  What I found is that there was a directory off the CD root named 'pool', and under that two directories named 'main' and 'restricted'.  Then under those were the letters of the alphabet with the first letter of a package name being in each respective letter.  For example, under 'B' was found the build-essential package.  However, I believe the build-essential.deb file is really nothing more than a script that lists all the other required pieces of the puzzel, such as binary utilities, libraries, and header files.  These actual constituents of large packages, i.e., the dependencies, must be organized in some way.  Could anyone point me to where this is documented, or if it isn't too complicated, explain it to me?

---

### Post by Bachstelze on 2007-05-03
[https://wiki.ubuntu.com/APTonCD](https://wiki.ubuntu.com/APTonCD)

---

### Post by Billy McCann on 2007-05-03
As HymnToLife pointed out, APTonCD is a great tool.  It's in the repos, so just install it. 

```
sudo apt-get install aptoncd
```

After it's done installing, you can find it in the System > Administration menu.  It'll burn the .deb files of everything you have installed onto a CD or DVD.  Quite a wonderful program, I'd say.

---

### Post by Frederick J. Harris on 2007-05-03
Thanks for the information, but unfortunately, it doesn't help me.  I don't have my Ubuntu installation connected to the internet, and it has been extremely difficult for me, verging on impossible really, to install very large and complex packages 'by hand'.  It actually took me many, many hours to download (through Windows) and install the build-essential package completely manually through dpkg.  I did that about a week or two ago, and if my memory serves there were about 30 deb files what with all the dependencies.  The inter-dependencies are really the problem.  At this time I am contemplating attempting to get the xorg-dev package installed, and in that case there are literally hundreds of deb packages involved.  The complexity of the thing is staggering.  That is why I asked the question of the actual format of repositories.  It seems to me that logic exists within Synaptic to easily accomplish what I wish to do (avoid dpkg and dependency hell, for one thing, and not accidentally trash my system for another), if I can manually create a repository and add the downloaded deb files to it.

Out of desperation, I just checked to see if a Comfort Inn about 20 miles down the road from me has broadband internet access.  Perhaps I ought to just rent a room to try to get it done.

---

### Post by deathbyswiftwind on 2007-05-03
Wow sweet I never heard of that program I installed it and now have a cool prog!

---

### Post by Billy McCann on 2007-05-03
Frederick, 

I see your dilemma now. I'm not sure the best option for you -- besides maybe finding a local hotspot. 

Or the hotel.  (Get the room with the hot tub.)

---

