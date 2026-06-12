---
title: "opengl and jpeg"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by jsmidt on 2006-03-31
I am installing an application that says I need the opengl and jpeg headers and libraries.  Which packages are they?

---

### Post by ubuntumaneh on 2006-03-31
[QUOTE=jsmidt]I am installing an application that says I need the opengl and jpeg headers and libraries.  Which packages are they?[/QUOTE]

Try looking at apt-cache:

apt-cache search opengl | grep opengl
apt-cache search jpeg|grep jpeg

But I believe you need a specific library for the language your application is build upon.

---

