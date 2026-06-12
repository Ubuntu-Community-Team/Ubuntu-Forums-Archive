---
title: "Ubuntu i Blu-Ray"
date: 2009-07-21
forum: Catalan Team
---

### Post by dafaktor on 2009-07-21
Salutacions companys.

Un servidor acaba de renovar el seu projector per un d’alta definició; per si a algú li interessa, és un Sanyo PLV-Z3000.

Bé, el tema és que ara estic reproduint des del PC, mitjançant VLC i voldria continuar així, fent servir el PC.

Per aconseguir-ho necessitaria renovar la màquina, de forma que la gràfica sigui la què s’encarregui de la major part de la decodificació, com ara ja està fent la Radeon 9600 amb el MPEG2  dels DVDs.

Sabeu si des de Ubuntu 9.04 podré reproduir Blu-Ray?

Actualment faig servir VLC però en la pàgina web no he vist que suporti el codec VC-1, que és el què es fa servir en els Blu-Ray.

Suposo que si faig servir MPlayer, que al seu torn fa servir ffmpeg, que usa libavcodec, que suporta VC1, sí que podré llegir-los….

Si fos així, actualitzaria el PC tot i que em sortís una mica més car que un reproductor de sobretaula.

Algun consell sobre placa base, CPU i gràfica? Pel què fa a la gràfica, suposo que escolliria alguna Nvidia pel tema del VDPAU (integrada o no en la PB).

Gràcies !!

---

### Post by ffp on 2009-07-30
Hola,

Mplayer no reprodueix BluRay, al menys en les proves que he fet aconsegueixo veure les imatges, però sense so.
VLC 1.0, sembla que si que ho farà, però encara no es a repositoris.
De fet es pot carregar una versió PPA [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) , jo ho penso provar el proper cap de setmana.
Respecte a VDPAU, jo no el faig servir, el meu HTPC amb Mythbuntu 9.04 64bits, gràfica nvidia 8400GS, sense VDPAU i amb processador AMD Athlon X2 Dual Core 5050E 2.6Ghz, mou els fitxers mkv a 1080p amb total facilitat, i amb la CPU al 50% aprox. VDPAU es incompatible amb alguns programes de gestió de capturadores de TV.

---

### Post by ffp on 2009-08-01
Confirmat,
VLC 1.0.1 carregat des del PPA reprodueix correctament, àudio i vídeo, el BluRay que he provat, sense menús per cert, tot i que reconeix els capitols. De fet es tracta d'un fitxer gravat al disc dur amb la estructura BluRay i fitxer STREAM amb extensió .m2ts.

---

### Post by dafaktor on 2009-08-08
merci per la info ffp, ho tindré en compte.

---

