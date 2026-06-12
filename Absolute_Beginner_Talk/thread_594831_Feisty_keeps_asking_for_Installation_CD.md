---
title: "Feisty keeps asking for Installation CD"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by rjmusto on 2007-10-28
Feisty has started asking for the original installation CD everytime I try to install some software.
Doesn't matter whether it's via the Add/Remove apps route or from Terminal apt-get.

Trouble is, I can't find the disk I used for the install anymore.

Why is it asking for this and how do I get round it?

Thanks,
Ralph

---

### Post by taurus on 2007-10-28
Open a terminal and edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the line that has CDROM in it to comment it out.  Save it and then run

```
sudo apt-get update
```

---

### Post by rjmusto on 2007-10-28
Great.  Sorted.

Thanks,
Ralph

---

### Post by mrwelch on 2007-10-28
> **taurus said:**
> Open a terminal and edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the line that has CDROM in it to comment it out.  Save it and then run

```
sudo apt-get update
```

I think this is similiar or a step towards what I am trying to do....

Due to restraints caused by ide cable connectors, and physical room in my server case, I need to remove my cdrom from the system to setup a raid 1 for my data. At some pount I will add a USB optical drive for maintenance.

I have created a folder called '/media/images' to place a copy of the distribution .iso file I installed the system with so that is always available when needed.

So my question is how to mount the image and add it to the sources list so it can always be located?

TIA

Michael

---

### Post by santiagoward2000 on 2007-10-28
Is that caused for installing it using the AlternateCD? I too have the same "problem", but honestly I don't mind. My internet connection is not very fast, so it's faster to get some software from the CD.

---

### Post by mrwelch on 2007-10-28
> **santiagoward2000 said:**
> Is that caused for installing it using the AlternateCD? I too have the same "problem", but honestly I don't mind. My internet connection is not very fast, so it's faster to get some software from the CD.

After removing my cdrom from my system I downloaded mdadm and installed it even though it said Ubuntu had a better version. After rebooting the updater wanted to update it and wanted the installation cd to update it.

I have a fast Internet connection but my thought is not to rely on that 100% since the focus of my system is to be a file server in my home network. 

So I;m basically hanging in limbo until I get this phase worked out.

---

