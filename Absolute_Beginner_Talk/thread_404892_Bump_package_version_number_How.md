---
title: "Bump package version number? How?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-04-09
I have installed a patched version of tilda to get true transeprency. It is a previous version of tilda and i get a notfication to update but it will wipe out my patched tilda. The instructions say that i can bump the package version to avoid this. How do i do that? below is the only instructions i have on how to do this but i am clueless. 

[I]
Bump package version number if you want by adding an entry to top of debian/changelog file like as tilda_0.09.3-0ubuntu1 to tilda_0.09.3-0ubuntu1.1[/I]

Here is where i got the patch if interested. 

[http://forum.beryl-project.org/viewtopic.php?f=51&t=1742&hilit=tilda]("http://forum.beryl-project.org/viewtopic.php?f=51&t=1742&hilit=tilda")

---

### Post by pjones0404 on 2007-04-09
Anyone have any ideas? i am fairly new to linux, i undertsand what i need to do but not how.

Also can i but the patch into the newest version of tilda and get the same effect?

Any and all help is greatly appreciated.

---

### Post by chalex on 2007-04-09
"bump the package version number" means to change one of the config files to say the version is "tilda_0.09.3-0ubuntu1.1" instead of "tilda_0.09.3-0ubuntu1".  This is only useful because when you build the package, the name of the resulting deb won't conflict.  This doesn't affect the functionality of the program.

You should try patching the newer version like you did with the older version.  Perhaps the patch will work, or perhaps someone needs to write a new patch for the new version.

---

### Post by JoseArmandoJeronymo on 2007-12-23
In case someone is still wondering how to bump up the package number, here follows a small explanation.

The key is to add a few lines to the top of the file named "changelog" that is on the debian folder of the source code folder. (Not the 'ChangeLog" that is on the source code folder.)

These lines tell the package creator the number of that new version or release, the name of the maintainer responsible for the changes and a small summary of the changes. It is easy to do, just use the other lines as an example but mind the precise indentation and lay-out or it will not compile the package.

You can find a complete explanation here: [http://www.debian.org/doc/debian-policy/ch-source.html](http://www.debian.org/doc/debian-policy/ch-source.html). Scroll down to "4.4 Debian changelog: debian/changelog".

BTW, the files involved require root privileges so you must open the text editor as sudo (e.g. $ sudo gedit) otherwise it will refuse to save your changes.

If you need help with creating the package you can find a nice summary that worked for me here: [https://bugs.launchpad.net/gdm/+bug/150193](https://bugs.launchpad.net/gdm/+bug/150193).

---

