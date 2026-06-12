---
title: "Problem with Synaptic"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by jeanvial on 2006-06-09
Hi.

I have a proble with Synaptic.
-------------------------------

When I want to start the Synaptic i can not because appear the following window:

E: Abriendo /etc/apt/sources.list - ifstream::ifstream (2 No existe el fichero o el directorio)
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.

-------------------------------
Well a will try to traslate this problem.

it say that can not open  "/etc/apt/sources.list - ifstream::ifstream" because the files are not in these location and doesnt exist.

Escuse me bad English.

I hope that you understand me. I am Mexican.

---

### Post by Dragonfire on 2006-06-09
Spanish AP student here.

okay, try 

> appt-get-update.

that should fix your synaptic, and if not, click the link in my signature, and email the email address on the main page of that site. and one of the LCT tech's will email you back within usually 10 minutes or less.site. and one of the LCT tech's will email you back within usually 10 minutes or less.

BTW! use [www.freetranslation.com](www.freetranslation.com)

It will help you translate if you need it.

---

### Post by nanotube on 2006-06-09
[QUOTE=jeanvial]Hi.

I have a proble with Synaptic.
-------------------------------

When I want to start the Synaptic i can not because appear the following window:

E: Abriendo /etc/apt/sources.list - ifstream::ifstream (2 No existe el fichero o el directorio)
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.

-------------------------------
Well a will try to traslate this problem.

it say that can not open  "/etc/apt/sources.list - ifstream::ifstream" because the files are not in these location and doesnt exist.

Escuse me bad English.

I hope that you understand me. I am Mexican.[/QUOTE]

please run this command:
```
ls -al /etc/apt/sources.list
```
and post the output here. it SHOULD look like this:
```
-rw-r--r--  1 root root 2382 2006-05-31 16:30 /etc/apt/sources.list
```
if it doesn't, run command
```
sudo chmod 644 /etc/apt/sources.list
```
and then try running synaptic again.

i have seen similar posts before, where some dapper upgrade has messed up the permissions on sources.list. i think this will fix it up.

---

### Post by jeanvial on 2006-06-09
Hi

Ok i will try it.

Thanks

---

