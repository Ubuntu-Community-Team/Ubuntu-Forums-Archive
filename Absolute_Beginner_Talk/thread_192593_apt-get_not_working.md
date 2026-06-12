---
title: "apt-get not working??"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by truth on 2006-06-08
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb)
  Connection failed [IP: 85.133.25.7 80]

why does my apt-get connection keep on failing? 

Does this have anything at all to do with a possible Port being Closed via my Router? 

thx

---

### Post by nalmeth on 2006-06-08
Try this
Open a terminal
type:
```
sudo nano /etc/apt/sources.list
```

go to the line with matching the address in the error, and remove the us so that it's just archive.ubuntu.com/ubuntu/....

then 

```
sudo apt-get update
```

and you should be good.

---

### Post by truth on 2006-06-08
[QUOTE=nalmeth]Try this
Open a terminal
type:
```
sudo nano /etc/apt/sources.list
```

go to the line with matching the address in the error, and remove the us so that it's just archive.ubuntu.com/ubuntu/....

then 

```
sudo apt-get update
```

and you should be good.[/QUOTE]

Na didnt work!! its weird cuz i can easly access the address via Firefox but just cant connect via apt-get  weird. .  :/

---

### Post by nalmeth on 2006-06-09
```
 Na didnt work!! its weird cuz i can easly access the address via Firefox but just cant connect via apt-get  weird. .  :/
```
whats the output of the error now? Are you sure you saved the change (removing 'us') It's just having difficulty downloading some .deb file

---

