---
title: "problemes d'instal·lació..."
date: 2009-10-07
forum: Catalan Team
---

### Post by acoro on 2009-10-07
Hola a tohtom. Soc nou amb això del programari lliure. M'he llegit el missatge aquell que deia que abans de fer una qüestió miressim al fòrum i no he sabut trobar res. La qüestió és la següent:
tinc un ordinador portàtil nou (un toshiba satellite d'aquests moderns). Hem instal·lat el nou bindws 7. Un cop fet això, he posat el cd de l'ubuntu 9.04 de 64 bits. He fet 3 particions (i la del bindous 4). Una per guardar fitxers (on les pugui mirar per linux i bindows) i les dues que et demanen per l'ubuntu (la d'ext 4 i la de swap). El problema arriba quan estic instal·lant-ho tot, no penso en enxufar l'ordinador i puf!! s'acaba la bateria.
Com no, ho torno a provar i de cop em surt un missatge (cap al 38% de l'instal·lació i després que tot anés bé) que em diu que tinc un fallo al cd o al disc dur!!!. Què faig? Dons torno a cremar un cd i el comprovo abans d'instal·lar. Em diu que hi ha un fallo. Què faig?, torno a descarregar-me de la web un altre ubuntu i el torno a cremar. Torno a comprovar-ho i em diu que el cd té un error. Què faig? Ho faig des d'un altre ordinador desconfiant de la gravadora anterior. Què passa? el mateix cada vegada....l'error que em surt és el següent: [Errno5] Input/output error (després parla que això acostuma a ser causat per un disco o lecotr cd/dvd defectuós i bla bla...).
 
Què hauria de fer¿? He llegit en algun fòrum i em diuen que ho formategi tot ja que és possible que el disc dur estigui fet malbé...(i en aquest cas com ho formatego tot habent fet tantes particions¿?amb algun programa en concret??)uf!!!us agraïré molt alguna resposta!!!estic parant una mica boig! Moltes gràcies per abançat!
Albert Corominas i Carles, Banyolí nat!

---

### Post by RafaelCarreras on 2009-10-07
Has provat de tornar a formatar la partició ext4 on fas la instal·lació d'Ubuntu?

---

### Post by acoro on 2009-10-07
> **RafaelCarreras said:**
> Has provat de tornar a formatar la partició ext4 on fas la instal·lació d'Ubuntu?
 sí!!! i res!!!

---

### Post by jaume69 on 2009-10-07
Yo de tu primer instal.laria el SO que tenies original al comprar l´ordinador,si pots..(Fa poc temps al comprar un ordinador nou,tenies que  fer els discs de Recuperació o demanarlos per Internet o alguna botiga,ara no ho sé..)

O,buscar un Live CD Ubuntu en bon estat.

Salut.

---

### Post by papapep on 2009-10-07
> Què faig?, torno a descarregar-me de la web un altre ubuntu i el torno a cremar. Torno a comprovar-ho i em diu que el cd té un error. Què faig?

Jo ho provaria amb una altra marca de CD. Quina fas servir?
"L'altre" sistema operatiu t'arrenca bé?

També podries provar a descarregar la versió alternate([32bits]("http://releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-i386.iso") o [64bits]("http://releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-amd64.iso")), que a vegades té menys problemes instal·lant-se que la Desktop.

---

### Post by quitus on 2009-10-07
Prova amb una memòria flash, com a mínim estalviaràs CD's

Per eliminar qualsevol cosa del disc, des de el live cd "dd if=/dev/urandom of=/dev/hda" canviant "hda" pel nom del teu disc dur, sda o el que sigui.

salut

---

### Post by acoro on 2009-10-08
Hola! moltes gràcies per tot. Finalment m'he descarregat l'alternate i m'ha funcionat. Ho he fet amb un amic informàtic usuari d'ubuntu i la veritat és que ha quedat sorprès...hem buscat per la xarxa i a més gent li ha passat el matix!!! de totes maneres gràcies per tot!!!ara ja puc dir que faig servir programari lliure amb tots els "ets i uts". Salut!
Albert Corominas i Carles

---

