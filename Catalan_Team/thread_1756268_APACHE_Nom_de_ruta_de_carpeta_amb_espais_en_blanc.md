---
title: "APACHE Nom de ruta de carpeta amb espais en blanc"
date: 2011-05-12
forum: Catalan Team
---

### Post by xangai on 2011-05-12
Tinc problemes amb l'arxiu "default" del servidor APACHE . La ruta de la carpeta conté espais en blanc (a sota teniu les rutes amb problemes). No trobo la forma de que reconegui els espais en blanc. He posat la barra inclinada a la dreta, la barra inclinada a l'esquerra, cometes simples i dobles, i res, quan executo la comanda 'localhost' al navegador no troba la carpeta.

La solució podria ser canviar els noms de la carpeta, però com podeu deduir estan creades a VIRTUALBOX, m'obligaria a esborrar la instal.lació del VIRUTALBOX el Windows i las aplicacions que allà tinc instal.lades. Si és possible no m'agradaria fer aquests passos.

Aquesta carpeta de execució de les pàgines web la vull tenir al VIRTUALBOX per què així les probo en windows i en UBUNTU.

Gràcies pel vostre ajut

[FONT="Times New Roman"]DocumentRoot */home/vicenc/VirtualBox VMs/VIRTUALBOX Compartir/www*
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory */home/vicenc/VirtualBox VMs/VIRTUALBOX Compartir/www*/>[/FONT]

---

### Post by wgarcia on 2011-05-12
Crear un enllaç simbòlic no t'ho arreglaria?

ln -s <nom carpeta existent amb espais> <nom sense espais>

i usar <nom sense espais> al fitxer de configuració.

---

### Post by xangai on 2011-05-12
> **wgarcia said:**
> Crear un enllaç simbòlic no t'ho arreglaria?

ln -s <nom carpeta existent amb espais> <nom sense espais>

i usar <nom sense espais> al fitxer de configuració.

Gràcies WGARCIA.

Per veure si això que em recomanes funciona estic fent els enllaços simbòlics. A la primera carpeta en ordre de jerarquia (VirtualBox VMs) la consola m'ha agafat l'enllaç, però per a la segona carpeta, que està dins de la primera quan executo la comanda "ln" em diu que no la troba. He provat aquestes dues opcions, havent fet primer el simbòlic de la primera carpeta en ordre de jerarquia (VirtualBox Vms):

      ln -s VirtualBox\ VMs/VIRTUALBOX\ Compartir VirtualBoxVMS/VIRTUALBOXCompartir
      - aquí em diu:
              en crear l’enllaç simbòlic «VirtualBoxVMs/VIRTUALBOXCompartir»: No such file or directory


ln -s VIRTUALBOX\ Compartir VIRTUALBOXCompartir
      - aquí crea un enllaç trencat a la mateixa carpeta a la que pertany VirtualBox VMs (és a dir, no dins de VirtualBox Vms sino "al costat").

Serà algún tipus d'error sintàctic ¿oi?

Gràcies.

---

### Post by xangai on 2011-05-12
Ja ho he solucionat. Quan feia la segona execució del "ln" a la consola no havia entrar en la carpeta primera i per això no trobava la segona carpeta. Bé total quin embolic de carpetes. Fent això ho he solucionat, és a dir entrant a la carpeta /VirtualBoxVms: 

   :~/VirtualBoxVMs$ ln -s VIRTUALBOX\ Compartir VIRTUALBOXCompartir

---

