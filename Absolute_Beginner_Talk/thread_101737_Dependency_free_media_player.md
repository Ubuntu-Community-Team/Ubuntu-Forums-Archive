---
title: "Dependency free media player?"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Evilchicken on 2005-12-10
Is there any media playing programs (mainly for mp3, mpeg, avi and wav) that doesnt have any dependencies or has what it needs with it? My ethernet card on my ubuntu machine is dead and Im getting a wireless router in a few weeks but don't want to wait that long to be able to listen to my music.

I downloaded realplayer and actually installed it (Woo!) but unfrotuanetly doesnt open. Have no idea why but it wont. It acts liek its opening the outline of a window pops up but quickly disappears adn then nothing happens.

Hmm while im at it might as well get my last few questions out. Can any media players play .wmv files? Will anyone write a tutorial to install XMMS without an internet connection? Including all of its dependencies, how to compile bla bla bla. Why is installing stuff without an internet connection so damn hard :( ?

Well thanks for your wonderful help this past week everyone and I look forward to more of my noobish questions and your quick and helpful support.

---

### Post by Ted D. on 2005-12-10
Hi,
Try XMM. It can be installed via Applications -add applications (more programs)
Ted D.

---

### Post by ssam on 2005-12-10
i assume you can download files on another computer and copy them onto your ubuntu computer.

all the ubuntu packages can be downloaded from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

if you get:
gstreamer0.8-mad
libmad0

and copy them to a folder called "debs" in your home folder. then open a terminal and type
```
cd debs
```
type
```
ls
```
to list whats in the folder.

to install a deb you type
```
sudo dpkg -i packagename.deb
```
replacing packagename.deb, with the names listed.

(tip, if you type the first few letters and then press tab it should expand to the full name).

if you get dependancy errors, you will need to go back to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and find those packages. it should not take more than few trips.

that should give you mp3 support in rhythmbox.

for video you might need
xine-ui
libxine1c2
ffmpeg

---

### Post by Estariel on 2005-12-10
Edit: ignore the following, ssam's guide is much better (and leads to the same result)
xine will do everything you want.
you will have to control it from the command line though, as long as you don't get something like xine-ui to control it.

xine will work on its own, xine-ui is a graphical interface (which of course depends on xine).

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=Evilchicken]Why is installing stuff without an internet connection so damn hard :( ?[/QUOTE]
Essentially because most package managers rely on a repository to have all the files and dependencies organized.  You can have repositories set up as filesystems or cdroms.

What would probably make a really good project would be a program (maybe something web based?) that would be like apt-get, but instead of installing the software for you, you would just get a big tarball of packages that could be imported into a local repository (burned to a CD or copied to a filesystem repository).  Then you could essentially download the stuff you needed on a friend's computer and import/install on your own.  That would be great for things like downloading NIC drivers, where you currently run into a chicken and egg kind of problem.

---

### Post by gord on 2005-12-10
if you can get a copy of wine running, you could use [winamp (lite version)](http://www.winamp.com)

---

### Post by Evilchicken on 2005-12-11
Thank you guys! I will try what you said ssam. 

See I have a PC downstairs with an internet connection (family computer) and then my ubuntu machine in my room. The NIC in my ubuntu computer is currently dead and im not going to bother replacing it since im going to get a wireless card soon (hopefully). SO i've just been downloading from this computer too my flash drive and then copying all the files to my /home folder upstairs.

Well thanks I'll let you know of my progress :D

---

