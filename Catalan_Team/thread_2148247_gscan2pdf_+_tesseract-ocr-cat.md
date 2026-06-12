---
title: "gscan2pdf + tesseract-ocr-cat"
date: 2013-05-24
forum: Catalan Team
---

### Post by AlbertJB on 2013-05-24
Hola bona tarda:

Amb **Ubuntu 12.04**, Gnome classic no effects, llengua predeterminada el **català**, tinc instal·lats el **gscan2pdf 0.9.32** i el **tesseract-ocr-cat 3.02-2**. Però en la GUI del tesseract (que és el mateix gscan2pdf), a l'hora de triar la llengua d'escaneig_ OCR només em deixa triar l'Anglès_, no el català, _tot i tenir el paquet OCR català instal·lat_. L'escànner és [B]Epson Perfection V10/V100.
[/B]
Sé que és una pregunta molt específica, he estat cercant a Google la combinació de gscan2pdf i català i no he trobat cap pista sobre el problema. He revisat l'historial de canvis del gscan2pdf i a la versió gscan2pdf 0.9.30 indica: "Start of Catalan translation" (es deu referir a la traducció de la interfície gràfica, res a veure amb tesseract). 

Qualsevol pista serà molt benvinguda. Salutacions.

******

Perdoneu, finalment he trobat la solució gràcies a un [blogger]("http://www.kubuntu-es.org/foro/201208/gscan2pdf-dejo-funcionar-tesseract-castellano-1204"). Resulta que ha de ser la versió més actual del gscan2pdf, i hi ha un ppa. Per això, per als qui els interessi, han de fer això:

[B]sudo add-apt-repository ppa:jeffreyratcliffe
[/B][B]sudo apt-get update
sudo aptitude install gscan2pdf[/B]

(tenint instal·lada la versió per defecte de tesseract-ocr ja va bé, ja em deixa escollir l'idioma, el català, per exemple).

---

### Post by AlbertJB on 2013-05-24
Actualització: malauradament el resultat OCR no és l'esperat (cada paraula encasellada en una caixa) :(  Ho comenta un anònim a [SourceForge]("https://sourceforge.net/p/gscan2pdf/feature-requests/73/").

---

