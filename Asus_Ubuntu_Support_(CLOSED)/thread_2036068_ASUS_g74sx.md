---
title: "ASUS g74sx"
date: 2012-08-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jncocontrol on 2012-08-01
Hello,
I'm having difficulty installing Ubuntu, 1 of 3 things usually happen.
When i install from the LiveCD i get a error log that sent to a place on my C drive (See below for the most recent), It installs but i have to get either;
2) BusyBox
3 Bash Minimal Line Command Prompt.

Any help would much appreciated

The most recent error i got was this, I'll copy and paste whole sha-bang

```
 07-11 16:55 INFO   root: === wubi 12.04 rev265 ===
07-11 16:55 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-11 16:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-11 16:55 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\data
07-11 16:55 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\bin\7z.exe
07-11 16:55 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-11 16:55 DEBUG  CommonBackend: Fetching basic info...
07-11 16:55 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-11 16:55 DEBUG  CommonBackend: platform=win32
07-11 16:55 DEBUG  CommonBackend: osname=nt
07-11 16:55 DEBUG  CommonBackend: language=en_US
07-11 16:55 DEBUG  CommonBackend: encoding=cp1252
07-11 16:55 DEBUG  WindowsBackend: arch=amd64
07-11 16:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\data\isolist.ini
07-11 16:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-11 16:55 DEBUG  WindowsBackend: Fetching host info...
07-11 16:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-11 16:55 DEBUG  WindowsBackend: windows version=vista
07-11 16:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-11 16:55 DEBUG  WindowsBackend: windows_sp=None
07-11 16:55 DEBUG  WindowsBackend: windows_build=7600
07-11 16:55 DEBUG  WindowsBackend: gmt=-8
07-11 16:55 DEBUG  WindowsBackend: country=US
07-11 16:55 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-11 16:55 DEBUG  WindowsBackend: windows_username=Brad
07-11 16:55 DEBUG  WindowsBackend: user_full_name=Brad
07-11 16:55 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-11 16:55 DEBUG  WindowsBackend: windows_language_code=1033
07-11 16:55 DEBUG  WindowsBackend: windows_language=English
07-11 16:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-11 16:55 DEBUG  WindowsBackend: bootloader=vista
07-11 16:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 334386.242188 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(C: hd 334386.242188 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(E: hd 1522.69140625 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(F: hd 230864.886719 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(H: removable 3753.97265625 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-11 16:55 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-11 16:55 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-11 16:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-11 16:55 DEBUG  WindowsBackend: keyboard_id=67699721
07-11 16:55 DEBUG  WindowsBackend: keyboard_layout=us
07-11 16:55 DEBUG  WindowsBackend: keyboard_variant=
07-11 16:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-11 16:55 DEBUG  CommonBackend: locale=en_US.UTF-8
07-11 16:55 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-11 16:55 DEBUG  CommonBackend: Searching ISOs on USB devices
07-11 16:55 DEBUG  CommonBackend: Searching for local CDs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylED1D.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-11 16:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-11 16:55 DEBUG  Distro: wrong version: 9.10 != 12.04
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro: wrong version: 9.10 != 12.04
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 INFO   root: Already installed, running the uninstaller...
07-11 16:55 INFO   root: Running the uninstaller...
07-11 16:55 INFO   CommonBackend: Launching previous uninestaller E:\ubuntu\uninstall-wubi.exe
07-11 16:55 DEBUG  root: application.quit
07-11 16:55 DEBUG  root: application.on_quit
07-11 16:55 INFO   root: sys.exit
07-11 16:55 INFO   root: Quitting application
07-11 16:55 INFO   root: === wubi 12.04 rev265 ===
07-11 16:55 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-11 16:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-11 16:55 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\data
07-11 16:55 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\bin\7z.exe
07-11 16:55 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-11 16:55 DEBUG  CommonBackend: Fetching basic info...
07-11 16:55 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-11 16:55 DEBUG  CommonBackend: platform=win32
07-11 16:55 DEBUG  CommonBackend: osname=nt
07-11 16:55 DEBUG  CommonBackend: language=en_US
07-11 16:55 DEBUG  CommonBackend: encoding=cp1252
07-11 16:55 DEBUG  WindowsBackend: arch=amd64
07-11 16:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\data\isolist.ini
07-11 16:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-11 16:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-11 16:55 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-11 16:55 DEBUG  WindowsBackend: Fetching host info...
07-11 16:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-11 16:55 DEBUG  WindowsBackend: windows version=vista
07-11 16:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-11 16:55 DEBUG  WindowsBackend: windows_sp=None
07-11 16:55 DEBUG  WindowsBackend: windows_build=7600
07-11 16:55 DEBUG  WindowsBackend: gmt=-8
07-11 16:55 DEBUG  WindowsBackend: country=US
07-11 16:55 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-11 16:55 DEBUG  WindowsBackend: windows_username=Brad
07-11 16:55 DEBUG  WindowsBackend: user_full_name=Brad
07-11 16:55 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-11 16:55 DEBUG  WindowsBackend: windows_language_code=1033
07-11 16:55 DEBUG  WindowsBackend: windows_language=English
07-11 16:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-11 16:55 DEBUG  WindowsBackend: bootloader=vista
07-11 16:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 334384.730469 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(C: hd 334384.730469 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(F: hd 230864.886719 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(H: removable 3753.97265625 mb free ntfs)
07-11 16:55 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-11 16:55 DEBUG  WindowsBackend: uninstaller_path=None
07-11 16:55 DEBUG  WindowsBackend: previous_target_dir=None
07-11 16:55 DEBUG  WindowsBackend: previous_distro_name=None
07-11 16:55 DEBUG  WindowsBackend: keyboard_id=67699721
07-11 16:55 DEBUG  WindowsBackend: keyboard_layout=us
07-11 16:55 DEBUG  WindowsBackend: keyboard_variant=
07-11 16:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-11 16:55 DEBUG  CommonBackend: locale=en_US.UTF-8
07-11 16:55 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-11 16:55 DEBUG  CommonBackend: Searching ISOs on USB devices
07-11 16:55 DEBUG  CommonBackend: Searching for local CDs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-11 16:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-11 16:55 DEBUG  Distro: wrong version: 9.10 != 12.04
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro: wrong version: 9.10 != 12.04
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-11 16:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-11 16:55 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:55 INFO   root: Running the installer...
07-11 16:55 DEBUG  WindowsFrontend: __init__...
07-11 16:55 DEBUG  WindowsFrontend: on_init...
07-11 16:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\translations, languages=['en_US', 'en']
07-11 16:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\translations, languages=['en_US', 'en']
07-11 16:56 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brad
07-11 16:56 INFO   root: Received settings
07-11 16:56 DEBUG  CommonBackend: Searching for local CD
07-11 16:56 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp is a valid Ubuntu CD
07-11 16:56 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\casper\filesystem.squashfs
07-11 16:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 16:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 16:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 16:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 16:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 16:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 16:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-11 16:56 DEBUG  Distro: wrong version: 9.10 != 12.04
07-11 16:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-11 16:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 16:56 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-11 16:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 16:56 DEBUG  CommonBackend: Searching for local ISO
07-11 16:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\translations, languages=['en_US', 'en']
07-11 16:56 DEBUG  TaskList: # Running tasklist...
07-11 16:56 DEBUG  TaskList: ## Running select_target_dir...
07-11 16:56 INFO   WindowsBackend: Installing into E:\ubuntu
07-11 16:56 DEBUG  TaskList: ## Finished select_target_dir
07-11 16:56 DEBUG  TaskList: ## Running create_dir_structure...
07-11 16:56 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-11 16:56 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-11 16:56 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-11 16:56 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-11 16:56 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-11 16:56 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-11 16:56 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-11 16:56 DEBUG  TaskList: ## Finished create_dir_structure
07-11 16:56 DEBUG  TaskList: ## Running create_uninstaller...
07-11 16:56 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-11 16:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-11 16:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-11 16:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-11 16:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-11 16:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-11 16:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-11 16:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-11 16:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-11 16:56 DEBUG  TaskList: ## Finished create_uninstaller
07-11 16:56 DEBUG  TaskList: ## Running create_preseed_diskimage...
07-11 16:56 DEBUG  TaskList: ## Finished create_preseed_diskimage
07-11 16:56 DEBUG  TaskList: ## Running get_diskimage...
07-11 16:56 DEBUG  TaskList: New task download
07-11 16:56 DEBUG  TaskList: ### Running download...
07-11 16:56 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz > E:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz
07-11 16:56 DEBUG  downloader: Download start filename=E:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz, basename=ubuntu-12.04-wubi-amd64.tar.xz, length=512730488, text=None
07-11 17:01 DEBUG  TaskList: ### Finished download
07-11 17:01 DEBUG  downloader: download finished (read 512730488 bytes)
07-11 17:01 DEBUG  TaskList: ## Finished get_diskimage
07-11 17:01 DEBUG  TaskList: ## Running extract_diskimage...
07-11 17:02 DEBUG  TaskList: ## Finished extract_diskimage
07-11 17:02 DEBUG  TaskList: ## Running choose_disk_sizes...
07-11 17:02 DEBUG  WindowsBackend: total size=8000
  root=7744
  swap=256
  home=0
  usr=0
07-11 17:02 DEBUG  TaskList: ## Finished choose_disk_sizes
07-11 17:02 DEBUG  TaskList: ## Running expand_diskimage...
07-11 17:04 DEBUG  TaskList: ## Finished expand_diskimage
07-11 17:04 DEBUG  TaskList: ## Running create_swap_diskimage...
07-11 17:04 DEBUG  TaskList: ## Finished create_swap_diskimage
07-11 17:04 DEBUG  TaskList: ## Running modify_bootloader...
07-11 17:04 DEBUG  TaskList: New task modify_bcd
07-11 17:04 DEBUG  TaskList: ### Running modify_bcd...
07-11 17:04 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 334384.730469 mb free ntfs)
07-11 17:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {76cd50a6-c7e9-11e1-ac33-be1aa438bbbf}
07-11 17:04 DEBUG  TaskList: ### Finished modify_bcd
07-11 17:04 DEBUG  TaskList: New task modify_bcd
07-11 17:04 DEBUG  TaskList: ### Running modify_bcd...
07-11 17:04 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 24874.9101563 mb free ntfs)
07-11 17:04 DEBUG  WindowsBackend: BCD has already been modified
07-11 17:04 DEBUG  TaskList: ### Finished modify_bcd
07-11 17:04 DEBUG  TaskList: New task modify_bcd
07-11 17:04 DEBUG  TaskList: ### Running modify_bcd...
07-11 17:04 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 10219.8867188 mb free ntfs)
07-11 17:04 DEBUG  WindowsBackend: BCD has already been modified
07-11 17:04 DEBUG  TaskList: ### Finished modify_bcd
07-11 17:04 DEBUG  TaskList: New task modify_bcd
07-11 17:04 DEBUG  TaskList: ### Running modify_bcd...
07-11 17:04 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 230864.886719 mb free ntfs)
07-11 17:04 DEBUG  WindowsBackend: BCD has already been modified
07-11 17:04 DEBUG  TaskList: ### Finished modify_bcd
07-11 17:04 DEBUG  TaskList: New task modify_bcd
07-11 17:04 DEBUG  TaskList: ### Running modify_bcd...
07-11 17:04 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 3753.97265625 mb free ntfs)
07-11 17:04 DEBUG  WindowsBackend: BCD has already been modified
07-11 17:04 DEBUG  TaskList: ### Finished modify_bcd
07-11 17:04 DEBUG  TaskList: New task modify_bcd
07-11 17:04 DEBUG  TaskList: ### Running modify_bcd...
07-11 17:04 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
07-11 17:04 DEBUG  WindowsBackend: BCD has already been modified
07-11 17:04 DEBUG  TaskList: ### Finished modify_bcd
07-11 17:04 DEBUG  TaskList: ## Finished modify_bootloader
07-11 17:04 DEBUG  TaskList: ## Running diskimage_bootloader...
07-11 17:04 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\winboot -> E:\ubuntu\winboot
07-11 17:04 DEBUG  TaskList: ## Finished diskimage_bootloader
07-11 17:04 DEBUG  TaskList: # Finished tasklist
07-11 17:04 INFO   root: Almost finished installing
07-11 17:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl3A23.tmp\translations, languages=['en_US', 'en']
07-11 17:04 INFO   root: Finished installation
07-11 17:04 DEBUG  root: application.quit
07-11 17:04 DEBUG  WindowsFrontend: frontend.quit
07-11 17:04 DEBUG  WindowsFrontend: frontend.on_quit
07-11 17:04 DEBUG  root: application.on_quit
07-11 17:04 INFO   root: sys.exit
07-19 05:41 INFO   root: === wubi 12.04 rev265 ===
07-19 05:41 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-19 05:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
07-19 05:41 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\data
07-19 05:41 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\bin\7z.exe
07-19 05:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-19 05:41 DEBUG  CommonBackend: Fetching basic info...
07-19 05:41 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
07-19 05:41 DEBUG  CommonBackend: platform=win32
07-19 05:41 DEBUG  CommonBackend: osname=nt
07-19 05:41 DEBUG  CommonBackend: language=en_US
07-19 05:41 DEBUG  CommonBackend: encoding=cp1252
07-19 05:41 DEBUG  WindowsBackend: arch=amd64
07-19 05:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\data\isolist.ini
07-19 05:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-19 05:41 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-19 05:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-19 05:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-19 05:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-19 05:41 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-19 05:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-19 05:41 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-19 05:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-19 05:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-19 05:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-19 05:41 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-19 05:41 DEBUG  WindowsBackend: Fetching host info...
07-19 05:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-19 05:41 DEBUG  WindowsBackend: windows version=vista
07-19 05:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-19 05:41 DEBUG  WindowsBackend: windows_sp=None
07-19 05:41 DEBUG  WindowsBackend: windows_build=7600
07-19 05:41 DEBUG  WindowsBackend: gmt=-8
07-19 05:41 DEBUG  WindowsBackend: country=US
07-19 05:41 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-19 05:41 DEBUG  WindowsBackend: windows_username=Brad
07-19 05:41 DEBUG  WindowsBackend: user_full_name=Brad
07-19 05:41 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-19 05:41 DEBUG  WindowsBackend: windows_language_code=1033
07-19 05:41 DEBUG  WindowsBackend: windows_language=English
07-19 05:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-19 05:41 DEBUG  WindowsBackend: bootloader=vista
07-19 05:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 238668.792969 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: drive=Drive(C: hd 238668.792969 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.7773438 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: drive=Drive(E: hd 5639.15234375 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: drive=Drive(F: hd 230864.753906 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-19 05:41 DEBUG  WindowsBackend: drive=Drive(H: hd 42582.0390625 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-19 05:41 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-19 05:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-19 05:41 DEBUG  WindowsBackend: keyboard_id=67699721
07-19 05:41 DEBUG  WindowsBackend: keyboard_layout=us
07-19 05:41 DEBUG  WindowsBackend: keyboard_variant=
07-19 05:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-19 05:41 DEBUG  CommonBackend: locale=en_US.UTF-8
07-19 05:41 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-19 05:41 DEBUG  CommonBackend: Searching ISOs on USB devices
07-19 05:41 DEBUG  CommonBackend: Searching for local CDs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-19 05:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-19 05:41 INFO   root: Running the uninstaller...
07-19 05:41 INFO   CommonBackend: This is the uninstaller running
07-19 05:41 DEBUG  WindowsFrontend: __init__...
07-19 05:41 DEBUG  WindowsFrontend: on_init...
07-19 05:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\translations, languages=['en_US', 'en']
07-19 05:41 INFO   root: Received settings
07-19 05:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\translations, languages=['en_US', 'en']
07-19 05:41 DEBUG  TaskList: # Running tasklist...
07-19 05:41 DEBUG  TaskList: ## Running Remove bootloader entry...
07-19 05:41 DEBUG  WindowsBackend: Removing bcd entry {76cd50a6-c7e9-11e1-ac33-be1aa438bbbf}
07-19 05:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
07-19 05:41 DEBUG  WindowsBackend: undo_bootini C:
07-19 05:41 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 238668.792969 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: undo_bootini D:
07-19 05:41 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.7773438 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: undo_bootini E:
07-19 05:41 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 5639.15234375 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: undo_bootini F:
07-19 05:41 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230864.753906 mb free ntfs)
07-19 05:41 DEBUG  WindowsBackend: undo_bootini H:
07-19 05:41 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 42582.0390625 mb free ntfs)
07-19 05:41 DEBUG  TaskList: ## Finished Remove bootloader entry
07-19 05:41 DEBUG  TaskList: ## Running Remove target dir...
07-19 05:41 DEBUG  CommonBackend: Deleting E:\ubuntu
07-19 05:41 DEBUG  TaskList: ## Finished Remove target dir
07-19 05:41 DEBUG  TaskList: ## Running Remove registry key...
07-19 05:41 DEBUG  TaskList: ## Finished Remove registry key
07-19 05:41 DEBUG  TaskList: # Finished tasklist
07-19 05:41 INFO   root: Almost finished uninstalling
07-19 05:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1998.tmp\translations, languages=['en_US', 'en']
07-19 05:41 INFO   root: Finished uninstallation
07-19 05:41 DEBUG  root: application.quit
07-19 05:41 DEBUG  WindowsFrontend: frontend.quit
07-19 05:41 DEBUG  WindowsFrontend: frontend.on_quit
07-19 05:41 DEBUG  root: application.on_quit
07-19 05:41 INFO   root: sys.exit
07-28 20:52 INFO   root: === wubi 12.04 rev265 ===
07-28 20:52 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-28 20:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-28 20:52 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\data
07-28 20:52 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\bin\7z.exe
07-28 20:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-28 20:52 DEBUG  CommonBackend: Fetching basic info...
07-28 20:52 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-28 20:52 DEBUG  CommonBackend: platform=win32
07-28 20:52 DEBUG  CommonBackend: osname=nt
07-28 20:52 DEBUG  CommonBackend: language=en_US
07-28 20:52 DEBUG  CommonBackend: encoding=cp932
07-28 20:52 DEBUG  WindowsBackend: arch=amd64
07-28 20:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\data\isolist.ini
07-28 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-28 20:52 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-28 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-28 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-28 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-28 20:52 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-28 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-28 20:52 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-28 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-28 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-28 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-28 20:52 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-28 20:52 DEBUG  WindowsBackend: Fetching host info...
07-28 20:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-28 20:52 DEBUG  WindowsBackend: windows version=vista
07-28 20:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-28 20:52 DEBUG  WindowsBackend: windows_sp=None
07-28 20:52 DEBUG  WindowsBackend: windows_build=7600
07-28 20:52 DEBUG  WindowsBackend: gmt=-8
07-28 20:52 DEBUG  WindowsBackend: country=US
07-28 20:52 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-28 20:52 DEBUG  WindowsBackend: windows_username=Brad
07-28 20:52 DEBUG  WindowsBackend: user_full_name=Brad
07-28 20:52 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-28 20:52 DEBUG  WindowsBackend: windows_language_code=1033
07-28 20:52 DEBUG  WindowsBackend: windows_language=English
07-28 20:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-28 20:52 DEBUG  WindowsBackend: bootloader=vista
07-28 20:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 281612.539063 mb free ntfs)
07-28 20:52 DEBUG  WindowsBackend: drive=Drive(C: hd 281612.539063 mb free ntfs)
07-28 20:52 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-28 20:52 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-28 20:52 DEBUG  WindowsBackend: drive=Drive(F: hd 230864.886719 mb free ntfs)
07-28 20:52 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-28 20:52 DEBUG  WindowsBackend: drive=Drive(H: hd 20003.125 mb free ntfs)
07-28 20:52 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-28 20:52 DEBUG  WindowsBackend: uninstaller_path=None
07-28 20:52 DEBUG  WindowsBackend: previous_target_dir=None
07-28 20:52 DEBUG  WindowsBackend: previous_distro_name=None
07-28 20:52 DEBUG  WindowsBackend: keyboard_id=67699721
07-28 20:52 DEBUG  WindowsBackend: keyboard_layout=us
07-28 20:52 DEBUG  WindowsBackend: keyboard_variant=
07-28 20:52 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-28 20:52 DEBUG  CommonBackend: locale=en_US.UTF-8
07-28 20:52 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-28 20:52 DEBUG  CommonBackend: Searching ISOs on USB devices
07-28 20:52 DEBUG  CommonBackend: Searching for local CDs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release amd64 (20120425)
07-28 20:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120425', 'codename': 'Precise Pangolin', 'arch': 'amd64'}
07-28 20:52 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-28 20:52 INFO   root: Running the installer...
07-28 20:52 DEBUG  WindowsFrontend: __init__...
07-28 20:52 DEBUG  WindowsFrontend: on_init...
07-28 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\translations, languages=['en_US', 'en']
07-28 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\translations, languages=['en_US', 'en']
07-28 20:52 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brad
07-28 20:52 INFO   root: Received settings
07-28 20:52 DEBUG  CommonBackend: Searching for local CD
07-28 20:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-28 20:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-28 20:52 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-28 20:52 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-28 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\translations, languages=['en_US', 'en']
07-28 20:52 DEBUG  TaskList: # Running tasklist...
07-28 20:52 DEBUG  TaskList: ## Running select_target_dir...
07-28 20:52 INFO   WindowsBackend: Installing into E:\ubuntu
07-28 20:52 DEBUG  TaskList: ## Finished select_target_dir
07-28 20:52 DEBUG  TaskList: ## Running create_dir_structure...
07-28 20:52 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-28 20:52 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-28 20:52 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-28 20:52 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-28 20:52 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-28 20:52 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-28 20:52 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-28 20:52 DEBUG  TaskList: ## Finished create_dir_structure
07-28 20:52 DEBUG  TaskList: ## Running uncompress_target_dir...
07-28 20:52 DEBUG  TaskList: ## Finished uncompress_target_dir
07-28 20:52 DEBUG  TaskList: ## Running create_uninstaller...
07-28 20:52 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-28 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-28 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-28 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-28 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-28 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-28 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-28 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-28 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-28 20:52 DEBUG  TaskList: ## Finished create_uninstaller
07-28 20:52 DEBUG  TaskList: ## Running copy_installation_files...
07-28 20:52 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-28 20:52 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\winboot -> E:\ubuntu\winboot
07-28 20:52 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-28 20:52 DEBUG  TaskList: ## Finished copy_installation_files
07-28 20:52 DEBUG  TaskList: ## Running get_iso...
07-28 20:52 DEBUG  TaskList: New task copy_file
07-28 20:52 DEBUG  TaskList: ### Running copy_file...
07-28 20:52 DEBUG  TaskList: ### Finished copy_file
07-28 20:52 DEBUG  TaskList: New task check_iso
07-28 20:52 DEBUG  TaskList: ### Running check_iso...
07-28 20:52 DEBUG  CommonBackend: Checking E:\ubuntu\install\installation.iso
07-28 20:52 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\installation.iso
07-28 20:52 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\installation.iso
07-28 20:52 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release amd64 (20120425)
07-28 20:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120425', 'codename': 'Precise Pangolin', 'arch': 'amd64'}
07-28 20:52 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu\install\installation.iso
07-28 20:52 DEBUG  TaskList: New task get_metalink
07-28 20:52 DEBUG  TaskList: #### Running get_metalink...
07-28 20:52 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-amd64.metalink > E:\ubuntu\install
07-28 20:52 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-12.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-amd64.metalink, basename=ubuntu-12.04-desktop-amd64.metalink, length=30782, text=None
07-28 20:52 DEBUG  downloader: download finished (read 30782 bytes)
07-28 20:52 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/MD5SUMS-metalink > E:\ubuntu\install
07-28 20:52 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
07-28 20:52 DEBUG  downloader: download finished (read 419 bytes)
07-28 20:52 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg > E:\ubuntu\install
07-28 20:52 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-28 20:52 DEBUG  downloader: download finished (read 198 bytes)
07-28 20:52 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-28 20:52 INFO   saplog: Checking block bindings..
07-28 20:52 INFO   saplog: Key verified successfully.
07-28 20:52 DEBUG  CommonBackend: metalink md5sums:
1e2a0b0f07bc43ab5924767a9cc03e82  ubuntu-12.04-alternate-amd64.metalink
4413660abc989dbbfe6e4abedc9a3ec1  ubuntu-12.04-alternate-i386.metalink
c29be6d58c1581d9cd679aca25db77d1  ubuntu-12.04-desktop-amd64.metalink
c7a6b99206703cfe37f1da5af1d28e3a  ubuntu-12.04-desktop-i386.metalink
4e44ca9bc7ee8ab54ff9565a5437bdc2  ubuntu-12.04-server-amd64.metalink
c9cfc1dd8c65099d929189eedc157f3c  ubuntu-12.04-server-i386.metalink

07-28 20:52 DEBUG  TaskList: #### Finished get_metalink
07-28 20:52 DEBUG  TaskList: New task get_file_md5
07-28 20:52 DEBUG  TaskList: #### Running get_file_md5...
07-28 20:53 DEBUG  TaskList: #### Finished get_file_md5
07-28 20:53 DEBUG  TaskList: ### Finished check_iso
07-28 20:53 DEBUG  TaskList: ## Finished get_iso
07-28 20:53 DEBUG  TaskList: ## Running extract_kernel...
07-28 20:53 DEBUG  CommonBackend: Copying files from CD I:\
07-28 20:53 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-28 20:53 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\vmlinuz
07-28 20:53 DEBUG  CommonBackend:   E:\ubuntu\install\boot\vmlinuz md5 = ec12ab2c89c1420f3362ebba47ddd23b == ec12ab2c89c1420f3362ebba47ddd23b
07-28 20:53 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\initrd.lz
07-28 20:53 DEBUG  CommonBackend:   E:\ubuntu\install\boot\initrd.lz md5 = 5d2b565e5e753b9211e3bb55b87042ce == 5d2b565e5e753b9211e3bb55b87042ce
07-28 20:53 DEBUG  TaskList: ## Finished extract_kernel
07-28 20:53 DEBUG  TaskList: ## Running choose_disk_sizes...
07-28 20:53 DEBUG  WindowsBackend: total size=7000
  root=6744
  swap=256
  home=0
  usr=0
07-28 20:53 DEBUG  TaskList: ## Finished choose_disk_sizes
07-28 20:53 DEBUG  TaskList: ## Running create_preseed...
07-28 20:53 DEBUG  TaskList: ## Finished create_preseed
07-28 20:53 DEBUG  TaskList: ## Running modify_bootloader...
07-28 20:53 DEBUG  TaskList: New task modify_bcd
07-28 20:53 DEBUG  TaskList: ### Running modify_bcd...
07-28 20:53 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 281612.539063 mb free ntfs)
07-28 20:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {76cd50ab-c7e9-11e1-ac33-be1aa438bbbf}
07-28 20:53 DEBUG  TaskList: ### Finished modify_bcd
07-28 20:53 DEBUG  TaskList: New task modify_bcd
07-28 20:53 DEBUG  TaskList: ### Running modify_bcd...
07-28 20:53 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 24874.9101563 mb free ntfs)
07-28 20:53 DEBUG  WindowsBackend: BCD has already been modified
07-28 20:53 DEBUG  TaskList: ### Finished modify_bcd
07-28 20:53 DEBUG  TaskList: New task modify_bcd
07-28 20:53 DEBUG  TaskList: ### Running modify_bcd...
07-28 20:53 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 10219.8867188 mb free ntfs)
07-28 20:53 DEBUG  WindowsBackend: BCD has already been modified
07-28 20:53 DEBUG  TaskList: ### Finished modify_bcd
07-28 20:53 DEBUG  TaskList: New task modify_bcd
07-28 20:53 DEBUG  TaskList: ### Running modify_bcd...
07-28 20:53 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 230864.886719 mb free ntfs)
07-28 20:53 DEBUG  WindowsBackend: BCD has already been modified
07-28 20:53 DEBUG  TaskList: ### Finished modify_bcd
07-28 20:53 DEBUG  TaskList: New task modify_bcd
07-28 20:53 DEBUG  TaskList: ### Running modify_bcd...
07-28 20:53 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 20003.125 mb free ntfs)
07-28 20:53 DEBUG  WindowsBackend: BCD has already been modified
07-28 20:53 DEBUG  TaskList: ### Finished modify_bcd
07-28 20:53 DEBUG  TaskList: ## Finished modify_bootloader
07-28 20:53 DEBUG  TaskList: ## Running modify_grub_configuration...
07-28 20:53 DEBUG  TaskList: ## Finished modify_grub_configuration
07-28 20:53 DEBUG  TaskList: ## Running create_virtual_disks...
07-28 20:53 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\root.disk of 6744MB
07-28 20:53 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\swap.disk of 256MB
07-28 20:53 DEBUG  TaskList: ## Finished create_virtual_disks
07-28 20:53 DEBUG  TaskList: ## Running uncompress_files...
07-28 20:53 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot /U /A /F
07-28 20:53 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot\*.* /U /A /F
07-28 20:53 DEBUG  TaskList: ## Finished uncompress_files
07-28 20:53 DEBUG  TaskList: ## Running eject_cd...
07-28 20:53 DEBUG  TaskList: ## Finished eject_cd
07-28 20:53 DEBUG  TaskList: # Finished tasklist
07-28 20:53 INFO   root: Almost finished installing
07-28 20:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl8CB2.tmp\translations, languages=['en_US', 'en']
07-28 20:53 INFO   root: Finished installation
07-28 20:53 DEBUG  root: application.quit
07-28 20:53 DEBUG  WindowsFrontend: frontend.quit
07-28 20:53 DEBUG  WindowsFrontend: frontend.on_quit
07-28 20:53 DEBUG  root: application.on_quit
07-28 20:53 INFO   root: sys.exit
07-29 10:09 INFO   root: === wubi 12.04 rev265 ===
07-29 10:09 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-29 10:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-29 10:09 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\data
07-29 10:09 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\bin\7z.exe
07-29 10:09 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-29 10:09 DEBUG  CommonBackend: Fetching basic info...
07-29 10:09 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-29 10:09 DEBUG  CommonBackend: platform=win32
07-29 10:09 DEBUG  CommonBackend: osname=nt
07-29 10:09 DEBUG  CommonBackend: language=en_US
07-29 10:09 DEBUG  CommonBackend: encoding=cp932
07-29 10:09 DEBUG  WindowsBackend: arch=amd64
07-29 10:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\data\isolist.ini
07-29 10:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-29 10:09 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-29 10:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-29 10:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-29 10:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-29 10:09 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-29 10:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-29 10:09 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-29 10:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-29 10:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-29 10:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-29 10:09 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-29 10:09 DEBUG  WindowsBackend: Fetching host info...
07-29 10:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-29 10:09 DEBUG  WindowsBackend: windows version=vista
07-29 10:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-29 10:09 DEBUG  WindowsBackend: windows_sp=None
07-29 10:09 DEBUG  WindowsBackend: windows_build=7600
07-29 10:09 DEBUG  WindowsBackend: gmt=-8
07-29 10:09 DEBUG  WindowsBackend: country=US
07-29 10:09 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-29 10:09 DEBUG  WindowsBackend: windows_username=Brad
07-29 10:09 DEBUG  WindowsBackend: user_full_name=Brad
07-29 10:09 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-29 10:09 DEBUG  WindowsBackend: windows_language_code=1033
07-29 10:09 DEBUG  WindowsBackend: windows_language=English
07-29 10:09 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-29 10:09 DEBUG  WindowsBackend: bootloader=vista
07-29 10:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 282513.109375 mb free ntfs)
07-29 10:09 DEBUG  WindowsBackend: drive=Drive(C: hd 282513.109375 mb free ntfs)
07-29 10:09 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:09 DEBUG  WindowsBackend: drive=Drive(E: hd 2499.88671875 mb free ntfs)
07-29 10:09 DEBUG  WindowsBackend: drive=Drive(F: hd 230864.886719 mb free ntfs)
07-29 10:09 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-29 10:09 DEBUG  WindowsBackend: drive=Drive(H: hd 20003.125 mb free ntfs)
07-29 10:09 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-29 10:09 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-29 10:09 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-29 10:09 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-29 10:09 DEBUG  WindowsBackend: keyboard_id=67699721
07-29 10:09 DEBUG  WindowsBackend: keyboard_layout=us
07-29 10:09 DEBUG  WindowsBackend: keyboard_variant=
07-29 10:09 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-29 10:09 DEBUG  CommonBackend: locale=en_US.UTF-8
07-29 10:09 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-29 10:09 DEBUG  CommonBackend: Searching ISOs on USB devices
07-29 10:09 DEBUG  CommonBackend: Searching for local CDs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-29 10:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-29 10:09 INFO   root: Already installed, running the uninstaller...
07-29 10:09 INFO   root: Running the uninstaller...
07-29 10:09 INFO   CommonBackend: This is the uninstaller running
07-29 10:09 DEBUG  WindowsFrontend: __init__...
07-29 10:09 DEBUG  WindowsFrontend: on_init...
07-29 10:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl7D85.tmp\translations, languages=['en_US', 'en']
07-29 10:09 INFO   WindowsFrontend: Operation cancelled
07-29 10:09 DEBUG  WindowsFrontend: frontend.quit
07-29 10:09 DEBUG  WindowsFrontend: frontend.on_quit
07-29 10:09 DEBUG  root: application.on_quit
07-29 10:09 INFO   root: sys.exit
07-29 10:22 INFO   root: === wubi 12.04 rev265 ===
07-29 10:22 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-29 10:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
07-29 10:22 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\data
07-29 10:22 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\bin\7z.exe
07-29 10:22 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-29 10:22 DEBUG  CommonBackend: Fetching basic info...
07-29 10:22 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
07-29 10:22 DEBUG  CommonBackend: platform=win32
07-29 10:22 DEBUG  CommonBackend: osname=nt
07-29 10:22 DEBUG  CommonBackend: language=en_US
07-29 10:22 DEBUG  CommonBackend: encoding=cp932
07-29 10:22 DEBUG  WindowsBackend: arch=amd64
07-29 10:22 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\data\isolist.ini
07-29 10:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-29 10:22 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-29 10:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-29 10:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-29 10:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-29 10:22 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-29 10:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-29 10:22 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-29 10:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-29 10:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-29 10:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-29 10:22 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-29 10:22 DEBUG  WindowsBackend: Fetching host info...
07-29 10:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-29 10:22 DEBUG  WindowsBackend: windows version=vista
07-29 10:22 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-29 10:22 DEBUG  WindowsBackend: windows_sp=None
07-29 10:22 DEBUG  WindowsBackend: windows_build=7600
07-29 10:22 DEBUG  WindowsBackend: gmt=-8
07-29 10:22 DEBUG  WindowsBackend: country=US
07-29 10:22 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-29 10:22 DEBUG  WindowsBackend: windows_username=Brad
07-29 10:22 DEBUG  WindowsBackend: user_full_name=Brad
07-29 10:22 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-29 10:22 DEBUG  WindowsBackend: windows_language_code=1033
07-29 10:22 DEBUG  WindowsBackend: windows_language=English
07-29 10:22 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-29 10:22 DEBUG  WindowsBackend: bootloader=vista
07-29 10:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 282526.164063 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: drive=Drive(C: hd 282526.164063 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: drive=Drive(E: hd 2499.88671875 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: drive=Drive(F: hd 230864.886719 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-29 10:22 DEBUG  WindowsBackend: drive=Drive(H: hd 20003.125 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-29 10:22 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-29 10:22 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-29 10:22 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-29 10:22 DEBUG  WindowsBackend: keyboard_id=67699721
07-29 10:22 DEBUG  WindowsBackend: keyboard_layout=us
07-29 10:22 DEBUG  WindowsBackend: keyboard_variant=
07-29 10:22 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-29 10:22 DEBUG  CommonBackend: locale=en_US.UTF-8
07-29 10:22 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-29 10:22 DEBUG  CommonBackend: Searching ISOs on USB devices
07-29 10:22 DEBUG  CommonBackend: Searching for local CDs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:22 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-29 10:22 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release amd64 (20120425)
07-29 10:22 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120425', 'codename': 'Precise Pangolin', 'arch': 'amd64'}
07-29 10:22 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-29 10:22 INFO   root: Running the uninstaller...
07-29 10:22 INFO   CommonBackend: This is the uninstaller running
07-29 10:22 DEBUG  WindowsFrontend: __init__...
07-29 10:22 DEBUG  WindowsFrontend: on_init...
07-29 10:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\translations, languages=['en_US', 'en']
07-29 10:22 INFO   root: Received settings
07-29 10:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\translations, languages=['en_US', 'en']
07-29 10:22 DEBUG  TaskList: # Running tasklist...
07-29 10:22 DEBUG  TaskList: ## Running Remove bootloader entry...
07-29 10:22 DEBUG  WindowsBackend: Removing bcd entry {76cd50ab-c7e9-11e1-ac33-be1aa438bbbf}
07-29 10:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
07-29 10:22 DEBUG  WindowsBackend: undo_bootini C:
07-29 10:22 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 282526.164063 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: undo_bootini D:
07-29 10:22 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: undo_bootini E:
07-29 10:22 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 2499.88671875 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: undo_bootini F:
07-29 10:22 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230864.886719 mb free ntfs)
07-29 10:22 DEBUG  WindowsBackend: undo_bootini H:
07-29 10:22 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 20003.125 mb free ntfs)
07-29 10:22 DEBUG  TaskList: ## Finished Remove bootloader entry
07-29 10:22 DEBUG  TaskList: ## Running Remove target dir...
07-29 10:22 DEBUG  CommonBackend: Deleting E:\ubuntu
07-29 10:22 DEBUG  TaskList: ## Finished Remove target dir
07-29 10:22 DEBUG  TaskList: ## Running Remove registry key...
07-29 10:22 DEBUG  TaskList: ## Finished Remove registry key
07-29 10:22 DEBUG  TaskList: # Finished tasklist
07-29 10:22 INFO   root: Almost finished uninstalling
07-29 10:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl33A.tmp\translations, languages=['en_US', 'en']
07-29 10:22 INFO   root: Finished uninstallation
07-29 10:22 DEBUG  root: application.quit
07-29 10:22 DEBUG  WindowsFrontend: frontend.quit
07-29 10:22 DEBUG  WindowsFrontend: frontend.on_quit
07-29 10:22 DEBUG  root: application.on_quit
07-29 10:22 INFO   root: sys.exit
07-29 10:27 INFO   root: === wubi 12.04 rev265 ===
07-29 10:27 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-29 10:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
07-29 10:27 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\data
07-29 10:27 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\bin\7z.exe
07-29 10:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-29 10:27 DEBUG  CommonBackend: Fetching basic info...
07-29 10:27 DEBUG  CommonBackend: original_exe=I:\wubi.exe
07-29 10:27 DEBUG  CommonBackend: platform=win32
07-29 10:27 DEBUG  CommonBackend: osname=nt
07-29 10:27 DEBUG  CommonBackend: language=en_US
07-29 10:27 DEBUG  CommonBackend: encoding=cp932
07-29 10:27 DEBUG  WindowsBackend: arch=amd64
07-29 10:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\data\isolist.ini
07-29 10:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-29 10:27 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-29 10:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-29 10:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-29 10:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-29 10:27 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-29 10:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-29 10:27 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-29 10:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-29 10:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-29 10:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-29 10:27 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-29 10:27 DEBUG  WindowsBackend: Fetching host info...
07-29 10:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-29 10:27 DEBUG  WindowsBackend: windows version=vista
07-29 10:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-29 10:27 DEBUG  WindowsBackend: windows_sp=None
07-29 10:27 DEBUG  WindowsBackend: windows_build=7600
07-29 10:27 DEBUG  WindowsBackend: gmt=-8
07-29 10:27 DEBUG  WindowsBackend: country=US
07-29 10:27 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-29 10:27 DEBUG  WindowsBackend: windows_username=Brad
07-29 10:27 DEBUG  WindowsBackend: user_full_name=Brad
07-29 10:27 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-29 10:27 DEBUG  WindowsBackend: windows_language_code=1033
07-29 10:27 DEBUG  WindowsBackend: windows_language=English
07-29 10:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-29 10:27 DEBUG  WindowsBackend: bootloader=vista
07-29 10:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 282527.84375 mb free ntfs)
07-29 10:27 DEBUG  WindowsBackend: drive=Drive(C: hd 282527.84375 mb free ntfs)
07-29 10:27 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:27 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-29 10:27 DEBUG  WindowsBackend: drive=Drive(F: hd 230864.886719 mb free ntfs)
07-29 10:27 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-29 10:27 DEBUG  WindowsBackend: drive=Drive(H: hd 20003.125 mb free ntfs)
07-29 10:27 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-29 10:27 DEBUG  WindowsBackend: uninstaller_path=None
07-29 10:27 DEBUG  WindowsBackend: previous_target_dir=None
07-29 10:27 DEBUG  WindowsBackend: previous_distro_name=None
07-29 10:27 DEBUG  WindowsBackend: keyboard_id=67699721
07-29 10:27 DEBUG  WindowsBackend: keyboard_layout=us
07-29 10:27 DEBUG  WindowsBackend: keyboard_variant=
07-29 10:27 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-29 10:27 DEBUG  CommonBackend: locale=en_US.UTF-8
07-29 10:27 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-29 10:27 DEBUG  CommonBackend: Searching ISOs on USB devices
07-29 10:27 DEBUG  CommonBackend: Searching for local CDs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-29 10:27 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-29 10:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-29 10:27 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-29 10:27 INFO   root: Running the CD menu...
07-29 10:27 DEBUG  WindowsFrontend: __init__...
07-29 10:27 DEBUG  WindowsFrontend: on_init...
07-29 10:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\translations, languages=['en_US', 'en']
07-29 10:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\translations, languages=['en_US', 'en']
07-29 10:27 INFO   root: CD menu finished
07-29 10:27 INFO   root: Running the CD boot helper...
07-29 10:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\translations, languages=['en_US', 'en']
07-29 10:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\translations, languages=['en_US', 'en']
07-29 10:28 INFO   root: CD boot helper confirmed
07-29 10:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\translations, languages=['en_US', 'en']
07-29 10:28 DEBUG  TaskList: # Running tasklist...
07-29 10:28 DEBUG  TaskList: ## Running select_target_dir...
07-29 10:28 INFO   WindowsBackend: Installing into C:\ubuntu
07-29 10:28 DEBUG  TaskList: ## Finished select_target_dir
07-29 10:28 DEBUG  TaskList: ## Running create_dir_structure...
07-29 10:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-29 10:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-29 10:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-29 10:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-29 10:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-29 10:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-29 10:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-29 10:28 DEBUG  TaskList: ## Finished create_dir_structure
07-29 10:28 DEBUG  TaskList: ## Running uncompress_target_dir...
07-29 10:28 DEBUG  TaskList: ## Finished uncompress_target_dir
07-29 10:28 DEBUG  TaskList: ## Running create_uninstaller...
07-29 10:28 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-29 10:28 DEBUG  TaskList: ## Finished create_uninstaller
07-29 10:28 DEBUG  TaskList: ## Running copy_installation_files...
07-29 10:28 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-29 10:28 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\winboot -> C:\ubuntu\winboot
07-29 10:28 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-29 10:28 DEBUG  TaskList: ## Finished copy_installation_files
07-29 10:28 DEBUG  TaskList: ## Running use_cd...
07-29 10:28 DEBUG  TaskList: New task copy_file
07-29 10:28 DEBUG  TaskList: ### Running copy_file...
07-29 10:28 DEBUG  TaskList: ### Finished copy_file
07-29 10:28 DEBUG  TaskList: New task check_iso
07-29 10:28 DEBUG  TaskList: ### Running check_iso...
07-29 10:28 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
07-29 10:28 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
07-29 10:28 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
07-29 10:28 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-29 10:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-29 10:28 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
07-29 10:28 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
07-29 10:28 DEBUG  TaskList: New task get_metalink
07-29 10:28 DEBUG  TaskList: #### Running get_metalink...
07-29 10:28 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink > C:\ubuntu\install
07-29 10:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-12.04-desktop-i386.metalink, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink, basename=ubuntu-12.04-desktop-i386.metalink, length=30559, text=None
07-29 10:28 DEBUG  downloader: download finished (read 30559 bytes)
07-29 10:28 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/MD5SUMS-metalink > C:\ubuntu\install
07-29 10:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
07-29 10:28 DEBUG  downloader: download finished (read 419 bytes)
07-29 10:28 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
07-29 10:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-29 10:28 DEBUG  downloader: download finished (read 198 bytes)
07-29 10:28 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-29 10:28 INFO   saplog: Checking block bindings..
07-29 10:28 INFO   saplog: Key verified successfully.
07-29 10:28 DEBUG  CommonBackend: metalink md5sums:
1e2a0b0f07bc43ab5924767a9cc03e82  ubuntu-12.04-alternate-amd64.metalink
4413660abc989dbbfe6e4abedc9a3ec1  ubuntu-12.04-alternate-i386.metalink
c29be6d58c1581d9cd679aca25db77d1  ubuntu-12.04-desktop-amd64.metalink
c7a6b99206703cfe37f1da5af1d28e3a  ubuntu-12.04-desktop-i386.metalink
4e44ca9bc7ee8ab54ff9565a5437bdc2  ubuntu-12.04-server-amd64.metalink
c9cfc1dd8c65099d929189eedc157f3c  ubuntu-12.04-server-i386.metalink

07-29 10:28 DEBUG  TaskList: #### Finished get_metalink
07-29 10:28 DEBUG  TaskList: New task get_file_md5
07-29 10:28 DEBUG  TaskList: #### Running get_file_md5...
07-29 10:28 DEBUG  TaskList: #### Finished get_file_md5
07-29 10:28 DEBUG  TaskList: ### Finished check_iso
07-29 10:28 DEBUG  TaskList: ## Finished use_cd
07-29 10:28 DEBUG  TaskList: ## Running extract_kernel...
07-29 10:28 DEBUG  CommonBackend: Copying files from CD I:\
07-29 10:28 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-29 10:28 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
07-29 10:28 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 0fb4d79f5f23cba37cf40ef017bb3c65 == 0fb4d79f5f23cba37cf40ef017bb3c65
07-29 10:28 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
07-29 10:28 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = f5112034765ef7db4c2ebcf2ea409ecf == f5112034765ef7db4c2ebcf2ea409ecf
07-29 10:28 DEBUG  TaskList: ## Finished extract_kernel
07-29 10:28 DEBUG  TaskList: ## Running create_preseed_cdboot...
07-29 10:28 DEBUG  TaskList: ## Finished create_preseed_cdboot
07-29 10:28 DEBUG  TaskList: ## Running modify_bootloader...
07-29 10:28 DEBUG  TaskList: New task modify_bcd
07-29 10:28 DEBUG  TaskList: ### Running modify_bcd...
07-29 10:28 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 282527.84375 mb free ntfs)
07-29 10:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {76cd50ac-c7e9-11e1-ac33-be1aa438bbbf}
07-29 10:28 DEBUG  TaskList: ### Finished modify_bcd
07-29 10:28 DEBUG  TaskList: New task modify_bcd
07-29 10:28 DEBUG  TaskList: ### Running modify_bcd...
07-29 10:28 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:28 DEBUG  WindowsBackend: BCD has already been modified
07-29 10:28 DEBUG  TaskList: ### Finished modify_bcd
07-29 10:28 DEBUG  TaskList: New task modify_bcd
07-29 10:28 DEBUG  TaskList: ### Running modify_bcd...
07-29 10:28 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 10219.8867188 mb free ntfs)
07-29 10:28 DEBUG  WindowsBackend: BCD has already been modified
07-29 10:28 DEBUG  TaskList: ### Finished modify_bcd
07-29 10:28 DEBUG  TaskList: New task modify_bcd
07-29 10:28 DEBUG  TaskList: ### Running modify_bcd...
07-29 10:28 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 230864.886719 mb free ntfs)
07-29 10:28 DEBUG  WindowsBackend: BCD has already been modified
07-29 10:28 DEBUG  TaskList: ### Finished modify_bcd
07-29 10:28 DEBUG  TaskList: New task modify_bcd
07-29 10:28 DEBUG  TaskList: ### Running modify_bcd...
07-29 10:28 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 20003.125 mb free ntfs)
07-29 10:28 DEBUG  WindowsBackend: BCD has already been modified
07-29 10:28 DEBUG  TaskList: ### Finished modify_bcd
07-29 10:28 DEBUG  TaskList: ## Finished modify_bootloader
07-29 10:28 DEBUG  TaskList: ## Running modify_grub_configuration...
07-29 10:28 DEBUG  TaskList: ## Finished modify_grub_configuration
07-29 10:28 DEBUG  TaskList: ## Running uncompress_files...
07-29 10:28 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
07-29 10:28 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
07-29 10:28 DEBUG  TaskList: ## Finished uncompress_files
07-29 10:28 DEBUG  TaskList: ## Running eject_cd...
07-29 10:28 DEBUG  TaskList: ## Finished eject_cd
07-29 10:28 DEBUG  TaskList: # Finished tasklist
07-29 10:28 INFO   root: Almost finished installing
07-29 10:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl1DAD.tmp\translations, languages=['en_US', 'en']
07-29 10:32 INFO   root: Finished installation
07-29 10:32 INFO   root: Rebooting
07-29 10:32 DEBUG  TaskList: # Running tasklist...
07-29 10:32 DEBUG  TaskList: ## Running reboot...
07-29 10:32 DEBUG  TaskList: ## Finished reboot
07-29 10:32 DEBUG  TaskList: # Finished tasklist
07-29 10:32 DEBUG  root: application.quit
07-29 10:32 DEBUG  WindowsFrontend: frontend.quit
07-29 10:32 DEBUG  WindowsFrontend: frontend.on_quit
07-29 10:32 DEBUG  root: application.on_quit
07-29 10:32 INFO   root: sys.exit
07-29 10:47 INFO   root: === wubi 12.04 rev265 ===
07-29 10:47 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-29 10:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
07-29 10:47 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\data
07-29 10:47 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\bin\7z.exe
07-29 10:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-29 10:47 DEBUG  CommonBackend: Fetching basic info...
07-29 10:47 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
07-29 10:47 DEBUG  CommonBackend: platform=win32
07-29 10:47 DEBUG  CommonBackend: osname=nt
07-29 10:47 DEBUG  CommonBackend: language=en_US
07-29 10:47 DEBUG  CommonBackend: encoding=cp932
07-29 10:47 DEBUG  WindowsBackend: arch=amd64
07-29 10:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\data\isolist.ini
07-29 10:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-29 10:47 DEBUG  WindowsBackend: Fetching host info...
07-29 10:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-29 10:47 DEBUG  WindowsBackend: windows version=vista
07-29 10:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-29 10:47 DEBUG  WindowsBackend: windows_sp=None
07-29 10:47 DEBUG  WindowsBackend: windows_build=7600
07-29 10:47 DEBUG  WindowsBackend: gmt=-8
07-29 10:47 DEBUG  WindowsBackend: country=US
07-29 10:47 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-29 10:47 DEBUG  WindowsBackend: windows_username=Brad
07-29 10:47 DEBUG  WindowsBackend: user_full_name=Brad
07-29 10:47 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-29 10:47 DEBUG  WindowsBackend: windows_language_code=1033
07-29 10:47 DEBUG  WindowsBackend: windows_language=English
07-29 10:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-29 10:47 DEBUG  WindowsBackend: bootloader=vista
07-29 10:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 285631.84375 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(C: hd 285631.84375 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-29 10:47 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-29 10:47 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-29 10:47 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-29 10:47 DEBUG  WindowsBackend: keyboard_id=67699721
07-29 10:47 DEBUG  WindowsBackend: keyboard_layout=us
07-29 10:47 DEBUG  WindowsBackend: keyboard_variant=
07-29 10:47 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-29 10:47 DEBUG  CommonBackend: locale=en_US.UTF-8
07-29 10:47 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-29 10:47 DEBUG  CommonBackend: Searching ISOs on USB devices
07-29 10:47 DEBUG  CommonBackend: Searching for local CDs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD854.tmp is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-29 10:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-29 10:47 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-29 10:47 INFO   root: Running the uninstaller...
07-29 10:47 INFO   CommonBackend: This is the uninstaller running
07-29 10:47 DEBUG  WindowsFrontend: __init__...
07-29 10:47 DEBUG  WindowsFrontend: on_init...
07-29 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\translations, languages=['en_US', 'en']
07-29 10:47 INFO   root: Received settings
07-29 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\translations, languages=['en_US', 'en']
07-29 10:47 DEBUG  TaskList: # Running tasklist...
07-29 10:47 DEBUG  TaskList: ## Running Remove bootloader entry...
07-29 10:47 DEBUG  WindowsBackend: Removing bcd entry {76cd50ac-c7e9-11e1-ac33-be1aa438bbbf}
07-29 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
07-29 10:47 DEBUG  WindowsBackend: undo_bootini C:
07-29 10:47 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 285631.84375 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: undo_bootini D:
07-29 10:47 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: undo_bootini E:
07-29 10:47 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 10219.8867188 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: undo_bootini F:
07-29 10:47 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230858.910156 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: undo_bootini H:
07-29 10:47 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 15951.4921875 mb free ntfs)
07-29 10:47 DEBUG  TaskList: ## Finished Remove bootloader entry
07-29 10:47 DEBUG  TaskList: ## Running Remove target dir...
07-29 10:47 DEBUG  CommonBackend: Deleting C:\ubuntu
07-29 10:47 DEBUG  TaskList: ## Finished Remove target dir
07-29 10:47 DEBUG  TaskList: ## Running Remove registry key...
07-29 10:47 DEBUG  TaskList: ## Finished Remove registry key
07-29 10:47 DEBUG  TaskList: # Finished tasklist
07-29 10:47 INFO   root: Almost finished uninstalling
07-29 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD854.tmp\translations, languages=['en_US', 'en']
07-29 10:47 INFO   root: Finished uninstallation
07-29 10:47 DEBUG  root: application.quit
07-29 10:47 DEBUG  WindowsFrontend: frontend.quit
07-29 10:47 DEBUG  WindowsFrontend: frontend.on_quit
07-29 10:47 DEBUG  root: application.on_quit
07-29 10:47 INFO   root: sys.exit
07-29 10:47 INFO   root: === wubi 12.04 rev265 ===
07-29 10:47 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-29 10:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
07-29 10:47 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\data
07-29 10:47 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\bin\7z.exe
07-29 10:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-29 10:47 DEBUG  CommonBackend: Fetching basic info...
07-29 10:47 DEBUG  CommonBackend: original_exe=I:\wubi.exe
07-29 10:47 DEBUG  CommonBackend: platform=win32
07-29 10:47 DEBUG  CommonBackend: osname=nt
07-29 10:47 DEBUG  CommonBackend: language=en_US
07-29 10:47 DEBUG  CommonBackend: encoding=cp932
07-29 10:47 DEBUG  WindowsBackend: arch=amd64
07-29 10:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\data\isolist.ini
07-29 10:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-29 10:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-29 10:47 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-29 10:47 DEBUG  WindowsBackend: Fetching host info...
07-29 10:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-29 10:47 DEBUG  WindowsBackend: windows version=vista
07-29 10:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-29 10:47 DEBUG  WindowsBackend: windows_sp=None
07-29 10:47 DEBUG  WindowsBackend: windows_build=7600
07-29 10:47 DEBUG  WindowsBackend: gmt=-8
07-29 10:47 DEBUG  WindowsBackend: country=US
07-29 10:47 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-29 10:47 DEBUG  WindowsBackend: windows_username=Brad
07-29 10:47 DEBUG  WindowsBackend: user_full_name=Brad
07-29 10:47 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-29 10:47 DEBUG  WindowsBackend: windows_language_code=1033
07-29 10:47 DEBUG  WindowsBackend: windows_language=English
07-29 10:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-29 10:47 DEBUG  WindowsBackend: bootloader=vista
07-29 10:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 286357.890625 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(C: hd 286357.890625 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-29 10:47 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-29 10:47 DEBUG  WindowsBackend: uninstaller_path=None
07-29 10:47 DEBUG  WindowsBackend: previous_target_dir=None
07-29 10:47 DEBUG  WindowsBackend: previous_distro_name=None
07-29 10:47 DEBUG  WindowsBackend: keyboard_id=67699721
07-29 10:47 DEBUG  WindowsBackend: keyboard_layout=us
07-29 10:47 DEBUG  WindowsBackend: keyboard_variant=
07-29 10:47 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-29 10:47 DEBUG  CommonBackend: locale=en_US.UTF-8
07-29 10:47 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-29 10:47 DEBUG  CommonBackend: Searching ISOs on USB devices
07-29 10:47 DEBUG  CommonBackend: Searching for local CDs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-29 10:47 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-29 10:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-29 10:47 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-29 10:47 INFO   root: Running the CD menu...
07-29 10:47 DEBUG  WindowsFrontend: __init__...
07-29 10:47 DEBUG  WindowsFrontend: on_init...
07-29 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\translations, languages=['en_US', 'en']
07-29 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl89E7.tmp\translations, languages=['en_US', 'en']
07-29 10:47 INFO   root: CD menu finished
07-29 10:47 INFO   root: Rebooting
07-29 10:47 DEBUG  TaskList: # Running tasklist...
07-29 10:47 DEBUG  TaskList: ## Running reboot...
07-29 10:47 DEBUG  TaskList: ## Finished reboot
07-29 10:47 DEBUG  TaskList: # Finished tasklist
07-29 10:47 DEBUG  root: application.quit
07-29 10:47 DEBUG  WindowsFrontend: frontend.quit
07-29 10:47 DEBUG  WindowsFrontend: frontend.on_quit
07-29 10:47 DEBUG  root: application.on_quit
07-29 10:47 INFO   root: sys.exit
07-29 10:49 INFO   root: === wubi 12.04 rev265 ===
07-29 10:49 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-29 10:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
07-29 10:49 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\data
07-29 10:49 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\bin\7z.exe
07-29 10:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-29 10:49 DEBUG  CommonBackend: Fetching basic info...
07-29 10:49 DEBUG  CommonBackend: original_exe=I:\wubi.exe
07-29 10:49 DEBUG  CommonBackend: platform=win32
07-29 10:49 DEBUG  CommonBackend: osname=nt
07-29 10:49 DEBUG  CommonBackend: language=en_US
07-29 10:49 DEBUG  CommonBackend: encoding=cp932
07-29 10:49 DEBUG  WindowsBackend: arch=amd64
07-29 10:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\data\isolist.ini
07-29 10:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-29 10:49 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-29 10:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-29 10:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-29 10:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-29 10:49 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-29 10:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-29 10:49 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-29 10:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-29 10:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-29 10:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-29 10:49 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-29 10:49 DEBUG  WindowsBackend: Fetching host info...
07-29 10:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-29 10:49 DEBUG  WindowsBackend: windows version=vista
07-29 10:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-29 10:49 DEBUG  WindowsBackend: windows_sp=None
07-29 10:49 DEBUG  WindowsBackend: windows_build=7600
07-29 10:49 DEBUG  WindowsBackend: gmt=-8
07-29 10:49 DEBUG  WindowsBackend: country=US
07-29 10:49 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-29 10:49 DEBUG  WindowsBackend: windows_username=Brad
07-29 10:49 DEBUG  WindowsBackend: user_full_name=Brad
07-29 10:49 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-29 10:49 DEBUG  WindowsBackend: windows_language_code=1033
07-29 10:49 DEBUG  WindowsBackend: windows_language=English
07-29 10:49 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-29 10:49 DEBUG  WindowsBackend: bootloader=vista
07-29 10:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 286352.152344 mb free ntfs)
07-29 10:49 DEBUG  WindowsBackend: drive=Drive(C: hd 286352.15625 mb free ntfs)
07-29 10:49 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:49 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-29 10:49 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-29 10:49 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-29 10:49 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-29 10:49 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-29 10:49 DEBUG  WindowsBackend: uninstaller_path=None
07-29 10:49 DEBUG  WindowsBackend: previous_target_dir=None
07-29 10:49 DEBUG  WindowsBackend: previous_distro_name=None
07-29 10:49 DEBUG  WindowsBackend: keyboard_id=67699721
07-29 10:49 DEBUG  WindowsBackend: keyboard_layout=us
07-29 10:49 DEBUG  WindowsBackend: keyboard_variant=
07-29 10:49 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-29 10:49 DEBUG  CommonBackend: locale=en_US.UTF-8
07-29 10:49 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-29 10:49 DEBUG  CommonBackend: Searching ISOs on USB devices
07-29 10:49 DEBUG  CommonBackend: Searching for local CDs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-29 10:49 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-29 10:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-29 10:49 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-29 10:49 INFO   root: Running the CD menu...
07-29 10:49 DEBUG  WindowsFrontend: __init__...
07-29 10:49 DEBUG  WindowsFrontend: on_init...
07-29 10:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\translations, languages=['en_US', 'en']
07-29 10:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD6CE.tmp\translations, languages=['en_US', 'en']
07-29 10:49 INFO   root: CD menu finished
07-29 10:49 INFO   root: Rebooting
07-29 10:49 DEBUG  TaskList: # Running tasklist...
07-29 10:49 DEBUG  TaskList: ## Running reboot...
07-29 10:49 DEBUG  TaskList: ## Finished reboot
07-29 10:49 DEBUG  TaskList: # Finished tasklist
07-29 10:49 DEBUG  root: application.quit
07-29 10:49 DEBUG  WindowsFrontend: frontend.quit
07-29 10:49 DEBUG  WindowsFrontend: frontend.on_quit
07-29 10:49 DEBUG  root: application.on_quit
07-29 10:49 INFO   root: sys.exit
07-29 10:52 INFO   root: === wubi 12.04 rev265 ===
07-29 10:52 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-29 10:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
07-29 10:52 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\data
07-29 10:52 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\bin\7z.exe
07-29 10:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-29 10:52 DEBUG  CommonBackend: Fetching basic info...
07-29 10:52 DEBUG  CommonBackend: original_exe=I:\wubi.exe
07-29 10:52 DEBUG  CommonBackend: platform=win32
07-29 10:52 DEBUG  CommonBackend: osname=nt
07-29 10:52 DEBUG  CommonBackend: language=en_US
07-29 10:52 DEBUG  CommonBackend: encoding=cp932
07-29 10:52 DEBUG  WindowsBackend: arch=amd64
07-29 10:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\data\isolist.ini
07-29 10:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-29 10:52 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-29 10:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-29 10:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-29 10:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-29 10:52 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-29 10:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-29 10:52 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-29 10:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-29 10:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-29 10:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-29 10:52 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-29 10:52 DEBUG  WindowsBackend: Fetching host info...
07-29 10:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-29 10:52 DEBUG  WindowsBackend: windows version=vista
07-29 10:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-29 10:52 DEBUG  WindowsBackend: windows_sp=None
07-29 10:52 DEBUG  WindowsBackend: windows_build=7600
07-29 10:52 DEBUG  WindowsBackend: gmt=-8
07-29 10:52 DEBUG  WindowsBackend: country=US
07-29 10:52 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-29 10:52 DEBUG  WindowsBackend: windows_username=Brad
07-29 10:52 DEBUG  WindowsBackend: user_full_name=Brad
07-29 10:52 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-29 10:52 DEBUG  WindowsBackend: windows_language_code=1033
07-29 10:52 DEBUG  WindowsBackend: windows_language=English
07-29 10:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-29 10:52 DEBUG  WindowsBackend: bootloader=vista
07-29 10:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 286355.59375 mb free ntfs)
07-29 10:52 DEBUG  WindowsBackend: drive=Drive(C: hd 286355.59375 mb free ntfs)
07-29 10:52 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-29 10:52 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-29 10:52 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-29 10:52 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-29 10:52 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-29 10:52 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-29 10:52 DEBUG  WindowsBackend: uninstaller_path=None
07-29 10:52 DEBUG  WindowsBackend: previous_target_dir=None
07-29 10:52 DEBUG  WindowsBackend: previous_distro_name=None
07-29 10:52 DEBUG  WindowsBackend: keyboard_id=67699721
07-29 10:52 DEBUG  WindowsBackend: keyboard_layout=us
07-29 10:52 DEBUG  WindowsBackend: keyboard_variant=
07-29 10:52 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-29 10:52 DEBUG  CommonBackend: locale=en_US.UTF-8
07-29 10:52 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-29 10:52 DEBUG  CommonBackend: Searching ISOs on USB devices
07-29 10:52 DEBUG  CommonBackend: Searching for local CDs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-29 10:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 10:52 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-29 10:52 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-29 10:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-29 10:52 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-29 10:52 INFO   root: Running the CD menu...
07-29 10:52 DEBUG  WindowsFrontend: __init__...
07-29 10:52 DEBUG  WindowsFrontend: on_init...
07-29 10:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\translations, languages=['en_US', 'en']
07-29 10:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl50DD.tmp\translations, languages=['en_US', 'en']
07-29 10:52 INFO   WindowsFrontend: Operation cancelled
07-29 10:52 DEBUG  WindowsFrontend: frontend.quit
07-29 10:52 DEBUG  WindowsFrontend: frontend.on_quit
07-29 10:52 DEBUG  root: application.on_quit
07-29 10:52 INFO   root: sys.exit
07-30 05:24 INFO   root: === wubi 12.04 rev265 ===
07-30 05:24 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-30 05:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-30 05:24 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\data
07-30 05:24 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\bin\7z.exe
07-30 05:24 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 05:24 DEBUG  CommonBackend: Fetching basic info...
07-30 05:24 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-30 05:24 DEBUG  CommonBackend: platform=win32
07-30 05:24 DEBUG  CommonBackend: osname=nt
07-30 05:24 DEBUG  CommonBackend: language=en_US
07-30 05:24 DEBUG  CommonBackend: encoding=cp932
07-30 05:24 DEBUG  WindowsBackend: arch=amd64
07-30 05:24 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\data\isolist.ini
07-30 05:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 05:24 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-30 05:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 05:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 05:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 05:24 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-30 05:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 05:24 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-30 05:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 05:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 05:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 05:24 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-30 05:24 DEBUG  WindowsBackend: Fetching host info...
07-30 05:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 05:24 DEBUG  WindowsBackend: windows version=vista
07-30 05:24 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-30 05:24 DEBUG  WindowsBackend: windows_sp=None
07-30 05:24 DEBUG  WindowsBackend: windows_build=7600
07-30 05:24 DEBUG  WindowsBackend: gmt=-8
07-30 05:24 DEBUG  WindowsBackend: country=US
07-30 05:24 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-30 05:24 DEBUG  WindowsBackend: windows_username=Brad
07-30 05:24 DEBUG  WindowsBackend: user_full_name=Brad
07-30 05:24 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-30 05:24 DEBUG  WindowsBackend: windows_language_code=1033
07-30 05:24 DEBUG  WindowsBackend: windows_language=English
07-30 05:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-30 05:24 DEBUG  WindowsBackend: bootloader=vista
07-30 05:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 285496.28125 mb free ntfs)
07-30 05:24 DEBUG  WindowsBackend: drive=Drive(C: hd 285496.28125 mb free ntfs)
07-30 05:24 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-30 05:24 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-30 05:24 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-30 05:24 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-30 05:24 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-30 05:24 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-30 05:24 DEBUG  WindowsBackend: uninstaller_path=None
07-30 05:24 DEBUG  WindowsBackend: previous_target_dir=None
07-30 05:24 DEBUG  WindowsBackend: previous_distro_name=None
07-30 05:24 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 05:24 DEBUG  WindowsBackend: keyboard_layout=us
07-30 05:24 DEBUG  WindowsBackend: keyboard_variant=
07-30 05:24 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-30 05:24 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 05:24 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-30 05:24 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 05:24 DEBUG  CommonBackend: Searching for local CDs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-30 05:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-30 05:24 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-30 05:24 INFO   root: Running the installer...
07-30 05:24 DEBUG  WindowsFrontend: __init__...
07-30 05:24 DEBUG  WindowsFrontend: on_init...
07-30 05:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\translations, languages=['en_US', 'en']
07-30 05:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\translations, languages=['en_US', 'en']
07-30 05:24 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brad
07-30 05:24 INFO   root: Received settings
07-30 05:24 DEBUG  CommonBackend: Searching for local CD
07-30 05:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 05:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:24 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-30 05:24 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-30 05:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\translations, languages=['en_US', 'en']
07-30 05:24 DEBUG  TaskList: # Running tasklist...
07-30 05:24 DEBUG  TaskList: ## Running select_target_dir...
07-30 05:24 INFO   WindowsBackend: Installing into E:\ubuntu
07-30 05:24 DEBUG  TaskList: ## Finished select_target_dir
07-30 05:24 DEBUG  TaskList: ## Running create_dir_structure...
07-30 05:24 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-30 05:24 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-30 05:24 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-30 05:24 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-30 05:24 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-30 05:24 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-30 05:24 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-30 05:24 DEBUG  TaskList: ## Finished create_dir_structure
07-30 05:24 DEBUG  TaskList: ## Running uncompress_target_dir...
07-30 05:24 DEBUG  TaskList: ## Finished uncompress_target_dir
07-30 05:24 DEBUG  TaskList: ## Running create_uninstaller...
07-30 05:24 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-30 05:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-30 05:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-30 05:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-30 05:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-30 05:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-30 05:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-30 05:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-30 05:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-30 05:24 DEBUG  TaskList: ## Finished create_uninstaller
07-30 05:24 DEBUG  TaskList: ## Running copy_installation_files...
07-30 05:24 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-30 05:24 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\winboot -> E:\ubuntu\winboot
07-30 05:24 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-30 05:24 DEBUG  TaskList: ## Finished copy_installation_files
07-30 05:24 DEBUG  TaskList: ## Running get_iso...
07-30 05:24 DEBUG  TaskList: New task copy_file
07-30 05:24 DEBUG  TaskList: ### Running copy_file...
07-30 05:25 DEBUG  TaskList: ### Finished copy_file
07-30 05:25 DEBUG  TaskList: New task check_iso
07-30 05:25 DEBUG  TaskList: ### Running check_iso...
07-30 05:25 DEBUG  CommonBackend: Checking E:\ubuntu\install\installation.iso
07-30 05:25 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\installation.iso
07-30 05:25 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\installation.iso
07-30 05:25 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-30 05:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-30 05:25 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu\install\installation.iso
07-30 05:25 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
07-30 05:25 DEBUG  TaskList: New task get_metalink
07-30 05:25 DEBUG  TaskList: #### Running get_metalink...
07-30 05:25 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink > E:\ubuntu\install
07-30 05:25 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
07-30 05:25 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.metalink > E:\ubuntu\install
07-30 05:25 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
07-30 05:25 DEBUG  TaskList: #### Finished get_metalink
07-30 05:25 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for E:\ubuntu\install\installation.iso, ignoring
07-30 05:25 DEBUG  TaskList: ### Finished check_iso
07-30 05:25 DEBUG  TaskList: ## Finished get_iso
07-30 05:25 DEBUG  TaskList: ## Running extract_kernel...
07-30 05:25 DEBUG  CommonBackend: Copying files from CD I:\
07-30 05:25 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-30 05:25 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\vmlinuz
07-30 05:25 DEBUG  CommonBackend:   E:\ubuntu\install\boot\vmlinuz md5 = 0fb4d79f5f23cba37cf40ef017bb3c65 == 0fb4d79f5f23cba37cf40ef017bb3c65
07-30 05:25 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\initrd.lz
07-30 05:25 DEBUG  CommonBackend:   E:\ubuntu\install\boot\initrd.lz md5 = f5112034765ef7db4c2ebcf2ea409ecf == f5112034765ef7db4c2ebcf2ea409ecf
07-30 05:25 DEBUG  TaskList: ## Finished extract_kernel
07-30 05:25 DEBUG  TaskList: ## Running choose_disk_sizes...
07-30 05:25 DEBUG  WindowsBackend: total size=8000
  root=7744
  swap=256
  home=0
  usr=0
07-30 05:25 DEBUG  TaskList: ## Finished choose_disk_sizes
07-30 05:25 DEBUG  TaskList: ## Running create_preseed...
07-30 05:25 DEBUG  TaskList: ## Finished create_preseed
07-30 05:25 DEBUG  TaskList: ## Running modify_bootloader...
07-30 05:25 DEBUG  TaskList: New task modify_bcd
07-30 05:25 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:25 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 285496.28125 mb free ntfs)
07-30 05:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {76cd50ad-c7e9-11e1-ac33-be1aa438bbbf}
07-30 05:25 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:25 DEBUG  TaskList: New task modify_bcd
07-30 05:25 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:25 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 24874.9101563 mb free ntfs)
07-30 05:25 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:25 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:25 DEBUG  TaskList: New task modify_bcd
07-30 05:25 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:25 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 10219.8867188 mb free ntfs)
07-30 05:25 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:25 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:25 DEBUG  TaskList: New task modify_bcd
07-30 05:25 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:25 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 230858.910156 mb free ntfs)
07-30 05:25 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:25 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:25 DEBUG  TaskList: New task modify_bcd
07-30 05:25 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:25 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 15951.4921875 mb free ntfs)
07-30 05:25 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:25 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:25 DEBUG  TaskList: ## Finished modify_bootloader
07-30 05:25 DEBUG  TaskList: ## Running modify_grub_configuration...
07-30 05:25 DEBUG  TaskList: ## Finished modify_grub_configuration
07-30 05:25 DEBUG  TaskList: ## Running create_virtual_disks...
07-30 05:25 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\root.disk of 7744MB
07-30 05:25 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\swap.disk of 256MB
07-30 05:25 DEBUG  TaskList: ## Finished create_virtual_disks
07-30 05:25 DEBUG  TaskList: ## Running uncompress_files...
07-30 05:25 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot /U /A /F
07-30 05:25 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot\*.* /U /A /F
07-30 05:25 DEBUG  TaskList: ## Finished uncompress_files
07-30 05:25 DEBUG  TaskList: ## Running eject_cd...
07-30 05:25 DEBUG  TaskList: ## Finished eject_cd
07-30 05:25 DEBUG  TaskList: # Finished tasklist
07-30 05:25 INFO   root: Almost finished installing
07-30 05:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylBBFF.tmp\translations, languages=['en_US', 'en']
07-30 05:26 INFO   root: Finished installation
07-30 05:26 INFO   root: Rebooting
07-30 05:26 DEBUG  TaskList: # Running tasklist...
07-30 05:26 DEBUG  TaskList: ## Running reboot...
07-30 05:26 DEBUG  TaskList: ## Finished reboot
07-30 05:26 DEBUG  TaskList: # Finished tasklist
07-30 05:26 DEBUG  root: application.quit
07-30 05:26 DEBUG  WindowsFrontend: frontend.quit
07-30 05:26 DEBUG  WindowsFrontend: frontend.on_quit
07-30 05:26 DEBUG  root: application.on_quit
07-30 05:26 INFO   root: sys.exit
07-30 05:43 INFO   root: === wubi 12.04 rev265 ===
07-30 05:43 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-30 05:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-30 05:43 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\data
07-30 05:43 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\bin\7z.exe
07-30 05:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 05:43 DEBUG  CommonBackend: Fetching basic info...
07-30 05:43 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-30 05:43 DEBUG  CommonBackend: platform=win32
07-30 05:43 DEBUG  CommonBackend: osname=nt
07-30 05:43 DEBUG  CommonBackend: language=en_US
07-30 05:43 DEBUG  CommonBackend: encoding=cp932
07-30 05:43 DEBUG  WindowsBackend: arch=amd64
07-30 05:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\data\isolist.ini
07-30 05:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 05:43 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-30 05:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 05:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 05:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 05:43 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-30 05:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 05:43 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-30 05:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 05:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 05:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 05:43 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-30 05:43 DEBUG  WindowsBackend: Fetching host info...
07-30 05:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 05:43 DEBUG  WindowsBackend: windows version=vista
07-30 05:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-30 05:43 DEBUG  WindowsBackend: windows_sp=None
07-30 05:43 DEBUG  WindowsBackend: windows_build=7600
07-30 05:43 DEBUG  WindowsBackend: gmt=-8
07-30 05:43 DEBUG  WindowsBackend: country=US
07-30 05:43 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-30 05:43 DEBUG  WindowsBackend: windows_username=Brad
07-30 05:43 DEBUG  WindowsBackend: user_full_name=Brad
07-30 05:43 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-30 05:43 DEBUG  WindowsBackend: windows_language_code=1033
07-30 05:43 DEBUG  WindowsBackend: windows_language=English
07-30 05:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-30 05:43 DEBUG  WindowsBackend: bootloader=vista
07-30 05:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 285478.21875 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: drive=Drive(C: hd 285478.21875 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.890625 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-30 05:43 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-30 05:43 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-30 05:43 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-30 05:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-30 05:43 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 05:43 DEBUG  WindowsBackend: keyboard_layout=us
07-30 05:43 DEBUG  WindowsBackend: keyboard_variant=
07-30 05:43 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-30 05:43 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 05:43 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-30 05:43 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 05:43 DEBUG  CommonBackend: Searching for local CDs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-30 05:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-30 05:43 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-30 05:43 INFO   root: Running the installer...
07-30 05:43 DEBUG  WindowsFrontend: __init__...
07-30 05:43 DEBUG  WindowsFrontend: on_init...
07-30 05:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\translations, languages=['en_US', 'en']
07-30 05:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\translations, languages=['en_US', 'en']
07-30 05:43 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brad
07-30 05:43 INFO   root: Received settings
07-30 05:43 DEBUG  CommonBackend: Searching for local CD
07-30 05:43 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 05:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-30 05:43 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-30 05:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\translations, languages=['en_US', 'en']
07-30 05:43 DEBUG  TaskList: # Running tasklist...
07-30 05:43 DEBUG  TaskList: ## Running select_target_dir...
07-30 05:43 INFO   WindowsBackend: Installing into E:\ubuntu
07-30 05:43 DEBUG  TaskList: ## Finished select_target_dir
07-30 05:43 DEBUG  TaskList: ## Running create_dir_structure...
07-30 05:43 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-30 05:43 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-30 05:43 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-30 05:43 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-30 05:43 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-30 05:43 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-30 05:43 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-30 05:43 DEBUG  TaskList: ## Finished create_dir_structure
07-30 05:43 DEBUG  TaskList: ## Running uncompress_target_dir...
07-30 05:43 DEBUG  TaskList: ## Finished uncompress_target_dir
07-30 05:43 DEBUG  TaskList: ## Running create_uninstaller...
07-30 05:43 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-30 05:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-30 05:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-30 05:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-30 05:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-30 05:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-30 05:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-30 05:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-30 05:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-30 05:43 DEBUG  TaskList: ## Finished create_uninstaller
07-30 05:43 DEBUG  TaskList: ## Running copy_installation_files...
07-30 05:43 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-30 05:43 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\winboot -> E:\ubuntu\winboot
07-30 05:43 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-30 05:43 DEBUG  TaskList: ## Finished copy_installation_files
07-30 05:43 DEBUG  TaskList: ## Running get_iso...
07-30 05:43 DEBUG  TaskList: New task copy_file
07-30 05:43 DEBUG  TaskList: ### Running copy_file...
07-30 05:43 DEBUG  TaskList: ### Finished copy_file
07-30 05:43 DEBUG  TaskList: New task check_iso
07-30 05:43 DEBUG  TaskList: ### Running check_iso...
07-30 05:43 DEBUG  CommonBackend: Checking E:\ubuntu\install\installation.iso
07-30 05:43 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\installation.iso
07-30 05:43 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\installation.iso
07-30 05:43 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-30 05:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-30 05:43 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu\install\installation.iso
07-30 05:43 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
07-30 05:43 DEBUG  TaskList: New task get_metalink
07-30 05:43 DEBUG  TaskList: #### Running get_metalink...
07-30 05:43 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink > E:\ubuntu\install
07-30 05:43 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-12.04-desktop-i386.metalink, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink, basename=ubuntu-12.04-desktop-i386.metalink, length=30559, text=None
07-30 05:43 DEBUG  downloader: download finished (read 30559 bytes)
07-30 05:43 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/MD5SUMS-metalink > E:\ubuntu\install
07-30 05:43 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
07-30 05:43 DEBUG  downloader: download finished (read 419 bytes)
07-30 05:43 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg > E:\ubuntu\install
07-30 05:43 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-30 05:43 DEBUG  downloader: download finished (read 198 bytes)
07-30 05:43 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-30 05:43 INFO   saplog: Checking block bindings..
07-30 05:43 INFO   saplog: Key verified successfully.
07-30 05:43 DEBUG  CommonBackend: metalink md5sums:
1e2a0b0f07bc43ab5924767a9cc03e82  ubuntu-12.04-alternate-amd64.metalink
4413660abc989dbbfe6e4abedc9a3ec1  ubuntu-12.04-alternate-i386.metalink
c29be6d58c1581d9cd679aca25db77d1  ubuntu-12.04-desktop-amd64.metalink
c7a6b99206703cfe37f1da5af1d28e3a  ubuntu-12.04-desktop-i386.metalink
4e44ca9bc7ee8ab54ff9565a5437bdc2  ubuntu-12.04-server-amd64.metalink
c9cfc1dd8c65099d929189eedc157f3c  ubuntu-12.04-server-i386.metalink

07-30 05:43 DEBUG  TaskList: #### Finished get_metalink
07-30 05:43 DEBUG  TaskList: New task get_file_md5
07-30 05:43 DEBUG  TaskList: #### Running get_file_md5...
07-30 05:43 DEBUG  TaskList: #### Finished get_file_md5
07-30 05:43 DEBUG  TaskList: ### Finished check_iso
07-30 05:43 DEBUG  TaskList: ## Finished get_iso
07-30 05:43 DEBUG  TaskList: ## Running extract_kernel...
07-30 05:43 DEBUG  CommonBackend: Copying files from CD I:\
07-30 05:43 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-30 05:43 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\vmlinuz
07-30 05:43 DEBUG  CommonBackend:   E:\ubuntu\install\boot\vmlinuz md5 = 0fb4d79f5f23cba37cf40ef017bb3c65 == 0fb4d79f5f23cba37cf40ef017bb3c65
07-30 05:43 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\initrd.lz
07-30 05:43 DEBUG  CommonBackend:   E:\ubuntu\install\boot\initrd.lz md5 = f5112034765ef7db4c2ebcf2ea409ecf == f5112034765ef7db4c2ebcf2ea409ecf
07-30 05:43 DEBUG  TaskList: ## Finished extract_kernel
07-30 05:43 DEBUG  TaskList: ## Running choose_disk_sizes...
07-30 05:43 DEBUG  WindowsBackend: total size=7000
  root=6744
  swap=256
  home=0
  usr=0
07-30 05:43 DEBUG  TaskList: ## Finished choose_disk_sizes
07-30 05:43 DEBUG  TaskList: ## Running create_preseed...
07-30 05:43 DEBUG  TaskList: ## Finished create_preseed
07-30 05:43 DEBUG  TaskList: ## Running modify_bootloader...
07-30 05:43 DEBUG  TaskList: New task modify_bcd
07-30 05:43 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:43 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 285478.21875 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:43 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:43 DEBUG  TaskList: New task modify_bcd
07-30 05:43 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:43 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 24874.9101563 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:43 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:43 DEBUG  TaskList: New task modify_bcd
07-30 05:43 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:43 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 10219.890625 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:43 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:43 DEBUG  TaskList: New task modify_bcd
07-30 05:43 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:43 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 230858.910156 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:43 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:43 DEBUG  TaskList: New task modify_bcd
07-30 05:43 DEBUG  TaskList: ### Running modify_bcd...
07-30 05:43 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 15951.4921875 mb free ntfs)
07-30 05:43 DEBUG  WindowsBackend: BCD has already been modified
07-30 05:43 DEBUG  TaskList: ### Finished modify_bcd
07-30 05:43 DEBUG  TaskList: ## Finished modify_bootloader
07-30 05:43 DEBUG  TaskList: ## Running modify_grub_configuration...
07-30 05:43 DEBUG  TaskList: ## Finished modify_grub_configuration
07-30 05:43 DEBUG  TaskList: ## Running create_virtual_disks...
07-30 05:43 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\root.disk of 6744MB
07-30 05:43 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\swap.disk of 256MB
07-30 05:43 DEBUG  TaskList: ## Finished create_virtual_disks
07-30 05:43 DEBUG  TaskList: ## Running uncompress_files...
07-30 05:43 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot /U /A /F
07-30 05:43 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot\*.* /U /A /F
07-30 05:43 DEBUG  TaskList: ## Finished uncompress_files
07-30 05:43 DEBUG  TaskList: ## Running eject_cd...
07-30 05:43 DEBUG  TaskList: ## Finished eject_cd
07-30 05:43 DEBUG  TaskList: # Finished tasklist
07-30 05:43 INFO   root: Almost finished installing
07-30 05:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl581E.tmp\translations, languages=['en_US', 'en']
07-30 05:43 INFO   root: Finished installation
07-30 05:43 INFO   root: Rebooting
07-30 05:43 DEBUG  TaskList: # Running tasklist...
07-30 05:43 DEBUG  TaskList: ## Running reboot...
07-30 05:43 DEBUG  TaskList: ## Finished reboot
07-30 05:43 DEBUG  TaskList: # Finished tasklist
07-30 05:43 DEBUG  root: application.quit
07-30 05:43 DEBUG  WindowsFrontend: frontend.quit
07-30 05:43 DEBUG  WindowsFrontend: frontend.on_quit
07-30 05:43 DEBUG  root: application.on_quit
07-30 05:43 INFO   root: sys.exit
07-30 05:49 INFO   root: === wubi 12.04 rev265 ===
07-30 05:49 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-30 05:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
07-30 05:49 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\data
07-30 05:49 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\bin\7z.exe
07-30 05:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 05:49 DEBUG  CommonBackend: Fetching basic info...
07-30 05:49 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
07-30 05:49 DEBUG  CommonBackend: platform=win32
07-30 05:49 DEBUG  CommonBackend: osname=nt
07-30 05:49 DEBUG  CommonBackend: language=en_US
07-30 05:49 DEBUG  CommonBackend: encoding=cp932
07-30 05:49 DEBUG  WindowsBackend: arch=amd64
07-30 05:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\data\isolist.ini
07-30 05:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 05:49 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-30 05:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 05:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 05:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 05:49 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-30 05:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 05:49 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-30 05:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 05:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 05:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 05:49 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-30 05:49 DEBUG  WindowsBackend: Fetching host info...
07-30 05:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 05:49 DEBUG  WindowsBackend: windows version=vista
07-30 05:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-30 05:49 DEBUG  WindowsBackend: windows_sp=None
07-30 05:49 DEBUG  WindowsBackend: windows_build=7600
07-30 05:49 DEBUG  WindowsBackend: gmt=-8
07-30 05:49 DEBUG  WindowsBackend: country=US
07-30 05:49 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-30 05:49 DEBUG  WindowsBackend: windows_username=Brad
07-30 05:49 DEBUG  WindowsBackend: user_full_name=Brad
07-30 05:49 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-30 05:49 DEBUG  WindowsBackend: windows_language_code=1033
07-30 05:49 DEBUG  WindowsBackend: windows_language=English
07-30 05:49 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-30 05:49 DEBUG  WindowsBackend: bootloader=vista
07-30 05:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 285508.203125 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: drive=Drive(C: hd 285508.203125 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: drive=Drive(E: hd 2496.97265625 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
07-30 05:49 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-30 05:49 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-30 05:49 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-30 05:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-30 05:49 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 05:49 DEBUG  WindowsBackend: keyboard_layout=us
07-30 05:49 DEBUG  WindowsBackend: keyboard_variant=
07-30 05:49 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-30 05:49 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 05:49 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-30 05:49 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 05:49 DEBUG  CommonBackend: Searching for local CDs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-30 05:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-30 05:49 DEBUG  Distro: wrong version: 9.10 != 12.04
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro: wrong version: 9.10 != 12.04
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-30 05:49 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 05:49 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 05:49 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-30 05:49 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-30 05:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-30 05:49 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-30 05:49 INFO   root: Running the uninstaller...
07-30 05:49 INFO   CommonBackend: This is the uninstaller running
07-30 05:49 DEBUG  WindowsFrontend: __init__...
07-30 05:49 DEBUG  WindowsFrontend: on_init...
07-30 05:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\translations, languages=['en_US', 'en']
07-30 05:49 INFO   root: Received settings
07-30 05:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\translations, languages=['en_US', 'en']
07-30 05:49 DEBUG  TaskList: # Running tasklist...
07-30 05:49 DEBUG  TaskList: ## Running Remove bootloader entry...
07-30 05:49 DEBUG  WindowsBackend: Removing bcd entry {76cd50ad-c7e9-11e1-ac33-be1aa438bbbf}
07-30 05:49 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
07-30 05:49 DEBUG  WindowsBackend: undo_bootini C:
07-30 05:49 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 285508.203125 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: undo_bootini D:
07-30 05:49 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: undo_bootini E:
07-30 05:49 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 2496.97265625 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: undo_bootini F:
07-30 05:49 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230858.910156 mb free ntfs)
07-30 05:49 DEBUG  WindowsBackend: undo_bootini H:
07-30 05:49 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 15951.4921875 mb free ntfs)
07-30 05:49 DEBUG  TaskList: ## Finished Remove bootloader entry
07-30 05:49 DEBUG  TaskList: ## Running Remove target dir...
07-30 05:49 DEBUG  CommonBackend: Deleting E:\ubuntu
07-30 05:49 DEBUG  TaskList: ## Finished Remove target dir
07-30 05:49 DEBUG  TaskList: ## Running Remove registry key...
07-30 05:49 DEBUG  TaskList: ## Finished Remove registry key
07-30 05:49 DEBUG  TaskList: # Finished tasklist
07-30 05:49 INFO   root: Almost finished uninstalling
07-30 05:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA6F8.tmp\translations, languages=['en_US', 'en']
07-30 05:49 INFO   root: Finished uninstallation
07-30 05:49 DEBUG  root: application.quit
07-30 05:49 DEBUG  WindowsFrontend: frontend.quit
07-30 05:49 DEBUG  WindowsFrontend: frontend.on_quit
07-30 05:49 DEBUG  root: application.on_quit
07-30 05:49 INFO   root: sys.exit
07-30 06:02 INFO   root: === wubi 12.04 rev265 ===
07-30 06:02 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-30 06:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-30 06:02 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\data
07-30 06:02 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\bin\7z.exe
07-30 06:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 06:02 DEBUG  CommonBackend: Fetching basic info...
07-30 06:02 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-30 06:02 DEBUG  CommonBackend: platform=win32
07-30 06:02 DEBUG  CommonBackend: osname=nt
07-30 06:02 DEBUG  CommonBackend: language=en_US
07-30 06:02 DEBUG  CommonBackend: encoding=cp932
07-30 06:02 DEBUG  WindowsBackend: arch=amd64
07-30 06:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\data\isolist.ini
07-30 06:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 06:02 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-30 06:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 06:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 06:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 06:02 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-30 06:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 06:02 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-30 06:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 06:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 06:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 06:02 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-30 06:02 DEBUG  WindowsBackend: Fetching host info...
07-30 06:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 06:02 DEBUG  WindowsBackend: windows version=vista
07-30 06:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-30 06:02 DEBUG  WindowsBackend: windows_sp=None
07-30 06:02 DEBUG  WindowsBackend: windows_build=7600
07-30 06:02 DEBUG  WindowsBackend: gmt=-8
07-30 06:02 DEBUG  WindowsBackend: country=US
07-30 06:02 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-30 06:02 DEBUG  WindowsBackend: windows_username=Brad
07-30 06:02 DEBUG  WindowsBackend: user_full_name=Brad
07-30 06:02 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-30 06:02 DEBUG  WindowsBackend: windows_language_code=1033
07-30 06:02 DEBUG  WindowsBackend: windows_language=English
07-30 06:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-30 06:02 DEBUG  WindowsBackend: bootloader=vista
07-30 06:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 284911.140625 mb free ntfs)
07-30 06:02 DEBUG  WindowsBackend: drive=Drive(C: hd 284911.140625 mb free ntfs)
07-30 06:02 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-30 06:02 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-30 06:02 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-30 06:02 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
07-30 06:02 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-30 06:02 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-30 06:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-30 06:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-30 06:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-30 06:02 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 06:02 DEBUG  WindowsBackend: keyboard_layout=us
07-30 06:02 DEBUG  WindowsBackend: keyboard_variant=
07-30 06:02 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-30 06:02 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 06:02 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-30 06:02 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 06:02 DEBUG  CommonBackend: Searching for local CDs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylEBC4.tmp\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-30 06:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-30 06:02 DEBUG  Distro: wrong version: 9.10 != 12.04
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro: wrong version: 9.10 != 12.04
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-30 06:02 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 06:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-30 06:02 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-30 06:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-30 06:02 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-30 06:02 INFO   root: Already installed, running the uninstaller...
07-30 06:02 INFO   root: Running the uninstaller...
07-30 06:02 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
07-30 06:02 DEBUG  root: application.quit
07-30 06:02 DEBUG  root: application.on_quit
07-30 06:02 INFO   root: sys.exit
07-30 06:02 INFO   root: Quitting application
07-30 06:21 INFO   root: === wubi 12.04 rev265 ===
07-30 06:21 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-30 06:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-30 06:21 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\data
07-30 06:21 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\bin\7z.exe
07-30 06:21 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 06:21 DEBUG  CommonBackend: Fetching basic info...
07-30 06:21 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-30 06:21 DEBUG  CommonBackend: platform=win32
07-30 06:21 DEBUG  CommonBackend: osname=nt
07-30 06:21 DEBUG  CommonBackend: language=en_US
07-30 06:21 DEBUG  CommonBackend: encoding=cp932
07-30 06:21 DEBUG  WindowsBackend: arch=amd64
07-30 06:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\data\isolist.ini
07-30 06:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 06:21 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-30 06:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 06:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 06:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 06:21 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-30 06:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 06:21 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-30 06:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 06:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 06:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 06:21 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-30 06:21 DEBUG  WindowsBackend: Fetching host info...
07-30 06:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 06:21 DEBUG  WindowsBackend: windows version=vista
07-30 06:21 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-30 06:21 DEBUG  WindowsBackend: windows_sp=None
07-30 06:21 DEBUG  WindowsBackend: windows_build=7600
07-30 06:21 DEBUG  WindowsBackend: gmt=-8
07-30 06:21 DEBUG  WindowsBackend: country=US
07-30 06:21 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-30 06:21 DEBUG  WindowsBackend: windows_username=Brad
07-30 06:21 DEBUG  WindowsBackend: user_full_name=Brad
07-30 06:21 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-30 06:21 DEBUG  WindowsBackend: windows_language_code=1033
07-30 06:21 DEBUG  WindowsBackend: windows_language=English
07-30 06:21 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-30 06:21 DEBUG  WindowsBackend: bootloader=vista
07-30 06:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 285640.714844 mb free ntfs)
07-30 06:21 DEBUG  WindowsBackend: drive=Drive(C: hd 285640.714844 mb free ntfs)
07-30 06:21 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-30 06:21 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-30 06:21 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-30 06:21 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
07-30 06:21 DEBUG  WindowsBackend: drive=Drive(H: hd 15951.4921875 mb free ntfs)
07-30 06:21 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-30 06:21 DEBUG  WindowsBackend: uninstaller_path=None
07-30 06:21 DEBUG  WindowsBackend: previous_target_dir=None
07-30 06:21 DEBUG  WindowsBackend: previous_distro_name=None
07-30 06:21 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 06:21 DEBUG  WindowsBackend: keyboard_layout=us
07-30 06:21 DEBUG  WindowsBackend: keyboard_variant=
07-30 06:21 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-30 06:21 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 06:21 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-30 06:21 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 06:21 DEBUG  CommonBackend: Searching for local CDs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-30 06:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-30 06:21 DEBUG  Distro: wrong version: 9.10 != 12.04
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro: wrong version: 9.10 != 12.04
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-30 06:21 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-30 06:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-30 06:21 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-30 06:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-30 06:21 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-30 06:21 INFO   root: Running the installer...
07-30 06:21 DEBUG  WindowsFrontend: __init__...
07-30 06:21 DEBUG  WindowsFrontend: on_init...
07-30 06:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\translations, languages=['en_US', 'en']
07-30 06:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\translations, languages=['en_US', 'en']
07-30 06:22 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=5000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brad
07-30 06:22 INFO   root: Received settings
07-30 06:22 DEBUG  CommonBackend: Searching for local CD
07-30 06:22 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF891.tmp is a valid Ubuntu CD
07-30 06:22 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\casper\filesystem.squashfs
07-30 06:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 06:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 06:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 06:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 06:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 06:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 06:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-30 06:22 DEBUG  Distro: wrong version: 9.10 != 12.04
07-30 06:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 06:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 06:22 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-30 06:22 INFO   Distro: Found a valid CD for Ubuntu: I:\
07-30 06:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\translations, languages=['en_US', 'en']
07-30 06:22 DEBUG  TaskList: # Running tasklist...
07-30 06:22 DEBUG  TaskList: ## Running select_target_dir...
07-30 06:22 INFO   WindowsBackend: Installing into E:\ubuntu
07-30 06:22 DEBUG  TaskList: ## Finished select_target_dir
07-30 06:22 DEBUG  TaskList: ## Running create_dir_structure...
07-30 06:22 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-30 06:22 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-30 06:22 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-30 06:22 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-30 06:22 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-30 06:22 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-30 06:22 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-30 06:22 DEBUG  TaskList: ## Finished create_dir_structure
07-30 06:22 DEBUG  TaskList: ## Running uncompress_target_dir...
07-30 06:22 DEBUG  TaskList: ## Finished uncompress_target_dir
07-30 06:22 DEBUG  TaskList: ## Running create_uninstaller...
07-30 06:22 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-30 06:22 DEBUG  TaskList: ## Finished create_uninstaller
07-30 06:22 DEBUG  TaskList: ## Running copy_installation_files...
07-30 06:22 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-30 06:22 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\winboot -> E:\ubuntu\winboot
07-30 06:22 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-30 06:22 DEBUG  TaskList: ## Finished copy_installation_files
07-30 06:22 DEBUG  TaskList: ## Running get_iso...
07-30 06:22 DEBUG  TaskList: New task copy_file
07-30 06:22 DEBUG  TaskList: ### Running copy_file...
07-30 06:22 DEBUG  TaskList: ### Finished copy_file
07-30 06:22 DEBUG  TaskList: New task check_iso
07-30 06:22 DEBUG  TaskList: ### Running check_iso...
07-30 06:22 DEBUG  CommonBackend: Checking E:\ubuntu\install\installation.iso
07-30 06:22 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\installation.iso
07-30 06:22 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\installation.iso
07-30 06:22 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-30 06:22 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-30 06:22 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu\install\installation.iso
07-30 06:22 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
07-30 06:22 DEBUG  TaskList: New task get_metalink
07-30 06:22 DEBUG  TaskList: #### Running get_metalink...
07-30 06:22 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink > E:\ubuntu\install
07-30 06:22 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-12.04-desktop-i386.metalink, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink, basename=ubuntu-12.04-desktop-i386.metalink, length=30559, text=None
07-30 06:22 DEBUG  downloader: download finished (read 30559 bytes)
07-30 06:22 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/MD5SUMS-metalink > E:\ubuntu\install
07-30 06:22 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
07-30 06:22 DEBUG  downloader: download finished (read 419 bytes)
07-30 06:22 DEBUG  downloader: downloading http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg > E:\ubuntu\install
07-30 06:22 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-30 06:22 DEBUG  downloader: download finished (read 198 bytes)
07-30 06:22 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-30 06:22 INFO   saplog: Checking block bindings..
07-30 06:22 INFO   saplog: Key verified successfully.
07-30 06:22 DEBUG  CommonBackend: metalink md5sums:
1e2a0b0f07bc43ab5924767a9cc03e82  ubuntu-12.04-alternate-amd64.metalink
4413660abc989dbbfe6e4abedc9a3ec1  ubuntu-12.04-alternate-i386.metalink
c29be6d58c1581d9cd679aca25db77d1  ubuntu-12.04-desktop-amd64.metalink
c7a6b99206703cfe37f1da5af1d28e3a  ubuntu-12.04-desktop-i386.metalink
4e44ca9bc7ee8ab54ff9565a5437bdc2  ubuntu-12.04-server-amd64.metalink
c9cfc1dd8c65099d929189eedc157f3c  ubuntu-12.04-server-i386.metalink

07-30 06:22 DEBUG  TaskList: #### Finished get_metalink
07-30 06:22 DEBUG  TaskList: New task get_file_md5
07-30 06:22 DEBUG  TaskList: #### Running get_file_md5...
07-30 06:22 DEBUG  TaskList: #### Finished get_file_md5
07-30 06:22 DEBUG  TaskList: ### Finished check_iso
07-30 06:22 DEBUG  TaskList: ## Finished get_iso
07-30 06:22 DEBUG  TaskList: ## Running extract_kernel...
07-30 06:22 DEBUG  CommonBackend: Copying files from CD I:\
07-30 06:22 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-30 06:22 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\vmlinuz
07-30 06:22 DEBUG  CommonBackend:   E:\ubuntu\install\boot\vmlinuz md5 = 0fb4d79f5f23cba37cf40ef017bb3c65 == 0fb4d79f5f23cba37cf40ef017bb3c65
07-30 06:22 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\initrd.lz
07-30 06:22 DEBUG  CommonBackend:   E:\ubuntu\install\boot\initrd.lz md5 = f5112034765ef7db4c2ebcf2ea409ecf == f5112034765ef7db4c2ebcf2ea409ecf
07-30 06:22 DEBUG  TaskList: ## Finished extract_kernel
07-30 06:22 DEBUG  TaskList: ## Running choose_disk_sizes...
07-30 06:22 DEBUG  WindowsBackend: total size=5000
  root=4744
  swap=256
  home=0
  usr=0
07-30 06:22 DEBUG  TaskList: ## Finished choose_disk_sizes
07-30 06:22 DEBUG  TaskList: ## Running create_preseed...
07-30 06:22 DEBUG  TaskList: ## Finished create_preseed
07-30 06:22 DEBUG  TaskList: ## Running modify_bootloader...
07-30 06:22 DEBUG  TaskList: New task modify_bcd
07-30 06:22 DEBUG  TaskList: ### Running modify_bcd...
07-30 06:22 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 285640.714844 mb free ntfs)
07-30 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {76cd50ae-c7e9-11e1-ac33-be1aa438bbbf}
07-30 06:22 DEBUG  TaskList: ### Finished modify_bcd
07-30 06:22 DEBUG  TaskList: New task modify_bcd
07-30 06:22 DEBUG  TaskList: ### Running modify_bcd...
07-30 06:22 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 24874.9101563 mb free ntfs)
07-30 06:22 DEBUG  WindowsBackend: BCD has already been modified
07-30 06:22 DEBUG  TaskList: ### Finished modify_bcd
07-30 06:22 DEBUG  TaskList: New task modify_bcd
07-30 06:22 DEBUG  TaskList: ### Running modify_bcd...
07-30 06:22 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 10219.8867188 mb free ntfs)
07-30 06:22 DEBUG  WindowsBackend: BCD has already been modified
07-30 06:22 DEBUG  TaskList: ### Finished modify_bcd
07-30 06:22 DEBUG  TaskList: New task modify_bcd
07-30 06:22 DEBUG  TaskList: ### Running modify_bcd...
07-30 06:22 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 230858.910156 mb free ntfs)
07-30 06:22 DEBUG  WindowsBackend: BCD has already been modified
07-30 06:22 DEBUG  TaskList: ### Finished modify_bcd
07-30 06:22 DEBUG  TaskList: New task modify_bcd
07-30 06:22 DEBUG  TaskList: ### Running modify_bcd...
07-30 06:22 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 15951.4921875 mb free ntfs)
07-30 06:22 DEBUG  WindowsBackend: BCD has already been modified
07-30 06:22 DEBUG  TaskList: ### Finished modify_bcd
07-30 06:22 DEBUG  TaskList: ## Finished modify_bootloader
07-30 06:22 DEBUG  TaskList: ## Running modify_grub_configuration...
07-30 06:22 DEBUG  TaskList: ## Finished modify_grub_configuration
07-30 06:22 DEBUG  TaskList: ## Running create_virtual_disks...
07-30 06:22 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\root.disk of 4744MB
07-30 06:22 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\swap.disk of 256MB
07-30 06:22 DEBUG  TaskList: ## Finished create_virtual_disks
07-30 06:22 DEBUG  TaskList: ## Running uncompress_files...
07-30 06:22 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot /U /A /F
07-30 06:22 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot\*.* /U /A /F
07-30 06:22 DEBUG  TaskList: ## Finished uncompress_files
07-30 06:22 DEBUG  TaskList: ## Running eject_cd...
07-30 06:22 DEBUG  TaskList: ## Finished eject_cd
07-30 06:22 DEBUG  TaskList: # Finished tasklist
07-30 06:22 INFO   root: Almost finished installing
07-30 06:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF891.tmp\translations, languages=['en_US', 'en']
07-30 06:22 INFO   root: Finished installation
07-30 06:22 INFO   root: Rebooting
07-30 06:22 DEBUG  TaskList: # Running tasklist...
07-30 06:22 DEBUG  TaskList: ## Running reboot...
07-30 06:22 DEBUG  TaskList: ## Finished reboot
07-30 06:22 DEBUG  TaskList: # Finished tasklist
07-30 06:22 DEBUG  root: application.quit
07-30 06:22 DEBUG  WindowsFrontend: frontend.quit
07-30 06:22 DEBUG  WindowsFrontend: frontend.on_quit
07-30 06:22 DEBUG  root: application.on_quit
07-30 06:22 INFO   root: sys.exit
07-31 07:20 INFO   root: === wubi 12.04 rev265 ===
07-31 07:20 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 07:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-31 07:20 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\data
07-31 07:20 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\bin\7z.exe
07-31 07:20 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 07:20 DEBUG  CommonBackend: Fetching basic info...
07-31 07:20 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 07:20 DEBUG  CommonBackend: platform=win32
07-31 07:20 DEBUG  CommonBackend: osname=nt
07-31 07:20 DEBUG  CommonBackend: language=en_US
07-31 07:20 DEBUG  CommonBackend: encoding=cp932
07-31 07:20 DEBUG  WindowsBackend: arch=amd64
07-31 07:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\data\isolist.ini
07-31 07:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 07:20 DEBUG  WindowsBackend: Fetching host info...
07-31 07:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 07:20 DEBUG  WindowsBackend: windows version=vista
07-31 07:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 07:20 DEBUG  WindowsBackend: windows_sp=None
07-31 07:20 DEBUG  WindowsBackend: windows_build=7600
07-31 07:20 DEBUG  WindowsBackend: gmt=-8
07-31 07:20 DEBUG  WindowsBackend: country=US
07-31 07:20 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 07:20 DEBUG  WindowsBackend: windows_username=Brad
07-31 07:20 DEBUG  WindowsBackend: user_full_name=Brad
07-31 07:20 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 07:20 DEBUG  WindowsBackend: windows_language_code=1033
07-31 07:20 DEBUG  WindowsBackend: windows_language=English
07-31 07:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 07:20 DEBUG  WindowsBackend: bootloader=vista
07-31 07:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 284623.773438 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(C: hd 284623.773438 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(E: hd 4496.97265625 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-31 07:20 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-31 07:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 07:20 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 07:20 DEBUG  WindowsBackend: keyboard_layout=us
07-31 07:20 DEBUG  WindowsBackend: keyboard_variant=
07-31 07:20 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 07:20 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 07:20 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 07:20 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 07:20 DEBUG  CommonBackend: Searching for local CDs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-31 07:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-31 07:20 DEBUG  Distro: wrong version: 9.10 != 12.04
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro: wrong version: 9.10 != 12.04
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-31 07:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 07:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 07:20 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 07:20 INFO   root: Already installed, running the uninstaller...
07-31 07:20 INFO   root: Running the uninstaller...
07-31 07:20 INFO   CommonBackend: This is the uninstaller running
07-31 07:20 DEBUG  WindowsFrontend: __init__...
07-31 07:20 DEBUG  WindowsFrontend: on_init...
07-31 07:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\translations, languages=['en_US', 'en']
07-31 07:20 INFO   root: Received settings
07-31 07:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\translations, languages=['en_US', 'en']
07-31 07:20 DEBUG  TaskList: # Running tasklist...
07-31 07:20 DEBUG  TaskList: ## Running Remove bootloader entry...
07-31 07:20 DEBUG  WindowsBackend: Removing bcd entry {76cd50ae-c7e9-11e1-ac33-be1aa438bbbf}
07-31 07:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
07-31 07:20 DEBUG  WindowsBackend: undo_bootini C:
07-31 07:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 284623.773438 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: undo_bootini D:
07-31 07:20 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: undo_bootini E:
07-31 07:20 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 4496.97265625 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: undo_bootini F:
07-31 07:20 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230858.910156 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: undo_bootini H:
07-31 07:20 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 3047.25390625 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: undo_bootini J:
07-31 07:20 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 15951.4921875 mb free ntfs)
07-31 07:20 DEBUG  TaskList: ## Finished Remove bootloader entry
07-31 07:20 DEBUG  TaskList: ## Running Remove target dir...
07-31 07:20 DEBUG  CommonBackend: Deleting E:\ubuntu
07-31 07:20 DEBUG  TaskList: ## Finished Remove target dir
07-31 07:20 DEBUG  TaskList: ## Running Remove registry key...
07-31 07:20 DEBUG  TaskList: ## Finished Remove registry key
07-31 07:20 DEBUG  TaskList: # Finished tasklist
07-31 07:20 INFO   root: Almost finished uninstalling
07-31 07:20 INFO   root: Finished uninstallation
07-31 07:20 DEBUG  CommonBackend: Fetching basic info...
07-31 07:20 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 07:20 DEBUG  CommonBackend: platform=win32
07-31 07:20 DEBUG  CommonBackend: osname=nt
07-31 07:20 DEBUG  WindowsBackend: arch=amd64
07-31 07:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\data\isolist.ini
07-31 07:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 07:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 07:20 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 07:20 DEBUG  WindowsBackend: Fetching host info...
07-31 07:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 07:20 DEBUG  WindowsBackend: windows version=vista
07-31 07:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 07:20 DEBUG  WindowsBackend: windows_sp=None
07-31 07:20 DEBUG  WindowsBackend: windows_build=7600
07-31 07:20 DEBUG  WindowsBackend: gmt=-8
07-31 07:20 DEBUG  WindowsBackend: country=US
07-31 07:20 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 07:20 DEBUG  WindowsBackend: windows_username=Brad
07-31 07:20 DEBUG  WindowsBackend: user_full_name=Brad
07-31 07:20 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 07:20 DEBUG  WindowsBackend: windows_language_code=1033
07-31 07:20 DEBUG  WindowsBackend: windows_language=English
07-31 07:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 07:20 DEBUG  WindowsBackend: bootloader=vista
07-31 07:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 284623.863281 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(C: hd 284623.863281 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 07:20 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 07:20 DEBUG  WindowsBackend: uninstaller_path=None
07-31 07:20 DEBUG  WindowsBackend: previous_target_dir=None
07-31 07:20 DEBUG  WindowsBackend: previous_distro_name=None
07-31 07:20 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 07:20 DEBUG  WindowsBackend: keyboard_layout=us
07-31 07:20 DEBUG  WindowsBackend: keyboard_variant=
07-31 07:20 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 07:20 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 07:20 DEBUG  CommonBackend: Searching for local CDs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro: wrong version: 9.10 != 12.04
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 07:20 DEBUG  Distro: wrong version: 9.10 != 12.04
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-31 07:20 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 07:20 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-31 07:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 07:20 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 07:20 INFO   root: Running the installer...
07-31 07:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\translations, languages=['en_US', 'en']
07-31 07:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl81AD.tmp\translations, languages=['en_US', 'en']
07-31 07:20 INFO   WindowsFrontend: Operation cancelled
07-31 07:20 DEBUG  WindowsFrontend: frontend.quit
07-31 07:20 DEBUG  WindowsFrontend: frontend.on_quit
07-31 07:20 DEBUG  root: application.on_quit
07-31 07:20 INFO   root: sys.exit
07-31 07:24 INFO   root: === wubi 12.04 rev265 ===
07-31 07:24 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 07:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 07:24 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\data
07-31 07:24 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\bin\7z.exe
07-31 07:24 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 07:24 DEBUG  CommonBackend: Fetching basic info...
07-31 07:24 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 07:24 DEBUG  CommonBackend: platform=win32
07-31 07:24 DEBUG  CommonBackend: osname=nt
07-31 07:24 DEBUG  CommonBackend: language=en_US
07-31 07:24 DEBUG  CommonBackend: encoding=cp932
07-31 07:24 DEBUG  WindowsBackend: arch=amd64
07-31 07:24 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\data\isolist.ini
07-31 07:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 07:24 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 07:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 07:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 07:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 07:24 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 07:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 07:24 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 07:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 07:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 07:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 07:24 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 07:24 DEBUG  WindowsBackend: Fetching host info...
07-31 07:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 07:24 DEBUG  WindowsBackend: windows version=vista
07-31 07:24 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 07:24 DEBUG  WindowsBackend: windows_sp=None
07-31 07:24 DEBUG  WindowsBackend: windows_build=7600
07-31 07:24 DEBUG  WindowsBackend: gmt=-8
07-31 07:24 DEBUG  WindowsBackend: country=US
07-31 07:24 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 07:24 DEBUG  WindowsBackend: windows_username=Brad
07-31 07:24 DEBUG  WindowsBackend: user_full_name=Brad
07-31 07:24 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 07:24 DEBUG  WindowsBackend: windows_language_code=1033
07-31 07:24 DEBUG  WindowsBackend: windows_language=English
07-31 07:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 07:24 DEBUG  WindowsBackend: bootloader=vista
07-31 07:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 284598.800781 mb free ntfs)
07-31 07:24 DEBUG  WindowsBackend: drive=Drive(C: hd 284598.800781 mb free ntfs)
07-31 07:24 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 07:24 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 07:24 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 07:24 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
07-31 07:24 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 07:24 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 07:24 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 07:24 DEBUG  WindowsBackend: uninstaller_path=None
07-31 07:24 DEBUG  WindowsBackend: previous_target_dir=None
07-31 07:24 DEBUG  WindowsBackend: previous_distro_name=None
07-31 07:24 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 07:24 DEBUG  WindowsBackend: keyboard_layout=us
07-31 07:24 DEBUG  WindowsBackend: keyboard_variant=
07-31 07:24 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 07:24 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 07:24 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 07:24 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 07:24 DEBUG  CommonBackend: Searching for local CDs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-31 07:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-31 07:24 DEBUG  Distro: wrong version: 9.10 != 12.04
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro: wrong version: 9.10 != 12.04
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-31 07:24 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 07:24 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
07-31 07:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 07:24 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 07:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 07:24 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 07:24 INFO   root: Running the CD menu...
07-31 07:24 DEBUG  WindowsFrontend: __init__...
07-31 07:24 DEBUG  WindowsFrontend: on_init...
07-31 07:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\translations, languages=['en_US', 'en']
07-31 07:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylADEA.tmp\translations, languages=['en_US', 'en']
07-31 07:24 INFO   root: CD menu finished
07-31 07:24 INFO   root: Rebooting
07-31 07:24 DEBUG  TaskList: # Running tasklist...
07-31 07:24 DEBUG  TaskList: ## Running reboot...
07-31 07:24 DEBUG  TaskList: ## Finished reboot
07-31 07:24 DEBUG  TaskList: # Finished tasklist
07-31 07:24 DEBUG  root: application.quit
07-31 07:24 DEBUG  WindowsFrontend: frontend.quit
07-31 07:24 DEBUG  WindowsFrontend: frontend.on_quit
07-31 07:24 DEBUG  root: application.on_quit
07-31 07:24 INFO   root: sys.exit
07-31 08:35 INFO   root: === wubi 12.04 rev265 ===
07-31 08:35 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 08:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 08:35 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\data
07-31 08:35 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\bin\7z.exe
07-31 08:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 08:35 DEBUG  CommonBackend: Fetching basic info...
07-31 08:35 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 08:35 DEBUG  CommonBackend: platform=win32
07-31 08:35 DEBUG  CommonBackend: osname=nt
07-31 08:35 DEBUG  CommonBackend: language=en_US
07-31 08:35 DEBUG  CommonBackend: encoding=cp932
07-31 08:35 DEBUG  WindowsBackend: arch=amd64
07-31 08:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\data\isolist.ini
07-31 08:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 08:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 08:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 08:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 08:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 08:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 08:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 08:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 08:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 08:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 08:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 08:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 08:35 DEBUG  WindowsBackend: Fetching host info...
07-31 08:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 08:35 DEBUG  WindowsBackend: windows version=vista
07-31 08:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 08:35 DEBUG  WindowsBackend: windows_sp=None
07-31 08:35 DEBUG  WindowsBackend: windows_build=7600
07-31 08:35 DEBUG  WindowsBackend: gmt=-8
07-31 08:35 DEBUG  WindowsBackend: country=US
07-31 08:35 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 08:35 DEBUG  WindowsBackend: windows_username=Brad
07-31 08:35 DEBUG  WindowsBackend: user_full_name=Brad
07-31 08:35 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 08:35 DEBUG  WindowsBackend: windows_language_code=1033
07-31 08:35 DEBUG  WindowsBackend: windows_language=English
07-31 08:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 08:35 DEBUG  WindowsBackend: bootloader=vista
07-31 08:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283002.472656 mb free ntfs)
07-31 08:35 DEBUG  WindowsBackend: drive=Drive(C: hd 283002.472656 mb free ntfs)
07-31 08:35 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 08:35 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 08:35 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 08:35 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 08:35 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 08:35 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 08:35 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 08:35 DEBUG  WindowsBackend: uninstaller_path=C:\linuxmint\uninstall-wubi.exe
07-31 08:35 DEBUG  WindowsBackend: previous_target_dir=C:\linuxmint
07-31 08:35 DEBUG  WindowsBackend: previous_distro_name=Linux Mint
07-31 08:35 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 08:35 DEBUG  WindowsBackend: keyboard_layout=us
07-31 08:35 DEBUG  WindowsBackend: keyboard_variant=
07-31 08:35 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 08:35 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 08:35 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 08:35 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 08:35 DEBUG  CommonBackend: Searching for local CDs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC032.tmp is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 08:35 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 08:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 08:35 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 08:35 INFO   root: Running the CD menu...
07-31 08:35 DEBUG  WindowsFrontend: __init__...
07-31 08:35 DEBUG  WindowsFrontend: on_init...
07-31 08:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\translations, languages=['en_US', 'en']
07-31 08:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylC032.tmp\translations, languages=['en_US', 'en']
07-31 08:35 INFO   root: CD menu finished
07-31 08:35 INFO   root: Already installed, running the uninstaller...
07-31 08:35 INFO   root: Running the uninstaller...
07-31 08:35 INFO   CommonBackend: Launching previous uninestaller C:\linuxmint\uninstall-wubi.exe
07-31 08:35 DEBUG  root: application.quit
07-31 08:35 DEBUG  WindowsFrontend: frontend.quit
07-31 08:35 DEBUG  WindowsFrontend: frontend.on_quit
07-31 08:35 DEBUG  root: application.on_quit
07-31 08:35 INFO   root: sys.exit
07-31 08:36 INFO   root: === wubi 12.04 rev265 ===
07-31 08:36 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 08:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 08:36 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\data
07-31 08:36 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\bin\7z.exe
07-31 08:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 08:36 DEBUG  CommonBackend: Fetching basic info...
07-31 08:36 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 08:36 DEBUG  CommonBackend: platform=win32
07-31 08:36 DEBUG  CommonBackend: osname=nt
07-31 08:36 DEBUG  CommonBackend: language=en_US
07-31 08:36 DEBUG  CommonBackend: encoding=cp932
07-31 08:36 DEBUG  WindowsBackend: arch=amd64
07-31 08:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\data\isolist.ini
07-31 08:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 08:36 DEBUG  WindowsBackend: Fetching host info...
07-31 08:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 08:36 DEBUG  WindowsBackend: windows version=vista
07-31 08:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 08:36 DEBUG  WindowsBackend: windows_sp=None
07-31 08:36 DEBUG  WindowsBackend: windows_build=7600
07-31 08:36 DEBUG  WindowsBackend: gmt=-8
07-31 08:36 DEBUG  WindowsBackend: country=US
07-31 08:36 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 08:36 DEBUG  WindowsBackend: windows_username=Brad
07-31 08:36 DEBUG  WindowsBackend: user_full_name=Brad
07-31 08:36 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 08:36 DEBUG  WindowsBackend: windows_language_code=1033
07-31 08:36 DEBUG  WindowsBackend: windows_language=English
07-31 08:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 08:36 DEBUG  WindowsBackend: bootloader=vista
07-31 08:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283830.5625 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(C: hd 283830.5625 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: uninstaller_path=None
07-31 08:36 DEBUG  WindowsBackend: previous_target_dir=None
07-31 08:36 DEBUG  WindowsBackend: previous_distro_name=None
07-31 08:36 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 08:36 DEBUG  WindowsBackend: keyboard_layout=us
07-31 08:36 DEBUG  WindowsBackend: keyboard_variant=
07-31 08:36 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 08:36 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 08:36 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 08:36 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 08:36 DEBUG  CommonBackend: Searching for local CDs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 08:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 08:36 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 08:36 INFO   root: Running the CD menu...
07-31 08:36 DEBUG  WindowsFrontend: __init__...
07-31 08:36 DEBUG  WindowsFrontend: on_init...
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\translations, languages=['en_US', 'en']
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\translations, languages=['en_US', 'en']
07-31 08:36 INFO   root: CD menu finished
07-31 08:36 INFO   root: Running the CD boot helper...
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\translations, languages=['en_US', 'en']
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl4AE4.tmp\translations, languages=['en_US', 'en']
07-31 08:36 DEBUG  WindowsFrontend: frontend.on_quit
07-31 08:36 DEBUG  root: application.on_quit
07-31 08:36 INFO   root: sys.exit
07-31 08:36 INFO   root: === wubi 12.04 rev265 ===
07-31 08:36 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 08:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 08:36 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\data
07-31 08:36 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\bin\7z.exe
07-31 08:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 08:36 DEBUG  CommonBackend: Fetching basic info...
07-31 08:36 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 08:36 DEBUG  CommonBackend: platform=win32
07-31 08:36 DEBUG  CommonBackend: osname=nt
07-31 08:36 DEBUG  CommonBackend: language=en_US
07-31 08:36 DEBUG  CommonBackend: encoding=cp932
07-31 08:36 DEBUG  WindowsBackend: arch=amd64
07-31 08:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\data\isolist.ini
07-31 08:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 08:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 08:36 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 08:36 DEBUG  WindowsBackend: Fetching host info...
07-31 08:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 08:36 DEBUG  WindowsBackend: windows version=vista
07-31 08:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 08:36 DEBUG  WindowsBackend: windows_sp=None
07-31 08:36 DEBUG  WindowsBackend: windows_build=7600
07-31 08:36 DEBUG  WindowsBackend: gmt=-8
07-31 08:36 DEBUG  WindowsBackend: country=US
07-31 08:36 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 08:36 DEBUG  WindowsBackend: windows_username=Brad
07-31 08:36 DEBUG  WindowsBackend: user_full_name=Brad
07-31 08:36 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 08:36 DEBUG  WindowsBackend: windows_language_code=1033
07-31 08:36 DEBUG  WindowsBackend: windows_language=English
07-31 08:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 08:36 DEBUG  WindowsBackend: bootloader=vista
07-31 08:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283830.375 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(C: hd 283830.375 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 08:36 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 08:36 DEBUG  WindowsBackend: uninstaller_path=None
07-31 08:36 DEBUG  WindowsBackend: previous_target_dir=None
07-31 08:36 DEBUG  WindowsBackend: previous_distro_name=None
07-31 08:36 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 08:36 DEBUG  WindowsBackend: keyboard_layout=us
07-31 08:36 DEBUG  WindowsBackend: keyboard_variant=
07-31 08:36 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 08:36 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 08:36 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 08:36 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 08:36 DEBUG  CommonBackend: Searching for local CDs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 08:36 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 08:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 08:36 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 08:36 INFO   root: Running the CD menu...
07-31 08:36 DEBUG  WindowsFrontend: __init__...
07-31 08:36 DEBUG  WindowsFrontend: on_init...
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\translations, languages=['en_US', 'en']
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\translations, languages=['en_US', 'en']
07-31 08:36 INFO   root: CD menu finished
07-31 08:36 INFO   root: Running the CD boot helper...
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\translations, languages=['en_US', 'en']
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\translations, languages=['en_US', 'en']
07-31 08:36 INFO   root: CD boot helper confirmed
07-31 08:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\translations, languages=['en_US', 'en']
07-31 08:36 DEBUG  TaskList: # Running tasklist...
07-31 08:36 DEBUG  TaskList: ## Running select_target_dir...
07-31 08:36 INFO   WindowsBackend: Installing into C:\ubuntu
07-31 08:36 DEBUG  TaskList: ## Finished select_target_dir
07-31 08:36 DEBUG  TaskList: ## Running create_dir_structure...
07-31 08:36 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-31 08:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-31 08:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-31 08:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-31 08:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-31 08:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-31 08:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-31 08:36 DEBUG  TaskList: ## Finished create_dir_structure
07-31 08:36 DEBUG  TaskList: ## Running uncompress_target_dir...
07-31 08:36 DEBUG  TaskList: ## Finished uncompress_target_dir
07-31 08:36 DEBUG  TaskList: ## Running create_uninstaller...
07-31 08:36 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-31 08:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-31 08:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-31 08:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-31 08:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-31 08:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-31 08:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-31 08:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-31 08:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-31 08:36 DEBUG  TaskList: ## Finished create_uninstaller
07-31 08:36 DEBUG  TaskList: ## Running copy_installation_files...
07-31 08:36 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-31 08:36 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\winboot -> C:\ubuntu\winboot
07-31 08:36 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl9B83.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-31 08:36 DEBUG  TaskList: ## Finished copy_installation_files
07-31 08:36 DEBUG  TaskList: ## Running use_cd...
07-31 08:36 DEBUG  TaskList: New task copy_file
07-31 08:36 DEBUG  TaskList: ### Running copy_file...
07-31 08:41 DEBUG  TaskList: ### Finished copy_file
07-31 08:41 DEBUG  TaskList: New task check_iso
07-31 08:41 DEBUG  TaskList: ### Running check_iso...
07-31 08:41 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
07-31 08:41 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
07-31 08:41 DEBUG  Distro:     wrong size: 3997450240 > 900000000
07-31 08:41 DEBUG  TaskList: ### Finished check_iso
07-31 08:41 DEBUG  TaskList: ## Finished use_cd
07-31 08:41 DEBUG  TaskList: ## Running extract_kernel...
07-31 08:41 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
07-31 08:41 DEBUG  TaskList: # Cancelling tasklist
07-31 08:41 DEBUG  TaskList: # Finished tasklist
07-31 08:41 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
07-31 08:46 INFO   root: === wubi 12.04 rev265 ===
07-31 08:46 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 08:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 08:46 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\data
07-31 08:46 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\bin\7z.exe
07-31 08:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 08:46 DEBUG  CommonBackend: Fetching basic info...
07-31 08:46 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 08:46 DEBUG  CommonBackend: platform=win32
07-31 08:46 DEBUG  CommonBackend: osname=nt
07-31 08:46 DEBUG  CommonBackend: language=en_US
07-31 08:46 DEBUG  CommonBackend: encoding=cp932
07-31 08:46 DEBUG  WindowsBackend: arch=amd64
07-31 08:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\data\isolist.ini
07-31 08:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 08:46 DEBUG  WindowsBackend: Fetching host info...
07-31 08:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 08:46 DEBUG  WindowsBackend: windows version=vista
07-31 08:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 08:46 DEBUG  WindowsBackend: windows_sp=None
07-31 08:46 DEBUG  WindowsBackend: windows_build=7600
07-31 08:46 DEBUG  WindowsBackend: gmt=-8
07-31 08:46 DEBUG  WindowsBackend: country=US
07-31 08:46 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 08:46 DEBUG  WindowsBackend: windows_username=Brad
07-31 08:46 DEBUG  WindowsBackend: user_full_name=Brad
07-31 08:46 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 08:46 DEBUG  WindowsBackend: windows_language_code=1033
07-31 08:46 DEBUG  WindowsBackend: windows_language=English
07-31 08:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 08:46 DEBUG  WindowsBackend: bootloader=vista
07-31 08:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 279995.820313 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(C: hd 279995.820313 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-31 08:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-31 08:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 08:46 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 08:46 DEBUG  WindowsBackend: keyboard_layout=us
07-31 08:46 DEBUG  WindowsBackend: keyboard_variant=
07-31 08:46 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 08:46 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 08:46 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 08:46 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 08:46 DEBUG  CommonBackend: Searching for local CDs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 08:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 08:46 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 08:46 INFO   root: Running the CD menu...
07-31 08:46 DEBUG  WindowsFrontend: __init__...
07-31 08:46 DEBUG  WindowsFrontend: on_init...
07-31 08:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\translations, languages=['en_US', 'en']
07-31 08:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\translations, languages=['en_US', 'en']
07-31 08:46 INFO   root: CD menu finished
07-31 08:46 INFO   root: Already installed, running the uninstaller...
07-31 08:46 INFO   root: Running the uninstaller...
07-31 08:46 INFO   CommonBackend: This is the uninstaller running
07-31 08:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\translations, languages=['en_US', 'en']
07-31 08:46 INFO   root: Received settings
07-31 08:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\translations, languages=['en_US', 'en']
07-31 08:46 DEBUG  TaskList: # Running tasklist...
07-31 08:46 DEBUG  TaskList: ## Running Remove bootloader entry...
07-31 08:46 DEBUG  WindowsBackend: Could not find bcd id
07-31 08:46 DEBUG  WindowsBackend: undo_bootini C:
07-31 08:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 279995.820313 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: undo_bootini D:
07-31 08:46 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: undo_bootini E:
07-31 08:46 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 10219.8867188 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: undo_bootini F:
07-31 08:46 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230858.910156 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: undo_bootini H:
07-31 08:46 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 3047.25390625 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: undo_bootini J:
07-31 08:46 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 15951.4921875 mb free ntfs)
07-31 08:46 DEBUG  TaskList: ## Finished Remove bootloader entry
07-31 08:46 DEBUG  TaskList: ## Running Remove target dir...
07-31 08:46 DEBUG  CommonBackend: Deleting C:\ubuntu
07-31 08:46 DEBUG  TaskList: ## Finished Remove target dir
07-31 08:46 DEBUG  TaskList: ## Running Remove registry key...
07-31 08:46 DEBUG  TaskList: ## Finished Remove registry key
07-31 08:46 DEBUG  TaskList: # Finished tasklist
07-31 08:46 INFO   root: Almost finished uninstalling
07-31 08:46 INFO   root: Finished uninstallation
07-31 08:46 DEBUG  CommonBackend: Fetching basic info...
07-31 08:46 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 08:46 DEBUG  CommonBackend: platform=win32
07-31 08:46 DEBUG  CommonBackend: osname=nt
07-31 08:46 DEBUG  WindowsBackend: arch=amd64
07-31 08:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\data\isolist.ini
07-31 08:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 08:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 08:46 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 08:46 DEBUG  WindowsBackend: Fetching host info...
07-31 08:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 08:46 DEBUG  WindowsBackend: windows version=vista
07-31 08:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 08:46 DEBUG  WindowsBackend: windows_sp=None
07-31 08:46 DEBUG  WindowsBackend: windows_build=7600
07-31 08:46 DEBUG  WindowsBackend: gmt=-8
07-31 08:46 DEBUG  WindowsBackend: country=US
07-31 08:46 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 08:46 DEBUG  WindowsBackend: windows_username=Brad
07-31 08:46 DEBUG  WindowsBackend: user_full_name=Brad
07-31 08:46 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 08:46 DEBUG  WindowsBackend: windows_language_code=1033
07-31 08:46 DEBUG  WindowsBackend: windows_language=English
07-31 08:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 08:46 DEBUG  WindowsBackend: bootloader=vista
07-31 08:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283810.652344 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(C: hd 283810.652344 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 08:46 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 08:46 DEBUG  WindowsBackend: uninstaller_path=None
07-31 08:46 DEBUG  WindowsBackend: previous_target_dir=None
07-31 08:46 DEBUG  WindowsBackend: previous_distro_name=None
07-31 08:46 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 08:46 DEBUG  WindowsBackend: keyboard_layout=us
07-31 08:46 DEBUG  WindowsBackend: keyboard_variant=
07-31 08:46 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 08:46 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 08:46 DEBUG  CommonBackend: Searching for local CDs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 08:46 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 08:46 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 08:46 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 08:46 INFO   root: Running the CD boot helper...
07-31 08:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\translations, languages=['en_US', 'en']
07-31 08:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\translations, languages=['en_US', 'en']
07-31 08:46 INFO   root: CD boot helper confirmed
07-31 08:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\translations, languages=['en_US', 'en']
07-31 08:46 DEBUG  TaskList: # Running tasklist...
07-31 08:46 DEBUG  TaskList: ## Running select_target_dir...
07-31 08:46 INFO   WindowsBackend: Installing into C:\ubuntu
07-31 08:46 DEBUG  TaskList: ## Finished select_target_dir
07-31 08:46 DEBUG  TaskList: ## Running create_dir_structure...
07-31 08:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-31 08:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-31 08:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-31 08:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-31 08:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-31 08:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-31 08:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-31 08:46 DEBUG  TaskList: ## Finished create_dir_structure
07-31 08:46 DEBUG  TaskList: ## Running uncompress_target_dir...
07-31 08:46 DEBUG  TaskList: ## Finished uncompress_target_dir
07-31 08:46 DEBUG  TaskList: ## Running create_uninstaller...
07-31 08:46 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-31 08:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-31 08:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-31 08:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-31 08:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-31 08:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-31 08:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-31 08:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-31 08:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-31 08:46 DEBUG  TaskList: ## Finished create_uninstaller
07-31 08:46 DEBUG  TaskList: ## Running copy_installation_files...
07-31 08:46 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-31 08:46 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\winboot -> C:\ubuntu\winboot
07-31 08:46 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pyl7638.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-31 08:46 DEBUG  TaskList: ## Finished copy_installation_files
07-31 08:46 DEBUG  TaskList: ## Running use_cd...
07-31 08:46 DEBUG  TaskList: New task copy_file
07-31 08:46 DEBUG  TaskList: ### Running copy_file...
07-31 08:51 DEBUG  TaskList: ### Finished copy_file
07-31 08:51 DEBUG  TaskList: New task check_iso
07-31 08:51 DEBUG  TaskList: ### Running check_iso...
07-31 08:51 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
07-31 08:51 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
07-31 08:51 DEBUG  Distro:     wrong size: 3997450240 > 900000000
07-31 08:51 DEBUG  TaskList: ### Finished check_iso
07-31 08:51 DEBUG  TaskList: ## Finished use_cd
07-31 08:51 DEBUG  TaskList: ## Running extract_kernel...
07-31 08:51 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
07-31 08:51 DEBUG  TaskList: # Cancelling tasklist
07-31 08:51 DEBUG  TaskList: # Finished tasklist
07-31 08:51 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
07-31 09:08 INFO   root: === wubi 12.04 rev265 ===
07-31 09:08 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 09:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 09:08 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\data
07-31 09:08 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\bin\7z.exe
07-31 09:08 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 09:08 DEBUG  CommonBackend: Fetching basic info...
07-31 09:08 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 09:08 DEBUG  CommonBackend: platform=win32
07-31 09:08 DEBUG  CommonBackend: osname=nt
07-31 09:08 DEBUG  CommonBackend: language=en_US
07-31 09:08 DEBUG  CommonBackend: encoding=cp932
07-31 09:08 DEBUG  WindowsBackend: arch=amd64
07-31 09:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\data\isolist.ini
07-31 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:08 DEBUG  WindowsBackend: Fetching host info...
07-31 09:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:08 DEBUG  WindowsBackend: windows version=vista
07-31 09:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:08 DEBUG  WindowsBackend: windows_sp=None
07-31 09:08 DEBUG  WindowsBackend: windows_build=7600
07-31 09:08 DEBUG  WindowsBackend: gmt=-8
07-31 09:08 DEBUG  WindowsBackend: country=US
07-31 09:08 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:08 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:08 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:08 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:08 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:08 DEBUG  WindowsBackend: windows_language=English
07-31 09:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:08 DEBUG  WindowsBackend: bootloader=vista
07-31 09:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 280000.210938 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(C: hd 280000.210938 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-31 09:08 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-31 09:08 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 09:08 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:08 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:08 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:08 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 09:08 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 09:08 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:08 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:08 DEBUG  CommonBackend: Searching for local CDs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 09:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 09:08 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:08 INFO   root: Running the CD menu...
07-31 09:08 DEBUG  WindowsFrontend: __init__...
07-31 09:08 DEBUG  WindowsFrontend: on_init...
07-31 09:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\translations, languages=['en_US', 'en']
07-31 09:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl446F.tmp\translations, languages=['en_US', 'en']
07-31 09:08 INFO   WindowsFrontend: Operation cancelled
07-31 09:08 DEBUG  WindowsFrontend: frontend.quit
07-31 09:08 DEBUG  WindowsFrontend: frontend.on_quit
07-31 09:08 DEBUG  root: application.on_quit
07-31 09:08 INFO   root: sys.exit
07-31 09:08 INFO   root: === wubi 12.04 rev265 ===
07-31 09:08 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 09:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-31 09:08 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\data
07-31 09:08 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\bin\7z.exe
07-31 09:08 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 09:08 DEBUG  CommonBackend: Fetching basic info...
07-31 09:08 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 09:08 DEBUG  CommonBackend: platform=win32
07-31 09:08 DEBUG  CommonBackend: osname=nt
07-31 09:08 DEBUG  CommonBackend: language=en_US
07-31 09:08 DEBUG  CommonBackend: encoding=cp932
07-31 09:08 DEBUG  WindowsBackend: arch=amd64
07-31 09:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\data\isolist.ini
07-31 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:08 DEBUG  WindowsBackend: Fetching host info...
07-31 09:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:08 DEBUG  WindowsBackend: windows version=vista
07-31 09:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:08 DEBUG  WindowsBackend: windows_sp=None
07-31 09:08 DEBUG  WindowsBackend: windows_build=7600
07-31 09:08 DEBUG  WindowsBackend: gmt=-8
07-31 09:08 DEBUG  WindowsBackend: country=US
07-31 09:08 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:08 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:08 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:08 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:08 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:08 DEBUG  WindowsBackend: windows_language=English
07-31 09:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:08 DEBUG  WindowsBackend: bootloader=vista
07-31 09:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 279999.796875 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(C: hd 279999.796875 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-31 09:08 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-31 09:08 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 09:08 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:08 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:08 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:08 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 09:08 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 09:08 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:08 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:08 DEBUG  CommonBackend: Searching for local CDs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 09:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 09:08 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:08 INFO   root: Already installed, running the uninstaller...
07-31 09:08 INFO   root: Running the uninstaller...
07-31 09:08 INFO   CommonBackend: This is the uninstaller running
07-31 09:08 DEBUG  WindowsFrontend: __init__...
07-31 09:08 DEBUG  WindowsFrontend: on_init...
07-31 09:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\translations, languages=['en_US', 'en']
07-31 09:08 INFO   root: Received settings
07-31 09:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\translations, languages=['en_US', 'en']
07-31 09:08 DEBUG  TaskList: # Running tasklist...
07-31 09:08 DEBUG  TaskList: ## Running Remove bootloader entry...
07-31 09:08 DEBUG  WindowsBackend: Could not find bcd id
07-31 09:08 DEBUG  WindowsBackend: undo_bootini C:
07-31 09:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 279999.796875 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: undo_bootini D:
07-31 09:08 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: undo_bootini E:
07-31 09:08 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: undo_bootini F:
07-31 09:08 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: undo_bootini H:
07-31 09:08 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: undo_bootini J:
07-31 09:08 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:08 DEBUG  TaskList: ## Finished Remove bootloader entry
07-31 09:08 DEBUG  TaskList: ## Running Remove target dir...
07-31 09:08 DEBUG  CommonBackend: Deleting C:\ubuntu
07-31 09:08 DEBUG  TaskList: ## Finished Remove target dir
07-31 09:08 DEBUG  TaskList: ## Running Remove registry key...
07-31 09:08 DEBUG  TaskList: ## Finished Remove registry key
07-31 09:08 DEBUG  TaskList: # Finished tasklist
07-31 09:08 INFO   root: Almost finished uninstalling
07-31 09:08 INFO   root: Finished uninstallation
07-31 09:08 DEBUG  CommonBackend: Fetching basic info...
07-31 09:08 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 09:08 DEBUG  CommonBackend: platform=win32
07-31 09:08 DEBUG  CommonBackend: osname=nt
07-31 09:08 DEBUG  WindowsBackend: arch=amd64
07-31 09:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\data\isolist.ini
07-31 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:08 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:08 DEBUG  WindowsBackend: Fetching host info...
07-31 09:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:08 DEBUG  WindowsBackend: windows version=vista
07-31 09:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:08 DEBUG  WindowsBackend: windows_sp=None
07-31 09:08 DEBUG  WindowsBackend: windows_build=7600
07-31 09:08 DEBUG  WindowsBackend: gmt=-8
07-31 09:08 DEBUG  WindowsBackend: country=US
07-31 09:08 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:08 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:08 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:08 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:08 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:08 DEBUG  WindowsBackend: windows_language=English
07-31 09:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:08 DEBUG  WindowsBackend: bootloader=vista
07-31 09:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283814.625 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(C: hd 283814.625 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:08 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:08 DEBUG  WindowsBackend: uninstaller_path=None
07-31 09:08 DEBUG  WindowsBackend: previous_target_dir=None
07-31 09:08 DEBUG  WindowsBackend: previous_distro_name=None
07-31 09:08 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:08 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:08 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:08 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:08 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:08 DEBUG  CommonBackend: Searching for local CDs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:08 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:08 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:08 INFO   root: Running the installer...
07-31 09:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\translations, languages=['en_US', 'en']
07-31 09:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\translations, languages=['en_US', 'en']
07-31 09:10 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brad
07-31 09:10 INFO   root: Received settings
07-31 09:10 DEBUG  CommonBackend: Searching for local CD
07-31 09:10 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp is a valid Ubuntu CD
07-31 09:10 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\casper\filesystem.squashfs
07-31 09:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:10 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\translations, languages=['en_US', 'en']
07-31 09:10 DEBUG  TaskList: # Running tasklist...
07-31 09:10 DEBUG  TaskList: ## Running select_target_dir...
07-31 09:10 INFO   WindowsBackend: Installing into E:\ubuntu
07-31 09:10 DEBUG  TaskList: ## Finished select_target_dir
07-31 09:10 DEBUG  TaskList: ## Running create_dir_structure...
07-31 09:10 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-31 09:10 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-31 09:10 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-31 09:10 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-31 09:10 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-31 09:10 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-31 09:10 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-31 09:10 DEBUG  TaskList: ## Finished create_dir_structure
07-31 09:10 DEBUG  TaskList: ## Running uncompress_target_dir...
07-31 09:10 DEBUG  TaskList: ## Finished uncompress_target_dir
07-31 09:10 DEBUG  TaskList: ## Running create_uninstaller...
07-31 09:10 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-31 09:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-31 09:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-31 09:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-31 09:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-31 09:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-31 09:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-31 09:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-31 09:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-31 09:10 DEBUG  TaskList: ## Finished create_uninstaller
07-31 09:10 DEBUG  TaskList: ## Running copy_installation_files...
07-31 09:10 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-31 09:10 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\winboot -> E:\ubuntu\winboot
07-31 09:10 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylF24A.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-31 09:10 DEBUG  TaskList: ## Finished copy_installation_files
07-31 09:10 DEBUG  TaskList: ## Running get_iso...
07-31 09:10 DEBUG  TaskList: New task copy_file
07-31 09:10 DEBUG  TaskList: ### Running copy_file...
07-31 09:15 DEBUG  TaskList: ### Finished copy_file
07-31 09:15 DEBUG  TaskList: New task check_iso
07-31 09:15 DEBUG  TaskList: ### Running check_iso...
07-31 09:15 DEBUG  CommonBackend: Checking E:\ubuntu\install\installation.iso
07-31 09:15 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\installation.iso
07-31 09:15 DEBUG  Distro:     wrong size: 3997450240 > 900000000
07-31 09:15 DEBUG  TaskList: ### Finished check_iso
07-31 09:15 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
07-31 09:15 DEBUG  TaskList: # Cancelling tasklist
07-31 09:15 DEBUG  TaskList: # Finished tasklist
07-31 09:15 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
07-31 09:16 INFO   root: === wubi 12.04 rev265 ===
07-31 09:16 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 09:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-31 09:16 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\data
07-31 09:16 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\bin\7z.exe
07-31 09:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 09:16 DEBUG  CommonBackend: Fetching basic info...
07-31 09:16 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 09:16 DEBUG  CommonBackend: platform=win32
07-31 09:16 DEBUG  CommonBackend: osname=nt
07-31 09:16 DEBUG  CommonBackend: language=en_US
07-31 09:16 DEBUG  CommonBackend: encoding=cp932
07-31 09:16 DEBUG  WindowsBackend: arch=amd64
07-31 09:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\data\isolist.ini
07-31 09:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:16 DEBUG  WindowsBackend: Fetching host info...
07-31 09:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:16 DEBUG  WindowsBackend: windows version=vista
07-31 09:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:16 DEBUG  WindowsBackend: windows_sp=None
07-31 09:16 DEBUG  WindowsBackend: windows_build=7600
07-31 09:16 DEBUG  WindowsBackend: gmt=-8
07-31 09:16 DEBUG  WindowsBackend: country=US
07-31 09:16 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:16 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:16 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:16 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:16 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:16 DEBUG  WindowsBackend: windows_language=English
07-31 09:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:16 DEBUG  WindowsBackend: bootloader=vista
07-31 09:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283813.667969 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(C: hd 283813.667969 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(E: hd 6405.0234375 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-31 09:16 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-31 09:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 09:16 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:16 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:16 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:16 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 09:16 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 09:16 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:16 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:16 DEBUG  CommonBackend: Searching for local CDs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 09:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 09:16 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:16 INFO   root: Already installed, running the uninstaller...
07-31 09:16 INFO   root: Running the uninstaller...
07-31 09:16 INFO   CommonBackend: This is the uninstaller running
07-31 09:16 DEBUG  WindowsFrontend: __init__...
07-31 09:16 DEBUG  WindowsFrontend: on_init...
07-31 09:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\translations, languages=['en_US', 'en']
07-31 09:16 INFO   root: Received settings
07-31 09:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\translations, languages=['en_US', 'en']
07-31 09:16 DEBUG  TaskList: # Running tasklist...
07-31 09:16 DEBUG  TaskList: ## Running Remove bootloader entry...
07-31 09:16 DEBUG  WindowsBackend: Could not find bcd id
07-31 09:16 DEBUG  WindowsBackend: undo_bootini C:
07-31 09:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 283813.667969 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: undo_bootini D:
07-31 09:16 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: undo_bootini E:
07-31 09:16 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6405.0234375 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: undo_bootini F:
07-31 09:16 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: undo_bootini H:
07-31 09:16 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: undo_bootini J:
07-31 09:16 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:16 DEBUG  TaskList: ## Finished Remove bootloader entry
07-31 09:16 DEBUG  TaskList: ## Running Remove target dir...
07-31 09:16 DEBUG  CommonBackend: Deleting E:\ubuntu
07-31 09:16 DEBUG  TaskList: ## Finished Remove target dir
07-31 09:16 DEBUG  TaskList: ## Running Remove registry key...
07-31 09:16 DEBUG  TaskList: ## Finished Remove registry key
07-31 09:16 DEBUG  TaskList: # Finished tasklist
07-31 09:16 INFO   root: Almost finished uninstalling
07-31 09:16 INFO   root: Finished uninstallation
07-31 09:16 DEBUG  CommonBackend: Fetching basic info...
07-31 09:16 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 09:16 DEBUG  CommonBackend: platform=win32
07-31 09:16 DEBUG  CommonBackend: osname=nt
07-31 09:16 DEBUG  WindowsBackend: arch=amd64
07-31 09:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\data\isolist.ini
07-31 09:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:16 DEBUG  WindowsBackend: Fetching host info...
07-31 09:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:16 DEBUG  WindowsBackend: windows version=vista
07-31 09:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:16 DEBUG  WindowsBackend: windows_sp=None
07-31 09:16 DEBUG  WindowsBackend: windows_build=7600
07-31 09:16 DEBUG  WindowsBackend: gmt=-8
07-31 09:16 DEBUG  WindowsBackend: country=US
07-31 09:16 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:16 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:16 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:16 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:16 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:16 DEBUG  WindowsBackend: windows_language=English
07-31 09:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:16 DEBUG  WindowsBackend: bootloader=vista
07-31 09:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283813.640625 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(C: hd 283813.640625 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: uninstaller_path=None
07-31 09:16 DEBUG  WindowsBackend: previous_target_dir=None
07-31 09:16 DEBUG  WindowsBackend: previous_distro_name=None
07-31 09:16 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:16 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:16 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:16 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:16 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:16 DEBUG  CommonBackend: Searching for local CDs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:16 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:16 INFO   root: Running the installer...
07-31 09:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\translations, languages=['en_US', 'en']
07-31 09:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl863F.tmp\translations, languages=['en_US', 'en']
07-31 09:16 INFO   WindowsFrontend: Operation cancelled
07-31 09:16 DEBUG  WindowsFrontend: frontend.quit
07-31 09:16 DEBUG  WindowsFrontend: frontend.on_quit
07-31 09:16 DEBUG  root: application.on_quit
07-31 09:16 INFO   root: sys.exit
07-31 09:16 INFO   root: === wubi 12.04 rev265 ===
07-31 09:16 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 09:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-31 09:16 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\data
07-31 09:16 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\bin\7z.exe
07-31 09:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 09:16 DEBUG  CommonBackend: Fetching basic info...
07-31 09:16 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 09:16 DEBUG  CommonBackend: platform=win32
07-31 09:16 DEBUG  CommonBackend: osname=nt
07-31 09:16 DEBUG  CommonBackend: language=en_US
07-31 09:16 DEBUG  CommonBackend: encoding=cp932
07-31 09:16 DEBUG  WindowsBackend: arch=amd64
07-31 09:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\data\isolist.ini
07-31 09:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:16 DEBUG  WindowsBackend: Fetching host info...
07-31 09:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:16 DEBUG  WindowsBackend: windows version=vista
07-31 09:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:16 DEBUG  WindowsBackend: windows_sp=None
07-31 09:16 DEBUG  WindowsBackend: windows_build=7600
07-31 09:16 DEBUG  WindowsBackend: gmt=-8
07-31 09:16 DEBUG  WindowsBackend: country=US
07-31 09:16 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:16 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:16 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:16 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:16 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:16 DEBUG  WindowsBackend: windows_language=English
07-31 09:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:16 DEBUG  WindowsBackend: bootloader=vista
07-31 09:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283813.480469 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(C: hd 283813.480469 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: uninstaller_path=None
07-31 09:16 DEBUG  WindowsBackend: previous_target_dir=None
07-31 09:16 DEBUG  WindowsBackend: previous_distro_name=None
07-31 09:16 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:16 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:16 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:16 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 09:16 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 09:16 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:16 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:16 DEBUG  CommonBackend: Searching for local CDs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylC052.tmp is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 09:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 09:16 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:16 INFO   root: Running the installer...
07-31 09:16 DEBUG  WindowsFrontend: __init__...
07-31 09:16 DEBUG  WindowsFrontend: on_init...
07-31 09:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\translations, languages=['en_US', 'en']
07-31 09:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylC052.tmp\translations, languages=['en_US', 'en']
07-31 09:16 INFO   WindowsFrontend: Operation cancelled
07-31 09:16 DEBUG  WindowsFrontend: frontend.quit
07-31 09:16 DEBUG  WindowsFrontend: frontend.on_quit
07-31 09:16 DEBUG  root: application.on_quit
07-31 09:16 INFO   root: sys.exit
07-31 09:16 INFO   root: === wubi 12.04 rev265 ===
07-31 09:16 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 09:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-31 09:16 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\data
07-31 09:16 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\bin\7z.exe
07-31 09:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 09:16 DEBUG  CommonBackend: Fetching basic info...
07-31 09:16 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 09:16 DEBUG  CommonBackend: platform=win32
07-31 09:16 DEBUG  CommonBackend: osname=nt
07-31 09:16 DEBUG  CommonBackend: language=en_US
07-31 09:16 DEBUG  CommonBackend: encoding=cp932
07-31 09:16 DEBUG  WindowsBackend: arch=amd64
07-31 09:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\data\isolist.ini
07-31 09:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:16 DEBUG  WindowsBackend: Fetching host info...
07-31 09:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:16 DEBUG  WindowsBackend: windows version=vista
07-31 09:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:16 DEBUG  WindowsBackend: windows_sp=None
07-31 09:16 DEBUG  WindowsBackend: windows_build=7600
07-31 09:16 DEBUG  WindowsBackend: gmt=-8
07-31 09:16 DEBUG  WindowsBackend: country=US
07-31 09:16 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:16 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:16 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:16 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:16 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:16 DEBUG  WindowsBackend: windows_language=English
07-31 09:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:16 DEBUG  WindowsBackend: bootloader=vista
07-31 09:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283812.824219 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(C: hd 283812.824219 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:16 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:16 DEBUG  WindowsBackend: uninstaller_path=None
07-31 09:16 DEBUG  WindowsBackend: previous_target_dir=None
07-31 09:16 DEBUG  WindowsBackend: previous_distro_name=None
07-31 09:16 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:16 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:16 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:16 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 09:16 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 09:16 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:16 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:16 DEBUG  CommonBackend: Searching for local CDs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:16 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 09:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 09:16 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:16 INFO   root: Running the installer...
07-31 09:16 DEBUG  WindowsFrontend: __init__...
07-31 09:16 DEBUG  WindowsFrontend: on_init...
07-31 09:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\translations, languages=['en_US', 'en']
07-31 09:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylE80D.tmp\translations, languages=['en_US', 'en']
07-31 09:16 INFO   WindowsFrontend: Operation cancelled
07-31 09:16 DEBUG  WindowsFrontend: frontend.quit
07-31 09:16 DEBUG  WindowsFrontend: frontend.on_quit
07-31 09:16 DEBUG  root: application.on_quit
07-31 09:16 INFO   root: sys.exit
07-31 09:17 INFO   root: === wubi 12.04 rev265 ===
07-31 09:17 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 09:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 09:17 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\data
07-31 09:17 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\bin\7z.exe
07-31 09:17 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 09:17 DEBUG  CommonBackend: Fetching basic info...
07-31 09:17 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 09:17 DEBUG  CommonBackend: platform=win32
07-31 09:17 DEBUG  CommonBackend: osname=nt
07-31 09:17 DEBUG  CommonBackend: language=en_US
07-31 09:17 DEBUG  CommonBackend: encoding=cp932
07-31 09:17 DEBUG  WindowsBackend: arch=amd64
07-31 09:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\data\isolist.ini
07-31 09:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:17 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:17 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:17 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:17 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:17 DEBUG  WindowsBackend: Fetching host info...
07-31 09:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:17 DEBUG  WindowsBackend: windows version=vista
07-31 09:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:17 DEBUG  WindowsBackend: windows_sp=None
07-31 09:17 DEBUG  WindowsBackend: windows_build=7600
07-31 09:17 DEBUG  WindowsBackend: gmt=-8
07-31 09:17 DEBUG  WindowsBackend: country=US
07-31 09:17 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:17 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:17 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:17 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:17 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:17 DEBUG  WindowsBackend: windows_language=English
07-31 09:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:17 DEBUG  WindowsBackend: bootloader=vista
07-31 09:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283812.683594 mb free ntfs)
07-31 09:17 DEBUG  WindowsBackend: drive=Drive(C: hd 283812.683594 mb free ntfs)
07-31 09:17 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:17 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:17 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:17 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:17 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:17 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:17 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:17 DEBUG  WindowsBackend: uninstaller_path=None
07-31 09:17 DEBUG  WindowsBackend: previous_target_dir=None
07-31 09:17 DEBUG  WindowsBackend: previous_distro_name=None
07-31 09:17 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:17 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:17 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:17 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 09:17 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 09:17 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:17 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:17 DEBUG  CommonBackend: Searching for local CDs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:17 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 09:17 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 09:17 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:17 INFO   root: Running the CD menu...
07-31 09:17 DEBUG  WindowsFrontend: __init__...
07-31 09:17 DEBUG  WindowsFrontend: on_init...
07-31 09:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\translations, languages=['en_US', 'en']
07-31 09:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl6805.tmp\translations, languages=['en_US', 'en']
07-31 09:17 INFO   root: CD menu finished
07-31 09:17 INFO   root: Rebooting
07-31 09:17 DEBUG  TaskList: # Running tasklist...
07-31 09:17 DEBUG  TaskList: ## Running reboot...
07-31 09:17 DEBUG  TaskList: ## Finished reboot
07-31 09:17 DEBUG  TaskList: # Finished tasklist
07-31 09:17 DEBUG  root: application.quit
07-31 09:17 DEBUG  WindowsFrontend: frontend.quit
07-31 09:17 DEBUG  WindowsFrontend: frontend.on_quit
07-31 09:17 DEBUG  root: application.on_quit
07-31 09:17 INFO   root: sys.exit
07-31 09:18 INFO   root: === wubi 12.04 rev265 ===
07-31 09:18 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 09:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 09:18 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\data
07-31 09:18 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\bin\7z.exe
07-31 09:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 09:18 DEBUG  CommonBackend: Fetching basic info...
07-31 09:18 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 09:18 DEBUG  CommonBackend: platform=win32
07-31 09:18 DEBUG  CommonBackend: osname=nt
07-31 09:18 DEBUG  CommonBackend: language=en_US
07-31 09:18 DEBUG  CommonBackend: encoding=cp932
07-31 09:18 DEBUG  WindowsBackend: arch=amd64
07-31 09:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\data\isolist.ini
07-31 09:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:18 DEBUG  WindowsBackend: Fetching host info...
07-31 09:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:18 DEBUG  WindowsBackend: windows version=vista
07-31 09:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:18 DEBUG  WindowsBackend: windows_sp=None
07-31 09:18 DEBUG  WindowsBackend: windows_build=7600
07-31 09:18 DEBUG  WindowsBackend: gmt=-8
07-31 09:18 DEBUG  WindowsBackend: country=US
07-31 09:18 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:18 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:18 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:18 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:18 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:18 DEBUG  WindowsBackend: windows_language=English
07-31 09:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:18 DEBUG  WindowsBackend: bootloader=vista
07-31 09:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283813.789063 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(C: hd 283813.789063 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: uninstaller_path=None
07-31 09:18 DEBUG  WindowsBackend: previous_target_dir=None
07-31 09:18 DEBUG  WindowsBackend: previous_distro_name=None
07-31 09:18 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:18 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:18 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:18 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 09:18 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 09:18 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:18 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:18 DEBUG  CommonBackend: Searching for local CDs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 09:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 09:18 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:18 INFO   root: Running the CD menu...
07-31 09:18 DEBUG  WindowsFrontend: __init__...
07-31 09:18 DEBUG  WindowsFrontend: on_init...
07-31 09:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\translations, languages=['en_US', 'en']
07-31 09:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA9E5.tmp\translations, languages=['en_US', 'en']
07-31 09:18 INFO   root: CD menu finished
07-31 09:18 DEBUG  CommonBackend: Showing info
07-31 09:18 DEBUG  root: application.quit
07-31 09:18 DEBUG  WindowsFrontend: frontend.quit
07-31 09:18 DEBUG  WindowsFrontend: frontend.on_quit
07-31 09:18 DEBUG  root: application.on_quit
07-31 09:18 INFO   root: sys.exit
07-31 09:18 INFO   root: === wubi 12.04 rev265 ===
07-31 09:18 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 09:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-31 09:18 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\data
07-31 09:18 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\bin\7z.exe
07-31 09:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 09:18 DEBUG  CommonBackend: Fetching basic info...
07-31 09:18 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-31 09:18 DEBUG  CommonBackend: platform=win32
07-31 09:18 DEBUG  CommonBackend: osname=nt
07-31 09:18 DEBUG  CommonBackend: language=en_US
07-31 09:18 DEBUG  CommonBackend: encoding=cp932
07-31 09:18 DEBUG  WindowsBackend: arch=amd64
07-31 09:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\data\isolist.ini
07-31 09:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 09:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 09:18 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 09:18 DEBUG  WindowsBackend: Fetching host info...
07-31 09:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 09:18 DEBUG  WindowsBackend: windows version=vista
07-31 09:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 09:18 DEBUG  WindowsBackend: windows_sp=None
07-31 09:18 DEBUG  WindowsBackend: windows_build=7600
07-31 09:18 DEBUG  WindowsBackend: gmt=-8
07-31 09:18 DEBUG  WindowsBackend: country=US
07-31 09:18 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 09:18 DEBUG  WindowsBackend: windows_username=Brad
07-31 09:18 DEBUG  WindowsBackend: user_full_name=Brad
07-31 09:18 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 09:18 DEBUG  WindowsBackend: windows_language_code=1033
07-31 09:18 DEBUG  WindowsBackend: windows_language=English
07-31 09:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 09:18 DEBUG  WindowsBackend: bootloader=vista
07-31 09:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283813.476563 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(C: hd 283813.476563 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 09:18 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 09:18 DEBUG  WindowsBackend: uninstaller_path=None
07-31 09:18 DEBUG  WindowsBackend: previous_target_dir=None
07-31 09:18 DEBUG  WindowsBackend: previous_distro_name=None
07-31 09:18 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 09:18 DEBUG  WindowsBackend: keyboard_layout=us
07-31 09:18 DEBUG  WindowsBackend: keyboard_variant=
07-31 09:18 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 09:18 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 09:18 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 09:18 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 09:18 DEBUG  CommonBackend: Searching for local CDs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylD509.tmp is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 09:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 09:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 09:18 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 09:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 09:18 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 09:18 INFO   root: Running the CD menu...
07-31 09:18 DEBUG  WindowsFrontend: __init__...
07-31 09:18 DEBUG  WindowsFrontend: on_init...
07-31 09:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\translations, languages=['en_US', 'en']
07-31 09:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\translations, languages=['en_US', 'en']
07-31 09:18 INFO   root: CD menu finished
07-31 09:18 INFO   root: Running the CD boot helper...
07-31 09:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\translations, languages=['en_US', 'en']
07-31 09:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\translations, languages=['en_US', 'en']
07-31 09:18 INFO   root: CD boot helper confirmed
07-31 09:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\translations, languages=['en_US', 'en']
07-31 09:18 DEBUG  TaskList: # Running tasklist...
07-31 09:18 DEBUG  TaskList: ## Running select_target_dir...
07-31 09:18 INFO   WindowsBackend: Installing into C:\ubuntu
07-31 09:18 DEBUG  TaskList: ## Finished select_target_dir
07-31 09:18 DEBUG  TaskList: ## Running create_dir_structure...
07-31 09:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-31 09:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-31 09:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-31 09:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-31 09:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-31 09:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-31 09:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-31 09:18 DEBUG  TaskList: ## Finished create_dir_structure
07-31 09:18 DEBUG  TaskList: ## Running uncompress_target_dir...
07-31 09:18 DEBUG  TaskList: ## Finished uncompress_target_dir
07-31 09:18 DEBUG  TaskList: ## Running create_uninstaller...
07-31 09:18 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-31 09:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-31 09:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-31 09:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-31 09:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-31 09:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-31 09:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-31 09:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-31 09:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-31 09:18 DEBUG  TaskList: ## Finished create_uninstaller
07-31 09:18 DEBUG  TaskList: ## Running copy_installation_files...
07-31 09:18 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-31 09:18 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\winboot -> C:\ubuntu\winboot
07-31 09:18 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylD509.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-31 09:18 DEBUG  TaskList: ## Finished copy_installation_files
07-31 09:18 DEBUG  TaskList: ## Running use_cd...
07-31 09:18 DEBUG  TaskList: New task copy_file
07-31 09:18 DEBUG  TaskList: ### Running copy_file...
07-31 09:23 DEBUG  TaskList: ### Finished copy_file
07-31 09:23 DEBUG  TaskList: New task check_iso
07-31 09:23 DEBUG  TaskList: ### Running check_iso...
07-31 09:23 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
07-31 09:23 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
07-31 09:23 DEBUG  Distro:     wrong size: 3997450240 > 900000000
07-31 09:23 DEBUG  TaskList: ### Finished check_iso
07-31 09:23 DEBUG  TaskList: ## Finished use_cd
07-31 09:23 DEBUG  TaskList: ## Running extract_kernel...
07-31 09:23 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
07-31 09:23 DEBUG  TaskList: # Cancelling tasklist
07-31 09:23 DEBUG  TaskList: # Finished tasklist
07-31 09:23 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
07-31 18:00 INFO   root: === wubi 12.04 rev265 ===
07-31 18:00 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 18:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
07-31 18:00 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\data
07-31 18:00 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\bin\7z.exe
07-31 18:00 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 18:00 DEBUG  CommonBackend: Fetching basic info...
07-31 18:00 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
07-31 18:00 DEBUG  CommonBackend: platform=win32
07-31 18:00 DEBUG  CommonBackend: osname=nt
07-31 18:00 DEBUG  CommonBackend: language=en_US
07-31 18:00 DEBUG  CommonBackend: encoding=cp932
07-31 18:00 DEBUG  WindowsBackend: arch=amd64
07-31 18:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\data\isolist.ini
07-31 18:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 18:00 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 18:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 18:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 18:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 18:00 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 18:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 18:00 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 18:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 18:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 18:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 18:00 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 18:00 DEBUG  WindowsBackend: Fetching host info...
07-31 18:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 18:00 DEBUG  WindowsBackend: windows version=vista
07-31 18:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 18:00 DEBUG  WindowsBackend: windows_sp=None
07-31 18:00 DEBUG  WindowsBackend: windows_build=7600
07-31 18:00 DEBUG  WindowsBackend: gmt=-8
07-31 18:00 DEBUG  WindowsBackend: country=US
07-31 18:00 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 18:00 DEBUG  WindowsBackend: windows_username=Brad
07-31 18:00 DEBUG  WindowsBackend: user_full_name=Brad
07-31 18:00 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 18:00 DEBUG  WindowsBackend: windows_language_code=1033
07-31 18:00 DEBUG  WindowsBackend: windows_language=English
07-31 18:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 18:00 DEBUG  WindowsBackend: bootloader=vista
07-31 18:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 279980.609375 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: drive=Drive(C: hd 279980.609375 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 18:00 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 18:00 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-31 18:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-31 18:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 18:00 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 18:00 DEBUG  WindowsBackend: keyboard_layout=us
07-31 18:00 DEBUG  WindowsBackend: keyboard_variant=
07-31 18:00 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 18:00 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 18:00 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 18:00 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 18:00 DEBUG  CommonBackend: Searching for local CDs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 18:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 18:00 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 18:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 18:00 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 18:00 INFO   root: Running the uninstaller...
07-31 18:00 INFO   CommonBackend: This is the uninstaller running
07-31 18:00 DEBUG  WindowsFrontend: __init__...
07-31 18:00 DEBUG  WindowsFrontend: on_init...
07-31 18:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\translations, languages=['en_US', 'en']
07-31 18:00 INFO   root: Received settings
07-31 18:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\translations, languages=['en_US', 'en']
07-31 18:00 DEBUG  TaskList: # Running tasklist...
07-31 18:00 DEBUG  TaskList: ## Running Remove bootloader entry...
07-31 18:00 DEBUG  WindowsBackend: Could not find bcd id
07-31 18:00 DEBUG  WindowsBackend: undo_bootini C:
07-31 18:00 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 279980.609375 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: undo_bootini D:
07-31 18:00 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: undo_bootini E:
07-31 18:00 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 10219.8867188 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: undo_bootini F:
07-31 18:00 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230858.910156 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: undo_bootini H:
07-31 18:00 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 3047.25390625 mb free ntfs)
07-31 18:00 DEBUG  WindowsBackend: undo_bootini J:
07-31 18:00 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 15951.4921875 mb free ntfs)
07-31 18:00 DEBUG  TaskList: ## Finished Remove bootloader entry
07-31 18:00 DEBUG  TaskList: ## Running Remove target dir...
07-31 18:00 DEBUG  CommonBackend: Deleting C:\ubuntu
07-31 18:00 DEBUG  TaskList: ## Finished Remove target dir
07-31 18:00 DEBUG  TaskList: ## Running Remove registry key...
07-31 18:00 DEBUG  TaskList: ## Finished Remove registry key
07-31 18:00 DEBUG  TaskList: # Finished tasklist
07-31 18:00 INFO   root: Almost finished uninstalling
07-31 18:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pyl958A.tmp\translations, languages=['en_US', 'en']
07-31 18:00 INFO   root: Finished uninstallation
07-31 18:00 DEBUG  root: application.quit
07-31 18:00 DEBUG  WindowsFrontend: frontend.quit
07-31 18:00 DEBUG  WindowsFrontend: frontend.on_quit
07-31 18:00 DEBUG  root: application.on_quit
07-31 18:00 INFO   root: sys.exit
07-31 18:12 INFO   root: === wubi 12.04 rev265 ===
07-31 18:12 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 18:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-31 18:12 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\data
07-31 18:12 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\bin\7z.exe
07-31 18:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 18:12 DEBUG  CommonBackend: Fetching basic info...
07-31 18:12 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 18:12 DEBUG  CommonBackend: platform=win32
07-31 18:12 DEBUG  CommonBackend: osname=nt
07-31 18:12 DEBUG  CommonBackend: language=en_US
07-31 18:12 DEBUG  CommonBackend: encoding=cp932
07-31 18:12 DEBUG  WindowsBackend: arch=amd64
07-31 18:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\data\isolist.ini
07-31 18:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 18:12 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 18:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 18:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 18:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 18:12 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 18:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 18:12 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 18:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 18:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 18:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 18:12 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 18:12 DEBUG  WindowsBackend: Fetching host info...
07-31 18:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 18:12 DEBUG  WindowsBackend: windows version=vista
07-31 18:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 18:12 DEBUG  WindowsBackend: windows_sp=None
07-31 18:12 DEBUG  WindowsBackend: windows_build=7600
07-31 18:12 DEBUG  WindowsBackend: gmt=-8
07-31 18:12 DEBUG  WindowsBackend: country=US
07-31 18:12 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 18:12 DEBUG  WindowsBackend: windows_username=Brad
07-31 18:12 DEBUG  WindowsBackend: user_full_name=Brad
07-31 18:12 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 18:12 DEBUG  WindowsBackend: windows_language_code=1033
07-31 18:12 DEBUG  WindowsBackend: windows_language=English
07-31 18:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 18:12 DEBUG  WindowsBackend: bootloader=vista
07-31 18:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 283765.453125 mb free ntfs)
07-31 18:12 DEBUG  WindowsBackend: drive=Drive(C: hd 283765.453125 mb free ntfs)
07-31 18:12 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 18:12 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 18:12 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 18:12 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 18:12 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 18:12 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 18:12 DEBUG  WindowsBackend: drive=Drive(J: hd 15951.4921875 mb free ntfs)
07-31 18:12 DEBUG  WindowsBackend: uninstaller_path=None
07-31 18:12 DEBUG  WindowsBackend: previous_target_dir=None
07-31 18:12 DEBUG  WindowsBackend: previous_distro_name=None
07-31 18:12 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 18:12 DEBUG  WindowsBackend: keyboard_layout=us
07-31 18:12 DEBUG  WindowsBackend: keyboard_variant=
07-31 18:12 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 18:12 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 18:12 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 18:12 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 18:12 DEBUG  CommonBackend: Searching for local CDs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 18:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 18:12 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 18:12 INFO   root: Running the installer...
07-31 18:12 DEBUG  WindowsFrontend: __init__...
07-31 18:12 DEBUG  WindowsFrontend: on_init...
07-31 18:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\translations, languages=['en_US', 'en']
07-31 18:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\translations, languages=['en_US', 'en']
07-31 18:12 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brad
07-31 18:12 INFO   root: Received settings
07-31 18:12 DEBUG  CommonBackend: Searching for local CD
07-31 18:12 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 18:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 18:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 18:12 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 18:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\translations, languages=['en_US', 'en']
07-31 18:12 DEBUG  TaskList: # Running tasklist...
07-31 18:12 DEBUG  TaskList: ## Running select_target_dir...
07-31 18:12 INFO   WindowsBackend: Installing into E:\ubuntu
07-31 18:12 DEBUG  TaskList: ## Finished select_target_dir
07-31 18:12 DEBUG  TaskList: ## Running create_dir_structure...
07-31 18:12 DEBUG  CommonBackend: Creating dir E:\ubuntu
07-31 18:12 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
07-31 18:12 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
07-31 18:12 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
07-31 18:12 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
07-31 18:12 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
07-31 18:12 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
07-31 18:12 DEBUG  TaskList: ## Finished create_dir_structure
07-31 18:12 DEBUG  TaskList: ## Running uncompress_target_dir...
07-31 18:12 DEBUG  TaskList: ## Finished uncompress_target_dir
07-31 18:12 DEBUG  TaskList: ## Running create_uninstaller...
07-31 18:12 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
07-31 18:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
07-31 18:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
07-31 18:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-31 18:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
07-31 18:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-31 18:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-31 18:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-31 18:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-31 18:12 DEBUG  TaskList: ## Finished create_uninstaller
07-31 18:12 DEBUG  TaskList: ## Running copy_installation_files...
07-31 18:12 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
07-31 18:12 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\winboot -> E:\ubuntu\winboot
07-31 18:12 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylFAD2.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
07-31 18:12 DEBUG  TaskList: ## Finished copy_installation_files
07-31 18:12 DEBUG  TaskList: ## Running get_iso...
07-31 18:12 DEBUG  TaskList: New task copy_file
07-31 18:12 DEBUG  TaskList: ### Running copy_file...
07-31 18:17 DEBUG  TaskList: ### Finished copy_file
07-31 18:17 DEBUG  TaskList: New task check_iso
07-31 18:17 DEBUG  TaskList: ### Running check_iso...
07-31 18:17 DEBUG  CommonBackend: Checking E:\ubuntu\install\installation.iso
07-31 18:17 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\installation.iso
07-31 18:17 DEBUG  Distro:     wrong size: 3997450240 > 900000000
07-31 18:17 DEBUG  TaskList: ### Finished check_iso
07-31 18:17 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
07-31 18:17 DEBUG  TaskList: # Cancelling tasklist
07-31 18:17 DEBUG  TaskList: # Finished tasklist
07-31 18:17 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
07-31 23:40 INFO   root: === wubi 12.04 rev265 ===
07-31 23:40 DEBUG  root: Logfile is c:\users\brad\appdata\local\temp\wubi-12.04-rev265.log
07-31 23:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Brad\\Downloads\\ubuntu-12.04-desktop-i386\\wubi.exe"']
07-31 23:40 DEBUG  CommonBackend: data_dir=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\data
07-31 23:40 DEBUG  WindowsBackend: 7z=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\bin\7z.exe
07-31 23:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 23:40 DEBUG  CommonBackend: Fetching basic info...
07-31 23:40 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 23:40 DEBUG  CommonBackend: platform=win32
07-31 23:40 DEBUG  CommonBackend: osname=nt
07-31 23:40 DEBUG  CommonBackend: language=en_US
07-31 23:40 DEBUG  CommonBackend: encoding=cp932
07-31 23:40 DEBUG  WindowsBackend: arch=amd64
07-31 23:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\data\isolist.ini
07-31 23:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 23:40 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 23:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 23:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 23:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 23:40 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 23:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 23:40 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 23:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 23:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 23:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 23:40 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 23:40 DEBUG  WindowsBackend: Fetching host info...
07-31 23:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 23:40 DEBUG  WindowsBackend: windows version=vista
07-31 23:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 23:40 DEBUG  WindowsBackend: windows_sp=None
07-31 23:40 DEBUG  WindowsBackend: windows_build=7600
07-31 23:40 DEBUG  WindowsBackend: gmt=-8
07-31 23:40 DEBUG  WindowsBackend: country=US
07-31 23:40 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 23:40 DEBUG  WindowsBackend: windows_username=Brad
07-31 23:40 DEBUG  WindowsBackend: user_full_name=Brad
07-31 23:40 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 23:40 DEBUG  WindowsBackend: windows_language_code=1033
07-31 23:40 DEBUG  WindowsBackend: windows_language=English
07-31 23:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 23:40 DEBUG  WindowsBackend: bootloader=vista
07-31 23:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 274548.332031 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: drive=Drive(C: hd 274548.332031 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: drive=Drive(E: hd 6405.0234375 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 23:40 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 23:40 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
07-31 23:40 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
07-31 23:40 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
07-31 23:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-31 23:40 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 23:40 DEBUG  WindowsBackend: keyboard_layout=us
07-31 23:40 DEBUG  WindowsBackend: keyboard_variant=
07-31 23:40 DEBUG  CommonBackend: python locale=('en_US', 'cp932')
07-31 23:40 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 23:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 23:40 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 23:40 DEBUG  CommonBackend: Searching for local CDs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 23:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 23:40 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
07-31 23:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
07-31 23:40 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 23:40 INFO   root: Already installed, running the uninstaller...
07-31 23:40 INFO   root: Running the uninstaller...
07-31 23:40 INFO   CommonBackend: This is the uninstaller running
07-31 23:40 DEBUG  WindowsFrontend: __init__...
07-31 23:40 DEBUG  WindowsFrontend: on_init...
07-31 23:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\translations, languages=['en_US', 'en']
07-31 23:40 INFO   root: Received settings
07-31 23:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\translations, languages=['en_US', 'en']
07-31 23:40 DEBUG  TaskList: # Running tasklist...
07-31 23:40 DEBUG  TaskList: ## Running Remove bootloader entry...
07-31 23:40 DEBUG  WindowsBackend: Could not find bcd id
07-31 23:40 DEBUG  WindowsBackend: undo_bootini C:
07-31 23:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 274548.332031 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: undo_bootini D:
07-31 23:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 24874.9101563 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: undo_bootini E:
07-31 23:40 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 6405.0234375 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: undo_bootini F:
07-31 23:40 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 230858.910156 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: undo_bootini H:
07-31 23:40 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 3047.25390625 mb free ntfs)
07-31 23:40 DEBUG  WindowsBackend: undo_bootini J:
07-31 23:40 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
07-31 23:40 DEBUG  TaskList: ## Finished Remove bootloader entry
07-31 23:40 DEBUG  TaskList: ## Running Remove target dir...
07-31 23:40 DEBUG  CommonBackend: Deleting E:\ubuntu
07-31 23:41 DEBUG  TaskList: ## Finished Remove target dir
07-31 23:41 DEBUG  TaskList: ## Running Remove registry key...
07-31 23:41 DEBUG  TaskList: ## Finished Remove registry key
07-31 23:41 DEBUG  TaskList: # Finished tasklist
07-31 23:41 INFO   root: Almost finished uninstalling
07-31 23:41 INFO   root: Finished uninstallation
07-31 23:41 DEBUG  CommonBackend: Fetching basic info...
07-31 23:41 DEBUG  CommonBackend: original_exe=C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe
07-31 23:41 DEBUG  CommonBackend: platform=win32
07-31 23:41 DEBUG  CommonBackend: osname=nt
07-31 23:41 DEBUG  WindowsBackend: arch=amd64
07-31 23:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\data\isolist.ini
07-31 23:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 23:41 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-31 23:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 23:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 23:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 23:41 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-31 23:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 23:41 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-31 23:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 23:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 23:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 23:41 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-31 23:41 DEBUG  WindowsBackend: Fetching host info...
07-31 23:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 23:41 DEBUG  WindowsBackend: windows version=vista
07-31 23:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 23:41 DEBUG  WindowsBackend: windows_sp=None
07-31 23:41 DEBUG  WindowsBackend: windows_build=7600
07-31 23:41 DEBUG  WindowsBackend: gmt=-8
07-31 23:41 DEBUG  WindowsBackend: country=US
07-31 23:41 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-31 23:41 DEBUG  WindowsBackend: windows_username=Brad
07-31 23:41 DEBUG  WindowsBackend: user_full_name=Brad
07-31 23:41 DEBUG  WindowsBackend: user_directory=C:\Users\Brad
07-31 23:41 DEBUG  WindowsBackend: windows_language_code=1033
07-31 23:41 DEBUG  WindowsBackend: windows_language=English
07-31 23:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-31 23:41 DEBUG  WindowsBackend: bootloader=vista
07-31 23:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 274545.554688 mb free ntfs)
07-31 23:41 DEBUG  WindowsBackend: drive=Drive(C: hd 274545.554688 mb free ntfs)
07-31 23:41 DEBUG  WindowsBackend: drive=Drive(D: hd 24874.9101563 mb free ntfs)
07-31 23:41 DEBUG  WindowsBackend: drive=Drive(E: hd 10219.8867188 mb free ntfs)
07-31 23:41 DEBUG  WindowsBackend: drive=Drive(F: hd 230858.910156 mb free ntfs)
07-31 23:41 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-31 23:41 DEBUG  WindowsBackend: drive=Drive(H: removable 3047.25390625 mb free ntfs)
07-31 23:41 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-31 23:41 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
07-31 23:41 DEBUG  WindowsBackend: uninstaller_path=None
07-31 23:41 DEBUG  WindowsBackend: previous_target_dir=None
07-31 23:41 DEBUG  WindowsBackend: previous_distro_name=None
07-31 23:41 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 23:41 DEBUG  WindowsBackend: keyboard_layout=us
07-31 23:41 DEBUG  WindowsBackend: keyboard_variant=
07-31 23:41 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 23:41 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 23:41 DEBUG  CommonBackend: Searching for local CDs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 23:41 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 23:41 INFO   root: Running the installer...
07-31 23:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\translations, languages=['en_US', 'en']
07-31 23:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\translations, languages=['en_US', 'en']
07-31 23:41 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=brad
07-31 23:41 INFO   root: Received settings
07-31 23:41 DEBUG  CommonBackend: Searching for local CD
07-31 23:41 DEBUG  Distro:   checking whether C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-31 23:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-31 23:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 23:41 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-31 23:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\translations, languages=['en_US', 'en']
07-31 23:41 DEBUG  TaskList: # Running tasklist...
07-31 23:41 DEBUG  TaskList: ## Running select_target_dir...
07-31 23:41 INFO   WindowsBackend: Installing into C:\ubuntu
07-31 23:41 DEBUG  TaskList: ## Finished select_target_dir
07-31 23:41 DEBUG  TaskList: ## Running create_dir_structure...
07-31 23:41 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-31 23:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-31 23:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-31 23:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-31 23:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-31 23:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-31 23:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-31 23:41 DEBUG  TaskList: ## Finished create_dir_structure
07-31 23:41 DEBUG  TaskList: ## Running uncompress_target_dir...
07-31 23:41 DEBUG  TaskList: ## Finished uncompress_target_dir
07-31 23:41 DEBUG  TaskList: ## Running create_uninstaller...
07-31 23:41 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Brad\Downloads\ubuntu-12.04-desktop-i386\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-31 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-31 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-31 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-31 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-31 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev265
07-31 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-31 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-31 23:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-31 23:41 DEBUG  TaskList: ## Finished create_uninstaller
07-31 23:41 DEBUG  TaskList: ## Running copy_installation_files...
07-31 23:41 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-31 23:41 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\winboot -> C:\ubuntu\winboot
07-31 23:41 DEBUG  WindowsBackend: Copying C:\Users\Brad\AppData\Local\Temp\pylA87E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-31 23:41 DEBUG  TaskList: ## Finished copy_installation_files
07-31 23:41 DEBUG  TaskList: ## Running get_iso...
07-31 23:41 DEBUG  TaskList: New task copy_file
07-31 23:41 DEBUG  TaskList: ### Running copy_file...
07-31 23:45 DEBUG  TaskList: ### Finished copy_file
07-31 23:45 DEBUG  TaskList: New task check_iso
07-31 23:45 DEBUG  TaskList: ### Running check_iso...
07-31 23:45 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
07-31 23:45 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
07-31 23:45 DEBUG  Distro:     wrong size: 3997450240 > 900000000
07-31 23:45 DEBUG  TaskList: ### Finished check_iso
07-31 23:45 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
07-31 23:45 DEBUG  TaskList: # Cancelling tasklist
07-31 23:45 DEBUG  TaskList: # Finished tasklist
07-31 23:45 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'

```

---

