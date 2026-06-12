---
title: "Have you gotten beryl working on MBP?"
date: 2007-04-23
forum: Apple Intel Users
---

### Post by rscow on 2007-04-23
Hi, I am fishing for feedback and help getting Beryl up and running. I have a 2.0GHz MPB.  I have a triple boot setup with Vista, Mac OSX, and Feisty.  

Feisty I set up with GRUB installed during OS install, using the debian version of REfiT.  I managed to get gdm up installing the fglrx driver.  

I went along and followed the instructions in a HOWTO to get Beryl installed.  Aptitude was used, and beryl, beryl-manager, emerald, etc., are all installed.  I have beryl and beryl-manager as startup apps in Sessions.  

When I startup and select an accelerated session, I get a hashmarked screen, followed by an ubuntu splash, and then a blue screen with white borders top and bottom, then the brown ubuntu desktop.  I can log out of this, but not shutdown or restart.  If I control-alt-delete and then restart X as a gnome session, all is well.  

I don't get a beryl icon on the top of the desktop.  I can't control beryl-manager.  

I get an appropriate output when I run fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)

So, any guidance specifically toward the MBP would be greatly appreciated.  URLs, links, sea stories, whatever.

Thanks,

Roger

---

### Post by ronocdh on 2007-04-23
I followed [this guide]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") and was able to get the awesome flippycube we all lust after, but effects like Rain didn't work. Then I broke it all to pieces, and the next time I tried it I got the "white screen of death" that plagues us ATI users.

So, give it a shot. I've since wiped and reinstalled Feisty, questing after wireless--as yet, to no avail. Once that's down I'll give beryl another go. Crucial point is that the Beryl in the universe repos does not work for our cards...

---

### Post by Greywhind on 2007-04-23
You should note that if you're trying to use ATI cards with Beryl, you can't use AIGLX. You have to use XGL. This is because the ATI fgrlx drivers don't support the "composite" feature, which is required for AIGLX.

You probably already know this, but it is very important, so I just thought I'd mention it.

---

### Post by stickboy3k on 2007-04-23
The best how to that I've found for this is located here: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

The important part for me was to downgrade to 0.2.0 and exclude the newer versions from updating. Then I renamed the beryl executable to beryl-old and copies beryl-xgl to beryl. That caused beryl-manager to open beryl-xgl instead of beryl (which would try using aiglx and fail).

---

