---
title: "No funciona una pàgina amb arxius de so Quicktime"
date: 2011-06-15
forum: Catalan Team
---

### Post by Numerianus on 2011-06-15
Hola a tothom

Soc coordinador d'informàtica d'un IES i tinc a càrrec prop de 100 PC's i fart de perdre temps amb Windows he possat Ubuntu a gairabé tot arreu.

El resultat és força bo. Però m'he trobat recentment amb un curiós problema. 

En aquesta pàgina d'idiomes [http://www.languageguide.org/](http://www.languageguide.org/) no s'activa el so quan et poses a sobre d'una paraula. Hauria de respondre al event MouseOver i es limita a reproduirme l'arxiu de so.

A Windows desprès d'instal.lar el quicktime tot va bé. També funciona i sense instal.lar res al Lucid Puppy que és que més m'alucina de tot..

Però a Ubuntu amb Firefox, Chrome o Seamonkey no funciona amb cap plugin ni amb cap ordinador. El Xine que és el recomenat de sèrie no funciona. I la resta de plugins que he provat tampoc. Estic una mica perdut.

Trampejo amb Wine i Ies2Linux i Quictime o VirtualBox però no hi ha res directe?

Gràcies per endevant

---

### Post by wgarcia on 2011-06-15
Jo ho he provat amb el meu Ubuntu 11.04, Firefox 4.0.1, i funciona perfectament, i no tinc instal·lat cap plugin especial al Firefox. 

Tens instal·lat tot allò d' "ubuntu-extras" i "medibuntu" ?

---

### Post by Numerianus on 2011-06-15
Hola,

Sí ,es clar que tinc tots els restricted, medibuntus etc. Pensa que hem de veure pelis, youtubes , googleearth, fer servir java, etc,etc.

Jo tinc instalada la Lucid però amb la Natty també recordo tenir problemes. Sempre quan alguna cosa no funciona és actualitzar i aquí res. També tinc gran varietat de màquines i, si bé no ho he provat a totes, si en algunes.

Estas segur que la pàgina et funciona completament?. Quan entres a qualsevol de les activitats t'has de poder posar a sobre de la paraula encerclada i en aquell moment, i sense fer cap click, es a dir responent només a un MouseOver, s'ha de sentir el nom de la paraula. Això és lo que a mi em falla. I només a Ubuntu, com ja comento amb Lucid Puppy o XP va perfecte.

Gràcies per la resposta

---

### Post by wgarcia on 2011-06-16
Sí, a mi em funciona perfectament, ho he provat al sobretaula a la feina i ara amb el portàtil, tenen arquitectures molt diferents però els dos estan amb l'Ubuntu 11.04 amb la versió de Firefox actualitzada que porta per defecte, i als dos funciona perfectament, quan poso el ratolí a sobre sense clicar ni res em llegeix el que hi ha (ho he provat amb l'alfabet, i perfecte). 

El Firefox i el Seamonkey fan servir el mateix arxiu de configuració, em sembla, i per tant les coses solen fallar als dos. Però si fallen també al Chrome és un altre cantar. Una cosa tonta per provar, que no crec que sigui el teu problema, és assegurar-se que a Edita -> Preferències -> Contingut estigui marcat "Habilita Javascript".

---

### Post by Numerianus on 2011-06-16
Doncs em deixes una mica frustrat.

És la única cosa que no m'ha funcionat en prop de dos anys. Ho tornaré a provar amb la 11.04, que és la única diferència així d'entrada que tinc amb lo teu.El que pasa que intento tirar de LTS, perquè sinò és massa actualitzar.

Amb la Natty ho vaig prova sense èxit però amb un pc de prop de 10 anys i dic jo si no serà per això. Provaré amb un de més nou.

Gràcies per la molèstia

---

### Post by wgarcia on 2011-06-16
Per a un desplegament de tants ordinadors penso que la LTS és millor, la 11.04 incorpora massa coses noves i no sé si et convindrà per a un desplegament tan gran.

Tens habilitat els dipòsits "backport"? Això et pot actualitzar alguns paquets a la 10.04.

---

### Post by Numerianus on 2011-06-17
Dipòsit "backports" ? Amb aquest nom no ho tenia present però l'he localitzat a 'Fonts de Programari'. Encara que no he fet el que diu aquí [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports), a casa el tinc activat, a la feina no. I després de desinstal.lar plugins una mica raros que tenia al Mozilla _ara va i em funciona _la pàgina de marras.

Igual els 'backports' són la clau. Si no venen activats de sèrie, que no em sona, només el tinc activat a casa. I en alguna d'aquestes actualitzacions se m'arreglat.A veure ara a la feina si puc fer el mateix. Tot i que no és un cas d'emergència sí era una 'espinita'

Com dius tu, una LTS és el que haig de fer anar. Les altres, alguna poso per curiositat, però poc més.

En qualsevol cas quan feia servir XP els meus problemes no eren aquestes xorradetes, sinò bastant més primaris. ("No arranca", "Que va molt lent",...) a més de la dependència total del DeepFreeze.Qué tiempos! i que no tornin pas.

---

### Post by wgarcia on 2011-06-17
A més que tecnològicament Linux pugui ser superior, cosa que no necessàriament serà sempre i en tot moment així, el que sí és imbatible és que si trobes un problema pots, amb una mica de bellugadissa, acabar interactuant amb els desenvolupadors per arreglar-ho!

A més de totes les altres llibertats que implica, òbviament.

---

### Post by Numerianus on 2011-06-21
Al final, he pogut comprovar que màquines a la última a les quals vaig haver de posar la Natty perquè sinò no funcionava el so amb la Luid, aquesta pàgina funciona perfectament. Podria haver començat per aquí, però un ordinador vell amb Natty no funcioanva i no vaig mirar més. No doy para más.

Només em falta provar la Lucid amb els backports.

I si no és ara serà a l'abril de 2012 quan actualitzi a la nova LTS. Això si no passo a la Natty, que espero no haver de fer.

Gràcies per tot un altre cop.

En quan a que Linux és superior, en molts aspectes sí. Desgraciadament no en marketing. El canvi només es produirà si Android dona el salt al PC. I una multinacional pot amb una altra.

---

### Post by wgarcia on 2011-06-21
El tema que engegues dóna per a molt. Més que el marketing, penso que la clau és que permeti models de negoci viables. Això depèn òbviament molt de la base instal·lada.

Android n'és un bon exemple, tot i que de Linux té el nucli i si mires l'estructura de fitxers costa reconèixer el de qualsevol altra distribució. Però el Android Market funciona.  

Per cert al Centre de Programari Ubuntu ja hi ha alguns jocs que es poden comprar, crec que la idea és semblant.

---

