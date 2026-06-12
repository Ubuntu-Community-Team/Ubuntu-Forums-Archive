---
title: "Problem with Automatix"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by helino on 2006-07-01
Hi, I'm new to Ubuntu, and I have to say it's really great, I just finished the installation. Although I encountered a problem when I tried to run Automatix to get all progams, codecs, plugins and so on. 

I type Automatix in the terminal, but the message I'm getting this:

```
bash: AUTOMATIX: command couldn't be found
```

I'm an absolute beginner on Ubuntu, so could someone please help me with this?

PS. I tried to search, but the Automatix thread is 52 pages long...:roll:

---

### Post by Spleenie on 2006-07-01
[QUOTE=helino]Hi, I'm new to Ubuntu, and I have to say it's really great, I just finished the installation. Although I encountered a problem when I tried to run Automatix to get all progams, codecs, plugins and so on. 

I type Automatix in the terminal, but the message I'm getting this:

```
bash: AUTOMATIX: command couldn't be found
```

I'm an absolute beginner on Ubuntu, so could someone please help me with this?

PS. I tried to search, but the Automatix thread is 52 pages long...:roll:[/QUOTE]

Judging by the above error, perhaps you have typed it in upper case. most, if not all *nix operating systems are case sensitive, as in S is not s. Try typing "automatix" and see what happens then

Another possibility is you have not installed automatix. If not then type:

```
sudo apt-get install automatix
```

If you have installed it then disregard that last piece of advice :)

Good luck!

---

### Post by helino on 2006-07-01
Thx for the answer, as far as I know, I haven't installed automatix, but when I'm trying to install it, I get:

```
 E: could not find the package automatix
```

Do you have any other suggestion?

---

### Post by Spleenie on 2006-07-01
[QUOTE=helino]Thx for the answer, as far as I know, I haven't installed automatix, but when I'm trying to install it, I get:

```
 E: could not find the package automatix
```

Do you have any other suggestion?[/QUOTE]

Yep :) read [http://ubuntuforums.org/showthread.php?t=190025]("http://ubuntuforums.org/showthread.php?t=190025")

---

### Post by kigina on 2006-07-01
[this]("http://www.getautomatix.com/index.php?option=com_content&task=view&id=13&Itemid=31") will probaly be a little easier to understand

---

### Post by helino on 2006-07-01
Spleenie: Thank you, now it all worked out really good!

kigina: I don't think Spleeines link was hard to understand, it only copy and paste :)

---

