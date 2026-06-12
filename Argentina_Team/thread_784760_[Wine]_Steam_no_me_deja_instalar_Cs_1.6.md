---
title: "[Wine] Steam no me deja instalar Cs 1.6"
date: 2008-05-06
forum: Argentina Team
---

### Post by smrdelj on 2008-05-06
Hola que tal. Cuando me conecto a mi cuenta Steam y le doy la orden de que instale el Cs 1.6 (licencia oficial, nada de cracks), simplemente se cierra el programa. Steam desaparece cuando ejecuto la orden de instalar.

Acá les dejo lo que arroja la consola, porq seguro que la clave está escondida ahi: ```

CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: CSDS returned 160 servers.
CellID: Connecting to 208.111.182.250:27031. . .
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.mix
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.asi
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
CellID: Connect to 208.111.182.250:27031 took 266 MS
CellID: Nothing beat our old best time of 176 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1abab8)->(1 00000002 0x12a3fb8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1abab8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1abab8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1abab8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1ac0b0)->(1 00000002 0x12a4020)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ac0b0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ac0b0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ac0b0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x213c20)->(1 00000002 0x12a4890)
fixme:shdocvw:PersistStreamInit_InitNew (0x213c20)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x213c20)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x213c20)->(ffffffff)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7b684a08, overlapped 0x7b6849ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x110def34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x213cbc)->((null) 1 0x3385dc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 25 2 0x3385f0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 26 2 0x3385f0 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x213cbc)->(0x33862c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x3386f0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x215408)->(L"" L"" 0 0x338728)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 29 2 0x33d558 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x213cbc)
fixme:shdocvw:ClientSite_GetContainer (0x213cbc)->(0x33d508)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x213cbc)->(0xf7e4a755)
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 25 2 0x33d43c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 26 2 0x33d43c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x111ee0e8)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x2167d0)
fixme:mshtml:HTMLBodyElement_put_scroll (0x111ee0e8)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x111ee0e8)->(L"no")
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10038,0x00000000,0,2): stub!
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1abb54)->((null) 1 0x33a874 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 25 2 0x33a888 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 26 2 0x33a888 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x1abb54)->(0x33a8c4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33a988 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x111e8108)->(L"" L"" 0 0x33a9c0)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 29 2 0x33d558 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1abb54)
fixme:shdocvw:ClientSite_GetContainer (0x1abb54)->(0x33d508)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1abb54)->(0xf7e4a755)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 25 2 0x33d43c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 26 2 0x33d43c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x1a0a68)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x111e3a10)
fixme:mshtml:HTMLBodyElement_put_scroll (0x1a0a68)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x1a0a68)->(L"no")
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:mshtml:HTMLBodyElement_put_scroll (0x114bba20)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 28 2 0x33d420 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 28 2 0x33d420 (nil))
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,169,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,169,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,96,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,69,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,25,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x213c20)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x213c20)
fixme:shdocvw:OleObject_Close (0x213c20)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x2167d0)->((nil))
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Fallo de segmentación

```

Muchas gracias, espero alguna ayuda!

Saludos

---

### Post by MeduZa on 2008-05-06
parece error en "el registro de windows":class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered

lo que yo haria seria probar de instalar el steam desde wine-doors y ver si hace lo msimo.
y si te sigue jodiendo con eso probar el cedega

---

### Post by smrdelj on 2008-05-06
El Wine-doors me trajo zarpados dolores de cabeza. Realmente no me tienta la opcion.

En cuanto al cedega, cuál sería exactamente el que debería bajar? Porq lo busqué y me pareció que todas las versiones son i386, y yo tengo Ubuntu 8.04 AMD 64. Habrá algo disponible? (ya se q es pago, yo lo soluciono...)

Saludos

---

### Post by anarko on 2008-05-06
existe algo llamado cedega small, hay version x86_64. lo unico que tenes que pagar es el engine, el resto es free

---

### Post by MeduZa on 2008-05-07
> **smrdelj said:**
> El Wine-doors me trajo zarpados dolores de cabeza. Realmente no me tienta la opcion.

En cuanto al cedega, cuál sería exactamente el que debería bajar? Porq lo busqué y me pareció que todas las versiones son i386, y yo tengo Ubuntu 8.04 AMD 64. Habrá algo disponible? (ya se q es pago, yo lo soluciono...)

Saludos

si tenes el de 64bits quisas los dolores de cabeza sean por ese lado, y no no es pago, te podes inscribir pero no es necesario.

---

### Post by smrdelj on 2008-05-07
Si instalo los Cedega i386 me va a dar error todo?

Por otro lado, creen q fue un error haber instalado Ubuntu AMD 64 en vez de i386? (mi maquina es una Athlon 64)

Saludos

---

