---
title: "MPlayer"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by blanc11 on 2006-06-05
Can someone tell me where to get MPlayer for Gnome please!

---

### Post by meng on 2006-06-05
Enable multiverse repositories.
Install mplayer package.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by bluevoodoo1 on 2006-06-05
[https://wiki.ubuntu.com/MplayerInstallHowto](https://wiki.ubuntu.com/MplayerInstallHowto)

---

### Post by blanc11 on 2006-06-05
Well, I enabled multiuniverse repositories and did  a search in Synaptic and I got nothing. I am working with dapper BTW

---

### Post by bluevoodoo1 on 2006-06-05
[QUOTE=blanc11]Well, I enabled multiuniverse repositories and did  a search in Synaptic and I got nothing. I am working with dapper BTW[/QUOTE]

Did you hit "Reload" in Synaptic after you added multiverse?

---

### Post by blanc11 on 2006-06-05
yes

---

### Post by bluevoodoo1 on 2006-06-05
Can you paste here the output of this terminal command:

```
cat /etc/apt/sources.list | grep multiverse
```

---

### Post by blanc11 on 2006-06-06
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

---

### Post by bluevoodoo1 on 2006-06-06
[QUOTE=blanc11]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse[/QUOTE]

You only have the backports multiverse there...

I suggest checking out [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) 

or the "source.list generator" link in my signature.

---

### Post by blanc11 on 2006-06-06
where is sources.list, I forgot

---

### Post by bluevoodoo1 on 2006-06-06
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

After you've added the repositories you want, save the file and run...

```
sudo apt-get update
```

---

### Post by blanc11 on 2006-06-06
Thanks so much!

---

