---
title: "Gravar catradio en directe"
date: 2012-09-04
forum: Catalan Team
---

### Post by sianeu on 2012-09-04
No m'en surto. Crec que em falta la direcció bona. Amb altres radios, com radio 4 sí que funciona: 

> sianeu@unicorn:~$ streamripper [http://rtve.stream.flumotion.com/rtve/radio4.mp3.m3u](http://rtve.stream.flumotion.com/rtve/radio4.mp3.m3u)
Connecting...
stream: Streamripper_rips
server name: 

[skipping...   ]  -  [  2,40M]


Pero amb catalunya-radio no hi ha manera:

> sianeu@unicorn:~$ streamripper [http://www.catradio.cat/directes/catradio_wm.m3u](http://www.catradio.cat/directes/catradio_wm.m3u)
Connecting...
stream: Streamripper_rips
server name: Cougar/9.6.7600.16564


Aquesta es la direccio que apunten desde la seva pàgina, i que funciona be, per exempla, per escoltar-la amb Radio-tray. He provat moltes altres coses, i la que mes s'ha acostat a estat:

> sianeu@unicorn:~$ streamripper [http://www.catradio.cat/ria/players/audio/srp/srp.swf](http://www.catradio.cat/ria/players/audio/srp/srp.swf)
Connecting...
stream: Streamripper_rips
server name: Footprint Distributor V4.8

[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]
[skipping...   ]  -  [  209kb]

Això segueix indefinidament, com si arranques i pares continuament i nomes grava un silenci de menys d'un segon.

Tampoc he aconseguit reproduir-la en directe amb el VLC. Fa el mateix, rearranca continuament (amb la direcció bona, no aquesta última). Però ja he dit que amb el Radio-tray sí que funciona. Així que no estic segur de si falla la direcció o si fallen els programes amb catradio.

---

### Post by epileg on 2012-09-06
Per a desar l'streaming de Catalunya Ràdio pots utilitzar el mateix VLC.

En format Ogg/Vorbis:
```
$ cvlc mmsh://tv3catwmlive.fplive.net/tv3cat-live/stream_CatRadio_WM --sout="#transcode{vcodec=none,acodec=vorb,ab=128,channels=2,samplerate=44100}:std{access=file,mux=ogg,dst='/cami/on/desar/catradio.ogg'}"
```

En format MP3:
```
$ cvlc mmsh://tv3catwmlive.fplive.net/tv3cat-live/stream_CatRadio_WM --sout="#transcode{vcodec=none,acodec=mp3,ab=128,channels=2,samplerate=44100}:std{access=file,mux=raw,dst='/cami/on/desar/catradio.mp3'}"
```

Salut,

Edit:
He fet servir el VLC perquè sembla que l'streamripper no dona suport al protocol (propietari) Microsoft Media Server (mms://)

---

### Post by sianeu on 2012-09-14
En mp3 no em funciona, no se identificar el perqué:

> sianeu@unicorn:~$  cvlc mmsh://tv3catwmlive.fplive.net/tv3cat-live/stream_CatRadio_WM --sout="#transcode{vcodec=none,acodec=mp3,ab=128,channels=2,samplerate=44100}:std{access=file,mux=raw,dst='/home/sianeu/radio/catradio.mp3'}"
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x92c318] dummy interface: using the dummy interface module...
[0x7f67880044f8] mux_dummy mux: Open
[0x7f6788006398] access_mms access error: cannot read data 2
[0x7f6784001118] avcodec encoder error: cannot find encoder MPEG I/II Layer 3
*** Your FFMPEG installation is crippled.   ***
*** Please check with your FFMPEG packager. ***
*** This is NOT a VLC media player issue.   ***
[0x7f6784001118] main encoder error: Ha fallat la transmissió/transcodificació
[0x7f6784001118] main encoder error: It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG I/II Layer 3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.

[0x7f6788002448] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mp3 ). Take a look few lines earlier to see possible reason.
[0x7f6788002448] stream_out_transcode stream out error: cannot create audio chain
[0x7f678801d798] main decoder error: cannot create packetizer output (WMA2)


En ogg també dona algun error, però funciona (grava):

> sianeu@unicorn:~$  cvlc mmsh://tv3catwmlive.fplive.net/tv3cat-live/stream_CatRadio_WM --sout="#transcode{vcodec=none,acodec=vorb,ab=128,channels=2,samplerate=44100}:std{access=file,mux=ogg,dst='/home/sianeu/radio/catradio.ogg'}"
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x1b42318] dummy interface: using the dummy interface module...
[0x7f60f80044f8] mux_ogg mux: Open
[0x7f60f80037c8] access_mms access error: cannot read data 2



Moltes gracies per l'ajut.

---

### Post by epileg on 2012-09-20
Per a poder desar en format mp3, cal tenir insta&#320;lat el paquet «ffmpeg»
```
$ sudo apt-get install ffmpeg
```

El camí del fitxer a desar pot ser relatiu, o sigui que si només poses «catradio.ogg», el desarà al directori actual.

Jo també rebo alguns errors, però tot i això, ambdós formats es desen correctament.

Salut!

---

