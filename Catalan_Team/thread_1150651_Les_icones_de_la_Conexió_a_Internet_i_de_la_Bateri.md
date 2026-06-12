---
title: "Les icones de la Conexió a Internet i de la Bateria"
date: 2009-05-06
forum: Catalan Team
---

### Post by MiquelBLL on 2009-05-06
Hola, per error vaig esborrar les icones que indiquen la conexió a internet i de la carrega de la bateria, ho he buscat i no he vist com puc tornar a que em surtin a la barra de Menú. Algú em pot ajudar?, He mirat a: *Afegir al quadre* pero alla no hi son.

---

### Post by Tomàs M. on 2009-05-06
Per a la icona de la bateria: Sistema - Preferències - Gestor d'energia, pestanya general.
Amb la icona de connexió a Internet, què vols dir exactament?

---

### Post by MiquelBLL on 2009-05-07
Hola. Avans que res dir que tinc el 9.04. No es aquesta que dius l´icona de carrega de la bateria, es un altra que fa la funció de que al cliclar es diu el percentage,historial capacitat si es bona o regular...
Sobre lo de internet es l´icona que son unes barres blaves i que tambe et diu la potencia si vols activar la xarxa sense fil i on pots veurer les diferents xarxes que hi ha. Em sembla que deu estar al inici en alguna preferencia per defecte pero no se on.

---

### Post by Tomàs M. on 2009-05-07
> **MiquelBLL said:**
> ...es un altra que fa la funció de que al cliclar es diu el percentage,historial capacitat si es bona o regular...


La que et dic jo fa tot això amb Jaunty, a base de botó dret i esquerre...

> **MiquelBLL said:**
> Sobre lo de internet es l´icona que son unes barres blaves i que tambe et diu la potencia si vols activar la xarxa sense fil i on pots veurer les diferents xarxes que hi ha. Em sembla que deu estar al inici en alguna preferencia per defecte pero no se on.

El network-manager? Prova d'executar nm-applet --sm-disable. Comprova també que el tens marcat a Sistema-Preferències-Aplicacions d'inici, Gestor de xarxes.

Sort!

---

### Post by MiquelBLL on 2009-05-08
No, no es la mateixa icona, no tens una icona al costat on te marca lo de internet que te surt una bateria i que at diu unes coses diferents que la icona de ´Gestor de energia´? La icona que em sortia avans no la vaig triar, ja en sortia per defecte.
Ja vaig fer  lo de ´nm-applet --sm-disable´ ho vaig veurer per alguna pagina i aixo es el que em surt al terminal:

miquel@miquel-laptop:~$ nm-applet --sm-disable

(nm-applet:7094): Gtk-WARNING **: No s'ha trobat el motor de tema al module_path: «aurora»,

** (nm-applet:7094): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

---

### Post by Tomàs M. on 2009-05-09
No sé si no ens entenem, però juraria que parlem de la mateixa...
No sé com ajudar-te; potser pots donar una mirada a [http://www.ubuntu-unleashed.com/2008/05/some-gnome-panel-applets-you-may-not.html](http://www.ubuntu-unleashed.com/2008/05/some-gnome-panel-applets-you-may-not.html) a veure si hi ha alguna alternativa que et sereixi...

---

### Post by MiquelBLL on 2009-05-09
Hola gracies, no veig a aquesta pagina com fer-ho. He intentat treurer lo de .gnome .gnome2 pero per tornar a iniciar l´escritori per defecte i no se com he perdut lo de .gnome i per exemple m´han marxat els fons de pantalla que tenia per triar, si els puc tornar a posar pero...
En concret nessesito l´aplicacio anomenada ´Networkmanager´ que es l´aplicacio que em deixaba triar la xarxa i es lo que vaig esborrar del quadre, millor dit nessesito que em surti l´icona que em sortia avans del networkmanager la conexio a internet em funciona be per ara.

---

### Post by lluisanunez on 2009-05-09
Vols dir que no has esborrat l'àrea de notificacions? Pots tornar-la a afegir clicant amb l'altre botó al panel (quadre?) > Afegir

---

### Post by Tomàs M. on 2009-05-09
Ostres, clar! Segur que és això, veïna d'install party :P

---

### Post by MiquelBLL on 2009-05-10
Un mil.lió de gracies, si que es això, no vegeu quines trencades de cap que me fotut, ahir tot el dia barallan-me, inclus vaig entrar a #linux_novatos pero no en van saber dir com, em van dir lo de ocultar lo de .gnome i .gnome2 pero no aixo...

Aviseu si vaniu pel Priorat sereu ben rebuts. Gracies de nou.

---

