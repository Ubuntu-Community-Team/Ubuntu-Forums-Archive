---
title: "format"
date: 2024-06-16
forum: Catalan Team
---

### Post by josep-maria on 2024-06-16
He volgut formatar una memòria flash, fent servir el gparted, però no l'he pogut trobar. On és?

---

### Post by ffp on 2024-06-16
Doncs instal·la'l: sudo apt install gparted. 
De totes maneres crec que no cal gparted per formatar una memòria flash. Des del nautilus (en la meva distro), botó dret del ratolí sobre la memòria i "formatar"

---

### Post by josep-maria on 2024-06-16
Fet. 
Ara el gparted és a: aplicacions > eines del sistema > gparted
Si hi faig clic, surt una finestreta on hi ha:
/dev/sda1  grub2core.img
/dev/sda2 fat32/boot/efi
/dev/sda3 wxt5/var/sna
No hi diu res de la memòria flash.
He fet una captura de pantalla, però no l'he pogut ficar a aquest text.

---

### Post by josep-maria on 2024-06-16
La finestreta és:  [https://blocs.tinet.cat/tokra/files/2024/06/Captura-de-pantalla-a-2024-06-16-17-46-35.png](https://blocs.tinet.cat/tokra/files/2024/06/Captura-de-pantalla-a-2024-06-16-17-46-35.png)

---

### Post by wgarcia on 2024-06-17
A dalt a la dreta, on posa "/dev/sda", és un desplegable on hauries de trobar els altres dispositius que veu el sistema. Per desplegar-ho, clica sobre el símbol que és com un "v" tot a la dreta.

---

### Post by josep-maria on 2024-06-18
Ara surt això:
[https://blocs.tinet.cat/tokra/files/2024/06/Captura-de-pantalla-a-2024-06-18-17-35-47.png](https://blocs.tinet.cat/tokra/files/2024/06/Captura-de-pantalla-a-2024-06-18-17-35-47.png)
Hi he fet clic amb el botó dret i no em deixa formatar, Si faig clic a partició, puc veure que diu "formata a" però no em deixa fer-hi clic.

---

### Post by ffp on 2024-06-21
Mira de desmuntar el dispositiu abans. Botó dret "desmunta" i després mira de formatar.

---

### Post by josep-maria on 2024-06-22
Ara ja s'ha i&#322;luminat el "formata a". Si hi faig clic, surt una llista on hi diu: ext2, ext3, ext4, fat16, fat32, linux-swap, minix, ntfs. On haig de fer clic?

---

### Post by ffp on 2024-06-23
Si nomes el fas servir per ubuntu ext4, si ha de ser compatible amb altres sistemes fat32

---

### Post by josep-maria on 2024-06-23
Surt això:
[https://blocs.tinet.cat/tokra/files/2024/06/Captura-de-pantalla-a-2024-06-23-17-59-10.png](https://blocs.tinet.cat/tokra/files/2024/06/Captura-de-pantalla-a-2024-06-23-17-59-10.png)

Diu "una operació pendent". He esperat una hora i no avança. Sembla que no faci res.

---

### Post by ffp on 2024-06-23
Has de clicar a la rodona verda per que s'inicii

---

### Post by josep-maria on 2024-06-24
aaah. :P ;)\\:D/ Moltes gràcies

---

