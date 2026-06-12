---
title: "New to linux - what should i do for upkeep?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by neufelry on 2007-05-01
Hello everyone. I just switched to Linux, Feisty specifically, just this last friday. I have found that since i started fiddling around getting my specialty hardware working (dual monitor, ati in specific :( ) i have installed several packages and their dependencies that I may never use again.

Thing is though, I can't remember all the packages i threw on to try things out that I don't think i need. 

My question, if you skipped the first few sentences: What amount of upkeep and removal of packages is necessary to keep my system running well? and how can i perform unused package removal without causing damage to my system?

---

### Post by wizardofyendor on 2007-05-01
As long as the items that have been installed aren't running as services, you shouldn't see any performance hits.

Here is a good guide for removing unused packages.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by trancepose on 2007-05-01
i think you may never need to remove those packages because they are generally very small in size. i don't know your experience level but "don't" attempt to remove them if you are a newbie. i did that fault at my first ubuntu install about 2 months ago and crashed the system.
just trust me. you will begin removing your unnecessary files after some experience. 

in addition, don't remove dependency packages. they are similar to dll files of windows and removal of one requires removal of its children. 

i don't know if there's a special application for removing unused packages, it would also help me

---

### Post by wizardofyendor on 2007-05-01
There is a utility to remove unused packages.

Download deborphan (it's in the repos) then run:

```
deborphan 
```

this will list what packages were installed as dependencies that are not being used any more.

If you are satisfied with what it is going to remove run:

```
sudo deborphan | xargs sudo apt-get -y remove --purge
```

to remove those packages for you.

---

### Post by neufelry on 2007-05-01
As far as experience goes i am not a newb :) I have the sense to not remove anything unless i know absolutely i do not need it. thanks for the concern though.

Thanks for the links and suggested apps wizard, I'll check em out

---

### Post by walesmd on 2007-05-01
This script will list any packages you have installed since installation:
[http://ubuntuforums.org/showthread.php?t=393615](http://ubuntuforums.org/showthread.php?t=393615)

Other than that, just crack open a terminal and use:
```
sudo aptitude remove *packagename*
```
This will remove the package as well as it's dependancies that you are no longer using with other packages. If you accidently remove a package:
```
sudo aptitude install *packagename*
```
and in a matter of seconds you are back up and running as you need to be.

Honestly, it's pretty damn hard to mess up your system by just adding/removing packages - you could even leave them if you wanted to.

---

