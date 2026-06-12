---
title: "beryl tarballs"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by LostArt on 2007-06-10
I have a desktop with no internet, and I would like to install beryl from the tarballs, but I have no idea how to do it so I need some help. So far, I've downloaded all of the beryl tarballs, Aquamarine, beryl core, and all of that. Now I need some help on how to install.

---

### Post by Kobalt on 2007-06-10
You'd rather download the packages and their dependencies from [http://packages.ubuntu.com](http://packages.ubuntu.com). Once you have them all, just double-click them to install.

---

### Post by KIAaze on 2007-06-10
1)
Well, I don't know if installing from tarballs is the easiest method.
Theoretically, you would have to install the tarballs in the right order by doing:
```
tar -xzvf tarball
cd tarball
./configure
make
sudo make install
cd ..

```

The problem is however, that you might get some errors in the ./configure and make phases.
Those error messages are sometimes easy to solve if they something like "xyz missing", but can also be more complicated.
So I don't think it's straightforward to install it from source.
If you plan to do so, make sure to always read the README and INSTALL files from the tarballs when available.

2)An easier solution is to install the binary .deb packages directly.
You can get them here: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
The only problems you might encounter when installing a .deb are probably dependency errors.
In that case, all you have to do is download the corresponding .deb.

3)
To make things even easier, there is a way to avoid any missing dependencies. However, I don't remember exactly how.

edit:
Here it is:
[howto for installing software without an internet connection]("http://ubuntuforums.org/showthread.php?t=34113")
It's not exactly the page I remember, but it also solves the repetitive download problem.

---

### Post by LostArt on 2007-06-11
Thank you very much, I deffinitely have to check out the page for computer's with no internet, and I was hoping that I'd be able to find the .deb packages

---

### Post by KIAaze on 2007-06-11
Now that I have some time, I searched again for the easiest solution:
> 1)Open synaptic
2)Click on File->Generate package download script
3)Go to the other PC (with GNU/Linux on it so that you can run the script) and run the script on it. It should generate something. Don't know what since I never tried it.
4)Get that thing back to the other PC.
5)Open synaptic and click on File->Add downloaded packages


Much easier, no? :)

Here's the thread where it was:  [Programme and Package Installation methods]("http://ubuntuforums.org/showthread.php?t=414490")

I don't know if it can be found somewhere in the Ubuntu doc. If not, it should be there! ;)

---

