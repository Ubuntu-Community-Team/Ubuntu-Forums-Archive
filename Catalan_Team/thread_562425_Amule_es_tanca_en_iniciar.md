---
title: "Amule es tanca en iniciar"
date: 2007-09-28
forum: Catalan Team
---

### Post by Dilov on 2007-09-28
Hola!

Fa poc que tinc l'Ubuntu 7.04 instal·lat i la veritat es que acostumat a les facilitats de windows, linux és un sistema operatiu molt didàctic. :)

El cas és que vaig activar els efectes d'escriptori per provar-los i els vaig desactivar després.
Llavors vaig iniciar l'Amule que em dona un missatge d'error perquè he borrat el fitxer d'aparença -skin- que utilitzava i que per tant utilitzarà el que té per defecte. Llavors s'obre el programa però un segon després es tanca sense més i no sé com solucionar-ho.
L'he eliminat completament i reinstal·lat, continua exactament igual.

He estat buscant pels fòrums però no he trobat cap cas similar...

*Alguna idea?*

Moltes gràcies!

---

### Post by papapep on 2007-09-29
Prova a executar-lo en un terminal a veure si et dóna algun missatge que ens doni pistes i, si és així, enganxa'l aquí.

---

### Post by CarlesOriol on 2007-09-29
1. Explica'ns com has esborrat l'arxiu de pell.

2. Elimina la carpeta oculta /home/dilov/.aMule (en lloc de dilov posa el nom del teu usuari si és una altra)

---

### Post by Dilov on 2007-09-29
Solucionat. Moltes gràcies!

Després de borrar la carpeta /home/dilov/.aMule (que suposo que és la configuració) l'amule s'inicia dient que és el 1r cop que l'inicio i funciona bé.
Respecte a l'skin, el tenia a l'escriptori i el vaig enviar a la paperera perquè no funcionava (l'aparença de l'amule no canviava).

I executant-lo en terminal em donava (jo no entenc res, però potser els experts hi veieu alguna cosa interessant :))
[SIZE="1"]
dilov@linux:~$ amule
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
HTTP download thread started
Testing skins
Host: amule.sourceforge.net:80
URL: [http://amule.sourceforge.net/lastversion](http://amule.sourceforge.net/lastversion)
Response: 200 (Error: 0)
Download size: 6
HTTP download thread ended
Loading temp files from /home/dilov/.aMule/Temp.
Loading PartFile 4 of 4
All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:****
*** TCP socket (TCP) listening on 0.0.0.0:****
*** Client UDP socket (extended eMule) at 0.0.0.0:****
Empty dir /home/dilov/.aMule/Incoming/ shared

Terminated after throwing an instance of 'std::bad_alloc'
        what(): St9bad_alloc
        backtrace:
[2] ?? in /usr/lib/libstdc++.so.6 [0xb74acca5]
[3] ?? in /usr/lib/libstdc++.so.6 [0xb74acce2]
[4] ?? in /usr/lib/libstdc++.so.6 [0xb74ace1a]
[5] operator new(unsigned int) in /usr/lib/libstdc++.so.6[0xb74ad25e]
[6] operator new[](unsigned int) in /usr/lib/libstdc++.so.6[0xb74ad33d]
[7] wxBookCtrlBase::RemovePage(unsigned int) in amule [0x8147360]
[8] wxBookCtrlBase::RemovePage(unsigned int) in amule [0x81475c1]
[9] wxBookCtrlBase::RemovePage(unsigned int) in amule [0x8148119]
[10] wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const in /usr/lib/libwx_baseu-2.8.so.0[0xb752cd65]
[11] wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0xb75d4cbf]
[12] wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) in /usr/lib/libwx_baseu-2.8.so.0[0xb75d4e0d]
[13] wxEvtHandler::ProcessEvent(wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0xb75d4f76]
[14] wxTimerBase::Notify() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb78dbfe1]
[15] ?? in /usr/lib/libwx_gtk2u_core-2.8.so.0 [0xb77b7555]
[16] ?? in /usr/lib/libglib-2.0.so.0 [0xb6f8b3c6]
[17] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0xb6f8adf2]
[18] ?? in /usr/lib/libglib-2.0.so.0 [0xb6f8ddcf]
[19] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0xb6f8e179]
[20] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0xb6d3b044]
[21] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb77add0c]
[22] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb784fcee]
[23] wxAppBase::OnRun() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb784f2e1]
[24] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.8.so.0[0xb756927a]
[25] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.8.so.0[0xb7569327]
[26] CryptoPP::IteratedHash<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, 64u, CryptoPP::HashTransformation>::~IteratedHash() in amule [0x812f490]
[27] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb7298ebc]
[28] wxNotebook::SetPadding(wxSize const&) in amule[0x8080fd1]

Aborted (core dumped)
dilov@linux:~$ 
[/SIZE]

---

### Post by pespin on 2007-09-29
Jo diria que l'error vedonat per un accés incorrecte/i&#320;legítim a un apartat de la RAM

---

