---
title: "how to install with ALL dependencies ???"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-31
I've downloaded some .deb programs
but when I want to install them it always asks me for other stuff
and I need to go to synoptics and install them one by one
and the worst pars it not always works.
like my case with blender3d 42.a
I have the .deb package - but it asks for dependencies 
and even after I get them - it doesn't recognize them !

1.how can I install a package with all dependencies ?
2.how can I install a package with all dependencies if I have the .deb package on my PC already ?

---

### Post by croak77 on 2006-08-31
The .deb you downloaded might be built against Debian Etch or Sid. Sometimes dependencies might be newer in Debian then in Ubuntu. 

You can try sudo aptitude install packagename. It might be easier then opening Synaptic.

---

### Post by omns on 2006-08-31
.

---

### Post by MaximB on 2006-08-31
> **manicka said:**
> Double clicking on the downloaded package in Dapper should start up gdebi which will install the package and necessary deps in a GUI.

but it still asks for dependencies
can I install from .deb file in my PC with all dependencies ?

---

### Post by omns on 2006-08-31
.

---

### Post by MaximB on 2006-08-31
well - it doesn't
it just asks me to install it myself
and it doesn't work all the time

---

### Post by mssever on 2006-08-31
Are the debs you're talking about already in the repos (available from Synaptic)? If so, you've got a strange problem indeed.

Otherwise, if the dependencies aren't available in the repos, then there isn't an easy solution, unfortunately. You might have to compile from source, which is slightly advanced (I do realize that this is the absolute beginner section, however...). Here's a basic outline of the process:[LIST=1]
[*]Install build-essential and checkinstall.
[*]Enable the appropriate source repositories and do "sudo apt-get source packagename"--or, download and extract a source tarball.
[*]In the terminal, cd to the folder containing the source.
[*]Type "./configure" and install anything that configure complains about not having. If configure fails for any reason, fix the problem before going on. Configure must run to completion or you won't be able to compile.
[*]Make sure that no package manager (Synaptic or otherwise) is running.
[*]Type "make && sudo checkinstall"
[*]Specify a meaningful package name when you see a menu, then let it do its thing.
[*]You should now have the software installed.[/LIST]If you run into problems, let us know and we can help you.

---

### Post by MaximB on 2006-08-31
I already have the .deb file to ubuntu
I don't need to compile
It's not in the repos
I have it in ubuntu.
I just need to get all the dependencies automaticlly

---

### Post by glenn45 on 2006-08-31
one question, is your PC currently connected to the internet or do you download the .deb file from the package site using another pc connected to the internet and then try to install the .deb file in your pc?

---

### Post by mssever on 2006-08-31
> **MAXDDARK said:**
> I already have the .deb file to ubuntu
I don't need to compile
It's not in the repos
I have it in ubuntu.
I just need to get all the dependencies automaticlly

The question is, are the dependencies in the repo? If they're not, they can't be installed automatically, as the automatic installer finds its dependencies in the repo. What dependencies do you need? It may be that recompiling will take care of ome of the dependencies if they can't be found in a repo somewhere.

---

### Post by MaximB on 2006-08-31
I already install the dependencies manually
but it still asks for them
I'm trying to install blender3d 2.42a
It works without installation (the .tar file)
but I wish to upgrade with the .deb file
here's a link :
[http://www.blender3d.org/forum/viewtopic.php?t=9285](http://www.blender3d.org/forum/viewtopic.php?t=9285)

---

### Post by mssever on 2006-08-31
Let me make sure I understand you correctly...
When you look at the deb in GDebi and look in the dependencies section, *each* of the dependencies shows up in Synaptic as *installed*? If so, which dependency is it complaining about?

---

### Post by MaximB on 2006-08-31
they are installed
but it still asks for them
try to install this programs
blender3d is great.

---

### Post by mssever on 2006-08-31
It's difficult to help you when you only provide vague information--despite specifics being requested.

I tried installing fron the link you provided, and here are my results: ```
[FONT=Courier New]~:$ sudo dpkg -i blender-2.42.a1ubuntu2.deb
Password:
Selecting previously deselected package blender.
(Reading database ... 138246 files and directories currently installed.)
Unpacking blender (from blender-2.42.a1ubuntu2.deb) ...
dpkg: dependency problems prevent configuration of blender:
 blender depends on ffmpeg (= 3:0.cvs20060718-5ubuntu1); however:
  Version of ffmpeg on system is 3:0.cvs20050918-5ubuntu1.
 blender depends on libopenal0a; however:
  Package libopenal0a is not installed.
 blender depends on libalut0; however:
  Package libalut0 is not installed.
dpkg: error processing blender (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 blender[/FONT]
```**Are these results the same as yours? If not, what's different?**

Here are the dependency problems I face (I learned this by looking at each dependency in Synaptic):[LIST]
[*]ffmpeg: required version is not available in any of the repos I have enabled. You'll need to find a deb for the proper version
[*]libopenal0a: cannot be automatically installed, because it conflicts with libopenal0, which is a dependency of blender...
[*]libalut0: depends on libopenal0a[/LIST]If I remove blender and then install libopenal0a and libalut0 from the repos, then those dependencies are taken care of. My guess is that if I had the proper version of ffmpeg, then everything would be fine. I don't think that this blender deb was built properly, because it should detect dependency problems *before* installing so that it doesn't leave broken packages around.

Try following the steps I took--assuming that you have version 3:0.cvs20060718-5ubuntu1 of ffmpeg. If that doesn't work for you, please provide **details**, and tell us **exactly** what the dependency problems are.[FONT=Courier New]
[/FONT]

---

### Post by rattlerviper on 2006-09-02
Are the RIGHT versions of the dependencies installed?  Sometimes it gets precarious if you start changing too much by hand as you may experience breakage of packages already installed.
Maybe you answered it already but what are you attempting to install? Are you on Edgy, Dapper, or Breezy?  Did you treat any suggested packages as dependencies? And finally where did you download the dependencies from that you installed? Are you sure they were in fact good?  With some more info we may be able to help you more.

---

