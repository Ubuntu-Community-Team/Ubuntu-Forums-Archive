---
title: "lan lenta"
date: 2010-11-10
forum: Catalan Team
---

### Post by dafaktor on 2010-11-10
Bona nit,

fa poc he habilitat la compartició de carpetes fent servir NFS.

Ara fa una estona volia copiar un fitxer d'una màquina a una altra i m'ha sorprès la tremenda lentitud amb la què es copiava: en cap moment ha passat de 600kB/segon.

Les dues màquines estan connectades amb cable a un router DSL (Linksys WAG200G), les dues estan a 100Mb-Full duplex.

Alguna idea?

Merci.

---

### Post by CarlesOriol on 2010-11-14
Amb un altre protocol o sistema et funciona ràpidament?

Tens algun tipus de tallafocs als ordinadors?

Els cables estan correctament trenats?

Si son molts arxius petits prova d'afegir async a l'arxiu d'exports.

Hi ha més transit a la xarxa ? encara que sigui d'altres ordinadors el router pot ser que funcioni com un hub i no com un switch.

Has comprovat que la configuració d'ips i gateways sigui correcta?

---

### Post by akyra on 2010-11-14
Hola a mí també em va passar, ho vaig provar amb el router, sense el router i amb cables creuats, i no sé quines maneres més. A mi la velocitat m'anava a 1MB/s, molt lluny de la teoria.

Bé, segons m'han dit els informàtics de la feina, perquè es pugués anar a 100MB/s haurien de ser les mateixes targes i amb unes distàncies petites, i alguna altra cosa més que no recordo.

El que vaig haver de fer finalment, va ser copiar-ho mitjançant un disc dur USB, sino no hi havia manera.

Si trobes alguna solució, ja ens la diràs ja que a vegades es necessita copiar entre ordinadors.

Salutacions

---

