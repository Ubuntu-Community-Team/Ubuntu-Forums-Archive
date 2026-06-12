---
title: "no login for gnome"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by supahfly on 2005-07-10
I have problems creating an account
I login cmd line with root and do

useradd -g adm -u 100 -s /bin/bash -p ubuntu supahfly

it gives no errors, but I cannot login with it :-(
can anyone help me pleasee

---

### Post by asimon on 2005-07-10
[QUOTE=supahfly]
useradd -g adm -u 100 -s /bin/bash -p ubuntu supahfly
[/QUOTE]

What happens if you try to login? Authentification failure?

If you expect the password to be 'ubuntu' you are wrong. The -p option is to be followed by the encrypted password. The easiest would be to omit '-p ubuntu' completly and do 'passwd sypahfly' afterwards to set the password.

And you specify the userid to be 100. Are you sure you want this? On my Ubuntu system user id 100 exists already for the postfix mail transfer agent. You don't want a system service and a user to have the same user id.

BTW there is a convenient GUI tool to manage user and groups easily. I think it's somewhere under the Sytem menu as "User & Groups". I can't check the exact location right now because I am on a different computer (without gnome) right now.

---

### Post by supahfly on 2005-07-10
that's the problem, I cannot login anymore into gnome, because root cannot login into gnome standard. I'll try without the -p option first and then do passwd

---

### Post by supahfly on 2005-07-10
Ok, so that worked :-)
but now I have some other errors in gnome, I'll copy paste :

GConf fout: Geen databank beschikbaar om configuratie naar op te slaan: Niet mogelijk om de waarde van sleutel '/apps/nautilus/preferences_version' op te slaan, omdat de configuratieserver geen schrijfbare databases heeft. Er zijn een aantal gemeenschappelijke redenen voor dit probleem: 1) Het configuratiebestandpad /etc/gconf/2/path bevat geen databases of werd niet gevonden. 2) Er zijn per ongeluk 2 gconfd processen gestart. 3) Uw besturingssysteem is verkeerd geconfigureerd waardoor NFS bestandsblokkering niet werkt op uw persoonlijke map. 4) Uw NFS-machine is gecrashed en heeft de server niet juist laten weten op reboot dat de bestandsblokkeringen opgeheven moesten worden. Als u 2 gconfd processen heeft (of 2 had op het moment dat de tweede werd gestart), kan uitloggen en alle kopieën van gconfd killen helpen. Als u verouderde blokkeringen heeft, verwijder dan ~/.gconf*/*lock. Misschien is het probleem dat u GConf vanaf 2 machines tegelijk probeert te gebruiken en ORBit nog zijn standaardconfiguratie heeft dat CORBA verbindingen tegenhoudt - zet "ORBIIOPIPv4=1" in /etc/orbitrc. Zoals gewoonlijk, bekijk de user.* syslogs voor details over problemen die gconfd tegenkwam. Er kan maar Ã©Ã©n gconfd zijn per thuismap en het moet zijn eigen blokkeringsbestand in ~/.gconfd plaatsen en ook blokkeringsbestanden voor individuele opslaglocaties zoals ~/.gconf

so thats in dutch that sucks ...
But anyone perhaps knows what the problm is ?

---

### Post by sooqing on 2005-07-10
[QUOTE=supahfly]Ok, so that worked :-)
but now I have some other errors in gnome, I'll copy paste :

GConf fout: Geen databank beschikbaar om configuratie naar op te slaan: Niet mogelijk om de waarde van sleutel '/apps/nautilus/preferences_version' op te slaan, omdat de configuratieserver geen schrijfbare databases heeft. Er zijn een aantal gemeenschappelijke redenen voor dit probleem: 1) Het configuratiebestandpad /etc/gconf/2/path bevat geen databases of werd niet gevonden. 2) Er zijn per ongeluk 2 gconfd processen gestart. 3) Uw besturingssysteem is verkeerd geconfigureerd waardoor NFS bestandsblokkering niet werkt op uw persoonlijke map. 4) Uw NFS-machine is gecrashed en heeft de server niet juist laten weten op reboot dat de bestandsblokkeringen opgeheven moesten worden. Als u 2 gconfd processen heeft (of 2 had op het moment dat de tweede werd gestart), kan uitloggen en alle kopieën van gconfd killen helpen. Als u verouderde blokkeringen heeft, verwijder dan ~/.gconf*/*lock. Misschien is het probleem dat u GConf vanaf 2 machines tegelijk probeert te gebruiken en ORBit nog zijn standaardconfiguratie heeft dat CORBA verbindingen tegenhoudt - zet "ORBIIOPIPv4=1" in /etc/orbitrc. Zoals gewoonlijk, bekijk de user.* syslogs voor details over problemen die gconfd tegenkwam. Er kan maar Ã©Ã©n gconfd zijn per thuismap en het moet zijn eigen blokkeringsbestand in ~/.gconfd plaatsen en ook blokkeringsbestanden voor individuele opslaglocaties zoals ~/.gconf

so thats in dutch that sucks ...
But anyone perhaps knows what the problm is ?[/QUOTE]
 i dun know dutch, i got something like that msg.

first, at the grub screen, choose the second option (recovery mode)

u will be able to login as root using cli..

add ur new user account. BEWARD, create a home dir for this new user and chmod its permissions to 777 (i was caught at this)

passwd this account

u can now login to it.

---

