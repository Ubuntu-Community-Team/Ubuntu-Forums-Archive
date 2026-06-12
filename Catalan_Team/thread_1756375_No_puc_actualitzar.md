---
title: "No puc actualitzar"
date: 2011-05-12
forum: Catalan Team
---

### Post by ladisse on 2011-05-12
Dissabte vaig instalar de nou la darrera versió de l'ubuntu; amb escriptori gnome. Dilluns, vaig poder instalar l'unity 2D. Des de llavors, no puc actualitzar (bé, de fet des d'abans de la darrera versió de l'ubuntu tampoc em deixava gaire; vaig poder actualitzar dissabte mateix). 
El cas és que he provat de canviar les fonts de repositoris i tampoc no puc (deixo les captures). Algun cop de mà? Gràcies.
[IMG]http://ubuntuforums.org/home/elena/Documents/Captura.png[/IMG]

També em surt aquest missatge quan miro de instalar programes a través del centre de programari.

---

### Post by wgarcia on 2011-05-13
Suggeriria obrir el Gestor de Paquets Synaptic, i inhabilitar els dipòsits addicionals que tinguis, (a la pestanya "Altres fons de programari") i després de tancar el synaptic, entrar en una terminal 


sudo apt-get update

Si no surten errors

sudo apt-get upgrade

Si surten errors intentar copiar el que ha sortit a un fitxer in engantxar-lo aquí.

---

### Post by ladisse on 2011-05-13
Primer he mirat de canviar lo dels dipòsits que em dius; no he sabut trobar quins són els que haig d'inhabilitar. 
(vegeu captura de la dreta)
gràcies per l'ordre de terminal a fer; he fet la de apt-get update i m'ha sortit els missatges següents:
(vegeu captura de l'esquerra)

He buscat per internet, i no he sabut trobar exactament què he de fer.

---

### Post by wgarcia on 2011-05-13
Això d'inhabilitar els dipòsits de l'altre programari, les instruccions exactes són: 
1) obrir Gestor de Paquets Synaptic
2) Escollir el menú Paràmetres -> Dipòsits
3) Buscar la pestanya "Altre programari" i desmarcar tot, si se soluciona el problema després es poden tornar a habilitar aquests dipòsits.

En quant als results de "apt-get update", segons el que mostra encara tens habilitat encara algun dipòsits de la versió "maverick". Possiblement els puguis deshabilitar a la pestanya que s'indica a dalt.

---

### Post by ladisse on 2011-05-19
Fins avui no he pogut entrar al fórum; he mirat d'arreglar el problema, fent diferents terminals (clean, autoclean, update, upgrade) i no me n'he sortit. Si algú em vol dir, si us plau, com treure la brossa que sembla que em bloqueja les actualitzacions, us estaré molt agraïda.

---

### Post by wgarcia on 2011-05-19
Pots enganxar el fitxer 

/etc/apt/sources.list 

? Aquí es defineixen els diferents dipòsits i potser algú pot fer l'entrellat. 

I també el que surt quant fas en una terminal 

ls /etc/apt/sources.list.d

a veure si ha algun dipòsit addicional que estigui fent la guixa.

---

### Post by ladisse on 2011-05-19
Aquí va el que he pogut agafar del darrer terminal (no domino el tema per enganxar-lo sencer :(). Entre una cosa i una altra, m'ha deixat actualitzar només algunes coses. He pogut instalar l'unity 2D (que feia força dies que no em deixava i puc instalar alguns programes altra vegda, q tampoc no em deixava).

---

