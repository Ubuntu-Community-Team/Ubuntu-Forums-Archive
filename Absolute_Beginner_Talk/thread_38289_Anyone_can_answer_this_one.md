---
title: "Anyone can answer this one :?"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by Mr_Tickles on 2005-05-30
Ok, this question will show just how new I am to this operating system.

I have no idea how to run a file.

I have downloaded a .run from the net, it's the linux version, and everything is ok with it.  However, if I double click it, it wants to open gedit, if I right click it gives me an option to open it with something else...

I'm really getting into using ubuntu, but I can't for the life of me, figure out how to run programs outside of the drop down menus.

Please, could someone answer me this one simple thing?

(Yes, I am a windows user :?)

{Edit}Also, I have a problem with my resolution, it's at 1024x786, I want to change it up to 1152x864, but i've read on other threads that this is only possible with Hoary, if so, how do I upgrade? Is there something in the Synaptic Package Manager to examine?{/Edit}

---

### Post by bored2k on 2005-05-30
[QUOTE=Mr_Tickles]Ok, this question will show just how new I am to this operating system.

I have no idea how to run a file.

I have downloaded a .run from the net, it's the linux version, and everything is ok with it.  However, if I double click it, it wants to open gedit, if I right click it gives me an option to open it with something else...

I'm really getting into using ubuntu, but I can't for the life of me, figure out how to run programs outside of the drop down menus.

Please, could someone answer me this one simple thing?

(Yes, I am a windows user :?)

{Edit}Also, I have a problem with my resolution, it's at 1024x786, I want to change it up to 1152x864, but i've read on other threads that this is only possible with Hoary, if so, how do I upgrade? Is there something in the Synaptic Package Manager to examine?{/Edit}[/QUOTE]
 Applications > System > Terminal

Go to the dir you have the file (cd folderX)
chmod +x filename.run
./filename.run

Resolution: try
sudo dpkg-reconfigure xserver-xorg then reboot

What are you trying to run from a .run ?

---

### Post by Mr_Tickles on 2005-05-30
I was trying to run an installation package for Planeshift... not sure if it's any good... thought I'd have a go :)
```
file:///home/dave/Games/Installation%20Files/PlaneShift_CBV0.3.010.run
```

Thanks, that stuff worked well :)
However, I got these messages, although this is surely something to do with the program

```
Uncompressing Planeshift Crystal Blue Version 3.010..
./setup.sh: line 57: dialog: command not found
./setup.sh: line 59: dialog: command not found
./setup.sh: line 113: dialog: command not found
```

Therefore i'm guessing this didn't work :(

I'll try the resolution thing now, thanks :)

---

### Post by Mr_Tickles on 2005-05-30
Also, I don't seem to have xserver-xorg
```
Package `xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

```

The nearest ones in the Synaptic Package Manager were:
```
xserver-common
xserver-xfree86
xserver-xfree86-dbg
```

Any idea how to get the .run file working? or is it a problem with that particular file?

---

### Post by bored2k on 2005-05-30
[QUOTE=Mr_Tickles]Also, I don't seem to have xserver-xorg
```
Package `xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

```

The nearest ones in the Synaptic Package Manager were:
```
xserver-common
xserver-xfree86
xserver-xfree86-dbg
```

Any idea how to get the .run file working? or is it a problem with that particular file?[/QUOTE]
 I used xorg because I thought you had xorg, but try the same with xfree86

---

### Post by Mr_Tickles on 2005-05-30
Brilliant! Thank you very much :D Resolution sorted perfectly now, thanks :D

Erm, any idea about the .run file though? The details I had when running that terminal command are in post #3

---

### Post by bored2k on 2005-05-30
[QUOTE=Mr_Tickles]Brilliant! Thank you very much :D Resolution sorted perfectly now, thanks :D

Erm, any idea about the .run file though? The details I had when running that terminal command are in post #3[/QUOTE]
 You ran ./filename.run and you got those errors ? 
That doesn't look like it's your problem.. Can you paste a little more ??

By the way, you are running an out of date Ubuntu ,you might want to upgrade  to Hoary ;) (you are using Warty).

---

### Post by Mr_Tickles on 2005-05-30
Hmmm, yes, it is Warty, I have no idea how to get Hoary though :?

Here's the entire root terminal text:
```
root@SpikeIII:/home/dave # ls
bookmarks.html  Downloads  Music  spikeii  Video
Desktop         Games      pics   Tools    Work
root@SpikeIII:/home/dave # cd Games
root@SpikeIII:/home/dave/Games # cd Installation\ Files/
root@SpikeIII:/home/dave/Games/Installation Files # chmod +x filename.run
chmod: failed to get attributes of `filename.run': No such file or directory
root@SpikeIII:/home/dave/Games/Installation Files # chmod +x PlaneShift_CBV0.3.0 10.run
root@SpikeIII:/home/dave/Games/Installation Files # ./PlaneShift_CBV0.3.010.run Creating directory ps.cb.03.010
Verifying archive integrity... All good.
Uncompressing Planeshift Crystal Blue Version 3.010..
./setup.sh: line 57: dialog: command not found
./setup.sh: line 59: dialog: command not found
./setup.sh: line 113: dialog: command not found

Removing tmp files...
root@SpikeIII:/home/dave/Games/Installation Files #

```

Thanks for all the help you're giving by the way :) Much appreciated.

---

### Post by jobezone on 2005-05-31
[QUOTE=Mr_Tickles]I was trying to run an installation package for Planeshift... not sure if it's any good... thought I'd have a go :)
```
file:///home/dave/Games/Installation%20Files/PlaneShift_CBV0.3.010.run
```

Thanks, that stuff worked well :)
However, I got these messages, although this is surely something to do with the program

```
Uncompressing Planeshift Crystal Blue Version 3.010..
./setup.sh: line 57: dialog: command not found
./setup.sh: line 59: dialog: command not found
./setup.sh: line 113: dialog: command not found
```

Therefore i'm guessing this didn't work :(

I'll try the resolution thing now, thanks :)[/QUOTE]
 Iinstall the package dialog which contains the program dialog that it can't find.
> 
sudo apt-get install dialog


---

### Post by meznak on 2005-06-05
[QUOTE=jobezone]Iinstall the package dialog which contains the program dialog that it can't find.[/QUOTE]

apt-get returns:

nate@alcove8:~/Desktop$ sudo apt-get install dialog
Reading package lists... Done
Building dependency tree... Done
Package dialog is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dialog has no installation candidate
nate@alcove8:~/Desktop$

I tried installing dialog from its homepage, but the debian installer claims:

Selecting previously deselected package dialog.
dpkg: regarding dialog_0.9a-20020309a-1_i386.deb containing dialog:
 debconf conflicts with dialog (<< 0.9b-20020814-1)
  dialog (version 0.9a-20020309a-1) is to be installed.
dpkg: error processing dialog_0.9a-20020309a-1_i386.deb (--install):
 conflicting packages - not installing dialog
Errors were encountered while processing:
 dialog_0.9a-20020309a-1_i386.deb

---

### Post by jobezone on 2005-06-06
Dialog is in the "Universe" repository : [http://packages.ubuntu.com/hoary/misc/dialog](http://packages.ubuntu.com/hoary/misc/dialog)

To use Universe, see [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

