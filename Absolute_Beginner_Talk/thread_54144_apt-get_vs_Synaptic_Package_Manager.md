---
title: "apt-get vs Synaptic Package Manager"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by rherman on 2005-08-03
A few questions I have been unluck in searching for answers about:

Should I use Synaptic or apt-get?

Regarding file organization, should I place the installed binaries from an archive into /usr/local with its own folder? Or should I put it in /usr/local/bin in its own folder? 

Pick points, but I just installed Ubuntu, and I want to keep it clean so that I can worry about the job at hand, and not reinstalling and deinstalling down the road. Thanks.

Ubuntu has changed me!

Rob

---

### Post by Zelut on 2005-08-03
Well both Synaptic and apt-get are going to function the same way.  Synaptic is just the GUI version of the apt-get system.  You won't need to worry about install points or directories with either of those as they auto-install packages & libraries.  Simply use #apt-get install <package> or search for that package using Synaptic and you're done.

Some prefer the GUI Synaptic and others like the terminal apt-get.  I, personally, use apt-get because I think using the terminal is faster.. but it does simply come down to personal preference.

---

### Post by black hole sun on 2005-08-03
apt-get is too pedantic for me. I like the SPM because it's so easy to search & install.

But functionality wise, they are identicle.

---

### Post by rherman on 2005-08-03
Thanks. I just tried aptitude as well. I know the package managers do the placement for you as well, but whenever you install from a tgz and it asks for a folder to install to, do you usually put, say Blender3D a 3D suite, in /usr/local/Blender... or /usr/local/bin/Blender... I know it's not terribly important, but I'm sure there's a more common approach to these things. Thanks.

Rob

---

### Post by Zelut on 2005-08-03
I generally avoid manual installation like that (I've run into too many problems in the past).  If I can't find a package using apt-get I then look for an .autopackage.  If those aren't available I look for a .deb package and use #dpkg -i to install those.  If I need it & I can't find it in any of those places I usually put them in /usr/local/... but, again, there are usually one of those three pakcage-types that you can find so it isn't a worry.

---

### Post by rherman on 2005-08-03
/usr/local as opposed to /home/username? 

Since if I try through gnome to double click the tar.gz2 file I don't have permissions to put it into /usr/local, but it decompresses to /home/username just fine. Which is best?
Thanks.

Rob

---

### Post by ltmon on 2005-08-03
[QUOTE=rherman]/usr/local as opposed to /home/username? 

Since if I try through gnome to double click the tar.gz2 file I don't have permissions to put it into /usr/local, but it decompresses to /home/username just fine. Which is best?
Thanks.

Rob[/QUOTE]

I think you aren't understanding what the tar.bz2 (or is it a tar.gz?) file is doing.  Usually they contain the source code, which must be compiled to be able to run it.  Often compiling can be difficult (although sometimes it 'just works').

It's best not to compile if you can get hold of a binary package another way.  I would have thought Blender was in the repositories somewhere, although I can't check right now.

The following is the basic instructions for compiling, if you wish to go through with this:

--------------------------------------------------------------------------

First, decompress the archive to somewhere in your home directory (or wherever, it doesn't matter at this stage).

Open a terminal

> cd appdirectory

Replace the appdirectory with the name of the directory that was created when you decompressed the source archive.

> ./configure

This will do precompile checks that you have everything you need to compile.  This can be a long list, and you may need to stop now and install lots of *-dev packages from synaptic.  At very least you will need "build-essential".  For Blender there will be a large number of things to install first, you may have to come back if you can't work it all out from the error messages you get. 

Once the configure stage finishes succesfully do:

> make

This will actually compile the package.  Can take a long time.  Get a cup of coffee at very least for Blender.

Finally:

> sudo make install

This will copy the created program into the right place.  You should now be able to run the program from the command line.  You probably won't have a menu entry for it.

A good habit is to use "checkinstall" to do the last step.  Checkinstall is available through synaptic.  Replace the last step with:

> sudo checkinstall -D make install

This will ask a couple of questions, and then actually create a .deb package and you will be able to easily remove or upgrade your new program through synaptic.

---

### Post by Kyral on 2005-08-03
Blender is in the Universe. Make sure you have the Universe enabled in your /etc/apt/sources.list then do a sudo apt-get install blender

---

### Post by rherman on 2005-08-04
Yes, I found Blender 2.36 in the repositories, but it is up to v 2.37a with major enhancements. On the Blender site, [www.blender3d.org](www.blender3d.org), they offer the the .tar.gz2. It is not source. It is all the files and folders tar'ed up for quicker download. I am able to untar it into a folder and run Blender. My question had to deal with the fact that I could only decompress the folder into my /home/username dir. When I tried to decompress the file into /usr/local, it said I didn't have permission. This is through the  gui, so I don't know how to be able to sudo through the gui. I guess I could just open a terminal and cd to the /usr/local folder and try untaring from there. Any thoughts?

Rob

---

### Post by Irony on 2005-08-04
You got 2.37a to work? I tried uncompressing it but it was empty!

Could you just do a copy command of you uncompressed home Blender folder into a local one. Then delete the home one. Something like;

[I]sudo mkdir /usr/local/blender
sudo cd /home/username/blender /usr/local/blender[/I]

In other words make a folder in your local folder called say blender then copy your current uncompressed folder called say blender into the new blender folder.

---

### Post by rherman on 2005-08-04
Yes, I could, but I thought there was a more elegant way of gaining sudo for the extractor. Your directory was empty? No hidden files, nothing?

Rob

---

