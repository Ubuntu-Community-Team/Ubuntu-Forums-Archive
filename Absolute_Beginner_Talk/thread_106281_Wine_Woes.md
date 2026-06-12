---
title: "Wine Woes"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-12-20
I installed Wine via Synaptic, but I can't get it to work. Most programs won't open at all. The one I really need, PageMaker, gets as far as the "window" (don't know what you call it: the basic PageMaker page after the splash screen) then crashes. I can post what I got in the error messages and debug script, but when I Googled that, people seem to be saying it's a Wine bug and either ignore it, or download a later version.

If I run winecfg, it tells me it's not actually going to change any files. Not that I understand what I'm supposed to change.

I'm really confused at this point.

I have a dual boot system. Wine is running under Win98 (although they tell you to change the Win version to 95 for PageMaker, which I've done) and I've tried to run Wine through Konqueror, and the command line. No joy.

Any advice for this Absolute Beginner?

---

### Post by iansyngin on 2005-12-20
yes, could someone even give a demonstration for getting windows notepad working under wine. something very simple

---

### Post by Mr. Electric Wizard on 2005-12-20
I'll give a different example, because Notepad seems to be pretty useless under linux...;) 

Use synaptic to download and install wine.
Download Picassa2 from [http://www.picasa.com]("http://www.picasa.com").
Then saved the *.exe in the /home directory.

Then ran in a terminal:
wine /home/picasa2_current.exe.

Then ran through the setup.

Easy as pie!

---

### Post by Mr. Electric Wizard on 2005-12-20
As for PageMaker, check to see if that is one of the programs that Wine works with...
Its on the WineHQ site.
I'm not sure if it'll work or not, I know Office 2000 installs but crashes really easily, and doesn't work right...
Picasa on the other hand works extremely well!

---

### Post by iansyngin on 2005-12-20
you wouldn't happen to know off hand what entries you need in sources.list to find wine. 
I only have the following:

----------------------------
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

---

### Post by iansyngin on 2005-12-20
forget that last post.
i just added universal from the synaptic repositary

---

### Post by iansyngin on 2005-12-20
once everything got installed.
i browsed to the picassa directory in /home/$USER/.wine/Program Files/Picassa2

i then ran #wine Picasa2.exe and the it produced something like this below.
am i on the right track ??

F     0x7fee6000-7fee9000     Deferred        libxrandr.so.2
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7e61000-b7e6b000     Deferred        libnss_files.so.2
ELF     0xb7e6c000-b7e6f000     Deferred        libdl.so.2
ELF     0xb7e6f000-b7f9d000     Deferred        libc.so.6
ELF     0xb7f9e000-b7fb0000     Deferred        libpthread.so.0
ELF     0xb7fb0000-b7fc9000     Export          libwine.so.1
ELF     0xb7fc9000-b7fcb000     Deferred        xlcutf8load.so.2
ELF     0xb7fcb000-b7fd4000     Deferred        libnss_nis.so.2
ELF     0xb7fd9000-b7fef000     Deferred        ld-linux.so.2

---

### Post by editrix on 2005-12-21
[QUOTE=Mr. Electric Wizard]As for PageMaker, check to see if that is one of the programs that Wine works with...[/QUOTE] Ironically, it's supposed to work very well in Wine. But winehq instructs you to install it in Wine. I suppose I can do that if I have to, but right now, nothing's working, so I don't think it's a PageMaker issue per se.

Nice to know Picassa works, but it's not what I need.

---

### Post by futz on 2005-12-21
[QUOTE=Mr. Electric Wizard]Use synaptic to download and install wine.
Download Picassa2 from [http://www.picasa.com]("http://www.picasa.com").
Then saved the *.exe in the /home directory.

Then ran in a terminal:
wine /home/picasa2_current.exe.

Then ran through the setup.

Easy as pie![/QUOTE]

Hehehe! Not so easy after all. Here's what I get when I do that:
```
futz@homer:~$ wine /home/futz/picasa2-current.exe
fixme:actctx:CreateActCtxW stub!
wine: Unhandled exception (thread 000b), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x800000ac in 32-bit code (0x701069b2).
In 32 bit mode.
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file rpcrt4.dbg ("rpcrt4.dbg")
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:701069b2 ESP:7fb1fccc EBP:7fb1fd0c EFLAGS:00010282(   - 00      - RIS1)
 EAX:0000000a EBX:00000000 ECX:80000098 EDX:7bef51d4
 ESI:80000098 EDI:00000000
Stack dump:
0x7fb1fccc:  00000068 701067e6 00000000 70101dc3
0x7fb1fcdc:  7fda0cf8 00000000 7bef51d4 6534e217
0x7fb1fcec:  0000000d 6534e1ba 7fb1fcdc 7fb1f874
0x7fb1fcfc:  7fb1ff38 7010a6dc 70146488 ffffffff
0x7fb1fd0c:  7fb1fd24 7bebf9e2 70100000 00000001
0x7fb1fd1c:  00000001 7bef51d4 7fb1fdbc 7bec075b
0200: sel=1007 base=b7f4c000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x701069b2 NdrServerMarshall+0x430 in rpcrt4 (0x7fb1fd0c)
  2 0x7bebf9e2 call_dll_entry_point+0x12 in ntdll (0x7fb1fd24)
  3 0x7bec075b in ntdll (+0x2075b) (0x7fb1fdbc)
  4 0x7bec105d in ntdll (+0x2105d) (0x7fb1fdf0)
  5 0x7bec102d in ntdll (+0x2102d) (0x7fb1fe24)
  6 0x7bec102d in ntdll (+0x2102d) (0x7fb1fe58)
  7 0x7bec3975 LdrInitializeThunk+0x382 in ntdll (0x7fb1ff20)
  8 0x7fcf8e2d in kernel32 (+0x48e2d) (0x7fb1fff4)
  9 0xb7f2ac45 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x701069b2 NdrServerMarshall+0x430 in rpcrt4: cmpl      0x14(%esi),%eax
Modules:
Module  Address                 Debug info      Name (63 modules)
PE      0x00400000-007d5000     Deferred        pay78a.tmp
PE      0x5e380000-5e3a5000     Deferred        msoss
PE      0x65340000-653d2000     Deferred        oleaut32
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x70100000-70153000     Export          rpcrt4
PE      0x702b0000-7032a000     Deferred        urlmon
PE      0x70bd0000-70c35000     Deferred        shlwapi
PE      0x71450000-714ae000     Deferred        crypt32
PE      0x71590000-7159e000     Deferred        wintrust
PE      0x78000000-78040000     Deferred        msvcrt
ELF     0x7be87000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e2b7000-7e2c0000     Deferred        libxcursor.so.1
ELF     0x7e2c0000-7e2dd000     Deferred        imm32<elf>
  \-PE  0x7e2d0000-7e2dd000     \               imm32
ELF     0x7e2dd000-7e2f9000     Deferred        ximcp.so.2
ELF     0x7e2f9000-7ea62000     Deferred        libglcore.so.1
ELF     0x7ea62000-7eae1000     Deferred        libgl.so.1
ELF     0x7eae1000-7eba1000     Deferred        libx11.so.6
ELF     0x7eba1000-7ebba000     Deferred        libice.so.6
ELF     0x7ebba000-7ec3c000     Deferred        winex11.drv<elf>
  \-PE  0x7ebd0000-7ec3c000     \               winex11.drv
ELF     0x7ec3c000-7ec5b000     Deferred        libexpat.so.1
ELF     0x7ec5b000-7ec89000     Deferred        libfontconfig.so.1
ELF     0x7ec98000-7ecac000     Deferred        libz.so.1
ELF     0x7ecac000-7ed16000     Deferred        libfreetype.so.6
ELF     0x7ed16000-7ed2a000     Deferred        lz32<elf>
  \-PE  0x7ed20000-7ed2a000     \               lz32
ELF     0x7ed2a000-7ed45000     Deferred        version<elf>
  \-PE  0x7ed30000-7ed45000     \               version
ELF     0x7ed45000-7ee04000     Deferred        comctl32<elf>
  \-PE  0x7ed50000-7ee04000     \               comctl32
ELF     0x7ee04000-7eeca000     Deferred        shell32<elf>
  \-PE  0x7ee20000-7eeca000     \               shell32
ELF     0x7eeca000-7ef0b000     Deferred        advapi32<elf>
  \-PE  0x7eee0000-7ef0b000     \               advapi32
ELF     0x7eff1000-7f8f4000     Deferred        gdi32<elf>
  \-PE  0x7f040000-7f8f4000     \               gdi32
ELF     0x7f8f4000-7fa20000     Deferred        user32<elf>
  \-PE  0x7f920000-7fa20000     \               user32
ELF     0x7fb23000-7fb30000     Deferred        libxext.so.6
ELF     0x7fb32000-7fb36000     Deferred        libxfixes.so.3
ELF     0x7fb36000-7fb3d000     Deferred        libsm.so.6
ELF     0x7fc85000-7fd90000     Export          kernel32<elf>
  \-PE  0x7fcb0000-7fd90000     \               kernel32
ELF     0x7fd91000-7fd95000     Deferred        libxdmcp.so.6
ELF     0x7fd95000-7fda0000     Deferred        libgcc_s.so.1
ELF     0x7feb0000-7feb2000     Deferred        libnvidia-tls.so.1
ELF     0x7feb2000-7febc000     Deferred        libnss_files.so.2
ELF     0x7febc000-7fed1000     Deferred        libnsl.so.1
ELF     0x7fed1000-7feda000     Deferred        libnss_compat.so.2
ELF     0x7fedd000-7fee5000     Deferred        libxrender.so.1
ELF     0x7fee5000-7fee7000     Deferred        xlcutf8load.so.2
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7de2000-b7de5000     Deferred        libdl.so.2
ELF     0xb7de5000-b7f13000     Deferred        libc.so.6
ELF     0xb7f14000-b7f26000     Deferred        libpthread.so.0
ELF     0xb7f26000-b7f3f000     Export          libwine.so.1
ELF     0xb7f40000-b7f43000     Deferred        libxau.so.6
ELF     0xb7f43000-b7f4c000     Deferred        libnss_nis.so.2
ELF     0xb7f51000-b7f67000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\windows\temp\pay78a.tmp.exe
        0000000b    0 <==
00000008
        00000009    0
WineDbg terminated on pid 0xa

```
And other programs I've attempted to install with wine do the same sort of thing. I've never gotten it to work yet.

---

### Post by aouie on 2005-12-21
The wine version in Ubuntu's universe repository is too old (0.0.2???). You should get the latest wine from < [http://winehq.com/](http://winehq.com/) >. If you follow their installation instructions on Synaptic then you will probably get some complaints from Synaptic (or if I remember correctly you couldn't set it up because of no custom repository specification support on Ubuntu). The packages are at < [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) >. The arrangement was not friendly for synaptic so I moved the packages around on my localhost to get something that would work with synaptic. The directory listing is further below. Just add the following repository to synaptic
Binary URI: [http://localhost/repos/wine/](http://localhost/repos/wine/) dist: breezy Section: main (or wherever you set it up). Install wine and winetools (it worked fine with wine 0.9.2 even though it cautions you that it was only tested with wine 0.9beta).
Follow each step on winetools till you have IE6 working. I was unable to run some other windows programs that I wanted to, but the main thing I wanted was to test some websites on IE6 and this helped accomplish that. (run ~/bin/ie6 (unless you set it up in a different location)).
Sincerely,
Aouie
PS: If someone can get wine setup done right either at Ubuntu or winehq that would be nice.
$ ls repos -R
repos:
wine

repos/wine:
binary  dists

repos/wine/binary:
libwine_0.9.2-winehq-1_all.deb      wine_0.9.2-winehq-1_i386.deb      winetools_3.0.9-winehq-1_all.deb
libwine-dev_0.9.2-winehq-1_all.deb  wine-dev_0.9.2-winehq-1_i386.deb

repos/wine/dists:
breezy

repos/wine/dists/breezy:
main

repos/wine/dists/breezy/main:
binary-i386

repos/wine/dists/breezy/main/binary-i386:
Packages.gz  Release
-------------------------------

---

### Post by scole on 2005-12-21
try going here for help [http://www.frankscorner.org/](http://www.frankscorner.org/) it is a great resource you might need dcom98.exe installed to run the program the site has a link to it. This may help.

---

### Post by futz on 2005-12-21
[QUOTE=aouie]The wine version in Ubuntu's universe repository is too old (0.0.2???). You should get the latest wine from < [http://winehq.com/](http://winehq.com/) >.[/QUOTE]
Thanks Aouie. That cured it. I did all that once before, but had troubles and uninstalled it all. Then the last time (when I last posted) I had just installed the old wine in the standard repositories. The previous time that I had the new wine, I probably just missed something in config, because this time it all went as advertised and I'm wining as we speak. :mrgreen:

Thanks for the pointers.

---

### Post by editrix on 2005-12-22
aouie, I've read your post 3 times and it sounds like you know what you're talking about. Unfortunately, I don't. I'm a real newbie. Also I'm on Hoary, and I don't know if that would make any difference.

You've gone through a lot of trouble answering, but I'm going to ask you to go through a bit more. Could you put it in a step 1, step 2 format? 

For example, I have no directory "repos" on my system. So right away, I'm stuck trying to follow your instructions.

---

### Post by editrix on 2005-12-22
I found this on the Wine Wiki: [http://wiki.jswindle.com/index.php/Debian_Debian_Based](http://wiki.jswindle.com/index.php/Debian_Debian_Based)

Installing with Debian based Distro
Detailed instructions here: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) 
1. Add the lines below to /etc/apt/sources.list
 deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 
2. Then, you can run 'apt-get update' to update APT's package information. 
3. Finally, to install Wine, do 'apt-get install wine winetools'. 
4. Configure using 'winetools' 

Frankly, it sounds too easy. And if Wine is already installed on my system, should I uninstall it, or will this overwrite everything?

---

### Post by futz on 2005-12-22
[QUOTE=editrix]Frankly, it sounds too easy. And if Wine is already installed on my system, should I uninstall it, or will this overwrite everything?[/QUOTE]
Go to [http://www.winehq.org/](http://www.winehq.org/) and look around. What you're looking for is this page [http://www.winehq.org/site/download](http://www.winehq.org/site/download) and then this page [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I don't know if new wine overwrites the old properly, so it might be a good idea to unmark it in Synaptic first and remove it completely before changing the repository and installing the new one. It probably doesn't matter, but it doesn't take long to uninstall it.

As soon as you put that repository in, Synaptic will ask you if you want to update. Do it and then scroll down to wine. The newest version will be listed, as well as winetools a couple lines down. Mark em both and hit the Apply button.

BTW: The Foxit PDF Reader (free and way faster and lighter than stupid fatty Acrobat Reader) works awesome in wine. It's just as fast as it is in windoze. You can download it at [http://www.foxitsoftware.com/pdf/rd_intro.php](http://www.foxitsoftware.com/pdf/rd_intro.php)

The exe file you download is not an installer. It's the actual executable file. Just put it somewhere safe and set up a launcher to start it with wine.

---

### Post by futz on 2005-12-22
If anybody can figure out how to get Microsoft Reader [http://www.microsoft.com/reader/downloads/pc.asp](http://www.microsoft.com/reader/downloads/pc.asp) to install with wine, I would be very very grateful. It has Installshield problems. I did try this [http://www.frankscorner.org/index.php?p=ishield](http://www.frankscorner.org/index.php?p=ishield) , but it didn't help.

I have tons of ebooks in lit format and would love to be able to read them in linux instead of windoze.

I tried to compile clit (convert lit) a couple times, but fell immediately into dependency hell and gave up.

---

### Post by gatorbrit on 2005-12-22
Related wine question:
Is it better to run an already installed windows exe file (i.e. installed in the windows partition) in wine (e..g wine /media/windows/program files/application.exe)

OR 

install the application fresh into the fake program files directory that wine set up and therefore first time run wine /blah blah/setup.exe)

then run /blah blah/application.exe 

Put another way, should I reinstall the windoze app in wine the run it rather than using the existing installed version.

Thanks!

---

### Post by editrix on 2005-12-22
futz, thanks for this. I knew it sounded too simple.

[QUOTE=futz]Go to [http://www.winehq.org/](http://www.winehq.org/) and look around. What you're looking for is this page [http://www.winehq.org/site/download](http://www.winehq.org/site/download) and then this page [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

... it doesn't take long to uninstall it.[/QUOTE]

Only about 10 minutes :-)

So, I did all that, and an hour later it's installing, but Synaptic tells me "Some of the packages could not be retrieved from the server. Do you want to continue ..." I chose Yes. 

So then, after the install finishes, I get:

W: Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.3-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.3-winehq-1_i386.deb)
  Error reading from server. Remote end closed connection

So, do I need these binaries for something? I'm reluctant to try anything in case too much screws up because they're missing. (And, as an aside, why couldn't Synaptic have been specific in what it couldn't download?)

Also, I'm on dialup, so if I don't have to download them, I'd rather not.

[/QUOTE]The exe file you download is not an installer. It's the actual executable file. Just put it somewhere safe and set up a launcher to start it with wine.[QUOTE]

I don't see an exe. Is this part of the binaries that didn't download? Where should I look for it?

---

### Post by futz on 2005-12-22
[QUOTE=editrix]So, I did all that, and an hour later it's installing, but Synaptic tells me "Some of the packages could not be retrieved from the server. Do you want to continue ..." I chose Yes.[/quote]
Ok, here's the trick. Don't choose Yes. Yes means you want to continue installing without all the files, which just won't work. 

Choose No and get back to the main synaptic screen again. Then hit Apply again. It will continue downloading whatever it couldn't get the first go. You may have to do this several times before it finishes downloading all files and installs everything.

I'm on a wireless connection on this box and often get timeouts on downloads. When I see that the download has stopped for a while, I just hit Cancel and No and Apply again. Works perfect.

> I don't see an exe. Is this part of the binaries that didn't download? Where should I look for it?
Oops, sorry. It's a zip file. When you unzip it, you get the exe file. On this page [http://www.foxitsoftware.com/pdf/rd_intro.php](http://www.foxitsoftware.com/pdf/rd_intro.php) click Download Now and get the zip. Anyway, that exe is the executable.

Sounds like you may be confusing this PDF reader file with the wine install. They're not the same thing at all. Wine is the program that lets you run some windoze programs in linux. The Foxit PDF Reader works very well under wine, but is not connected in any way.

---

### Post by Mr. Electric Wizard on 2005-12-22
That is correct about the version in the Repositories being really old.
I never had much luck with it either...
I actually installed it using the Wine Repository that they suggest on the WineHQ site.
They give instructions and everything about how to get it going on Ubuntu.
I am a happy camper.
Just wish I could get Word going 100%.
Awesome.

---

### Post by Mr. Electric Wizard on 2005-12-22
[QUOTE=editrix]I found this on the Wine Wiki: [http://wiki.jswindle.com/index.php/Debian_Debian_Based](http://wiki.jswindle.com/index.php/Debian_Debian_Based)

Installing with Debian based Distro
Detailed instructions here: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) 
1. Add the lines below to /etc/apt/sources.list
 deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 
2. Then, you can run 'apt-get update' to update APT's package information. 
3. Finally, to install Wine, do 'apt-get install wine winetools'. 
4. Configure using 'winetools' 

Frankly, it sounds too easy. And if Wine is already installed on my system, should I uninstall it, or will this overwrite everything?[/QUOTE]

I did an apt-get remove first.
I don't know if it will overwrite, but I assume it would.
I just removed first to be on the safe side.

---

### Post by editrix on 2005-12-23
Now I can't even download/install Wine.

Tried last night with Synaptic, and now this morning from the terminal. Got the same error message:

wolfgang@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  wine-doc wine-utils
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 180 not upgraded.
Need to get 13.8MB of archives.
After unpacking 55.8MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.3-winehq-1 [13.8MB]
Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.3-winehq-1
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.3-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.3-winehq-1_i386.deb)  Error reading from server. Remote end closed connection

Please, what the **** am I doing wrong?

---

