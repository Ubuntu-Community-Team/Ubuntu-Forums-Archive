---
title: "problems with visual effects"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Willye on 2007-11-22
Hi friends, i'm in appearance preferences->visual effects and i'm trying to enable Extra, but appear this error: Desktop effects could not be enabled,  the question is why ?

---

### Post by Willye on 2007-11-22
who knows what is happend

---

### Post by Willye on 2007-11-22
andddd ????????????

---

### Post by spiderbatdad on 2007-11-22
i get that too. I think my graphics card is too old or not supported, but I was still able to get compiz working with xserver and xgl.

---

### Post by fairuz27 on 2007-11-22
Have u tried enable your graphic card?
Go to System > Administration > Restricted Driver Manager and enable it from there

---

### Post by tomcat1_12 on 2007-11-22
which graphic card are you using?

---

### Post by Willye on 2007-11-22
Have u tried enable your graphic card?
Go to System > Administration > Restricted Driver Manager and enable it from there

I HAVE IN: SYSTEM->ADMINISTRATION THESE OPTIONS:
KEYRING MANAGER
NETWORK TOOLS
PRINTING
SYSTEM LOG
SYSTEM MONITOR
UPDATE MANAGER
no more options are there, i have a question, is mandatory to have a special graphical card
i have a normal computer without any special graphical card

---

### Post by fairuz27 on 2007-11-22
Maybe u missing some of the item??

Try go to System/Preference/Main Menu
On left pane select administration  and check item on the right pane

---

### Post by spiderbatdad on 2007-11-22
That doesn't look like a menu from 7.10 are you running Fiesty? It doesn't even look complete for Fiesty. Something appears to be amiss.

---

### Post by overdrank on 2007-11-22
> **Willye said:**
> Have u tried enable your graphic card?
Go to System > Administration > Restricted Driver Manager and enable it from there

I HAVE IN: SYSTEM->ADMINISTRATION THESE OPTIONS:
KEYRING MANAGER
NETWORK TOOLS
PRINTING
SYSTEM LOG
SYSTEM MONITOR
UPDATE MANAGER
no more options are there, i have a question, is mandatory to have a special graphical card
i have a normal computer without any special graphical card

HI since you decided to create a new thread I will ask the same questions as before
Post the output of this command in the terminal ```
lspci
``` And what version of ubuntu are you using?

---

### Post by Willye on 2007-11-22
Maybe u missing some of the item??

Try go to System/Preference/Main Menu
On left pane select administration and check item on the right pane


i'm trying to select some options but when i select the options its automatically deselected, why, or how to install these options

---

### Post by Willye on 2007-11-22
i ran lspci, but the problem continue: Desktop effects could not be enabled

---

### Post by overdrank on 2007-11-22
> **Willye said:**
> i ran lspci, but the problem continue: Desktop effects could not be enabled

Post the output of the lspci command and we can help if we know what the graphics card is. The output will tell us :KS
And what version of ubuntu????

---

### Post by Willye on 2007-11-22
I'm using Ver 7.10 i rna lspci but it doesn't fix the problem:
Desktop effects could not be enalbed

---

### Post by Ub1476 on 2007-11-22
The command "lspci" will tell us what hardware you have on your computer. Just write it in the terminal and post the output here (copy, paste). 

I guess you're administrator too, right (also called root)?

---

### Post by spiderbatdad on 2007-11-22
Overdrank is asking you to "post" the output of the terminal when you enter lspci in the terminal. Just copy and paste it into this thread.

---

### Post by Willye on 2007-11-22
this is the display when run the command:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
00:10.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
00:11.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)

---

### Post by overdrank on 2007-11-22
> **Willye said:**
> this is the display when run the command:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
00:10.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
00:11.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)

HI and I don't believe you can run the effects on a virtual machine.

---

### Post by Willye on 2007-11-22
then, if i'am running linux under VMware the special efects doesn't work ?
is it definitely or there is any solution ?

---

### Post by kevin11951 on 2007-11-23
personally i think, it sounds like he is using a non root user (as in he created another user after install, and uses that)... when ever i log onto a different user name, i get that short list, because you just aren't allowed to do anything else.

EDIT: sorry didnt read where he says virtual machine!

---

