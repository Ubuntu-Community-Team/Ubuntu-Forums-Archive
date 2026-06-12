---
title: "Wifi WPA2"
date: 2010-08-20
forum: Catalan Team
---

### Post by Daerun on 2010-08-20
Tenia el wifi en mode WEP, de manera que he pensat de canviar-ho a WPA2, per si les mosques... però ara em trobo que no tinc ni idea de com connectar-me amb el meu notebook a la xarxa 0_o

Configuració que he posat al router:

Network Authentication: WPA2
WPA2 Preauthentication: enabled
RADIUS Server IP Address: la ip del router
RADIUS Key: contrasenyabencomplexa
WPA Encryption: TKIP+AES

Aleshores, a l'ubuntu, em demana tipus d'autenticació > TLS, LEAP, TLS per túnel, o EAP protegit (PEAP). Ni idea.

Identitat anònima. Ni idea

Nom d'usuari (si selecciono LEAP em surt el nom de la xarxa, a part d'aixó, ni idea)

Contraseña: si poso la contrasenyabencomplexa no es conecta.

També per seleccionar Certificat d'usuari, de CA i Clau privada.


Ajudeta, si us plau :P

---

### Post by kimet on 2010-08-21
Jo utilitzo WPA2-PSK

Al router:

**WPA Pre-Shared Key**:  contrasenya

**WPA Group Rekey Interval**: 20 (temps que tarda en generar una contasenya nova, (pots posar-ne un altre))

**WPA Encryption**: AES

I al gestor de xarxes/tipus d'autenticació:

**WPA 1/2 preshared key**: contrasenya

I s'ha acabat el bròquil.

---

### Post by Daerun on 2010-08-22
Ah, genial, una hora barallant-m'hi y no era tan difícil :lol: Gràcies.

---

