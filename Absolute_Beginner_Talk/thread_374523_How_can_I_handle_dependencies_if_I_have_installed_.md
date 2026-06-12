---
title: "How can I handle dependencies if I have installed them by hand?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Songwind on 2007-03-02
I was wondering what the best plan is for dealing with dependency issues if I have installed a program from source.

For example, I installed MPlayer from the packages but it didn't have all the newest codec support (WinAMP video and WMV in specific).  So, I downloaded the source and compiled mplayer, gmplayer, and mencoder that way.  It all works great.

The problem is that some packages require mplayer or mencoder as a prerequisite, and understandably the package manager doesn't know I have them.

Should I install the package then overwrite with "make install" from source?  Or is there a more elegant solution?

---

### Post by PPAAUULL on 2007-03-02
Well if it is one of the latest releases and is not in the repos then the repos might not have the software that you need. They too might also not be the upto date versions. You can always try it anyways though.

---

### Post by Songwind on 2007-03-02
> **PPAAUULL said:**
> Well if it is one of the latest releases and is not in the repos then the repos might not have the software that you need. They too might also not be the upto date versions. You can always try it anyways though.

Right, that's my point.  I wanted the newest version of MPlayer and so I installed it.  Now if I install some multimedia product that relies on it, Synaptic or KPackage don't think they are there.

---

### Post by Zigs on 2007-03-03
For what its worth.  I had the exact same problem when trying to install k9copy.

I fixed it, although I have no idea if this is considered good practice.

  1) I removed the checkinstall package I had made of the mplayer source build.
            sudo dpkg -r <name of mplayer package>

  2) Installed the mencoder package from ubuntu repos
            sudo aptitude install mencoder

  3) Forced the installation of that mplayer source package.
            sudo dpkg -i --force-overwrite <mplayer source deb file>

I checked the status of the mencoder package with  'dpkg -l mencoder' and it appears to be still installed.

I'm guessing that your idea of running 'make install' again would work, but you're right, it's feels too brute force.

---

