---
title: "running ubuntu on com w/o data storage drive"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by minibeardeath on 2008-02-27
let me preface this with the following statement: my only experience w/ any linux is using an ubuntu live cd to access data files on broken windows machines.

as part of a school project i am planning on building a computer w/ parts donated from ppl i know. one of the project requirements is that the project must represent a genuine challenge, and building a computer is hardly a challenge (for me anyway). in order to make the project challenging to me, my project mentor has suggested that i attempt to build the computer w/o any sort of data drive (i.e. hdd, ssd, flash drive...). as mentioned in the preface, i have basicly zero experience w/ linux (also i have 0 experience w/ command promt (windows or linux)). does anybody have any ideas as to where i should start? also, after completed, i plan to run folding@home on the computer, so i would need to be able to boot that program from the cd/dvd. this computer will not be used for anything other than folding@home, so i do not need any sort of productivity apps on the disc. 

sorry i cannot post any of the specs for the computer because i am still acquiring them.
any help would be much appreciated.

ps i do have a computer w/ ubuntu installed on it, so i do have a method of creating the personalized disc myself.

---

### Post by bollix47 on 2008-02-27
You could give [notfred's folding CD]("http://reilly.homeip.net/folding/") a try.

---

### Post by dstew on 2008-02-27
It seems you want to run a diskless workstation. See[ this HowTo]("https://help.ubuntu.com/community/DisklessUbuntuHowto"). You need a PXE-enabled BIOS on your motherboard to do this. Look in your BIOS settings to see if it has a Network boot option. If it does, you can make it a diskless workstation.

There are two types of diskless workstations. One is a thin client, which really acts as a remote terminal. The whole operating system remains in the server. The other type runs the operating system and other applications inside the client memory, and uses the server only for storage.

---

### Post by minibeardeath on 2008-02-27
is it possible to run the diskless ubuntu without a server? (i do not have a comp @ home that is always on that cud serve as the server, and i do not want to put the machine on the school's server, or even leave it at school for that matter)

---

### Post by dstew on 2008-02-27
Well, at a minimum you will have to get the kernel into it from somewhere. If you have no local disk storage, it has to come from some remote storage, which is another way of saying a server. Maybe you can do a network boot from an internet site instead of a local server.

---

