---
title: "Error virtualbox"
date: 2010-06-20
forum: Catalan Team
---

### Post by antoniu on 2010-06-20
Quan intento iniciar la màquina virtual de windowsxp em surt un error que diu:
No s'ha pogut obrir una sessió per a la màquina virtual Windows XP.
Virtual machine 'Windows XP' has terminated unexpectedly during startup.

a detalls surt:
Resultat Codi:
NS_ERROR_FAILURE (0x80004005)
Component:
Machine
Interfície:
IMachine {99404f50-dd10-40d3-889b-dd2f79f1e95e}


A la vegada em surt un altre missatge que diu: 
Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

Ahir ja vaig instal·lar virtualbox-ose-dkms package i em va funcionar però avui em torna a sortir aquest problema; he intentat de reinstal·lar el paquet però res; i això de modprobe vboxdrv no sé com fer-ho perquè no sé entrar com a root.

Algú em pot ajudar?

---

### Post by PatrickVogeli on 2010-06-20
sudo /etc/init.d/vboxdrv setup

despres d'aixo en principi t'hauria de funcionar

---

### Post by antoniu on 2010-06-20
No, em diu command not found

---

### Post by wgarcia on 2010-06-21
És possible que instal·lant build-essential, i linux-headers per al nucli que tens, faci que en arrencar el sistema el "dkms" et reconstrueixi el mòdul del nucli per virtualbox. 

Pots trobar i instal·lar "build-essential" al Gestor de Paquets Synaptic (busca "build-essential"), i els linux-headers també (has de mirar quina versió del nucli és la que estàs usant i buscar aquesta versió dins de totes les que te ofereix Synaptic quan busques "linux-headers"). Per veure quina versió del nucli estàs usant, dóna aquesta instrucció a una terminal:

uname -a

---

