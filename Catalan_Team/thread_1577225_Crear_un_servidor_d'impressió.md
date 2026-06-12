---
title: "Crear un servidor d'impressió"
date: 2010-09-18
forum: Catalan Team
---

### Post by tanreb20 on 2010-09-18
Hola!

Fa uns dies em vaig carregar el Servidor d'Impressió de la meva impresora :( (problemes amb el cable i el voltatge...)

Resulta que ara amb el nou router que tenim ja podem interconectar aparells en xarxa(l'anterior no ho permetia)

Algú sap com crear un servidor d'impressio amb un PC vell i ubuntu (sense gráfics)? Quins paquets instalar perqué tots els ordinadors puguin enviar-hi documents? (tant linux com windows...)

---

### Post by kukat on 2010-09-19
Una vegada tens els ordinadors en xarxa, per a veure la impressora tens que anar a "Configuració d'Impressora" (KDE) o a GNOME Sistema -> Administració -> Impressora

A la part de Server Settings marques les opcions per a la compartició de Xarxa....
"Mostrar les impressores compartides per altres S.O"
"Comparteix les impressores....."
Jo les he marcades _totes_.

Açò es fa al ordinador que actua de servidor d'impressió. Als altres ordinadors tens que afegir una nova impressora, marcar-li que és una impressora de Xarxa, i cercar la impressora que ja deu estar visible a la xarxa.

Respecte a Windows, tens que insta&#320;lar Samba i fer altres coses. 
T'assegure que d'aquests temes hi ha milers i milers de pàgines a Internet que ho expliquen. Únicament cal posar a Google: "Impressora xarxa ubuntu windows" o "Impresora en red ubuntu windows" o "Network Printer ubuntu windows". 
 
per exemple: [http://www.guia-ubuntu.org/index.php?title=Compartir_una_impresora_con_Windows_2000/XP](http://www.guia-ubuntu.org/index.php?title=Compartir_una_impresora_con_Windows_2000/XP) (castellà)

Salut!

---

### Post by PatrickVogeli on 2010-09-19
mira manuals de com configurar el samba, em sembla que no es massa dificil.

De totes maneres, si ho entes bé, t'estas plantejan mantenir un PC vell ences tot el dia i fer-lo servir només de servidor d'impressió? Si es així, pensa't-ho 2 vegades, pel tema de consum elèctric: t'acabara sortint molt més economic comprar-te una altre servidor que fer anar el PC vell.

Salut

---

