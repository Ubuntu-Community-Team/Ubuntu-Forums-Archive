---
title: "postgresql-8.3: el subprocés post-installation script retornà el codi d'eixida d'erro"
date: 2009-11-12
forum: Catalan Team
---

### Post by dsanchezfra on 2009-11-12
Hola Bon dia.

Fent una instal·lació de postgresql-8.3 vaig tenir un problema i ara tinc el paquet trencat que no hi  manera d'eliminar-lo. Tinc instal·lat Ubuntu 9.04 Jaunty Jackalope i ja he provat de tot per mirar de solucionar-ho. 

Des de synaptic si intento reinstal·lar el paquet em surt aquesta errada:
[COLOR=Navy]E: postgresql-8.3: el subprocés post-installation script retornà el codi d'eixida d'error 1

[COLOR=Black]En els detalls de l'errada em surt:[/COLOR]
S'està configurant postgresql-8.3(8.3.8-0ubuntu9.04) ...
*Starting PostgreSQL  database server
*Error: /var/lib/postgresql/8.3/main is not accessible or does not exist ... fail!
invoke-rc.d: initscript postgresql -8.3, action "start" failed.
dpkg: s'ha produït un error en processar postgresql-8.3 (--configure): el subrocés post-installation script retornà el codi d'eixida d'error 1
S'han trobat errors en processar: postgresql-8.3
E:Sub-process /usr/bin dpkg returned an error code (1) 
ha fallat la instal·lació d'un paquet. S'està intentant la recuperació:[/COLOR]


Si intento purgar des de terminal:
[COLOR=Navy]daniel@daniel-laptop:~$ sudo apt-get purge postgresql-8.3
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
Els paquets següents s'instal·laren automàticament i ja no són necessaris:
  postgresql-client-8.3 php5-gd libt1-5 postgresql-client-common
  postgresql-common
Empreu «apt-get autoremove» per a suprimir-los.
Es SUPRIMIRAN els paquets següents:
  postgresql-8.3*
0 actualitzats, 0 nous a instal·lar, 1 a suprimir i 0 no actualitzats.
1 no instal·lats o suprimits completament.
Després d'aquesta operació s'alliberaran 14,2MB d'espai en disc.
Voleu continuar [S/n]? s
(S'està llegint la base de dades ... hi ha 221791 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant postgresql-8.3 ...
* Stopping PostgreSQL 8.3 database server                                       
* Error: /var/lib/postgresql/8.3/main is not accessible or does not exist
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "stop" failed.
dpkg: s'ha produït un error en processar postgresql-8.3 (--purge):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
* Starting PostgreSQL 8.3 database server                                       
* Error: /var/lib/postgresql/8.3/main is not accessible or does not exist
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: s'ha produït un error en netejar:
 el subprocés post-installation script retornà el codi d'eixida d'error 1
S'han trobat errors en processar:
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)
daniel@daniel-laptop:~$ 

[COLOR=Black]Si intento forçar l'eliminació:
[COLOR=Navy]daniel@daniel-laptop:~$ sudo dpkg --remove --force-all postgresql-8.3
(S'està llegint la base de dades ... hi ha 221791 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant postgresql-8.3 ...
 * Stopping PostgreSQL 8.3 database server                                                                                                                                  
* Error: /var/lib/postgresql/8.3/main is not accessible or does not exist
                                                                                                                                                                    [fail]
invoke-rc.d: initscript postgresql-8.3, action "stop" failed.
dpkg: s'ha produït un error en processar postgresql-8.3 (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
 * Starting PostgreSQL 8.3 database server                                                                                                               
 * Error: /var/lib/postgresql/8.3/main is not accessible or does not exist
                                                                                                                                                                    [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: s'ha produït un error en netejar:
 el subprocés post-installation script retornà el codi d'eixida d'error 1
S'han trobat errors en processar:
 postgresql-8.3
daniel@daniel-laptop:~$ 
[/COLOR]
Si intento eliminar des d'aptitude.
[COLOR=Navy]daniel@daniel-laptop:~$ sudo aptitude
(S'està llegint la base de dades ... hi ha 221791 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant postgresql-8.3 ...
 * Stopping PostgreSQL 8.3 database server                                                                                                                                  * Error: /var/lib/postgresql/8.3/main is not accessible or does not exist
                                                                                                                                                                    [fail]
invoke-rc.d: initscript postgresql-8.3, action "stop" failed.
dpkg: s'ha produït un error en processar postgresql-8.3 (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
 * Starting PostgreSQL 8.3 database server                                                                                                                                 
 * Error: /var/lib/postgresql/8.3/main is not accessible or does not exist
                                                                                                                                                                    [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: s'ha produït un error en netejar:
 el subprocés post-installation script retornà el codi d'eixida d'error 1
S'està desinstal·lant php5-gd ...
S'està desinstal·lant libt1-5 ...
S'està desinstal·lant postgresql-client-8.3 ...
S'està desinstal·lant postgresql-common ...
S'està desinstal·lant postgresql-client-common ...
S'estan processant els gallets per a libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /opt/PostgreSQL/8.3/lib/liblwgeom.so.1 is not a symbolic link

S'estan processant els gallets per a man-db ...
S'han trobat errors en processar:
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)
S'ha produït un error en la instal·lació del paquet. S'està intentant restablir.
Premeu retorn per continuar.
[/COLOR]

Bé, no me'n surto amb aquest trencat, ni amb reinstal·lació ni amb eliminació.
Algú té idea de que podría fer?

Moltes gracies per endavant.




[/COLOR][/COLOR]

---

### Post by CarlesOriol on 2009-11-13
i provant d'eliminar-lo amb el dpkg?

---

### Post by papapep on 2009-11-13
Crec recordar que fa temps vaig tenir algun sarau semblant amb un paquet i vaig acabar resolent-ho esborrant dins /var/lib/dpkg/info el fitxer postinst corresponent al que em donava maldecaps (en el teu cas postgresql).

Tot i això, abans podries provar a fer un:

```
sudo apt-get -f install
```

si falla, un:

```
sudo dpkg-reconfigure nomdelpaquet
```

i, si segueix fallant, prova a carregar-te el fitxer que t'he esmentat al principi, però fes-ne còpia abans, no et puc garantir que no et causi problemes derivats tocar-lo.

---

### Post by dsanchezfra on 2009-11-14
Hola, moltes gràcies als dos.

He provat de fer-ho esborrant directament amb el dpkg, amb sudo apt-get -f install i amb sudo dpkg-reconfigure postgresql-8.3. No he tingut resultats.
També he provat de esborrar l'arxiu postgresql-8.3.postinst al directori /var/lib/dpkg/info i el problema ha continuat. 
Finalment s'ha resolt esborrant tots els arxius que començaven amb postgresql-8.3. és a dir, els que tenien com a extensió:
- conffiles
- list
- md5sums
- postrm
- prerm
- postinst

Ara per fi ja no em surt el problema i si faig actualitzacions de sistema no em sur constantment l'errada.
El que no se es si em provocarà algun problema secundari, per si de cas he guardat tots els arxius.
Si hi ha novetats o comento.

Moltes gràcies de nou.

---

