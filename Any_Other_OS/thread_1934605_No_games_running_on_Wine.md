---
title: "No games running on Wine"
date: 2012-03-02
forum: Any Other OS
---

### Post by Mike Loubet on 2012-03-02
Hi there,

I've got a box where I can't get any games to run under Wine even though they work fine on my laptop.

Are there any generic things I can do to make them work?

Got the latest Wine (1.4-rc4 I beleive), proprietary Nvidia drivers on the xorg-edgers PPA and followed instructions on winehq for each game... Also using Mint LXDE 11.

Thanks

---

### Post by nd456 on 2012-03-02
I would recommend using playonlinux... They have a great database for games and is virtually no works to install; however, on multi monitor computers it can get tricky for some games...

---

### Post by oldos2er on 2012-03-02
Thread moved to Wine.

---

### Post by Mike Loubet on 2012-03-03
I have used playonlinux before (some time ago actually), I downloaded it and like some of the new features, it simplifies the process of installing/playing games on Wine.

However, the games I want to play (Civ5 and Victoria II) aren't on the database, So all playonlinux really does is make the whole prefix creation and DLL installation process easier.

Even with the improved config, I still can't get anything to run properly. Things like installers and loading screens work but then when it reaches the main menus of the games, they either hang on a black screen or simply close down...

This leads me to believe that it's a 3d acceleration problem or some incompatibility with my Nvidia card/drivers and Wine...

---

### Post by nd456 on 2012-03-03
> **Mike Loubet said:**
> I have used playonlinux before (some time ago actually), I downloaded it and like some of the new features, it simplifies the process of installing/playing games on Wine.

However, the games I want to play (Civ5 and Victoria II) aren't on the database, So all playonlinux really does is make the whole prefix creation and DLL installation process easier.

Even with the improved config, I still can't get anything to run properly. Things like installers and loading screens work but then when it reaches the main menus of the games, they either hang on a black screen or simply close down...

This leads me to believe that it's a 3d acceleration problem or some incompatibility with my Nvidia card/drivers and Wine...
I see...
This is when wine becomes a pain in the ***

---

### Post by cwwilson721 on 2012-03-04
You DID check the winehq database, right?

---

### Post by Mike Loubet on 2012-03-06
> **nd456 said:**
> I see...
This is when wine becomes a pain in the ***

Yup. All logical sense says it should work.. But for some annoying reason it doesn't.

> **cwwilson721 said:**
> You DID check the winehq database, right?

First thing I did. I've had these games running on my laptop, but it only has a small SSD drive so I want to move games off that onto the desktop but doesn't really work. I get the loading screen for one of the games then it crashes, which makes me think it has something to do with the graphics card or wine not detecting it properly (no idea how to fix that though).

I have gone on regedit and told wine that my graphics card is 512mb but doesn't make a difference.

---

### Post by Mike Loubet on 2012-03-06
Here's the debug:

