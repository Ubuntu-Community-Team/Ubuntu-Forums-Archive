---
title: "temperatures a l'ordinador"
date: 2007-06-04
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-06-04
Vaig instal·lar el GKrellM però només em deia la temperatura de la gràfica Nvidia. He anat buscant pel google i això i m'he trobat com fer perquè també em digui la de la CPU, els voltatges i la velocitat del ventilador. I s'ha de configurar no sé que de sensor, vaja que ja va.
Més avall poso la captura...
Doncs bé, ara ja ho veig tot, el ventilador gira a 1300 o així. La gràfica normalment està a 63 graus.. i puja fins els 80 si faig anar el 3D a tope, és normal?

I bé, ara resulta que tinc tres coses més que mesuren. Aaahh, i a més del GkrellM també he posat xsensor.
Doncs tinc una temp1 (que puja i baixa moderadament; i que l'xsensor em te tota l'estona amb roig i la marca com a M/B temp), una temp2 (que no gairebé no es mou mai massa i és molt estable)i una temp3 que pot anar des de 20 graus centígrads fins a 55 graus.. Això no ho he provat massa estona, però és el que veig.

Aquí van les preguntes:
- Les temperatures són normals i correctes?
- A que fa referència cada temperatura? (processador = CPU, no?, temperatura de la caixa, de la placa, etcc)

LA CAPTURA --> [http://racocatala.cat/bikerbaixcamp/temperatures.png]("http://racocatala.cat/bikerbaixcamp/temperatures.png")

Gràcies!

---

### Post by bikerbaixcamp on 2007-06-05
A veure, segur que algú ho sap... ;)

Visca l'Ubuntu!

---

