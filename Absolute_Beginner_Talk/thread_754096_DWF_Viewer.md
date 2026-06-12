---
title: "DWF Viewer?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Gripp on 2008-04-13
NOT DWG. I have QCad installed, it doesn't do the trick.  i need to open and redline DWF files. 

I tried installing Autodesk Design Review 2009 with wine installed, but it hangs on the C+ lib install... i'm guessing it's simply not supported (maybe an older version? but the files i need to review are in 09 format...)

i also found DWF Toolkit 7.3 but it isn't on the repository and i dont know how to install a tarball
even stilll, i'm not certain that the toolkit will allow me to redline the drawings anyways

---

### Post by compiledkernel on 2008-04-13
BRiCsCad was the only one Ive heard of that can do it, and even then, when I was dealing with such applications, you had to wine its installation to get it to work. I think they offer RPMs now (I seem to remember they were talking about a linux version at some point) , you could probably do an alien conversion and get it to work if you wanted to. 

[http://www.bricsys.com](http://www.bricsys.com) I think is their URL, but I might be wrong.

---

### Post by Gripp on 2008-04-13
okay, i got it, but i have no idea how to install it.

---

### Post by compiledkernel on 2008-04-13
what form is the package in, specifically the package name gripp?

---

### Post by Gripp on 2008-04-13
Bricscad-6.0.0020-1.en_US.i386.tgz

the contents of the file dont have anything like .bin .exe etc.  a lot of .so files

there is a regapp file that when i run in the terminal gives me the typical wine errors of not being able to work wubi (cant allocate files or whatever)

---

### Post by compiledkernel on 2008-04-13
cd /to/where/ever/the/file/is

tar zxvf Bricscad-6.0.0020-1.en_US.i386.tgz
cd BrisBricscad-6.0.0020-1.en_US (or the directory that command creates). 
./configure (unless no configuration script is there) 
make
sudo make install

---

### Post by Gripp on 2008-04-15
Thanks
but, nope
it didn't work.  no ./config file, no make file, no install file. 

here is an output of the tgz file:

API
auto.dll.so
base.dcl
binary.trg
bonus.mnl
Bonus.mnu
Bonuspop.mnu
bricscad.desktop
BricsCad-EULA.txt
bricscad.ico
bricscad.menu
BrisDir.txt
db.dll.so
dcl.dll.so
Fonts
geo.dll.so
gr.dll.so
heavyduty.lsp
Help
icad
icadauth.dll.so
icadbrx.lsp
Icad-cm.dwg
icad.dll.so
Icad.dwg
icad.exe.so
icad.fmp
icad.fnt
Icad-imperial.dwg
ICADISO.LIN
icad.lin
ICAD.LIN
icad.lsp
Icad-meter.dwg
Icad-mm.dwg
icad.pat
icad.sds
icad.tip
icad.unt
ICAD.UNT
icadutils.dll.so
ID_S_BONUS11.bmp
ID_S_BONUS12.bmp
ID_S_BONUS13.bmp
ID_S_BONUS14.bmp
ID_S_BONUS15.bmp
ID_S_BONUS16.bmp
ID_S_BONUS17.bmp
ID_S_BONUS1.bmp
ID_S_BONUS2.bmp
ID_S_BONUS3.bmp
ID_S_BONUS4.bmp
ID_S_BONUS5.bmp
ID_S_BONUS6.bmp
ID_S_BONUS7.bmp
ID_S_BONUS8.bmp
ID_S_BONUS9.bmp
ID_S_EXPLL.bmp
Image.dcl
imagemenu.dll.so
imagemenu.lsp
ImageMenu.txt
layerstatus.lsp
libauto.dll.so
libdb.dll.so
libdcl.dll.so
libgeo.dll.so
libgr.dll.so
libicadauth.dll.so
libicadutils.dll.so
libmfc42.dll.so
libpc3ed.dll.so
libpstyleed.dll.so
libstd.dll.so
licensemanager3.dll.so
mfc42.dll.so
objproptb.dll.so
Patterns
pc3app
pc3app.dll.so
pc3app.exe.so
pc3ed.dll.so
Plot\ Styles
Plotters
profileseditor.dll.so
pstyleapp
pstyleapp.dll.so
pstyleapp.exe.so
pstyleed.dll.so
r18tor15.dll.so
readme-bonustools.txt
readme.htm
regapp
regapp.dll.so
regapp.exe.so
Samples
std.dll.so
sysvarstack.lsp
userprofilemanager
userprofilemanager.dll.so
userprofilemanager.exe.so
WinePatch
xrm.dll.so

i'm guessing its a binary...

---

### Post by zipperback on 2008-05-29
[http://www.varicad.com/en/home/](http://www.varicad.com/en/home/)

This will do what you want. And there is a free view application available as well. They have it available in a .deb file so it will install on your ubuntu systems without problem. I installed the viewer and use it quite often.

Hope this helps you.
- zipperback
:popcorn:

---

### Post by darsovidus on 2008-06-05
Varicad does indeed have a free viewer for the following file types: *.dwb, *.stp, *.step, *.dwg, *.dxf, *.igs, *.iges

However unless I missed something it does not support *.DWF files which makes this program irrelevant to this thread which is concerned with the viewing of *.DWF files.

*.DWG and *.DWF files are not the same and because a program can view *.DWG files does not mean it will view *.DWF files by default. 

Autodesk Design Review is such a program that can view *.DWF files however it currently only functions with Windows. 

In my situation at work certain government entities require that I use *.DWF house plan drawings when submitting for permits. This is the format they chose and require for their system. 

I am not a programmer by any means, but have switched my laptop at work over from Windows to Linux. So far so good for the most part. Networking and everyday tasks are wonderful to work with except this one thorn in my side. *.DWF files.

I have been eying Linux for quite some time and have tried out approximately 8 different distributions before settling with one. This disappointment is what I was afraid would happen. I cannot be 100% productive because of limited compatibility solutions related to my specific needs. This is just one example of why people are reluctant to switch to Linux from Windows. So far, it has been an endless and fruitless search with no viable suggestions found. If people have to spend hours searching for non-existent packages that support their everyday needs then they will waste money on a more "mainstream" OS so they can spend more time working and less time scouring forums. 

It is hard for me to believe that there is not one single solution out there for this problem and that *.DWF files are completely unsupported in Linux. 

Any solutions or suggestions as to how to address this problem would be wonderful. I am not down on the Linux community, programmers, or developers I am just deeply disappointed that I cannot use Linux as my sole OS.

On to Bricscad to see if that works....

PS-I do not have Wine on my system and do not want it on my system. The packages and programs on my system are either going to be for Linux or I may as well just go back to Windows. Why reach around the back of my head to scratch my nose?

---