```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0097690d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0097690d ESP:0033f36c EBP:00b91bc0 EFLAGS:00210287(  R- --  I S - -P-C)
 EAX:00000000 EBX:00000000 ECX:014ec2f8 EDX:00000000
 ESI:0033f39c EDI:00000010
Stack dump:
0x0033f36c:  00000010 0033f760 0033f864 01968a40
0x0033f37c:  00000020 78645c2e 6973756d 70632e63
0x0033f38c:  7bc30070 0000000d 0000000f 014ec0b8
0x0033f39c:  00beb3b0 00b96400 01944a98 00000000
0x0033f3ac:  00000000 0033f3a8 0033f3ac 00000000
0x0033f3bc:  00000000 0033f3b8 0033f3bc 00000000
Backtrace:
=>0 0x0097690d in v2game (+0x57690d) (0x00b91bc0)
  1 0x00c08e44 in v2game (+0x808e43) (0x004a1370)
0x0097690d: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (80 modules)
PE	  340000-  346000	Deferred        lua51
PE	  350000-  379000	Deferred        lua5.1
PE	  380000-  393000	Deferred        zlib1
PE	  400000- 1153000	Export          v2game
PE	10000000-1041a000	Deferred        d3dx9_41
ELF	20000000-20004000	Deferred        libnvidia-tls.so.295.20
ELF	3e231000-3fe60000	Deferred        libnvidia-glcore.so.295.20
PE	51080000-510e1000	Deferred        dsound
ELF	68000000-6801e000	Deferred        ld-linux.so.2
ELF	6801e000-6815f000	Dwarf           libwine.so.1
ELF	6815f000-68178000	Deferred        libpthread.so.0
ELF	68178000-682d9000	Deferred        libc.so.6
ELF	682d9000-682dd000	Deferred        libdl.so.2
ELF	682dd000-682e5000	Deferred        libnss_compat.so.2
ELF	682e5000-682fc000	Deferred        libnsl.so.1
ELF	682fc000-68307000	Deferred        libnss_nis.so.2
ELF	68307000-683c4000	Deferred        gdi32<elf>
  \-PE	68310000-683c4000	\               gdi32
ELF	683c4000-68424000	Deferred        advapi32<elf>
  \-PE	683d0000-68424000	\               advapi32
ELF	68424000-68564000	Deferred        user32<elf>
  \-PE	68440000-68564000	\               user32
ELF	68564000-6857d000	Deferred        version<elf>
  \-PE	68570000-6857d000	\               version
ELF	6857d000-68591000	Deferred        psapi<elf>
  \-PE	68580000-68591000	\               psapi
ELF	68591000-685c9000	Deferred        d3d9<elf>
  \-PE	685a0000-685c9000	\               d3d9
ELF	685c9000-6863e000	Deferred        rpcrt4<elf>
  \-PE	685d0000-6863e000	\               rpcrt4
ELF	6863e000-686eb000	Deferred        winmm<elf>
  \-PE	68650000-686eb000	\               winmm
ELF	686eb000-68713000	Deferred        msacm32<elf>
  \-PE	686f0000-68713000	\               msacm32
ELF	68713000-68745000	Deferred        ws2_32<elf>
  \-PE	68720000-68745000	\               ws2_32
ELF	68745000-687ad000	Deferred        ddraw<elf>
  \-PE	68750000-687ad000	\               ddraw
ELF	687ad000-68833000	Deferred        libfreetype.so.6
ELF	68833000-68848000	Deferred        libz.so.1
ELF	68848000-688dc000	Deferred        winex11<elf>
  \-PE	68850000-688dc000	\               winex11
ELF	688dc000-688e4000	Deferred        libsm.so.6
ELF	688e4000-688fc000	Deferred        libice.so.6
ELF	688fc000-68a17000	Deferred        libx11.so.6
ELF	68a17000-68a1c000	Deferred        libuuid.so.1
ELF	68a1c000-68a35000	Deferred        libxcb.so.1
ELF	68a35000-68a39000	Deferred        libxau.so.6
ELF	68a39000-68a3f000	Deferred        libxdmcp.so.6
ELF	68a3f000-68a43000	Deferred        libxinerama.so.1
ELF	68a43000-68a49000	Deferred        libxxf86vm.so.1
ELF	68a49000-68a53000	Deferred        libxrender.so.1
ELF	68a53000-68a82000	Deferred        libfontconfig.so.1
ELF	68a82000-68aac000	Deferred        libexpat.so.1
ELF	68aac000-68ab6000	Deferred        libxcursor.so.1
ELF	6a11f000-6a141000	Deferred        imm32<elf>
  \-PE	6a130000-6a141000	\               imm32
ELF	6f364000-6f36c000	Deferred        libxrandr.so.2
ELF	703c3000-703c9000	Deferred        libxfixes.so.3
ELF	70b75000-70c7b000	Deferred        ole32<elf>
  \-PE	70b90000-70c7b000	\               ole32
PE	72880000-72890000	Deferred        vcomp
ELF	741c0000-742f4000	Deferred        wined3d<elf>
  \-PE	741d0000-742f4000	\               wined3d
ELF	7561d000-75629000	Deferred        libnss_files.so.2
ELF	75b49000-75b4d000	Deferred        libxcomposite.so.1
ELF	75c14000-75ca1000	Deferred        msvcrt<elf>
  \-PE	75c30000-75ca1000	\               msvcrt
ELF	76e3f000-76e4e000	Deferred        libxi.so.6
ELF	7723e000-7724d000	Deferred        libxext.so.6
ELF	77c66000-77c8c000	Deferred        libm.so.6
PE	78130000-781cb000	Deferred        msvcr80
ELF	7a33b000-7a413000	Deferred        libgl.so.1
ELF	7a5f9000-7a615000	Deferred        dinput8<elf>
  \-PE	7a600000-7a615000	\               dinput8
ELF	7b800000-7ba13000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba13000	\               kernel32
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Paradox Interactive\Victoria 2\v2game.exe
	00000009    0 <==
0000000e services.exe
	00000032    0
	0000001f    0
	0000001e    0
	0000001c    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	00000021    0
	00000018    0
	00000014    0
	00000013    0
00000019 plugplay.exe
	00000020    0
	0000001b    0
	0000001a    0
00000024 explorer.exe
	00000025    0
System information:
    Wine build: wine-1.4-rc6
    Platform: i386
    Host system: Linux
    Host version: 2.6.38-13-generic
```

---

### Post by Mike Loubet on 2012-03-06
OK, I'm 99% sure it's the graphics getting this:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x33ea14,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:wgl:internal_SetPixelFormat Invalid operation on root_window
```

Can't copy text from the POL debug reports for some reason so I've copied some of the text the best I can.

---

### Post by thatguruguy on 2012-03-07
Have you considered posting this question on the LinuxMint forums?  They may do a better job of helping you.

---

### Post by Perfect Storm on 2012-03-07
Moved to Other OS/Distro Talk.

---

### Post by Mike Loubet on 2012-03-08
Because it's an issue with graphics card drivers, the distribution is irrelevant. I'm only using Mint on this box because I wanted to see what it was like (conclusion: Lubuntu's slightly better looking identical twin).

I really think having the thread in the Wine section is more appropriate... I mean, this is a wine/nvidia issue not a Linux Mint issue.

If I lie and say I'm using Lubuntu will people help me? It really doesn't affect my issue. I use these forums because they have always been helpful to me, whatever flavour of Ubuntu I use.

---

### Post by Mike Loubet on 2012-03-11
OK, since this has been moved to a non-relevant part of the forums, I'm bumping and either hoping for a helpful response or to have this moved back to the Wine section or Nvidia...

---

### Post by Mike Loubet on 2012-03-13
OK, so I solved the problem by doing:

```
winetricks physx
```

This should help people having trouble with nvidia cards/drivers and wine.

Stumbled across it here:

[http://www.unixmen.com/install-and-configure-wine-to-play-latest-windows-games-in-linux-ubuntu-linuxmint-fedora/]("http://www.unixmen.com/install-and-configure-wine-to-play-latest-windows-games-in-linux-ubuntu-linuxmint-fedora/")

In the long time I have been looking to solve this problem, nowhere did it suggest this.

Seems that the fact I was using mint in this case was irrelevant.

---

