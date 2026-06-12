---
title: "how do i take care of this problem ????"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by rutz on 2007-07-30
hello ppl m new to linux ............... was jst installin sun- java-5 ie jre amd jdk .....from adept manager...........the package got downloaded and was gettin installed ......as it was gettin installed it got stuck at 22% ......i kept it like tat for an hr or so still it did not show any progress.....therefore i closed it .... and i again opened the adept manager to reinstall it ...its givein me the foll error : ====> screenshot below 




[IMG]http://img293.imageshack.us/img293/1130/snapshot2ga4.jpg[/IMG]




plzzz help me to solve this problem .....



thanx in advance 


regards,
rUTz!! :guitar:

---

### Post by daller on 2007-07-30
Please restart your computer, and run this from a terminal:

```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by Seisen on 2007-07-30
It might even help to run ```
sudo dpkg --configure -a
``` before you run ```
sudo apt-get -f install
```

---

### Post by rutz on 2007-07-30
@daller ,Seisen thank you very much ma problem is solved ...linux rocks man .....:guitar:

---

