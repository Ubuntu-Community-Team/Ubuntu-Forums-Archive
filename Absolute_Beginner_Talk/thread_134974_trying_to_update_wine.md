---
title: "trying to update wine"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2006-02-22
Hello,

I've been attempting to add **WineHQ APT** to my repositories, per the instructions [here]("http://www.winehq.com/site/download-deb"). I don't receive any errors after adding that repository, however, it never shows the newer version. Am I doing something wrong, I'm unaware of?

Thank you

---

### Post by george_apan on 2006-02-23
Open your sources list file with:
```
sudo gedit /etc/apt/sources.list
```
Make sure there is a
```
deb http://wine.sourceforge.net/apt/ binary/
```
line in there. I'm thinking maybe you added the sources repository instead of the binary one.
Do a
```
sudo apt-get update
```
from a terminal window.
You should see all available upgrades now.

---

### Post by Il_Tuo_Nome on 2006-02-23
Thank you very much, that did the trick. I must of been copying the wrong file or mistyped or something.

either way thank you very much

---

