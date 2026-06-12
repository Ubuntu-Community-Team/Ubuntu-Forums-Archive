---
title: "Playonlinux"
date: 2011-09-12
forum: Catalan Team
---

### Post by akyra on 2011-09-12
Hola a tots,

Tinc un petit programa (Sansung KIE) per treure els contactes i demés d'un movil Samsung i volia instalar-lo en l'ordinador de casa que és en UBUNTU.
El problema és que quan intento instalar-lo amb WINE peta la instalació.

He llegit que el software "Playonlinux" és per executar programes que només poden correr en windows, però no veig gaire com funciona (sembla que tot és amb scripts).

Algú la utilitzat i em pot donar 4 idees?

Gracies

---

### Post by oriolsbd on 2011-09-12
El PlayOnLinux és bàsicament un programa que té «memoritzades» les configuracions de Wine amb les que funcionen correctament uns quants programes de Windows. Va començar per a jocs, i per això es diu PlayOnLinux, però ara hi ha altres programes com Word, Spotify, etc. Per tant, el que fa és indicar-te una sèrie de programes i, quan l'insta&#320;les, et posa un perfil amb versió de Wine concreta, amb una configuració concreta, i a sobre t'hi insta&#320;la el programa (necessites el seu insta&#320;lador, no et ve amb el PlayOnLinux). Si vols insta&#320;lar un altre programa de la seva llista, fas el mateix, i el PlayOnLinux t'insta&#320;larà un altre perfil de Wine amb una altra versió de Wine, una altra configuració de Wine i, en ella, t'insta&#320;larà l'altre programa.

Crec que, a menys que el Samsung KIE estigui a la llista de PlayOnLinux (que ho dubto), el millor és tractar directament els missatges que t'ha donat la insta&#320;lació amb Wine. Jo alguns cops he pogut insta&#320;lar programes «estranys» amb Wine. Ens pots enviar els missatges?

Salut!

---

### Post by akyra on 2011-09-13
Hola Oriolbsd

Ja he vist que el Samsung KIE no està a la llista de Playonlinux, no he vist els missatges d'erors en Wine, simplement no me'l deixa instal·lar.

Com puc veure aquest els missatges que dóna el wine? Jo simplement faig doble click en el fitxer.exe que ha d'instalar-ho.

He solucionat el tema dels contactes amb el Gammu, així que pel moment ja no utilitzare el Samsung Kia, però trobar els errors del wine aniria bé.

Gracies

---

### Post by oriolsbd on 2011-09-15
Quan executes el fitxer .exe no et surt cap finestra d'error? Simplement se't tanca el programa? O no se t'arriba a mostrar res?

Prova d'executar-lo des d'un terminal. Ves al directori on tinguis el fitxer d'insta&#320;lació i executa el següent:
> wine fitxer.exe

---