### Post by crazyserver on 2007-06-05
CPU: Processador
M/B: Mother Board /Placa Base
Temp3 no ho se i jo també la tinc... a més sempre em va de 10 a 20 graus... dec tenir pinguins i tot!XD (potser es la temperatura d'en tux.. XD es broma)


LEs temperatures que dius son completament normals, el que mes cal vigilar es la cpu (fins a 60º jo ho considero normal, pero tot depen de quin processador sigui)

---

### Post by bikerbaixcamp on 2007-06-05
> **crazyserver said:**
> CPU: Processador
M/B: Mother Board /Placa Base
Temp3 no ho se i jo també la tinc... a més sempre em va de 10 a 20 graus... dec tenir pinguins i tot!XD (potser es la temperatura d'en tux.. XD es broma)


LEs temperatures que dius son completament normals, el que mes cal vigilar es la cpu (fins a 60º jo ho considero normal, pero tot depen de quin processador sigui)

;)

Tinc un Dual Core a 2.13 Mhz. I de targeta gràfica una Nvidia 7300 GT.

Així que 50 graus la CPU correcte. Si, això del temp 3 pot anar dels 18 graus als 40 i va pujant i baixant de cop a lo bèstia.. I per la gràfica és normal que es posi a 75 o 80 amb tota tranquiliat fent anar vídeos o jocs? En l'estat normal està a 65 graus.

Salut!

---

### Post by Tomàs M. on 2007-06-06
Ei, podeu explicar una mica més què heu instal·lat exactament i com? Jo fa dies que tinc pendent de mirar [http://www.guia-ubuntu.org/index.php?title=Monitorizar_temperaturas_de_hardware](http://www.guia-ubuntu.org/index.php?title=Monitorizar_temperaturas_de_hardware) , però a més m'agradaria poder canviar la velocitat del ventilador, perquè vagi més lent quan no faci falta més velocitat. Es pot fer?

Gràcies!

---

### Post by Tomàs M. on 2007-06-11
> **Tomàs M. said:**
> Ei, podeu explicar una mica més què heu instal·lat exactament i com? Jo fa dies que tinc pendent de mirar [http://www.guia-ubuntu.org/index.php?title=Monitorizar_temperaturas_de_hardware](http://www.guia-ubuntu.org/index.php?title=Monitorizar_temperaturas_de_hardware) , però a més m'agradaria poder canviar la velocitat del ventilador, perquè vagi més lent quan no faci falta més velocitat. Es pot fer?

Gràcies!

Bé, he trobat això: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29)

---

### Post by Druiling on 2007-11-22
Hola tots.
Un dels problemes que vaig deixar de tenir quan vaig fer les particions i instal.lar Ubuntu, va ser que vaig deixar de sentir el ventilador del portàtil cada dos per tres amb aquell escàndol que feia com si s'anés a incendiar.
En els darrers dies, estic tornant a sentir-lo i em preocupa. El tema és que m'he instal.lat unes aplicacions a les quals no sóc capaç de veure la utilitat en aquest sentit.Són aquestes:
XSensor, Xfce 4 Task Manager, GKrellM, Hardinfo, Sisynfo.
Diria, pel que he pogut entendre, que no totes elles serveixen exactament per això que vull que és saber com estem de temperatura, però no m'aclareixo.
A banda, he mirat els links que poseu i encara m'envolico més.
Algú pot il.luminar-me? Començo a estar preocupada amb això. He detectat que em passa des que em vaig instal.lar una aplicació per desar al disc vídeos del Youtube (Youplayer), i no passa necessàriament quan descarrego vídeos, sinó en moltes més ocasions.
Gràcies.
D.

---

### Post by CarlesOriol on 2007-11-23
Inicia el monitor del sistema ( o top en consola ) per veure quins processos "xupen" més.

---

### Post by lluisalguero on 2007-11-26
jo es que tampoc m'en surto, tot i després de seguir els manuals que heu ficat.
Té algo a veure que sigui un portàtil clònic?

---

### Post by Druiling on 2007-11-26
Hola, he fet allò del top a la consola i adjunto un pdf amb el que sortia, que per cert, anava canviant de tant en tant.
Gràcies.

---

### Post by CarlesOriol on 2007-11-26
Jo no hi veig cap problema.

Comprova que les entrades/sortides d'aire del portàtil estiguin netes (bufant i un cop d'aspiradora).

Afegeixte al quadre superior(o inferior) el monitor del sistema per veure l'activitat quan s'escalfi (butó dret afegeix al quadre).

Un cop tinguis el monitor d'activitat pots veure en qualsevol moment els procesos actius fent dobleclic damunt d'ell.

---

### Post by Druiling on 2007-11-26
D'acord.
Dues preguntes:
Un cop veig els processos actius, com faig si hi ha alguna cosa que vull parar?, de fet no és aquesta la pregunta, però puc esguerrar alguna altra cosa que no sigui la que aturo voluntàriament?
I la segona, teniu idea d'alguna aplicació que em permeti veure la temperatura en tot moment? Ho demano perquè he provat d'instal.lar els Im sensors tant des del synaptic com amb les instruccions que donen en aquest enllaç : 
[http://www.guia-ubuntu.org/index.php?title=Monitorizar_temperaturas_de_hardware]("http://www.guia-ubuntu.org/index.php?title=Monitorizar_temperaturas_de_hardware")
i no me n'he sortit, tot i que ho he fet tres cops, els gDesklets no funcionen correctament (a més ara ja no els puc intentar configurar, no sé què dec haver fet).
En fi, gràcies.:confused:

---

### Post by CarlesOriol on 2007-11-27
Fem-ho a l'estil papapep :

cat /proc/acpi/thermal_zone/TZ00/temperature 

o

cat /proc/acpi/thermal_zone/TZ01/temperature

---

### Post by Druiling on 2007-11-27
Hola.
Em surt això:
No such file or directory
Salut.

---

### Post by papapep on 2007-11-27
Doncs ves fent **cd** (change directory) fins arribar a dins **acpi**, mira quins subdirectoris hi ha dins, fins que trobis algun fitxer que es digui temperature o alguna cosa similar. Aleshores fes el **cat** d'aquest.

Per exemple, a un dels meus servidors ho tinc a:

```
debian:/proc/acpi/thermal_zone/THRM# cat temperature
temperature:             39 C

```

---

### Post by Druiling on 2007-11-27
Sentint-ho molt, no entenc què haig de fer. Seria molta molèstia que m'ho diguéssiu pas a pas?, no sé on haig de ficar cd ni quan. He provat de diverses maneres però deu ser això, que no entenc què haig de fer.
Gràcies.

---

### Post by papapep on 2007-11-27
T'hauries de llegir el [tutorial de l'intèrpret d'ordres]("https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes#head-8c12f0ae1263fc5cc5313599bc2fd93f08d97bee") per a no quedar-te clavada amb temes simples d'aquests.

Doncs has de fer això:

```
cd /proc/acpi
```

i a veure què hi ha dins:

```
ls -la
```

i depenent del que hi ha, hauries de fer cd a algun altre directori (suposem que n'hi hagués un que es digúes temperature):

```
cd temperature
```

---

### Post by Druiling on 2007-11-27
Vinga doncs! Llegirem i n'aprendrem. 
Gràcies per la vostra paciència a tots plegats :) 
Ja us diré què.
Salut!

---

### Post by papapep on 2007-11-27
un truquet que va molt bé per a no haver de "picar" tota la lletra en moure't pels directoris:

Si, per exemple, vols passar de /proc/acpi a /proc/acpi/temperature, no cal que piquis tota la paraula temperature. Si fiques:

```
cd tem
```

i prems la tecla **tabulador**, et completarà la paraula ella sola en veure que existeix un directori que comença pel que tu has escrit.

Si ni hagués més d'un que comencés per temp, et mostrarà les opcions que tens per a que tu triis.

Amb això, fa que moure't per l'estructura de directoris pel terminal sigui gairebé més ràpid que fer-ho per l'entorn gràfic ;-)

Exemple:

Soc a /usr i vull anar a /usr/local:

```
debian:/usr# cd lo
```

Premo tabulador i m'apareix:

```
debian:/usr# cd local/

```

Però si, en canvi, només poso:

```
debian:/usr# cd l

```

i premo tabulador **dos cops**:

```
debian:/usr# cd l
lib/   local/
debian:/usr# cd l

```

Em mostra que n'hi ha dos que comencen per l, lib i local.

Aleshores només cal posar o una i o una o darrera la l i prèmer tabulador de nou.

PD UUUiiiiiii, veig que acabo de caure al costat fosc d'en Carles....m'he sortit de tema :-)

---

### Post by Druiling on 2007-12-02
Hola tots, aquí hi veieu alguna cosa?

maria@maria-laptop:~$ cd /proc/acpi
maria@maria-laptop:/proc/acpi$ ls -la
total 0
dr-xr-xr-x  14 root root 0 2007-12-02 16:15 .
dr-xr-xr-x 156 root root 0 2007-12-02 17:14 ..
dr-xr-xr-x   3 root root 0 2007-12-02 18:08 ac_adapter
-rw-r--r--   1 root root 0 2007-12-02 18:08 alarm
dr-xr-xr-x   2 root root 0 2007-12-02 18:08 asus
dr-xr-xr-x   3 root root 0 2007-12-02 18:08 battery
dr-xr-xr-x   5 root root 0 2007-12-02 18:08 button
-r--------   1 root root 0 2007-12-02 18:08 dsdt
dr-xr-xr-x   3 root root 0 2007-12-02 18:08 embedded_controller
-r--------   1 root root 0 2007-12-02 16:15 event
-r--------   1 root root 0 2007-12-02 18:08 fadt
dr-xr-xr-x   3 root root 0 2007-12-02 18:08 fan
-r--r--r--   1 root root 0 2007-12-02 18:08 info
dr-xr-xr-x   3 root root 0 2007-12-02 18:08 power_resource
dr-xr-xr-x   3 root root 0 2007-12-02 18:08 processor
-rw-r--r--   1 root root 0 2007-12-02 18:08 sleep
dr-xr-xr-x   2 root root 0 2007-12-02 18:08 sony
dr-xr-xr-x   3 root root 0 2007-12-02 18:08 thermal_zone
dr-xr-xr-x   4 root root 0 2007-12-02 18:08 video
-rw-r--r--   1 root root 0 2007-12-02 18:08 wakeup
dr-xr-xr-x   2 root root 0 2007-12-02 18:08 wmi
maria@maria-laptop:/proc/acpi$ cd thermal_zone

Perquè jo no. jajaja...
D.

---

### Post by papapep on 2007-12-02
El directori aquest on has entrat (thermal_zone) hauria de tenir algun fitxer dins:

```
ls -la
```

Un cop vegis quins fitxers hi ha, pots veure el seu contingut fent:

```
cat nom_del_fitxer
```

---

### Post by Druiling on 2007-12-02
Ara es veu, però igualment no veig la temperatura:

maria@maria-laptop:/proc/acpi$ ls -la
total 0
dr-xr-xr-x  14 root root 0 2007-12-02 16:15 .
dr-xr-xr-x 163 root root 0 2007-12-02 17:14 ..
dr-xr-xr-x   3 root root 0 2007-12-02 18:40 ac_adapte
r
-rw-r--r--   1 root root 0 2007-12-02 18:40 alarm
dr-xr-xr-x   2 root root 0 2007-12-02 18:40 asus
dr-xr-xr-x   3 root root 0 2007-12-02 18:40 battery
dr-xr-xr-x   5 root root 0 2007-12-02 18:40 button
-r--------   1 root root 0 2007-12-02 18:40 dsdt
dr-xr-xr-x   3 root root 0 2007-12-02 18:40 embedded_
controller
-r--------   1 root root 0 2007-12-02 16:15 event
-r--------   1 root root 0 2007-12-02 18:40 fadt
dr-xr-xr-x   3 root root 0 2007-12-02 18:40 fan
-r--r--r--   1 root root 0 2007-12-02 18:40 info
dr-xr-xr-x   3 root root 0 2007-12-02 18:40 power_res             ource
dr-xr-xr-x   3 root root 0 2007-12-02 18:40 processor
-rw-r--r--   1 root root 0 2007-12-02 18:40 sleep
dr-xr-xr-x   2 root root 0 2007-12-02 18:40 sony
dr-xr-xr-x   3 root root 0 2007-12-02 18:40 thermal_z             one
dr-xr-xr-x   4 root root 0 2007-12-02 18:40 video
-rw-r--r--   1 root root 0 2007-12-02 18:40 wakeup
dr-xr-xr-x   2 root root 0 2007-12-02 18:40 wmi
maria@maria-laptop:/proc/acpi$ cd thermal_zone ls -la
maria@maria-laptop:/proc/acpi/thermal_zone$ ls -la
total 0
dr-xr-xr-x  3 root root 0 2007-12-02 18:40 .
dr-xr-xr-x 14 root root 0 2007-12-02 16:15 ..
dr-xr-xr-x  2 root root 0 2007-12-02 18:40 THRM
maria@maria-laptop:/proc/acpi/thermal_zone$ cat THRM
cat: THRM: Is a directory
maria@maria-laptop:/proc/acpi/thermal_zone$
maria@maria-laptop:/proc/acpi/thermal_zone$

D.

---

### Post by papapep on 2007-12-02
> maria@maria-laptop:/proc/acpi/thermal_zone$ ls -la
total 0
dr-xr-xr-x 3 root root 0 2007-12-02 18:40 .
dr-xr-xr-x 14 root root 0 2007-12-02 16:15 ..
[COLOR="Red"]**d**[/COLOR]r-xr-xr-x 2 root root 0 2007-12-02 18:40 THRM

Fixa't en la primera lletra de la línia. Si és una [COLOR="Red"]**d**[/COLOR] significa que és un directori, no un fitxer.

Així doncs, cal que hi entris amb:

```
cd THRM
```

miris dins què hi ha, i en funció del que hi hagi facis el que ja t'he explicat.

---

### Post by Druiling on 2007-12-02
Després de fer el burro una estona, a la fi i gràcies a la incommensurable saviesa d'en Josep, taxannnn:

maria@maria-laptop:/proc/acpi$ ls -la
total 0
dr-xr-xr-x  14 root root 0 2007-12-02 16:15 .
dr-xr-xr-x 159 root root 0 2007-12-02 17:14 ..
dr-xr-xr-x   3 root root 0 2007-12-02 21:09 ac_adapter
-rw-r--r--   1 root root 0 2007-12-02 21:09 alarm
dr-xr-xr-x   2 root root 0 2007-12-02 21:09 asus
dr-xr-xr-x   3 root root 0 2007-12-02 21:09 battery
dr-xr-xr-x   5 root root 0 2007-12-02 21:09 button
-r--------   1 root root 0 2007-12-02 21:09 dsdt
dr-xr-xr-x   3 root root 0 2007-12-02 21:09 embedded_controller
-r--------   1 root root 0 2007-12-02 16:15 event
-r--------   1 root root 0 2007-12-02 21:09 fadt
dr-xr-xr-x   3 root root 0 2007-12-02 21:09 fan
-r--r--r--   1 root root 0 2007-12-02 21:09 info
dr-xr-xr-x   3 root root 0 2007-12-02 21:09 power_resource
dr-xr-xr-x   3 root root 0 2007-12-02 21:09 processor
-rw-r--r--   1 root root 0 2007-12-02 21:09 sleep
dr-xr-xr-x   2 root root 0 2007-12-02 21:09 sony
dr-xr-xr-x   3 root root 0 2007-12-02 21:09 thermal_zone
dr-xr-xr-x   4 root root 0 2007-12-02 21:09 video
-rw-r--r--   1 root root 0 2007-12-02 21:09 wakeup
dr-xr-xr-x   2 root root 0 2007-12-02 21:09 wmi
maria@maria-laptop:/proc/acpi$ ls -la
total 0
dr-xr-xr-x  14 root root 0 2007-12-02 16:15 .
dr-xr-xr-x 159 root root 0 2007-12-02 17:14 ..
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 ac_adapter
-rw-r--r--   1 root root 0 2007-12-02 21:10 alarm
dr-xr-xr-x   2 root root 0 2007-12-02 21:10 asus
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 battery
dr-xr-xr-x   5 root root 0 2007-12-02 21:10 button
-r--------   1 root root 0 2007-12-02 21:10 dsdt
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 embedded_controller
-r--------   1 root root 0 2007-12-02 16:15 event
-r--------   1 root root 0 2007-12-02 21:10 fadt
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 fan
-r--r--r--   1 root root 0 2007-12-02 21:10 info
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 power_resource
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 processor
-rw-r--r--   1 root root 0 2007-12-02 21:10 sleep
dr-xr-xr-x   2 root root 0 2007-12-02 21:10 sony
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 thermal_zone
dr-xr-xr-x   4 root root 0 2007-12-02 21:10 video
-rw-r--r--   1 root root 0 2007-12-02 21:10 wakeup
dr-xr-xr-x   2 root root 0 2007-12-02 21:10 wmi
maria@maria-laptop:/proc/acpi$ ls -la
total 0
dr-xr-xr-x  14 root root 0 2007-12-02 16:15 .
dr-xr-xr-x 159 root root 0 2007-12-02 17:14 ..
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 ac_adapter
-rw-r--r--   1 root root 0 2007-12-02 21:10 alarm
dr-xr-xr-x   2 root root 0 2007-12-02 21:10 asus
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 battery
dr-xr-xr-x   5 root root 0 2007-12-02 21:10 button
-r--------   1 root root 0 2007-12-02 21:10 dsdt
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 embedded_controller
-r--------   1 root root 0 2007-12-02 16:15 event
-r--------   1 root root 0 2007-12-02 21:10 fadt
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 fan
-r--r--r--   1 root root 0 2007-12-02 21:10 info
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 power_resource
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 processor
-rw-r--r--   1 root root 0 2007-12-02 21:10 sleep
dr-xr-xr-x   2 root root 0 2007-12-02 21:10 sony
dr-xr-xr-x   3 root root 0 2007-12-02 21:10 thermal_zone
dr-xr-xr-x   4 root root 0 2007-12-02 21:10 video
-rw-r--r--   1 root root 0 2007-12-02 21:10 wakeup
dr-xr-xr-x   2 root root 0 2007-12-02 21:10 wmi
maria@maria-laptop:/proc/acpi$ thermal_zone cd THRM
bash: thermal_zone: command not found
maria@maria-laptop:/proc/acpi$ cd THRM
bash: cd: THRM: No such file or directory
maria@maria-laptop:/proc/acpi$ cd thermal_zone THRM
maria@maria-laptop:/proc/acpi/thermal_zone$ cd THRM
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ ls -la
total 0
dr-xr-xr-x 2 root root 0 2007-12-02 21:12 .
dr-xr-xr-x 3 root root 0 2007-12-02 21:12 ..
-rw-r--r-- 1 root root 0 2007-12-02 21:12 cooling_mode
-rw-r--r-- 1 root root 0 2007-12-02 21:12 polling_frequency
-r--r--r-- 1 root root 0 2007-12-02 21:12 state
-r--r--r-- 1 root root 0 2007-12-02 21:12 temperature
-rw-r--r-- 1 root root 0 2007-12-02 21:12 trip_points
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             **43 C**
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ 

Ara que jo trobo que és alta. Puc fer alguna cosa per controlar-la o per què hi hagi alguna cosa que m'avisi?, o no ho emboliquem me&#347;?
Gràcies.
D.

---

### Post by papapep on 2007-12-02
Home! 43 graus és molt per a nosaltres, però no tant pel processador.
Jo, ara mateix, el tinc a 39 graus.
Això també depen de quantes aplicacions hi tens execuntat-se concurrentment, i de si són gaire exigents a nivell de càlcul o tractament de dades.

Respecte el tema de monitoritzar-la, jo ho faria amb algún gdesklet d'aquests (que jo no faig servir). Però si la vigiles un parell de dies, ara que ja saps com mirar-la, i no puja sense més, no m'hi preocuparia massa.

---

### Post by Druiling on 2007-12-02
A mi també em sembla que és molt. Jo abans, amb el Windows, el solia tenir a 35-39 també, i a nivell d'aplicacions, què va, si quan he pres aquesta temperatura tant sols tenia obert el Firefox i l'Evolution, com ara. 
A banda, a mi els deskjets aquests no em funcionen, però faré això que dius i m'ho aniré mirant durant un parell de dies.
Moltes i moltes gràcies, com sempre.
Druiling
---------------------------------------------------------------------------------------------------
**INFORMACIÓ PER A PARDALETS!!**
Per cert, voldria afegir que el que estic fent és el següent:
M'he posat la consola a la barra. Quan s'obre, hi ha una opció "Bookmarks" que és uns favorits. M'he fixat que em desa l'ordre que estic executant i que quan torno a obrir la consola, marco el favorit, em comença tota la línia i jo tant sols haig de picar el final ( cat temperature ). Sóc conscient que potser ja no m'explico, però per si de cas m'explicava més del que veig...
Salut.

---

### Post by Druiling on 2007-12-05
Bé, han passat un parell de dies i no acabo de saber què pot estar passant.

M'ha donat això tot just fa un momentet. Sols tinc obert l'Evolution i el Firefox, res més:

maria@maria-laptop:~$ cd '/proc/acpi/thermal_zone/THRM/'
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             61 C
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             61 C
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             61 C
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             60 C
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             60 C
maria@maria-laptop:/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             60 C

No ho entenc. El ventilador salta, això si (no para, més aviat). Algú té idea què pot ser?. He desinstal.lat el youtube player ja que va ser des de la seva instal.lació, aproximadament, que em passa això, però veig que res.
No sé...
_________________________________________________________________

PD: sabeu que no trobo el post aquell on en Papapep m'indicava com posar SOLVED? Jo hauria dit que era a Thread Tools, però ara no ho veig enlloc:oops:

---

### Post by SiscoGarcia on 2007-12-05
Druling, de la temperatura ni idea, però per posar-hi [SOLVED] és fàcil i ja anaves bé: has d'estar al fil, com ara, ser administradora del fòrum (no és el teu cas, ni el meu) o ser **qui ha obert el fil** (que tampoc no és el cas i per això no et surt l'opció), anar a "Thread Tools" i a baix de tot dir "Mark this Thread as Solved". ;)

---

### Post by Druiling on 2007-12-05
Ahh! D'acord. Gràcies company.

---

### Post by SiscoGarcia on 2007-12-05
De res, per això som aquí, no? Fins una altra!

---

### Post by Druiling on 2007-12-05
):p

---

### Post by Druiling on 2007-12-08
Per cert, he aconseguit configurar els deskjets aquests. Com que no podia ni a la de 3, el que vaig fer, va ser desinstal·lar-los i tornar a instal·lar, de tal manera que ara funcionen perfectament. He comprovat que la temperatura que em dona l'aplicació aquesta és, efectivament, la mateixa que veig en la consola perquè ho he mirat simultàniament, per tant, entenc que, de moment funcionen bé.
Ara, segueixo trobant que la temperatura o bé és massa alta (el valor més baix que m'ha donat és 41 graus), o bé la lectura que feia en windows estava esbiaixada o bé ho està aquesta. No sé.
Salut!

---

