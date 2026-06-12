---
title: "The more you break it the more you learn (Updates)"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by grimmson on 2005-10-04
Hello all. Had an interesting thing happen. Installed 5.04, downloaded 50 mb +/- of updates and wanted to install nvidia 7667 drivers. Followed the steps and glx gears went from 250 to 1900. Damn was I happy. I currently have three weeks of install / upgrade /debug experiance and I'm getting better. Things were great. I tried to install the remaining 75 mb of updates and things took a curve. Update manager said it had problems downloading a few packages,"Would I like to procede?" I'm big on progress, of course I wan't to procede. Oops. Upon restart xserver failed. I tried reinstalling nvidia drivers following both n00b guide and sudo sh, sudo nano and things didn't go well. I ended up reconfiging xorg with nv and that restored the desktop "kind of." It was long drawn out and choppy so I cant remember a lot of detail. With a gui I wanted to continue updating to hopefully iron out the problem but networking was down (no internet.) I think the problem was Loopback interface (not sure.) Dead in the water and a little drained I opted for a reinstall. I tried downloading   updates but came up with the same problem "missing packages." I did not proceide to ask questions first.
1) can I download all updates and burn to cd because I'll probably kill the system again?
2) can I "unzip" the 5.04 install cd and update the install cd with all updates for a one disk "clean" up to date install cd? (I'll need it)
3) when downloading updates should I do a few at a time and not proceide when packets (dependancies?) are missing?
4) Is it assumeable that xserver (and other system things) became unstable when I installed some packets but their dependancies failed to download or the nvidia kernal (i forget the term I saw) didn't mesh whith the updates?
5) How often will I have to reinstall nvidia drivers and what are the proper steps to do so? I think ati's need a "sudo modprobe -r fglrx" to remove the fglrx driver.

Sorry for the string of questions. I'm just tired of bugering up my system ,reinstalling and downloading 166 mb of updates just to watch it crash again. Thanks

---

### Post by Mustard on 2005-10-04
What I've done is set up /home, /usr as seperate partitions and when I want to reinstall I don't install over those.  I've also told synaptic never to delete any packages I download.   I'm pretty sure this is going to work when I try it out.

There are a number of HOW-To's on setting up local repositories.  I just haven't had the patience to go through them all.

The best thing I discovered though, which is really useful is the progam mondo, which is an emergency system recovery tool.  It can take a backup of your running system, and you can save it to CD/DVD and use it to restore your system to the state it was in at the time of the backup.  Using this I try to get my system to an optimal state, and before I start experimenting too much, I use mondo to take a backup of that state giving me a good launching point for the next time I break Ubuntu.

---

