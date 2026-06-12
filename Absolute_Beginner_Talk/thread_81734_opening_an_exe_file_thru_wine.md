---
title: "opening an exe file thru wine"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by blueberrycheesecake on 2005-10-25
wine is already installed then i tried to open an exe file and this showed up:

fixme:ole:CoRegisterMessageFilter stub
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.12 Setup" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.12 Setup" of other process window (nil) should not use SendMessage
fixme:shell:BrsFolder_OnCreate flags 40 not implemented
fixme:shell:BrsFolderDlgProc Set selection "c:\\Program Files\\Mozilla ActiveX Control v1.7.12"
You need to install the Mozilla ActiveX control to
use Wine's builtin CLSID_WebBrowser from SHDOCVW.DLL
fixme:shdocvw:ProvideClassInfo_GetGUID (0x7fe03720)->(1 0x7e251f4c)
fixme:shdocvw:ProvideClassInfo_GetGUID Wrongly returning IPropertyNotifySink interface {9bfbbc02-eff1-101a-84ed-00aa00341d07}
fixme:shdocvw:QuickActivate_QuickActivate (0x7fe03720)->(0x7facd9d0 0x7facda10)
fixme:shdocvw:WebBrowser_QueryInterface (0x7fe03720)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x7facdad8) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x7fe03720)->(0x7facdaa4)
fixme:shdocvw:OleObject_Close (0x7fe03720)->(1)

what does it mean?:confused:

---

### Post by Murgle on 2005-11-30
what version of wine do you have installed?  I know they just released it as beta a while ago... That might fix your problems

---

### Post by aysiu on 2005-11-30
What program are you trying to run? Wine does not run all Windows programs successfully.

The "ActiveX" in there's got me worried, too. Linux does not have or emulate ActiveX.

---

### Post by tay on 2005-12-08
i was wondering too, how you can get this to work.

i need it too work before i can get some other wine applications to work.

ross-tech vag-com audi/vw/skodi diagnostic equipment

and i need to get an activex extension for firefox if  their is one.

