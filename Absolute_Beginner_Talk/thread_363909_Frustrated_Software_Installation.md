---
title: "Frustrated: Software Installation"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Starving.Wolf on 2007-02-17
Hi, All --

So asside from not being able to get Windows back on my machine (at all), I'm having some additional issues here.  Mostly they revolve around me trying to install software of any sort.

Everything (and I mean EVERYTHING) I download and try to run has SOME kind of error that happens during the installation.  I have yet to unpack a .tar.gz package and have it work.  ./configure just splashes a whole screen of error messages.  "Make" just sits there and laughs at me.  *.deb files stand there and pick their proverbial noses and say they'll get to it later... or that they're dependant on "libraryX" (which I don't have in any of my adept or package manager files).

Every turn I've made since switching to Linux has required typing hundreds of lines of code (only about 5% of which actually end up doing anything, mind you) and I'm about at the end of my rope.  I feel like my grandfather sitting at my own computer.  All I need to do is start typing with only my index fingers and I'd be all set.

So my question is WTF?!  What the hell is wrong with my system that EVERYTHING I try to install requires some weird 3rd party crap?  First it want's a C compiler, then it wants a DIFFERENT C compiler, and then it wants Python-GNOME something-something (I'm running Kubuntu, by the way, so I don't even HAVE GNOME...) Anything I install wants something on my machine I don't have.  That doesn't seem right to me.

I've been browsing help forums for two weeks, and I get messages like: "How are you so retarded that you can't install Firefox?"  My retort is usually: "If Firefox was that damned easy to install/upgrade, then how come so many people are asking how to do it?"

I need some help here.  Simple, hold-my-hand, explain it like I'm 6 years old kind of help.  Any suggestions?

~ Matt

PS:  What is the "BREAK" message in Adept?  I get that a lot when I try to install extra libraries or codex for AmaroK, or basically anything I'm pretty sure is a dependant for something I'm trying to install...

---

### Post by rosieg on 2007-02-17
Assuming you have a working version of Ubuntu you should be able to install software through Add/Remove Programs or Synaptic. Most stuff is in there, and these apps will automatically sort out dependencies for you and create icons on the correct menus etc. Using these tools is a lot easier than just downloading programs off the internet :-)

---

### Post by Maestro23 on 2007-02-17
Installing in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also might want to look into Automatix(help you install stuff) until you understand things a little better.
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Another good link for getting your feet wet with commands/file structure in linux: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

*Don't get frustrated, hang in there.  Walk before you try to run.

Good luck.

---

### Post by picpak on 2007-02-17
> Assuming you have a working version of Ubuntu you should be able to install software through Add/Remove Programs or Synaptic. Most stuff is in there, and these apps will automatically sort out dependencies for you and create icons on the correct menus etc. Using these tools is a lot easier than just downloading programs off the internet  :)

Yes, I second that! I got all of my most used programs through Applications > Add/Remove.

*edit* No, wait, you're using Kubuntu. However, you can still get it by installing gnome-app-install.

---

### Post by meng on 2007-02-17
Installing from source is just a little harder than installing from repositories. In most instances, it's not even necessary, many users try to install software from source that is already available in repositories. It's tough to break the Windows habit of locating software on the web yourself, downloading and then installing!

---

### Post by nalmeth on 2007-02-17
Follow the installing software links provided by Maestro23

You're probably missing the build-essential package, which is needed for all compilation. If you asked to download additional libs for these apps you're trying to install, search with the package manager for those libraries.

OR, I recommend using the terminal.

apt-cache search sdl

that command will search for packages with sdl in the name
If you're looking for sdl libs, and theres too many results to pick thru, use grep to narrow the results

apt-cache search sdl | grep lib

---

### Post by annda on 2007-02-17
look for help on Adept. the repositories are, well, repositories of pre-compiled programs. get as much as you can from there - the idea is to take care of dependencies among other things. they are for people like you and me, who will compile from source only occasionally or never at all.

post a message regarding your problem with adept and people runnung kubuntu will help you.

good luck!

---

### Post by Starving.Wolf on 2007-02-18
Thanks for the encouragement, everyone!  I think I'm starting to get the hang of things, but it's still a little tough with my limited knowledge of the subject.  Baby steps.... baby steps... slow deep breaths.... baby steps :)

---

### Post by Maestro23 on 2007-02-18
> **Starving.Wolf said:**
> Thanks for the encouragement, everyone!  I think I'm starting to get the hang of things, but it's still a little tough with my limited knowledge of the subject.  [COLOR="Red"]Baby steps.... baby steps... slow deep breaths.... baby steps [/COLOR]:)

"What about Bob?" Great movie:) 

Hang in there man. Good luck.

---

