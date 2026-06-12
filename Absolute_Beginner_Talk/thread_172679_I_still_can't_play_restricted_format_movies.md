---
title: "I still can't play restricted format movies"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-09
I've installed w32codecs following all the stepd showed in this forum, but i still can't play movies in my computer.I'm using Ubuntu 6.06 Dapper. HELP

---

### Post by tseliot on 2006-05-09
Try with:
```
sudo apt-get install totem-xine mplayer
```

---

### Post by skippy81 on 2006-05-09
Are you on AMD64 by any chance?

Don't think the windows only codecs work on 64 bit.

---

### Post by kart3r on 2006-05-09
[QUOTE=tseliot]Try with:
```
sudo apt-get install totem-xine mplayer
```[/QUOTE]

i've tried this but it says that this package is a virtual package, i'm new with linux :S

---

### Post by tseliot on 2006-05-09
[QUOTE=kart3r]i've tried this but it says that this package is a virtual package, i'm new with linux :S[/QUOTE]
???
post the output of th error, please

---

### Post by kart3r on 2006-05-09
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
O pacote mplayer é um pacote virtual disponibilizado por:
  mplayer-nogui 1:1.0-pre6-0.3ubuntu6
  mplayer-k6 1:1.0-pre6-0.3ubuntu6
  mplayer-custom 1:1.0-pre5-0.6ubuntu1
  mplayer-586 1:1.0-pre6-0.3ubuntu6
  mplayer-386 1:1.0-pre6-0.3ubuntu6
Você deve seleccionar explicitamente um para instalar.
E: O pacote mplayer não tem candidato para instalação


sorry because it is in portuguese =X

---

### Post by tseliot on 2006-05-09
```
sudo apt-get install totem-xine mplayer-386 mplayer-skins
```

Then try to play the video either with totem or with mplayer

---

### Post by kart3r on 2006-05-09
i've done this: sudo apt-get install libtotem-plparser1 libtotem-plparser-dev
because the command lines you gave me do not worked.i still can't view movies :(

---

### Post by helpme on 2006-05-09
[QUOTE=kart3r]i've done this: sudo apt-get install libtotem-plparser1 libtotem-plparser-dev
because the command lines you gave me do not worked.i still can't view movies :([/QUOTE]
If you don't post the actual error messages, it's very hard to help you.

Also, try the following:
sudo apt-get install totem-xine libxine-extracodecs

---

### Post by kart3r on 2006-05-09
sudo apt-get install totem-xine libxine-extracodecs doesn't work to, it says that the package is not available and there is no candidate for it :(

---

### Post by mostwanted on 2006-05-09
You need to enable the extra repositories:

[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)

---

### Post by helpme on 2006-05-09
You´ll have to enable the needed repositories first:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

After that, it should work.

---

