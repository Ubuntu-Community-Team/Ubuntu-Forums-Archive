---
title: "Installation (Partitioning) problems"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Deeper on 2007-10-06
Hi there, I've searched through the forums, found a few posts which come close to helping me, but I need some help :)

After playing with linux/windows only systems I've decided that dual booting will be the best option for me.

Anyway I've been having some problems with partioning my Hard drive for windows and ubuntu,. At current I have XP Pro, in /hda1 (NTFS).

I have been experiencing the problem described here; [http://ubuntuforums.org/showthread.php?t=401656](http://ubuntuforums.org/showthread.php?t=401656)

I tried running Gparted and then went to HDA and set to resize it, giving me 30gb for ubuntu. (Hard disk size = 160GB). I then told it to make a new partician with that space (set to NTFS again).

It managed to resize the first partition, something which the ubuntu live CD installed did not manage to do, however it gave me an error saying it couldnt create a new partition? In GParted i now have:

[IMG]http://img507.imageshack.us/img507/375/screenshotrt6.png[/IMG]


I am completelly lost as to what to do now, I really need the windows installation preserved (i backed up all my documents just in case though).

I am quite new to ubuntu, I tried it a while back, but I'm not too familiar with the way things work :P. Be gentle please, and any help would be greatly appreciated,

Much appreciated,

Deeper.

---

### Post by shae on 2007-10-06
In my experience, if gparted fails the first time when resizeing a NTFS partition, it is not going to work ever.  I would however reccommend that you boot to windows and defragment your harddrive several times.  Then give gparted another shot.  If that does not work, I am not sure what you can do.  Perhaps try a different partition resizer?

---

### Post by Deeper on 2007-10-06
Ahh damn, I was afraid of this. I guess I'll try a different approach, maybe get a second hard drive.

---

### Post by Deeper on 2007-10-06
Good news people.

I managed to seriously break my windows installation (it has now dissapeared lol). Guess I'm ready to take the plunge into linux now.

Deeper.

---

