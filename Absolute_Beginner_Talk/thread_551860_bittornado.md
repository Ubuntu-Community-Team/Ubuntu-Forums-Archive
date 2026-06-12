---
title: "bittornado"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-09-15
hey there everyone just a quick question, i just moved into residence at university and we have unlimited bandwidth on weekend so i wanted to download some movies but!  i open any torrent  and it connects to peers but download and upload rates are zeroooooo!?!?!  i'm guessing it has something to do with our campus internet and my bittornado settings, anyone got any ideas?!?!

Thanks in advance, Alain

---

### Post by skymera on 2007-09-15
i use uTorrent through wine. :D

---

### Post by glotz on 2007-09-15
Have you given it some time? It will always take awhile when it connects to the peers.

---

### Post by S15_88 on 2007-09-15
ya i jus took a shower and it still has nothing, one of them is connected to 12 peers and 10 seeds but still no upload or download rates!  i just don't know wat setting to adjust!  i'm sure it's got something to do with the resnet's settings and stuff but i just don't know wat to cahnge!  

Thanks, Alain

---

### Post by HereInOz on 2007-09-15
If you are using it at a University, I would suggest that you are pretty heavily firewalled and that to get BitTornado to work, you are going to have to do two things.

1. Click on prefs in the BitTornado gui and remove the "randomize" option in the top right corner, and then set a range of, say, 5 ports to use.  Lets say you decide on ports 45673 - 45678.

2. You then go to the network administrators of the University and ask them to forward ports 45673 - 45678 to your computer's IP address.

My feeling is that point 1 is going to be pretty easy, but point 2? A snowball's hope in hell, I would guess, knowing the average university system admin.

If you can't get that port forwarding done, and I doubt you will, then BitTornado will not work properly.

---

