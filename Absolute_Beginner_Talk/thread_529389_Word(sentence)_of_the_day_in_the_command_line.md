---
title: "Word(sentence) of the day in the command line"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by UbuntuKhan on 2007-08-19
I'm sorry to start a new thread but I was not able to find what I was looking for. What I am looking for is some command in bash that enables the Terminal window to show a word (sentence) of wisdom every time I open the terminal. I think I have seen this somewhere.

---

### Post by guguma on 2007-08-19
I remember that this was in SLACKWARE LINUX. 

Well I have found this in linuxquestions.org.

It seems that the command is "fortune"

and it is a part of the bds-games package. Get that package.

and I guess that the .sh file is this one.

bsd-games-login-fortune.sh

here is a link 

[http://www.linuxquestions.org/questions/showthread.php?p=1477241&highlight=bash+wisdom#post1477241](http://www.linuxquestions.org/questions/showthread.php?p=1477241&highlight=bash+wisdom#post1477241)

---

### Post by schorsch on 2007-08-19
You should install

fortune-mod
fortunes-min

and then add the following line at the end of your ~/.bashrc:

fortune

---

### Post by UbuntuKhan on 2007-08-21
Thank you both! It was fortune indeed, but here's something funny: Apparently it was already installed and it is saying that the package libecore1-dbus is no longer necessary. What is this package and what is the connection between it and fortune? This is a question for which I will probably not get an answer, but I'm hoping that I do.
> Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture de l'information d'état... Fait
fortune-mod est déjà la plus récente version disponible.
Les paquets suivants ont été automatiquement installés mais ne sont plus nécessaires :
  libecore1-dbus
Utiliser "apt-get autoremove" pour les supprimer
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.

---

### Post by schorsch on 2007-08-21
I guess the package "fortune" has no relation to the package "libecore1-dbus". As you apt'ed to install fortune apt has checked something in the background and found that the mentioned package will be no longer used. It is possible that you uninstalled something not long ago .....
Could you please mark this thread as solved as it could help others, too? This can be done via the "Thread Tools" link in the upper right .....

---

