---
title: "No es pot montar el volum"
date: 2007-09-25
forum: Catalan Team
---

### Post by prostata on 2007-09-25
Quan introdueix-ho un cd o un dvd, el SO em biu que no es pot montar el volum i per tant no puc accedir.....¿cóm és fa "muntable" ;-) els volums...gràcies

---

### Post by orestesmas on 2007-09-25
Si no pots muntar el volum, pot ser per diverses causes:

1) error de lectura del suport, o bé el suport no és muntable.

2) El teu usuari no té permisos per fer-ho (cal que l'usuari pertanyi al grup "cdrom"). Normalment l'usuari que ha instal·lat el sistema ja petany a aquest grup de forma predeterminada.

3) Altres que ara no se m'acuden.

Jo m'inclino per la primera, passa massa sovint. Per confirmar-ho obre una consola, insereix el CD al lector i posa l'ordre següent (comprova primer que existeixi el dispositiu /dev/cdrom i el directori /media/cdrom0. en el meu sistema estan creats, però en el teu no ho sé...)

sudo mount -t iso9660 /dev/cdrom /media/cdrom0

Si tot va bé, dins el directori /media/cdrom0 veuràs els continguts del CD. Si falla quelcom, et donarà un missatge d'error i aleshores ens dius quin és

---

### Post by prostata on 2007-09-25
> **orestesmas said:**
> Si no pots muntar el volum, pot ser per diverses causes:

1) error de lectura del suport, o bé el suport no és muntable.

2) El teu usuari no té permisos per fer-ho (cal que l'usuari pertanyi al grup "cdrom"). Normalment l'usuari que ha instal·lat el sistema ja petany a aquest grup de forma predeterminada.

3) Altres que ara no se m'acuden.

Jo m'inclino per la primera, passa massa sovint. Per confirmar-ho obre una consola, insereix el CD al lector i posa l'ordre següent (comprova primer que existeixi el dispositiu /dev/cdrom 

**Si, existeix..**

i el directori /media/cdrom0. en el meu sistema estan creats, però en el teu no ho sé...)

sudo mount -t iso9660 /dev/cdrom /media/cdrom0

Si tot va bé, dins el directori /media/cdrom0 

**També existeix, però cdrom0 és totalment vuit..**

veuràs els continguts del CD. Si falla quelcom, et donarà un missatge d'error i aleshores ens dius quin és

Doncs aquest és el missatge:

josep@josep-desktop:~$ sudo mount -t iso9660 /dev/cdrom /media/cdrom0
Password:
mount: dispositivo de bloques /dev/cdrom está protegido contra escritura; se monta como sólo lectura
mount: tipo de sistema de ficheros incorrecto, opción incorrecta,
       superbloque incorrecto en /dev/cdrom, falta la página de códigos,
       o algún otro error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

---

### Post by orestesmas on 2007-09-25
Que el directori /media/cdrom0 estigui buit abans de muntar-hi res és normal. Captes la idea del muntatge? En Unix no hi ha discs C: D: etc. Tot són directoris. Passa el mateix amb gairebé tots els dispositius excepte (per raons històriques i altres que s e m'escapen) amb les interfícies de xarxa.

Quant al missatge d'error... doncs mala sort. Veient això sóc de l'opinió que:

1) O bé el suport està cascat (en la zona crítica del superbloc). Prova amb altres CD.

2) o bé el lector està cascat.

A vegades no cal que el lector estigui cascat al 100%, només que no sigui capaç de seguir correctament les variacions que puguin contenir les pistes d'alguns CD. Pensa que l'amplada d'aquestes pistes és petitíssima, de l'ordre de micres. Qualsevol variació que nosaltres considerem "poca cosa" (temperatura, humitat, torsions mecàniques) pot deformar la forma circular de les pistes fins a fer-les impossibles de seguir. A vegades un CD gravat amb un lector no és llegible en un altre perquè un dels dos està desajustat i treballa fora dels límits de l'especificació.

Buf, quin rotllo m'ha sortit...

---

### Post by prostata on 2007-09-25
> **orestesmas said:**
> Que el directori /media/cdrom0 estigui buit abans de muntar-hi res és normal. Captes la idea del muntatge? En Unix no hi ha discs C: D: etc. Tot són directoris. Passa el mateix amb gairebé tots els dispositius excepte (per raons històriques i altres que s e m'escapen) amb les interfícies de xarxa.

Quant al missatge d'error... doncs mala sort. Veient això sóc de l'opinió que:

1) O bé el suport està cascat (en la zona crítica del superbloc). Prova amb altres CD.

2) o bé el lector està cascat.

A vegades no cal que el lector estigui cascat al 100%, només que no sigui capaç de seguir correctament les variacions que puguin contenir les pistes d'alguns CD. Pensa que l'amplada d'aquestes pistes és petitíssima, de l'ordre de micres. Qualsevol variació que nosaltres considerem "poca cosa" (temperatura, humitat, torsions mecàniques) pot deformar la forma circular de les pistes fins a fer-les impossibles de seguir. A vegades un CD gravat amb un lector no és llegible en un altre perquè un dels dos està desajustat i treballa fora dels límits de l'especificació.

Buf, quin rotllo m'ha sortit...

No que va.....a jo aquestos rotllos m'encanten, o sigui que per mi no et tallis...gràcies, he provat amb altres suports i si funcionen, es dir es monten, pot ser sigui que  el suport DVD, que vull montar, está espatllat, com dius..

---

