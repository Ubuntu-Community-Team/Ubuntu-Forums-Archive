---
title: "Samsung YP-Z5 Read Only Problem"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Funky91 on 2008-04-21
I have a Samsung YP-Z5 mp3 player which I have had for a while and have not had problems with it until now.

For some reason it has started mounting as read only. How do I change this.

---

### Post by indiecast on 2008-04-21
i have the YP-T10 and its an MTP only.

are you using MTP or UMS?

---

### Post by Funky91 on 2008-04-29
I have the option with mine and I have it set to UMS Only.

---

### Post by Headly B on 2008-05-09
Hi 

What version of Ubuntu are you using? I have the Samsung T10 which I got working since upgrading to Hardy heron using MTPFS to drag and drop files onto it. However since the release of 8.04 I think that one of the upgrades may have caused a problem.
When I try to access the music or pictures folders on my T10 (using Nautilus) I get this error message:
"Couldn't display "/home/fintan/T10/Music".
Error: Error stating file '/home/fintan/T10/Music': Transport endpoint is not connected
Please select another viewer and try again."
However in the Terminal I can navigate into these directories and copy files to and from them.
I would be interested if your problem has happened in version 8.04...

Headly B

---

### Post by indiecast on 2008-05-11
my T10 was getting this problem sometimes. i just mounted it to a new folder and tried again. i think it happened when i was using it with rhythm box.  make sure ur using only one or the other.  and make sure to mount and unmount ever time you connect and disconnect.

rhythm box has been working pretty good lately since i figured out only to use mtpfs and rhythm box one at a time


ur UMS read only problem is just a matter of permissions. i think ur fstab file has something to do with this. i think you can chmod it too.  look up fstab and chmod in the forums and try messing with them.

---

### Post by Headly B on 2008-05-12
Hi Indiecast

Can you give me any pointers on getting the T10 working with Rhythmbox? I've seen some threads deal with this but talk of recompiling from source etc lose me very quickly!

Headly B

---

