---
title: "Millora de script"
date: 2010-08-21
forum: Catalan Team
---

### Post by tanreb20 on 2010-08-21
HOla companys!

He fet un script per, usant el gphoto2, fer time-lapses!

Pero hi ha un parell de coses que no se fer i m'agradaria a veure si algú em pot ajudar.

Per una banda, optimitzar-lo ja que segur que no es gaire eficient(que si eficaç).

I per l'altre... en cas que algu introdueixi un valor erroni, repetir l'accio fins a introduir un valor correcte (en els entry-text)


```
#!/bin/bash

function fotografies()
{
fotos=$(/usr/bin/zenity --entry --title="Time-Lapse"  --text="Quantitat de fotografies" --entry-text="100")
strfot=`echo $?`
if [ $strfot == 0 ]
	then
	temps=$(/usr/bin/zenity --entry --title="Time-Lapse"  --text="Temps entre fotografies" --entry-text="10")
	strtmp=`echo $?`
else
	exit
fi
}

function pelicula()
{
fps=$(/usr/bin/zenity --entry --title="Time-Lapse" --text="Quantes fotografies vols per segon?" --entry-text="12")
				strftp=`echo $?`
				mida=$(/usr/bin/zenity --entry --title="Time-Lapse" --text="Quin tamany de video vols? Ample:Alt" --entry-text="640:480")
				strmid=`echo $?`
				/usr/bin/mencoder "mf://*.jpg" -mf fps=$fps:type=jpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:vbitrate=7000 -vf scale=$mida -oac copy -o /home/alorma/gphoto2/video.avi
}

zenity --info --title="Time-Lapse" --text="Anem a fer un Time-Lapse"
zenity --info --title="Time-Lapse" --text="Ara passem a detectar la camera"
/usr/bin/gphoto2 --auto-detect
detect=$(/usr/bin/zenity --question --title="Time-Lapse" --text="L'ha detectat correctament?")
strdet=`echo $?`

if [ $strdet == 0 ]
	then
	fotografies
	
		disparar=$(/usr/bin/zenity --question --title="Time-Lapse"  --text="Has decidit fer: $fotos fotos a $temps segons entre foto i foto. \n\n Correcte?")
		strdis=`echo $?`
		if [ $strdis == 0 ]
			then
			/usr/bin/gphoto2 --set-config beep=0 --set-config flashmode=0 --set-config resolution=3 -I $temps -F $fotos --capture-image-and-download --filename "%Y%m%d-%H%M%S.jpg"
			
			video=$(zenity --question --title="Time-Lapse" --text="Vols fer el video ara?")
			strvid=`echo $?`
			if [ $strvid == 0 ]
				then
				pelicula
			else
				exit
			fi
		else
			exit
		fi
else
	exit
fi

```

---

### Post by RainCT on 2010-08-22
Aquí tens un exemple de com demanar el nombre de fotografies fins que sigui un número més gran de zero. Confio en que sabràs adaptar el codi als altres casos ;).

```

fotos=0
while [ ! -z "${fotos##[0-9]*}" ] || [ "$fotos" -lt 1 ]; do
	fotos=$(/usr/bin/zenity --entry --title="Time-Lapse" --text="Quantitat de fotografies" --entry-text="100")
	if [ $? -ne 0 ]; then
		exit
	fi
done

echo $fotos

```

Per cert, m'has donat la idea que podria ser interessant un sistema per poder dissenyar interfícies gràfiques amb el Glade i connectar-hi accions escrites en Bash. Seria una cosa que t'interesses utilitzar?

---

### Post by tanreb20 on 2010-08-22
UHm.. que és el Glade? XD

Em smebla que si que m'interessa!

---

### Post by RainCT on 2010-08-22
[http://glade.gnome.org/](http://glade.gnome.org/)

És una interfície gràfica per a crear interfícies gràfiques ;).


**Edito:** Sembla que ja existeix un programa per fer-ho: [http://linux.pte.hu/~pipas/gtkdialog/](http://linux.pte.hu/~pipas/gtkdialog/).

---

