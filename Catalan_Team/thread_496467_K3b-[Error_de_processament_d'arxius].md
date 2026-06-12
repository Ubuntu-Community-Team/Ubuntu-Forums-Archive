---
title: "K3b-[Error de processament d'arxius]"
date: 2007-07-09
forum: Catalan Team
---

### Post by prostata on 2007-07-09
Bon dia:

Tinc un arxiu.avi, però quan el vull processar amb K3b, aquest m'envia un messatge que diu:

"problemes al afegir arxius al projecte. Detall: els arxius no tenen una codificació valida, pot arreglar-lo amb l'eina CONVMV."

He mirat al menú eines però no veig aquesta. Això es la primera vegada que em passa, al voler gravar DVD's en arxius de format.avi.

Teniu alguna idea al respecte? Gràcies

---

### Post by vila-seca on 2007-07-09
Entenc que el problema dels teus fitxers es que segurament estan codificats amb la codificació de caracters ISO i  Ubuntu treballa amb [UTF8]("http://en.wikipedia.org/wiki/UTF-8").

Per això  t'indica que facis servir l'eina per a canviar la codificació. Hauries d'obrir una consola i la sintaxi seria d'aquest tipus:

convmv -f <codificació actual> -t utf-8 <nom del fitxer>
(Canvieu iso-8859-1 pel joc de caràcters del que esteu 
convertint)Fes una còpia de seguretat per si un cas del fitxer. ja diràs el que company

---

