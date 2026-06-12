---
title: "Problems Connecting to Internet"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by _python_ on 2007-08-03
Hi all,

Here's the problem: My girlfriend bought a new computer today, and she wanted to get rid of Vista and put Ubuntu on it. Since I have had Ubuntu for a while, I volunteered to help. I successfully installed it (Edgy), however, it did not want to connect to the internet. After some searching and coming up with no results, I simply brought the computer back to my house, where it currently sits. Since I have my other computer here (that is successfully connected to the internet), I decided to take a look and see what was different between the two. It seems that on her computer, when it is hooked up via ethernet cable to a router, there is no option of "wired connection." The wired connection option did not show up on either router (mine is a D-Link while hers is a Linksys). I know my router works fine, as it works with my computer. The modem connection is the only option under Administration > Networking. Additionally, her computer was successfully connected to the internet on her router when she had Vista. I haven't been able to figure out why the wired connection isn't showing up on her computer, so that's where I turn to you guys. Any help would be much appreciated.

Thanks in advance,
Chris

---

### Post by oilchangeguy on 2007-08-03
it appears 6.10 is not seeing your nic card. why not create a live cd of 7.04. run the computer from that, if all is well, install it.

---

### Post by Cypher on 2007-08-03
Open a terminal on her computer and type the following
```

dmesg | grep eth

```
and show us the output..

---

### Post by _python_ on 2007-08-03
> **oilchangeguy said:**
> it appears 6.10 is not seeing your nic card. why not create a live cd of 7.04. run the computer from that, if all is well, install it.

I am currently downloading it, but I figured I might as well try to fix the problem on Edgy if I could.

[quote=Cypher]Open a terminal on her computer and type the following


```
dmesg | grep eth
```

and show us the output..[/quote]

That doesn't give any output. I suppose I'll just try to install 7.04 and see if that helps.

---

