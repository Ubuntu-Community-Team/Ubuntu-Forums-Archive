---
title: "Maldito beryl BIS, Maldita placa"
date: 2007-03-14
forum: Argentina Team
---

### Post by jayflower on 2007-03-14
No se porque beryl tira este error ... :(
Ya instale el openchrome, tengo una placa via s3 ( las que traen los mothers ASRock).
No se si sera que tenia que usar AIGLX o XGL. ya habia agregado el beryl al startup.

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x46
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
libGL warning: 3D driver claims to not support visual 0x46
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by felipelerena on 2007-03-14
es que tenes que hacer la segunda parte del tutorial que te mande, la parte que dice "si no anda el 3D"

---

### Post by jayflower on 2007-03-14
ahora lo tengo que hacer de nuevo porque reconfigure de nuevo la placa "a mano" (me quede sin X server). Tengo que instalar de nuevo el Openchrome supongo.
igual ya estoy de nuevo con mi usuario. Grande Ubuntu!

 dpkg-reconfigure xserver-xorg

---

