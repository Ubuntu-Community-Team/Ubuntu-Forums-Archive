---
title: "compartir arxius entre ubuntus"
date: 2009-01-18
forum: Catalan Team
---

### Post by Turituri on 2009-01-18
Hola
tinc tres ordinadors amb l'ubuntu 8.10, abans tenia el 8.04, un l'he actualitzat i els altres dosa he fet una instal·lació nova. En principi em funciona tot bastant be, però no aconsegueixo fer que es puguin compartir arxius entre ells i que puguin imprimir amb la impressora que tinc des de qualsevol d'ells. Tinc un pc que esta connectat al router i també a la impressora, aquest te com a ip 192.168.2.100, després tinc un altre pc que el tinc via wifi al router i aquest te de ip 192.168.2.101, per últim tinc un portàtil també amb wifi, que te d'ip 192.168.2.102, puc navegar perfectament des de qualsevol d'ells però no puc veure'ls entre ells, porto molts dies llegint per molts fòrums i provant molts manual i coses sense èxit, i al final m'he decidit a escriure aquí. Tinc instal·lat el samba, he creat una carpeta als tres amb el mateix nombre i la tinc compartida per qualsevol usuari, també la impressora la tinc compartida. Quan tenia el ubuntu 8.04, tampoc vaig a aconseguir-ho del tot ja que no podia imprimir directament però si que vaig aconseguir que escrivint al nautilus la ip del ordinador que volia poder entrar es a dir posava al nautilus sftp://192.168.2.100 i entrava al ordinador pc del router i podia copiar o enganxar el que volgués om si fos una carpeta mes, això ara tampoc em funciona. Algú sap els passos que hauria de fer o disposa d'algun manual en català o castellà. Gracies per la vostra ajuda

---

### Post by ggoscarl on 2009-01-19
Hola,

aquest fil et pot ajudar:

[http://ubuntuforums.org/showthread.php?t=635062&highlight=compartir+arxius](http://ubuntuforums.org/showthread.php?t=635062&highlight=compartir+arxius)

---

### Post by Turituri on 2009-01-19
Hola
es just el que buscava i com ho tenia abans, ara puc enviar informació entre ells tres.
D'altre banda com puc fer per imprimir des de els altres 2 ordinadors?
La impressora esta connectada a un d'ells, es possible i fàcil de poder imprimir des de els altres dos?. Gracies per la vostra ajuda

---

### Post by Tomàs M. on 2009-01-20
Jo ho tinc així: sistema - administració - impressió; Nou - impressora; protocol ipp; ordinador: ip del que la té connectada:631; cua: /printers/nom de la impressora - verifica; endavant; aplica.

---

### Post by CarlesOriol on 2009-01-23
(1 preguna 1 fil... o el papapep ens enviarà a l'infern on sols hi ha sistemes privatius i versions de demostració)

A l'ordinador que té connectada la impressora vas a 

**Sistema > Administració > Impresores** (perdoneu si els textos no son justos però estic en un ordinador en italià)

al menú **Server > Configura**

als clients dius que vegin les impresores compartides dels altres sistemes (em sembla que és predeterminat) i al servidor que les comparteixi...

Vas a afegir impresora i ja veuras que ho fa tot solet.

---

### Post by Turituri on 2009-01-27
Gracies, m'ha anat perfecte, ara ja puc enviar coses entre ells, i a mes també imprimir arxius des de els altres ordinadors. Gracies
Perdoneu per no contestar abans es que no ho havia pogut provar

---

