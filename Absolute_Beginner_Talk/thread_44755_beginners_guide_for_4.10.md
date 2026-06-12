---
title: "beginners guide for 4.10?"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-06-27
I have just started the beginners guide and tried to add extra repositories and it turns out I am running 4.10 warty warthog amd64 beta.

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview amd64 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

That is the sources file.

Where can I find a guide for that version or can the amd64 version of 4.10 be upgraded to 5?

---

### Post by bored2k on 2005-06-27
[http://ubuntuguide.org/4.10/index.html](http://ubuntuguide.org/4.10/index.html)

---

### Post by gammyhand on 2005-06-27
[QUOTE=bored2k][http://ubuntuguide.org/4.10/index.html](http://ubuntuguide.org/4.10/index.html)[/QUOTE]
 Thanks :)

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=gammyhand]I have just started the beginners guide and tried to add extra repositories and it turns out I am running 4.10 warty warthog amd64 beta.
[/QUOTE]

Please note that the 64 bit version lacks windows codecs, java, and other things. Its meant for experiance Linux users only.

---

### Post by gammyhand on 2005-06-27
[QUOTE=poofyhairguy]Please note that the 64 bit version lacks windows codecs, java, and other things. Its meant for experiance Linux users only.[/QUOTE]
 grrr. I wish it had mentioned this before I installed it. :( Think I will re-install with the 32 bit version. Shame.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=gammyhand]grrr. I wish it had mentioned this before I installed it. :( Think I will re-install with the 32 bit version. Shame.[/QUOTE]

Sorry. There is a way around it if you want to know:

[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot)

Its a little nerdy though.

---

### Post by gammyhand on 2005-06-28
[QUOTE=poofyhairguy]Sorry. There is a way around it if you want to know:

[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot)

Its a little nerdy though.[/QUOTE]
 Thanks :)

---

