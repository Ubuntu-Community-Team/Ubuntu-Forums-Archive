---
title: "Problema con Teclado"
date: 2014-08-09
forum: Argentina Team
---

### Post by hernan6 on 2014-08-09
tengo un teclado SEISA mod.DN-V390 y el problema en si es que me reconoce las tecas ALT, ALTGR, super (win) y CTRL como si fuera el SHIFT derecho, el xev tira el mismo keycode. No se que mas hacer, ya vi la configuracion regional, la distribucion está perfecta y la accesibilidad esta toda desactivada... Gracias

---

### Post by lucasgz on 2014-10-25
Hola, tengo exactamente el mismo teclado usb y me pasa lo mismo. Me lo detecta como SONiX USB Keyboard. Lo prove en windows y funciona perfecto.
Tambien note que no se encienden las luces de Block Mayus y Bloq Num, cosa que funciona en windows. Pero si funcionan como comando, SE ACTIVA EL BLOCK.

Pongo la salida de evtest asi se ve mejor.

```

Testing ... (interrupt to exit)
***Esta es la "a"
Event: time 1414255168.847782, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70004
Event: time 1414255168.847782, type 1 (EV_KEY), code 30 (KEY_A), value 1
Event: time 1414255168.847782, -------------- SYN_REPORT ------------
aEvent: time 1414255168.911776, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70004
Event: time 1414255168.911776, type 1 (EV_KEY), code 30 (KEY_A), value 0
Event: time 1414255168.911776, -------------- SYN_REPORT ------------
***La "s"
Event: time 1414255169.543779, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70016
Event: time 1414255169.543779, type 1 (EV_KEY), code 31 (KEY_S), value 1
Event: time 1414255169.543779, -------------- SYN_REPORT ------------
sEvent: time 1414255169.607778, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70016
Event: time 1414255169.607778, type 1 (EV_KEY), code 31 (KEY_S), value 0
Event: time 1414255169.607778, -------------- SYN_REPORT ------------
***La "d"
Event: time 1414255170.167777, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70007
Event: time 1414255170.167777, type 1 (EV_KEY), code 32 (KEY_D), value 1
Event: time 1414255170.167777, -------------- SYN_REPORT ------------
dEvent: time 1414255170.247776, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70007
Event: time 1414255170.247776, type 1 (EV_KEY), code 32 (KEY_D), value 0
Event: time 1414255170.247776, -------------- SYN_REPORT ------------

***SHIFT izquierdo
Event: time 1414255176.375785, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255176.375785, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 1
Event: time 1414255176.375785, -------------- SYN_REPORT ------------
Event: time 1414255176.439780, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255176.439780, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 0
Event: time 1414255176.439780, -------------- SYN_REPORT ------------

**** CTRL izquierdo, Como se ve salen con igual codigo
Event: time 1414255177.007780, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255177.007780, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 1
Event: time 1414255177.007780, -------------- SYN_REPORT ------------
Event: time 1414255177.087781, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255177.087781, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 0
Event: time 1414255177.087781, -------------- SYN_REPORT ------------
*** tecla WIN izq
Event: time 1414255178.759785, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255178.759785, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 1
Event: time 1414255178.759785, -------------- SYN_REPORT ------------
Event: time 1414255178.847783, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255178.847783, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 0
Event: time 1414255178.847783, -------------- SYN_REPORT ------------
***ALT izq
Event: time 1414255179.087782, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255179.087782, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 1
Event: time 1414255179.087782, -------------- SYN_REPORT ------------
Event: time 1414255179.167770, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255179.167770, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 0
Event: time 1414255179.167770, -------------- SYN_REPORT ------------
***ALT Gr
Event: time 1414255182.303813, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255182.303813, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 1
Event: time 1414255182.303813, -------------- SYN_REPORT ------------
Event: time 1414255182.367783, type 4 (EV_MSC), code 4 (MSC_SCAN), value 700e1
Event: time 1414255182.367783, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 0
Event: time 1414255182.367783, -------------- SYN_REPORT ------------

***tira un valor al apretar y al soltar

```

