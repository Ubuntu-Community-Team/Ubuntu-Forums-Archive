---
title: "Battery Boost, estalvi de bateria"
date: 2009-03-29
forum: Catalan Team
---

### Post by jinglada on 2009-03-29
En el [Packard Bell, EASYNOTE MT85-M-005SP]("http://support.packardbell.com/es/item/?m=home&pn=PC18E01904"), el teclat inclou damunt la línia de de les tecles de funció una tira metàlica que anomena "[Panel de control]("http://support.packardbell.com/es/item/index.php?i=instr_ic_controlpanel_yamit_steele&ppn=PC18E01904")" en la que a més del botó de potència hi ha un botó que anomena "[BatteryBoost]("http://support.packardbell.com/es/item/index.php?i=spec_ic_batteryboost&ppn=PC18E01904")" per a activar/desactivar l'estalvi de bateria, que en Ubuntu no funciona i en Windows si.

Qué hauria de fer per a activar el Battery Boost?

---

### Post by PatrickVogeli on 2009-03-30
prem el boto varies vegades i despres fes un dmesg. Mira si a les ultimes linies hi apareix alguna cosa que hi diu setkeycode bla bla.

Un altra cosa que pots fer es obrir el programa acpi_listen i pitjar-lo, a veure si t'el reconeix.

ja diras algo

---

### Post by jinglada on 2009-03-30
> **PatrickVogeli said:**
> prem el boto varies vegades i despres fes un dmesg. Mira si a les ultimes linies hi apareix alguna cosa que hi diu setkeycode bla bla.

Un altra cosa que pots fer es obrir el programa acpi_listen i pitjar-lo, a veure si t'el reconeix.

ja diras algo

Prement el botó vàries vegades i fent un **dmesg** no apareix cap vegada la paraula **setkeycode** en les 511 línies mostrades pel Terminal.

En canvi l'**acpi_listen** dóna el següent:
joan@joan-laptop:~$ acpi_listen
hotkey ATKD 000000ac 00000009
hotkey ATKD 000000ac 0000000a
hotkey ATKD 000000ac 0000000b

Ja em diràs si puc fer res més.
Salut i gràcies.

---

### Post by PatrickVogeli on 2009-03-31
hi deu haver alguna manera de desvincular aquesta tecla de ser un event acpi i per tant poder-la assignar al que volguem, pero de moment aixo se m'escapa. De fet, aixo de l'acpi es força complicat.

salut!

---

