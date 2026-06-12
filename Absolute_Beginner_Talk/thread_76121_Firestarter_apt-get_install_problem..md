---
title: "Firestarter apt-get install problem."
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by Save 62% on 2005-10-14
I have been trying to install firestarter (firewall) on Breezy (5.10) to no success. I've used the "sudo apt-get install firestarter" command to no avail. I even tried inserting "1.0.3" to the end of the command to specify which version I wanted, all I get is "this package doesn't exist." I briefly read somewhere about universes and multiverses, I believe that they have to do with the repositories. I thought that the installation of firestarter would be a lot easier from what I had read in some other threads on this site, but it has become a fustrating matter to say the least. I'm a noob to linux, any help will be greatly appreciated.

---

### Post by DJ_Max on 2005-10-14
Firestarter is in the Universe. Do a simple backup of your sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
And edit it
```
sudo gedit /etc/apt/sources.list
```

It's commented, so it should be straightforward. Uncomment the universe lines.

Then
```
sudo apt-get update
```

---

### Post by Save 62% on 2005-10-15
Much thanks DJ_Max your info helped me solve my problem :D . After messing up using the terminal I found out that the same could be done using Synaptic (Ubuntu Wiki via Google), so I went that route, and it worked. These forums Rock!

---

### Post by DJ_Max on 2005-10-15
No problem. I get forgetting the same can be done in Synaptic, but that's because I normally use the command line for everything.

---