Este es como empieza el comando
```

desktop:~$ sudo evtest

No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:    Power Button
/dev/input/event1:    Power Button
/dev/input/event2:    ImPS/2 Generic Wheel Mouse
/dev/input/event3:    HDA ATI SB Front Headphone
/dev/input/event4:    HDA ATI SB Line Out
/dev/input/event5:    HDA ATI SB Line
/dev/input/event6:    HDA ATI SB Rear Mic
/dev/input/event7:    HDA ATI SB Front Mic
/dev/input/event8:    Eee PC WMI hotkeys
/dev/input/event9:    HDA ATI HDMI HDMI/DP,pcm=11
/dev/input/event10:    HDA ATI HDMI HDMI/DP,pcm=10
/dev/input/event11:    HDA ATI HDMI HDMI/DP,pcm=9
/dev/input/event12:    HDA ATI HDMI HDMI/DP,pcm=8
/dev/input/event13:    HDA ATI HDMI HDMI/DP,pcm=7
/dev/input/event14:    HDA ATI HDMI HDMI/DP,pcm=3
/dev/input/event15:    DragonRise Inc.   Generic   USB  Joystick  
/dev/input/event16:    SONiX USB Keyboard
/dev/input/event17:    SONiX USB Keyboard
Select the device event number [0-17]: 17
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0xc45 product 0x7603 version 0x111
Input device name: "SONiX USB Keyboard"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 1 (KEY_ESC)
    Event code 2 (KEY_1)
    Event code 3 (KEY_2)
    Event code 4 (KEY_3)
    Event code 5 (KEY_4)
    Event code 6 (KEY_5)
    Event code 7 (KEY_6)
    Event code 8 (KEY_7)
    Event code 9 (KEY_8)
    Event code 10 (KEY_9)
    Event code 11 (KEY_0)
    Event code 12 (KEY_MINUS)
    Event code 13 (KEY_EQUAL)
    Event code 14 (KEY_BACKSPACE)
    Event code 15 (KEY_TAB)
    Event code 16 (KEY_Q)
    Event code 17 (KEY_W)
    Event code 18 (KEY_E)
    Event code 19 (KEY_R)
    Event code 20 (KEY_T)
    Event code 21 (KEY_Y)
    Event code 22 (KEY_U)
    Event code 23 (KEY_I)
    Event code 24 (KEY_O)
    Event code 25 (KEY_P)
    Event code 26 (KEY_LEFTBRACE)
    Event code 27 (KEY_RIGHTBRACE)
    Event code 28 (KEY_ENTER)
    Event code 29 (KEY_LEFTCTRL)
    Event code 30 (KEY_A)
    Event code 31 (KEY_S)
    Event code 32 (KEY_D)
    Event code 33 (KEY_F)
    Event code 34 (KEY_G)
    Event code 35 (KEY_H)
    Event code 36 (KEY_J)
    Event code 37 (KEY_K)
    Event code 38 (KEY_L)
    Event code 39 (KEY_SEMICOLON)
    Event code 40 (KEY_APOSTROPHE)
    Event code 41 (KEY_GRAVE)
    Event code 42 (KEY_LEFTSHIFT)
    Event code 43 (KEY_BACKSLASH)
    Event code 44 (KEY_Z)
    Event code 45 (KEY_X)
    Event code 46 (KEY_C)
    Event code 47 (KEY_V)
    Event code 48 (KEY_B)
    Event code 49 (KEY_N)
    Event code 50 (KEY_M)
    Event code 51 (KEY_COMMA)
    Event code 52 (KEY_DOT)
    Event code 53 (KEY_SLASH)
    Event code 54 (KEY_RIGHTSHIFT)
    Event code 55 (KEY_KPASTERISK)
    Event code 56 (KEY_LEFTALT)
    Event code 57 (KEY_SPACE)
    Event code 58 (KEY_CAPSLOCK)
    Event code 59 (KEY_F1)
    Event code 60 (KEY_F2)
    Event code 61 (KEY_F3)
    Event code 62 (KEY_F4)
    Event code 63 (KEY_F5)
    Event code 64 (KEY_F6)
    Event code 65 (KEY_F7)
    Event code 66 (KEY_F8)
    Event code 67 (KEY_F9)
    Event code 68 (KEY_F10)
    Event code 69 (KEY_NUMLOCK)
    Event code 70 (KEY_SCROLLLOCK)
    Event code 71 (KEY_KP7)
    Event code 72 (KEY_KP8)
    Event code 73 (KEY_KP9)
    Event code 74 (KEY_KPMINUS)
    Event code 75 (KEY_KP4)
    Event code 76 (KEY_KP5)
    Event code 77 (KEY_KP6)
    Event code 78 (KEY_KPPLUS)
    Event code 79 (KEY_KP1)
    Event code 80 (KEY_KP2)
    Event code 81 (KEY_KP3)
    Event code 82 (KEY_KP0)
    Event code 83 (KEY_KPDOT)
    Event code 85 (KEY_ZENKAKUHANKAKU)
    Event code 86 (KEY_102ND)
    Event code 87 (KEY_F11)
    Event code 88 (KEY_F12)
    Event code 89 (KEY_RO)
    Event code 90 (KEY_KATAKANA)
    Event code 91 (KEY_HIRAGANA)
    Event code 92 (KEY_HENKAN)
    Event code 93 (KEY_KATAKANAHIRAGANA)
    Event code 94 (KEY_MUHENKAN)
    Event code 95 (KEY_KPJPCOMMA)
    Event code 96 (KEY_KPENTER)
    Event code 97 (KEY_RIGHTCTRL)
    Event code 98 (KEY_KPSLASH)
    Event code 99 (KEY_SYSRQ)
    Event code 100 (KEY_RIGHTALT)
    Event code 102 (KEY_HOME)
    Event code 103 (KEY_UP)
    Event code 104 (KEY_PAGEUP)
    Event code 105 (KEY_LEFT)
    Event code 106 (KEY_RIGHT)
    Event code 107 (KEY_END)
    Event code 108 (KEY_DOWN)
    Event code 109 (KEY_PAGEDOWN)
    Event code 110 (KEY_INSERT)
    Event code 111 (KEY_DELETE)
    Event code 113 (KEY_MUTE)
    Event code 114 (KEY_VOLUMEDOWN)
    Event code 115 (KEY_VOLUMEUP)
    Event code 116 (KEY_POWER)
    Event code 117 (KEY_KPEQUAL)
    Event code 119 (KEY_PAUSE)
    Event code 121 (KEY_KPCOMMA)
    Event code 122 (KEY_HANGUEL)
    Event code 123 (KEY_HANJA)
    Event code 124 (KEY_YEN)
    Event code 125 (KEY_LEFTMETA)
    Event code 126 (KEY_RIGHTMETA)
    Event code 127 (KEY_COMPOSE)
    Event code 128 (KEY_STOP)
    Event code 129 (KEY_AGAIN)
    Event code 130 (KEY_PROPS)
    Event code 131 (KEY_UNDO)
    Event code 132 (KEY_FRONT)
    Event code 133 (KEY_COPY)
    Event code 134 (KEY_OPEN)
    Event code 135 (KEY_PASTE)
    Event code 136 (KEY_FIND)
    Event code 137 (KEY_CUT)
    Event code 138 (KEY_HELP)
    Event code 139 (KEY_MENU)
    Event code 140 (KEY_CALC)
    Event code 142 (KEY_SLEEP)
    Event code 143 (KEY_WAKEUP)
    Event code 144 (KEY_FILE)
    Event code 150 (KEY_WWW)
    Event code 152 (KEY_SCREENLOCK)
    Event code 155 (KEY_MAIL)
    Event code 156 (KEY_BOOKMARKS)
    Event code 158 (KEY_BACK)
    Event code 159 (KEY_FORWARD)
    Event code 161 (KEY_EJECTCD)
    Event code 163 (KEY_NEXTSONG)
    Event code 164 (KEY_PLAYPAUSE)
    Event code 165 (KEY_PREVIOUSSONG)
    Event code 166 (KEY_STOPCD)
    Event code 167 (KEY_RECORD)
    Event code 168 (KEY_REWIND)
    Event code 169 (KEY_PHONE)
    Event code 171 (KEY_CONFIG)
    Event code 172 (KEY_HOMEPAGE)
    Event code 173 (KEY_REFRESH)
    Event code 174 (KEY_EXIT)
    Event code 176 (KEY_EDIT)
    Event code 177 (KEY_SCROLLUP)
    Event code 178 (KEY_SCROLLDOWN)
    Event code 181 (KEY_NEW)
    Event code 182 (KEY_REDO)
    Event code 183 (KEY_F13)
    Event code 184 (KEY_F14)
    Event code 185 (KEY_F15)
    Event code 186 (KEY_F16)
    Event code 187 (KEY_F17)
    Event code 188 (KEY_F18)
    Event code 189 (KEY_F19)
    Event code 190 (KEY_F20)
    Event code 191 (KEY_F21)
    Event code 192 (KEY_F22)
    Event code 193 (KEY_F23)
    Event code 194 (KEY_F24)
    Event code 206 (KEY_CLOSE)
    Event code 207 (KEY_PLAY)
    Event code 208 (KEY_FASTFORWARD)
    Event code 209 (KEY_BASSBOOST)
    Event code 210 (KEY_PRINT)
    Event code 212 (KEY_CAMERA)
    Event code 216 (KEY_CHAT)
    Event code 217 (KEY_SEARCH)
    Event code 219 (KEY_FINANCE)
    Event code 223 (KEY_CANCEL)
    Event code 228 (KEY_KBDILLUMTOGGLE)
    Event code 231 (KEY_SEND)
    Event code 232 (KEY_REPLY)
    Event code 233 (KEY_FORWARDMAIL)
    Event code 234 (KEY_SAVE)
    Event code 235 (KEY_DOCUMENTS)
    Event code 240 (KEY_UNKNOWN)
    Event code 241 (KEY_VIDEO_NEXT)
    Event code 256 (BTN_0)
    Event code 353 (KEY_SELECT)
    Event code 354 (KEY_GOTO)
    Event code 358 (KEY_INFO)
    Event code 362 (KEY_PROGRAM)
    Event code 366 (KEY_PVR)
    Event code 370 (KEY_SUBTITLE)
    Event code 372 (KEY_ZOOM)
    Event code 374 (KEY_KEYBOARD)
    Event code 376 (KEY_PC)
    Event code 377 (KEY_TV)
    Event code 378 (KEY_TV2)
    Event code 379 (KEY_VCR)
    Event code 380 (KEY_VCR2)
    Event code 381 (KEY_SAT)
    Event code 383 (KEY_CD)
    Event code 384 (KEY_TAPE)
    Event code 386 (KEY_TUNER)
    Event code 387 (KEY_PLAYER)
    Event code 389 (KEY_DVD)
    Event code 392 (KEY_AUDIO)
    Event code 393 (KEY_VIDEO)
    Event code 396 (KEY_MEMO)
    Event code 397 (KEY_CALENDAR)
    Event code 398 (KEY_RED)
    Event code 399 (KEY_GREEN)
    Event code 400 (KEY_YELLOW)
    Event code 401 (KEY_BLUE)
    Event code 402 (KEY_CHANNELUP)
    Event code 403 (KEY_CHANNELDOWN)
    Event code 405 (KEY_LAST)
    Event code 408 (KEY_RESTART)
    Event code 409 (KEY_SLOW)
    Event code 410 (KEY_SHUFFLE)
    Event code 416 (KEY_VIDEOPHONE)
    Event code 417 (KEY_GAMES)
    Event code 418 (KEY_ZOOMIN)
    Event code 419 (KEY_ZOOMOUT)
    Event code 420 (KEY_ZOOMRESET)
    Event code 421 (KEY_WORDPROCESSOR)
    Event code 422 (KEY_EDITOR)
    Event code 423 (KEY_SPREADSHEET)
    Event code 424 (KEY_GRAPHICSEDITOR)
    Event code 425 (KEY_PRESENTATION)
    Event code 426 (KEY_DATABASE)
    Event code 427 (KEY_NEWS)
    Event code 428 (KEY_VOICEMAIL)
    Event code 429 (KEY_ADDRESSBOOK)
    Event code 430 (KEY_MESSENGER)
    Event code 432 (KEY_SPELLCHECK)
    Event code 433 (KEY_LOGOFF)
    Event code 439 (KEY_MEDIA_REPEAT)
    Event code 442 (?)
  Event type 2 (EV_REL)
    Event code 6 (REL_HWHEEL)
  Event type 3 (EV_ABS)
    Event code 32 (ABS_VOLUME)
      Value      0
      Min        0
      Max      896
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
Properties:
  Property type 20 (EV_REP)
    Property code 0 (REP_DELAY)
      Value    250
    Property code 1 (REP_PERIOD)
      Value     33
Testing ... (interrupt to exit)
Event: time 1414255155.439775, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70058
Event: time 1414255155.439775, type 1 (EV_KEY), code 96 (KEY_KPENTER), value 0


```

