---
title: "Problemes a l'actualitzar Azureus"
date: 2007-03-22
forum: Catalan Team
---

### Post by jraulbc on 2007-03-22
Hola,

És el primer cop que escric al fòrum i espero que em pugueu ajudar. Tinc l'Azureus instal·lat al meu Ubuntu Edgy Eft. Avui m'ha sortit una finestra per a que actualitzara el programa i a l'acabar el procés m'ha donat un error:

[INDENT]Error
Version 2.1.4 of plugin 'azplugins'
failed to install - /opt/azureus/plugins/
azplugins/azplugins_2.1.4.jar
(Permission denied) [/INDENT]

Em dona la impressió que el que ha passat és que al gravar l'arxiu en el directori no ha pogut per que no tinc permisos per escriure-hi.

Una altra dada que pot ser siga important és que l'Azureus el vaig instal·lar amb l'Automatix.

Gràcies per endavant!

jraulbc

---

### Post by CarlesOriol on 2007-03-23
Es clar que amb permisos d'usuari no et permet fer modificacions al programa.

Jo et recomano que esperis a la propera versió que se t'instal·li automàticament des del teu gestor de paquets (si l'automatix funciona com els apt-get / aptitude / adept / synactic).

Si fos una actualització molt crítica sempre pots iniciar-lo amb sudo (sudo azuerus) i amb permisos d'administrador permetre al programa actualitzar-se tot i que això és posar la seguretat del sistema a l'alçada d'un sistema privatiu de redmon.

---

### Post by jraulbc on 2007-03-26
Hola de nou,

Desprès de llegir en la llista d'Ubuntucat-info que no recomanaven utilitzar Automatix ni Easyubuntu més que per a allò que no es possible instal·lar amb els recursos pròpis d'Ubuntu (seria el cas dels drivers d'Nvidia o els codecs propietaris) he desinstal·lat Azureus amb l'Automatix i l'he tornat a instal·lar amb l'Afegeix/Elimina. Em funciona igual que abans i per ara no m'ha mostrat cap finestra d'actualització. Si tingués algun altre problema us ho tornaria a comentar. Gràcies i fins ara,

jraulbc

---

