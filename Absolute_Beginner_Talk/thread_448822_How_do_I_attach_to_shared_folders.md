---
title: "How do I attach to shared folders?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by PhilKE3FL on 2007-05-19
I have a network hard drive which I'd like to be able to access from Linux, if it is possible. The network is not as domain network only a workgroup network.

When I use the "Network" link it finds a "Windows Network" then it finds "esoffice" but then "The folder contents could not be displayed" error message pops up so I don't seem to be able to browse to any available locations.

How would I do this?

---

### Post by Martin on 2007-05-19
Is esoffice the name of the other computer or the name of the folder you are sharing? You may not have shared the folder you wish to access. So while the computer or device is visible the actual resource is not.

---

### Post by PhilKE3FL on 2007-05-25
esoffice is the name of the work group, LKG7BF807 is the name of the network hard drive, Phil is the name of the folder I want access to & which is shared & I have access to it with any & all Windows PCs on the network.

When I try to use Places / Network it can see esoffice but it can not open it to see any of the shared resources, why is that?

I am an experienced Windows Network IT consultant, assume that I at least know what I'm doing in that regard, but I have no clue as to how to share these resources in Linux. Perhaps I can't share windows resources to a Linux box?

Thanks,
Phil K

---

### Post by seetho on 2007-05-25
If the HD you are trying to share sits in a Linux box then you need Samba to make it available to Windows PCs.

---

### Post by PhilKE3FL on 2007-05-25
LKG7BF807 is a network drive, it is NOT in any computer at all. It is attached to the switch via a Network Hard Drive Box, which takes the place of a computer to house the hard drive. You can't possibly tell me you are not familiar with these devices for Windows Networks?

Anyway, thanks I tried browsing again (Places / Network / Windows Network / ...) after I tried connecting a number of different ways & the network had the LKG7BF807 network drive there! After playing with it I was able to figure out how to get the folder to be on the Linux desktop so I can now save files back & forth to a place where all the Windows PCs can pick it up from as well.

I have noticed that Linux crashes from time to time. Sometimes I have access to the Windows Network & when I don't I have to restart the box. Is there a better way to regain access?

Now, how do I make a folder on the Linux box shared for access to the Windows PCs?

---

### Post by PhilKE3FL on 2007-05-28
Thanks for the information about "you need Samba to make it available to Windows PCs." That's what I'll need to do next I guess so I can go the other way.

Now, here's a related problem which may be a bug in Ubuntu?

When I first boot up I can browse to any shared network location, but after some time browsing no longer works. If I have established a connection to a shared resource & left the connection to it on my desktop (in Windows a mapped drive) then I can always get to it.

I have not yet had time to play with it to find out at what point the browse connection is lost, but it seems to be under 5 minutes.

Anyone have any ideas? Is this a bug? Does anyone else have the same problem or is this something site specific? And, if it is site specific, what in the world am I doing wrong?

Phil Karras

---

