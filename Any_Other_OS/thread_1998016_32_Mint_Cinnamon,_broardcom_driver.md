---
title: "32 Mint Cinnamon, broardcom driver"
date: 2012-06-06
forum: Any Other OS
---

### Post by penguinslide on 2012-06-06
Hi I'm trying to install 32 bit Mint cinnamon on girlfriends Compaq Presario 3000v, the wireless card broardcom driver (4311 I think) just flatly refuses to work, have even been installing other distros in a desperate attempt to get it going, vector linux shipped with it, but couldn't work out how to install it.

Have also been trying commands off this forum to get it going, so far no success, perhaps because Cinnamon is debian? I'm not sure. 

Previously had ubuntu 8.something installed on her laptop, she got sick of the slow speed, constant shaded windows. I can't remember having any driver trouble with ubuntu 8.something. Updates stuff up all installation efforts, it's been an extremely frustrating 4 days!!

So what I am asking is: 

Is there a (or series of) terminal command(s) to install the driver in Cinnamon without dragging along any other updates?

---

### Post by penguinslide on 2012-06-06
ok, followed instruction on this thread:

[http://ubuntuforums.org/showthread.php?t=1997880&highlight=broardcom+4311](http://ubuntuforums.org/showthread.php?t=1997880&highlight=broardcom+4311)

So I have the wireless card responding, but there seems to be a software issue, 2 windows keep asking me for the network password, neither are connecting me

sudo apt-get remove --purge bcmwl-kernel-source

Did not remove anything, it said not found.

---

### Post by penguinslide on 2012-06-07
Ok, found this thread and tried it on a fresh install and it worked, 

 [http://ubuntuforums.org/showthread.php?t=1982932&highlight=bcm+4311](http://ubuntuforums.org/showthread.php?t=1982932&highlight=bcm+4311)

I have to say I'm more than a little surprised by the lack of response from this forum, usually a very reliable team.

---

