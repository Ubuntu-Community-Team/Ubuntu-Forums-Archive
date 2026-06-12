---
title: "Problemes amb la BIOS"
date: 2009-02-19
forum: Catalan Team
---

### Post by ibea on 2009-02-19
Acabo d'instal·lar-me l'ubuntu 8.10 en un disc dur extern. He provat d'arrencar-lo en d'altres ordinadors i funciona, per tant sé que la instal·lació està ben feta i el GRUB rutlla correctament. 
El problema és amb el meu, que no em vol arrencar des de l'USB. He configurat la bios perquè hi arrenqui (HDD USB com a primera opció) i de fet, el detecta, però no hi vol arrancar.

Algú em sabria donar alguna solució?
Gràcies

---

### Post by RainCT on 2009-02-19
Si no ens dones més informació, no.

Quina BIOS és? Quin disc dur és? Et dóna algun error?

---

### Post by ibea on 2009-02-19
La Bios és una NVDIA TNT2 Model 64 versió 3.05.00.10.00
(C) 1996-2000
i el disc dur extern és un IOMEGA de 500Gb. És nou de trinca.

No dóna cap error. Al disc dur intern hi ha el Windows XP i sempre arranca el Windows, posi el que posi a la Bios. Si el desconnecto no arrenca res; diu que no troba res per arrencar.

---

### Post by papapep on 2009-02-19
Has provat a canviar de port USB?

---

### Post by ibea on 2009-02-19
Sí, però tampoc funciona.

---

### Post by papapep on 2009-02-19
Doncs, sense tenir més pistes, té tot l'aspecte de que falti per configurar alguna cosa a la bios per a poder arrencar des dels ports USB, a més del que ja has modificat.

---

### Post by torracastanyes on 2009-02-19
Mira si a la teva BIOS hi ha res semblat a :
USB Legacy Support=Enabled


(Per cert, diría que la NVIDIA TNT2 mod.64 és una tarja gràfica)

---

### Post by indiosincracia on 2009-02-27
Prova smart boot manager

---

