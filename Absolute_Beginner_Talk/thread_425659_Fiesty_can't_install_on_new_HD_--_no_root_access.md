---
title: "Fiesty can't install on new HD -- no root access"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by thinpaperwings on 2007-04-27
This is the first computer I've built, and it's my first time installing Linux.

The install CD boots up ok, and LiveCD works great, but when I try to install, I get the following error:

	Failed to run /usr/lib/ubiquity/bin/ubiquity 'gtkui' as user root
		Failed to exec new process: Exec format error

Then I went to  System > Administration > Users and groups
and got the following error:
	Failed to run users-admin as user root
		Failed to exec new process: Exec format error

My hard drive is Western Digital Caviar SE16, and is brand new.  

Do I need to do something to my hard drive (either in bios/cmos or in Terminal with LiveCD) to prepare it for installation?  
Or do I need to initially set the password for root via terminal or bios?  

Let me know what other information would be useful.
Thank you for your help!

---

### Post by bobplano on 2007-04-27
maybe the cd has errors. did you check the cd for errors with the option or the hashes?

---

### Post by thinpaperwings on 2007-04-27
More info:  I restarted, and at the startup screen picked "Check CD for defects".

After checking, errors in 10 files were found.

The MD5 sum of the .iso file is correct, so perhaps I simply need to reburn it and try to install again?

I will do that and post back with the outcome. 

Feel free to add suggestions in the meantime!

Thanks!

---

### Post by Najand on 2007-04-27
Yeah, you should. Or try the ubuntu alternative cd.

---

### Post by kai_haider on 2007-04-27
I think I got the same error when I installed and I didn't define a partition as "/" I had it at the default "/media/(something)" that it showed during install. Your problem might be that. Just change the mount location to "/"

---

### Post by thinpaperwings on 2007-04-27
I've tried reburning the .iso image.  (btw, I'm using Mac OS 10.4)

Using Disk Utility again at a slower speed (16x instead of the 24x I used before) yielded 9 instead of the 10 errors I got the first time.

Using YuBurner yielded no results as I couldn't get it to burn the image (it burned the image *file* to the disk, such that the disk had the .iso on it, instead of the stuff *in* the .iso).

Using Firestarter yielded 11 errors on the disk.

When I downloaded the .iso I checked the md5 sum and it was correct.  Does that mean that the image I have downloaded is good, and the problem is with the burning?  Or could there be a problem with the downloading of the .iso that didn't show up with the md5 sum check?  In other words, would it be a good idea to re-download the .iso file, and reburn the new .iso file?  Or should I find other methods of burning the .iso file I have already downloaded?

---

### Post by bobplano on 2007-04-27
16X is almost always way too fast to burn an iso this big without errors. try burning at 4X or less and then check it for errors. i don' t think it really matters which burner you use as long as it can burn .iso

---

### Post by Najand on 2007-04-27
16X is too fast. Use speeds less than 4X.

---

### Post by thinpaperwings on 2007-04-27
Awesome, that's good to know.

I'll reburn at 4x and see how that goes.

Thanks : )

---

### Post by thinpaperwings on 2007-04-27
I burned it with Firestarter FX at 2x, and it still showed 5 errors.

Interestingly, when I went back to re-check the md5 sum using YuImageBurner it gave the wrong sum.  I thought that was strange, so I checked it in Terminal, which yielded the correct sum.  I don't understand how the two methods could come to different sums.

So I'm now I'm trying to burn the image via command line (because it at least gives the right md5 sum):
  hdiutil burn ubuntu-7.04-desktop-amd64.iso
I don't know what speed that defaults to.

If this continues to not work, I'll download the alternative image and try that.

---

### Post by thinpaperwings on 2007-04-27
That yielded 7 files with errors.

Now I'm redoing it at 1x speed:
hdiutil burn -speed 1 ubuntu-7.04-desktop-amd64.iso

---

### Post by Najand on 2007-04-28
Well, maybe your problem is not with the cd-rom
ubuntu-7.04-desktop-amd64.iso

---

### Post by thinpaperwings on 2007-04-28
I downloaded the .iso again, checked the md5 sum in terminal, burned it through terminal at 1x, and checked the number of errors on the disk: 6 files have errors.

So I'll try the alternative disk, unless anyone has a better suggestion.

---

### Post by thinpaperwings on 2007-04-28
I gave one more shot at burning the graphical installation image.  This time I used Firestarter FX at 1x speed, yielding 4 errors in the disk (the lowest so far).  

Is this few enough that I can go ahead and attempt the install?  
Or should I really try to get a disk with no errors before attempting to install.

. . . do I need to ask around to find someone with a good burner in order to get an error free burn?

---

### Post by jimrz on 2007-04-28
> **thinpaperwings said:**
> I gave one more shot at burning the graphical installation image.  This time I used Firestarter FX at 1x speed, yielding 4 errors in the disk (the lowest so far).  

Is this few enough that I can go ahead and attempt the install?  
Or should I really try to get a disk with no errors before attempting to install.

. . . do I need to ask around to find someone with a good burner in order to get an error free burn?

maybe try a fresh download or get the alternate. in either case, try using a torrent for your download, as it will do a hash check as part of it's process and then burn at the lowest speed your drive can do.

---

### Post by thinpaperwings on 2007-04-29
I've re-downloaded the graphic and alternate versions, checked their md5 sums (which were correct), and tried burning them at 1x.  None have been error-free.

I ended up installing from the disk with errors in 4 files, and it is working fine for now.  I suppose I can order the imaged CD and reinstall when I get it.

---

