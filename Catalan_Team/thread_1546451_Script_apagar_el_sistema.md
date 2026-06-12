---
title: "Script apagar el sistema"
date: 2010-08-05
forum: Catalan Team
---

### Post by tanreb20 on 2010-08-05
Hola!

M'estic fent un petit script per poder programar l'apagada del sistema...

Pero em demana permisos de root, i no sé com fer per donar-li al script, ja que no el vui executar desde consola sino amb alt+f2

```
#!/bin/bash
gksu apagar
temps=$(/usr/bin/zenity --entry --text="Quants minuts (Num) o Quina hora vols apagar? (hh:mm)" --entry-text="10")
segur=$(/usr/bin/zenity --question --text="N'estas segur d'apagar l'ordiandor en $temps minuts?")
if [ $? -eq 0 ]
	then
		sudo shutdown -h $temps
	else
		exit
fi

```

PD: Ja de pas algun consell per millorar el script?

---

### Post by kimet on 2010-08-05
Per que hi poses el gksu? shutdown no cal que s'executi com a root si esta així defenit a /etc/sudoers, com sol ser habitual.

---

### Post by tanreb20 on 2010-08-05
Script:

```
#!/bin/bash
temps=$(/usr/bin/zenity --entry --text="Quants minuts (Num) o Quina hora vols apagar? (hh:mm)" --entry-text="10")
segur=$(/usr/bin/zenity --question --text="N'estas segur d'apagar l'ordiandor en $temps minuts?")
if [ $? -eq 0 ]
	then
		sudo shutdown -h $temps
		notify-send -i /usr/share/icons/gnome/32x32/apps/gnome-terminal.png "Shutdown en $temps minuts"
	else
		exit
fi

```

/etc/sudoers:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%alorma ALL=(ALL) ALL

```

Esta correcte?

PD: COm puc fer apareixe notificacions a l'hora que en el temrinal anirien sortint les alertes?

---

### Post by kimet on 2010-08-05
Has afegit aquesta linia? %alorma ALL=(ALL) ALL
Es millor donar al teu usuari privilegis per a executar nomes l'ordre shutdown.
 
 sota de:
 # User privilege specification
 root	ALL=(ALL) ALL
 
Afegeixes:
 
```
el_teu_usuari ALL=NOPASSWD:/sbin/shutdown
```

Aixó dona privilegis al teu usuari per executar shutdown al terminal sense ser root
(revisa el manual de sudoers per estar segur)

Sobre notify no en tinc ni idea.

Salut

---

### Post by xtort on 2010-08-07
&

---

### Post by tanreb20 on 2010-08-07
Xtort... t'expliques?XD

---

### Post by kimet on 2010-08-08
M'he descarregat el notify i funciona be, no el coneixia.

Al teu script hi falta encadenar els diàlegs de zenity per que es tanquin quan es sel.leciona "no" o "cancel.lar", sinó s'executarà sempre.

```
#!/bin/bash


function segur()
{
segur=$(/usr/bin/zenity --question --text="N'estas segur d'apagar l'ordiandor en $temps minuts?")
srtseg=`echo $?`	
}

temps=$(/usr/bin/zenity --entry --text="Quants minuts (Num) o Quina hora vols apagar? (hh:mm)" --entry-text="10")
srttmp=`echo $?`

if [ $srttmp == 0 ]
	then
	segur
else
	exit
fi
if [ $srtseg == 0 ]
	then
		sudo shutdown -h $temps
		notify-send -i /usr/share/icons/gnome/32x32/apps/gnome-terminal.png "Shutdown en $temps minuts"
	else
		exit
fi
```

Salut

---

### Post by tanreb20 on 2010-08-08
Vale... m'ho expliques?XD

---

### Post by kimet on 2010-08-08
> **tanreb20 said:**
> Vale... m'ho expliques?XD



```
#!/bin/bash



*#declaro la funció segur amb el dialeg de zenity question*

function segur()
{
segur=$(/usr/bin/zenity --question --text="N'estas segur d'apagar l'ordiandor en $temps minuts?")
#`[I]echo $?` captura el codi de sortida, no el valor que posem en minuts, atenció als accents. 
#zenity retorna el valor 0 si tot a anat bé i 1 si alguna cosa ha fallat, en aquest cas si hagues 
#clicat "cancelar" hauria retornat "1"[/I]
srtseg=`echo $?`	
}

*#declaro la variable temps, podria haver-ho fet amb una altre funció...*

temps=$(/usr/bin/zenity --entry --text="Quants minuts (Num) o Quina hora vols apagar? (hh:mm)" --entry-text="10")
*#capturo el codi*
srttmp=`echo $?`
#*si el codi de sortida de "temps" és 0 continua amb la funcio "segur" si no, surt del programa* 

if [ $srttmp == 0 ]
	then
	segur
	else
		exit
fi

*# si la sortida de segur es igual a 0 s'executa l'ordre que hi ha a continuació, si no, sortir*
if [ $srtseg == 0 ]
	then
		sudo shutdown -h $temps
		notify-send -i /usr/share/icons/gnome/32x32/apps/gnome-terminal.png "Shutdown en $temps minuts"
	else
		exit
fi

```

OK?

PD. Ara et toca posar-hi una alarma que avisi quan falta un minut per apagar.XD

---

