---
title: "Problemes amb llengua predeterminada"
date: 2009-01-22
forum: Catalan Team
---

### Post by enricXIII on 2009-01-22
Bones!

Us explico. De cop i volta em trobo el meu Ubuntu (Hardy) mig en català i mig en anglès.. i m'ha trucat un company de feina a qui vaig instal.lar fa temps també la Hardy però en castellà, dient-me que perquè li surten de cop i volta els programes en anglès. Podeu imaginar-vos la cara de "pamfilu" que se m'ha quedat? :mrgreen::mrgreen:
He buscat per sant google i no trobo res anormal, sembla ser que ho tinc tot be..només em queda pensar que hagi estat per alguna actualització que no rutlli be ja que últimament n'han entrat forces.

Alguna idea de que pot estar passant? algú s'ha trobat amb quelcom semblant?
Gràcies i salut!

---

### Post by oriolsbd on 2009-01-22
Escriu el resultat de la comanda:
```
locale
```

Salut!

---

### Post by enricXIII on 2009-01-22
Bon dia Oriol!

enric@enric-desktop:~$ locale
LANG=ca_ES.UTF-8@valencia
LC_CTYPE="ca_ES.UTF-8@valencia"
LC_NUMERIC="ca_ES.UTF-8@valencia"
LC_TIME="ca_ES.UTF-8@valencia"
LC_COLLATE="ca_ES.UTF-8@valencia"
LC_MONETARY="ca_ES.UTF-8@valencia"
LC_MESSAGES="ca_ES.UTF-8@valencia"
LC_PAPER="ca_ES.UTF-8@valencia"
LC_NAME="ca_ES.UTF-8@valencia"
LC_ADDRESS="ca_ES.UTF-8@valencia"
LC_TELEPHONE="ca_ES.UTF-8@valencia"
LC_MEASUREMENT="ca_ES.UTF-8@valencia"
LC_IDENTIFICATION="ca_ES.UTF-8@valencia"
LC_ALL=
enric@enric-desktop:~$ 

També he provat fent un:

sudo dpkg-reconfigure locales

i res de res...reinicio i tot continua igual.

Merci company!

---

### Post by enricXIII on 2009-01-22
Per cert, tinc un altra usuari al mateix ordinaddor ( la meva parella ), en espanyol, i l'hi passa el mateix..

---

### Post by papapep on 2009-01-22
Recordo haver llegit fa temps que qui tenia activat l'idioma ca_ES.UTF-8@valencia experimentava problemes "curiosos". No sé si és aquest el cas, però igual podrieu anar eliminant possibilitats canviant-lo a ca_ES.UTF-8 que sí que funciona correctament.

---

### Post by enricXIII on 2009-01-22
Hola papapep!

No pot ser el que dius perquè per lògica, si fos això, no afectaria a l'usuari amb idioma "espanyol"...no?
Continuo buscant solucions, si no la trobo aqui, la publicaré igualment perquè us n'assabenteu.. de totes maneres hem fa molt mala pinta, hem penso que d'aquesta si que m'en faré la pell.... :D

---

### Post by papapep on 2009-01-22
Probablement, però què perds a provar-ho? :-D

---

### Post by oriolsbd on 2009-01-22
Jo faria la prova que diu en Papapep.

Per cert, si vas a Sistema>Administració>Suport d'idioma, suposo que tens activats el "Catalan;Valencian" (i el "Spanish;Castilian"), oi?

Salut!

---

### Post by enricXIII on 2009-01-22
> **oriolsbd said:**
> Jo faria la prova que diu en Papapep.

Per cert, si vas a Sistema>Administració>Suport d'idioma, suposo que tens activats el "Catalan;Valencian" (i el "Spanish;Castilian"), oi?

Salut!

Si oriol!

Estic intentant el que diu en papapep...però o estic tonto o no sé com fer-ho! inclús he provat a fer això:

