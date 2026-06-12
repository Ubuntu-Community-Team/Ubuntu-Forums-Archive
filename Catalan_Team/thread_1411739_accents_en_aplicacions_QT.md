---
title: "accents en aplicacions QT"
date: 2010-02-20
forum: Catalan Team
---

### Post by epileg on 2010-02-20
Bones,

Algú te ho ha tingut problemes en introduir els accents en una aplicació QT dins d'un entorn gnome?

El problema és que quan premo una tecla d'accent, aquesta no espera a que a posteriori premi la lletra a on s'ha d'afegir l'accent i l'imprimeix sense més, o sigui que no actuen com a «dead keys».

En canvi, si copio i enganxo text amb accents a una aplicació QT, ho fa sense problemes.

Algú te una solució a aquest problema?

Gràcies,

---

### Post by papapep on 2010-02-20
Sembla que sigui un error encara pendent de solucionar:

[https://bugs.launchpad.net/ubuntu/+source/ibus-qt/+bug/481612](https://bugs.launchpad.net/ubuntu/+source/ibus-qt/+bug/481612)

---

### Post by epileg on 2010-02-20
Gràcies,

Per si a algú li interessa, he trobat una manera de solucionar-ho temporalment. Cal executar l'aplicació així:

$ XMODIFIERS= QT_IM_MODULE= aplicació_qt

A mi em funciona.

Salut,

---

### Post by orestesmas on 2010-02-20
> **epileg said:**
> Bones,

Algú te ho ha tingut problemes en introduir els accents en una aplicació QT dins d'un entorn gnome?

El problema és que quan premo una tecla d'accent, aquesta no espera a que a posteriori premi la lletra a on s'ha d'afegir l'accent i l'imprimeix sense més, o sigui que no actuen com a «dead keys».

En canvi, si copio i enganxo text amb accents a una aplicació QT, ho fa sense problemes.

Algú te una solució a aquest problema?

Gràcies,

Et passa des de no fa gaire, oi?

Fes
```

sudo im-switch -s default-xim
sudo im-switch -s default

```

i suposo que se t'arreglarà

---

### Post by epileg on 2010-02-21
Gràcies Orestes per la resposta però a mi no m'ha funcionat.

Salut,

---

