---
title: "Why I can't listen MP3s?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by ondoin on 2007-12-05
I tried to listen some mp3 songs but I found out that I couldn't.Searching for help [I found this]("https://help.ubuntu.com/community/RestrictedFormats/MP3#head-adbf583092e864395cc02a8ee6aaf82e573720a3") but didn't understand what should I do.
Can somebody help me please?

I have Xubuntu.

---

### Post by Peryl on 2007-12-05
I think it would help if you would tell what program you are using to listen to the music/ but besides that

try usinng amarok plays alot of popular formats

---

### Post by SOULRiDER on 2007-12-05
Using Amarok is a very abd idea if youre using Xubuntu.

To isntall mp3 support follow these steps.
In a terminal type:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install w32codecs
```

You should have mp3 support now.

---

### Post by Peryl on 2007-12-05
ops lol i only read ubuntu didnt see X in front thanks for catching that

---

### Post by quandary on 2007-12-05
Applications->System Tools->Konsole

type:
sudo apt-get install mplayer
sudo apt-get install totem
sudo apt-get install ubuntu-restricted-extras

---

### Post by ondoin on 2007-12-05
After I type:
sudo apt-get install mplayer
sudo apt-get install totem
sudo apt-get install ubuntu-restricted-extras

on terminal it asks for Password and freezes.I tried to enter password but nothing,can't type at all.

Well,now something happened.I think it downloaded something.

---

### Post by diatribe on 2007-12-05
when you type the password there wont be any output

---

### Post by ondoin on 2007-12-05
> **Peryl said:**
> I think it would help if you would tell what program you are using to listen to the music/ but besides that

try usinng amarok plays alot of popular formats

 I used gxine and VLC Media Player.

---

### Post by quandary on 2007-12-05
> **ondoin said:**
> After I type:
sudo apt-get install mplayer
sudo apt-get install totem
sudo apt-get install ubuntu-restricted-extras

on terminal it asks for Password and freezes.I tried to enter password but nothing,can't type at all.

Well,now something happened.I think it downloaded something.

diatribe is correct. it doesn't show the password as you type it. Just press enter afterwards.

Software now installed --> MP3 should play...

---

### Post by ondoin on 2007-12-05
gxine doesnt play at all the mp3.VLC Media player plays the song but without the sound.
Maybe I should restart my computer or am I missing something else here?

BTW,in the terminal,I should write as you showed
sudo apt-get install 
press enter?
sudo apt-get install totem
enter?
sudo apt-get install ubuntu-restricted-extras
enter?


or I can also copy and paste?
sudo apt-get install mplayer
sudo apt-get install totem
sudo apt-get install ubuntu-restricted-extras

---

### Post by stchman on 2007-12-06
> **ondoin said:**
> I tried to listen some mp3 songs but I found out that I couldn't.Searching for help [I found this]("https://help.ubuntu.com/community/RestrictedFormats/MP3#head-adbf583092e864395cc02a8ee6aaf82e573720a3") but didn't understand what should I do.
Can somebody help me please?

I have Xubuntu.

Follow my tutorial for MP3.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---

### Post by quandary on 2007-12-07
> **ondoin said:**
> gxine doesnt play at all the mp3.VLC Media player plays the song but without the sound.
Maybe I should restart my computer or am I missing something else here?

BTW,in the terminal,I should write as you showed
sudo apt-get install 
press enter?
sudo apt-get install totem
enter?
sudo apt-get install ubuntu-restricted-extras
enter?


or I can also copy and paste?
sudo apt-get install mplayer
sudo apt-get install totem
sudo apt-get install ubuntu-restricted-extras

either always press enter, or type:
sudo apt-get install mplayer totem ubuntu-restricted-extras

---