[http://www.realarcade.com/?tps=google_&src=googlegames,mcode_googlegames2_](http://www.realarcade.com/?tps=google_&src=googlegames,mcode_googlegames2_)

it is the same plugin.  Is this really impossible?

how come?

---

### Post by YokoZar on 2005-12-08
To install Mozilla ActiveX, download this file: [http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz)

Untar it to any directory, then navigate to that directory in a terminal and run regsvr32 mozctlx.dll

---

### Post by tay on 2005-12-08
[http://www.iol.ie/~locka/mozilla/mozilla.htm](http://www.iol.ie/~locka/mozilla/mozilla.htm)

---

### Post by tay on 2005-12-08
[email]root@sahaihost:/home/sahai/.wine[/email]/drive_c # tar -xvzf mozcontrol-1.tgz /home/sahai/.wine/drive_c/mozactivex/
tar: mozcontrol-1.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /home/sahai/.wine/drive_c/mozactivex: Not found in archive
tar: Error exit delayed from previous errors
[email]root@sahaihost:/home/sahai/.wine[/email]/drive_c #

---

### Post by Jengu on 2005-12-08
If the application does what you want it to, just ignore all that gibberish. Even with applications it works with, wine generates alot of output. That output is aimed at bugging developers to let them know when a hack is making something work or something isn't fully implemented. That doesn't mean it isn't implemented enough for the app you're trying to work though.

ActiveX is a microsoft specific technology. In order to be able to use it under linux, the wine developers have made a clever trick -- you install the windows version of mozilla with wine, and the mozilla ActiveX plugin with wine. This then gives any apps you install with wine the ability to use ActiveX. You can find the windows version of mozilla at mozilla.org, and you can find the ActiveX plugin here:

[http://www.iol.ie/~locka/mozilla/MozillaControl177.exe](http://www.iol.ie/~locka/mozilla/MozillaControl177.exe)

---

### Post by tay on 2005-12-08
do i have to uninstall mozilla-firefox for linux first?

---

### Post by YokoZar on 2005-12-08
[QUOTE=tay]do i have to uninstall mozilla-firefox for linux first?[/QUOTE]
No.  The Wine environment is kept seperate from everything on the system, and all stuff installed in your virtual windows installation is in your home directory (at ~/.wine)

---

### Post by tay on 2005-12-08
the new exe file cannot install because it cannot find the /mozilla/bin  which i don't see in there either.  

that was the same problem i had with linux mozilla, and now the same thing after i installed mozilla in wine.

also mozilla in wine, could not access the internet.  how do i give permissions to the wine browser?

sorry to lay out all these questions.. seems you few couple people are the only ones successfully using wine for active-x browser applications.

---

### Post by tay on 2005-12-09
[email]root@sahaihost:/home/sahai/.wine[/email]/drive_c/mozactivex # ls
MozillaControl177.exe
[email]root@sahaihost:/home/sahai/.wine[/email]/drive_c/mozactivex # wine MozillaControl177.exe
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.7 Setup" of other proc ess window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.7 Setup" of other proc ess window (nil) should not use SendMessage
fixme:shell:BrsFolder_OnCreate flags 40 not implemented
fixme:shell:BrsFolderDlgProc Set selection "c:\\Program Files\\Mozilla ActiveX Control v1. 7.7"
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Common Files\\Mozilla ActiveX Control v1.7.7\\mozctl.dll") not found




also  i looked for it.. MSVCP60.dll



root@sahaihost:/home/sahai # locate MSVCP60.dll
root@sahaihost:/home/sahai # locate dll
/etc/sane.d/dll.conf
/usr/share/man/man1/dlltool.1.gz
/usr/share/man/man5/sane-dll.5.gz
/usr/lib/sane/libsane-dll.so.1.0.15
/usr/lib/sane/libsane-dll.la
/usr/lib/sane/libsane-dll.so.1
/usr/lib/wine/mapi32.dll.so
/usr/lib/wine/dmusic32.dll.so
/usr/lib/wine/mscms.dll.so
/usr/lib/wine/shell32.dll.so
/usr/lib/wine/d3dxof.dll.so
/usr/lib/wine/psapi.dll.so
/usr/lib/wine/capi2032.dll.so
/usr/lib/wine/wininet.dll.so
/usr/lib/wine/rsaenh.dll.so
/usr/lib/wine/cabinet.dll.so
/usr/lib/wine/msi.dll.so
/usr/lib/wine/odbccp32.dll.so
/usr/lib/wine/dmscript.dll.so
/usr/lib/wine/amstream.dll.so
/usr/lib/wine/vdmdbg.dll.so
/usr/lib/wine/powrprof.dll.so
/usr/lib/wine/secur32.dll.so
/usr/lib/wine/advapi32.dll.so
/usr/lib/wine/d3d8.dll.so
/usr/lib/wine/ws2_32.dll.so
/usr/lib/wine/oledlg.dll.so
/usr/lib/wine/w32skrnl.dll.so
/usr/lib/wine/odbc32.dll.so
/usr/lib/wine/wintab32.dll.so
/usr/lib/wine/iphlpapi.dll.so
/usr/lib/wine/msvfw32.dll.so
/usr/lib/wine/wnaspi32.dll.so
/usr/lib/wine/dmsynth.dll.so
/usr/lib/wine/msvcrtd.dll.so
/usr/lib/wine/crtdll.dll.so
/usr/lib/wine/version.dll.so
/usr/lib/wine/mcicda.dll.so
/usr/lib/wine/sti.dll.so
/usr/lib/wine/iccvid.dll.so
/usr/lib/wine/advpack.dll.so
/usr/lib/wine/dbghelp.dll.so
/usr/lib/wine/shlwapi.dll.so
/usr/lib/wine/riched32.dll.so
/usr/lib/wine/wined3d.dll.so
/usr/lib/wine/serialui.dll.so
/usr/lib/wine/avicap32.dll.so
/usr/lib/wine/ole32.dll.so
/usr/lib/wine/ntdll.dll.so
/usr/lib/wine/olepro32.dll.so
/usr/lib/wine/lz32.dll.so
/usr/lib/wine/libcryptdll.def
/usr/lib/wine/wtsapi32.dll.so
/usr/lib/wine/imm32.dll.so
/usr/lib/wine/newdev.dll.so
/usr/lib/wine/d3dx8.dll.so
/usr/lib/wine/crypt32.dll.so
/usr/lib/wine/msnet32.dll.so
/usr/lib/wine/msimg32.dll.so
/usr/lib/wine/url.dll.so
/usr/lib/wine/wow32.dll.so
/usr/lib/wine/comctl32.dll.so
/usr/lib/wine/dinput8.dll.so
/usr/lib/wine/olesvr32.dll.so
/usr/lib/wine/msvcrt.dll.so
/usr/lib/wine/dciman32.dll.so
/usr/lib/wine/winmm.dll.so
/usr/lib/wine/glu32.dll.so
/usr/lib/wine/ctl3d32.dll.so
/usr/lib/wine/rundll32.exe.so
/usr/lib/wine/avifil32.dll.so
/usr/lib/wine/atl.dll.so
/usr/lib/wine/netapi32.dll.so
/usr/lib/wine/cards.dll.so
/usr/lib/wine/dplayx.dll.so
/usr/lib/wine/winnls32.dll.so
/usr/lib/wine/gdi32.dll.so
/usr/lib/wine/ddraw.dll.so
/usr/lib/wine/devenum.dll.so
/usr/lib/wine/mciseq.dll.so
/usr/lib/wine/cfgmgr32.dll.so
/usr/lib/wine/riched20.dll.so
/usr/lib/wine/comdlg32.dll.so
/usr/lib/wine/imagehlp.dll.so
/usr/lib/wine/objsel.dll.so
/usr/lib/wine/itss.dll.so
/usr/lib/wine/mswsock.dll.so
/usr/lib/wine/msacm32.dll.so
/usr/lib/wine/libntdll.def
/usr/lib/wine/activeds.dll.so
/usr/lib/wine/dpnet.dll.so
/usr/lib/wine/dmcompos.dll.so
/usr/lib/wine/olecli32.dll.so
/usr/lib/wine/msrle32.dll.so
/usr/lib/wine/mciavi32.dll.so
/usr/lib/wine/dswave.dll.so
/usr/lib/wine/rasapi32.dll.so
/usr/lib/wine/tapi32.dll.so
/usr/lib/wine/dmloader.dll.so
/usr/lib/wine/d3dim.dll.so
/usr/lib/wine/msxml3.dll.so
/usr/lib/wine/opengl32.dll.so
/usr/lib/wine/rpcrt4.dll.so
/usr/lib/wine/msvidc32.dll.so
/usr/lib/wine/oleaut32.dll.so
/usr/lib/wine/dsound.dll.so
/usr/lib/wine/snmpapi.dll.so
/usr/lib/wine/twain_32.dll.so
/usr/lib/wine/shfolder.dll.so
/usr/lib/wine/winedos.dll.so
/usr/lib/wine/quartz.dll.so
/usr/lib/wine/mshtml.dll.so
/usr/lib/wine/user32.dll.so
/usr/lib/wine/kernel32.dll.so
/usr/lib/wine/msvcrt20.dll.so
/usr/lib/wine/d3d9.dll.so
/usr/lib/wine/dmime.dll.so
/usr/lib/wine/comcat.dll.so
/usr/lib/wine/sensapi.dll.so
/usr/lib/wine/dpnhpast.dll.so
/usr/lib/wine/msdmo.dll.so
/usr/lib/wine/dplay.dll.so
/usr/lib/wine/midimap.dll.so
/usr/lib/wine/unicows.dll.so
/usr/lib/wine/mlang.dll.so
/usr/lib/wine/wldap32.dll.so
/usr/lib/wine/uxtheme.dll.so
/usr/lib/wine/mpr.dll.so
/usr/lib/wine/cryptdll.dll.so
/usr/lib/wine/dinput.dll.so
/usr/lib/wine/rsabase.dll.so
/usr/lib/wine/msvcrt40.dll.so
/usr/lib/wine/d3drm.dll.so
/usr/lib/wine/wsock32.dll.so
/usr/lib/wine/dxdiagn.dll.so
/usr/lib/wine/dmstyle.dll.so
/usr/lib/wine/qcap.dll.so
/usr/lib/wine/dmusic.dll.so
/usr/lib/wine/oleacc.dll.so
/usr/lib/wine/usp10.dll.so
/usr/lib/wine/dmband.dll.so
/usr/lib/wine/setupapi.dll.so
/usr/lib/wine/wintrust.dll.so
/usr/lib/wine/shdocvw.dll.so
/usr/lib/wine/libcrtdll.def
/usr/lib/wine/urlmon.dll.so
/usr/lib/wine/icmp.dll.so
/usr/lib/wine/msvideo.dll.so
/usr/lib/wine/toolhelp.dll.so
/usr/lib/wine/winnls.dll.so
/usr/lib/wine/setupx.dll.so
/usr/lib/wine/olecli.dll.so
/usr/lib/wine/dispdib.dll.so
/usr/lib/wine/win87em.dll.so
/usr/lib/wine/winaspi.dll.so
/usr/lib/wine/wintab.dll.so
/usr/lib/wine/msacm.dll.so
/usr/lib/wine/storage.dll.so
/usr/lib/wine/wprocs.dll.so
/usr/lib/wine/ole2nls.dll.so
/usr/lib/wine/ddeml.dll.so
/usr/lib/wine/compobj.dll.so
/usr/lib/wine/win32s16.dll.so
/usr/lib/wine/typelib.dll.so
/usr/lib/wine/ole2conv.dll.so
/usr/lib/wine/twain.dll.so
/usr/lib/wine/commdlg.dll.so
/usr/lib/wine/ole2prox.dll.so
/usr/lib/wine/mmsystem.dll.so
/usr/lib/wine/olesvr.dll.so
/usr/lib/wine/stress.dll.so
/usr/lib/wine/ctl3d.dll.so
/usr/lib/wine/w32sys.dll.so
/usr/lib/wine/ole2.dll.so
/usr/lib/wine/windebug.dll.so
/usr/lib/wine/ole2thk.dll.so
/usr/lib/wine/wing.dll.so
/usr/lib/wine/ver.dll.so
/usr/lib/wine/shell.dll.so
/usr/lib/wine/ctl3dv2.dll.so
/usr/lib/wine/rasapi16.dll.so
/usr/lib/wine/lzexpand.dll.so
/usr/lib/wine/winsock.dll.so
/usr/lib/wine/imm.dll.so
/usr/lib/wine/ole2disp.dll.so
/usr/lib/wine/avifile.dll.so
/home/sahai/Desktop/mozcontrol/components/accessibility.dll
/home/sahai/Desktop/mozcontrol/components/appshell.dll
/home/sahai/Desktop/mozcontrol/components/caps.dll
/home/sahai/Desktop/mozcontrol/components/chrome.dll
/home/sahai/Desktop/mozcontrol/components/cookie.dll
/home/sahai/Desktop/mozcontrol/components/docshell.dll
/home/sahai/Desktop/mozcontrol/components/editor.dll
/home/sahai/Desktop/mozcontrol/components/embedcomponents.dll
/home/sahai/Desktop/mozcontrol/components/gkgfxwin.dll
/home/sahai/Desktop/mozcontrol/components/gklayout.dll
/home/sahai/Desktop/mozcontrol/components/gkparser.dll
/home/sahai/Desktop/mozcontrol/components/gkplugin.dll
/home/sahai/Desktop/mozcontrol/components/gkwidget.dll
/home/sahai/Desktop/mozcontrol/components/i18n.dll
/home/sahai/Desktop/mozcontrol/components/imglib2.dll
/home/sahai/Desktop/mozcontrol/components/ipcdc.dll
/home/sahai/Desktop/mozcontrol/components/jar50.dll
/home/sahai/Desktop/mozcontrol/components/necko.dll
/home/sahai/Desktop/mozcontrol/components/necko2.dll
/home/sahai/Desktop/mozcontrol/components/pipboot.dll
/home/sahai/Desktop/mozcontrol/components/pipnss.dll
/home/sahai/Desktop/mozcontrol/components/profile.dll
/home/sahai/Desktop/mozcontrol/components/rdf.dll
/home/sahai/Desktop/mozcontrol/components/uconv.dll
/home/sahai/Desktop/mozcontrol/components/ucvmath.dll
/home/sahai/Desktop/mozcontrol/components/webbrwsr.dll
/home/sahai/Desktop/mozcontrol/components/xmlextras.dll
/home/sahai/Desktop/mozcontrol/components/xpc3250.dll
/home/sahai/Desktop/mozcontrol/components/xpcom_compat_c.dll
/home/sahai/Desktop/mozcontrol/components/xppref32.dll
/home/sahai/Desktop/mozcontrol/gkgfx.dll
/home/sahai/Desktop/mozcontrol/ipc/modules/lockmodule.dll
/home/sahai/Desktop/mozcontrol/ipc/modules/transmgr.dll
/home/sahai/Desktop/mozcontrol/js3250.dll
/home/sahai/Desktop/mozcontrol/mozctl.dll
/home/sahai/Desktop/mozcontrol/mozctlx.dll
/home/sahai/Desktop/mozcontrol/mozz.dll
/home/sahai/Desktop/mozcontrol/msvcp60.dll
/home/sahai/Desktop/mozcontrol/nspr4.dll
/home/sahai/Desktop/mozcontrol/nss3.dll
/home/sahai/Desktop/mozcontrol/nssckbi.dll
/home/sahai/Desktop/mozcontrol/plc4.dll
/home/sahai/Desktop/mozcontrol/plds4.dll
/home/sahai/Desktop/mozcontrol/plugins/npnul32.dll
/home/sahai/Desktop/mozcontrol/smime3.dll
/home/sahai/Desktop/mozcontrol/softokn3.dll
/home/sahai/Desktop/mozcontrol/ssl3.dll
/home/sahai/Desktop/mozcontrol/xpcom.dll
/home/sahai/Desktop/mozcontrol/xpcom_compat.dll
/home/sahai/Desktop/mozcontrol/xpcom_core.dll
/home/sahai/.wine/drive_c/windows/temp/is-V85ST.tmp/_isetup/_shfoldr.dll
/home/sahai/.wine/drive_c/windows/rundll32.exe
/home/sahai/.wine/drive_c/Program Files/Shareaza/Plugins/zlibwapi.dll
/home/sahai/.wine/drive_c/Program Files/Shareaza/Plugins/ImageServices.dll
/home/sahai/.wine/drive_c/Program Files/Shareaza/Plugins/ImageViewer.dll
/home/sahai/.wine/drive_c/Program Files/Shareaza/Plugins/MediaPlayer.dll
/home/sahai/.wine/drive_c/Program Files/Shareaza/Plugins/SkinScanSKS.dll
/home/sahai/.wine/drive_c/Program Files/Shareaza/Plugins/RazaWebHook.dll
/home/sahai/.wine/drive_c/Program Files/Shareaza/zlibwapi.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/msvcr70. dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/msvcp70. dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/gkgfx.dl l
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/js3250.d ll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/mozctl.d ll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/mozctlx. dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/mozz.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/nspr4.dl l
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/nss3.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/nssckbi. dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/plc4.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/plds4.dl l
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/smime3.d ll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/softokn3 .dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/ssl3.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/xpcom.dl l
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/xpcom_co mpat.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/accessibility.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/appshell.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/caps.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/chrome.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/cookie.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/docshell.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/editor.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/embedcomponents.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/embed_lite.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/gkgfxwin.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/gklayout.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/gkparser.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/gkplugin.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/gkwidget.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/i18n.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/imglib2.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/ipcdc.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/jar50.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/necko.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/necko2.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/pipboot.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/pipnss.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/profile.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/rdf.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/uconv.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/ucvmath.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/webbrwsr.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/xmlextras.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/xpc3250.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/xpcom_compat_c.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/componen ts/xppref32.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/ipc/modu les/lockmodule.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/ipc/modu les/transmgr.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/plugins/ npmozax.dll
/home/sahai/.wine/drive_c/Program Files/Mozilla ActiveX Control v1.7.12/plugins/ npnul32.dll
/root/.wine/drive_c/windows/temp/ABDResource.dll
/root/.wine/drive_c/windows/temp/ABDComponents.dll
/root/.wine/drive_c/windows/rundll32.exe
/opt/LimeWire/GenericWindowsUtils.dll
/opt/LimeWire/LimeWire20.dll
/opt/LimeWire/WindowsV5PlusUtils.dll
root@sahaihost:/home/sahai #

which is strange..  i don't have that dll.  so  anyone have a clue?

---

### Post by YokoZar on 2005-12-09
[QUOTE=tay][email]root@sahaihost:/home/sahai/.wine[/email]/drive_c/mozactivex # ls
MozillaControl177.exe
[email]root@sahaihost:/home/sahai/.wine[/email]/drive_c/mozactivex # wine MozillaControl177.exe
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.7 Setup" of other proc ess window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.7 Setup" of other proc ess window (nil) should not use SendMessage
fixme:shell:BrsFolder_OnCreate flags 40 not implemented
fixme:shell:BrsFolderDlgProc Set selection "c:\\Program Files\\Mozilla ActiveX Control v1. 7.7"
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Common Files\\Mozilla ActiveX Control v1.7.7\\mozctl.dll") not found[/QUOTE]Do not run Wine as root.

**Do not run Wine as root.**

---

### Post by YokoZar on 2005-12-09
[QUOTE=tay][email]root@sahaihost:/home/sahai/.wine[/email]/drive_c # tar -xvzf mozcontrol-1.tgz /home/sahai/.wine/drive_c/mozactivex/
tar: mozcontrol-1.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /home/sahai/.wine/drive_c/mozactivex: Not found in archive
tar: Error exit delayed from previous errors
[email]root@sahaihost:/home/sahai/.wine[/email]/drive_c #[/QUOTE]maybe you should point tar at an actual existing file.  mozcontrol-1.tgz isn't the name of the file you downloaded.  Also, do not do this as root, do this as your user, otherwise you'll have permissions all wrong and the activex control won't be installed into your user's Wine drive.

---

### Post by Mr. Electric Wizard on 2005-12-09
Anybody know if this Windows Mozilla hack will allow MS Word 2000 to run [under Wine]?

---

### Post by tay on 2005-12-10
i keep on getting to the missing dll, and the mozilla plugin not being able to find /mozilla/bin

which does'nt exist.

[email]sahai@sahaihost:~/.wine[/email]/drive_c$ cd ./mozactivex
[email]sahai@sahaihost:~/.wine[/email]/drive_c/mozactivex$ ls
MozillaControl177.exe
[email]sahai@sahaihost:~/.wine[/email]/drive_c/mozactivex$ wine MozillaControl177.exe
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.7 Setup" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.7 Setup" of other process window (nil) should not use SendMessage
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Mozilla ActiveX Control v1.7.7\\mozctl.dll") not found


sahai@sahaihost:~$ locate /mozilla/bin
sahai@sahaihost:~$[ATTACH]4383[/ATTACH]

---

### Post by tay on 2005-12-11
this one activex thing could enable alot of microsoft programs to run under wine.

---

### Post by JimS on 2005-12-11
FYI

There are 2 articles on Wine in _Linux Pro Magazine_
by Joachim Von Thadden.

August 2005 issue has a 7 page article on Wine.
September 2005 issue has a 5 page article on Wine Tools.

The author writes that he uses version 20041019 rather
than more current 200510xx due to its better stability.
Also the author writes that Wine packages supplied with
Debian - highly unpredictable.  (Does that apply to Ubuntu?)
Better to go to Wine HQ is the author's advise.
[www.winehq.org](www.winehq.org)

Wine Tools homepage: 
[www.von-thadden.de/Joachim/WineTools](www.von-thadden.de/Joachim/WineTools)

Wine Weekly Newsletter issue 300 has an article
"Installing the Mozilla ActiveX Control"
winehq.org/?issue=300

JimS - not a Wine user.

---

### Post by YokoZar on 2005-12-11
[QUOTE=JimS]The author writes that he uses version 20041019 rather
than more current 200510xx due to its better stability.[/QUOTE]
Winetools is now designed to use the next stable release of Wine that came out, 0.9.0.  You can also use it with 0.9.3, the latest release, which is pretty stable too.

> Also the author writes that Wine packages supplied with
Debian - highly unpredictable.  (Does that apply to Ubuntu?)
Better to go to Wine HQ is the author's advise.
[www.winehq.org](www.winehq.org)The Debian packages being so screwy is what drove me to start making the Ubuntu packages in the first place.  Those are the ones at winehq.  They also work in Debian.

---

### Post by tay on 2005-12-12
thanks for the info.  i downloaded the missing dlls, and unziped them and moved them into the windows folder of my /.wine drive.  i'll try later tonight to point mozilla to that dll dir in windows.  and see if that works.

---

### Post by tay on 2005-12-12
thanks

---

