---
title: "Italian keyboard layout"
date: 2005-02-05
forum: Apple PPC Users
---

### Post by Caesar on 2005-02-05
Italian layout is active and setted up as the default layout.... but still my italian iBook keyboard isn't mapped well.

W\w instead of Z\z, ò\ç instead of m\M.... and so on, any help?

---

### Post by Leonida on 2005-02-20
[QUOTE=Caesar]Italian layout is active and setted up as the default layout.... but still my italian iBook keyboard isn't mapped well.

W\w instead of Z\z, ò\ç instead of m\M.... and so on, any help?[/QUOTE]
 Same problem, please help.
Thanks in adavance .L.

---

### Post by robsta on 2005-02-20
Maybe you have luck there:
[http://lists.debian.org/debian-powerpc/2002/08/msg00259.html](http://lists.debian.org/debian-powerpc/2002/08/msg00259.html)

BTW, this is the first google result when searching for "ibook italian keymap"

- Rob

---

### Post by Leonida on 2005-02-21
[QUOTE=robsta]Maybe you have luck there:
[http://lists.debian.org/debian-powerpc/2002/08/msg00259.html](http://lists.debian.org/debian-powerpc/2002/08/msg00259.html)

BTW, this is the first google result when searching for "ibook italian keymap"

- Rob[/QUOTE]
Thanks a lot for your google search, perhaps this link is also useful:
[http://www.gnuraghe.org/?Articoli:Installare_Ubuntu_4.10_su_iBook_G3_500](http://www.gnuraghe.org/?Articoli:Installare_Ubuntu_4.10_su_iBook_G3_500)
> **Tastiera fuori dall'ambiente grafico**

per poter scrivere alcuni caratteri è necessario l'uso dell'alt-gr tasto che manca nella tastiera del nostro adorato iBook. È tuttavia possibile risolvere questo problema modificando la mappa dei caratteri caricata durante il boot. Per rendere più semplice il tutto potete usare quella creata da me:[ ibook-it.map](http://www.gnuraghe.org/?download=ibook-it.zip)

a questo punto occorre copiarla nella cartella "/usr/share/keymaps/i386/qwerty/" e modificare il file "/etc/init.d/keymap.sh" come segue:

#CONFFILE=${CONFDIR}/${CONFFILEROOT}.${EXT}.gz
CONFFILE=/usr/share/keymaps/i386/qwerty/ibook-it.map

Le modifiche saranno attive automaticamente ad ogni avvio dell'iBook. Tuttavia se si vuole verificare che tutto funzioni è possibile eseguire il seguente comando:
```
sudo /etc/init.d/keymap.sh restart
```
Read more in the link above.

I'll try as soon as possible.

---

### Post by Leonida on 2005-02-22
[QUOTE=Leonida]I'll try as soon as possible.[/QUOTE]
I didn't install _ibook-it.map_ I just set in [COLOR=Navy]System ->Preference->Keyboard[/COLOR], on Layouts tab:
**Keyboard model**: Generic 101-key PC
**Layout**: Italian

It work fine with my iBook G4 933mhz Hoary 5.04.
To get: **# @[ ]** use _cmd (Apple)_ key instead of Alt-gr key.

It work also on Live CD.

Screenshot at the end of this [page](http://www.freesmug.org/newsitems/news065)

---

### Post by andreabg on 2005-03-07
Hello everyone,

I've got the same problem for my Ibook Se 466 graphite.

I've found the solution:

in System ->Preference->Keyboard, on Layouts tab I've selected:
macintosh - No decription

Layout:
Italian

So now my qzerty italian keyboard (also called Olivetti type) the one with M/m besides L/l works properly.

Andrea

---

### Post by Caesar on 2005-03-08
Thanks, it works!! \\:D/

---