Estoy usando Ubuntu 14.04, la placa es
 -BIOS-
Date        : 12/12/2013
Vendor        : American Megatrends Inc. ([www.ami.com]("http://www.ami.com"))
Version        : 2202
-Board-
Name        : M5A97 LE R2.0
Vendor        : ASUSTeK COMPUTER INC. (SEAGATE, [www.seagate.com]("http://www.seagate.com"))

Nose si cuestion de esperar a que agreguen los drivers del modelo al ubuntu y si tendria o no que reportarlo como falla, alguien me puede pasar el link si es que hay que reportarlo como falla? gracias.

---

### Post by andresj551 on 2015-09-29
Hola, tengo exactamente el mismo problema... Llevo meses buscando la solución.
Al parecer el problema es que no existe un driver para esta marca de teclado. No sé como programar un driver o si quiera cambiarlo en el SO.

Ya estoy resignado a usar el teclado en pantalla, ojalá alguien encuentre la solución.

Saludos.

---

### Post by lositor on 2015-10-30
A mí me pasa exactamente lo mismo con las teclas Ctrl Alt y AltGr, pero con el Shift izquierdo.
Uso Ubuntu 14.04 y un teclado Coolbox Quasar Selene.
¿Alguien consiguió solucionarlo?
Gracias.

---

### Post by gabriel60 on 2015-11-15
Hola a Todos Yo tengo un teclado retro iluminado SEISA DN-V390 y buscando por internet logre dar solución a los problemas del uso de las teclas control, shift, alt y altgr. Lo que hay que hacer es copiar todo este codigo y pegarlo en la terminal, luego le dan Enter y se auto configurara. Puede que les pase que el teclado quede como inactivo, la solución es desconectarlo y volverlo a conectar y ya esta.

sudo apt-get install mercurial build-essential linux-headers-generic dkms
hg clone [https://bitbucket.org/Swoogan/aziokbd](https://bitbucket.org/Swoogan/aziokbd)
cd aziokbd
sudo ./install.sh dkms

Aclaro que sirve para todos los teclados multimedia y/o Gamer
Saludos y espero que les sirva....

---

### Post by lositor on 2015-12-26
¡Muchísimas gracias, gabriel60!
También me ha funcionado a mí en Ubuntu 14.04 con un teclado Selene Quasar de Coolbox.

---

