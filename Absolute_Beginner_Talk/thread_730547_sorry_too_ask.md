---
title: "sorry too ask"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2008-03-21
but would anyone like too sit through and help me get my wireless internet working?
i will go as long as it takes, i am determined, just need a good person too help walk me through it

---

### Post by Mustard on 2008-03-21
You could try the Ubuntu IRC support channel, if you are familiar with using IRC.  Doesnt seem to be many volunteers at this stage on the forums. :)

---

### Post by adult swim on 2008-03-21
do you know what wireless card you have?
EDIT: by looking at your other thread i really dont know what else to add

---

### Post by Presto123 on 2008-03-21
You need to post in code tags the output of the following if you don't know what kind of wireless card you have:
```
lspci
```

---

### Post by jan quark on 2008-03-21
Presto is right

some input is necessary so that we have a picture of your current network status.
additionally:

```
sudo lshw -C network
iwconfig
cat /etc/network/interfaces
```

---

### Post by billgoldberg on 2008-03-21
If the wireless card can see the network but can't connect, you can use 

[wicd]("http://wicd.sourceforge.net/download.php")

(download the .Deb file).

You'll have to remove network manager first if you want to use it.

Be sure to have the gutsy cd laying around to reinstall "network manager" if things won't work.

Wicd was the only program that would connect in feisty. In gutsy my laptop connected fine out of the box so I haven't tested it on gutsy, but heared it was ok.

---

### Post by imdano on 2008-03-21
I know from his previous thread that dylon has a driver problem, so wicd won't be able to help him.  His USB wireless card isn't being detected at all by Ubuntu.

---

### Post by dylondadank on 2008-03-21
sorry about not posting back last night!!!! family emergency! 

i have a different question though, when i start my computer, and if i open the boot drive, how do i know if i have windows still on my computer, its not in the grub menu, but my buddy has been switching from ubuntu and windows by using f12 at the start up, or f2, i dont really remember, then he either goes too hard drive or c drive or something, and he can use windows os or ubuntu!

---

### Post by candtalan on 2008-03-21
If you do not see a windows entry in a boot menu then it is possible windows is not there maybe. What can you tell about who installed ubuntu and how, and also about the machine it is installed on?

---

