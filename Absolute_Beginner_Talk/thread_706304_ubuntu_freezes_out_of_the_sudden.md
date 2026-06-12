---
title: "ubuntu freezes out of the sudden"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Harisz750 on 2008-02-24
i recently installed Ubuntu 7.10 gutsy 32bit .   eveything seemed right but 2 days now ubuntu freezes and nothing moves.. except mouse. i cannot shout it down, can't open programs, can't do anything. So i have to shut it manually from the cpu button!!!!!!!!  it happens all the time.. i uninstalled automatix2 and amsn due to problems , don't know if this has to do with that....can i fix this??? or have to reformat again???? please help...i am new user and really like ubuntu!!!!

---

### Post by oedha on 2008-02-24
automatix is still not stable yet (as far as i know)
can you open console ? ctrl+alt+f2
sudo apt-get autoremove

---

### Post by aaguilar4 on 2008-02-24
Hey I have the exact same problem, but I have managed to narrow down the cause of my problem.  What happens for me is that Ubuntu will freeze up whenever I am in Firefox and I try to drag something from there to somewhere where I can't drag (i.e. the panel up top).  If I select a piece of text and just as much as try to drag it into another place in the paragraph, I get the same results as you.  I have tried it with different applications, and apparently it is firefox's problem.  Some other people suggested that I install a different browser, but I still haven't done so.  Now that I know what the problem is, I just avoid it (never frozen up since).  
Anyway, try and see what the cause of your problem is, and if it's not what I mentioned, then maybe post that up to see if there's anything that people can help you with.

---

### Post by MyDearWatson on 2008-02-24
I have problems with freezing too... but there doesn't seem to be one cause, it just happens out of the blue.  It's actually less stable than my windows partition at the moment...

---

### Post by chiltonm on 2008-02-25
With me it seems to be whenever I'm playing Gnometris.

---

### Post by MrKlean on 2008-02-25
Try this.... it worked for me ; )

[http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_kernel](http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_kernel)

---

### Post by camlin on 2008-03-02
I am having the same problem. And admittedly it is unlikely to be the machine as I have on it Ubuntu 7.04 (no auto update) and Windows XP and they work fine...

To me the problem seems to have been caused by Friday's update (29th of February) although I am not 100% sure (there was other big updates a few days before). I managed to rollback libnautilus-extension1, libvolume-id0, nautilus and nautilus-data but for some reason Synaptic does not let me rollback udev.

Also, when I try to rollback volumeid it also tries to remove 40 or so packages (with things like linux headers!! :-( )

I will try and see if this already improve things but admittedly if anyone has suggestions on how to rollback do udev and volumeid I am definitivelly interested...

---

### Post by camlin on 2008-03-03
So far I don't have any more freezes since I rollbacked libnautilus-extension1, libvolume-id0, nautilus and nautilus data... I still suspect the problem is more at the "udev" and "volumeid" level but so far it seems that reverting the others (as I can't revert these two) stop them from triggering the fault...

Has anyone encountered a similar issue?

---

### Post by K3l3v on 2008-03-03
I'm having a similar problem (though it seems to be fairly closely tied to running anything that uses the internet).

How did you 'rollback' libnautilus?

---

