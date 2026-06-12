---
title: "Gnofract4D"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Incompetnce on 2007-02-27
I want to install [Gnofract4D]("http://gnofract4d.sourceforge.net/") on my ubuntu system, but im not sure what is the best way to do that as im not a very experienced user. there are options to download the tarball, or get a .rpm package which the ubuntu documentation tells me i can convert into a .deb package. which of these routes to fractal fun would people reccomend? it doesnt seem there is any program comparable to gnofract in the package manager...

---

### Post by lambros on 2007-02-27
Hi,

I'm a bit of a fractal fan myself, as well as being fairly experienced with Ubuntu.  I managed to get gnofract4d working by building it from source code, and I don't recall any difficulties doing this.  I don't know any other way to run this program - but you might have some success using 'alien' to convert one of the RPMs into a .deb package (I haven't tried it myself).

If you haven't got it working any other way, I could talk you through building it from source if you want.  Other fractal programs you could install are: xaos and xfractint (these are in the repositories).

Lambros

---

### Post by igknighted on 2007-02-27
You can build the source into a .deb and install via dpkg, that would probably be ideal.

---

### Post by Incompetnce on 2007-02-28
i have played around with xaos and fracint on my old windows system as well as apophysis. it seems as if gnofract offers more stuff.

the ubuntu manual section on compiling from source code leaves a lot to be desired, some tips on how to in general im sure i can pick up from other threads, any gnofract specific comments would be welcome, however...

thanks.

---

### Post by Incompetnce on 2007-02-28
i compiled gnofract and it worked! hooray! couple of points;

1. when installing it said it couldnt find "gconf-2.0" i searched synaptic for that and didnt get any exact  matches... but it works anyway.

2. i did ./setup.py build instead of ./setup.py install because install didnt work. so how do i get a launcher on my desktop, or add gnofract to my applicatios menu?

3. and if i wanted to uninstall gnofract, how would i go about it?

---

### Post by lambros on 2007-02-28
> **Incompetnce said:**
> i compiled gnofract and it worked! hooray! couple of points;

Well done, glad you've got it basically working :-)

> **Incompetnce said:**
> 
1. when installing it said it couldnt find "gconf-2.0" i searched synaptic for that and didnt get any exact  matches... but it works anyway.

2. i did ./setup.py build instead of ./setup.py install because install didnt work. so how do i get a launcher on my desktop, or add gnofract to my applicatios menu?

3. and if i wanted to uninstall gnofract, how would i go about it?

1. Could you try installing the packages libgconf2-dev and python-gconf, then see if the install step works?
2. If you still can't get it to install, it will be fairly tedious to set it up manually.  You could create a desktop shortcut by copying the supplied gnofract4d.desktop file to your desktop.  Then you'd have to edit it: change the "Exec=" and the "Icon=" lines to include the full pathname of your executable and icon files.  And to create a menu entry, I think you'd have to use Ubuntu's menu editor (there might be other ways of doing it, I don't know).  But if you can get the proper installer to work, all this would be automatic.
3. Sorry to disappoint you on this one, but it appears that gnofract4d doesn't provide any obvious means of removal :-(  However, it can record a list of all the files that get installed.  Run this command from your gnofract4d-3.2 folder:

```
sudo ./setup.py install --record installedfiles
```

That will re-run the installation script (no harm in doing this), and create a file called "installedfiles" in that folder (you could choose any name for this file).  You can then go through this list and delete the installed files.  (this last step could be automated)

If you have any more questions, do ask - I'll try my best to help out.

Lambros

---

### Post by Incompetnce on 2007-02-28
having done build instead of install, will now doing install mean i have all sorts of guff i dont need clogging up my HD? (OK, i have 40 gigs of space, but its the principle of the thing...)

having installed those packages (and using sudo) everything went swimmingly. awesome.

thanks for your help, by the way

---

### Post by lambros on 2007-03-01
Yeah, you will have all sorts of guff now :-)  513 files from gnofract4d itself, and then whatever extra packages you had to install.  And a couple of hidden files in your home folder.  Don't worry, it's natural for GNU/Linux installations to build up a lot of cruft after a while.  Doesn't seem to affect the performance though :-)  And Ubuntu provides a few cruft-removal tools, if you're keen.  Briefly:

Synaptic has sections for "Not installed (residual config)" and "Orphaned" packages.  Generally, you can remove stuff in there.
There is the "gtkorphan" tool, which can find packages it thinks you're not using.
There's a package called "cruft" you could look at.  Never used it myself.
My personal favourite is the "Graphical Disk Map" tool.  Package name is "gdmap".  Shows you graphically what's eating up all your disk space.

Have fun :-)

Lambros

---

### Post by catenary on 2007-03-10
A couple of notes.

It is also possible to run Gnofract 4D without installing it. Just run ./setup.py build then ./gnofract4d to run it directly from the directory you unpacked it in.

The 'gconf-2.0' warning just means that it won't be able to work out what your default browser is. Apart from that everything else should work.

---

