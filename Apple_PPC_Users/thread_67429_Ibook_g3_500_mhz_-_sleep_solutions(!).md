---
title: "Ibook g3 500 mhz - sleep solutions(!?)"
date: 2005-09-20
forum: Apple PPC Users
---

### Post by MArco_ubuntu on 2005-09-20
Hi to all!
I have a g3 dual usb and 1 firewire !

The sleep (suspend-to-ram) no wake up.

I have tried two script solution :

This :

[http://www.gnuraghe.org/?Articoli:Installare_Ubuntu_4.10_su_iBook_G3_500](http://www.gnuraghe.org/?Articoli:Installare_Ubuntu_4.10_su_iBook_G3_500) 

```
#!/bin/sh
# this file is /etc/apm/scripts.d/dbus-1
# hald prevents proper resume after sleep-wake cycle
# stopping dbus at suspend and restarting at resume
# fixes this
INIT="/etc/init.d/dbus-1"
[ -x "${INIT}" ] || exit 0
case "${1},${2}" in
(suspend,*)
"${INIT}" stop
echo "stopped dbus-1"
;;
(resume,suspend)
"${INIT}" start
echo "started dbus-1"
;;
esac
exit 0




sudo chmod 755 /etc/apm/scripts.d/dbus-1

creare i seguenti link simbolici eseguendo i comandi:

cd /etc/apm/suspend.d/
sudo ln -s /etc/apm/scripts.d/dbus-1 98dbus-1
sudo ln -s /etc/apm/scripts.d/dbus-1 01dbus-1 
``` 


And this solution that "usually" work but not ever 
I copy and paste the test because I doest have the link 

```

create this files callled   /etc/hal/fdi/local_disablecdrom.fdi 


<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
	<device>
		<match key="block.device" string="/dev/hdb">
			<merge key="storage.media_check_enabled" type="bool">false</merge>
		</match>
	</device>
</deviceinfo>


``` 

Disable suspend :
That can be done by stopping pbbuttons 

/etc/init.s/pbbuttonsd stop

But I found more helpful Install powerpref and configure the system for black-screen insted suspend-by-ram

An other think that I found very hopefull is pblevel
Whit this tool you can set the luminosity of your Display (an othe good idea for long battery life)

Thanks to the developer  of laptop-mode for help and suggestion.
I hope that can help 

Bye

ps: Can be a great idea make a script that auto-set the luminosity of screen (if you not use the fblevel can be 1 insted that 12)

---

### Post by RIVE on 2005-09-20
[QUOTE=MArco_ubuntu]Hi to all!
I have a g3 dual usb and 1 firewire !

The sleep (suspend-to-ram) no wake up.

I have tried two script solution :

This :

[http://www.gnuraghe.org/?Articoli:Installare_Ubuntu_4.10_su_iBook_G3_500](http://www.gnuraghe.org/?Articoli:Installare_Ubuntu_4.10_su_iBook_G3_500) 

```
#!/bin/sh
# this file is /etc/apm/scripts.d/dbus-1
# hald prevents proper resume after sleep-wake cycle
# stopping dbus at suspend and restarting at resume
# fixes this
INIT="/etc/init.d/dbus-1"
[ -x "${INIT}" ] || exit 0
case "${1},${2}" in
(suspend,*)
"${INIT}" stop
echo "stopped dbus-1"
;;
(resume,suspend)
"${INIT}" start
echo "started dbus-1"
;;
esac
exit 0




sudo chmod 755 /etc/apm/scripts.d/dbus-1

creare i seguenti link simbolici eseguendo i comandi:

cd /etc/apm/suspend.d/
sudo ln -s /etc/apm/scripts.d/dbus-1 98dbus-1
sudo ln -s /etc/apm/scripts.d/dbus-1 01dbus-1 
``` 


And this solution that "usually" work but not ever 
I copy and paste the test because I doest have the link 

```

create this files callled   /etc/hal/fdi/local_disablecdrom.fdi 


<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
	<device>
		<match key="block.device" string="/dev/hdb">
			<merge key="storage.media_check_enabled" type="bool">false</merge>
		</match>
	</device>
</deviceinfo>


``` 

Disable suspend :
That can be done by stopping pbbuttons 

/etc/init.s/pbbuttonsd stop

But I found more helpful Install powerpref and configure the system for black-screen insted suspend-by-ram

An other think that I found very hopefull is pblevel
Whit this tool you can set the luminosity of your Display (an othe good idea for long battery life)

Thanks to the developer  of laptop-mode for help and suggestion.
I hope that can help 

Bye

ps: Can be a great idea make a script that auto-set the luminosity of screen (if you not use the fblevel can be 1 insted that 12)[/QUOTE]
 I had the same problem, I resolvit with this instructions 

[http://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39](http://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39)

Hope works for you to.

---

### Post by MArco_ubuntu on 2005-09-21
No,I doest work :-/

i have removed HAL and now the sleep work but I need to mount manually the driver..

Ok... It's a big price but the sleep work ever corrtly

---

