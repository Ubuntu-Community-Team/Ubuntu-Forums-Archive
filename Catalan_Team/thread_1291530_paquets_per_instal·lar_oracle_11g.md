---
title: "paquets per instal·lar oracle 11g??"
date: 2009-10-14
forum: Catalan Team
---

### Post by pserra on 2009-10-14
hola,
encara estic intentant instal·lar oracle 11g
i em surten molts pàquets per instal·lar, he mirat al synaptic i si tinc 
un pàquet es una versio antiga..... he provat de fer update desde el terminal  i no em troba rés...
alguna suggerència?
es estrany qie faltin tants pàquets.... en el meu Ubuntu  9.04

Merci

---

### Post by pserra on 2009-10-14
em deixava la captura de pantalla...
Merci

---

### Post by kentchicken on 2009-10-15
Hola, no m'en recordo exactament pero crec que tinc la versió 10g instalada en un hardy i m'anava força be amb el paquet que vaig baixar de oracle.
Jo provaria d'actualitzar (estas a la 7.10 no?)
Sort
Kent

---

### Post by pserra on 2009-10-19
Hola,
la meva versio es la 9.4 i tornoa  deisxar 'pantallasso' amb els paquets 
faltants.... he provat 3 paquets desde el ternimal i no me'ls instal·la..
alguna suggerencia??
Merci

---

### Post by papapep on 2009-10-19
> he provat 3 paquets desde el ternimal i no me'ls instal·la..
alguna suggerencia??

Sí, que ens ajudis una mica a poder-te ajudar, Pere. 
Si executes una ordre i no funciona com creus que ha d'anar, _cal que ens posis exactament la ordre i la resposta_ (o la no resposta) del sistema.

Al volcat de pantalla que has posat abans no s'hi veu absolutament res (com a mínim jo no distingeixo la lletra).

L'oracle 11g aquest porta documentació sobre com instal·lar-lo? parla de l'Ubuntu? o és genèrica?
Has mirat llocs com aquest: [http://oracleabc.com/b/?p=167](http://oracleabc.com/b/?p=167) a veure si et serveixen?

Si no ens dónes alguna pista, poc podem fer per tu.

---

### Post by pserra on 2009-10-21
Hola Papapep,
molt bo l'enllaç,
però tinc 2 problemes.... si l'executo el runInstaller des de el usuari creat oracle em surt un error  que no te permmisos de ..../Orainventori que esta al meu perfil......con ho canvio? per mi, ho agafa perque he provat de fer alguna instalació fustrada anteriorment a aquest directori...

Executo desde el meu perfil, aquest error ja l'evito  i em surt un error que no havia vist mai de un directori X11 i de un arxiu xlock.... ho he mirat i es un relotge!!

Adjunto sortida terminal:


pere@pere-portatil:/home/database$  ./runInstaller 
Starting Oracle Universal Installer...

Checking Temp space: must be greater than 80 MB.   Actual 3599 MB    Passed
Checking swap space: must be greater than 150 MB.   Actual 2878 MB    Passed
Checking monitor: must be configured to display at least 256 colors
    >>> Could not execute auto check for display colors using command /usr/X11R6/bin/xdpyinfo. Check if the DISPLAY variable is set.    Failed <<<<

Some requirement checks failed. You must fulfill these requirements before

continuing with the installation,

Continue? (y/n) [n] y


>>> Ignoring required pre-requisite failures. Continuing...
Preparing to launch Oracle Universal Installer from /tmp/OraInstall2009-10-22_12-11-09AM. Please wait ...
DISPLAY not set. Please set the DISPLAY and try again.
Depending on the Unix Shell, you can use one of the following commands as examples to set the DISPLAY environment variable:
- For csh:  			% setenv DISPLAY 192.168.1.128:0.0
- For sh, ksh and bash: 	$ DISPLAY=192.168.1.128:0.0; export DISPLAY
Use the following command to see what shell is being used:
	echo $SHELL
Use the following command to view the current DISPLAY environment variable setting:
	echo $DISPLAY
- Make sure that client users are authorized to connect to the X Server.
To enable client users to access the X Server, open an xterm, dtterm or xconsole as the user that started the session and type the following command:
% xhost +
To test that the DISPLAY environment variable is set correctly, run a X11 based program that comes with the native operating system such as 'xclock':
	% <full path to xclock.. see below>
If you are not able to run xclock successfully, please refer to your PC-X Server or OS vendor for further assistance.
Typical path for xclock: /usr/X11R6/bin/xclock

---

### Post by papapep on 2009-10-21
Pere, aquí t'està dient què hauries de fer i provar:

> DISPLAY not set. Please set the DISPLAY and try again.
Depending on the Unix Shell, you can use one of the following commands as examples to set the DISPLAY environment variable:
- For csh: % setenv DISPLAY 192.168.1.128:0.0
- For sh, ksh and bash: $ DISPLAY=192.168.1.128:0.0; export DISPLAY
Use the following command to see what shell is being used:
echo $SHELL
Use the following command to view the current DISPLAY environment variable setting:
echo $DISPLAY
- Make sure that client users are authorized to connect to the X Server.
To enable client users to access the X Server, open an xterm, dtterm or xconsole as the user that started the session and type the following command:
% xhost +
To test that the DISPLAY environment variable is set correctly, run a X11 based program that comes with the native operating system such as 'xclock':
% <full path to xclock.. see below>
If you are not able to run xclock successfully, please refer to your PC-X Server or OS vendor for further assistance.
Typical path for xclock: /usr/X11R6/bin/xclock

Per cert, vols dir que l'Oracle aquest és programari lliure? per que si no ho és, no hauríem d'estar tractant això aquí. El problema no és de l'Ubuntu en sí :)

---

### Post by pserra on 2009-10-22
Tens rao Papapep,
estem sortint de contexte...
Merci

---

