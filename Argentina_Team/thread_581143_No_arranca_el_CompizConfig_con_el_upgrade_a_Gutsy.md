---
title: "No arranca el CompizConfig con el upgrade a Gutsy"
date: 2007-10-19
forum: Argentina Team
---

### Post by WanderingKnight on 2007-10-19
(Vale la pena aclarar que ya tenia el CompizConfig instalado antes de upgradear, si bien no lo usaba porque Compiz me andaba terriblemente lento)

Compiz ahora, con el upgrade, anda perfecto, pero tengo un problema: el CompizConfig no arranca. Puedo hacer andar el Compiz desde la consola, obviamente, pero no puedo configurarle los efectos (bah, podria hacerlo pero me queda un comando choclo terrible). Cuando lo trato de arrancar desde la consola me salta el siguiente error:

```
bilkis@bilkis:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

Alguna idea?

EDIT: Lo resolvi: tenia que desinstalar y volver a instalar, cuando lo hice apt agarro otros 500k asi que supongo que le faltaban algunas bibliotecas.

---

