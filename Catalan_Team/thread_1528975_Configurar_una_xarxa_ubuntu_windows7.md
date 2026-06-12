---
title: "Configurar una xarxa ubuntu windows7"
date: 2010-07-11
forum: Catalan Team
---

### Post by karto_on on 2010-07-11
hola, 

vull configurar una xarxa local amb ubuntu i windows 7.
les maquines es veuen, pero no puc accedir-hi.
m'he intsl·lat el samba... pero no hi ha manera.
el curiós es que hi ha hagut un moment en que de win7 a linux podia entrar, pero despres de remenar molt pel que he pogut llegir, ara ja no hi puc entrar :(

em dona aquest error:

No s'ha pogut muntar l'ubicació.
No s'ha pogut recuperar la llista de compartits del servidor

abans em donava aquest altre:

DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

alguna idea?

---

### Post by kukat on 2010-07-12
mitjançant Samba?????
Doncs crec que tens que tocar alguna cosa del registre de Windows 7. 

[http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)

Si prems a l'enllaç que hi ha en eixa secció del wiki de Samba, et baixes un arxiu (".reg") que et modifica l'arxiu per tu.

---

### Post by karto_on on 2010-07-14
[FONT=Arial]Hola, 
soc una mica limitadet, vagi per davant. aquest arxiu on l'he d'instal·lar? perquè el path:
[/FONT][FONT=Arial]HKLM \ System \ CCS \ Services \ LanmanWorkstation \ Parameters

no correspon ni al win7 ni a l'ubuntu...

s'ha d'instal·lar l'arxiu o modificar algun arxiu del registre amb els paràmetres:

[LEFT]DWORD  DomainCompatibilityMode = 1[/LEFT] DomainCompatibilityMode DWORD = 1
[LEFT]DWORD  DNSNameResolutionRequired = 0[/LEFT] DNSNameResolutionRequired DWORD = 0


el servei [/FONT][FONT=Arial]LanmanWorkstation és de windows o d'ubuntu?

buff... quin merder...es complicat això del linux, eh? :p
[/FONT]

---

### Post by kukat on 2010-07-14
vas al "Executar" de Windows i poses
"regedit"

I t'eixirà l'arxiu del registre de Windows 7


Però no et recomane que toques eixe arxiu. Millor executa l'arxiu ".reg" que hi ha a l'enllaç que t'he passat, no siga cosa que espatlles el registre de Win7.

L'arxiu ".reg" és aquest: [https://bugzilla.samba.org/attachment.cgi?id=4988&action=view](https://bugzilla.samba.org/attachment.cgi?id=4988&action=view)
deuria de deixar-te executar-lo, però també pot donar problemes (la paranoia aquesta de les darreres versions de Windows que no aprofita per a res....) 

Després, si no et funciona, igual tens que fer alguna cosa de permisos que hi ha al Windows7
[http://www.linuxplanet.com/linuxplanet/tutorials/6911/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6911/1/)




Et recomane que li pegues una mirada al tutorial de Samba: 
[http://www.ziddu.com/download/8495803/UbuntuCatalanTeam_SAMBA.pdf.zip.html](http://www.ziddu.com/download/8495803/UbuntuCatalanTeam_SAMBA.pdf.zip.html)

---

