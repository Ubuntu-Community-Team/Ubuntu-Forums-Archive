---
title: "iBook G3 WPA Original Airport - works!"
date: 2010-08-10
forum: Apple Hardware Users
---

### Post by danpwright on 2010-08-10
Dear all,

I read with some interest the work that has gone into getting wireless to work with Ubuntu.  I have had a headache that thanks to jeroen and a little reading myself, I managed to solve and would like to help others that have encountered it.

Those of you with Apple Macs with original (orinoco) airport cards; they connect to WPA/WPA 2 out of the box IF you do the following:

Upon installing Ubuntu 10.0.4, immediately open the terminal and type:

sudo aptitude install wicd

Follow the instructions.  Next, 

sudo aptitude remove network-manager

Follow the instructions.

Next, open up WICD which should be in your applications area, find your network, click properties and enter the password in.  Click connect.

Now, whilst I am mad at myself for not having worked this out earlier, it was through jeroen's excellent IM help and advice last night that made me think.  

We were getting my iBook to work with Linux Mint wirelessly when he noticed I wasn't added to the netdev group.  I twigged that could be why it wasn't working in Ubuntu, so did a fresh install today.  When you install WICD, it adds your username to the netdev group; Gnome's network manager doesn't do it out of the box.

I hope this helps any others who have been having issues.  It certainly helped me; I now have both Linux Mint and Ubuntu running side by side on my iBook (and both through Parallels 5 on my Mac mini).

danpwright

---

### Post by linuxopjemac on 2010-08-10
I am happy that it worked out for you...

---

### Post by danpwright on 2010-08-10
All thanks to you!  However, I don't think I'll be using Ubuntu on the laptop...it is sluggish after using the Debian Lenny Mint installation!

---

### Post by marklogan on 2010-11-03
Hi there...  How would one connect via WEP?

---

