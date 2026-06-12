---
title: "discontinued?"
date: 2011-06-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by prn on 2011-06-21
Hi Folks,

I'm trying to install something sensible on an Asus Surf 2G for someone. My first thought was the UNR, but I cannot seem to find a current version. I can find the Netbook Remix in version 10.10, but no 11.04.  All the links I seem to find lead me to the general download, but none to the netbook remix. 

Why is that? Has the UNR been discontinued? Am I missing something else? What's up?

Thanks,
Paul

---

### Post by TomAnkcorn on 2011-06-22
ubuntu 11.04 is a one size fits all.
it is pretty much the same as the 10.10 netbook but with loads more functionality and effects.

If your netbook doesnt have the hardware to run the unity shell you can always try adding unity 2d

```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update
sudo apt-get install unity-qt-default-settings
```
(open the terminal and copy paste those in and then select unity qt while logging in)

you probably wont have to do that though if your netbook isn't that old

---

