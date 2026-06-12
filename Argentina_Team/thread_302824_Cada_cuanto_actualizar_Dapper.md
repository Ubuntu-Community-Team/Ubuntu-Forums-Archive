---
title: "Cada cuanto actualizar Dapper?"
date: 2006-11-19
forum: Argentina Team
---

### Post by delphinen on 2006-11-19
Buenas.

Soy un usuario de Ubuntu Dapper Drake, Development Branch. Es algo asi como la ultima version antes del release. La vengo usando desde hace meses y todo funciono barbaro. Y sigue funcionando barbaro. Tengo un Apache corriendo sin problemas, un Squid, Compiz-Quinn (la ultima version antes de que sea Beryl), Xgl, etc etc...

Esto me lleva a pensar, es necesario actualizar los paquetes con apt-get upgrade? ni hablar de apt-dist-upgrade, que ventajas me traeria migrar a Edgy Eft? cual es "la mentalidad" sobre actualizar paquetes todos los dias en una pc de escritorio?

PD: Felicitaciones por tener su propio foro!

---

### Post by ariel on 2006-11-19
Edgy está mucho mas pulido que dapper. Nuevo kernel, y sobre todo compatibilidad con Automatix2 que te instala todos los medias player nuevos que mejoraron muchisimo; incluse flash player 9 beta. Gnome mejoró mucho en pequeños detalles y estabilidad, por ejemplo nautilus no se cuelga más, al menos para mí. En general todas las aplicaciones basicas mejoraron, desde openoffice hasta gnomebaker (esta ultima versión está tan mejorada que me permitió finalmente semi-abandonar k3b)

Yo vivo en canada y me gusta mucho escuchar radios de baires, con dapper, hacer funcionar streams rtsp (mms o shoutcast) fue muy complicado y nunca fue estable (a la media hora los streams se cortaban, con vlc y gmplayer y xmms). Con edgy podes dejar la radio conectada durante dias sin problemas.

Instalar beryl es increíblemente fácil, tres comandos nada mas, y no hace falta editar ningún archivo de configuración, todo gracias al nuevo xorg.

No todo son rosas, yo tuve que pelearme un poco con el instalador, beryl 0.1.2 tiene algunos problemas con nvidia, vmware anda con quirks, y el kernel 2.6.17  ya se quedó en el tiempo. Pero Edgy es definitivamente mejor que Dapper en mil aspectos. Si lo que buscás es estabilidad, ya escuché muchas veces que la versión de ubuntu más estable es breezy.

Ah, me olvidaba: yo no te recomendaría un "upgrade" de tu distro, sino un "fresh install". En promedio creo que así te ahorras muchísimo tiempo y problemas.

---

### Post by QUASAR_FREAK on 2006-11-19
En tu lugar updatearia minimo a dapper estable, Edgy anda bastante bien pero hay mucha gente que tuvo problemas al updatear de dapper a edgy (yo lo hice de un dapper sucio a edgy knot2 sin dramas pero muchos tuvieron problemas), si podes instalalo en otro disco para probarlo o hacete una imagen con partimage de tu dapper cosa que si edgy explota puedas volver a dapper.

---

### Post by derjames on 2006-11-19
De acuerdo con Quasar, Dapper estable es una maravilla además que tiene soporte a largo plazo por lo que actualizar a Edgy realmente no es necesario...

---

### Post by Linuxerodel9 on 2006-11-19
Si tenes un dapper estable no updatees aun, ese es mi consejo. Edgy tiene mucho camino por recorrer aun, sobre todo con Beryl:mad: . hace dias que estoy tratando de configurarla y me esta costando.
salu2 ubunteros

---

### Post by delphinen on 2006-11-19
Bueno, por lo que me dijeron, mejor no actualizo nada. El dia que "sienta" que tengo Ubuntu muy atrasado, instalare Edgy de 0, si es que para entonces no salio una version mas nueva. Mientras tanto para bleeding edge tengo Arch.

---

### Post by beuno on 2006-11-19
Yo me aseguraria tener todos los paquetes de dapper en su ultima version (sudo aptitude update && sudo aptitude upgrade) y lo dejaria asi hasta que surja alguna necesidad especifica.

---

