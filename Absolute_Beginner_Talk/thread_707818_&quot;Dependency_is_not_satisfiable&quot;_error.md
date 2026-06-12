---
title: "&quot;Dependency is not satisfiable&quot; error"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by wiiforblender on 2008-02-25
how do I fix this error: "Dependency is not satisfiable" I get it when I try to install either Blender, or YafRay from the ubuntu package area... I tried Blender.org, but theirs has a bug that they have yet to fix, and I just need something to render my scenes for school the next day... any help?

---

### Post by taurus on 2008-02-25
Maybe you didn't have all the repos enable in /etc/apt/sources.list.  Go to System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark in front of all the lines except the last one, Source code, and the Cdrom in the window below.  Close it and press Refresh.  Now, see if you can install blender from synaptic or close down synaptic first and install it with apt-get.

```
sudo apt-get update
sudo apt-get install blender
```

---

### Post by wiiforblender on 2008-02-25
I'm afraid I did not word this right, I downloaded the deb files from another computer (windows) and brought them to the ubuntu computer via a flash drive, since I have yet to get my internet adapter working...

---

### Post by Sordelka on 2008-02-25
If you are installing from a .deb package, it means you do not have all data packages installed (the error always comes with the name of the dependency lacking). The best way to install is first from synaptic manager and then updating.

Update: for the thing, try looking for the name of the dependency to satisfy in google and download it. Usually it is some library.

---

### Post by wiiforblender on 2008-02-25
I found a list... I'm installing them...

---

### Post by wiiforblender on 2008-02-25
wow, most all of these have dependencies of their own, if I were to move my computer to a wired internet connection temporarily (would be easier than all these tho manage) would the installer automatically install all the needed dependencies???

---

### Post by taurus on 2008-02-25
> **wiiforblender said:**
> wow, most all of these have dependencies of their own, if I were to move my computer to a wired internet connection temporarily (would be easier than all these tho manage) would the installer automatically install all the needed dependencies???

Yes.  It would install all the necessary dependencies for you.

---

### Post by wiiforblender on 2008-02-25
I'll try that and see how it works...

---

### Post by wiiforblender on 2008-02-25
I installed it successfully, but the program is messing up, apparently the same way as the blender.org files... I'll have to wait to find out (I know someone with an older copy, I'll try that and see if it works)

---

### Post by Sordelka on 2008-02-25
Yea one more suggestion:

Get blender from [www.getdeb.net](www.getdeb.net)

It works perfectly on my Ubuntu 7.10 distro!

---

### Post by wiiforblender on 2008-02-26
got it working (relatively, besides this being a low end computer made for long time renders) by just setting the render to be exported to POVray, since the linux blender keeps crashing... and also, I just went through the whole list of files for the package installer, and got every one I would need for a LONG time... tank you ^_^

P.S. support perfecting Wii controllers for Blender

---

