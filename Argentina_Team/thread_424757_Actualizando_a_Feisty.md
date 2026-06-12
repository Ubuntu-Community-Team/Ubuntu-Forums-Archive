---
title: "Actualizando a Feisty"
date: 2007-04-27
forum: Argentina Team
---

### Post by jajajavi on 2007-04-27
Hace unos días que intento actualizar vía **Update Manager ** y en el diálogo  *Preparando la actualización * se queda trabado un rato largo en *Descargando archivo 134 de 140*. Finalmente me aparece:

**Error durante la actualización**

Ocurrió un problema durante la actualización. Normalmente es debido a algún tipo de problema en la red, por lo que le recomendamos que compruebe su conexión de red y vuelva a intentarlo.

Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/plf/dists/edgy/Release.gpg) No se pudo conectar a packages.freecontrib.org:80 (88.191.33.6); expiró el tiempo de conexión
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/free/i18n/Translation-es.bz2](http://packages.freecontrib.org/plf/dists/edgy/free/i18n/Translation-es.bz2) No se pudo conectar a packages.freecontrib.org:80 (88.191.33.6); expiró el tiempo de conexión
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/non-free/i18n/Translation-es.bz2](http://packages.freecontrib.org/plf/dists/edgy/non-free/i18n/Translation-es.bz2) No se pudo conectar a packages.freecontrib.org:80 (88.191.33.6); expiró el tiempo de conexión
Failed to fetch [http://ubuntu.geole.info/dists/edgy/universe/binary-amd64/Packages.gz](http://ubuntu.geole.info/dists/edgy/universe/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://b2cs.delcorp.org/debian/dists/edgy/main/binary-amd64/Packages.gz](http://b2cs.delcorp.org/debian/dists/edgy/main/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/edgy/multiverse/binary-amd64/Packages.gz](http://ubuntu.geole.info/dists/edgy/multiverse/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/Release](http://ubuntu.beryl-project.org/dists/edgy/Release) Unable to find expected entry  main-amd64/binary-amd64/Packages in Meta-index file (malformed Release file?)

¿Tengo algo mal en los repositorios (ya que agregué cosas) o es porque hay mucha gente tratando de hacer lo mismo?

---

### Post by Al_maverick on 2007-04-27
Me parece que el problema es que tenias muchos repositorios aparte de los standards. Deberías haberlos comentado antes de la actualizacion, o al menos eso es lo que entendi de las instrucciones de actualizacion.

Postea tu sources.list, eso puede dar una idea de donde esta el problema.

---

### Post by jajajavi on 2007-04-28
copio y pego:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## BACKPORTS REPOSITORY (Paquetes viejos, ya no incluidos en edgy y que pueden causar daño. Usar bajo su propia responsabilidad )

## PLF REPOSITORY (No soportados por ser privados y no libres) 
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Son paquetes ofrecidos por Canonical, no por Ubuntu
## Incluyen RealPlayer10, Opera, etc ) 

## xgl/beryl
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main-amd64
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main-amd64

#Added by software-properties
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS
deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) edgy misc
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted universe multiverse main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security restricted universe multiverse #Added by software-properties

## Medibuntu
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) edgy universe multiverse

#ntfs-3g
deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://b2cs.delcorp.org/debian/](http://b2cs.delcorp.org/debian/) edgy main
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

#debian.scribus.net - Primary repository
deb [http://debian.scribus.net/debian](http://debian.scribus.net/debian) edgy main restricted
deb-src [http://debian.scribus.net/debian](http://debian.scribus.net/debian) edgy main restricted
#debian.tagancha.org - Backup repository
deb [http://debian.tagancha.org/debian](http://debian.tagancha.org/debian) edgy main restricted
deb-src [http://debian.tagancha.org/debian](http://debian.tagancha.org/debian) edgy main restricted
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
deb-src [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb [http://viewizard.com/linux](http://viewizard.com/linux) debian/

#AUTOMATIX REPOS START
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main
#AUTOMATIX REPOS END

---

### Post by Al_maverick on 2007-04-29
Complicado el sources :D

Por lo que veo, tenes muchos repositorios ademas de los standard. Para hacer el upgrade, te recomendaria hacer una copia y dejar solo los repositorios propios de ubuntu. 

Una vez que termines la actualización, te recomendaría que te vuelvas a fijar en  cada lado si tienen repositorios para feisty, antes de descomentarlos.

```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## BACKPORTS REPOSITORY (Paquetes viejos, ya no incluidos en edgy y que pueden causar daño. Usar bajo su propia responsabilidad )

## PLF REPOSITORY (No soportados por ser privados y no libres)
#deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
#deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free

## CANONICAL COMMERCIAL REPOSITORY (Son paquetes ofrecidos por Canonical, no por Ubuntu
## Incluyen RealPlayer10, Opera, etc )

## xgl/beryl
#deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
#deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
#deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main-amd64
#deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main-amd64

#Added by software-properties
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS
#deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) edgy misc
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted universe multiverse main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security restricted universe multiverse #Added by software-properties

## Medibuntu
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
#deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) edgy universe multiverse

#ntfs-3g
#deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
#deb [http://b2cs.delcorp.org/debian/](http://b2cs.delcorp.org/debian/) edgy main
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

#debian.scribus.net - Primary repository
#deb [http://debian.scribus.net/debian](http://debian.scribus.net/debian) edgy main restricted
#deb-src [http://debian.scribus.net/debian](http://debian.scribus.net/debian) edgy main restricted
#debian.tagancha.org - Backup repository
#deb [http://debian.tagancha.org/debian](http://debian.tagancha.org/debian) edgy main restricted
#deb-src [http://debian.tagancha.org/debian](http://debian.tagancha.org/debian) edgy main restricted
#deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
#deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
#deb-src [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
#deb [http://viewizard.com/linux](http://viewizard.com/linux) debian/

#AUTOMATIX REPOS START
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main
#AUTOMATIX REPOS END
```

---

### Post by sebas.rhcp on 2007-04-29
Ojo que muchos que tenian tantos sources cuando actualizaron a feisty tuvieron muchos lios.

---

