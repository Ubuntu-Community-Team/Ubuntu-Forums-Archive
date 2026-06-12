---
title: "[PowerPc] Install KDE 4"
date: 2008-05-30
forum: Apple Hardware Users
---

### Post by Kerri on 2008-05-30
Hi

I'm using an up-to-date ubuntu 8.04
I want to install and try the new KDE 4, but as you see I can't: 
```
kerri@kerri-laptop:~$ sudo apt-get install kde4
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.

Puisque vous n'avez demandé qu'une seule opération, le paquet n'est
probablement pas installable et vous devriez envoyer un rapport de bogue.
L'information suivante devrait vous aider à résoudre la situation*: 

Les paquets suivants contiennent des dépendances non satisfaites*:
  kde4: Dépend: kde4-amusements (>= 3.3) mais ne sera pas installé
        Dépend: kde4-core (>= 3.3) mais ne sera pas installé
        Dépend: kdeadmin-kde4 (>= 4:4.0.0) mais ne sera pas installé
        Dépend: kdeartwork-kde4 (>= 4:4.0.0) mais ne sera pas installé
        Dépend: kdegraphics-kde4 (>= 4:4.0.0) mais ne sera pas installé
        Dépend: kdemultimedia-kde4 (>= 4:4.0.0) mais ne sera pas installé
        Dépend: kdenetwork-kde4 (>= 4:4.0.0) mais ne sera pas installé
        Dépend: kdeutils-kde4 (>= 4:4.0.0) mais ne sera pas installé
E: Paquets défectueux

```
sorry for the french: I don't know how to put the terminal in english, and on french forum there's not a lot of ppc users :(

anyway, do you know how can I do to install KDE 4?

P.S: I've got the same problem if I try apt-get install kubuntu-kde4-desktop

P.S2: please, excuse my bad english

---

### Post by oswaldkelso on 2008-05-30
Care of Bable fish

kerri@kerri-laptop: ~$ sudo apt-get install kde4 Reading of the lists of packages&#8230; Fact Construction of l' tree of the dependences Reading of information d' state&#8230; Fact Certain packages cannot be installed. This can mean that you asked for l' impossible, or, if you use the distribution unstable, that certain packages n' do not have yet summer created or did not leave d' Incoming. Since you n' asked qu' only one operation, the package n' is probably not installable and should send a report/ratio of bug to you. L' following information should help you to solve the situation*: The following packages contain dependences not satisfaites*: kde4: Depends: kde4-recreations (> = 3.3) but will not be installed Depends: kde4-core (> = 3.3) but will not be installed Depends: kdeadmin-kde4 (> = 4:4.0 .0) but will not be installed Depends: kdeartwork-kde4 (> = 4:4.0 .0) but will not be installed Depends: kdegraphics-kde4 (> = 4:4.0 .0) but will not be installed Depends: kdemultimedia-kde4 (> = 4:4.0 .0) but will not be installed Depends: kdenetwork-kde4 (> = 4:4.0 .0) but will not be installed Depends: kdeutils-kde4 (> = 4:4.0 .0) but will not be installed E: Defective packages

---

### Post by mfox on 2008-05-30
Bonjour Kerri.  Je pense que j'ai trouvé le problème, une répository vous manque. Voir [ici]("https://bugs.launchpad.net/ubuntu/+source/meta-kde4/+bug/186609").  Je pense qu'il faut seulement ajouter "hardy backports" s'ils existent maintenant.

---------------------------
Hi Kerri.  I think I found the problem, a missing repository.  See [this url]("https://bugs.launchpad.net/ubuntu/+source/meta-kde4/+bug/186609"). I think you will just have to add the hardy backports repositories if they exist right now for the powerpc.

---

### Post by Kerri on 2008-05-31
Hi
in my apt-sources, I've got a backport repository wich seems to be valid: [http://ports.ubuntu.com/dists/hardy-backports/](http://ports.ubuntu.com/dists/hardy-backports/)

does I need an other?

---

### Post by Kerri on 2008-05-31
I add this line:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/) hardy main multiverse restricted universe

and my problem is still here :(

---

### Post by Kerri on 2008-06-01
Up :)

---

### Post by mfox on 2008-06-01
I think you have the repositories you need and I'm not sure what the problem is.  Try this.  Using Synaptic Package Manager, do a search for KDE4 and check if the main packages show up (especially kde4-core, kdebase-kde4 and kdebase-bin-kde4).  From what I can tell, these and everything else I would need to run KDE4 shows up on Synaptic.  If this is true for you, try to install the three listed above and if that works, add others you need a few at a time.  I would try this myself, but I don't want to populate my PowerBook HD with too many Linux things right now as I only have 10gb formatted for all of Linux.

---

