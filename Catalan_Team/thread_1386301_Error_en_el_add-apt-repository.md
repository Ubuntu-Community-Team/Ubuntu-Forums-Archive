---
title: "Error en el add-apt-repository"
date: 2010-01-20
forum: Catalan Team
---

### Post by tanreb20 on 2010-01-20
Després de varies instalacions i coses varies alguna cosa he destrosssat :(

Quan intento fer un add-apt-repository m'apareix aixó:

```
[500][alorma:/home/alorma]$ sudo add-apt-repository ppa:ubuntu-wine/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 28, in <module>
    sp = SoftwareProperties(options)	
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```


Alguna idea de perqué? Que puc fer per arreglar-ho? I en el seu defecte, com pouc afegir aquets repositoris automaticament?

---

### Post by kukat on 2010-01-21
ostres noi....
t'he contestat a l'altre post com afegir els repositoris del karmic, però els missatges aquestos no sé el que volen dir.... 

Pareix com si no trobara l'arxiu "sources.list", o alguna cosa similar.
Tens l'arxiu al directori "/etc/apt/" ??

---

