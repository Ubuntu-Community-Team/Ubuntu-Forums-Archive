---
title: "Problem with installing... anything"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by abrainlessdude on 2006-04-13
Any time I try to install.... *anything*, I get the following error message (what I tried to install included)

```
marc@ubuntu:~$ sudo apt-get install ipodslave
sudo: unable to lookup ubuntu via gethostbyname()
marc@ubuntu:~$
```

---

### Post by nemequ on 2006-04-13
Try prepending the following line to your /etc/hosts file:

```
127.0.0.1       ubuntu
```

---

### Post by abrainlessdude on 2006-04-13
[QUOTE=nemequ]Try prepending the following line to your /etc/hosts file:

```
127.0.0.1       ubuntu
```[/QUOTE]Would you mind helping me do that?

What do I type in to pull up /etc/hosts because in the /etc/host file doesnt let me edit it, it's read only.

---

### Post by dickohead on 2006-04-13
Run this:
```
sudo echo 127.0.0.1 ubuntu >> /etc/hosts
```

or you can do:

```
sudo vi /etc/hosts
```

and then add the line in yourself.

>> appends input to the end of a file

---

### Post by steve.horsley on 2006-04-13
Reminds me of a song "There's a hole in my bucket.". 

He can't sudo vi /etc/hosts because sudo doesn't work because hosts is wrong.

The answer is to use rescue mode from the installer CD. This places you at a root prompt where you have the rights to edit hosts.

A neat trick  I saw yesterday was to use Esc to stop grub, press e to edit the default entry, then edit the kernel line to append rw init=/bin/bash, then press b to boot. This dumps you at a root prompt.

---

