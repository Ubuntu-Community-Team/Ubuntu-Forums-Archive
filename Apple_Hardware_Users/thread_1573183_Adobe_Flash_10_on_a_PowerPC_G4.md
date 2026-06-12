---
title: "Adobe Flash 10 on a PowerPC G4"
date: 2010-09-12
forum: Apple Hardware Users
---

### Post by tucktheproducer on 2010-09-12
I know that I'm in search of a bit of a Holy Grail, but I'm hoping someone will have a suggestion that will help me with a solution for this sticky issue.

I recently dug my old iBook G4 out of mothballs, needing a nice, portable machine while I'm saving up to replace my dead desktop.  I tried out several versions of OSX on the thing, and none would work without slowing the machine down to speeds rivaled by Boston winter molasses.  So, my progress was clear - upgrade the system to Ubuntu.

I've installed 10.04 on the Mac (thank you community for such a lovely distro!), and the system is working faster than I remember it working when it was an MacOS machine.  This change over has been nearly perfect for this machine.

There is a single caveat:  There is not a version of the Flash 10 plugin available for a PowerPC.  

Is there anywhere, or anyone, that I could be searching for to allow this machine to have Flash 10?  I have several projects that I monitor online that are Flash based, and not having Flash would curtail my ability to use my "uBook" to its full potential.  I fear that this is a "no longer supported - get a new machine" sort of situation, but there's no reason not to try, and to dream.

Thank you all - I look forward, with hope, to hearing your thoughts and solutions.

---

### Post by jackhe22 on 2010-09-12
Hello!

Welcome to the Apple-Ubuntu community!

First of all, I've done some research and it seems you can just install the normal Flash Plugin through firefox, but it will cause choppy playback. You can fix it by disabling Flash Hardware Support. (Right click on any Flash Based object, select Preferences.)

---

### Post by tucktheproducer on 2010-09-12
@jackhe22 - Thank you for the warm welcome.  It's a pleasure to be here, and not looking on from the sidelines any longer.

On the question of my problem, I'm afraid that I've tried installing the plugin through the regular Firefox methods, and I come up against several roadblocks.  Everything that stalls me out seems to indicate that Flash 10 isn't prepared to see my PowerPC G4 processor, and can't work with it.  

Using the pulldown at the "Download Flash Player" site, I have several options I can run.  These are the results:
 
- If I select the ".deb for Ubuntu 8.04+" I get an error from Package Installer telling me the file has "[the] Wrong architecture 'i386.'"  

- If I try to use the "APT for Ubuntu 9.04+" and after approving the additional software channel, I receive a message telling me "Package 'adobe-flashplugin' is virtual."  I then get no other info, and Firefox doesn't get its plugin. 

-  All the other packaged options (YUM for Linux, .tar.gz for Linux and .rpm for Linux) has similar problems, as well as being less friendly for me, as a beginner, to try and run.

It would seem, from what I can tell, that I need to find a version of Flash that dosen't balk at me not having an Intel.  Does such a package exist?  If so, where can I find it?

---

### Post by linuxopjemac on 2010-09-13
To make it very clear for you: there is no Adobe flash player for Linux/PPC. Wait for Lightspark to be ported to PowerPC. It will come in the near future.

[http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users](http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users)

---

### Post by MegaLoler on 2010-09-13
Adobe does not have a ppc ubuntu port of their flash plugin.  there are a few open source alternatives, but they dont work that well.  I use gnash.  it works alright for some things, for most it doesnt though . for youtube videos, see [http://ubuntuforums.org/showthread.php?t=951546&page=2](http://ubuntuforums.org/showthread.php?t=951546&page=2)  and scroll down to my reply.  Or you can use minitube.  I've never tried it though, so I dot know what minitube is like.

---

