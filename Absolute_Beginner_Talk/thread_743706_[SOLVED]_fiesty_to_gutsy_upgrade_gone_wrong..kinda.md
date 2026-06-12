---
title: "[SOLVED] fiesty to gutsy upgrade gone wrong..kinda"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by klick.here on 2008-04-02
After some fiddling I got gnome.  Network is broken now.  HAL failed to initiate.  I don't even know who HAL is...seems to be working for the most part.  I did this upgrade before without any need to think too much.  Also I could use some help learning to share folders between multiple Linux computers and at least one micro$oft.  I had it working at one time but I have changed the network setup to make it work how it should and thefore also in Linux...trying to learn IRC after not touching it for probabally a decade.  Thank You:guitar:

---

### Post by foxbuntu on 2008-04-03
This could be a really tough one, did you try upgrade via "apt-get dist-upgrade"? If so, if it failed at any one point the kernel could be broke or just HAL, however you could spend tons of time fixing HAL and still have issues. (BTW: HAL = Hardware Abstraction Layer). I would suggest backing everything up that needs to be and reload the machine will save you hours of frustration. For future reference, a much easier way (and safer) to upgrade between release versions:

```
sudo update-manager -c -d
```

As far as sharing folders goes, it should be pretty easy when you get Hardy ready to go again, you will be able to right click folders to share them from one machine to the next, for additional information on sharing start out googling for Samba and NFS. If you get stuck in with the wikis or documentation on either you can post more specifc questions in the forums to get better help.

---

### Post by klick.here on 2008-04-05
I just reinstalled it from a 7.10 cd i had and it's working fine.  i was mainly just using it to teach me about ubuntu and running gcompris for my four year old.  He really likes penguins now and so do I.  btw how do i mark as solved?

---

### Post by Michael.Godawski on 2008-04-05
Use the Thread Tools to mark a Thread as solved: Upper right section.

---

