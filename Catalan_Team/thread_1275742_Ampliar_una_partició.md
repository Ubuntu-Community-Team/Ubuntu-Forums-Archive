---
title: "Ampliar una partició"
date: 2009-09-26
forum: Catalan Team
---

### Post by LitusMayol on 2009-09-26
Ei familia!

Tinc dues particions en un portàtil. Una de prop de 40Gb i l'altre de 2,5Gb. La de 40 té el seu SO i les seves dades(que no vull perdre), i la de 2,5Gb està buida.

Amb una Live intento ampliar la partició de 40Gb fins que ocupi tot. Però el GParted em dona errors. Aquest és el document "*gparted_details*" que puc desar com a informe dels errors.


```
<!DOCTYPE html PUBLIC '-//W3C//DTD XHTML 1.0 Transitional//EN' 'http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd'>
<html xmlns='http://www.w3.org/1999/xhtml' xml:lang='ca-ES' lang='ca-ES'>
<head>
<meta http-equiv='Content-Type' content='text/html;charset=utf-8' />
<title>GParted Details</title>
</head>
<body>
<p>GParted 0.4.3</p>
<p>Libparted 1.8.8</p>
<table border='0'>
<tr>
<td colspan='2'>
<b>Grow /dev/sda1 from 53.39 GiB to 55.89 GiB</b>&nbsp;&nbsp;00:00:32&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
calibrate /dev/sda1&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>path: /dev/sda1<br />start: 63<br />end: 111973049<br />size: 111972987 (53.39 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
calculate new size and position of /dev/sda1&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>requested start: 63<br />requested end: 117210239<br />requested size: 117210177 (55.89 GiB)</i>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
<i>new start: 63<br />new end: 117210239<br />new size: 117210177 (55.89 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
check file system on /dev/sda1 for errors and (if possible) fix them&nbsp;&nbsp;00:00:32&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<b><i>ntfsresize -P -i -f -v /dev/sda1</i></b>
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
```


Alguna idea?
Merciii!

---

### Post by orestesmas on 2009-09-27
Costa una mica de seguir l'XML aquest, però sembla que la partició de 40GB és NTFS i hi detecta un error que li impedeix seguir. Abans de continuar hauràs de reparar l'error probablement executant un algun programa des del propi windows o bé el ntfsfix des de Linux (inclòs en el paquet ntfsprogs). Com que jo no uso windows, en aquest cas no tinc experiència, ni idea de si això ho farà bé i sense perdre dades.

Per tal d'assegurar el tret, si realment ho necessites molt, jo faria el següent:

[LIST=1]
[*]Copiar totes les dades de la partició NTFS a un disc extern.
[*]Reparticionar i reformatejar el disc amb una sola partició que ho ocupi tot
[*]Tornar a bolcar les dades
[*]Arreglar l'arrencada del windows
[/LIST]

No sé si aquest error que et dóna és una mala interpretació del programa Linux que testeja el sistema de fitxers NTFS, o bé és realment un error del disc. En aquest darrer cas pot ser que s'arregli tornant a formatejar la partició, però també pot ser que el disc estigui físicament danyat per la qual cosa no estaria de més evaluar la possibilitat de comprar-te un disc nou.

---

