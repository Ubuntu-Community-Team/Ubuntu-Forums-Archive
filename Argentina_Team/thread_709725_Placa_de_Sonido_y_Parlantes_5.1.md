---
title: "Placa de Sonido y Parlantes 5.1"
date: 2008-02-27
forum: Argentina Team
---

### Post by tzulberti on 2008-02-27
Hola. Una consulta: alguien usa parlantes 5.1 en su placa de sonido y no tuvo problemas? Yo tengo una placa onboard que ya de por si trae problemas con linux (es un asus m2n-e sli). Me quiero comprar unos parlantes 5.1, y quisiera saber si conocen alguna placa de sonido donde simplemente conectando los parlantes todo el resto funcione...

Gracias,
TZ

---

### Post by Hei Ku on 2008-02-27
yo tengo un msi k8 y con la placa de sonido onboard no tengo problemas. te podes fijar en el alsa-mixer si ves los parlantes traseros cuando la pasas a modo 5.1

---

### Post by tzulberti on 2008-02-28
El problema lo tiene la placa de sonido. Los linuxes no me la detectan bien, por lo que solo puedo escuchar un unico sonido a la vez... Por eso, para ahorrarme problemas prefiero comprarme una placa de sonido que sea compatible con linux.

---

### Post by kaiju on 2008-02-28
creo que poder escuchar un unico sonido a la vez es una problema con la configuracion de alsa (hardware / software mixing).

---

### Post by pol666 on 2008-02-28
Casi odas las placas funcionan, el problema no es de Ubuntu ni  de ningun Linux sino de ALSA cuando te compres los 5.1 

hace una cosa....
bri una terminal y pone

**gedit ~/.asoundrc**

Te sale el editor de texto y copias esto y luego guardas

> #########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. 


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

---

### Post by faktorqm on 2008-02-28
Yo tengo un MSI K7N2G-L con nforce 2 y anda bien. tiene drivers de nvidia igual el chipset para linux, capaz sea por eso. Salu2!

---

