---
title: "update manager problem"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-05-30
> sushubh@ubuntu:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the lupin-target package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
sushubh@ubuntu:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the lupin-target package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
sushubh@ubuntu:~$ 


When I start the update manager I get this message:

> A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package lupin-target needs to be reinstalled, but I can't find an archive for it.'

---

### Post by Jussi Kukkonen on 2007-05-30
Have you tried removing the package lupin-target (or downloading it again from where ever you got it, and installing again)?

---

### Post by Sushubh on 2007-05-30
[http://ubuntuforums.org/showthread.php?p=2747116#post2747116](http://ubuntuforums.org/showthread.php?p=2747116#post2747116)

it was from there. how do i remove this package? downloading it again and reinstalling has not helped.

---

### Post by Jussi Kukkonen on 2007-06-01
Looks like the package you installed was somehow broken, and now apt is confused about it... This is a problem that can happen when you install 3rd party packages. I suggest you contact the person who packaged lupin-target, he should know how to fix the problem without breaking other things.

You can try running *apt-get install -f* if you haven't done it already, but I doubt it'll help in this case.

---

### Post by zvacet on 2007-06-01
```
whereis lupin-target
```

This will give you all folders with  lupin-target file.Go to every directory and manualy remove  lupin-target file.

```
sudo rm -r file_name
```

file_name = exact name of lupin-target file in directory.

---

