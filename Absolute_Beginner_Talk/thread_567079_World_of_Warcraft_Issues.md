---
title: "World of Warcraft Issues"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-04
I have updated to version 2.2.0 and when i start the launcher i get this error, i am using wine:

fixme:shdocvw:WebBrowser_QueryInterface (0x190200)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x33e474) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x190200)->(0x33e440)
fixme:shdocvw:OleControl_FreezeEvents (0x190200)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x190200)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x1914b8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x191910): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x191910): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x191910): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x191910): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x191910): WIN32_FIND_DATA is not yet filled.
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x190294)->((null) 1 0x33dcfc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x190294)->((null) 25 2 0x33dd10 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x190294)->((null) 26 2 0x33dd10 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x190294)->(0x33dd4c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x190294)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33de70 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1a8938)->(L"" L"" 0 0x33de84)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x1a8938)->(0x33de88 0x33ddac)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:shdocvw:ClOleCommandTarget_Exec (0x190294)->((null) 29 2 0x33ebb8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x190294)
fixme:shdocvw:ClientSite_GetContainer (0x190294)->(0x33ebc8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x190294)->(0xb7ee4f49)
fixme:shdocvw:ClOleCommandTarget_Exec (0x190294)->((null) 25 2 0x33eb04 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x190294)->((null) 26 2 0x33eb04 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4

is this a known problem?  it there a different program i shpould be using to play WoW?

---

### Post by jpeddicord on 2007-10-04
I'm assuming that it just isn't compatible with Wine for the time being until some updates are released. Check [http://appdb.winehq.org/](http://appdb.winehq.org/) for compatibility* to find some tips on getting it running.

* Site is currently down, but should hopefully be back online soon.

Jacob

---

### Post by Faud on 2007-10-04
I was just playing WoW tonight with Wine...voice chat working perfectly

What version of wine are you using and with what sound drivers ?

You should be using the latest wine 0.9.46
and unless you love the launcher; open a terminal and start WoW with
wine "C:\Program Files\World of Warcraft\WoW.exe"

---

### Post by UbuntuniX on 2007-10-04
It is compatible, though the latest version of WINE causes some bugs. I'm not sure if it's in the 7.04 repository, though.

---

### Post by brigux on 2007-10-04
I do have this issue from time to time. It seems to be an issue with Wine/WoW messing up with the Network Card driver. 
Just rebooting the computer normally fixes it for me (I mean rebooting, not just restarting x)

Hope it helps

---

### Post by RyanZec on 2007-10-04
yea it fixed itself.

I have another issue now, the graphics are not all displaying like they should(most bars liek the casting bars and buff boxes(default ones)), anyone know what the issue is?

---

### Post by brigux on 2007-10-04
are you running the game with -opengl as in:
wine ./WoW.exe -opengl
If not, can you try?

---

### Post by Faud on 2007-10-04
Are you running any addons like Bongs or Bongos2 ?

---

