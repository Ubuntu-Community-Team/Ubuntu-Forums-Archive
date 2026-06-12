---
title: "ubuntu won't start after beryl install"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-02-27
please help after intalling beryl ubuntu loads to about 95% then stalls ikow that i can get into the terminal as root by pressing esc at startup  can anyone help with removing beryl to start again.

---

### Post by ed-j on 2007-02-27
Caution: Reply from Novice!

Please see _[COLOR="DarkOrchid"]www.psychocats.net/ubuntu/index[/COLOR]_ The Terminal command will be something like [COLOR="SeaGreen"]sudo aptitude remove Beryl[/COLOR] But please check this or another site first.

Best I can do! Good Luck!

Failing that, please read the Sticky by Brunellus at the top of the first forum page!

---

### Post by fongs on 2007-02-27
> **ed-j said:**
> Caution: Reply from Novice!

Please see _[COLOR="DarkOrchid"]www.psychocats.net/ubuntu/index[/COLOR]_ The Terminal command will be something like [COLOR="SeaGreen"]sudo aptitude remove Beryl[/COLOR] But please check this or another site first.

Best I can do! Good Luck!

Failing that, please read the Sticky by Brunellus at the top of the first forum page!

cheers champ thanks for quick response have u used this

---

### Post by ed-j on 2007-02-27
Hey!

Only to remove KDE, and I've just remembered something, you may need to put [COLOR="SeaGreen"]-desktop[/COLOR] at the end. Ooops!

---

### Post by fongs on 2007-02-27
> **ed-j said:**
> Hey!

Only to remove KDE, and I've just remembered something, you may need to put [COLOR="SeaGreen"]-desktop[/COLOR] at the end. Ooops!

will this allow ubuntu start again

---

### Post by ed-j on 2007-02-27
If the command is correct, you'll have to restart to make the change. Please check with Psychocats.

---

### Post by Scarlett on 2007-02-27
Omg, ed-j have you made friends with the terminal now?  lol

---

### Post by ed-j on 2007-02-27
Try KDE, Gnome and Xfce: If your machines got the beans, then *you've* got the means!

---

### Post by fongs on 2007-02-27
> **ed-j said:**
> Try KDE, Gnome and Xfce: If your machines got the beans, then *you've* got the means!

and what will this do  to help me with beryl

---

### Post by ed-j on 2007-02-27
> **fongs said:**
> and what will this do  to help me with beryl

Apologies, that message was meant for scarrlet. Please resume with your original questions.

---

### Post by fongs on 2007-02-27
> **ed-j said:**
> Apologies, that message was meant for scarrlet. Please resume with your original questions.

i'm in ubuntu, kernel 2.6.17- generic (recovery mode) wil that command work from there

---

### Post by Scarlett on 2007-02-27
Looks like you've got more beans than me, ed-j.  You must be doing something right.  ;)

fongs, wish I could help but my beryl install went very smooth and I don't have enough experience to help with anything I haven't struggled through.

---

### Post by ed-j on 2007-02-27
Please resume with #3.

---

### Post by fongs on 2007-02-27
> **ed-j said:**
> Please resume with #3.

All i got from that was 'this aptitude does not have super cow powers'

---

### Post by ed-j on 2007-02-27
Then the command is incomplete. Please see #3.

---

### Post by Scarlett on 2007-02-27
> **fongs said:**
> All i got from that was 'this aptitude does not have super cow powers'

This is not in any way helpful but kind of interesting....

"...some have alluded that the reference to "super cow powers" means APT is able to import packages from newer releases of Debian (such as testing << unstable)."
[http://www.eeggs.com/items/36008.html](http://www.eeggs.com/items/36008.html)

---

### Post by fongs on 2007-02-27
> **fongs said:**
> i'm in ubuntu, kernel 2.6.17- generic (recovery mode) wil that command work from there

is it possible to remove beryl from recovery mode

---

### Post by fongs on 2007-02-27
> **Scarlett said:**
> This is not in any way helpful but kind of interesting....

"...some have alluded that the reference to "super cow powers" means APT is able to import packages from newer releases of Debian (such as testing << unstable)."
[http://www.eeggs.com/items/36008.html](http://www.eeggs.com/items/36008.html)

does anyone knw how to remove beryl from recovery mode please help

---

### Post by PriceChild on 2007-02-27
> **fongs said:**
> does anyone knw how to remove beryl from recovery mode please help```
sudo apt-get remove --purge beryl-dbus beryl-plugins-extra-dbg beryl-plugins-extra aquamarine-dbg aquamarine-dev aquamarine beryl-core-dbg beryl-core beryl-dev beryl-manager beryl-plugins-data beryl-plugins-dbg beryl-plugins-unsupported-dbg beryl-plugins-unsupported beryl-plugins beryl-settings-bindings beryl-settings-simple beryl-settings beryl emerald-dbg emerald heliodor-dbg heliodor-dev heliodor libberyldecoration-dev libberyldecoration0 libberylsettings-dev libberylsettings0-dbg libberylsettings0 libemeraldengine0-dbg libemeraldengine0
```Should do the job

---

### Post by ed-j on 2007-02-27
> **PriceChild said:**
> ```
sudo apt-get remove --purge beryl-dbus beryl-plugins-extra-dbg beryl-plugins-extra aquamarine-dbg aquamarine-dev aquamarine beryl-core-dbg beryl-core beryl-dev beryl-manager beryl-plugins-data beryl-plugins-dbg beryl-plugins-unsupported-dbg beryl-plugins-unsupported beryl-plugins beryl-settings-bindings beryl-settings-simple beryl-settings beryl emerald-dbg emerald heliodor-dbg heliodor-dev heliodor libberyldecoration-dev libberyldecoration0 libberylsettings-dev libberylsettings0-dbg libberylsettings0 libemeraldengine0-dbg libemeraldengine0
```Should do the job

[COLOR="SeaGreen"]Many thanks![/COLOR]

---

### Post by fongs on 2007-02-27
> **ed-j said:**
> [COLOR="SeaGreen"]Many thanks![/COLOR]

yes that worked thakks for alll the support but unfortunatly  Ubuntu would not star so a reeboot was in order thanks again.

---

