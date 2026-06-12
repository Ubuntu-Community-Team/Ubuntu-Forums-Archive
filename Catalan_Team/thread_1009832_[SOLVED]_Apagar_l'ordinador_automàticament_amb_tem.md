---
title: "[SOLVED] Apagar l'ordinador automàticament amb temporitzador"
date: 2008-12-13
forum: Catalan Team
---

### Post by lo gambusí on 2008-12-13
Hola!

M'agradaria tenir alguna aplicació amb la qual pugués demanar-li a l'ordinador que s'apague sol en X minuts. Teniu idea si existeix? He googlejat una mica i no he trobat res.

Moltes gràcies!

---

### Post by CarlesOriol on 2008-12-13
carles@asusx20sg:~$ shutdown
shutdown: s'esperava una especificació de temps
Proveu «shutdown --help» per a obtenir més informació.
carles@asusx20sg:~$ shutdown --help
Forma d'ús: shutdown [OPCIÓ]... TEMPS [MISSATGE]
Atura el sistema.

Opcions:
  -r                          reboot after shutdown
  -h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)
  -c                          cancel a running shutdown
  -k                          only send warnings, don't shutdown
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

El TEMPS pot tenir formats diferents, el més usual dels quals és la paraula
«now» (ara), la qual provoca una aturada del sistema immediata. Altres
formats vàlids són +m, que especifica el nombre de minuts abans d'iniciar
l'aturada del sistema, o bé hh:mm, que especifica l'hora de l'aturada en el
format de 24 hores.

Abans de l'inici de l'aturada del sistema s'avisen els usuaris connectats per
mitjà d'un missatge enviat als seus terminals (el qual es pot especificar com
a MISSATGE opcional). Els missatges també es poden enviar sense haver d'aturar
el sistema amb l'opció -k.

Si s'especifica el TEMPS, l'ordre d'aturada del sistema roman en el primer pla
fins que l'aturada es produeix. Aquest procés es pot cancel·lar en prémer
Contrl-C o bé per un altre usuari a través de l'opció -c.

Per defecte el sistema entrarà en el mode de manteniment (usuari únic) en
aturar-se, cosa que es pot canviar a través de les opcions -r o -h, a través
de les quls es pot reiniciar o aturar, respectivament. L'opció -h es pot
modificar en especificar -H o -P, amb la qual cosa es pot aturar el sistema
completament o bé desconnectar-li l'energia, respectivament. L'opció per
defecte es prendrà dels scripts d'aturada del sistema.

Informeu dels errors a <upstart-devel@lists.ubuntu.com>

---

### Post by lo gambusí on 2008-12-13
Què gran l'ordre --help O_O

Per tant, si jo a un terminal poso shutdown 01:24 en una hora i 24 minuts se m'apagarà l'ordinador, no? He de mantenir el terminal obert, però?

---

### Post by tanreb20 on 2008-12-13
Nops!

Hauries de posar:

```
sudo shutdown -h 84
``` per a que en una hora i 84 minuts s'apagues.

No se si hi ha manera de posar-li en mode "hores"

Si poses 01:24 t'ho apagara a les 01:24 AM

---

### Post by ernestux on 2008-12-13
Resumint:

sudo shutdown -P 02:30        (per apagar-se a les 2:30 h)

sudo shutdown -c               (per anular l'acció)

---

### Post by lo gambusí on 2008-12-13
Moltes gràcies!

---

### Post by RainCT on 2008-12-14
Si vols una alternative gràfica, prova el **gshutdown** (està als dipòsits).

---

### Post by lo gambusí on 2008-12-16
Moltes gràcies als dos!

---

