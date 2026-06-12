---
title: "App. Help"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by venoom27 on 2007-07-08
I installed ubuntu yesterday and love it! It runs so much better then a Windows OS.

I am a web developer and need to have access to Flash and have tried installing Flash 8 through Wine but it will not install. I have also tried to installing f4l-0.2.1 but cannot get it to install. I was wondering if anyone had any suggestions? Would a copy of Flash MX work better in Wine? 

Also I am currently connecting to work via Check Point's Secure Remote is there another VPN client I could use instead of Secure Remote since I am having trouble installing it on my box?


Thanks

---

### Post by trinaryouroboros on 2007-07-09
Why are you using Wine to install flash? Are you using 64-bit Ubuntu? If so, there's workarounds for that natively.

Otherwise, you could try IE4Linux:

[http://www.tatanka.com.br/](http://www.tatanka.com.br/)

In regards to the Remote Access, see the following:

[https://launchpad.net/bounties/rverrips](https://launchpad.net/bounties/rverrips)

Work in progress here at Ubuntu Forums:

[http://ubuntuforums.org/showthread.php?p=2462150#post2462150](http://ubuntuforums.org/showthread.php?p=2462150#post2462150)

Cisco has a Redhat version, but, as you might have seen in the previous thread link - it's not weeded out yet:

[http://www.checkpoint.com/downloads/quicklinks/eula_sr.html](http://www.checkpoint.com/downloads/quicklinks/eula_sr.html)

---

### Post by trinaryouroboros on 2007-07-09
My apologies, you meant to develop in Flash. The only thing I've been able to turn up, and I haven't really tried it myself, is something similar to the Adobe Photoshop CS2 workaround. Someone wrote a how-to, albeit it's a bit old, it should still work for Feisty I presume:

[http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper](http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper)

---

### Post by venoom27 on 2007-07-09
I have tried the crack for over a day and the Macromedia apps will not work. The splash screen comes up and then it fades away. I have looked all over the Wine page and repeated the crack a number of times still with no luck.

---

### Post by trinaryouroboros on 2007-07-09
What's the terminal output as it crashes?

---

### Post by venoom27 on 2007-07-11
Sorry but I had to reinstall my OS because I read on a Blog that changing my depth rate in the x config file would work but it crashed the system, so I will get to reinstalling those apps later. 
Another question until then how can I get permission to write stuff to a mounted drive?
Also I am trying to share a folder with another computer through sharing but it keeps on asking for a login and password and I have tried everything and it will not work. Got any ideas of they might be??

---

### Post by randytuggle on 2007-07-11
I would install a copy of VMWARE Server to do the Flash MX development - of course, you'd have to install Windows as a virtual OS on VMWARE Server. I don't think you'll have any real luck getting any Macromedia apps to run up to speed with Wine.

---

### Post by venoom27 on 2007-07-11
I got t testing Flash and this is what it gives me.


john@john:~$ wine '/home/john/.wine/drive_c/Program Files/Macromedia/Flash 8/Flash.exe' 
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFileInfoW pidl is null!
fixme:wintab32:WTInfoW (0, 0, (nil)): stub
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFolderPathW Failed to create directory L"Y:\\Desktop".
err:shell:SHGetFileInfoW pidl is null!
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:storage:StgCreateDocfile Transacted mode not implemented.
fixme:imm:ImmSetCandidateWindow (0x162510, 0x33bec0): stub
fixme:imm:ImmReleaseContext (0x4009e, 0x162510): stub
fixme:imm:ImmReleaseContext (0x4009e, 0x162510): stub
wine: Unhandled page fault on read access to 0x000007e0 at address 0x7b850686 (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x000007e0 in 32-bit code (0x7b850686).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b850686 ESP:0033e520 EBP:0033e588 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000001 EBX:7b8ad908 ECX:ffffffff EDX:000007e0
 ESI:00000000 EDI:00000073
Stack dump:
0x0033e520:  00000073 01c90000 01cb6fe0 00000000
0x0033e530:  00000000 00000000 00000028 0000010a
0x0033e540:  ffffffec 00000000 00000000 00000001
0x0033e550:  00000001 00000000 00000000 00000000
0x0033e560:  00000000 0033e914 01ec1118 7bc29ba1
0x0033e570:  00000128 0033e824 00000001 7b8ad908
Backtrace:
=>1 0x7b850686 INSTR_EmulateInstruction+0x66() in kernel32 (0x0033e588)
  2 0x7b8519b4 INSTR_vectored_handler+0x64() in kernel32 (0x0033e5a8)
  3 0x7bc308c3 in ntdll (+0x208c3) (0x0033e618)
  4 0x7bc30d49 __regs_RtlRaiseException+0x29() in ntdll (0x0033e688)
  5 0x7bc583bc in ntdll (+0x483bc) (0x0033e6a8)
  6 0xdeadbabe (0x00000000)
0x7b850686 INSTR_EmulateInstruction+0x66 in kernel32: movzbl    0x0(%esi,%edx,1),%eax
Modules:
Module  Address                 Debug info      Name (121 modules)
PE      3c0000-3c8000   Deferred        emlaunch
PE      3e0000-3e7000   Deferred        flfile
PE      400000-154d000  Deferred        flash
PE      1c90000-2052000 Deferred        flashresources
PE      2060000-2163000 Deferred        mfc71
PE      5170000-5272000 Deferred        mfc71u
PE      10000000-1022f000       Deferred        flash_8_video_extension
PE      12000000-121ae000       Deferred        xerces-c_2_6
PE      13000000-13191000       Deferred        mmxptresources
PE      30000000-30256000       Deferred        authplay
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
ELF     7c485000-7c4a4000       Deferred        wintab32<elf>
  \-PE  7c490000-7c4a4000       \               wintab32
ELF     7c70a000-7c72a000       Deferred        mlang<elf>
  \-PE  7c710000-7c72a000       \               mlang
ELF     7c72a000-7c779000       Deferred        crypt32<elf>
  \-PE  7c730000-7c779000       \               crypt32
ELF     7c779000-7c793000       Deferred        wsock32<elf>
  \-PE  7c780000-7c793000       \               wsock32
ELF     7c793000-7c7a8000       Deferred        midimap<elf>
  \-PE  7c7a0000-7c7a8000       \               midimap
ELF     7c7a8000-7c7c0000       Deferred        msacm32<elf>
  \-PE  7c7b0000-7c7c0000       \               msacm32
ELF     7c7c0000-7c7fc000       Deferred        wineoss<elf>
  \-PE  7c7d0000-7c7fc000       \               wineoss
ELF     7c7fc000-7c84d000       Deferred        libgcrypt.so.11
ELF     7c84d000-7c862000       Deferred        libtasn1.so.3
ELF     7cd72000-7cd76000       Deferred        libgpg-error.so.0
ELF     7cd76000-7cda4000       Deferred        libcrypt.so.1
ELF     7cdaf000-7ce1f000       Deferred        libgnutls.so.13
ELF     7ce1f000-7ce50000       Deferred        libcups.so.2
ELF     7ce69000-7ce9b000       Deferred        uxtheme<elf>
  \-PE  7ce70000-7ce9b000       \               uxtheme
ELF     7ce9d000-7cea2000       Deferred        libxfixes.so.3
ELF     7cea2000-7ceab000       Deferred        libxcursor.so.1
ELF     7ceab000-7ceb1000       Deferred        libxrandr.so.2
ELF     7ceb1000-7ceb9000       Deferred        libxrender.so.1
ELF     7ceb9000-7cebc000       Deferred        libxinerama.so.1
ELF     7debc000-7e112000       Deferred        i915_dri.so
ELF     7e112000-7e11b000       Deferred        libdrm.so.2
ELF     7e11b000-7e17b000       Deferred        libgl.so.1
ELF     7e17b000-7e180000       Deferred        libxdmcp.so.6
ELF     7e180000-7e183000       Deferred        libxau.so.6
ELF     7e183000-7e274000       Deferred        libx11.so.6
ELF     7e274000-7e282000       Deferred        libxext.so.6
ELF     7e282000-7e287000       Deferred        libxxf86vm.so.1
ELF     7e287000-7e29f000       Deferred        libice.so.6
ELF     7e29f000-7e2a8000       Deferred        libsm.so.6
ELF     7e2a8000-7e336000       Deferred        winex11<elf>
  \-PE  7e2c0000-7e336000       \               winex11
ELF     7e3af000-7e3cf000       Deferred        libexpat.so.1
ELF     7e3cf000-7e3fa000       Deferred        libfontconfig.so.1
ELF     7e3fa000-7e40e000       Deferred        libz.so.1
ELF     7e40e000-7e479000       Deferred        libfreetype.so.6
ELF     7e479000-7e49b000       Deferred        oledlg<elf>
  \-PE  7e480000-7e49b000       \               oledlg
ELF     7e49b000-7e4ba000       Deferred        mpr<elf>
  \-PE  7e4a0000-7e4ba000       \               mpr
ELF     7e4ba000-7e502000       Deferred        wininet<elf>
  \-PE  7e4c0000-7e502000       \               wininet
ELF     7e502000-7e52f000       Deferred        ws2_32<elf>
  \-PE  7e510000-7e52f000       \               ws2_32
ELF     7e52f000-7e5ca000       Deferred        oleaut32<elf>
  \-PE  7e540000-7e5ca000       \               oleaut32
ELF     7e5ca000-7e5de000       Deferred        msimg32<elf>
  \-PE  7e5d0000-7e5de000       \               msimg32
ELF     7e5de000-7e5fb000       Deferred        imm32<elf>
  \-PE  7e5f0000-7e5fb000       \               imm32
ELF     7e5fb000-7e610000       Deferred        psapi<elf>
  \-PE  7e600000-7e610000       \               psapi
ELF     7e610000-7e637000       Deferred        msvfw32<elf>
  \-PE  7e620000-7e637000       \               msvfw32
ELF     7e637000-7e65d000       Deferred        msacm32<elf>
  \-PE  7e640000-7e65d000       \               msacm32
ELF     7e65d000-7e697000       Deferred        avifil32<elf>
  \-PE  7e660000-7e697000       \               avifil32
ELF     7e697000-7e726000       Deferred        winmm<elf>
  \-PE  7e6a0000-7e726000       \               winmm
ELF     7e726000-7e73a000       Deferred        lz32<elf>
  \-PE  7e730000-7e73a000       \               lz32
ELF     7e73a000-7e753000       Deferred        version<elf>
  \-PE  7e740000-7e753000       \               version
ELF     7e753000-7e786000       Deferred        winspool<elf>
  \-PE  7e760000-7e786000       \               winspool
ELF     7e786000-7e826000       Deferred        comdlg32<elf>
  \-PE  7e790000-7e826000       \               comdlg32
ELF     7e826000-7e8e2000       Deferred        comctl32<elf>
  \-PE  7e830000-7e8e2000       \               comctl32
ELF     7e8e2000-7e8f5000       Deferred        libresolv.so.2
ELF     7e8f5000-7e913000       Deferred        iphlpapi<elf>
  \-PE  7e900000-7e913000       \               iphlpapi
ELF     7e913000-7e968000       Deferred        rpcrt4<elf>
  \-PE  7e920000-7e968000       \               rpcrt4
ELF     7e968000-7eaa4000       Deferred        user32<elf>
  \-PE  7e980000-7eaa4000       \               user32
ELF     7eaa4000-7eb3e000       Deferred        ole32<elf>
  \-PE  7eab0000-7eb3e000       \               ole32
ELF     7eb3e000-7eb97000       Deferred        shlwapi<elf>
  \-PE  7eb50000-7eb97000       \               shlwapi
ELF     7eb97000-7ec8c000       Deferred        shell32<elf>
  \-PE  7ebb0000-7ec8c000       \               shell32
ELF     7ec8c000-7ec98000       Deferred        libgcc_s.so.1
ELF     7ed8d000-7ee4a000       Deferred        gdi32<elf>
  \-PE  7eda0000-7ee4a000       \               gdi32
ELF     7ee4a000-7ee90000       Deferred        advapi32<elf>
  \-PE  7ee60000-7ee90000       \               advapi32
ELF     7efa2000-7efad000       Deferred        libnss_files.so.2
ELF     7efad000-7efb7000       Deferred        libnss_nis.so.2
ELF     7efb7000-7efce000       Deferred        libnsl.so.1
ELF     7efce000-7eff5000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d05000-b7d09000       Deferred        libdl.so.2
ELF     b7d09000-b7e4a000       Deferred        libc.so.6
ELF     b7e4b000-b7e62000       Deferred        libpthread.so.0
ELF     b7e6d000-b7f7e000       Deferred        libwine.so.1
ELF     b7f80000-b7f9b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000016 (D) C:\Program Files\Macromedia\Flash 8\Flash.exe
        0000002c    0
        00000025    0
        0000001b   15
        00000019    0 <==
00000010 
        00000014    1
        00000013    1
        00000012    0
        00000011    0
0000000a 
        0000000c    0
        0000000b

---

### Post by trinaryouroboros on 2007-07-11
The latter debugging portion is important, but, should be looked at by a wine developer on:

[http://www.winehq.com/]("http://www.winehq.com/")

The beginning portion looks like there's either permissions assignment issues, or something messed up in winecfg's folder assignments (like "/" folder assigned instead of /home/john/.wine/drive_c/Documents and Settings)

Considering this is a completly reinstalled operating system, I'm presuming you have the latest and greatest Wine version?

Sidenote: Try using alsa-oss instead.

For alsa-oss do the following:

```
sudo apt-get install alsa-oss
```

Then run flash.exe by typing:

```
aoss wine /home/john/.wine/drive_c/Program\ Files/Macromedia/Flash\ 8/Flash.exe
```

See what happens, can't hurt.

---

### Post by Tomosaur on 2007-07-11
To be perfectly honest, you may wish to just find an alternative. There are a few projects available which work natively on Linux, which allow you to produce Flash media. However, I'm not aware whether there are any graphical IDEs available to do it. The one I've tried, called HaXe (do a google search for it), behaves like an ordinary code compiler. You write all of the code yourself (with the help of the normal Flash reference docs from Adobe, if you need them), in an ordinary text file, then use the HaXe compiler to ceate the .swf. There are a few tutorials on the HaXe website for you to try out. You can use stuff like Gimp to create the images and stuff you'll need, and general audio production stuff if you need to create your own sound files.

Have fun!

---

### Post by trinaryouroboros on 2007-07-11
> **randytuggle said:**
> I would install a copy of VMWARE Server to do the Flash MX development - of course, you'd have to install Windows as a virtual OS on VMWARE Server. I don't think you'll have any real luck getting any Macromedia apps to run up to speed with Wine.

For the most part, I agree. VMWARE is the way to go for the most troublesome apps, but, if you have the time to troubleshoot - it will always help to get things more compatible for linux in the long run.

---

### Post by trinaryouroboros on 2007-07-11
> **Tomosaur said:**
> To be perfectly honest, you may wish to just find an alternative. There are a few projects available which work natively on Linux, which allow you to produce Flash media. However, I'm not aware whether there are any graphical IDEs available to do it. 

I haven't found any great graphical solutions myself to Flash, this might be a keystone, too, considering most of the linux community is into some form of development...

Here's some other stuff you can check out:

[http://ktoon.toonka.com/]("http://ktoon.toonka.com/")

[http://linuxappfinder.com/package/swftools]("http://linuxappfinder.com/package/swftools")

---

### Post by venoom27 on 2007-07-11
Thanks but I still can't get it to work so I installed Virtual Machine to run the apps.

---

