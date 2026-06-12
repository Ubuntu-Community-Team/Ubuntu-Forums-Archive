---
title: "ifpgui: how to install?"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by Rinzwind on 2005-12-05
I have an iRiver and successfully installed ifp. The command works and I can view files on my iRiver (go me!).
BUT there's a GUI for the iRiver called ifpgui. It's not in the aps (breezy, omniverse and universe).

Soooooooooo how do I go about installing this?

I think I need to unpack ifp_gui-0.10.5.tar.gz inside /bin/ and then  do a ./build.sh and  ./noroot.sh. Is this correct? Or if it's not, how would I go about this?


edit: solved.

---

### Post by public_void on 2005-12-05
I think it will be like most other .tar.gz files.

tar -xvzf /PathToFile/ifp_gui-0.10.5.tar.gz : Unpacks the .tar.gz and creates a new directory named after the file
cd ifp_gui-0.10.5 : Change directory to that new directory
./configure : Run configure in that Directory
make : Compiles source
sudo make install : Installs program

---

### Post by Rinzwind on 2005-12-05
I've seen your posts around void :) :)

I solved it rather elegantly. There's a .DEB package out there that did it almost all for me with another GUI: fpi-gnome.

Solved it like this:

[http://ifp-gnome.sourceforge.net/](http://ifp-gnome.sourceforge.net/)

> Installing Ubuntu .deb files

For easiest install, use Ubuntu Linux.  You need three .deb files:  Grab the ifp-gnome AND pyifp install files from the ifp-gnome site, and then get libifp from here. 

Then from a command prompt, type

      sudo dpkg -i ifp-gnome*.deb libifp4*.deb python2.4-pyifp*.deb

(Thanks to Joe Wreschig for creating the libifp4 .deb file!)

 

After that 

> 
sudo ifp-gnome 


from my music directory did the trick.

My iRiver is packed with new files now.

(posting this for others that run  into the same 'problem').

---

### Post by lemino on 2006-05-11
Ok. I have the same problem. I want to use my iFp-795 under linux. Thought I had found the answer to my prayers when I found iFp-Gnome, but after a succesfull install I run into trouble: when I start the program it isn't able to make contact with the player. It asks if the player is connected and turned on. It all seems to work if I issue the command "sudo ifp-gnome", but I don't wanna run programs as root. Surely there must be a way around this, right?

---

### Post by lemino on 2006-05-11
Found the solution: I flashed the thing with the latest UMS firmware, a piece of cake. Now it comes up just like a regular mass storage device. Victory!

---

