---
title: "Wine--- problem winecfg"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-09
i have installed wine using 
```
sudo apt-get install wine
```

now according to the search i have done on google i have to do 
```
winecfg
```
but when i do this i get
```
bash: winecfg: command not found
```

---

### Post by kaamos on 2006-03-09
What is the output of
```
wine --version
```
?

---

### Post by animesh on 2006-03-09
wine --version
if  i do not click any option on the dialog box then i get

wine --version
```
Invoking /usr/lib/wine/wine.bin --version ...
wine: creating configuration directory '/home/animesh/.wine'...
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
wine: '/home/animesh/.wine' created successfully.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Wine 20050310
Wine exited with a successful status
/usr/bin/wine: line 609: 30495 Terminated              $XMESSAGE -timeout 30 -buttons "    Dismiss    ":0," Never display this message again ":3 -title "Wine Launch Window" "Invoking $WINEBIN/$WINE_BIN_NAME $@ ...

        This dialog box is a temporary status dialog to let you know
        that Wine is attempting to launch your application.

        Since Wine is still very much in a development stage,
        many applications will fail silently.
        This dialog box is your indication
        that we're *trying* to run your application.

        This dialog box will automatically disappear after 30 seconds,
        or after your application finishes.

        You can permanently disable this dialog by selecting
        the option below.
        " 2>/dev/null

```

if i click on dismiss option in the dialog box then

```
Invoking /usr/lib/wine/wine.bin --version ...
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Wine 20050310
Wine exited with a successful status
```

---

### Post by kaamos on 2006-03-09
Oookay. I think you have a version of wine that does not even have winecfg. Here is a way to upgrade wine (to 0.9.9) from the command line.

```
sudo su
cp /etc/apt/sources.list /etc/apt/sources.list.bak
echo "deb http://wine.sourceforge.net/apt/ binary/" >> /etc/apt/sources.list
apt-get update
apt-get upgrade
exit
winecfg
```

If you rather wish to use synaptic, here are instructions -> [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

The wine servers aren't in a very good shape right not because they just released a new version and everyone is downloading it. So if your connections times out or something, just try again.

---

### Post by animesh on 2006-03-09
it upgraded other things like gaim ,xchat ....but not wine,libwine these 2 were the only packages not to be upgraded

The following packages have been kept back:
  libwine wine
The following packages will be upgraded:
  file-roller gaim gaim-data gimp gimp-data gimp-python
  gtk2-engines-clearlooks jfsutils libgimp2.0 xchat xchat-common
11 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


so after doing exactly as you told i am still getting the same error on doing winecfg

---

### Post by kaamos on 2006-03-09
Ah it still depends on libwine.

So remove wine and libwine packages and then install wine again.
```
sudo apt-get remove wine libwine
sudo apt-get install wine
```
(and hope the server is not too busy)

It also might be a good idea to move the old configuration files out of the way before running winecfg
```
mv ~/.wine ~/.wine_old
winecfg
```

---

### Post by OSConvert on 2006-03-09
I am also having difficulty in starting winecfg.  I get the following output:

home@home:~$ winecfg
wine: creating configuration directory '/home/home/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ec2f13f (thread 0009), starting debugger...
WineDbg starting on pid 0x8
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image C:\windows\rundll32.exeUnhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ec2f13f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ec2f13f ESP:7faffc2c EBP:7faffc68 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c0d72a8 ECX:b7f5d900 EDX:7c018df8
 ESI:7c018df8 EDI:7c018df8
Stack dump:
0x7faffc2c:  7c018df8 7ec649a0 7c018df8 7ec2dab6
0x7faffc3c:  7c018df8 7c018df8 7ed357d0 7c0d7198
0x7faffc4c:  7ec8a883 7c018df8 7c0d719c 00000001
0x7faffc5c:  7edd3bec 7eddc9f4 00000000 7faffc88
0x7faffc6c:  7ed9edb7 7c018df8 7edd3bec 7faffc88
0x7faffc7c:  7ed9eda6 7edd3bec 00000001 7faffdc8
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ec2f13f in libgl.so.1 (+0x3613f) (0x7ec2f13f)
  2 0x7ed9edb7 X11DRV_GDI_Finalize+0x27 in winex11 (0x7ed9edb7)
  3 0x7edb52b1 DllMain+0x41 in winex11 (0x7edb52b1)
  4 0x7edc431c in winex11 (+0x5431c) (0x7edc431c)
  5 0x7bebb125 call_dll_entry_point+0x15 in ntdll (0x7bebb125)
  6 0x7bebbf3a in ntdll (+0x1bf3a) (0x7bebbf3a)
  7 0x7bebc21a in ntdll (+0x1c21a) (0x7bebc21a)
  8 0x7fcdc5d9 ExitProcess+0x19 in kernel32 (0x7fcdc5d9)
  9 0x7fb1eb36 in rundll32 (+0xeb36) (0x7fb1eb36)
  10 0x7fcddc9f in kernel32 (+0x4dc9f) (0x7fcddc9f)
  11 0xb7f82107 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f82107)
