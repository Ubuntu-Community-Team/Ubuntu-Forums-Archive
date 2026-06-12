---
title: "new computer"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by mar225 on 2007-01-17
What is the best way to transfer ubuntu from one computer to another. I have a new machine coming and want it exactly like the one I have now. I can't even remember what all is on here but I like it so want the new machine to be exactly the same.

Than You

---

### Post by taurus on 2007-01-17
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by gh0st on 2007-01-17
There's a cool machine imaging tool for Linux called PartImage. It's free and open source. Here's a link to their web site [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

I haven't really had much of a chance to try it out yet but lots of other people on the forums seem to like it. It works like Norton Ghost would on a Windows machine if you've seen that. Sorry I can't give any more detailed help but as I say I haven't really tried it myself yet. I'm sure someone more knowledgeable will be able to help out.

I hope thats of some use but it may be the blind leading the blind a bit sorry :D

---

### Post by gh0st on 2007-01-17
> **taurus said:**
> [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Looks as though someone more knowledgeable beat me to the punch. Thanks for the link Taurus I could do with reading this myself I think :)

---

### Post by mar225 on 2007-01-17
I read about partimage but was led to believe it would only work on a machine with the same hardware. My machine wont be the same hardware (I hope). It makes reference to loading 50 machines with one partimage as long as the hardware is the same ????

---

### Post by taurus on 2007-01-17
What's the spec of your current machine and the spec of the new machine?  It would probably work except you may have to reconfigure X again because of new video card and monitor!

---

### Post by indytim on 2007-01-17
Taurus,

Might there also be a potential problem if they are going from a PATA to SATA HD?

IndyTim

---

### Post by taurus on 2007-01-17
> **indytim said:**
> Taurus,

Might there also be a potential problem if they are going from a PATA to SATA HD?

IndyTim

And that's why I asked for the spec of those two machines.  Regarding harddrives, you just have to modify the kernel and the entries in /etc/fstab.

---

### Post by mar225 on 2007-01-17
Somewhere I thought the specs for part image also required the hard drive to be the same size or it wouldn't reload.  I don't know this for sure because I have done so much reading about ubuntu lately that guides and help files are beginning to overlap. 

The old machine is a P1 with a built in graphics card and no dvd burner. The hard drive is eide 80 gig.
The new machine is a P4 (I stayed away from dual because of problems I read about.) The drive is a SATA and has a dvd burner. 1 gig of ram on new. 256 on old.

A lot of difference if a image file expects to find similar

---

### Post by oilchangeguy on 2007-01-17
are you sure you've got an 80g hd on a P1 machine? unless you've flashed the bios the motherboard probably supports 20g or less.

---

### Post by mar225 on 2007-01-17
You could be right. The drive is 80 gig how much is being used I don't know. I assumed when ubuntu was loaded it took some of the probably unused area of the drive.

---

### Post by oilchangeguy on 2007-01-17
ok, if you've got a smaller hd i'd use that. because there's no way a P1 machine will see all of a drive of that size, no matter what os you use, it's a computer issue not an os issue. enter the bios and it will show the hd size (it sees)

---

### Post by mar225 on 2007-01-17
I really don't care what is on the old machine or how much was in use. I just need to find a way to get the OS from the P1 to the new P4 along with all the goodies on the old machine without having to find and reload them one at a time. I think most any backup program will take care of the home directory and my data but not the OS

---

### Post by oilchangeguy on 2007-01-17
if your new computer already has a hd with an os why not leave that and install the other drive to dual boot? if the new mobo is sata you might have to get a pci ide controller card to hook the old drive to.

---

### Post by mar225 on 2007-01-17
Even if that was the case (new machine is ordered without an OS) the new machine isn't going to look like what the old hard drive has on it for drives and hardware. Looks like the only out is to start over from scratch. Guess thats one plus for windows

---

### Post by oilchangeguy on 2007-01-17
true, i don't know if ubuntu has something like windows found new hardware, if it does then my idea should work.

---

### Post by mar225 on 2007-01-17
I am afraid that when the partimage or putting the old drive in the new machine it will crash as soon as it finds things like a nic card that is different or the amount of ram or a multitude of things that aren't the same. I am looking into a program called ghost4linux or some such. Don't have any details yet but I have convinced myself it would be a mistake to use partimage or just plug the old drive in the new machine.

---

### Post by oilchangeguy on 2007-01-17
i know linux is very different from windows. but maybe as you suggest a fresh install is in order. if nothing else to keep from bringing any un-needed baggage from the old computer to the new one. if you can, write or print your browser bookmarks, installed programs, and backup any documents you need to keep and give that new computer a fresh start instead of a recycled os. i know it's alot of trouble to do a fresh install, but in the end it'll be worth it.

---

### Post by mar225 on 2007-01-17
right now I think a frsh install will be in order. Then take the dvd burner from the new machine to the old one and burn a dvd of the /home directory. Move the bruner to the new machine and use the dvd to load a new /home directory.  LOL Hell I don't know. Just fishing for ideas. The forum gives me ideas and when the time comes I'll probably reload the OS a dozen times but at least the /home will be on a dvd and can be used till I get it right.

---

### Post by oilchangeguy on 2007-01-17
good luck! don't know what version of ubuntu you're using, but i'd use 6.06 because it has a support life of 3 years, whereas 6.10 (a test version) has a support life of around 3 months. see the sticky post on upgrading to edgy.

---

### Post by irish_flu on 2007-01-17
Just FYI (if I read you correctly) I wouldn't do that hard drive move from one machine to another in Windows, either; you're bound to get some registry weirdness.  I don't think that's a bad thing about Windows or Linux, it's just how they're built considering the wide range of hardware they both must support....

---

