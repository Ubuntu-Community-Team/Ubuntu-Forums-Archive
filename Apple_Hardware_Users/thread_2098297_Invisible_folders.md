---
title: "Invisible folders"
date: 2012-12-26
forum: Apple Hardware Users
---

### Post by cheath on 2012-12-26
Hey y'all, got a problem...
My external IOMEGA 2TB HD has been working fine with my UBUNTU 10.04LTS computer for about a year now but today I got an old G4 powerbook running and wanted to get some files from it so I unplugged my 2TB HD from my UBUNTU computer and plugged it into my G4.  When I tried to copy a file from the G4 to the 2TB HD I got a prompt that said the drive wasn't able to copy files to it because I didn't have "permission".  After plugging it back in to my UBUNTU computer I am now unable to see the folders or files names or anything for that matter.  I plugged it back in to the G4 and am able to see the folders on that computer but not on my main UBUNTU computer. I don't need to see them on my old G4 I need to see them on my UBUNTU computer. Any ideas?

---

### Post by Yougo on 2012-12-26
did you umnount, or eject the drive before removing it, or did you just yank the cable out?

do this both on your Ubuntu and your Apple device, reboot both and see if that helped

inproperly removing a drive can confuse the OS about the drive's status, and make it difficult to mount it again
also some operating systems lock the drive. if the OS doesn't get the chance to release the drive before disconnecting, other devices can't acces it.

bottom line: always properly software-eject the drive before disconnecting, especially when using an external drive between more than one computer.

---

### Post by fdrake on 2012-12-26
when you exchange files with a mac the mac tends to change the ownership sometimes. do this and see if the files shows.
```

gksudo nautilus /media

```
browse to the externa drive forlder

---

### Post by Bucky Ball on 2012-12-26
*Thread Moved to **Apple Users***
[I][B]
Reason: [/B][/I]Should improve you chances of getting help here ...


> **fdrake said:**
> when you exchange files with a mac the mac tends to change the ownership sometimes. do this and see if the files shows.
```

gksudo nautilus /media

```browse to the externa drive forlder

All good fdrake, but just wondering if it might chuck the external drive in /mnt in newer releases ... as in:

```

gksudo nautilus /mnt

```;)

---

### Post by cheath on 2012-12-26
Hey Yougo,
Yes, I unmounted the drives properly.  I tried it again and the files are still not visible.  Any other ideas?

---

### Post by Yougo on 2012-12-26
i guess the damage may already has been done. follow fdrake and Bucky Balls suggestions to see if superuser has acces to the drive

---

### Post by iMac71 on 2012-12-26
Since the trouble seems to have happened after you've unplugged the external disk from the Powerbook, you might try install hfsplus on your UBUNTU PC and verify if one or more of their tools are able to solve your problem.

---

### Post by cheath on 2012-12-26
Hey iMac71
I've installed hfs but can't access it. Is it a gui?
thanks

---

### Post by iMac71 on 2012-12-26
> **cheath said:**
> Hey iMac71
I've installed hfs but can't access it. Is it a gui?
thanksno, they're command line tools.

---

