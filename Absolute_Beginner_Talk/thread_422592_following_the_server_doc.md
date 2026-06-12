---
title: "following the server doc"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Garry.k on 2007-04-25
I have a problem it might be something silly am doing but when reading through the guide it was fine when using 
sudo apt-get comands to install and upgrade and remove packages but when reading on to conf the network it say the ethernet conf is in the /etc/network/interfaces file but when i try to use this it says permission denied but when I use sudo /etc/network/interfaces it cant find file or path can some one plz help me on this TY:confused:

---

### Post by RedSquirrel on 2007-04-25
Are you trying to edit the file? If so, you have to specify an editor to open the file, for example:

```
sudo nano -w /etc/network/interfaces
```

---

