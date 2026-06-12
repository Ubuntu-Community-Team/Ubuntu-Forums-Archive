---
title: "Trouble Downloading"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Catfish_lolipop on 2007-07-27
I am having a problem downloading things. i dont know what i did, or what the problem is  but every time that i try to download something from synaptic or automatix it comes up with a whole lot of errors.maybe i have broken packages? maybe im behind a firewall now? idk if you could help me it would be apprieciated.

---

### Post by Majorix on 2007-07-27
Could you try installing something through the terminal and post the output please?

Like this:
```
sudo apt-get install *packagename*
```

Then we can help :)

---

### Post by Catfish_lolipop on 2007-07-27
im obviously doing it wrong because it says that it cant find the package. i changed the directory to where the package is located, then i ran that code. then terminal tells me that it isnt there. did i skip something? or just wrong way of doing it? idk......

---

### Post by Majorix on 2007-07-28
The packages are located on the web, not on your computer somewhere. Did you enable the repositories (universe, multiverse)?

---

### Post by mkoehler on 2007-07-28
Go into Synaptic Package Manger, then go to Settings > Repositories.  Make sure all of the checkboxes on the first tab are selected (multiverse, universe, etc)  Then open up the terminal and type```
sudo apt-get update
``` followed by ```
sudo apt-get <package-name>
```Then paste the output here so we can help you more.

Cheers!

---

### Post by Catfish_lolipop on 2007-07-28
okay i tried the sudo apt-get update and it popped up with a whole lot of errors saying -------- Err [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by Majorix on 2007-07-29
Could you please post your /etc/apt/sources.list? Probably in an attachment so that it doesn't take up space here :)

---

### Post by Catfish_lolipop on 2007-07-29
when i try to upload it as an attachment it says that is an "invalid file" should i just copy and paste what the file says?

---

