---
title: "Uninstalling a couple of unwanted apps"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-08-18
Can someone out there help me uninstall a couple of unwanted applications?  In both cases they are programs that I download as .tar files and installed with a command line.  Neither of the programs shows up when I run Applications > Add/Remove.

The first one is called Songbird.

The second one is called Wine-Doors, and came highly recommended from this [source]("http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html").  

Unfortunately Wine-Doors didn't work too well on my system.


Help, anyone?

---

### Post by rich.bradshaw on 2007-08-18
Only things installed using synaptic/apt-get are in Add/Remove - for  other things you can usually just delete them.

How did you install using cli? You can likely just reverse the steps.

---

### Post by rich.bradshaw on 2007-08-18
Wine doors will probably remove using

[SIZE=-1]**sudo dpkg** --[B]remove wine-doors

[/B]Although I have never used it, so this might not work![/SIZE]

---

### Post by nitro_n2o on 2007-08-18
> **Mr. Svinlesha said:**
> 
The second one is called Wine-Doors, and came highly recommended from this [source]("http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html").  

well.. come on it's up to your needs, nothing is highly recommended :)  i personally never heard of wine-doors... anyways, 
if you downloaded the tar ball and did a ./configure; make; sudo make install 
then go to the same directory and if you have your Makefile just type sudo make uninstall this should remove it..  
don't compile from source as long as there is .deb package, this will save u a lot of troubles..

---

### Post by Mr. Svinlesha on 2007-08-18
Hey, **rich.bradshaw**, thanks for the tip.  It seems to have worked.

Unfortunately the command doesn't work for Songbird.  Here are directions for installing Songbird:

> First download the archive say you have downloaded the archive in directory /home/user

Now extract the contents of the archive by using command

tar xzvf Songbird_0_2_5_linux-i686.tar.gz

This would extract songbird in directory /home/user/Songbird however if you would like to extract Songbird in different directory copy the Songbird archive to different directory and use the same command to extract file there.

Now you can run Songbird by going into Songbird directory and typing ./Songbird to launch Songbird music player. I think I pretty much followed the instructions.  Anyway, I have a Songbird folder in my /home/username folder with a bunch of files related to the program and an .exe file (or it's linux equivalent).

I would follow **nitro's** instructions, but unfortunately, I don't speak Ubuntu too good yet...;)  (In other words, I have no idea what he's on about.  Translation, please?)

Finally, even after uninstalling wine-doors I find I have a hidden folder -- .wine-doors -- still hanging out in my /home/username directory.  I have a couple of other similar folders from other programs that I've removed with the Add/Remove command.  What are they, and why don't they go away when I uninstall the programs?

---

### Post by ThrobbingBrain66 on 2007-08-18
The hidden folders contain your settings and preferences for those programs.  If you've unisntalled them and are sure you won't reinstall them, they can be safely deleted.

If you  followed the directions for Songbird exactly, you can just delete it from your /home folder as well.

---

### Post by Mr. Svinlesha on 2007-08-18
Thanks, **Brain**.  I'll try it and see how it works.

---

### Post by Mr. Svinlesha on 2007-08-18
Just a quick shout-out to thank everyone for the help and let you know it all worked out.  Thanks!

I notice a wine-doors folder in my etc folder as well.  Should I just delete it too?

---

### Post by rich.bradshaw on 2007-08-18
basically when you uninstall software it tends to leave settings behind incase you install again - useful usually, but sometimes annoying.

/etc is only full of settings - remember these take up such little space there isn't much point worrying, but they are safe to delete if you aren't using the software anymore...

You will find installing/uninstalling using synaptic much easier in future by the way!

---

### Post by Mr. Svinlesha on 2007-08-18
Gotcha.

Thanks again for all the help!

---

