---
title: "Nvidia and IDE"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by gavd6968 on 2007-08-14
Hello all!  I'm new to Ubuntu and Linux and I would appreciate some help in two areas.

First, I have an Nvidia GeForce 7300 GT with 512 MB, it is an AGP card.  When I use the restricted driver X locks at 800x600.  When I try to install the Linux driver from Nvidia it says that I don't have the header files.  What do I do?  (This is actually related to my next question)

Second, I am learning C++ using Visual Studio, but my main goal is to learn C/C++ in Linux, and I was wondering what would be a nice IDE to install?  I have heard that Glade is excellent for Gnome, KDE has an excellent IDE (I don't recall the name at the moment) and Netbeans is supposed to be good as well.    What I would like to know is what packages would I need to get with synaptic for programming and object oriented programming?  Hopefully it will be a small list and synaptic will handle the dependencies without problems.  Also, what are the recommended packags for buiding 3D games?

Thanks all!

---

### Post by BaffledMollusc on 2007-08-14
> **gavd6968 said:**
> Hello all!  I'm new to Ubuntu and Linux and I would appreciate some help in two areas.

First, I have an Nvidia GeForce 7300 GT with 512 MB, it is an AGP card.  When I use the restricted driver X locks at 800x600.  When I try to install the Linux driver from Nvidia it says that I don't have the header files.  What do I do?  (This is actually related to my next question)

Are you downloading and trying to install the driver yourself? Wouldn't it be far easier just to use Synaptic (System->Administration->Synaptic Package Manager), which would only take a couple of clicks?
> 
Second, I am learning C++ using Visual Studio, but my main goal is to learn C/C++ in Linux, and I was wondering what would be a nice IDE to install?  I have heard that Glade is excellent for Gnome, KDE has an excellent IDE (I don't recall the name at the moment) and Netbeans is supposed to be good as well.    What I would like to know is what packages would I need to get with synaptic for programming and object oriented programming?  Hopefully it will be a small list and synaptic will handle the dependencies without problems.

I use KDevelop, which is the KDE IDE you mentioned. I think if you install that it should pull down everything you need to build/compile software. I think.
> 
Also, what are the recommended packags for buiding 3D games?

I use OGRE, which is an open source rendering engine. It's cross-platform and extremely comprehensive. I believe there are packages in the repositories for it, but I've always found them a bit outdated. Downloading the source from the OGRE homepage and compiling it better in my opinion because you get the lastest build and you also get all the additional demos, media files and whatnot.

---

### Post by Hospadar on 2007-08-14
You might also want to look into eclipse-cdt for your IDE.  If you do use it, I would download eclipse and cdt from the eclipse websites, they have more recent versions than the repo and they work a little better.

As for configuring your video card, i would recommend "envy" you can install it through synaptic and then run it on the command line.  It's a very complete tool for installing video drivers

---

### Post by gavd6968 on 2007-08-14
Hi.  I'll try using Synaptic again.  Maybe I overlooked something.  But I've tried Synaptic and the stock restricted drivers and that's what sent me to Nvidia.

---

### Post by gavd6968 on 2007-08-16
Nvidia is all straight now.  I found and used Envy and it's a GREAT script!  Now its Netbeans that's posing one last problem.  Here's the link to my current puzzle.

[http://ubuntuforums.org/showthread.php?p=3198727#post3198727]("http://ubuntuforums.org/showthread.php?p=3198727#post3198727")

---

### Post by Inxsible on 2007-08-16
I would give Eclipse a whirl. I use it everyday and I love it.

---

