---
title: "&quot;the system is running in low-graphics mode&quot; no arrenca SO"
date: 2017-02-11
forum: Catalan Team
---

### Post by adriarv on 2017-02-11
Bona tarda,

el dijous vaig fer els següents passos sense fer copia de seguretat ni sabent si era correcte del tot (ho sento que estic començant i potser m'he confiat):

 Here's what worked for me:
  
[LIST=1]
[*]Ensure that numlockx is installed:
  sudo apt-get install numlockx

[*]Edit the file /etc/lightdm/lightdm.conf
  gksudo gedit /etc/lightdm/lightdm.conf
[/LIST]
    3 Add the following line to the file:

        greeter-setup-script=/usr/bin/numlockx on

explicat en aquest fòrum [http://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen](http://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen)

des de que reinicio l'ordinador em surten les pantalles que us adjunto. Estrictament no em deixa fer res i lo únic és un control d'errors que 
s'ha passat casi 48 hores fent un "control d'errors" linia per línia i fins que he parat.

Tinc un Asus K541U i una targeta gràfica Nvidia Geforce 920mx. També tinc (o tenia el ubunu 16.04 LTS)

Teniu alguna solució al respecte? Potser amb algun pen drive d'arrenque o alguna cosa així. Pero ara ja vaig més amb cuidado...

Moltes gràcies i espero que d'aquí un temps sigui jo qui pugui ajudar a altres.
[ATTACH=CONFIG]273646[/ATTACH]
[ATTACH=CONFIG]273647[/ATTACH]
[ATTACH=CONFIG]273648[/ATTACH]
[ATTACH=CONFIG]273649[/ATTACH]

---

### Post by wgarcia on 2017-02-13
Jo el primer que intentaria seria eliminar les línies que has afegit al fitxer lightdm.conf. Per això el primer que provaria seria l'opció que mostra a la segona captura de pantalla "Exit to console login". Aquí donaria l'ordre:

```
nano /etc/lightdm/lightdm.conf
```

i a l'editor que s'obre esborraria la línia afegida en qüestió. 

Per sortir d'aquest editor veuràs a sota les opcions, però bàsicament se surt amb "Control X - Control C", et pregunta si vols desar el fitxer modificat i surt.

A veure si hi ha sort, sinó s'haurà d'anar amb l'opció que deies d'iniciar el sistema amb un pendrive d'instal·lació de l'ubuntu en mode de prova, i aquí fer una sèrie de passos per prendre control de la instal·lació que tens.

---

### Post by adriarv on 2017-02-13
He instal.lat un un altre ubuntu al costat i he pogut recuperar els arxius. Gracies per ajudar-me igualment!
no sé com canviar el títol i posar "solved" o borrar el post

---

### Post by wgarcia on 2017-02-13
Per posar "Solved", obres el primer missatge teu i veuràs "Thread tools" a dalt , i aquí una opció per posar "Solved".

---

