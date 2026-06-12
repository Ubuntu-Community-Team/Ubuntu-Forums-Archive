---
title: "Connexió a pc's en xarxa"
date: 2009-11-24
forum: Catalan Team
---

### Post by lluisalguero on 2009-11-24
Hola nois,
a l'instal·lar la 9.10, vaig estar comprovant que la xarxa que tinc amb el altres pc's em funciones i realment així era, podia veure les carpetes compartides que tenia als altres pc's (tots ells amb finestres).

Doncs avui que em fa falta agafar uns arxius d'un dels pc's, veig que no puc veure'n cap. He estat mirant tutorials, però tots fan referència a versions anteriors a la meva i sembla que alguna cosa ha canviat.

També he mirat la configuració de la meva connexió, i tant la IP, DNS, com la porta d'enllaç estàn ben ficades, però com he dit no veig els altres pc's

Si vaig a Llocs -> Xarxa, em surt una icona que fica "Xarxa de Windows" i quan el vull obrir em diu.

```
No s'ha pogut montar l'ubicació
No s'ha pogut recuperar la llista de compartits del servidor
```

Amb les altre versions que tenia de l'Ubuntu, ho vaig poder configurar perfectament, però en aquesta no trobo cap opció on pugui mirar alguna cosa.

He estat buscant i remenant fils del fòrum, però no trobo enlloc alguna cosa clara.

Si vosaltres sabeu d'algun fil on se'n parli, us ho agraïria.

Salutacions,
Lluís

---

### Post by inforbi on 2010-02-15
Tinc el mateix problema, amb ubuntu 9.10. Fins i tot, al clicar a "xarxa" m'apareixen els compartits i la icona de "xarxa windows" però al fer click a qualsevol d'ells m'apareix el missatge comentat.

Agrairé qualsevol comentari.

Moltes gracies.

Inforbi.

---

### Post by bumux on 2010-03-19
Bona nit.

Hem passa exactament el mateix. Amb altres versions podia veure un disc dur que tinc en xarxa amb FAT32; ara amb la 9.10 no hi ha manera.

Salutacions.

---

### Post by carlesbm on 2010-10-16
Hola companys 

Hem trobo igual amb l'acces a la xarxa local, no puc veure cap ordinador que estigui conectat, per contra desde un portatil que tinc si que puc veure i accedir a tots els ordinadors compartits menys el meu ( el que no pot veure cap altre ordinador)

Algú te alguna solució?

No consegueixo solucionar el problema. El problema va apareixer amb la versio 10.04, ahir vaig actualitzar a la 10.10 i segueix igual.

---

### Post by carlesbm on 2010-10-17
Hola un altre cop

   Ara es per tal de informar que he pogut solucionar el problema per accedir a la xarxa desde els navegador.

   Segons sembla tot el problema estava en la configuració del tallafocs, despres de molt buscar per la xarxa he trobat un web on s'explica que calia configurar el iptables per tal de permetre que samba pugues tenir acces ha fora del sistema.

[http://betatwits.wordpress.com/2009/12/08/arreglando-problema-entre-samba-y-firestarter/](http://betatwits.wordpress.com/2009/12/08/arreglando-problema-entre-samba-y-firestarter/)

Esperoq ue ha vosaltres tambe se us pugui solucionar. Ara tindre que configurar tot el firestarter, però aixó ja es un altre tema.

---

### Post by akyra on 2010-10-18
A mi m'ha pasat quelcom semblant en cada versió d'ubuntu, a mi em pasava amb el disc dur  multimedia que tenia a la xarxa, i jo no tenia activat el tallafocs.
Després de donar voltes i buscar a altres forums donaven una solució que a mi no m'ha funcionat però a altres sí, un deixo l'enllaç per si de cas:
[http://ubuntuforums.org/archive/inde...t-1166093.html]("http://ubuntuforums.org/archive/inde...t-1166093.html")

Jo aconseguia que em funciones de forma molt tonta però que em funcionava, arrancava l'ordinador amb el windows, em connectava al disc i després quan tornava a arrecar l'ubuntu em tornava a funcionar.
Aquesta darrera vegada em va pasar amb la versió 10.04 d'Ubuntu, però després d'estar funcionant 4 mesos, un dia m'intento connectar al disc dur que havia estat funcionant una hora abans, però que vaig tancar desendollant-lo de la corrent perquè s'havia quedat penjat, i no em va tornar a funcionar fins al cap de 3 dies, no vaig iniciar el windows ni cap altre cosa.
M'entre em pasava això sí que em podia connectar a la feina per VPN i compartir les carpetes per windows, cosa que em feia deduir que la culpa no era de l'ubuntu.

Heu provat a tornar a arrencar els ordinadors amb windows i tornar a provar?

Una pregunta si feu un "ping" que us surt? Potser "Host unreacheable"?

---

