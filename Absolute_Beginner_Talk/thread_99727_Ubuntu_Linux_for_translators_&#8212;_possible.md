---
title: "Ubuntu Linux for translators &#8212; possible?"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by esperantisto on 2005-12-06
I've given several tries to Linuxes, now I'm trying Ubuntu 5.10. Well, it's a curious toy. But what about real work? I'm interested in particular in software for translators. Here's what exxentially needed:

[COLOR="Red"]a)[/COLOR] Office suite (first of all, word processor and spreadsheet programs). Not a big problem with [OpenOffice.org]("http://www.openoffice.org"). The only bad new is that quite many clients require MS Office formats &#8212; and OOo cannot produce them 100% good. Particularly, there are problems with graphics and other OLE objects (I judge on the basis of OOo for Window).

[COLOR="Red"]b)[/COLOR] Computer-aided translation software. Again, not a big problem: there's [OmegaT]("http://www.omegat.org/omegat/omegat.html"). Not as sophisticated as Trados or Deja Vu X or other heavyweights, but already quite good for freelance translators.

[COLOR="Red"]c)[/COLOR] Electronic dictionaries. This is a **[COLOR="Red"]BIG[/COLOR]** problem. Not that there are no dictionaries at all, but they are not fit to professional translation needs. I'd like to know, if there's anything like [Lingvo]("http://www.lingvo.ru") for Linux?

So, I mean, a good dictionary program should:
[LIST]
[*]allow more sophisticated syntax than just word - translation:
[LIST]
[*]multiple translation with separation by sences;
[*]comments, explanations etc;
[*]sub-articles for particlar expressions;
[*]examples of usage;
[*]cross-references to other articles.
[/LIST]
[*]allow multiple dictionaries: to differentiate by topics;
[*]have full text search capabilities (in source words, translations, comments, examples etc);
[*]allow creation of user dictionaries with full set of above-mentioned capabilities.
[/LIST]

Does anyone know a good dictionary? Also, other comments to the topic are welcome.

---

### Post by sethmahoney on 2005-12-06
I don't know offhand if there is a good translator's dictionary available for Linux, but you might try (if you have a copy) seeing if you can get the Windows versions of your favorite software running in Linux using Wine (which can get an awful lot of Windows programs running under Linux).

---

### Post by esperantisto on 2005-12-07
I certainly will try. But this should be a matter of concern for developers. Yes, Linux is good for servers. Yes, it's quite good for word processing. But other areas of use are still Windows domain.

---

### Post by Perfect Storm on 2005-12-07
You could try to add this to the repo list and see if the final version of OO2 is better:
```
sudo gedit  /etc/apt/sources.list
```

add:
[b]# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./[/b]

Another option is to get M$ Office to run on Linux with **Crossover office** [http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by esperantisto on 2005-12-07
I thought, OOo2 bound with Ubuntu was final! Unfortunately, I've got Ubuntu on a machine not connected to Internet and can't use your advise. I've been OOo user for quite long (of Windows vesion, however), including almost all pre-1.9/2.0 versions, and must say, both in OOo2 final and in OOo pre-2.0.1, compatibility with MSO is not perfect. I know, OOo developers are not to blame &#8212; but tell that to customers!

Anyway, the major problem is not about text editing &#8212; it's about dictionaries.

---

