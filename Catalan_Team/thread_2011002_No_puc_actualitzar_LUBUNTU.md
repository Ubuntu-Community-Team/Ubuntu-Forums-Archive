---
title: "No puc actualitzar LUBUNTU"
date: 2012-06-26
forum: Catalan Team
---

### Post by Arteazul on 2012-06-26
Hola a tots, quan tracte d'actualitzar lubuntu, em dona el següent problema:

Ha fallat la càrrega de la llista de paquets

Aquest es un problema seriós.  Torneu a intentar-ho més tard. Si el problema reapareix, informeu-ne els desenvolupadors.

Details: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.

Moltes gràcies si algú pot ajudar-me. Porte ja així dues setmanes i les recomanacions d'altres no em funcionen o no sé fer-les funcionar.

Gràcies

---

### Post by dgharmon on 2012-06-26
> **Arteazul said:**
> Details: E:Encountered a section with no Package: header
[I]
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update             [/I]

---

### Post by Arteazul on 2012-06-26
Ràpid i efectiu.

Moltes gràcies :)

---

### Post by wgarcia on 2012-06-27
Si pots marcar "Solved" a "Thread tools", faràs un favor als que es trobin amb aquest problema i facin una cerca en aquest fòrum.

---

