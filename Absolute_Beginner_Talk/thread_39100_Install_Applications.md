---
title: "Install Applications"
date: 2005-06-03
forum: Absolute Beginner Talk
---

### Post by Comatose on 2005-06-03
I am very new to Ubuntu, and Linux as a whole. I am trying to install yahoo messenger on my computer, and I havent any clue as to how to get this done. Any help would be greatly appreciated.

---

### Post by Leif on 2005-06-03
I'm afraid yahoo messenger itself is not available in linux, but Gaim, which you can find under your Applications->Internet tab should enable you to connect to the yahoo network. Take a look at ubuntuguide.org to get an idea of how to install stuff in ubuntu.

---

### Post by Comatose on 2005-06-03
The Yahoo server gives download instructions for linux though, I just thought that  they would have a functioning linux version since they say they do. Thanks for the giam tip though, worked like a charm.

---

### Post by bored2k on 2005-06-03
[QUOTE=Comatose]The Yahoo server gives download instructions for linux though, I just thought that  they would have a functioning linux version since they say they do. Thanks for the giam tip though, worked like a charm.[/QUOTE]
 If you still want the ugliest yahoo messenger on the planet:
Applications > system tools > terminal
Here do:
```
wget http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb
sudo dpkg -i ymessenger_1.0.4_1_i386.deb
```

*not recommended.

---

### Post by Leif on 2005-06-03
Sorry about that, I had no idea there was a linux client for this.

---

### Post by bored2k on 2005-06-03
[QUOTE=Leif]Sorry about that, I had no idea there was a linux client for this.[/QUOTE]
 No no , you were right pointing him to gaim ! But if he still wants the ugly official yahoo client, he should have it ;).

---

### Post by angrykeyboarder on 2005-06-21
[QUOTE=Leif]Sorry about that, I had no idea there was a linux client for this.[/QUOTE]

It's been around for ages. It's just not well known. Most like yourself would not think to check.

It's wrechedly ugly though (GTK1) and is about 4 years behind the Windows client in functionality.

Gaim (or Kopete) is a much better choice.  AIM has a Linux version too, it's slightly more up to date, but still not as good as Gaim.

---

