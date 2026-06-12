---
title: "how do i encrypt files?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-07
i want a gui that doesnt have a bunch of dependencies that i have to install via source code, and fairly easy to use, possibly something that integrates in to nautilus so that i can right-click file and select an option like "encrypt file" and type a password. also anything with the ability to have a master password that stores all the other ones would be good (i think thats called a key ring, not sure though).

TIA,
anti

---

### Post by bodhi.zazen on 2008-01-07
Simple : gpg
		Encrypt gpg -c file
		Decrypt gpg file.gpg
		[http://www.linuxjournal.com/article/8732](http://www.linuxjournal.com/article/8732)

---

### Post by p_quarles on 2008-01-07
The Krusader file manager certainly does what you're looking for, but I'm not sure if it can use the Gnome Keyring app. There is a GPG frontend for Gnome, though:
```
sudo apt-get install gpgp
```

---

### Post by ryanVickers on 2008-01-07
thanks!

everyone ... lol this was most useful! :p

---

