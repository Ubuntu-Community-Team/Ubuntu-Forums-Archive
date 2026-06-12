---
title: "Remove un-used packages"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by 6and9.42 on 2006-07-13
Hello!

Just starting out with linux (installed ubuntu about a month ago for the first time) and I just wanted to make sure I'm installing/uninstalling packages correctly. I originally installed Fluxbox but have since decided to go with Openbox and would like to uninstall Fluxbox. So I went into the package manager and just told it to remove it, no problems there. My question is, when I installed Fluxbox I *think* it downloaded and installed a few other packages it depended on, but I have no idea what they may be. Is it possible to find packages that are not needed (or were installed by a now removed program) and remove them?

Thanks for the help, I've been browsing these forums for awhile and have found answers to most questions already!

g.

---

### Post by hotbrainz on 2006-07-13
Hiya, 

Well when you install something new, the best idea would be to use:

sudo aptitude install package-name

By doing this the removal command becomes

sudo aptitude remove package-name

In this method, the package and all dependant packages will be removed as well. But using other methods to install, will make you face the problem of having unwanted dependancy packages.

Or you could find what these dependencies are for the "fluxbox" package and remove them one by one. Sounds bad but i dont know of another way.

Hope this helps :)

---

### Post by 6and9.42 on 2006-07-13
Works for me, thanks for the info :)

Is "aptitude install" the same as "apt-get install"? As I've been using apt-get up to this point...

g.

---

### Post by hotbrainz on 2006-07-13
It is the same in terms of installation. It does the same thing. But the additional feature is that it keeps track of all the related packages, making it easy for you to uninstall. 

You can use it all the time. I have never had any issues with it

---

### Post by mcduck on 2006-07-13
you can also install package 'deborphan' and then create a new filter in Synaptic to show only orphaned packages. This is very easy way to remove pacakges that were installed as dependencies for some other package, and were left behind when the original package was uninstalled.

---

### Post by shinythings on 2006-07-13
Or, if you prefere a graphical version, gtkorphan is a pretty good front end.

---

### Post by mcduck on 2006-07-13
> **shinythings said:**
> Or, if you prefere a graphical version, gtkorphan is a pretty good front end.

I'd call Synaptic graphical too ;)

---

### Post by 6and9.42 on 2006-07-13
Perfect! I went with deborphan and that's exactly what I was looking for. Thanks!

---

