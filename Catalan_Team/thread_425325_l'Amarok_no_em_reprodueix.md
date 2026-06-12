---
title: "l'Amarok no em reprodueix"
date: 2007-04-27
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-04-27
Des de la col·leció poso a que es carregui les cançons i no m'ho fa, dóna error.

Em diu que no té suport mp3 i no sé que més... i es queda atontat...

En canvi el Rythmbox per exemple em va..

---

### Post by Ferri on 2007-04-27
```
sudo apt-get install amarok-xine
```
Si no et funciona, afegeix les fonts de Medibuntu:
Per afegir la seva clau:
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```
Per afegir les fonts:
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
I finalment:
```
sudo apt-get update && sudo apt-get upgrade
```
Si no has pogut instal·lar abans l'amarok-xine, torna-ho a provar ara.

---

