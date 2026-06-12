---
title: "YAFRay- libc6?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by saxofoner on 2006-08-25
I'm trying to install YAFRay ray tracer, so I downloaded the .deb (Debian) package and tried to install it.  It said something about an unsatisfiable libc6 dependency.  

I tried 
```
sudo apt-get install libc6
```  but it was already updated.  


WHAT TO DO???

---

### Post by Woei on 2006-08-25
Erm, by 'downloading' YAFRay, do you mean downloading it from the project's own website ? There's no need to do that, as this program is already included prepackaged in Ubuntu. However, you'll need to enable the [Universe repository](https://help.ubuntu.com/community/Repositories) before installing YAFray through Synaptic or on a terminal with apt-get install yafray. 

The version included in Dapper is 0.0.8 and installs fine here.

---

### Post by saxofoner on 2006-08-25
Yeah, um, 0.0.9 is out now.  I wanted that.

---

### Post by Woei on 2006-08-25
> **saxofoner said:**
> Yeah, um, 0.0.9 is out now.  I wanted that.

The 'problem' with stable binary distributions like Ubuntu is the fact that you're probably stuck with the version of a given piece of software that was available back when the distribution version was first released. You'll either have to wait for the next version of Ubuntu (Edgy Eft) for an updated binary package *or* compile the package yourself from source (tar.gz archive). Doing the latter requires a bit of expertise and is certainly not as simple as apt-get install foo, and will require you to install compiler tools, linkers and development versions of libraries used by the program in question.

However, the dpkg package management system used by Ubuntu allows you to install the requirements for building a certain package yourself with a single command. This means that you install the dependencies to build 0.08. Uninstall 0.08, and then compile 0.09 from source against the libraries used to build 0.08 in Dapper. In this case, this will probably work as the version update is rather minor, but there are no promises.

You'll want to try something like this: 
```

apt-get install build-essentials 
apt-get build-dep yafray

```

Note that this will pull several megabytes of packages off the network that you only need to build, but not run, the software. You may optionally remove these installed development libraries after you have successfully installed the newest version of yafray.

Alternatively, you may opt to rebuild the possibly updated version of yafray that will end up in Edgy against Dapper, but that is still a bit harder than the previous step.

---

