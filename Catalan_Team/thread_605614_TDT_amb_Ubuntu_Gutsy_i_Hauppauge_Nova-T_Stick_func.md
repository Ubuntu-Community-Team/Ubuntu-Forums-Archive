---
title: "TDT amb Ubuntu Gutsy i Hauppauge Nova-T Stick funcionant, Problema IRC control remot"
date: 2007-11-07
forum: Catalan Team
---

### Post by jcampos on 2007-11-07
[SIZE=6][COLOR=DarkOrange]Índex[/COLOR][/SIZE][LIST=1]
[*]  **Ubuntu Gutsy i Hauppauge Nova-T Stick *funcionant***[LIST=1]
[*]per a qui li pugui servir[/LIST] 
[*]  ***Problema* IRC control remot**[LIST=1]
[*]per a qui hem pugui ajudar[/LIST] [/LIST][SIZE=6][COLOR=DarkOrange] 1.- Ubuntu Gutsy i Hauppauge Nova-T Stick funcionant[/COLOR][/SIZE]

[SIZE=4]Base[/SIZE]

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick)

wget [http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-dib0700-01.fw](http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-dib0700-01.fw)
 
```
sudo cp dvb-usb-dib0700-01.fw /lib/firmware/2.6.22-14-generic/

sudo /etc/init.d/mythtv-backend stop
sudo /etc/init.d/mythtv-backend start
``````
mythtv-setup
``` Capture cards:
   Card type: DVB DTV capture card (v3.x)
 Video sources
   New
   EIT
 Input sources
   Video source: (the defined previously)
   Scan for channels

```
mythfilldatabase

 sudo /etc/init.d/mythtv-backend stop
 sudo /etc/init.d/mythtv-backend start

 mythfrontend --service
```[SIZE=4]Problemes video[/SIZE]

Correct device file in /dev for ATI video card
[http://ubuntuforums.org/showthread.php?t=275831](http://ubuntuforums.org/showthread.php?t=275831)

```
cat /etc/modprobe.d/aliases | grep video
ls -lath /dev | grep 81,

mknod /dev/video0 c 81 0
chmod 0666 /dev/video0
ln -s /dev/video0 /dev/video
``````
mythfrontend
```Utilities-Themes-Paint Engine: OpenGL

Errors (al provar de veure TV):
```
2007-10-31 08:39:51.943 TV: Attempting to change from None to 2007-10-31 08:39:52.320 VideoOutputXv Error: Could not find suitable XVideo surface.
2007-10-31 08:39:52.329 VideoOutputXv: Falling back to X shared memory video output.
***
* Your system is not capable of displaying the
* full framerate at 1280x1024 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.
``````
sudo vi /etc/X11/xorg.conf
Section "Device"
        Identifier      "ATI Technologies Inc RV410 [Radeon X700]"
        Driver          "fglrx"
        Busid           "PCI:2:0:0"
        Option          "VideoOverlay" "on"     # jordi
        Option          "OpenGLOverlay" "off"   # jordi
EndSection
```** Unofficial ATI Linux Driver Wiki**
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)
[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
[http://www.mythtv.org/docs/mythtv-HOWTO.html](http://www.mythtv.org/docs/mythtv-HOWTO.html)
[http://www.hauppauge.co.uk/pages/products/data_novatstick.html](http://www.hauppauge.co.uk/pages/products/data_novatstick.html)
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)


[SIZE=4] Quality[/SIZE]

```
sudo vi /etc/security/limits.conf
@mythtv     -      rtprio       50
@mythtv     -      nice         0
``````
mythfrontend
```Utilities-Setup-General-TVSettings-Playback
+ Non-interlaced
+ Enable OpenGL vertical sync for timing
+ Enable realtime priority threads

=> now the quality is very good!


[SIZE=4]Channels (TV3, C33, 300...)[/SIZE]

[http://www.ubuntu-es.org/index.php?q=node/37628](http://www.ubuntu-es.org/index.php?q=node/37628)

```
aptitude install dvb-utils
sudo /etc/init.d/mythtv-backend stop
scan -5 -n /usr/share/doc/dvb-utils/examples/scan/dvb-t/es-Collserola > channels.conf
cp channels.conf ~/.xine
cp channels.conf ~/.mplayer
sudo /etc/init.d/mythtv-backend start

mythtv-setup
InputSource-Scan-ImportFromFile
/home/jcampos/.mplayer/channels.conf
```[SIZE=4]
Save config[/SIZE]

```
mysqldump --create-options -c -u mythtv -p mythconverg > mythtvBackup2007-11-07.sql
```[http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards](http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards)
[http://knoppmythwiki.org/index.php?page=DVBHowTo](http://knoppmythwiki.org/index.php?page=DVBHowTo)


[SIZE=6][COLOR=DarkOrange]2.- Problema IRC control remot [/COLOR][/SIZE]

** Problema**: no aconsegueixo veure la entrada de IRC per cap /dev.

Mirant els logs, veig que es detecta:

```
less /var/log/messages
lirc_dev: IR Remote Control driver registered, at major 61
```
Però després no es crea el /dev/inputX corresponent:

```
cat /proc/bus/input/devices
(mouse, keyboard, power buttons and Wacom)
```potser perquè tinc una Wacom tablet que se'm situa a /dev/input/event4?


** Algú ha pogut configurar el control remot amb Hauppauge Nova-T Stick?**

Gràcies

---

