---
title: "Having a problem with getting into sources.list"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by esocyn on 2007-02-09
Hey,

I'm trying to get into sources.list so I can edit it to add the PLF repository (so I can start playing rmvb files.) The problem is, I'll put in

```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```

and that prompts me to put in my password. I do and it simply goes back to my desktop command.

Then I put in

```
gksudo gedit /etc/apt/sources.list
```

and it will try to start the application, but a message pops up in terminal that says;

```
(gedit:28786): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

and then it kills the application start up.

I assume this means that I'm in some way putting my password in wrong, but that doesn't make any sense because I can get into the other administrative applications and my password works just fine.

WTH is going on? If I can't fix it in terminal, then how can I manualy add the repository?

ETA: I'm using Dapper Drake.

---

### Post by jd65pl on 2007-02-09
You could try adding it using a gui do the following.

*SYSTEM > ADMIN > SOFTWARE SOURCES*

Then just add your repo to the third party tab

---

### Post by esocyn on 2007-02-09
> **jd65pl said:**
> You could try adding it using a gui do the following.

*SYSTEM > ADMIN > SOFTWARE SOURCES*

Then just add your repo to the third party tab

SOFTWARE SOURCES = Software Properties?

---

### Post by meng on 2007-02-09
Yes, that is one way, or else try this:
sudo nano -B /etc/apt/sources.list

for a console-based text editor that is very easy to use.

---

### Post by jd65pl on 2007-02-09
> **esocyn said:**
> SOFTWARE SOURCES = Software Properties?
I'm using edgy and it states 'software sources' if you are using dapper it may have a different title but should still be fairly self explainatory

---

### Post by _simon_ on 2007-02-09
try just

```

sudo gedit /etc/apt/sources.list

```

---

### Post by esocyn on 2007-02-09
> **meng said:**
> Yes, that is one way, or else try this:
sudo nano -B /etc/apt/sources.list

for a console-based text editor that is very easy to use.

This worked! Thank you! :guitar:

---

### Post by esocyn on 2007-02-09
> **_simon_ said:**
> try just

```

sudo gedit /etc/apt/sources.list

```

When I do that, nothing pops up. It just goes right back to the Desktop command.

---

### Post by meng on 2007-02-09
I wish I knew why you can't run gedit: can you run it as a normal user (for another file, of course)?

---

### Post by ckaya on 2007-02-09
BTW, isn't PLF down now? Take a look at Medibuntu ([http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)) instead. 

For this kind of issues, Source-o-matic is a great tool too. ([http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/))

---

### Post by ckaya on 2007-02-09
> **meng said:**
> I wish I knew why you can't run gedit: can you run it as a normal user (for another file, of course)?

Has to do sth with: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

