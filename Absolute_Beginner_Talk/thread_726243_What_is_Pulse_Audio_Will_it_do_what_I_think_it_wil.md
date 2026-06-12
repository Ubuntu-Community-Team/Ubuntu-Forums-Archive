---
title: "What is Pulse Audio? Will it do what I think it will?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-03-16
I am curious about [Pulse Audio]("http://pulseaudio.org/"), and I've done some googling on it but all of the information I've discovered is way over my Newb Head...

[LIST=1]
[*]Can someone explain what it does in layman's newb terms?
[*]I run multiple VM's on my Ubuntu Box, will Pulse Audio allow all my VM's to use the same sound device at the same time? Currently, I can only allow one of my VM's to use the sound device at a time, would Pulse Audio allow them to share?
[*]I heard this is going to be standard in the next Ubuntu Release Hardy 8.04, is this true? Should I just wait for that before I jump ahead and install it?
[/LIST]

TIA,
-BassKozz

---

### Post by durand on 2008-03-16
1. Pulseaudio is a sound server and it basically allows sounds that applications pass to it to be modified, played around with and moved to different sound cards and computers on a network. Not all programs support it at the moment but many do..The biggest problem is probably ALSA support which is effectively another sound server and it takes control over the sound card, like pulse audio would.

2. Not so sure about this...It might depend on the VM because you could install pulse audio into the VMs and then transfer sounds over the network to your host computer.

3. It's already in Hardy at the moment and should be stable when hardy's released. It mostly works but there are slight glitches.

Since hardy is coming out in a month, you may as well wait and get it with that since its a lot easier than manual setup.

---

### Post by logos34 on 2008-03-17
Here's a thread I found interesting:
[http://ubuntuforums.org/showthread.php?t=599334&highlight=talk+pulseaudio](http://ubuntuforums.org/showthread.php?t=599334&highlight=talk+pulseaudio)

---