enric@enric-desktop:~$ sudo apt-get install ca_ES.UTF-8
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
E: No s'ha pogut trobar el paquet ca_ES.UTF-8
enric@enric-desktop:~$ 

Cada vegada ho entenc menys... :(

---

### Post by oriolsbd on 2009-01-23
Edita el fitxer ~/.profile, i afegeix al final aquestes línies:
```

export LANG=ca_ES.UTF-8
export LC_CTYPE="ca_ES.UTF-8"
export LC_NUMERIC="ca_ES.UTF-8"
export LC_TIME="ca_ES.UTF-8"
export LC_COLLATE="ca_ES.UTF-8"
export LC_MONETARY="ca_ES.UTF-8"
export LC_MESSAGES="ca_ES.UTF-8"
export LC_PAPER="ca_ES.UTF-8"
export LC_NAME="ca_ES.UTF-8"
export LC_ADDRESS="ca_ES.UTF-8"
export LC_TELEPHONE="ca_ES.UTF-8"
export LC_MEASUREMENT="ca_ES.UTF-8"
export LC_IDENTIFICATION="ca_ES.UTF-8"
export LC_ALL=

```

Un cop fet, reinicia l'ordinador.

---

### Post by enricXIII on 2009-01-23
Bon dia de nou!
Bé...he desinstal.lat el ca_ES.UTF-8@valencia, he reiniciat i per tant he deixat que quedi amb l'idioma predeterminat anglès. A sistems-administració-languagu support he tornat a instal.lar el català- valencia i al reiniciar he escollit a la pantalla de "login" canviar l'idioma de la sessió. Ara hem permetia escollir el català i l'hi he dit que el faci predeterminat.
Un cop iniciada la sessió, l'ordre "locale" a la terminal hem dona això:

enric@enric-desktop:~$ locale
LANG=ca_ES.UTF-8
LC_CTYPE="ca_ES.UTF-8"
LC_NUMERIC="ca_ES.UTF-8"
LC_TIME="ca_ES.UTF-8"
LC_COLLATE="ca_ES.UTF-8"
LC_MONETARY="ca_ES.UTF-8"
LC_MESSAGES="ca_ES.UTF-8"
LC_PAPER="ca_ES.UTF-8"
LC_NAME="ca_ES.UTF-8"
LC_ADDRESS="ca_ES.UTF-8"
LC_TELEPHONE="ca_ES.UTF-8"
LC_MEASUREMENT="ca_ES.UTF-8"
LC_IDENTIFICATION="ca_ES.UTF-8"
LC_ALL=
enric@enric-desktop:~$ 

Interpreto que lògicament he pogut canviar a "ca_ES.UTF-8" tal com m'aconsellava en papapep..però tot continua mig en català i mig en anglès...:confused:
Continuaré cargolant el google a veure si l'hi puc exprimir alguna cosa mes, que ja el tinc emprenyat,:D
Salut companys!

---

### Post by CarlesOriol on 2009-01-23
1. Al menu sistema>preferencies>idioma has comprovat que la insta&#320;lació del suport d'idioma està COMPLETAMENT finalintzada?

2. Quins repositoris tens configurats (backports / proposed??). Pot ser que estiguis insta&#320;lant programari d'alguna font diversa que no estigui correcte?

3. Quins programes et mostren textos en anglès? (dir mig en anglès ajuda poc a veure el problema)

---

### Post by enricXIII on 2009-01-23
Una imatge val més que 1000 paraules...
Com pots veure, el firefox en català, el gimp en anglès, i els menús i opcions amb coses a mitges.
Durant mesos m'ha anat tot bé..vaig fer fa 15 o 20 dies un "localepurgue" per eliminar idiomes innecessaris i cap problema fins ara...
[http://img294.imageshack.us/my.php?image=imatgejo1.png](http://img294.imageshack.us/my.php?image=imatgejo1.png)

A System-Administració-Language support ho tinc així:
[http://img294.imageshack.us/my.php?image=imatge2kg4.png](http://img294.imageshack.us/my.php?image=imatge2kg4.png)

I ara mateix he fet un "locale" a la terminal i em surt això:
[http://img515.imageshack.us/img515/2582/imatge3yp7.png](http://img515.imageshack.us/img515/2582/imatge3yp7.png)

---

### Post by oriolsbd on 2009-01-23
De la primera imatge que mostres (la de Software Sources) mira la primera pestanya (Programari Ubuntu), a veure quins dipòsits hi tens activats (main, universe, restricted i multiverse). No sé en quins d'ells estan els paquets de llengua, però per si de cas, mira que els tinguis tots quatre activats (el de codi font no cal).

Si no és això, no sé què més pot ser.

Salut!

---

### Post by enricXIII on 2009-01-24
Els tinc tots quatre activats oriolbsd, sempre ho han estat..
Gràcies de totes maneres, seguiré buscant solució perquè hem nego a reinstal.lar tot el sistema fins esgotar totes les vies al meu abast.
Si algú vol alguna informació mes, accepto sugerències.. 

Carlesoriol:
No tinc activats ni backport ni proposed..
El suport d'idioma com ho puc comprovar? si ho miro hem permet posar per defecte catala.andorra i català-Valencian..
Tinc per exemple el firefox i openoffice en català, i el gimp en anglès..

Merci companys!
Salut!

---

### Post by CarlesOriol on 2009-01-24
Tot sembla força correcte.

copia'ns el contingut del /etc/apt/sources.list

---

### Post by enricXIII on 2009-01-24
Aqui va:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security multiverse

#GnomeDo
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
deb [http://open.movilforum.com/archive/escritorio-movistar/ubuntu](http://open.movilforum.com/archive/escritorio-movistar/ubuntu) hardy main

# Afegim aquestes per Cairo-Dock
# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) gutsy cairo-dock
# deb [http://ppa.launchpad.net/do-testers/ubuntu](http://ppa.launchpad.net/do-testers/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/do-testers/ubuntu](http://ppa.launchpad.net/do-testers/ubuntu) intrepid main

---

### Post by enricXIII on 2009-01-25
Bones de nou!
Per si serveix d'orientació per algú, he instal.lat a través de synaptic el paquet Ubuntu-desktop, ja que no el tenia instal.lat (no se perquè, teoricament hauria d'haver-ho estat,no?
També he instal.lat els paquets d'idioma amb aquesta ordre al terminal:

sudo apt-get install kde-i18n-ca kde-l10n-ca language-pack-ca language-pack-ca-base language-pack-gnome-ca language-pack-gnome-ca-base language-pack-kde-ca language-pack-kde-ca-base language-support-ca language-support-translations-ca language-support-writing-ca

M'ha instal.lat un munt de coses que suposo que també hauria de tenir i no hi eren..

El resultat de totes maneres ha estat nul, segueix el mateix batibull que tenia.
Salut!

---

### Post by orestesmas on 2009-01-25
A veure, no conec prou el Gnome com per afirmar categòricament això que diré, però no podria ser que aquests repositoris del GnomeDO t'estiguin instal·lant paquets no oficials que no disposin de les traduccions corresponents?

---

### Post by enricXIII on 2009-01-25
No ho crec orestes, fa temps que ho tinc així i anava bé..i en tot cas, em sembla a mi, no hauria de tenir res a veure amb que el gimp o la barra d'eines estigui en anglès i el firefox en català..
Ja no ho se pas...

---

### Post by CarlesOriol on 2009-01-26
> **orestesmas said:**
> A veure, no conec prou el Gnome com per afirmar categòricament això que diré, però no podria ser que aquests repositoris del GnomeDO t'estiguin instal·lant paquets no oficials que no disposin de les traduccions corresponents?

Tots els repositoris semblen correctes... fins i tot això del movistar no sembla que hagi d'afectar massa.

> **enricXIII said:**
> sudo apt-get install kde-i18n-ca kde-l10n-ca language-pack-ca language-pack-ca-base language-pack-gnome-ca language-pack-gnome-ca-base language-pack-kde-ca language-pack-kde-ca-base language-support-ca language-support-translations-ca language-support-writing-ca

Prova de fer un dpkg-reconfigure dels paquets que has dit que has insta&#320;lat.

---

### Post by enricXIII on 2009-01-27
Fet, amb aquest resultat a la terminal, però sense èxit.Tot continua igual...

enric@enric-desktop:~$ sudo dpkg-reconfigure language-support-ca language-support-translations-ca language-support-writing-ca language-pack-ca
[sudo] password for enric: 
Generating locales...
  ca_AD.UTF-8... done
  ca_ES.UTF-8... done
  ca_ES.UTF-8@valencia... done
  ca_FR.UTF-8... done
  ca_IT.UTF-8... done
Generation complete.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
Generating locales...
  ca_AD.UTF-8... up-to-date
  ca_ES.UTF-8... up-to-date
  ca_ES.UTF-8@valencia... up-to-date
  ca_FR.UTF-8... up-to-date
  ca_IT.UTF-8... up-to-date
Generation complete.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
enric@enric-desktop:~$

---

### Post by enricXIII on 2009-01-27
Ep! Mireu que passa si faig un sudo apt-get update, les linies "translation ca" hem sembla que donen error...("ign" vol dir ignorar?)

enric@enric-desktop:~$ sudo apt-get update
[sudo] password for enric: 
Get:1 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy Release.gpg [189B]                                                                                                 
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/main Translation-ca                                                                                                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/restricted Translation-ca                                                                                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/universe Translation-ca                                                                                  
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/multiverse Translation-ca                                                                                
Get:2 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates Release.gpg [189B]                                                                             
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates/main Translation-ca                                                                                          
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates/restricted Translation-ca                                                                        
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates/universe Translation-ca                                                                          
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates/multiverse Translation-ca                                                                                    
Get:3 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security Release.gpg [189B]                                                                                        
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security/main Translation-ca                                                                                         
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security/restricted Translation-ca                                                                                   
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security/universe Translation-ca                                                                         
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security/multiverse Translation-ca                                                                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy Release                                                                                                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates Release                                                                                          
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security Release                                                                                                     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/main Packages                                                                                                        
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/restricted Packages                                                                                                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/universe Packages                                                                                        
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/multiverse Packages                                                                                      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates/main Packages                                                                                    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates/restricted Packages                                                                              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates/universe Packages                                                                                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates/multiverse Packages                                                                              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security/main Packages                                                                                   
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security/restricted Packages                                                                             
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security/universe Packages                                                                               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-security/multiverse Packages                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-ca                                                                                                      
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]                                                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                                                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-ca                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                  
Ign mirror://www.getdeb.net hardy/ Release.gpg                          
Ign mirror://www.getdeb.net hardy/ Translation-ca                       
Ign mirror://www.getdeb.net hardy/ Release
Get:5 mirror://www.getdeb.net hardy/ Packages [50,0kB]
Hit [http://open.movilforum.com](http://open.movilforum.com) hardy Release.gpg                                                                                                            
Ign [http://open.movilforum.com](http://open.movilforum.com) hardy/main Translation-ca
Hit [http://open.movilforum.com](http://open.movilforum.com) hardy Release
Ign [http://open.movilforum.com](http://open.movilforum.com) hardy/main Packages
Hit [http://open.movilforum.com](http://open.movilforum.com) hardy/main Packages
Fetched 50,6kB in 1min15s (666B/s)
Reading package lists... Done
enric@enric-desktop:~$

---

### Post by Kaia on 2009-01-27
A mi em passa lo mateix, pensava que no estaria finalitzada la traducció o algo...

---

### Post by enricXIII on 2009-01-28
Bon dia.
Després d'uns quants dies d'investigar, remenar al google fins a l'extenuació, d'haver consultat i provat tot tipus de configuracions ( tant les que se m'han suggerit aquí com a d'altres llocs...), i haver-hi dedicat moltes hores per intentar sol.lucionar-ho, valorant la situació, arribo només a una conclusió: Ha d'haver-hi un error produit per alguna actualització.
Perquè? 
Doncs per pura lògica. Si ho tinc tot bé i tal com ja vaig comentar al principi d'obrir aquest fil, resulta que m'afecta tant a l'usuari català com al castellà i a més a més, un company de feina a qui vaig instal.lar l'Ubuntu en castella sense cap problema, s'ha trobat al mateix temps que jo amb el mateix problema i ara apareix a aquest mateix fil un altra usuari amb el mateix problema.. que algú hem corretgeixi si vaig errat!
De totes maneres el que més hem sorprèn es que al meu portàtil, de moment, no m'ha afectat gens..
Estava ja pensant que hauria de re-instal.lar-ho tot, (cosa que no m'atrau gens ni mica, almenys fins esgotar totes les vies possibles al meu abast) però de moment no ho faré. No reinstal.laré. Aguantaré així fins que trobi alguna sol.lució..
Gràcies a tots per el temps dedicat a aquest tema, prometo tornar aportant una resposta satisfactòria si la trobo!
Salut companys!

---

### Post by papapep on 2009-01-28
> Doncs per pura lògica. Si ho tinc tot bé i tal com ja vaig comentar al principi d'obrir aquest fil, resulta que m'afecta tant a l'usuari català com al castellà i a més a més, un company de feina a qui vaig instal.lar l'Ubuntu en castella sense cap problema, s'ha trobat al mateix temps que jo amb el mateix problema i ara apareix a aquest mateix fil un altra usuari amb el mateix problema.. que algú hem corretgeixi si vaig errat!

La pregunta del milió és aquesta: per què et passa a tu (i al teu company) i a nosaltres no?

Si fos una actualització seria massiu, perque tots el tenim en català, o gairebé tots...

---

### Post by enricXIII on 2009-01-28
No ho se papapep..si tingués la resposta a la pregunta del miliò ja hauria arreglat el meu problema..per`veig que amb comptegotes sembla que van apareixent casos, no? :-(
Vull provar a instal.lar kde i iniciar sessió amb aquest escriptori per veure com afecta al tema de l'idioma. Hem podrieu dir què he d'instal.lar exactament per poder alternar el tipus d'escriptori sense problemes?
Salut!

---

### Post by oriolsbd on 2009-01-28
Prova una cosa. Si vas a "Sistema\Administració\Fonts de Programari", a la pestanya "Programari Ubuntu" hi deus tenir marcat que et baixi els paquets del "Servidor per a Espanya". En la mateixa llista desplegable, marca "Servidor principal" (o "Main Server" si no ho tens traduït). A vegades m'ha donat problemes el servidor d'Espanya, i amb el principal no he tingut cap problema.

Després de modificar-ho, torna a mirar si tens actualitzacions.

A veure si hi ha sort...

Salut!

---

### Post by papapep on 2009-01-28
Per instal·lar el KDE:

```
sudo aptitude install kubuntu-desktop
```

però tal i com tens el tema, no sé si t'ajudarà o t'acabarà de matar...

---

### Post by indiosincracia on 2009-01-28
amb el synaptic marca;

kubuntu-desktop

en quant al gestor d'arrencada és igual tots dos t'aniran bé, el GDM (s'integra visualment més amb el gnome) i el KDM (s'integra visualment amb kde).

edito: perdò per la xafada papapep

---

### Post by enricXIII on 2009-01-28
Ho acabo de mirar oriol, ja ho tenia al servidor principal però, per si de cas, ho he fet a l'inversa. He posat el servidor per espanya i he actualizat. No tenia actualitzacions pendents. He tornat al principal i tampoc en tenia de pendents. Ho deixo al principal com ja tenia.

Papapep, plis, feu una plegària a la Mare de Deu dels Peixos per l'integritat de la meva màquina,:D:D;) ,Vaig a instal.lar kde per provar.. :evil: hem penso que deu ser l'única cosa que encara no he tocat..

---

### Post by torracastanyes on 2009-01-28
Tranquil, no crec que la teva màquina corri perill.
Penso que convindría poder comparar el teu sources.list amb el del teu amic i el d'en Kaia i veure si teniu repositoris comuns.
En tot cas, jo provaría de desactivar els repositoris de hardy-partners, launchpad i movilforum i actualitzar el suport d'idioma, abans de tocar res més.

---

### Post by enricXIII on 2009-01-28
Nois, agrait per les pregàries..tot a anat correctament en quant a l'instal.lació de kde.
De totes maneres no ha servit de res, en quant a l'idioma tot continua igual..
Provaré a desactivar el launchpad i tot això, però no ho veig clar, ja us diré com va.

---

### Post by enricXIII on 2009-01-28
Ho acabo de provar torrecastanyes, sense èxit.
M'he fixat que a l'actualitzr, hi han unes línies de translation-ca que fallen sempre. Us adjunto una captura de pantalla perquè ho veieu..
[http://img515.imageshack.us/img515/406/translationcauq0.png]("http://img515.imageshack.us/img515/406/translationcauq0.png")

---

### Post by enricXIII on 2009-01-28
Com que fa un temps vaig fer un "localepurgue" (i tot va anar bé,almenys fins ara), se m'ocurreix que potser tornant a fer-l'ho i reinstal.lant TOTS els idiomes..hauria d'anar bé. No ho sé, hem sembla exagerat fer-ho..però..que us sembla?

---

### Post by torracastanyes on 2009-01-28
Bé, lo dels errors a l'actualitzar les fonts també em passa, pero en canvi, mai m'ha portat problemes.
Mes aviat crec que és una incompatibilitat amb algun paquet que hagis intalat d'un repositori "no oficial" (com el launchpad, per exemple).
Se t'acut quin podría ser?

Edito: Dius que al portàtil no l'hi passa. Pots mirar el souces.list i comparar-lo amb el que has penjat aquí?

---

### Post by enricXIII on 2009-01-29
Bones!
A veure. no se m'acudeix res torracastanyes..
En quant al source.lst no hi veig tampoc diferencies, però crec que ja tinc pistes significatives de que pot passar.
Coneixeu el "localepurge"? He trobat per el google un usuari que el va instal.lar, per netejar idiomes que no fa servir i sembla que aquest "programa" ja avisan que pot portar problemes perquè pot fer malbé arxius d'idioma. A aquest usuari que el va fer servir l'hi va passar **exactament** l'ho que hem passa a mi! Llàstima que es un fil trencat, sense respostes, amb lo qual no he pogut saber com ho va solucionar..
He desinstal.lat el "localepurge" i ho he remenat tot per retornar les coses al seu lloc però res.
Per el que he entès, aquest programa fa la feina i a partir d'aquell moment, quan instal.les qualsevol cosa al final fa la "neteja" que va programar-se en el seu moment..i no he trobat ningú que sàpiga com inutilitzarlo.
Potser aquesta sigui la mare dels ous..

---

### Post by torracastanyes on 2009-01-29
No conec el programa, així que no et puc ajudar gaire, però he trobat això que potser et servirà:

[http://osdir.com/ml/debian.devel.spanish/2002-10/msg00124.html](http://osdir.com/ml/debian.devel.spanish/2002-10/msg00124.html)

De tota manera, m'extranya que uns programes funcionin i altres no. Jo miraría bé el que t'ha dit l'Orestes.

---

### Post by enricXIII on 2009-01-29
Bones.
A veure. Per si de cas, tingués raó l'Orestes, he desinstalat completament el gnome-do, però tot segueix igual a pesar de desinstalar el català i tornarlo a instalar.
De totes maneres m'hauria extranyat molt que fos això perquè al portàtil també el tinc instalat i no tinc cap problema..
Mireu que arribo a ser tossut, m'he mirat mil i una opcions i ho he provat quasi tot..i l'única cosa que trobo que si que podia portar problemes amb l'idioma es el ditxós "localepurge".
Ja no sé si es culpa d'aquest programa o no, però es l'única cosa que afortunadament, NO vaig instalar al portàtil!
Per tant..ara si que hem sembla que hauré de fer còpia de seguretat de tot lo que no en tingui..i reinstalar.
Hem toca més els "uremus" el fet de no poder-ho arreglar, que no pas el fet de reinstalar, ja que a la fí i al cap, amb una horeta escassa puc tornar a teni-ho tot configurat de nou i llestos..
Així de pas faré neteja de coses que no utilitzo..

---

### Post by Diegstroyer on 2009-02-01
Tranquils, si no m'equivoco és el Openoffice que el tens en Anglès no? Això és degut a que el paquet d'idioma de l'openoffice del launchpad (OOo3).

A tothom que conec li passa el mateix (tothom que s'ha instal·lat la versió OOo3 per launchpad), els que continuen amb la 2.4 no tenen aquest problema.

És degut a que OOo3 ha deixat de ser Release Candidate, per ser una versió definitiva, paciència, ja arribaran els paquets d'idioma.

Per saber si és això, ves a Synaptic i intenta instal·lar els paquets d'idioma en Català per a l'OOo3 (openoffice.org-l10n-ca), et dirà que vol marcar per desinstal·lar l'openoffice mateix (no ho facis!). No ho instal·lis i a esperar. Si en canvi, no et dona aquest missatge, instal·la i creua els dits (jo ja el tinc en català :)).

Si et passa el mateix amb altres aplicacions, utilitza Synaptic per mirar si pots instal·lar els paquets d'idioma.

Sobre tot, no reinstal·lis els paquets d'idioma per mitjà de **Sistema-->Administració-->Suport d'idioma**, si ho fas, l'openoffice deixa de funcionar i l'hauràs de reinstal·lar de nou.

Salutacions.

---

### Post by oriolsbd on 2009-02-01
No ho entenc. Jo tinc l'OpenOffice 3 de launchpad, i sí que veig els menús en català.

---

### Post by enricXIII on 2009-02-01
Gràcies per l'informació Diegstroyer, però no era aquest el meu problema (precisament l'openoffice era dels que tenia en català 2.4 ).
Bé, ja que m'havia disposat a reinstalar..m'ho vaig repensar i vaig decidir ahir que, en lloc de reinstalar, podia actualitzar a Intrepid a veure que passava..i sorpresa!!! A l'actualitzar se m'han corregit TOTS els problemes d'idioma!
O sigui, que en principi ho tinc tot arreglat i ja que m'ho ha detectat tot correctament (tampoc esperava menys del meu estimat Ubuntu :D:D ), de moment ho deixaré aixi.
L'única cosa que no hem rutlla es el meu escàner de l'impressora multifunció Brother DCP-150c, però suposo que podre reconfigurar-ho, en tot cas ja hem veureu plorant en un altra fil si no m'en surto...:p
Agrait a tots per l'interés mostrat en ajudar-me, tant de bó us pugui tornar el suport amb els coneixements que vaig adquirint i que, lluny de desanimarme, no fan més que enamorarme cada dia més d'aquest món de GNU/Linux i del programari lliure.
Salut companys!!

Edito: No poso el "solved" a aquest fil perquè no hem semblaria correcte. El problema no s'ha solucionat.
Si algun administrador considera que s'ha de posar ho deixo a les seves mans...
Merci!

---

