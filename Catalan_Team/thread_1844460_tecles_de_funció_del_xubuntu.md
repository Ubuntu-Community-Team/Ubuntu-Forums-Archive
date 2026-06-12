---
title: "tecles de funció del xubuntu"
date: 2011-09-15
forum: Catalan Team
---

### Post by josep-maria on 2011-09-15
Quan he configurat el xubuntu no he trobat on puc assignar les tecles de funció, vull dir fer que F2 sigui la carpeta meva, F4 tancar la finestra, etc. He mirat i remirat els menús i no ho he trobat.

---

### Post by Toz on 2011-09-15
Just ran your question through google translate, so I'm hoping it got the right translation.

There are two places for keyboard shortcuts in Xubuntu.
1. **Settings->SettingsManager->WindowManager->Keyboard** - here you can view the existing window management shortcuts.
2. **Settings->SettingsManager->Keyboard->ApplicationShortcuts** - here you can set user-specific shortcuts.

---

### Post by josep-maria on 2011-09-20
Ja havia mirat a: ajustaments > gestor d'ajustaments > teclat > dreceres, però només hi ha set línies que diuen coses que no entenc, com ara: xfce4, o xflock4, o xfrun4. Suposo que s'hi pot afegir les ordres que vull, però què hi haig d'escriure? Jo volia que F2= carpeta meva, F3= internet, F9= apagar pc, i F12= tancar finestra.

---

### Post by Toz on 2011-09-20
Use the following commands:

```
F2 = exo-open --launch FileManager
F3 = exo-open --launch WebBrowser
F9 = dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown

or

F9 = dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

(The first F9 command is for older ubuntus, the second F9 command is for 11.04 and newer).

Alt-F4 will close the currently focused window.

---

### Post by josep-maria on 2011-09-28
Quan entro a 'teclat' i faig clic a 'afegeix', surt una finestra petita que es diu 'drecera d'ordre'. Faig clic a 'obre' i surt una llista. Hi trobo exo-open, hi faig clic. Torna a la finestra 'drecera d'ordre', faig clic a 'd'acord'. Surt una altra finestreta que es diu 'drecera d'ordre'. I aquí s'atura tot, no es pot dir d'acord ni ficar-hi cap lletra.

---

### Post by Toz on 2011-09-28
When you click add, instead of clicking on open, simply copy and paste the commands from above into the text field. Then, when you press OK, the box will wait for a keypress combination that will be the shortcut key.

For example, for F2 shortcut:
1. Click "Add"
2. Copy/paste "exo-open --launch FileManager" (no quotes)
3. Click "OK"
4. Press F2

---

### Post by Miquel Ubuntero on 2011-10-01
Dear Toz.
This is the Catalan Team forum.
You should better use Catalan language, please.
Best regards,
Miquel Adroer.
;)

---

### Post by Toz on 2011-10-01
I'm sorry, but I do not speak Catalan. I have been using google translate to translate the questions. If you so wish, I will no longer respond to this thread.

---

### Post by josep-maria on 2011-10-05
Dear Toz,

I've done what you said and it works. Thanks a lot. What about closing a window? Can we use F12 instead of altF4? Thanks a lot again.

---

### Post by Toz on 2011-10-05
Install the program **wmctrl**.
```
sudo apt-get install wmctrl
```

Then follow the previous instructions for creating a keyboard shortcut, but instead, use the following command to close the active window:
```
wmctrl -c :ACTIVE:
```

-------------------------------------------------------------------------------------------
[COLOR="Blue"]Instal leu el programa **wmctrl**.
```
sudo apt-get install wmctrl
```

A continuació, seguiu les instruccions anteriors per crear una drecera de teclat, però en el seu lloc, utilitzeu la següent comanda per tancar la finestra activa:
```
wmctrl -c :ACTIVE:
```[/COLOR]

---

### Post by josep-maria on 2011-10-10
I've done so, and it works. Thank you.

---

### Post by josep-maria on 2011-10-10
I've done so and it works. Thnak you.

---

