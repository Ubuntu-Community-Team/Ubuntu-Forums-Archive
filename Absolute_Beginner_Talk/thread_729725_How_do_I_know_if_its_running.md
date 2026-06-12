---
title: "How do I know if its running?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-20
I have checked that clamd is an on-access scanner for Clam. So I do this:

```
sudo clamd
```

And I return back to the prompt, assuming that clamd has starter in background. It doesnt show up in "top", so how do I check whether it is running?

---

### Post by kpkeerthi on 2008-03-20
```
ps aux | grep clamd
```

You may want to add sudo to the command

---

### Post by sayakb on 2008-03-20
Does this mean it's running? How do I test it?

```
glade@Muzic-Jukebox:~$ ps aux | grep clamd
clamav    7421  0.5  5.3  79544 54892 ?        Ss   16:37   0:01 clamd
glade     8703  0.0  0.0   5120   808 pts/0    S+   16:43   0:00 grep clamd
glade@Muzic-Jukebox:~$ 

```

---

### Post by kpkeerthi on 2008-03-20
> Does this mean it's running?
Yes it is running with the process id **7421**. 
> How do I test it?
I'm sorry. I don't use any antivirus.

---

### Post by sayakb on 2008-03-20
Thnx for the help.. :)

---

### Post by seshomaru samma on 2008-03-20
> **LinuxIsInnovation said:**
> Does this mean it's running? How do I test it?



there is some information here: [http://www.clamav.org/doc/latest/html/](http://www.clamav.org/doc/latest/html/)

---

### Post by billgoldberg on 2008-03-20
You do know that clamav only scans for windows viruses, do you?

So it's only usefull if you share allot of files with windows computer (like on a network).

If don't care about other windows pc's on the network or you don't share with windows pc's, then there is no reason whatsoever to install it. 

It just going to make the pc slower.

There aren't any linux viruses in the wild, and if there is going to one, clamav isn't going to stop it.

Just to make things clear.

edit:
(I didn't read the OP very well, it says clamd, not clamav, it could be the same program, if it's not, I just made a fool out off myself)

---

### Post by forrestcupp on 2008-03-20
You can also use the System Monitor and click the Processes tab.

Sysem->Administration->System Monitor

---

### Post by sayakb on 2008-03-20
So basically clamd is a command line tool and doesn't provide on access protection?

---

### Post by sayakb on 2008-03-20
> **billgoldberg said:**
> You do know that clamav only scans for windows viruses, do you?

So it's only usefull if you share allot of files with windows computer (like on a network).

If don't care about other windows pc's on the network or you don't share with windows pc's, then there is no reason whatsoever to install it. 

It just going to make the pc slower.

There aren't any linux viruses in the wild, and if there is going to one, clamav isn't going to stop it.

Just to make things clear.

Speed has been affected in my case.. I already have avast installed, what I dont like is that each time I update it, it downloads a 18MB file.. anyway, I think I should remove clam. How do I ensure that it has been completely removed?

---

### Post by billgoldberg on 2008-03-20
Searching for it in synaptic, right clicking it and choosing "mark for complete removal" and then pressing apply.

---

### Post by sayakb on 2008-03-20
That is okay.. I just installed everything I found related to Clam.. from the net, I compiled tarballs, etc. Btw, I've removed the clam packages already. But I would keep avast, in case..

---

