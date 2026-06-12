---
title: "How to check available HDD space?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by showty on 2007-03-16
Hey

Sorry for the really newb question, but how do I check how much HDD space I have left on my Linux partition?

And also, how can I resize partitions (ehh, take more space away from my Windows partition and give it to Ubuntu, I've outgrown it ;) )

---

### Post by AtrejuT on 2007-03-16
you can resize partitions using gparted which is in the repositories, so it can easily be installed through synaptic. It also shows you how much space is occupied

atreju

---

### Post by aysiu on 2007-03-16
If you want a really quick overview, [the terminal](http://www.psychocats.net/ubuntu/terminal) command ```
df -h
``` will show you how much space you have left on each partition.

If you want a more comprehensive view, install and use *filelight*. You won't regret it. I've attached an image of FileLight in action.

For the Windows partition you're ditching, install and using GParted to delete it: ```
sudo apt-get update
sudo apt-get install gksu gparted ntfsprogs
gksudo gparted
``` Then you can mount it within Ubuntu by following these instructions:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by showty on 2007-03-16
Oh.. damn

I set up Ubuntu on an logical partition, as I had 3 primary partitions to begin with already (System with Windows and apps, Games with.. games and Files with files).

Ubuntu is then installed on 8gb of the 10gb (as an extended partition) and ive got a 2gb swap.

Nothing I can do then eh? I was actually planning on giving Ubuntu my whole 120gb HDD, then putting Windows and everything else on my new HDD (which I am getting soon) but there isn't a way to do this now is there?

---

