---
title: "Problemes en suprimir (ubuntu 9.04)"
date: 2009-09-25
forum: Catalan Team
---

### Post by Razlo on 2009-09-25
Bon dia!

Sóc usuari d'ubuntu des de fa uns dos anys, quan se'm va espatllar el windows i vaig tirar per la via ràpida, live cd i sistema nou.

Ara al meu germà li ha passat el mateix, i vam instal·lar amb el live cd 9.04, que vaig descarregar de la pàgina oficial. Tot i que el sistema va net, hi ha un parell de detalls que molesten una mica:

- fent servir el nautilus, no apareix l'opció de suprimir (definitivament) en el menú contextual

- en suprimir un fitxer amb la tecla, o fent clic a "mou a la paperera", l'arxiu no hi apareix, i tampoc es pot buidar la paperera 'perquè no hi ha res'. També he enganxat un fitxer a la paperera i ha desaparegut com en un forat negre.

Hem provat de, fent servir el nautilus de superusuari, crear una carpeta, crear-hi un fitxer de 4 línies i moure'l a la paperera (de les tres maneres citades). Doncs bé, ni fent Ctrl+H hem aconseguit descobrir on van a parar aquests fitxers.

Seria possible que existís una segona paperera? Enganxant el fitxer a la paperera de trash:/// (fent clic a la icona), però també desapareixia.

És sospitós que la funció d'eliminar no aparegui tampoc, potser és molt senzill i només s'han d'instal·lar uns paquets, però és no ho he sabut trobar.

Gràcies per l'atenció

---

### Post by PatrickVogeli on 2009-09-25
Suprimir definitivament: al nautilus, Edita -> Preferencies -> Comportament -> "Inclou una ordre Suprimeix que no tingui en compte la papelera"

Respecte al tema de la papera, pots mirar si tens el fitxers a /home/usuari/.local/share/Trash

El tema de la papelera es curios, a mi em funciona perfectament i mai he tingut problemes.

---

### Post by Razlo on 2009-09-25
Moltes gràcies! Tot era com has dit.
Miraré de direccionar l'opció de moure a la paperera a la paperera general.

Salut!

---

