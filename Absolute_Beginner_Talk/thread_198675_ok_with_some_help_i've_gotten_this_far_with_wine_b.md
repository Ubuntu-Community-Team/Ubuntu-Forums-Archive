---
title: "ok with some help i've gotten this far with wine but..."
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-17
I am stuck here is a review of what i have done so far

drag the exe from windows to linux and launch wine.
heres the section i am stuck at i was told it needed microsoft visual basic runtime libraries so i downloaded them and ran it almost had it installed but got this
> maddbaron@ubuntu:~$ wine /home/maddbaron/exe/vc6redistsetup_enu.exe
wine: Unhandled page fault on write access to 0x0440002e at address 0x7ff96505 ( thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x0440002e in 32-bit code (0x 7ff96505).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
EIP:7ff96505 ESP:7fb9e118 EBP:7fb9e150 EFLAGS:00210202( - 00 - -RI1)
EAX:7c1750e0 EBX:7ffd5824 ECX:0440002a EDX:7fd39ed0
ESI:7fd39ec8 EDI:7fd39ea8
Stack dump:
0x7fb9e118: 00000000 7fb9e190 7fd39ec0 00000000
0x7fb9e128: 7ff8fa1a 00000018 00000020 7fce0000
0x7fb9e138: 7fd39eb8 7fd39eb0 00000010 7ffd5824
0x7fb9e148: 7fd39ea8 00000020 7fb9e1a0 7ff96ce1
0x7fb9e158: 7fb9e1d0 7fce0000 00000004 00000000
0x7fb9e168: 00000000 00000000 00000000 7ff95887
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x7ff96505 in ntdll (+0x26505) (0x7ff96505)
2 0x7ff96ce1 in ntdll (+0x26ce1) (0x7ff96ce1)
3 0x7ff96f38 RtlFreeHeap+0xf9 in ntdll (0x7ff96f3
4 0x7f2d87f3 in shell32 (+0x87f3) (0x7f2d87f3)
5 0x7f86094a WINPROC_wrapper+0x1a in user32 (0x7f86094a)
6 0x7f86106b WINPROC_wrapper+0x73b in user32 (0x7f86106b)
7 0x7f8641b0 WINPROC_CallProcAtoW+0x35a in user32 (0x7f8641b0)
8 0x7f864d6a WINPROC_CallDlgProcA+0xba in user32 (0x7f864d6a)
9 0x7f7f9b99 DefDlgProcA+0x84 in user32 (0x7f7f9b99)
10 0x7f86094a WINPROC_wrapper+0x1a in user32 (0x7f86094a)
11 0x7f862853 in user32 (+0xa2853) (0x7f862853)
12 0x7f864e6a CallWindowProcA+0x57 in user32 (0x7f864e6a)
13 0x7f82fc37 in user32 (+0x6fc37) (0x7f82fc37)
14 0x7f833450 SendMessageTimeoutA+0x1eb in user32 (0x7f833450)
15 0x7f83350b SendMessageA+0x50 in user32 (0x7f83350b)
err:dbghelpe_load_dbg_file -Unable to peruse .DBG file exe\wextract.dbg ("\xff ")
16 0x01003bb5 in vc6redistsetup_enu (+0x3bb5) (0x01003bb5)
17 0x7f2d8770 in shell32 (+0x8770) (0x7f2d8770)
18 0x7f86094a WINPROC_wrapper+0x1a in user32 (0x7f86094a)
19 0x7f86106b WINPROC_wrapper+0x73b in user32 (0x7f86106b)
20 0x7f865e19 WINPROC_CallDlgProcW+0x57 in user32 (0x7f865e19)
21 0x7f7f99f7 DefDlgProcW+0x84 in user32 (0x7f7f99f7)
22 0x7f86094a WINPROC_wrapper+0x1a in user32 (0x7f86094a)
23 0x7f862853 in user32 (+0xa2853) (0x7f862853)
24 0x7f865f0c CallWindowProcW+0x57 in user32 (0x7f865f0c)
25 0x7f82fcc6 in user32 (+0x6fcc6) (0x7f82fcc6)
26 0x7f8336d0 SendMessageTimeoutW+0x191 in user32 (0x7f8336d0)
27 0x7f83372f SendMessageW+0x50 in user32 (0x7f83372f)
28 0x7f7ffef0 in user32 (+0x3fef0) (0x7f7ffef0)
29 0x7f800a5a DialogBoxParamW+0x7f in user32 (0x7f800a5a)
30 0x7f2d7b49 SHBrowseForFolderW+0x71 in shell32 (0x7f2d7b49)
31 0x7f2d7cb5 SHBrowseForFolderA+0x14b in shell32 (0x7f2d7cb5)
32 0x01003c8d in vc6redistsetup_enu (+0x3c8d) (0x01003c8d)
33 0x01002e2e in vc6redistsetup_enu (+0x2e2e) (0x01002e2e)
34 0x7f86094a WINPROC_wrapper+0x1a in user32 (0x7f86094a)
35 0x7f86106b WINPROC_wrapper+0x73b in user32 (0x7f86106b)
36 0x7f86551b in user32 (+0xa551b) (0x7f86551b)
37 0x7f865e70 WINPROC_CallDlgProcW+0xae in user32 (0x7f865e70)
38 0x7f7f99f7 DefDlgProcW+0x84 in user32 (0x7f7f99f7)
39 0x7f86094a WINPROC_wrapper+0x1a in user32 (0x7f86094a)
40 0x7f862853 in user32 (+0xa2853) (0x7f862853)
41 0x7f865f0c CallWindowProcW+0x57 in user32 (0x7f865f0c)
42 0x7f82fcc6 in user32 (+0x6fcc6) (0x7f82fcc6)
43 0x7f8336d0 SendMessageTimeoutW+0x191 in user32 (0x7f8336d0)
44 0x7f83372f SendMessageW+0x50 in user32 (0x7f83372f)
45 0x7f7e180b in user32 (+0x2180b) (0x7f7e180b)
46 0x7f7e22bb in user32 (+0x222bb) (0x7f7e22bb)
47 0x7f86094a WINPROC_wrapper+0x1a in user32 (0x7f86094a)
48 0x7f862853 in user32 (+0xa2853) (0x7f862853)
49 0x7f865f0c CallWindowProcW+0x57 in user32 (0x7f865f0c)
50 0x7f83005c DispatchMessageW+0x169 in user32 (0x7f83005c)
51 0x7f7fe37b IsDialogMessageW+0xfb in user32 (0x7f7fe37b)
52 0x7f7fec90 DIALOG_DoDialogBox+0x13b in user32 (0x7f7fec90)
53 0x7f800938 DialogBoxIndirectParamAorW+0x5a in user32 (0x7f80093
54 0x7f8009d1 DialogBoxIndirectParamA+0x41 in user32 (0x7f8009d1)
55 0x01005a79 in vc6redistsetup_enu (+0x5a79) (0x01005a79)
56 0x01004fde in vc6redistsetup_enu (+0x4fde) (0x01004fde)
57 0x01002b9a in vc6redistsetup_enu (+0x2b9a) (0x01002b9a)
58 0x7fc4b94f in kernel32 (+0x4b94f) (0x7fc4b94f)
59 0xb7f2e2e3 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f2e2e3)
0x7ff96505: movl %eax,0x4(%ecx)
Modules:
Module Address Debug info Name (63 modules)
PE 0x01000000-011c2000 Export vc6redistsetup_enu
ELF 0x7bf00000-7bf03000 Deferred <wine-loader>
ELF 0x7f14c000-7f16b000 Deferred iphlpapi<elf>
\-PE 0x7f150000-7f16b000 \ iphlpapi
ELF 0x7f16b000-7f1be000 Deferred rpcrt4<elf>
\-PE 0x7f180000-7f1be000 \ rpcrt4
ELF 0x7f1be000-7f253000 Deferred ole32<elf>
\-PE 0x7f1d0000-7f253000 \ ole32
ELF 0x7f253000-7f2af000 Deferred shlwapi<elf>
\-PE 0x7f270000-7f2af000 \ shlwapi
ELF 0x7f2af000-7f38c000 Export shell32<elf>
\-PE 0x7f2d0000-7f38c000 \ shell32
ELF 0x7f39b000-7f3cc000 Deferred uxtheme<elf>
\-PE 0x7f3a0000-7f3cc000 \ uxtheme
ELF 0x7f3cc000-7f3d5000 Deferred libxcursor.so.1
ELF 0x7f3d5000-7f3f1000 Deferred imm32<elf>
\-PE 0x7f3e0000-7f3f1000 \ imm32
ELF 0x7f3f1000-7f3f9000 Deferred libxrender.so.1
ELF 0x7f3f9000-7f45f000 Deferred libgl.so.1
ELF 0x7f45f000-7f545000 Deferred libx11.so.6
ELF 0x7f545000-7f552000 Deferred libxext.so.6
ELF 0x7f552000-7f56a000 Deferred libice.so.6
ELF 0x7f56a000-7f5ed000 Deferred winex11<elf>
\-PE 0x7f580000-7f5ed000 \ winex11
ELF 0x7f5ed000-7f60c000 Deferred libexpat.so.1
ELF 0x7f60c000-7f63a000 Deferred libfontconfig.so.1
ELF 0x7f63a000-7f64e000 Deferred libz.so.1
ELF 0x7f64e000-7f6b7000 Deferred libfreetype.so.6
ELF 0x7f6b7000-7f6cb000 Deferred lz32<elf>
\-PE 0x7f6c0000-7f6cb000 \ lz32
ELF 0x7f6cb000-7f6e4000 Deferred version<elf>
\-PE 0x7f6d0000-7f6e4000 \ version
ELF 0x7f6e4000-7f7a6000 Deferred comctl32<elf>
\-PE 0x7f6f0000-7f7a6000 \ comctl32
ELF 0x7f7a6000-7f8d9000 Export user32<elf>
\-PE 0x7f7c0000-7f8d9000 \ user32
ELF 0x7f9ae000-7fa5f000 Deferred gdi32<elf>
\-PE 0x7f9c0000-7fa5f000 \ gdi32
ELF 0x7fa5f000-7faa0000 Deferred advapi32<elf>
\-PE 0x7fa70000-7faa0000 \ advapi32
ELF 0x7fba1000-7fba5000 Deferred libxfixes.so.3
ELF 0x7fba5000-7fbac000 Deferred libdrm.so.2
ELF 0x7fbdf000-7fce0000 Export kernel32<elf>
\-PE 0x7fc00000-7fce0000 \ kernel32
ELF 0x7fdf3000-7fdf8000 Deferred libxxf86vm.so.1
ELF 0x7fdf8000-7fe00000 Deferred libsm.so.6
ELF 0x7fe00000-7fe0a000 Deferred libnss_files.so.2
ELF 0x7fe0a000-7fe13000 Deferred libnss_nis.so.2
ELF 0x7fe13000-7fe28000 Deferred libnsl.so.1
ELF 0x7fe28000-7fe31000 Deferred libnss_compat.so.2
ELF 0x7fe31000-7fe36000 Deferred libxxf86dga.so.1
ELF 0x7fe36000-7fe40000 Deferred libgcc_s.so.1
ELF 0x7fe41000-7fe44000 Deferred libxrandr.so.2
ELF 0x7fe48000-7fe6a000 Deferred libm.so.6
ELF 0x7fe6a000-7ff62000 Deferred libwine_unicode.so.1
ELF 0x7ff62000-7ffe0000 Export ntdll<elf>
\-PE 0x7ff70000-7ffe0000 \ ntdll
ELF 0xb7dd1000-b7dd4000 Deferred libdl.so.2
ELF 0xb7dd4000-b7f03000 Deferred libc.so.6
ELF 0xb7f03000-b7f15000 Deferred libpthread.so.0
ELF 0xb7f16000-b7f19000 Deferred libxau.so.6
ELF 0xb7f29000-b7f43000 Export libwine.so.1
ELF 0xb7f46000-b7f5c000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000a
0000000b 0
00000008 (D) J:\exe\vc6redistsetup_enu.exe
00000009 0 <==
maddbaron@ubuntu:~$ /home/maddbaron/exe/yWriter2.exe
run-detectors: unable to find an interpreter for /home/maddbaron/exe/yWriter2.exe

i was told to do this to try to fix that but it doesnt work
> $ cabextract vc6redistsetup_enu.exe
$ wine vcredist.exe

anyway to fix this? i need to install this program and 2more and i wont need windows anymore....

anyone?

---

### Post by harishg on 2006-06-17
Check this out.

[http://www.jsware.net/jsware/vblinux.php3](http://www.jsware.net/jsware/vblinux.php3)

---

