---
title: "Tried to fix &quot;boot sector backup&quot; problem - I broke it!"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by littlesir on 2006-10-15
Ok, so I went to [http://www.cs.cornell.edu/~djm/ubuntu/#fix-vfat-mount](http://www.cs.cornell.edu/~djm/ubuntu/#fix-vfat-mount) and followed the instructions to get rid of the message "there are differences between the boot sector and its backup". Only it didn't work, probably because I changed the wrong bit.

Note: I really am a noob. I know pretty much nothing about Ubuntu, command lines, programming or anything of the sort (I'm trying to learn, but everything seems to have a certain amount of assumed knowledge - I had to ask a friend "so where do I put this "sudo gedit..." stuff)

Anyway, so I did a very silly thing and went and changed the "vfat defaults,utf8,umask=007,gid=46 0 1" lines on all four partitions there, thinking that would work.

Now it won't load the graphical interface when I start up, and all I can get is the command line stuff.

So how do I change it all back? All I want to do now is set those four lines back to what they were when it was giving me the error message. I figure that message at startup is better than not being able to start up.

Any help would be greatly appreciated.

---

