---
title: "[SOLVED] claredat tipus de lletra"
date: 2007-09-11
forum: Catalan Team
---

### Post by tnemilc on 2007-09-11
Salutacions, ubuntaires
Fa tan sols uns dies (durant aquest cap de setmana llarg), he instal·lat ubuntu feisty fawn, juntament amb el W$ (de moment). LLevat de uns quants maldecaps amb el wifi, que ja he resolt, voldria saber si hi ha alguna utilitat per millorar la claredat dels caràcters que em surten en pantalla i en gairebé tots els programes (firefox, thunderbird, aquest post, openoffice, etc), a l'estil del cleartype de w$. I ja que hi sóc, també estic interessat en alguna utilitat per controlar i millorar la connexió wifi al meu router.

---

### Post by papapep on 2007-09-11
Respecte la "claredat" dels caràcters, i sense més informació per la teva part (no sé què és ni què fa el Cleartype) puc pensar que és un problema de configuració de la tarja gràfica el qual fa que no ho vegis tan bé com ho hauries de veure. Més quan parles de que no és un programa, sinó un munt.

I respecte la "millora de la connexió wifi", què vols dir? un programa que sigui més fàcil o entenedor que el Network-manager que porta per defecte Ubuntu? fa uns dies va sortir un fil que parlava d'un programa anomenat Wicd que fa aquesta feina:

[http://ubuntuforums.org/showthread.php?t=543547](http://ubuntuforums.org/showthread.php?t=543547)

---

### Post by tnemilc on 2007-09-12
He trobat les opcions "tipus de lletra" en l'apartat preferències del sistema i ja he pogut millorar la definició. (la funció Cleartype és nativa dels sistemes windows i permet millorar la visualització dels caràcters). Quant a la wifi, vull dir si coneixeu d'algun programari estil network-manager que doni més informació sobre la connexió, per exemple.
tot i això, gràcies. miraré el Wicd.

---

### Post by CarlesOriol on 2007-09-12
ves a consola i prova:

sudo iwlist scanning

sudo iwconfig

Tens un munt de comandes iwlist, iwconfig, ifconfig... tu mateix

---

### Post by CarlesOriol on 2007-09-12
> **tnemilc said:**
> He trobat les opcions "tipus de lletra" en l'apartat preferències del sistema i ja he pogut millorar la definició. (la funció Cleartype és nativa dels sistemes windows i permet millorar la visualització dels caràcters). Quant a la wifi, vull dir si coneixeu d'algun programari estil network-manager que doni més informació sobre la connexió, per exemple.
tot i això, gràcies. miraré el Wicd.

El suavitzat dels caracters (ja sigui per pixels sencers o subpixels com el cleartype) el pots activar a opcions tipus de lletra com has fet. Sols has de tenir en compte que si engegues el kde et caldrà fer-ho també en aquell entorn al Centre de control (kcontrol) -> Aparença -> Fonts.

***Nota: Per tal que el seguiment dels missatges sigui més clar poseu una sola pregunta per tema ja que si no tenim un poti-poti creuat de respostes***

---

### Post by orestesmas on 2007-09-13
A més de tot el que t'han suggerit, cal que t'asseguris que la resolució que tens posada a la tarja gràfica és la mateixa que la del monitor TFT, sinó ho veuràs borrós facis el que facis. Els LCD/TFT només accepten bé les resolucions idèntiques a les seves pròpies. La resta les interpolen i es veuen fatal.

---

