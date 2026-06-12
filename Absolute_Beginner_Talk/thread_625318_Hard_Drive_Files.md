---
title: "Hard Drive Files"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by WierdKid on 2007-11-27
I'm getting ready to install Ubuntu on my AMD64. It is currently set up with 2 HDD. A 40gig with XP Pro 64, and an 80gig that I use to store my music and other files. I would like to not lose 30 gigs of music by installing Ubuntu. When installing, I know I can keep the install from affecting the large hdd, but once its installed, how do I get ubuntu to read my music on the other HDD?

---

### Post by siciliancasanova on 2007-11-27
If you're not planning to dual boot I would recommend installing Ubuntu and the /home folder on the 40 gig.

What type of partition is the 80gig?

---

### Post by OldTimeTech on 2007-11-27
Actually, you might be better off taking out the hard drive you don't want Ubuntu to load on and then replace after loading Ubuntu....that way you'll have the dual boot on the small drive.

---

### Post by WierdKid on 2007-11-27
I'm not planning on Dual Booting. But if I install on the 40, without the 80 plugged in. Then after ubuntu is installed and running, plug the 80 in, it should have the files.

---

### Post by OldTimeTech on 2007-11-27
if you have the 80 in ntfs, you'll need to load the ntfs-g3 which is in Synaptic Package Manager.

otherwise yes...you'll have the files cause they won't have been written over or deleted when installing ubuntu

---

### Post by WierdKid on 2007-11-27
Do i do that before or after i install ubuntu, and if its after ubuntu, does that come before or after i plug the drive in

---

### Post by OldTimeTech on 2007-11-27
after the install and before you plug the drive in

---

### Post by WierdKid on 2007-11-27
And that will let me keep and access the old files?

---

### Post by exactopposite on 2007-11-27
> **OldTimeTech said:**
> if you have the 80 in ntfs, you'll need to load the ntfs-g3 which is in Synaptic Package Manager.

otherwise yes...you'll have the files cause they won't have been written over or deleted when installing ubuntu


i might be wrong but i think gutsy comes with this built in

---

### Post by OldTimeTech on 2007-11-27
Well don't tie me down to an answer.....but everything I've read, here in forums and other places and according to my "hacks book"....yes!

---

### Post by OldTimeTech on 2007-11-27
> **exactopposite said:**
> i might be wrong but i think gutsy comes with this built in

I said use synaptic package manager

---

### Post by WierdKid on 2007-11-27
Sweet sweet. I guess thats what I'm doing this weekend.

---

### Post by OldTimeTech on 2007-11-27
Let me know how it goes....I'm in and out of the forums ;)

---

### Post by WierdKid on 2007-11-29
Turns out the version of Ubuntu i have already had the driver on it. I installed Ubuntu, got it all set up how I want it, turned the comp off, pluged my 80 gig in, And when I turned the thing back on, I have all my music, I updated all my codecs and all my files play flawlessly.

I don't see how people complain about Ubuntu, Its so awesome.

---

### Post by exactopposite on 2007-11-29
> **OldTimeTech said:**
> I said use synaptic package manager

i see what you said. What I was saying was that i think ntfs3g is part of the standard gutsy install which means there would be no need to install it via synaptic.

---

