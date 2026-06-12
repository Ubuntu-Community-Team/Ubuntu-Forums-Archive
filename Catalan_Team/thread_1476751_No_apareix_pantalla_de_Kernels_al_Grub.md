---
title: "No apareix pantalla de Kernels al Grub"
date: 2010-05-08
forum: Catalan Team
---

### Post by RicardKp on 2010-05-08
Hola, a tothom,

A l'actaulitzar a lucid m'ha desaparegut el menú d'entrada als diferents kernels, ara si em fallés el kernel amb el que entro normalment no sé què em passaria, no sé si per defecte el grub provaria d'entrar mitjançant el següent kernel, o si es quedaria el grub penjat? Pot ésser que he canviat el maquinari, fa poc vaig instal·lar-ho tot en un Dell Inspiron, mentre abans anava amb un pc de sobretaula.

Algú em pot ajudar per tal que torni a aparèixer el menú de kernels.

Gràcies per endavant,
Ricard

---

### Post by wgarcia on 2010-05-08
Vols dir que quan engegues l'ordinador entra directament a la pantalla d'entrada d'usuari de l'Ubuntu sense oferir-te el menú inicial (el Grub)?

---

### Post by RicardKp on 2010-05-08
> **wgarcia said:**
> Vols dir que quan engegues l'ordinador entra directament a la pantalla d'entrada d'usuari de l'Ubuntu sense oferir-te el menú inicial (el Grub)?

Exacte, tu ho has explicat molt millor que jo, això és el que hem passa.

---

### Post by papapep on 2010-05-08
Quan l'ordinador arrenca, just després de la bios, prement la tecla ESC t'ha d'aparèixer sempre el menú del Grub.

---

### Post by wgarcia on 2010-05-08
Sols tens instal·lat l'Ubuntu 10.04 al teu ordinador? Si és així és normal que vagi directament al login, però es pot canviar perquè ensenyi el grub en començar, però primer confirma si sols tens instal·lat l'Ubuntu 10.04...

---

### Post by RicardKp on 2010-05-08
> **wgarcia said:**
> Sols tens instal·lat l'Ubuntu 10.04 al teu ordinador? Si és així és normal que vagi directament al login, però es pot canviar perquè ensenyi el grub en començar, però primer confirma si sols tens instal·lat l'Ubuntu 10.04...

Sí, sols el 10.04

Gràcies,
Ricard

---

### Post by wgarcia on 2010-05-08
Per veure el menú de grub, pots fer com diu el papapep (esc just després d'arrencar l'ordinador).

Si el vols veure sempre sense fer esc pots canviar la configuració del grub de la manera següent. Obre una terminal de comandes i edita l'arxiu de configuració del grub mitjançant l'ordre següent:

gksudo gedit /etc/default/grub

Has de canviar una línia que posa:

GRUB_HIDDEN_TIMEOUT_QUIET=false

i li has de posar "true", o sigui que al final ha de ser:

GRUB_HIDDEN_TIMEOUT_QUIET=true

Un cop deses l'arxiu, has d'entrar l'ordre següent a la mateixa terminal:

sudo update-grub

A la següent arrencada hauries de veure ja el menú de grub.

---

### Post by RicardKp on 2010-05-09
Ja hi posa true


Us deixo la meva configuració del grub, per si hi veieu alguna cosa estranya.

Gràcies,
Ricard



# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="vga=786"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by wgarcia on 2010-05-09
D'acord, per veure el menú has d'editar l'arxiu i "comentar" la línia:

GRUB_HIDDEN_TIMEOUT=0

és a dir, posar-li un "#" al principi, i s'haurà de veure així:

#GRUB_HIDDEN_TIMEOUT=0

No t'oblidis de fer

sudo update-grub

quan acabis.

Amb això t'hauria de començar el sistema amb el menú de grub.

Quan vinguin actualitzacions del grub aquesta configuració et pot desaparèixer.

---

### Post by RicardKp on 2010-05-09
Ara sí, ja he comentat la línia tal com m'has dit i ja em surt el menú del Grub. Potser sí que triga una mica més en engegar, però sempre he treballat així i m'hi sento més còmode.

Moltes gracies,

Treballar amb la comunitat Ubuntu és magnífic, llàstima que aquesta filosofia no sigui la que regeixi el planeta... 

Ricard

---

### Post by wgarcia on 2010-05-10
Me n'alegro que t'hagi quedat com volies. 

No t'oblidis de canviar el tema del fil a "Solved" amb Thread Tools, així li pot servir a algun usuari futur.

---