0x7ec2f13f: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (94 modules)
ELF     0x7be86000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7da18000-7da30000     Deferred        advpack<elf>
  \-PE  0x7da20000-7da30000     \               advpack
ELF     0x7db73000-7dbcb000     Deferred        shlwapi<elf>
  \-PE  0x7db90000-7dbcb000     \               shlwapi
ELF     0x7dbcb000-7dc90000     Deferred        shell32<elf>
  \-PE  0x7dbe0000-7dc90000     \               shell32
ELF     0x7dc90000-7dcc1000     Deferred        uxtheme<elf>
  \-PE  0x7dca0000-7dcc1000     \               uxtheme
ELF     0x7dcc1000-7dd75000     Deferred        comctl32<elf>
  \-PE  0x7dcd0000-7dd75000     \               comctl32
ELF     0x7dd75000-7ddc5000     Deferred        dsound<elf>
  \-PE  0x7dd90000-7ddc5000     \               dsound
ELF     0x7ddc5000-7de20000     Deferred        quartz<elf>
  \-PE  0x7dde0000-7de20000     \               quartz
ELF     0x7df31000-7df46000     Deferred        midimap<elf>
  \-PE  0x7df40000-7df46000     \               midimap
ELF     0x7df46000-7df5d000     Deferred        msacm<elf>
  \-PE  0x7df50000-7df5d000     \               msacm
ELF     0x7df5d000-7dfa0000     Deferred        wineoss<elf>
  \-PE  0x7df70000-7dfa0000     \               wineoss
ELF     0x7dfc3000-7dfe8000     Deferred        msvfw32<elf>
  \-PE  0x7dfd0000-7dfe8000     \               msvfw32
ELF     0x7dfe8000-7e079000     Deferred        oleaut32<elf>
  \-PE  0x7e000000-7e079000     \               oleaut32
ELF     0x7e079000-7e105000     Deferred        ole32<elf>
  \-PE  0x7e090000-7e105000     \               ole32
ELF     0x7e105000-7e18c000     Deferred        winmm<elf>
  \-PE  0x7e110000-7e18c000     \               winmm
ELF     0x7e18c000-7e1b0000     Deferred        msacm32<elf>
  \-PE  0x7e190000-7e1b0000     \               msacm32
ELF     0x7e2c6000-7e2da000     Deferred        avicap32<elf>
  \-PE  0x7e2d0000-7e2da000     \               avicap32
ELF     0x7e2da000-7e300000     Deferred        devenum<elf>
  \-PE  0x7e2f0000-7e300000     \               devenum
ELF     0x7e300000-7e31e000     Deferred        iphlpapi<elf>
  \-PE  0x7e310000-7e31e000     \               iphlpapi
ELF     0x7e31e000-7e366000     Deferred        rpcrt4<elf>
  \-PE  0x7e330000-7e366000     \               rpcrt4
