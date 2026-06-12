---
title: "[SOLVED] How can I (relatively easily) install packages and Dependencies on my OFFLIN"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-18
"Dependencies" is they key word here. Combining Google and packages.ubuntu.com I'm doing alright with finding and downloading each package I need.  The problem however is that my Ubuntu system is offline so when I try to install one package

ie. **restricted-manager-kde**,  I find out that first I need to install **kdelibs4c2s**, then when I try to install that, I find out that I need **adept-batch**, and then I find out I need **libarts1c2a**, and who knows what will be next for the umteenmillionth iteration.

The repository lists all the dependencies, unfortunately it doesn't list which ones aren't by default included in the Ubuntu install.

Does anyone know if there's some site or some list or some application that can solve this.  It's kind of annoying when I try to install a package on Ubuntu, get denied, turn to my online computer, google the package, follow the link, download the package to my Flash driver, copy it over to my Ubuntu system, install the package, find out there's a missing dependency, remove the Flash driver, connect it to my online system, google the package, follow the link.... you get the idea :)

Anyone have any thoughts?

---

### Post by hyper_ch on 2008-01-18
with apt-on-cd you can create your own "repository" cd and Synaptic has an option somewhere that shows you the dependencies needed for installing something. So you could then just use that list to fetch them all.

---

### Post by bodhi.zazen on 2008-01-18
It is hard.

If you want to do do this manually, you need to look up the dependencies. Easiest way is to look them up like this :

[http://packages.ubuntu.com/gutsy/admin/restricted-manager-kde](http://packages.ubuntu.com/gutsy/admin/restricted-manager-kde)

The alternate would be to download kubuntu (alternate CD) and add the CD as a repository.

Last AptOnCD : [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by toastysquirrel on 2008-01-18
> **hyper_ch said:**
> with apt-on-cd you can create your own "repository" cd and Synaptic has an option somewhere that shows you the dependencies needed for installing something. So you could then just use that list to fetch them all.

> **bodhi.zazen said:**
> It is hard.

If you want to do do this manually, you need to look up the dependencies. Easiest way is to look them up like this :

[http://packages.ubuntu.com/gutsy/admin/restricted-manager-kde](http://packages.ubuntu.com/gutsy/admin/restricted-manager-kde)

The alternate would be to download kubuntu (alternate CD) and add the CD as a repository.

Last AptOnCD : [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

It seems like AptOnCD is something I'd be interested in *after the fact*, since right now I don't know what packages I need (unless I read the program's description wrong :P) because it doesn't make a distinction between what's dependent and present (by default) and what's needs to be obtained.  Through [http://packages.ubuntu.com](http://packages.ubuntu.com) and through Synaptic I can see *all* of the dependencies, but I can't see which ones I actually need.  Although, at the rate this is going just to get my ATI driver working correctly, it might be just as fast to start with **restricted-manager-kde**, download *all* of its dependences, then go to each dependency and download all of *its* dependencies and so on.

I just seems like there's bound to be some easier way to do this... :confused:

How would Kubuntu's disk help? (curious)

---

### Post by ByteJuggler on 2008-01-18
Can you not download the DVD edition of Ubuntu/Kubuntu which will contain a far greater variety of packes that you could install, and should hopefully include many of the dependencies you're after.  Then you just simply add the DVD to the availble package sources in synaptic, disable the online ones, and it will then automatically install packages from there instead.

---

### Post by toastysquirrel on 2008-01-18
> **ByteJuggler said:**
> Can you not download the DVD edition of Ubuntu/Kubuntu which will contain a far greater variety of packes that you could install, and should hopefully include many of the dependencies you're after.  Then you just simply add the DVD to the availble package sources in synaptic, disable the online ones, and it will then automatically install packages from there instead.

Hmmm.... okay, two part question:
1) Where can I get the DVD version?
2) Since I don't have a DVD burner or reader (yeah, yeah, I need a system upgrade :) ), would I somehow be able to mount the DVD image and use it that way?

---

### Post by hyper_ch on 2008-01-18
[http://cdimages.ubuntu.com/releases/7.10/release/](http://cdimages.ubuntu.com/releases/7.10/release/)

You can mount them using the "mount" command ;)

---

### Post by forestpixie on 2008-01-18
Perhaps these will be some help to you

[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)
[http://ubuntuforums.org/showpost.php?p=3742162&postcount=11](http://ubuntuforums.org/showpost.php?p=3742162&postcount=11)

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by toastysquirrel on 2008-01-18
> **hyper_ch said:**
> [http://cdimages.ubuntu.com/releases/7.10/release/](http://cdimages.ubuntu.com/releases/7.10/release/)

You can mount them using the "mount" command ;)

Okay, so here's what I'm going to do, let me know if there's an easier way to do this.  (Of course as I'm doing this I'm still manually downloading dependencies.)

1) Download the DVD
2) Because my Flash drive is only 1.88gb in size I'm going to have to split the image.  My online computer is W2K, so I'm going to use [skarSPLIT ]("http://www.skarsoft.com/products/skarsplit/")to do this.
3) I'll copy the split image onto my Ubuntu system.
4) Because I don't know of a splitting/merging program that works for both Linux AND Windows, I'll reboot into XP, merge the image, then boot *back* into Ubuntu
5) Mount the image and then take it from there.

If there's a way to combing steps 2-4, I'm all ears :)

---

### Post by SeanHodges on 2008-01-18
I hadn't heard of AptOnCD before, looks really useful.

Thanks for pointing it out.

---

### Post by ByteJuggler on 2008-01-18
> **toastysquirrel said:**
> Okay, so here's what I'm going to do, let me know if there's an easier way to do this.  (Of course as I'm doing this I'm still manually downloading dependencies.)

1) Download the DVD
2) Because my Flash drive is only 1.88gb in size I'm going to have to split the image.  My online computer is W2K, so I'm going to use [skarSPLIT ]("http://www.skarsoft.com/products/skarsplit/")to do this.
3) I'll copy the split image onto my Ubuntu system.
4) Because I don't know of a splitting/merging program that works for both Linux AND Windows, I'll reboot into XP, merge the image, then boot *back* into Ubuntu
5) Mount the image and then take it from there.

If there's a way to combing steps 2-4, I'm all ears :)

I don't know skarSPLIT, but if the chunks of the file it produces are just raw slices with nothing added, then you can easily recombine them on linux using the "cat" command (which is shorthand for "conCATenate"  e.g:

```
cat part1 part2 part3 part4 >resultant_file
```

---

### Post by toastysquirrel on 2008-01-19
> **hyper_ch said:**
> [http://cdimages.ubuntu.com/releases/7.10/release/](http://cdimages.ubuntu.com/releases/7.10/release/)

You can mount them using the "mount" command ;)

How does this work exactly?  I noticed that in Nautilus there's no "mount volume" option for an .iso image and I'm unfamiliar with how to do it from the terminal.  I installed [gmountiso]("http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html"), however that mounts the image as a browseable folder which doesn't seem to do any good.

Two more questions that I think are related:

1) How do you change volumes from the terminal window? :p
2) How do you tell your Ubuntu (via Synaptic???) to use the soon-to-be mounted image as a repository?

---

### Post by toastysquirrel on 2008-01-19
> **forestpixie said:**
> Perhaps these will be some help to you

[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)
[http://ubuntuforums.org/showpost.php?p=3742162&postcount=11](http://ubuntuforums.org/showpost.php?p=3742162&postcount=11)

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

This seems like a completely kick *** solution.  You may have totally saved my butt when it comes to beginning to use Ubuntu and installing apps.

---

