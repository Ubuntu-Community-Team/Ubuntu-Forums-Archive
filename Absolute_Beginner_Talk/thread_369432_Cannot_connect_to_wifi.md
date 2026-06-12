---
title: "Cannot connect to wifi"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by birddseedd on 2007-02-24
I have a Atheros wifi adapter in my laptop. i just installed kubuntu. i was told that i had to install a madwifi thing to get the atheros adapter to work in linux. it reconizes networks. but just cannot connect to them. the madwifi thing is a red hat package manager file. how do i get rpm's to install on kubuntu?

---

### Post by Aazn on 2007-02-24
Use alien.
```

sudo apt-get install alien

```

```

sudo alien madwifi.rpm
dpkg -i madwifi*.deb

```

---

### Post by birddseedd on 2007-02-24
mike@toshiba:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package alien

---

### Post by birddseedd on 2007-02-24
ok. i was able to use adept to install alien. but madwifi and madwifi.rpm both are not found?

---

