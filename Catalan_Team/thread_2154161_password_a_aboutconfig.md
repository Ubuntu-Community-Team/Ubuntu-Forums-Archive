---
title: "password a about:config"
date: 2013-06-13
forum: Catalan Team
---

### Post by JUSTERINI1 on 2013-06-13
Hola ubuntuaires,
Estic intentant accedir al about:config del Firefox i em demana un password que no sé, i no és que l'hagi oblidat, és que no recordo
haver-li posat mai. He probat amb tots els que tinc i no hi ha manera.
Alguna solució? algun password genèric?


Gràcies
Justerini

---

### Post by ajgreeny on 2013-06-13
Sorry, I don't speak Spanish.

Try changing permissions of ~/.mozilla/firefox/xxxxxxx.default/prefs.js to read only; it locks the file and its contents.
```
chmod 500 /home/*username*/.mozilla/firefox/xxxxxxx.default/prefs.js 
```
Change** xxxxxxx.default** to your own system foldername

---

### Post by JUSTERINI1 on 2013-06-14
Hi ajgreeny! thanks, but I couldn't tried it yet :-(
Now the problem is worst because I uninstalled Firefox thinking to reinstall it again, and solve the problem, but, now I cannot install nothing
from ubuntu repositories (neither from ubuntu programs or terminal, always the connection fails), and at this point, I'm thinking that this problem was before the origin of this thread. 
So, Now I'm trying to solve this issue and once I've done it, will try to fix the firefox issue if is needed.

Algú sap perquè no puc instal.lar CAP tipus de programari de la comunitat? Perquè sempre em diu que falla la connexió? He modificat el servidor a fonts de programari, i segueix igual. La última cosa que recordo haver instal.lat era el Citrix Receiver, si algú coneix el Citrix, sap si pot haver interferit amb la configuració de les actualitzacions?

Gràcies

---

### Post by wgarcia on 2013-06-14
Et surt algun error quan fas des d'una terminal 

```
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by JUSTERINI1 on 2013-06-14
Hola Wgarcia,
Tinc la versió [COLOR=#3C3C3C]11.04 - the *Natty Narwhal* -[/COLOR]

l'update busca però no pot baixar cap paquet, al final dóna el seg. error: 
E: Some index files failed to download. They have been ignored, or old ones used instead.
l'upgrade:
sudo: unable to resolve host jordi-LIFEBOOK-AH530
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.

Alguna cosa m'he carregat, però què?
Tinc connexió a la xarxa sense problemes, l´únic que no connecta és pel programari del Ubuntu i Synaptic.

Justerini

---

### Post by wgarcia on 2013-06-14
Potser obre un nou fil i enganxa aquest últim missatge amb un títol adient, el títol d'aquest fil ha quedat completament desfasat, i la continuem allà.

---

### Post by JUSTERINI1 on 2013-06-16
Hi ajgreeny, Wgarcia,

Finally I fixed the issue "password at about:config" by restoring Firefox with safe mode and depurating the plugins:

[https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode#w_troubleshooting-problems-in-safe-mode](https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode#w_troubleshooting-problems-in-safe-mode)

He pogut solucionar el problema, restaurant el Firefox amb la opció d'iniciar en mode segur i depurant els plugins que interferien
en el password de la configuració. En l'enllaç anterior podeu trobar informació de com fer-ho.

Sobre el problema de baixada de repositoris de l'Ubuntú, ho he arreglat a lo bèstia, actualitzant de la versió 11.04 a la 12.04 via cd, i la veritat és que ja tocava, tot i que no trobo gens útil la barra de l´Unity (algú més ho havia de dir) m'he passat al clàssic again.

Gràcies
Justerini.

---

