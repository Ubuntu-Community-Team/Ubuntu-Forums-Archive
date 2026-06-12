---
title: "Installing BF2 on Linux"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-10
Ugh
I've waited long enough
I must get this working now.

If I must, ill start a remote desktop because I just don't understand it:(\

Emulators?

:|

I miss my BattleField 2. =[
( Its not 2147 or whatever, It's just BF2. )

---

### Post by christarp on 2007-05-10
Get wine.

[www.winehq.org](www.winehq.org)

---

### Post by christarp on 2007-05-10
Here's the link to the downloads and it tells you what to do.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by LollYouSuckZor on 2007-05-10
> **christarp said:**
> Here's the link to the downloads and it tells you what to do.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Im using Kubuntu..:mad:

---

### Post by smartalecks on 2007-05-10
> **LollYouSuckZor said:**
> Im using Kubuntu..:mad:

Same debs should work just fine :), it doesn't matter with wine because it isn't made specifically for a desktop environment.

other applications it may matter because they might be built to work specifically with a desktop environment.

---

### Post by russell.h on 2007-05-10
It should still work I would think....?

---

### Post by LollYouSuckZor on 2007-05-10
Yeah Ive got it, but how do I start the setup.exe with wine....
:(

---

### Post by Nekiruhs on 2007-05-10
in a terminal 
wine /path/to/setup.exe

---

### Post by LollYouSuckZor on 2007-05-10
nic@nic-desktop:~$ wine /path/to/setup.exe
bash: wine: command not found

---

### Post by Nekiruhs on 2007-05-10
> **LollYouSuckZor said:**
> nic@nic-desktop:~$ wine /path/to/setup.exe
bash: wine: command not found
/path/to/setup.exe is the PATH to the setup.exe not literally the command. And by the sound of things wine isn't installed.

---

### Post by LollYouSuckZor on 2007-05-10
nic@nic-desktop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
nic@nic-desktop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list
--19:05:06--  [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 139 [text/plain]

100%[====================================>] 139           --.--K/s

19:05:07 (14.73 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [139/139]

---

What now? :X

---

### Post by LollYouSuckZor on 2007-05-10
nic@nic-desktop:~$ sudo apt-get update
E: Type '-e\n' is not known on line 34 in source list /etc/apt/sources.list
nic@nic-desktop:~$ sudo apt-get install wine
E: Type '-e\n' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
nic@nic-desktop:~$

---

### Post by Nekiruhs on 2007-05-10
Why dont you post your sources.lst here. I've got to sleep now, but I can help you fix it in the morning. Btw, if you wanna fix it yourself, theres a typo involving -e\n in line 34 of sources.list. Im thinking it should be -e/n

---

### Post by ZeroWing on 2007-05-10
> **LollYouSuckZor said:**
> nic@nic-desktop:~$ wine /path/to/setup.exe
bash: wine: command not found

 Hehe...

 You're a total noob, man.

 Set up an RDS, and I'll do it for you, but you really got to learn how to do this stuff on your own sooner or later.

---

### Post by LollYouSuckZor on 2007-05-10
> **ZeroWing said:**
> Hehe...

 You're a total noob, man.

 Set up an RDS, and I'll do it for you, but you really got to learn how to do this stuff on your own sooner or later.

Not if I keep giving you butt secks.

---

### Post by ZeroWing on 2007-05-10
> **LollYouSuckZor said:**
> Not if I keep giving you butt secks.

 No profanity, unless you want to get banned...

---

### Post by LollYouSuckZor on 2007-05-11
> **ZeroWing said:**
> No profanity, unless you want to get banned...

Oh God, You're such a square.

---

