---
title: "[SOLVED] Proble al iniciar l'ubuntu"
date: 2008-12-13
forum: Catalan Team
---

### Post by markinux on 2008-12-13
Hola de nou a tothom.
He estat utilitzant el linux durant les darreres setmanes i no havia tingut cap problema. Però ultimament se'm penja bastant i he de reiniciar l'ordinador.
No sé si és per això però avui, al carregar l'ubuntu m'ha fet un check, però al arribar al 41% m'ha sortit el següent:
[B]Checking drive /de/sda3: 41% (stage 1/5 256/433
i així igual fins arribar al 53%
a sota:
/dev/sda3: inode 2753433 has illegal block(s)
/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.l.) without -a or -p options
checking drive /dev/ sda3: 54% (stage 1/5, 336/433)
fsck died with exitstatus 4
*File system check failed
A log is being saved in / vas/log/fsck/checks i that location is writable. PLease repair the file system manually.
*A maintenance shell will now be started
CONTROL- D will terminate this shell and resume system boot.
bash: no job control in this shell.
root@trias-desktop: #[/B]
Fent el control -d puc engegar l'ordinador, però això que em posa és senyal que hi ha un problema en el sistema no?
Sabeu que he de fer?
Gràcies


Salutacions

---

### Post by quitus on 2008-12-14
Hi ha innumerables fils on s'explica la solució al teu problema, es ben senzill. inicies des de el live cd (si pots desmuntar la partició afectada es pot fer des de el mateix disc dur) i llavors en el terminal vas a la partició afectada i executes l'ordre que t'indica en la informació que t'ha donat "fsck"

salut

---

### Post by markinux on 2008-12-23
He estat buscant pel fòrum fils que parlin sobre això, però no trobu res que m'acabi de convèncer.
Em podrieu especificar una mica més que he de fer amb el meu problema?

GRÀCIES I SALUTACIONS A TOTHOM!

---

### Post by oriolsbd on 2008-12-23
Primer, cal saber quin tipus de FileSystem és (ntfs, ext3, ext2,...). Un cop el sàpigues, engega el PC amb un LiveCD i des de terminal executa:

sudo fsck -t tipus_filesystem /dev/sda3

També ho pots fer des del teu Ubuntu un cop iniciat, però primer hauràs de desmuntar aquesta partició (amb l'error que et dóna no tinc clar si al final t'acaba muntant la partició o no).

---

### Post by trendyguide on 2008-12-23
Organic Farming May Be the Best Route to Global Food Security

---

### Post by markinux on 2008-12-23
Com puc saber el tipus de file system que tinc?

---

### Post by markinux on 2008-12-23
El tipus de file system que tinc és de ext3. Llavors el que he de posar el terminal és: sudo fsck -t ext3_filesystem /dev/sda3   
Ho he fet i l'error no ha desaparegut.
Que faig?

---

### Post by papapep on 2008-12-23
Fent:

```
cat /etc/mtab
```

veuràs els sistemes de fitxers que tens muntats i els seus tipus.

---

### Post by oriolsbd on 2008-12-23
La comanda que has de fer és aquesta:
sudo fsck -t ext3 /dev/sda3 

Salut!

---

### Post by markinux on 2008-12-24
Hola

He creat el terminal que m'heu dit des del live cd i el que m'ha sortit és el següent:

**fsck 1.41.3 (12-Oct-2008 )**

El cas és que el problema encara no està resolt, i pel que he llegit no està recomanat dependre del control -d durant gaire temps.
Després també he provat de fer el fsck -t ext3.... des del meu ubuntu i m'ha dit que això podria danyar greument el meu ordinador.
Faig el fsck des del meu ubuntu ja que des del cd no funciona?

GRÀCIES.

---

### Post by markinux on 2008-12-28
Puc fer la comanda que m'heu dit des del meu ubuntu, encara que em digui que pot danyar greument el meu equip?
Si us plau, respongueu-me com més aviat millor. Ja fa força dies que estic fent el control -D.

GRÀCIES PER LA VOSTRA PACIÈNCIA.

---

### Post by CarlesOriol on 2008-12-28
Pot ser sigui un missatge inútil però abans de fer res has iniciat amb un cd/pen drive i has fet una copia de tot el que tens important a l'ordinador?

---

### Post by markinux on 2008-12-28
Hola
Ja he fet les còpies de seguretat, i estic fent la comanda que meu dit des del meu ubuntu. El que em surt es el següent:
**El node-i 2753537 té blocs no vàlids.  Esborra<s>? **

Li dic que si?

Gràcies

---

### Post by markinux on 2008-12-28
Hola he fet el terminal:
sudo fsck -t ext3 /dev/sda3 des del meu ubuntu i he anat suprimint i arreglant fitxers.
El cas és que quan he acabat el problema al reiniciar l'ordinador segueix igual i l'internet l'he hagut de configurar manualment.
No sé si us servirà de molt ajut, però aquí us deixo al que em surt quan falla el check( que és una mica diferent que abans):
[B]Checking drive/dev/sda 3: 68% (stage 1/5, 421/433
....... 69%
/dev/sda3: Duplicate on bad block in use!
................ 70%
/dev/sda3 MUltiply_clained block(s)in inode: 319529: 12784174
/dev/sda3 (there ara 2 inodes containing in inode multiply clained blocks
/dev/sda3 File... (inode #3195321 mod time Sun DEc 28 23:04:22 2008 
has multiply-clained block (s) shared with 1 file (s)
/dev/sda 3: / trias/ gconf/ system/ networking/connetions/1/conection% conf
/dev/sda3:
7 dev/sda 3UNEXPECTED INCONSISTENCY 
I a partir d'aquí, la resta és igual que sempre.[/B]

Que està passsant i que he de fer? Formatar l'ordinador?


GRÀCIES I PERDÓ SI SÓC PESAT.

---

### Post by markinux on 2008-12-29
No cal que contesteu. Ja he formatejat l'ordinador i ja no tinc el problema.
Per mi, donc el fil per tancat.

Gràcies igualment per la gent que m'ha ajudat.

---

### Post by CarlesOriol on 2008-12-31
Això del bad block, no és un error físic del disc? 

Comprova-ho, ja que si és així tornaras a tenir problemes.

---

