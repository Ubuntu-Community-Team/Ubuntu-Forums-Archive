---
title: "I set up two partitions in Samba. The network finds one, but not the other."
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by genekrupa on 2006-10-15
I used the howto set up samba peer to peer ([http://www.ubuntuforums.org/showthread.php?t=202605&highlight=howto+samba](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=howto+samba)) to make two harddisks in on my Ubuntu-machine accessible in my home-network.

The respective sections in smb.conf look like this:

[disk2]
    path = /media/disk2
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = gamleoern
    force group = gamleoern

[photodisk]
    path = /media/photodisk
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = gamleoern
    force group = gamleoern

Now the other machines on the network, one running Windows and the other one running OSX, find disk2 (which is really nice, thanks Stormbringer), but they don't find photodisk. They show me something sure enough, but the contents of photodisk are not on it.

In terms of hardware, disk2 is a disk of 10 gb, and in Nautilus it appears as a harddisk, while photodisk is a partition of 37 gb on a third disk and appears as a folder. 

I have run the chmod 0777 /media/photodisk about 100 times, to make sure that that is not the problem. 

Actually, for a moment I had access to photodisk; At first i misunderstood the howto and had created a section in smb.conf going like this:

[MyFiles]
    path = /media/disk2
    path = /media/photodisk
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = gamleoern
    force group = gamleoern

When I then added the two sections above, I had the contents of photodisk under the name of MyFiles in the network, whilst photodisk also was shown in the network, but I could not see any the content. But this was kind of messy, so I took out the MyFiles section - and photodisk disappeared.

What am I doing wrong?

---

### Post by genekrupa on 2006-10-15
I found the problem: I tried to make a shortcut to media/photodisk on my desktop. Somehow, this shortcut turned out to be another folder by the same name... ](*,) This is embarrassing...

---

