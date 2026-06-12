---
title: "ubuntu hangs after logging in"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Brewbart on 2007-03-10
I downgraded back to ubuntu 6.06 LTS.  When i start i log in and it doesn't load up it just sits on a brown screen.  I have a book and it tells me I must reconfigure X.org
it tells me I must type:
dkpg reconfigure xserver-xorg
when I type this it says 
bash: dkpg: command not found.  
I don't know what I am doing wrong  If anyone knows any way to not make my Ubuntu hang on this screen I would like some help
Thanks in advance.

---

### Post by taurus on 2007-03-10
It should be

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by overdrank on 2007-03-10
> **Brewbart said:**
> I downgraded back to ubuntu 6.06 LTS.  When i start i log in and it doesn't load up it just sits on a brown screen.  I have a book and it tells me I must reconfigure X.org
it tells me I must type:
dkpg reconfigure xserver-xorg
when I type this it says 
bash: dkpg: command not found.  
I don't know what I am doing wrong  If anyone knows any way to not make my Ubuntu hang on this screen I would like some help
Thanks in advance.

Hi try sudo in front of the command, sudo dpkg-reconfigure xserver-xorg   good luck

Awwweee Beat me to it LOL

---

### Post by Brewbart on 2007-03-10
even when i type sudo before it sudo it says:
sudo: dkpg-reconfigure: command not found

---

### Post by taurus on 2007-03-10
> **Brewbart said:**
> even when i type sudo before it sudo it says:
sudo: dkpg-reconfigure: command not found

```
sudo **[COLOR="Red"]dpkg[/COLOR]**-reconfigure xserver-xorg
```

---

### Post by Brewbart on 2007-03-10
LOL yea theres my problem... sorry for reading wrong.  Got into what I needed good catch on my mistake.  Thanks a lot

---