ELF     0x7e366000-7e37a000     Deferred        lz32<elf>
  \-PE  0x7e370000-7e37a000     \               lz32
ELF     0x7e37a000-7e393000     Deferred        version<elf>
  \-PE  0x7e380000-7e393000     \               version
ELF     0x7e393000-7e3e6000     Deferred        setupapi<elf>
  \-PE  0x7e3a0000-7e3e6000     \               setupapi
ELF     0x7e440000-7e444000     Deferred        libxfixes.so.3
ELF     0x7e444000-7e44d000     Deferred        libxcursor.so.1
ELF     0x7e44d000-7e469000     Deferred        imm32<elf>
  \-PE  0x7e450000-7e469000     \               imm32
ELF     0x7e469000-7e485000     Deferred        ximcp.so.2
ELF     0x7e485000-7e488000     Deferred        libxrandr.so.2
ELF     0x7e488000-7e490000     Deferred        libxrender.so.1
ELF     0x7e490000-7ebf9000     Deferred        libglcore.so.1
ELF     0x7ebf9000-7ec78000     Export          libgl.so.1
ELF     0x7ec78000-7ed38000     Deferred        libx11.so.6
ELF     0x7ed38000-7ed45000     Deferred        libxext.so.6
ELF     0x7ed45000-7ed5e000     Deferred        libice.so.6
ELF     0x7ed5e000-7eddd000     Export          winex11<elf>
  \-PE  0x7ed70000-7eddd000     \               winex11
ELF     0x7eddd000-7edfc000     Deferred        libexpat.so.1
ELF     0x7edfc000-7ee2a000     Deferred        libfontconfig.so.1
ELF     0x7ee2a000-7ee3e000     Deferred        libz.so.1
ELF     0x7ee3e000-7eea8000     Deferred        libfreetype.so.6
ELF     0x7eea8000-7eee5000     Deferred        advapi32<elf>
  \-PE  0x7eeb0000-7eee5000     \               advapi32
ELF     0x7efcb000-7f8ce000     Deferred        gdi32<elf>
  \-PE  0x7f010000-7f8ce000     \               gdi32
ELF     0x7f8ce000-7f9f0000     Deferred        user32<elf>
  \-PE  0x7f8f0000-7f9f0000     \               user32
ELF     0x7fb01000-7fb0c000     Deferred        libgcc_s.so.1
PE      0x7fb0c000-7fb20000     Export          rundll32
PE      0x7fb10000-7fb20000     Export          rundll32
ELF     0x7fb21000-7fb23000     Deferred        xlcutf8load.so.2
ELF     0x7fb25000-7fb2a000     Deferred        libxxf86vm.so.1
ELF     0x7fc72000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe81000-7fe83000     Deferred        libnvidia-tls.so.1
ELF     0x7fe83000-7fe88000     Deferred        libxxf86dga.so.1
ELF     0x7fe88000-7fe92000     Deferred        libnss_files.so.2
ELF     0x7fe92000-7fe9b000     Deferred        libnss_nis.so.2
ELF     0x7fe9b000-7feb0000     Deferred        libnsl.so.1
ELF     0x7feb0000-7feb9000     Deferred        libnss_compat.so.2
ELF     0x7feb9000-7febd000     Deferred        libxdmcp.so.6
ELF     0x7febd000-7fec4000     Deferred        libsm.so.6
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e2f000-b7e32000     Deferred        libdl.so.2
ELF     0xb7e32000-b7f60000     Deferred        libc.so.6
ELF     0xb7f60000-b7f72000     Deferred        libpthread.so.0
ELF     0xb7f72000-b7f75000     Deferred        libxau.so.6
ELF     0xb7f7d000-b7f97000     Export          libwine.so.1
ELF     0xb7f9a000-b7fb0000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==

Sorry for the long list.  If I knew how to use scroll bars I would.
Any help would be appreciated.

---

