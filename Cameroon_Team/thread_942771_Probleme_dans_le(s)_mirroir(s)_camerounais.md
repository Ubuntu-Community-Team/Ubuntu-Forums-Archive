---
title: "Probleme dans le(s) mirroir(s) camerounais ?"
date: 2008-10-09
forum: Cameroon Team
---

### Post by ongola_boy on 2008-10-09
Hi !
je vous fais part d'un probleme que je rencontre depuis la semaine passee sur certains postes de mon reseau.
Mes postes ont Xubuntu (7.10 et 8.04) . En faisant un apt-get update, j'obtiens un des erreurs sur certains depots. Par exemple, voici l'une des sorties que j'obtiens.
```
 Impossible de récupérer http://cm.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2  Somme de contrôle de hachage incohérente

E: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
```

J'ai deux questions :
[LIST]
[*]le probleme est-il a mon niveau ou au niveau du(des) mirroir(s) [http://cm.archive.ubuntu.com](http://cm.archive.ubuntu.com) ?
[*]quand j'y pense, comment peut-on changer de mirroirs ?
[/LIST]

---

### Post by ongola_boy on 2008-10-13
Visiblement ca devait etre un probleme avec le(s) miroir(s)... Actuellement je peux proceder a un ```
sudo apt-get update
``` sans qu'il n'y ait d'erreur...

---

### Post by septox on 2009-02-23
regle ?

---

### Post by ongola_boy on 2009-03-03
non, pas vraiment :( . Il y a toujours des moments où j'ai toujours ces erreurs. Je veux bien croire (*d'apres ce qu'on m'avait dit sur #ubuntu-mirrors*) qu'il doit s'agir d'un probleme avec ma connexion internet.

---

