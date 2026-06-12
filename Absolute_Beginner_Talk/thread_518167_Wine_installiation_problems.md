---
title: "Wine installiation problems"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by GeneralHooHa on 2007-08-05
I just downloaded the wine source, and when typing ./tools/wineinstall, I get this:
```
../../../tools/makedep -C. -S../../.. -T../../..  system.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/uxtheme/tests'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/version/tests'
../../../tools/makedep -C. -S../../.. -T../../..  info.c install.c  version.rc  
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/version/tests'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/wininet/tests'
../../../tools/makedep -C. -S../../.. -T../../..  ftp.c generated.c http.c internet.c url.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/wininet/tests'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winmm/tests'
../../../tools/makedep -C. -S../../.. -T../../..  capture.c mci.c mixer.c mmio.c timer.c wave.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winmm/tests'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winspool.drv/tests'
../../../tools/makedep -C. -S../../.. -T../../..  info.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winspool.drv/tests'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/wintrust/tests'
../../../tools/makedep -C. -S../../.. -T../../..  crypt.c register.c            
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/wintrust/tests'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/ws2_32/tests'
../../../tools/makedep -C. -S../../.. -T../../..  protocol.c sock.c             
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/ws2_32/tests'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/glu32'
../../tools/makedep -C. -S../.. -T../..  glu.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/glu32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/opengl32'
../../tools/makedep -C. -S../.. -T../..  opengl_ext.c opengl_norm.c wgl.c  version.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/opengl32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/wined3d'
../../tools/makedep -C. -S../.. -T../..  arb_program_shader.c baseshader.c basetexture.c clipper.c context.c cubetexture.c device.c directx.c drawprim.c glsl_shader.c indexbuffer.c palette.c pixelshader.c query.c resource.c state.c stateblock.c surface.c surface_gdi.c swapchain.c texture.c utils.c vertexbuffer.c vertexdeclaration.c vertexshader.c volume.c volumetexture.c wined3d_main.c            
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/wined3d'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winequartz.drv'
../../tools/makedep -C. -S../.. -T../..  quartzdrv_main.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winequartz.drv'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winex11.drv'
../../tools/makedep -C. -S../.. -T../..  bitblt.c bitmap.c brush.c clipboard.c clipping.c codepage.c dce.c desktop.c dib.c dib_convert.c dib_dst_swap.c dib_src_swap.c event.c graphics.c init.c keyboard.c mouse.c opengl.c palette.c pen.c scroll.c settings.c text.c window.c winpos.c wintab.c x11ddraw.c x11drv_main.c xdnd.c xfont.c xim.c xinerama.c xrandr.c xrender.c xvidmode.c  version.rc           
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winex11.drv'
../tools/makedep -C. -S.. -T..
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/documentation'
../tools/makedep -C. -S.. -T..
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/documentation'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/fonts'
../tools/makedep -C. -S.. -T..
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/fonts'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/include'
../tools/makedep -C. -S.. -T..       activscp.idl amstream.idl amvideo.idl austream.idl comcat.idl control.idl d3d10.idl ddstream.idl dispex.idl docobj.idl downloadmgr.idl dxgi.idl dxgitype.idl exdisp.idl hlink.idl htiframe.idl iads.idl icftypes.idl indexsrv.idl mediaobj.idl mimeinfo.idl mlang.idl mmstream.idl mshtmhst.idl mshtml.idl msxml.idl msxml2.idl netfw.idl oaidl.idl objidl.idl objsafe.idl ocidl.idl ocmm.idl oledb.idl oleidl.idl optary.idl propidl.idl pstore.idl richole.idl sensevts.idl servprov.idl shldisp.idl shobjidl.idl shtypes.idl strmif.idl tom.idl unknwn.idl urlhist.idl urlmon.idl wine/itss.idl wtypes.idl xmldom.idl xmldso.idl
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/include'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/port'
../../tools/makedep -C. -S../.. -T../..  ffs.c fstatvfs.c futimes.c getopt.c getopt1.c getpagesize.c gettid.c interlocked.c lstat.c memcpy_unaligned.c memmove.c mkstemps.c pread.c pwrite.c readlink.c sigsetjmp.c spawn.c statvfs.c strcasecmp.c strerror.c strncasecmp.c usleep.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/port'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/wine'
../../tools/makedep -C. -S../.. -T../..  casemap.c collation.c compose.c config.c cptable.c debug.c fold.c ldt.c loader.c mbtowc.c mmap.c port.c sortkey.c string.c utf8.c wctomb.c wctype.c c_037.c c_424.c c_437.c c_500.c c_737.c c_775.c c_850.c c_852.c c_855.c c_856.c c_857.c c_860.c c_861.c c_862.c c_863.c c_864.c c_865.c c_866.c c_869.c c_874.c c_875.c c_878.c c_932.c c_936.c c_949.c c_950.c c_1006.c c_1026.c c_1250.c c_1251.c c_1252.c c_1253.c c_1254.c c_1255.c c_1256.c c_1257.c c_1258.c c_10000.c c_10006.c c_10007.c c_10029.c c_10079.c c_10081.c c_20127.c c_20866.c c_20932.c c_21866.c c_28591.c c_28592.c c_28593.c c_28594.c c_28595.c c_28596.c c_28597.c c_28598.c c_28599.c c_28600.c c_28603.c c_28604.c c_28605.c c_28606.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/wine'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/wpp'
../../tools/makedep -C. -S../.. -T../..  preproc.c wpp.c              ppy.y ppl.l
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/wpp'
../tools/makedep -C. -S.. -T..
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/loader'
../tools/makedep -C. -S.. -T..  glibc.c kthread.c main.c preloader.c pthread.c  
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/loader'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/clock'
../../tools/makedep -C. -S../.. -T../..  main.c winclock.c  rsrc.rc             
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/clock'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/cmd'
../../tools/makedep -C. -S../.. -T../..  batch.c builtins.c directory.c wcmdmain.c  wcmdrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/cmd'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/cmdlgtst'
../../tools/makedep -C. -S../.. -T../..  cmdlgtst.c  cmdlgr.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/cmdlgtst'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/control'
../../tools/makedep -C. -S../.. -T../..  control.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/control'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/eject'
../../tools/makedep -C. -S../.. -T../..  eject.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/eject'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/expand'
../../tools/makedep -C. -S../.. -T../..  expand.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/expand'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/explorer'
../../tools/makedep -C. -S../.. -T../..  desktop.c device.c diskarb.c explorer.c hal.c systray.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/explorer'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/hh'
../../tools/makedep -C. -S../.. -T../..  main.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/hh'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/icinfo'
../../tools/makedep -C. -S../.. -T../..  icinfo.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/icinfo'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/iexplore'
../../tools/makedep -C. -S../.. -T../..  main.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/iexplore'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/msiexec'
../../tools/makedep -C. -S../.. -T../..  msiexec.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/msiexec'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/net'
../../tools/makedep -C. -S../.. -T../..  net.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/net'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/notepad'
../../tools/makedep -C. -S../.. -T../.. -I../../include/msvcrt dialog.c main.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/notepad'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/oleview'
../../tools/makedep -C. -S../.. -T../..  details.c interface.c oleview.c pane.c tree.c typelib.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/oleview'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/progman'
../../tools/makedep -C. -S../.. -T../..  dialog.c group.c grpfile.c main.c program.c string.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/progman'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/regedit'
../../tools/makedep -C. -S../.. -T../.. -I../../include/msvcrt about.c childwnd.c edit.c framewnd.c hexedit.c listview.c main.c regedit.c regproc.c treeview.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/regedit'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/regsvr32'
../../tools/makedep -C. -S../.. -T../..  regsvr32.c  regsvr32.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/regsvr32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/rpcss'
../../tools/makedep -C. -S../.. -T../..  epmap_server.c np_server.c rpcss_main.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/rpcss'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/rundll32'
../../tools/makedep -C. -S../.. -T../..  rundll32.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/rundll32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/spoolsv'
../../tools/makedep -C. -S../.. -T../..  main.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/spoolsv'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/start'
../../tools/makedep -C. -S../.. -T../..  start.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/start'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/taskmgr'
../../tools/makedep -C. -S../.. -T../.. -I../../include/msvcrt about.c affinity.c applpage.c column.c dbgchnl.c debug.c endproc.c graph.c graphctl.c optnmenu.c perfdata.c perfpage.c priority.c proclist.c procpage.c run.c taskmgr.c trayicon.c  taskmgr.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/taskmgr'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/uninstaller'
../../tools/makedep -C. -S../.. -T../..  main.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/uninstaller'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/view'
../../tools/makedep -C. -S../.. -T../..  init.c view.c winmain.c  viewrc.rc     
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/view'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/wineboot'
../../tools/makedep -C. -S../.. -T../..  shutdown.c wineboot.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/wineboot'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winebrowser'
../../tools/makedep -C. -S../.. -T../..  main.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winebrowser'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winecfg'
../../tools/makedep -C. -S../.. -T../..  appdefaults.c audio.c drive.c drivedetect.c driveui.c libraries.c main.c theme.c winecfg.c x11drvdlg.c  winecfg.rc     
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winecfg'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/wineconsole'
../../tools/makedep -C. -S../.. -T../..  curses.c dialog.c registry.c user.c wineconsole.c  wineconsole_res.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/wineconsole'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winedbg'
../../tools/makedep -C. -S../.. -T../..  be_alpha.c be_i386.c be_ppc.c be_x86_64.c break.c db_disasm.c display.c expr.c gdbproxy.c info.c memory.c source.c symbol.c stack.c tgt_active.c tgt_minidump.c tgt_module.c types.c winedbg.c              dbg.y debug.l
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winedbg'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winedevice'
../../tools/makedep -C. -S../.. -T../..  device.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winedevice'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winefile'
../../tools/makedep -C. -S../.. -T../..  splitpath.c winefile.c  rsrc.rc        
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winefile'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winemenubuilder'
../../tools/makedep -C. -S../.. -T../..  winemenubuilder.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winemenubuilder'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winemine'
../../tools/makedep -C. -S../.. -T../..  dialog.c main.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winemine'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winepath'
../../tools/makedep -C. -S../.. -T../..  winepath.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winepath'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winetest'
../../tools/makedep -C. -S../.. -T../..  gui.c main.c send.c util.c  winetest.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winetest'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winevdm'
../../tools/makedep -C. -S../.. -T../..  winevdm.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winevdm'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winhelp'
../../tools/makedep -C. -S../.. -T../..  callback.c hlpfile.c macro.c string.c winhelp.c  rsrc.rc             macro.lex.l
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winhelp'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winver'
../../tools/makedep -C. -S../.. -T../..  winver.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/winver'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/wordpad'
../../tools/makedep -C. -S../.. -T../.. -I../../include/msvcrt wordpad.c  rsrc.rc
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/wordpad'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/xcopy'
../../tools/makedep -C. -S../.. -T../.. -I../../include/msvcrt xcopy.c  rsrc.rc 
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs/xcopy'
../tools/makedep -C. -S.. -T..
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/programs'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/server'
../tools/makedep -C. -S.. -T..  async.c atom.c change.c class.c clipboard.c console.c context_alpha.c context_i386.c context_powerpc.c context_sparc.c context_x86_64.c debugger.c device.c directory.c event.c fd.c file.c handle.c hook.c mach.c mailslot.c main.c mapping.c mutex.c named_pipe.c object.c process.c procfs.c ptrace.c queue.c region.c registry.c request.c semaphore.c serial.c signal.c snapshot.c sock.c symlink.c thread.c timer.c token.c trace.c unicode.c user.c window.c winstation.c
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/server'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/widl'
../../tools/makedep -C. -S../.. -T../..  client.c hash.c header.c proxy.c server.c typegen.c typelib.c utils.c widl.c write_msft.c              parser.y parser.l
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/widl'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winebuild'
../../tools/makedep -C. -S../.. -T../..  import.c main.c parser.c relay.c res16.c res32.c spec16.c spec32.c utils.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winebuild'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winedump'
../../tools/makedep -C. -S../.. -T../..  debug.c dos.c dump.c emf.c le.c lib.c lnk.c main.c minidump.c misc.c msc.c msmangle.c ne.c output.c pdb.c pe.c search.c symbol.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winedump'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winegcc'
../../tools/makedep -C. -S../.. -T../..  utils.c winegcc.c
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winegcc'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/wmc'
../../tools/makedep -C. -S../.. -T../..  lang.c mcl.c utils.c wmc.c write.c              mcy.y
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/wmc'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/wrc'
../../tools/makedep -C. -S../.. -T../..  dumpres.c genres.c newstruc.c readres.c translation.c utils.c wrc.c writeres.c              parser.y parser.l
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/wrc'
../tools/makedep -C. -S.. -T.. -I/usr/include/freetype2 bin2res.c fnt2bdf.c fnt2fon.c make_ctests.c makedep.c relpath.c sfnt2fnt.c
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools'
./tools/makedep -C. -S. -T.
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/port'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/wine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/wine'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs/wpp'
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/libs'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/widl'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winebuild'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winedump'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/winegcc'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/wmc'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/wrc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools/wrc'
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/tools'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/include'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/fonts'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/fonts'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/loader'
(GIT_DIR=../.git git-describe HEAD 2>/dev/null || echo "wine-0.9.42") | sed -e 's/\(.*\)/const char wine_version[] = "\1";/' >version-stamp || (rm -f version-stamp && exit 1)
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/loader'
make[1]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/dxerr8'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/dxerr8'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/dxerr9'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/dxerr9'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/dxguid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/dxguid'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/strmiids'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/strmiids'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/uuid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/uuid'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winecrt0'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/winecrt0'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/dinput'
make[2]: `libdinput.def.a' is up to date.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/dinput'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/acledit'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/acledit'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/activeds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/activeds'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/advapi32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/advapi32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/advpack'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/advpack'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/amstream'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/amstream'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/atl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/atl'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/avicap32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/avicap32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/avifil32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/avifil32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/browseui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/browseui'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cabinet'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cabinet'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/capi2032'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/capi2032'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cards'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cards'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cfgmgr32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cfgmgr32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/clusapi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/clusapi'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/comcat'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/comcat'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/comctl32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/comctl32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/comdlg32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/comdlg32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/compstui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/compstui'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/credui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/credui'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/crtdll'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/crtdll'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/crypt32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/crypt32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cryptdll'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cryptdll'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cryptnet'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/cryptnet'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/ctl3d32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/ctl3d32'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/d3d10'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/d3d10'
make[2]: Entering directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/d3d8'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./d3d8.spec    basetexture.o cubetexture.o d3d8_main.o device.o directx.o indexbuffer.o pixelshader.o resource.o stateblock.o surface.o swapchain.o texture.o vertexbuffer.o vertexdeclaration.o vertexshader.o volume.o volumetexture.o     version.res    -o d3d8.dll.so  -lwined3d -luser32 -lgdi32 -ladvapi32 -lkernel32  -ldxguid -luuid ../../libs/port/libwine_port.a
winebuild: resource.o is an empty file
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [d3d8.dll.so] Error 2
make[2]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls/d3d8'
make[1]: *** [d3d8] Error 2
make[1]: Leaving directory `/home/silve/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.
nick@Nafus-Laptop:~/Desktop/wine-0.9.42~winehq0~ubuntu~7.04.orig$

```

I think the bottom is all that matters, but what is wrong? Thank you very much.

---

### Post by wolfen69 on 2007-08-05
go here [http://www.getdeb.net/search.php?keywords=wine](http://www.getdeb.net/search.php?keywords=wine)  to download wine. just click to install it.

---

### Post by GeneralHooHa on 2007-08-05
Thank you! That worked even better than Synaptic.

---

