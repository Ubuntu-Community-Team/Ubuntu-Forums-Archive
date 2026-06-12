---
title: "Cvs wine/cedega configuration"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by Struck on 2005-10-01
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

4. Configuration

We need a so called fake windows. The cvscedega-script will create it if we run it the first time:

$ cvscedega

cvscedega creates a configuration (~/.cvscedega) and a fake windows directory (~/.cvscedega/c_drive). It is possible to change the directory for the fake windows e.g.

and edit the config file (~/.cvscedega/config) for your needs.

  [Drive C]
  ...

  "Path" = "/home/linux-gamers.net/windows/C"
  ...



CD-ROMS are autodetected but you configure one as follows:

 [Drive D]
 "Path" = "/media/cdrom"
 "Type" = "cdrom"
 "Label" = "CD-ROM"
 "Filesystem" = "win95"
 "Device" = "/dev/hdc"



Change "Path" and "Device" if necessary.

Configuration variables which you should change

in the [x11drv] section


; How much Video RAM does your graphic card have?
; If this option is not present, it will default set to 32MB.
"VideoRam" = "128"
; How much should Cedega attempt to store into faster AGP memory
; Set the amount of video memory to be allocated for OpenGL vertex arrays.
"AGPVertexRam" = "32"




If you have OSS change:

[WinMM]
"Drivers" = "wineoss.drv"



For Freetype font support set:

[fonts]
"Freetype" = "Y"


Computer>Search for files... I entered cvscedega*since when i type locate cvscedega on terminal as root it gives  me a whole lot of locations>.<* found 2 files one is on /home/andrea/bin and one on /home/andrea/My Downloads.

So I typed in*terminal as root* /home/andrea/bin/cvscedega and this showed up =(

root@pc12:/home/andrea # /home/andrea/bin/cvscedega

FuddFeatures:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:  cvscedega regapi <regfilename.reg>
Install .reg with regedit: cvscedega regedit [regfilename.reg]
Start winecfg:             cvscedega winecfg
Log to file:               cvscedega log <normal params>
         eg:               cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console

Cedega CVS

Usage: /home/andrea/.WineCVS/installs/cvscedega/bin/wine [options] [--] program_name [arguments]
The -- has to be used if you specify arguments (of the program)

Options:
   --debugmsg name  Turn debugging-messages on or off
   --dll name       Enable or disable built-in DLLs
   --dosver x.xx    DOS version to imitate (e.g. 6.22)
                    Only valid with --winver win31
   --help,-h        Show this help message
   --managed        Allow the window manager to manage created windows
   --version,-v     Display the Wine version
   --winver         Version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win20,win30,win31)
   --dt             Defer trace until Alt+F12
   --use-dos-cwd    Used to set the DOS current working directory for the process (needs a path)
   --cmdline        Specifies the application's command line
   --monitor-cdrom-eject        Activate monitoring of CD-ROM ejection requests
root@pc12:/home/andrea # /home/andrea/bin
bash: /home/andrea/bin: is a directory
root@pc12:/home/andrea # cvscedega
bash: cvscedega: command not found
root@pc12:/home/andrea # /home/andrea/bin/cvscedega

FuddFeatures:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:  cvscedega regapi <regfilename.reg>
Install .reg with regedit: cvscedega regedit [regfilename.reg]
Start winecfg:             cvscedega winecfg
Log to file:               cvscedega log <normal params>
         eg:               cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console

Cedega CVS

Usage: /home/andrea/.WineCVS/installs/cvscedega/bin/wine [options] [--] program_name [arguments]
The -- has to be used if you specify arguments (of the program)

Options:
   --debugmsg name  Turn debugging-messages on or off
   --dll name       Enable or disable built-in DLLs
   --dosver x.xx    DOS version to imitate (e.g. 6.22)
                    Only valid with --winver win31
   --help,-h        Show this help message
   --managed        Allow the window manager to manage created windows
   --version,-v     Display the Wine version
   --winver         Version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win20,win30,win31)
   --dt             Defer trace until Alt+F12
   --use-dos-cwd    Used to set the DOS current working directory for the process (needs a path)
   --cmdline        Specifies the application's command line
   --monitor-cdrom-eject        Activate monitoring of CD-ROM ejection requests
root@pc12:/home/andrea # make uninstall
make: *** No rule to make target `uninstall'.  Stop.
root@pc12:/home/andrea # -h
bash: -h: command not found
root@pc12:/home/andrea # --help,-h
bash: --help,-h: command not found
root@pc12:/home/andrea # /home/andrea/bin/cvscedega

FuddFeatures:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:  cvscedega regapi <regfilename.reg>
Install .reg with regedit: cvscedega regedit [regfilename.reg]
Start winecfg:             cvscedega winecfg
Log to file:               cvscedega log <normal params>
         eg:               cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console

Cedega CVS

Usage: /home/andrea/.WineCVS/installs/cvscedega/bin/wine [options] [--] program_name [arguments]
The -- has to be used if you specify arguments (of the program)

Options:
   --debugmsg name  Turn debugging-messages on or off
   --dll name       Enable or disable built-in DLLs
   --dosver x.xx    DOS version to imitate (e.g. 6.22)
                    Only valid with --winver win31
   --help,-h        Show this help message
   --managed        Allow the window manager to manage created windows
   --version,-v     Display the Wine version
   --winver         Version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win20,win30,win31)
   --dt             Defer trace until Alt+F12
   --use-dos-cwd    Used to set the DOS current working directory for the process (needs a path)
   --cmdline        Specifies the application's command line
   --monitor-cdrom-eject        Activate monitoring of CD-ROM ejection requests

what do i do>.<?

---

### Post by katu on 2005-10-01
First of all, try to use the code markers. It's really hard to find what you are actually doing in that post.
Did you manage to actually  compile cvs cedega? I got shot down with errors when I tried it about two days ago... 
To try make by itself, as in: "make clean" or  "make" you have to be in the source directory: ./WineCVS/sources/profile name/  (If I remember right). It could be one more directory down. Anyhow, you should have a file named "Makefile" in the directory where you want to use make.  
try running make there. If it compiled ok, it should say "Nothing to be done for  ...". I would expect it to finish with a lvalue error though. that means that there are errors in the cvs source... I haven't been able to find a workaround as of yet... 
Sorry I'm not much help here.

---

