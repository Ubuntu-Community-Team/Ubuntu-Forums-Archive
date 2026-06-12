---
title: "Synaptic repositories"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-11-08
I have upgraded to the latest Synaptic release 0.57.4 on Breezy.
I found its having quite a few problems. One of the most irritating is that when I go  Settings>Repositories, nothing happens. So I cannot change or remove anything there.
I have manually added and removed files in my sources.list. Most notably, I changed "Hoary" to "Breezy" and removed all the older lines that was edited out. So I basically have the original sources.list. Problem is when I start Synaptic, it still show things like "unable to update.....hoary....." and some CD's I've added on later, and don't use anymore. How come? I don't have those in my sources.list anymore and as I said, I cannot access repositories from within Synaptic.

---

### Post by Remmelas on 2005-11-08
do from the command line
sudo gedit /etc/apt/sources.list 
and just make sure that there are no references to hoary anymore, and that only references to breezy are uncommented.
Then, 
sudo apt-get update
and if that goes well, 
sudo apt-get dist-upgrade

these are the steps I followed when I had some strangeness in synaptic, and cleared them, hopefully works for u too...

---

