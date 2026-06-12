---
title: "Problema amb instal·lació des de CDLive"
date: 2013-01-01
forum: Catalan Team
---

### Post by TRYCAS73 on 2013-01-01
Hola a tots.

   Fa poc me he decidit a instal•lar al meu equip Ubuntu 12.10 i no ho aconsegueixo. Vaig descarregar el CDLive de 32b i el de 64b. He comprovat la integritat de la ISO descarregada i la he cremat amb NERO a 2x. Entro en el Setup de la BIOS i modifico el Boot perquè comenci a llegir des de el DVD. Fico el DVD amb Ubuntu i comença a llegir el disc, surt una pantalla de color lila o morat amb dos dibuixets a la part inferior i al cap de una estona surt el nom d’UBUNTU i uns puntets a sota que van canviant de color fins que es queden clavats, al cap de uns segons el lector deixa de llegir, la única sortida passa per fer un reset.

   També he provat fent un ESC quant arrenca i entro en un mode text on selecciono F6 i APIC=off, noapic, nolapic, nomodeset i també he provat de arrencar el CD amb aquestes opcions marcades i el resultat es el mateix.

   Veient el procés en mode text puc seguir la instal•lació fins que s’atura on es poden llegir les ultimes files en las que surt això:
VFS: Close: file count is 0
Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000009
panic ocurred, switching back to tex console

No se que fer, necessito ajuda.

¡¡¡FELIÇ ANY 2013 I BONES FESTES!!!

---

### Post by irv on 2013-01-01
This is an English forum, but I used Google Translate to read your post.
First make sure you got a good download and it is not corrupt. 
Does your system have a 64 or 32 CPU. If a 64 then install that. When you are booting from the DVD give it time, it takes awhile to come to the install. This time will vary depending on the speed and amount of memory of your system. 
If you continue to have problems with 12.10, then try installing 12.04. They are both very good releases of Ubuntu.

---

### Post by TRYCAS73 on 2013-01-01
Thanks for reading my post, I also use the google translator, excuse my English is bad. This forum is not just for English-speaking people, this subforum is for people of Catalan.

I checked the integrity of the downloaded image using "md5sum" and the result has been good. I have also burned the image with the NERO program to x2, with subsequent verification errors.

The characteristics of my computer are:

-	Intel Pentium 4 **Dual Core 3.40GHz** **64Bits**
-	2 x 1GB= **2GB DDR**
-	Main Board ASUS P5LD2-SE
-	Graphics Card XFX Nvidia GeForce 6600 256Mb PCI-E
-	DVD RW GDR8163B ATA
-	DVD GSA-4167B ATA (Burner)
-	Audio Sound Max Integrated HD
-	2 x HD 250GB

I tried CDLive 12.04LTS and 12.10, 32-bit versions and 64-bit and the result is the same.

Thanks again for your help.

---

### Post by irv on 2013-01-01
I am thinking the problem is with the Graphics Card XFX Nvidia GeForce 6600 256Mb PCI-E. I don't have this card, but I have read somewhere of others having this problem. Maybe someone with this card could jump in if I am right about this being the problem. Someone should have an answer for you.

---

### Post by TRYCAS73 on 2013-01-02
Hola a tots.
 

    Ja he pogut resoldre el problema d'inici del CDLive. Era culpa d'una targeta de TV que tenia instal·lada.
 

    He instal·lat la versió 12.10 i ja la tinc en marxa. Ara m'ha sorgit un altre problema, el grub no inicia el W7 i no se com editar-lo.
 

 Gracies a tots.

---

### Post by irv on 2013-01-02
Glad to be of help. Thanks for marking this thread solved.

---

### Post by wgarcia on 2013-01-03
Respecte al problema que no es vegi el W7, si no has fet servir tot el disc per instal·lar l'Ubuntu, el W7 hauria de tenir una partició encara al disc. 

Per veure si és així, es pot obrir una terminal (ALT-F2 i entra "terminal" sense les cometes) i un cop oberta la terminal entra:

```
sudo fdisk -l
```

i prem INTRO. 

Aquí es podran veure les particions que hi ha al disc i si encara hi és la partició de W7.

---

### Post by TRYCAS73 on 2013-01-04
> **irv said:**
> Glad to be of help. Thanks for marking this thread solved.

   Thanks **Irv**, I too am glad collaboration from USA, it is very gratifying to find people willing to help efforts to understand other languages&#8203;&#8203;.

Excuse me if this translation is not valid, but I used the Google translator.

Greetings from Catalunya.

---

### Post by TRYCAS73 on 2013-01-04
> **wgarcia said:**
> Respecte al problema que no es vegi el W7, si no has fet servir tot el disc per instal·lar l'Ubuntu, el W7 hauria de tenir una partició encara al disc. 

Per veure si és així, es pot obrir una terminal (ALT-F2 i entra "terminal" sense les cometes) i un cop oberta la terminal entra:

```
sudo fdisk -l
```i prem INTRO. 

Aquí es podran veure les particions que hi ha al disc i si encara hi és la partició de W7.

Hola **wgarcia**.

                                     Gracies per la seva ajuda obro un altre fil ja que aquest ja esta resol i aixo es un altre problema diferent.

---

### Post by TRYCAS73 on 2013-01-04
Gracies

---

