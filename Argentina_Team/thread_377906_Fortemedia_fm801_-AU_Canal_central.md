---
title: "Fortemedia fm801 -AU Canal central"
date: 2007-03-06
forum: Argentina Team
---

### Post by Vndecid on 2007-03-06
Buenas otra vez yo , me compre una fortemedia fm801 (43 morlacos) con varias salidas (6 canales) , creo que fue lo mejor quie hice en mi vida ^^ pero la macana es que el canal central no funca el de atras si los de enfrente tambien pero los centrales (centro y subwoofer ) no ...preguntaba si alguien tenia alguna idea de como se hace para que esto funque desde ya muchas gracias

---

### Post by felipelerena on 2007-03-07
que chip tiene?

---

### Post by Vndecid on 2007-03-07
La misma que todos XD...no se como decirte el chip...la verdad
Te tiro la parte del lsmod

ppp_generic            28180  6 pppoe,pppox
slhc                    7552  1 ppp_generic
nls_iso8859_1           4352  2 
nls_cp437               6016  2 
vfat                   13440  2 
fat                    54556  1 vfat
lp                     11972  0 
[COLOR="Red"]snd_via82xx_modem      15496  0 
snd_fm801              20384  5 
snd_tea575x_tuner       4352  1 snd_fm801[/COLOR]
i2c_viapro              8980  0 
nvidia               6827412  32 
[COLOR="Red"]snd_ac97_codec         96672  2 snd_via82xx_modem,snd_fm801
snd_ac97_bus            2432  1 snd_ac97_codec[/COLOR]
videodev                9728  1 snd_tea575x_tuner
af_packet              21768  4 
i2c_core               22288  3 i2c_ec,i2c_viapro,nvidia

y lo que dice "Administrador d dispiositivos" es una

Xwave QS3000A Fm801

y hasta ahi llego jejeje

Espero que alguien me pueda constestar por que esta linda la placa para ver Evangelio en Ac3 :lolflag:  :P

nos vemos
DESDE YA MUCHAS GRACIAS

---

### Post by felipelerena on 2007-03-08
lo que haria yo:

1) buscar en este foro a ver si ahy algo
2) buscar en google
3) la pagina del fabricante
4) ver si hay algun bug reportado en launchpad
5) ver si hay algun bug en alsa
6)la mentarme por no haber comprado una marca mas "conocida" y haberme fijado si era compatible con linux.

creo que si seguis todos esos pasos lo vas a solucionar. contanos como va tu progreso.

---

### Post by Vndecid on 2007-03-08
Ok lo voy a ser ..igual se buscar en google solamete que configure varias cosas de mi maquina y como me costo trabajo buscando y mirando quise acortar camino preguntando si alguien tiene la misma placa ...No dudes que si lo soluciono voy a poner como lo solucione ;-)..

GRACIAS 

PD: El chipset es C-Media 8738(de una Noga net sound card jeje)

---

### Post by Vndecid on 2007-03-08
Zankukoku na tenshi no youni !!!..se se SeeeeeEEE!!!1 anda ..es facil hacerlo
se tiene que hacer estos pasos

1-Crear el archivo en /home/usuario/.asoundrc
2-Copiar en este lo siguiente

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

3-Control+Alt+Backscape para reiniciar el modo grafico yincluso ALSA ... y ejecuten el totem ...jeje...JEJEJEJE ...JEJEJE :D...Nos vemos CIAO!

---

