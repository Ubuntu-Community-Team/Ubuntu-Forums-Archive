---
title: "cgis en apache"
date: 2007-04-27
forum: Catalan Team
---

### Post by joant on 2007-04-27
Hola,

Bentrobats. Avui m'estreno al fòrum.

tinc l'apache instal·lat al kubuntu. Sabeu a quin directori han d'anar els scripts .cgi perquè s'executin?. També m'agradaria saber com puc canviar aquest directori per defecte.

Gràcies.

Joan.

---

### Post by CarlesOriol on 2007-04-27
De: 	Josep Sànchez Mesegué <papapep@gmail.com>
Respon: 	[email]papapep@noVullCorreuBrossagmail.com[/email], Equip català d'Ubuntu LoCo Team <ubuntucat-info@cpl.upc.edu>
Per a: 	[email]jtp@tinet.cat[/email], Equip català d'Ubuntu LoCo Team <ubuntucat-info@cpl.upc.edu>
Assumpte: 	Re: [Ubuntucat-info] apache Kubuntu
Data: 	Fri, 27 Apr 2007 13:19:12 +0200


El 27/04/07, Joan T. <jtp@tinet.cat> ha escrit:
> Tinc l'apache instal·lat al kubuntu. Sabeu a quin directori han d'anar
> els scripts cgi perquè s'executin?. També m'agradaria saber com puc
> canviar aquest directori per defecte.

Una de les directives que tens a /etc/apache2/sites-available/default és:

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

 Entenc que si li dius un altre lloc, sempre que els permisos estiguin
correctes, t'hauria de funcionar. Però perquè li vols canviar el
lloc??

Salutacions.

-- 
Josep Sànchez
[papapep]
-----------------------------------------------------------------
[http://recepteslinux.homelinux.org/wordpress](http://recepteslinux.homelinux.org/wordpress)
-----------------------------------------------------------------
_______________________________________________
Ubuntucat-info mailing list
[email]Ubuntucat-info@cpl.upc.edu[/email]
[https://lists.lafarga.cpl.upc.edu/mailman/listinfo/ubuntucat-info](https://lists.lafarga.cpl.upc.edu/mailman/listinfo/ubuntucat-info)

---

### Post by joant on 2007-04-27
Anava a postejar la resposta que he obtingut a la llista de correu, però he vist que te m'has avançat, Carles Oriol :-).  Gràcies.

De fet, hem pogut comprovar que de moment la llista és més àgil que el forum, tot i que probablement tots els que som a un lloc també som a un altre,no?

Salut.

Joan T.

---

### Post by CarlesOriol on 2007-04-28
no, no... hi ha bastants llistaires no forumaires i forumaires no llistaires.

---

