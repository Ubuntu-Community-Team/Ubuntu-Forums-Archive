---
title: "[SOLVED] Configuració del Compiz-Fusion al Gutsy Gibbon"
date: 2007-10-13
forum: Catalan Team
---

### Post by Mitjons on 2007-10-13
Bones
Doncs he actulitzat a Gutsy Gibbon i tinc  la gràfica funcionant i el Compiz-Fusion en marxa però no puc configurar-lo. He instal·lat el settings-manager i ara em surt l'opció de custom, però per molt que la trii i li done al nou botó de Preferencies aqui no passa res.:confused:

---

### Post by anigwei on 2007-10-13
Et funciona l'acceleració? Tens Ati o Nvidia?

Suposo que per settings-manager et refereixes al configurador del compiz, si no es aixi, executa'l des de cònsola:

```
$ ccsm
```

Siau

---

### Post by Mitjons on 2007-10-13
Sip, està activada i de fet els efectes estan en "extres" tot i que semblen ven normals i "hohos" com diria el millor cuiner del mon.

CCSM no em funciona, em dona aquest error: AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by Ferri on 2007-10-13
Com ja t'han preguntat, quina tarja gràfica tens?
Si no ho has fet, instal·la't emerald (gestor de temes de compiz-fusion) i engega'l. Fes clic dret damunt la icona i podràs veure realment si tens engegat compiz-fusion o encara estàs a Metacity.
Des de l'Emerald, almenys amb Beryl, també pots configurar les opcions i canviar de tema fàcilment.

---

### Post by Mitjons on 2007-10-13
És NVIDIA i el compizfusion/beryl ha funcionat sempre a antigues versions

I l'Esmerald ara mateix no em deixa intal·lar-lo el Synaptic em diu que hi ha un parell de llibreries que no s'instal·laran i que nanai de la xina

---

### Post by papapep on 2007-10-13
Si ens enganxes el missatge exacte que et dona el synaptic tindrem més pistes.

---

### Post by CarlesOriol on 2007-10-13
> **Mitjons said:**
> És NVIDIA i el compizfusion/beryl ha funcionat sempre a antigues versions

I l'Esmerald ara mateix no em deixa intal·lar-lo el Synaptic em diu que hi ha un parell de llibreries que no s'instal·laran i que nanai de la xina

Heu aquí el problema. En versions anteriors no existia compizfusion, per tant la teva insta&#320;lació es d'una font diferent.

Això pot haver provocat divergencies entre les versions que actualitzaves i la d'ubuntu. Per tant el ccsm no troba les llibreries que requereix.

El millor que pots fer és eliminar tots els paquets de compiz, assegurar-te que no et queda cap repositori al sources.list que et pugui produir l'error i tornar-los a insta&#320;lar tot.

---

### Post by Mitjons on 2007-10-14
Aquest és el missatge d'error al synaptic
[I]emerald:
 Depén: libemeraldengine0 però no s'instal·larà
 Depén: libwnck18 (>=2.15.90) but it is not installable[/I]

Jo només he instal·lat el manager-setting ja que el fusion ve amb Gutsy Gibbon. Si esborro tot el fusion esborrare coses que venen de serie.
La instal·lació del 7.10 va ser completament neta:confused:

---

### Post by Mitjons on 2007-10-14
Solucionat.
Això de les versions que ha dit en Carles m'ha fet rumiar i el Synaptic a l'hora d'instal·lar el setting manager he mirat la versió, anava per davant del propi compizFusion. 
Per aixó per molt que reinstal·les no funcionava.

He forçat el setting manager a la mateixa versió del compiz (synaptic->paquet->forçar versió) i ara si que puc configurar-lo

Merces a tots

---

### Post by klonner on 2007-10-15
a mi em passa algo semblant a tu,vaig instalar-ho i al principi funcionava bé, amb les actualitzacions que hi han hagut ara no fa tots els efectes que feia, nomes es difumina al minimitzar, quan abans tenia les finestres com si fos gelatina, 

com ho has arreglat? quin paquet has forçat? a quina versio??

Gracies

---

### Post by Mitjons on 2007-10-15
Bé de fet a mi no em fallava cap efecte, simplement no tirava el configurador. 
Vaig forçar d'instal·lar la versió 0.5.2 del "compizconfig-settings-manager". Aquesta versió va parell amb la resta del compiz que ve amb el Gutsy. 

Tot i que sembla que la nova que ve després de la 0.5.2 ara per ara només està als supositoris del Treviño

Ara el que no tinc collons de fer anar és el cub!!! ](*,)

---

### Post by papapep on 2007-10-15
> Tot i que sembla que la nova que ve després de la 0.5.2 ara per ara només està als [COLOR="Red"]**supositoris**[/COLOR] del Treviño


Ui!!! Passo, passo!!! No els aguanto, ja em conformo amb el Metacity si haig de passar per això...:-P

---

