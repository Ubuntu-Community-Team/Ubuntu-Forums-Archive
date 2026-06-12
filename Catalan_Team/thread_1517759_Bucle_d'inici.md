---
title: "Bucle d'inici"
date: 2010-06-25
forum: Catalan Team
---

### Post by ladisse on 2010-06-25
Avui mateix he fet una mica de neteja... i potser he netejat massa paquets (principalment de jocs: KHangMann, Pixfraogger, Pengupop, F-spot, avidemux i evolution). Abans de tancar-lo, hi tenia connectat el disc dur extern connectat, també. La qüestió és que després, al cap d'un parell d'hores he volgut tornar a engegar l'ordinador i aquest ha entrat en una espècie de bucle que no hi ha manera de treure'l... sinó és amb un live. Total, que la única manera que el pc funcioni una mica bé és amb el cd live. Algú em pot orientar com me'n puc sortir d'aquesta? MOltes gràcies a tots!!

Més detalls: 

a la pantalla d'inici, primer és la violeta de la versió 10.04; més tard, em demana amb quin usuari vull entrar i, finalment surt un terminal (la qual cosa, no sé quina ordre donar pq no hi entenc. Sóc primerenca...).

---

### Post by kimet on 2010-06-26
Possiblement al desinstal·lar algun d'aquets paquets ha arrossegat alguna dependència important, dels paquets que dius podria ser evolution el culpable.
 
Prova a tornar a instal.ar evolution.
Al terminal que et surt:
```
sudo aptitude install evolution
```

Si no resulta, i no recordes els paquets que has desinstal.lat en pots tenir una idea consultant els logs:
```
sudo cat /var/log/apt/term.log | tail -n 100 | less
```
Per veure les ultimes 100 linies.

Bon dia.

---

### Post by ladisse on 2010-06-26
Gràcies Kimet. Al llegir la teva resposta, ja havia solucionat una gran part del problema d'una manera més... tradicional? el que he fet, ha sigut amb el cd-live he fet una còpia de seguretat del què he pogut (pq no m'ha permès entrar/copiar alguns dels arxius que tenia) i reinstal·lar la versió 10.04. Potser no ha sigut la millor solució, la veritat, però és com ho he sabut fer. 
De totes maneres, et dono les gràcies i prenc nota per una altra vegada... pq coneixo la màquina que tinc i sé que de tant en tant em fa fer coses rares.

---

