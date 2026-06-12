---
title: "No puc iniciar sessió   error Xsession"
date: 2009-10-12
forum: Catalan Team
---

### Post by pserra on 2009-10-12
Hola,
estic fent la instal·lacio de Oracle 11g i m'està donant un munt de problemes(permisos directoris, memòria swap..)
El cas es que ahir vaig trobar un 'manual per internet' el qual es creava el directori manualment i es donaven permisos prèviament abans de la instal·lacio....
Desprès de fer  desde  root: 

```
chown -R oracle:oinstall /mount_point/app/
```

vaig voler reiniciar la màquina i no em va deixar entrar....
em surt un error abans de carregar la pantalla ubuntu:

```
etc/gdm/xsession/
Beginning session setup Setting......
......
```

vaig estar mirant per internet solucions sobre permisos... però vaig perdut...alguna suggerència?
hi ha algu que teballi amb oracle 11g? quins son els passos mínims??

---

### Post by pserra on 2009-10-13
donaré més  detalls sobre el missatge que em surt... a veure si algu em dona un cop de mà...(disculpeu si hi ha un error ortogràfic)

quan carrega surt-> la vostra sessió ha durat menys de 10 segons
cliko a detalls->
 ```
 /etc/gdm/Xsession. Beginning session setup...
Setting IM thougth /etc/xm/xinit/ximput.d/all_ALL  linked to /etc/x11/xinit/xinput/default.
mkdtemp: private socked dir: Permission denied.

```

**Estic convençut que qualsevol usuari avançat sabrà entendre el error anterior que em mostra i la seva solució...**
Merci

---

### Post by papapep on 2009-10-13
Pserra, amb les pistes que dónes no hi ha gaire per on estirar.
Els missatges són prou generals per no saber cap on apuntar.

Amb un simple:

```
chown -R oracle:oinstall /mount_point/app/
```

no es pot muntar aquest sidral que sembla que tens de permisos, ja que no afecta a cap fitxer o directori de sistema. 
O sigui que el més probable és que alguna de les altres coses d'aquell "manual per internet" que esmentes, o del mateix instal·lador de l'Oracle hagi provocat el desgavell.

Per altra banda, l'Oracle, en qualsevol versió, és un monstre suficientment gran com per no poder-te indicar uns "passos mínims". És com demanar un manual en deu passes per a fer un gratacels. :)

Per provar un parell de coses:

1. Entra en "recovery mode" a veure què fa. (en sortir el grub, prem Esc i tria el kernel amb el text "Recovery mode" al final).

2. Verifica el propietari i els permisos del directori /tmp:

```
ls -la /tmp |grep ' .'\$
```

Si és diferent d'això (evidentment, la data i hora han de ser diferents):

```
drwxrwxrwt 15 root    root    4096 2009-10-13 16:31 .
```

potser hem trobat la punta del cabdell. Aleshores, hauries de fer:

```
sudo chown root:root /tmp && sudo chmod 777 /tmp
```

I prova a veure què fa ara.

Per cert:
> Estic convençut que qualsevol usuari avançat sabrà entendre el error anterior que em mostra i la seva solució...

Això és molt suposar quan no es sap l'origen del problema...

---

### Post by pserra on 2009-10-13
Perfecte Papapep,
ets un mestre...
problema solucionat... has donat al clau...
a reveure...
Merci

---

