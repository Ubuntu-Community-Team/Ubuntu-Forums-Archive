---
title: "[PPC] Finally Lubuntu Run on my Quad G5"
date: 2014-05-02
forum: Apple Hardware Users
---

### Post by luigiburdo on 2014-05-02
Yesterday i finally have Lubuntu PPC work on my Quad G5 2.5 ghz  was since 12.x i was try to have it start the installation on my machine with X1900gt but without success...  every time i had a black screen when the graphic system turn on ...   i had been try all the distro ppc on the net from ubuntu to gentoo with fedora all didn't have Xog running all dont attach the video , i swapped my X1900gt with Nv6600 but with the same result...  After some strange message on other distos (no x86 bios compatible ) regarding the video board .. yesterday the idea ...  I put a RadeonHD 4450 Pcie on my Late 2005 G5 with 2 monitor ... One monitor was for Open firmware and mac os X board (ppc bios) the X1900 ...  The other i use for the RadeonHD board ...   Turn on the machine and Surprise everything on Lubuntu 14.x start run , i make the installation (everything goes ok) , and now i have Lubuntu installed and working on my machine. I have the reported bug of bed colors on mesa , but Xeno74 gave me today a tip i will test later the unofficial build ...  why of my post  ? because thanks of Lubuntu i can have the new video board run on my machine :) Not all know that the last video board "officially" working on G5 late 2005 are the X1900 Gt 256mb and the Nvidia 7800gtx 512mb..   If the dev need i can help making the report of all problems  i will encounter during my Lubuntu Quad G5 Experience   Thanks for all  Luigi (tlosm)

---

### Post by bapoumba on 2014-05-02
Moved to Apple Users.

---

### Post by luigiburdo on 2014-05-02
Thanks and sorry for my mistake :P

Edit: 
I forget to mention : I have the video full working from Hdmi of the RadeonHD and the Audio too :) :)

---

### Post by bapoumba on 2014-05-02
> **luigiburdo said:**
> Thanks and sorry for my mistake :P

Edit: 
I forget to mention : I have the video full working from Hdmi of the RadeonHD and the Audio too :) :)
No worries, the Apple Users subforum is a little hidden ;)
It is dedicated to people running Ubuntu on Apple hardware. You'll find interesting threads in here.

---

### Post by xeno74 on 2014-05-02
> **luigiburdo said:**
> Yesterday i finally have Lubuntu PPC work on my Quad G5 2.5 ghz 
was since 12.x i was try to have it start the installation on my machine with X1900gt but without success... 
every time i had a black screen when the graphic system turn on ... 

i had been try all the distro ppc on the net from ubuntu to gentoo with fedora all didn't have Xog running all dont attach the video , i swapped my X1900gt with Nv6600 but with the same result... 
After some strange message on other distos (no x86 bios compatible ) regarding the video board .. yesterday the idea ... 
I put a RadeonHD 4450 Pcie on my Late 2005 G5 with 2 monitor ...
One monitor was for Open firmware and mac os X board (ppc bios) the X1900 ... 
The other i use for the RadeonHD board ... 

Turn on the machine and Surprise everything on Lubuntu 14.x start run , i make the installation (everything goes ok) , and now i have Lubuntu installed and working on my machine.
I have the reported bug of bed colors on mesa , but Xeno74 gave me today a tip i will test later the unofficial build ...

why of my post  ? because thanks of Lubuntu i can have the new video board run on my machine :)
Not all know that the last video board "officially" working on G5 late 2005 are the X1900 Gt 256mb and the Nvidia 7800gtx 512mb..


If the dev need i can help making the report of all problems  i will encounter during my Lubuntu Quad G5 Experience 

Thanks for all 
Luigi (tlosm)

That's very interesting! Thanks for posting your experience! :-)

---

### Post by luigiburdo on 2014-05-02
Thanks xeno but i think will need a better optimization. 
First thing:
 after launching the "software updater" tool the system become totally unstable (some kernel upgrades?)
Second thing 
The second video card (macosx side) spinning like mad ... some time yes some times no... 
Third thing 
I try to upgrade the MesaLibs like in Hyperion Entertainment forum but i dont have success in installing ... there is a svn for this unofficial release? :P
Im not really good with linux was from Apus in 2001 i stop using it .
i have to re enter in matrix :P

another thing how to know if my system is running on Quad cpu and not only in single ? i have a strange feeling ..

---

### Post by luigiburdo on 2014-05-02
Edit: I had been found a Monitor for Cpu the system run in Multi Core but
 when i run the System Information and run a benchmark eg CPU blowFish only CPU3 on 4 running the bench.

---

### Post by xeno74 on 2014-05-03
> **luigiburdo said:**
> 
I try to upgrade the MesaLibs like in Hyperion Entertainment forum but i dont have success in installing ... there is a svn for this unofficial release? :P


The installation is very simple.

Unofficial Mesa packages downloads: [http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html](http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html)

_**Install instructions for example for Mesa 10.0.3 unofficial**_: 


[LIST=1]
[*] Unpack the archive MesaLib-10.0.3-powerpc-unofficial.tar.bz2 
[*] Copy it as root to the directory **/usr/local/** -> sudo cp -R mesa10 /usr/local/ 
[*]Set up the new library path -> export LD_LIBRARY_PATH=/usr/local/mesa10/lib 
[*]Test it with **glxgears**. When you see the correct colors then you use the new version of Mesa. After that you can start some games for example **Neverball**. 
[/LIST]

If you want that Mesa works system wide then you have to add the line **export LD_LIBRARY_PATH=** to the **.profile** file in your home directory.

SuperTuxKart needs a special **run_game.sh** for the new Mesa: LD_LIBRARY_PATH=./bin/:/usr/local/mesa10/lib bin/supertuxkart

Another thread: [http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2359](http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2359)

---

### Post by luigiburdo on 2014-05-03
Thank you Xeno :P
I will check it .
 
I have to check better why after installing some simple packages taken from the "Lubuntu Software Center" the machine start have a core dump and become ultra super unstable... and force me reinstall everything from beginning.
Plus need to understand if the temperatures sensors is working inside "in lubuntu side" for the automatic spinning of fans and the pump when the cpu start becoming hot

---

### Post by luigiburdo on 2014-05-03
Edit: the cpu sensor is working i use Gkrellm and look like everything is ok 
for make the audio working i installed Kmix 

now is time to check the mesa ;)

---

### Post by luigiburdo on 2014-05-03
Xeno, umm i test with the last build unofficial from your website and nothing change to me , probably i make something wrong ,
but i see the same wrong colors form the hyperion forums shots...
In any way good job with X1000 :D

---

### Post by luigiburdo on 2014-05-03
umm ... after installing something that need qt4 the system become really unstable
example after installing one of the Qmu build with Qt interface i dont have any moore the icons and the start bar 
of the desktop .... the system become unusable and i have to reinstall all
How to updated a bug ticker and contribute/help for better system performances?

---

### Post by luigiburdo on 2014-05-03
It thread is linked on Apple Support and on Other Apple Users site :) hope it will increase the users and the developing 

@xeno74
I test the unofficial 10.4 and the 10.3 
but no positive result :( i think something is different from the X1000 kernel and G5 ;) 
I hope in future release for now we can scream to a miracle for have lubuntu working on this great machines 

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/IMG_3597_zpsa594e423.jpg[/IMG]

---

### Post by luigiburdo on 2014-05-05
I make a small step up i heve the right summary for the video board :P but colors in glx are not good :P

Note i try to swap the video board x1900(osx) to pci 8x slot and the RadeonHd to pcie 16x, this is not influent on MacOsX side i make some tests and dont effect the overall performances ... but in Lubuntu (linux) side i found many problems in stability (i had re installed everything form beginning but with no success too) ... i return all to original configuration X1900 on Pcie 16x and RadeonHD on 8x slot


[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/snapshot1_zpsf9eea402.png[/IMG]

---

### Post by luigiburdo on 2014-05-05
Continue investigating ...
I installed cairo dock and look like the composite system is not running and cant be activated 

plus i make a timedemo of Quake3 (with wrong colors) and i have on the RadeonHD very less performances compared with the (x1900) on the MacOsX side.
Demo four RadeonHD 82fps at 1280x1024 (lubuntu)
Demo four X1900gt  390fps at 1280x 1024 (macOsx)

---

### Post by luigiburdo on 2014-05-05
Something need to  be optimized 

luigi@luigi-desktop:~$ cat /proc/cpuinfo
processor    : 0
cpu        : PPC970MP, altivec supported
clock        : 2500.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 1
cpu        : PPC970MP, altivec supported
clock        : 2500.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 2
cpu        : PPC970MP, altivec supported
clock        : 2500.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 3
cpu        : PPC970MP, altivec supported
clock        : 2500.000000MHz
revision    : 1.1 (pvr 0044 0101)

timebase    : 33333333
platform    : PowerMac
model        : PowerMac11,2
machine        : PowerMac11,2
motherboard    : PowerMac11,2 MacRISC4 Power Macintosh 
**detected as    : 337 (PowerMac G5 Dual Core)** <--- it is a quad core
pmac flags    : 00000000
**L2 cache    : 1024K unified** <-- is 1mb for core 4mb total
pmac-generation    : NewWorld


[B]but some time cat /proc/cpuinfo 
gave me this too... [/B]

luigi@luigi-desktop:~$ cat /proc/cpuinfo
processor    : 0
cpu        : PPC970MP, altivec supported
clock        : 1250.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 1
cpu        : PPC970MP, altivec supported
clock        : 1250.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 2
cpu        : PPC970MP, altivec supported
clock        : 1250.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 3
cpu        : PPC970MP, altivec supported
clock        : 1250.000000MHz
revision    : 1.1 (pvr 0044 0101)

timebase    : 33333333
platform    : PowerMac
model        : PowerMac11,2
machine        : PowerMac11,2
motherboard    : PowerMac11,2 MacRISC4 Power Macintosh 
detected as    : 337 (PowerMac G5 Dual Core)
pmac flags    : 00000000
L2 cache    : 1024K unified
pmac-generation    : NewWorld

---

### Post by xeno74 on 2014-05-07
Very interesting thread. Thanks a lot. :-)

---

### Post by aperez-6 on 2014-05-07
> **luigiburdo said:**
> Something need to  be optimized 

luigi@luigi-desktop:~$ cat /proc/cpuinfo
processor    : 0
cpu        : PPC970MP, altivec supported
clock        : 2500.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 1
cpu        : PPC970MP, altivec supported
clock        : 2500.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 2
cpu        : PPC970MP, altivec supported
clock        : 2500.000000MHz
revision    : 1.1 (pvr 0044 0101)

processor    : 3
cpu        : PPC970MP, altivec supported
clock        : 2500.000000MHz
revision    : 1.1 (pvr 0044 0101)

timebase    : 33333333
platform    : PowerMac
model        : PowerMac11,2
machine        : PowerMac11,2
motherboard    : PowerMac11,2 MacRISC4 Power Macintosh 
**detected as    : 337 (PowerMac G5 Dual Core)** <--- it is a quad core


This is expected. All "quad core" G5 PowerMacs are actually dual-socket, two-core systems. 



> 
pmac flags    : 00000000
**L2 cache    : 1024K unified** <-- is 1mb for core 4mb total
pmac-generation    : NewWorld


[B]but some time cat /proc/cpuinfo 
gave me this too... [/B]

luigi@luigi-desktop:~$ cat /proc/cpuinfo
processor    : 0
cpu        : PPC970MP, altivec supported
clock        : 1250.000000MHz

pmac-generation    : NewWorld

The 1.25GHz "resting" clock rate is also likely expected behavior, when the machine is mostly idle. Play with the kernel CPU governor settings if you wish to waste energy 24/7 by having this run full-bore :)

---

### Post by luigiburdo on 2014-05-08
hi  				 				 					 						 	[**[COLOR=#000000]aperez-6[/COLOR]**]("http://ubuntuforums.org/member.php?u=1922367") ;)
Thank you for explanations , they are really appreciated. Im an old linux user and return on it after 10 years... I was using LinuxApus PPC with RedHad 5 many many yerars ago (im becoming old :( :( ) and many things change in years plus my memory need to remember this Os and isnt really simple :P

Now is time to return in topic ;)

About the cores , i know the machine have 2 sockets with 2x core on , i have here 2x G5 Quad and one is working with only one of this modules on it (pratically is two core:P) 
Cpu0 and Cpu1 (first two core) in the hardware are the top socket on the Logic Board and this are essenzial for make the machine turn on and work the other two Cpu2 and Cpu3 are pratically used as extras.

About the cat /proc/cpuinfo 
The 1250mhz i have if i make the same command exactly after see the before infos ,what make me really courious is the L2 cache infos 1024 unified.
if the cat /proc/cpuinfo was referring one 2xcpu module have to gave me 2048 in total , and 4096 for the two modules in total.
I think the kernel is referring to an older model and not the quad i found many many thread about this question on google "337 powermac G5".

im pretty sure after checking all the web for weaks (monts) this is the first G5 Quad with linux finally working with Xorg and this thankyou of the RadeonHD and the good support of  it in the Lubuntu 14.04 distro ... all the other distros work only with terminal and there is no way for have the Xorg running, probably there i will need to install the new Xorg radeon driver for have a positive result , but Lubuntu run from the first beginning and is for now the first linux distro who make this.

Another strange thing is the bogomips . the system information geve me 0 .

and another thing is the "Hurricane spinning" of the X1900gt:
If run MacOS X first and after reboot in Lubuntu the X1900 fan is quite and not make me become creazy
If i run first Lubuntu i will need something in my ears because look like a jet taking off  :P

---

### Post by luigiburdo on 2014-05-08
thank you Xeno :P

---

### Post by luigiburdo on 2014-05-08
Today i make another test.
I put the Nvidia 7800gtx 512mb swapped with the Radeon 1900gt and now i dont have the video any more on the RadeonHD in the linux side...
will make more tests and reports

---

### Post by luigiburdo on 2014-05-08
With the 7800Gtx the ubuntu installation stop working ... inst possible to install Lubuntu..

new test incoming ...

---

### Post by luigiburdo on 2014-05-08
Swapped the Video Board the Nvidia on the 8x and the RadeonHD on the 16x pcie ... Nvidia is inizialized and video is present during the installation process i can see the "Lubuntu logo" after graphic become totally glitch and unusable ...

For now i can confirm the only way for have Lubuntu on G5 working and installed is have RedeonHD on 8x and Radeon 1900gt on 16x
and it is the only way for have a better and newer video board working on Quad G5 too ;)

---

### Post by luigiburdo on 2014-05-09
Debian 7.5 is compatible with 7800gtx 512mb with the Glx working... Lubuntu not :-/
cat /proc/cpuinfo gave me the same problems with lubuntu there but not show me the 1250mhz bug
Ok ...more investigating

---

### Post by luigiburdo on 2014-05-11
Ok i understood the arcane 
For use a RadeonHD working is needed for sure another radeon (Apple flashed)on Pcie 16x and the new video board unsupported by Apple Osx (X86 flashed) have to stay on the 8x pcie slot ...
In this way The radeon hd will work without problems ... 
Only thing needed now is fix the color on Mesa/Gallium 3d and improve the overall performances. I bit sure will be the next step of Lubuntu distros ;)

---

### Post by xeno74 on 2014-05-11
> **luigiburdo said:**
> Ok i understood the arcane 
For use a RadeonHD working is needed for sure another radeon (Apple flashed)on Pcie 16x and the new video board unsupported by Apple Osx (X86 flashed) have to stay on the 8x pcie slot ...
In this way The radeon hd will work without problems ... 
Only thing needed now is fix the color on Mesa/Gallium 3d and improve the overall performances. I bit sure will be the next step of Lubuntu distros ;)

Thank you for your explanation. Very interesting. :-)

---

### Post by yangdh on 2014-05-11
> **luigiburdo said:**
> Debian 7.5 is compatible with 7800gtx 512mb with the Glx working... Lubuntu not :-/
cat /proc/cpuinfo gave me the same problems with lubuntu there but not show me the 1250mhz bug
Ok ...more investigating
Did you run 7800GTX on Debian using Nouveau driver with HW acceleration? Is the system running 32-bit or 64-bit one? Thank you.

---

### Post by luigiburdo on 2014-05-12
HI yagdh.
I tested my 7800gtx with Lubuntu and graphic is corrupted and cant make me start the installation, Noveau driver dont seems work proprely .
On Wheezy it is working but the performances there are not the top the nv6600 driver is more optimized and faster compared the 7800gtx  in some application 4x more faster.
Some times on 7800 on Gnome3 there are some flash with glitched graphic but the glxgears gave me really great results on 7800 compared with nv6600 and on yabause (sega saturn emulator) is better 6600 vs 7800 
with the two boards Gnome3 is really faster and enjoyable gave great system responds.
Example (debian look like isnt with vsync)
Glxgears 340 to 360 fps on 7800 
Glxgears 140 to 160 fps on 6600
Yabuze 
32 to 64 fps on 7800
58 to 120 fps on 6600
MacOSx is more slower compared the linux side but it is a really old build 

But note no audio on wheezy pulse audio is dummy(!) and i try with all the way for have it running but without result

On Lubuntu
Yes Audio (hdmi from Radeon HD ) yes 3d yes 2d acceleration but 3D colors and Opengl are wrong (sdl too)
Glxgears is 59/60fps (vsync) 
yabause on Lubuntu have problems with rendering in Gl mode but works in multithreading and software mode with audio too.

About the system wheezy with installed 64bit kernel report me the system is 32bit SMP 
Probably soon i will test if is possible  put a recent nv video board in couple with the old nv like i did on radeon..

i have the feeling this boards are working because the system think it is running in Sli mode 


On Lubuntu 
kernel report me is 64bit SMP
but the system in lubuntu is really much unstable compared with wheezy probably will need more optimization or everything depend by Video drivers i dont now ...
for make the system be much more stable i have to turn off the machine and wait 15 seconds and strange the system return bette (? ram cache????)
im pretty sure everything will better in future



I forget to mentions , im pretty sure the trick used (radeonhd in couple with X1900) on my Quad G5 can work on oldest agp machine ...
Probably if someone can test a Radeon HD on a Pcie->PCi apaptor in couple with an old radeon Agp board will be great


Every day i found new system upgrades (on lubuntu) and the machine become everyday more stable i think the devs working without any pause , every day i 
send notifications when i have a core dump or software crashes ... plus i noticed the devs about this thread hope will help their work ;)

Next step will be test the Kvm mod ;)


Hope my help will make the PowerPc user more motivated and will gave a little help to the new powerpc systems like (x5000) or power.org machine

---

### Post by luigiburdo on 2014-05-12
My lpci can be useful :P
[[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/IMG_3633_zpsfd69330b.jpg[/IMG]](http://s1249.photobucket.com/user/tlosm/media/IMG_3633_zpsfd69330b.jpg.html)

---

### Post by luigiburdo on 2014-05-12
Just a small Video :) 

[https://www.youtube.com/watch?v=zp_IvG7h5_0&feature=youtu.be](https://www.youtube.com/watch?v=zp_IvG7h5_0&feature=youtu.be)

---

### Post by yangdh on 2014-05-13
Could you also upload  Xorg.0.log, dmesg, lsmod and xorg.conf(when applicable)? I have much interest in it.
Thank you.

---

### Post by luigiburdo on 2014-05-13
Yes i will do it after work . 
the only one problem **i try to enter in root directory as superuser from terminal but without positive result** , i was need the Xorg.conf for understand why wheezy continue try use X1900 and fail (no video Xrg only terminal) and Lubuntu use the RadeonHD from beginning ... Im thinking (supposing) is something related the kernel on Lubuntu is  3.13 on wheezy is 3.3 but better be sure .
[B]If some one can help to retrive the Xorg conf from Lubuntu root i think will be really appreciated.


[/B]Note : i had been buy a 6570 2gb ... soon a new test 8)

---

### Post by yangdh on 2014-05-13
> **luigiburdo said:**
> Yes i will do it after work . 
the only one problem **i try to enter in root directory as superuser from terminal but without positive result** , i was need the Xorg.conf for understand why wheezy continue try use X1900 and fail (no video Xrg only terminal) and Lubuntu use the RadeonHD from beginning ... Im thinking (supposing) is something related the kernel on Lubuntu is  3.13 on wheezy is 3.3 but better be sure .
[B]If some one can help to retrive the Xorg conf from Lubuntu root i think will be really appreciated.


[/B]Note : i had been buy a 6570 2gb ... soon a new test 8)
Can't 'sudo' be used to get root privilege? Can't you even access '/etc/X11' directory?

---

### Post by luigiburdo on 2014-05-13
i had been try with "sudo  su -user password" , and with "su -user  password" ... on root without results  (access to root deny) ... i will try after work in /etc/x11

---

### Post by yangdh on 2014-05-13
How about "sudo ls /etc/X11"? Some systems won't let normal users escalate to root privilege, but you can use "sudo" to execute some commands of superuser, after the right user's password has been typed when asked.

---

### Post by luigiburdo on 2014-05-13
will check later and report...
today i found only 183 mb of updates to the clean 14.04 system :)

---

### Post by luigiburdo on 2014-05-13
sudo ls /root = permission dienied

About /etc/X11 i enter there , what do you need from there ?


[B]updated the system and the Kernel 3.13.29 make a core dump when the system boot.
[/B]i been reinstalled everything :P

---

### Post by yangdh on 2014-05-13
> **luigiburdo said:**
> sudo ls /root = permission dienied

About /etc/X11 i enter there , what do you need from there ?


[B]updated the system and the Kernel 3.13.29 make a core dump when the system boot.
[/B]i been reinstalled everything :P
xorg.conf file should be there.
 Wasn't you asked to enter root password when you installed Lubuntu? Can Lubuntu be booted as single user mode? If yes you can add normal users in the file '/etc/sudoers' when you run the system in this mode.
I'd like to see your Xorg.0.log, xorg.conf, and dmesg. Could you upload these files at your convenience? Thank you.

---

### Post by alan26 on 2014-05-13
I'm lost, but this is a pretty cool thread, learned a few things, thanks!

---

### Post by yangdh on 2014-05-13
> **luigiburdo said:**
> Ok i understood the arcane 
For use a RadeonHD working is needed for sure another radeon (Apple flashed)on Pcie 16x and the new video board unsupported by Apple Osx (X86 flashed) have to stay on the 8x pcie slot ...
In this way The radeon hd will work without problems ... 
Only thing needed now is fix the color on Mesa/Gallium 3d and improve the overall performances. I bit sure will be the next step of Lubuntu distros ;)
If you can boot Lubuntu to the console with an PC card in PCIEx16 slot and an ATI or Nvidia mac card in another PCIE slot, maybe you could make the things go further by tweaking the xorg.conf file. By specifying right video drivers for different PCI buses where the video cards are accordingly, you may make X working in this configuration.
When you want to get root privilege you can boot to Lubuntu recovery mode described in this link:
[http://ubuntuforums.org/showthread.php?t=2142634](http://ubuntuforums.org/showthread.php?t=2142634)
Thanks for your experiments!

---

### Post by luigiburdo on 2014-05-14
@[**[COLOR=#000000]yangdh[/COLOR]**]("http://ubuntuforums.org/member.php?u=1923223")
I can help on everything  im here for this , share my esperiences wirth all users , my hope is with this  i can help all the G5 users and devs for make a better life to our great machine right now totally alone and unsupported by Apple in hardware too... break the wall of Video Boards is a great advantage.

About your ask
After work at home i will try to upload and share the configs and everything needed, im in italy and here the working day start now :P

I will try to have the root privilage using the theread you posted me , Xorg.conf im pretty sure is in the /root directory because was there in the Wheezy distro.
During install sprocess Lubuntu differing from the wheezy bercause the second ask me for make a  root user and root password and the second pass is make an user and a password for it.
on Lubuntu i dont have this opportunity just ask for make and user and a password for it.
Thanks for your tips and help ;)

@[**[COLOR=#000000]alan26[/COLOR]**]("http://ubuntuforums.org/member.php?u=1923675")
Thank you for motivate my esperiences :P


Now is time to share some other esperiences 
I installed a **simple game **a pacman clone "**tomato"** (sorry i dont remember the name) it use sdl , and there was wrong colors and trasparents sprites.
I test the **mozilla plugin gnash **"the flash player" and i can see only one frame of the video... on wheezy was running perfect at 720p res too. 

I think everything is related to the wrong video board configurations of 3d gnash use opengl if i right undestand

Tested the **VLC **and a huge 3.2 gb Mkv 1080p with surround audio and was running perfect with only 30% of one cpu core. it means the GPU video accelerations are running in right way.

---

### Post by yangdh on 2014-05-14
@[[COLOR=#000000]luigiburdo[/COLOR]]("http://ubuntuforums.org/member.php?u=1921200")[COLOR=#000000][FONT=Microsoft YaHei]   

Thank you for your valuable work. I'd like to know if you can boot to a console with Nv 6600 card in PCIEx8 slot and HD card in PCIEx16 slot using Lubuntu. From my experience Nouveau driver has problems with HW acceleration on PPC64, a way to work around is to pass kernel param "NoAccel=1" when loading the kernel. I tried Fedora 20 on my PowerMac G5 2.0 with Nv 6800Ultra AGP card months ago, and succeeded in installation when HW acceleration was disabled. I had only garbage or artifacts when acceleration was enabled(which is default for Nouveau drivers).
I think if you use ATI HD card with an Nv card, you could follow the steps below:
1). Install the kernel and boot to a console(Does Yaboot of Lubuntu have an option of booting to tty?).
2). Install Xorg and Gnome.
3). Edit xorg.conf, in the Nv card section enable "NoAccel=1" Option.
4). Execute "startx" in the console. 
The X and Gnome should run. I haven't tried to run Lubuntu on my G5 with two video cards.
In Fedora 20 PPC version the boot loader is Grub2, you can insert directly the kernel param when it's called and shown on the screen. Don't know if Yaboot loader could also be edited online to pass param in the same way. You could install Lubuntu all the way through if Yaboot can accept param when running, without the trouble of following steps.[/FONT][/COLOR]

---

### Post by luigiburdo on 2014-05-14
On debinan Wheezy 7.5 i have Xorg with Nouveau full working without problem (only small glitch some times random, with compositing windows) with Hardware acceleration and no 3d wrong colors  do you downloaded the 7.5 ? Note i use the DVD version not the net version. 
From my previus tests where 
Pcie 16x + Pcie 8x
Lubuntu:

x1900 + Nv i had black screen during installation process and system dont run .
Nv + RadeonHD same like previous post.
Nv 6600 and/or Nv 7800Gtx .. Lubuntu Logo and after graphic totally glitched and unusable pretty sure no acceleration will make right graphic .
RadeonHD + X1900 right installation and right graphic (3d with same problems) but really unstable system (the video exit only on the RadeonHD)
X1900 + RadeonHd = everything perfect only 3d color wrong (the video exit only on radeon hd)
x1900 only no video

Fedora 20
Nv6600 No video 
X1900  No Video 
Nvidia 7800  No video
X1900 + RadeonHD ... I have the Video (terminal only, didn't check the xorg, video on RadeonHD) :) 


Gentoo 
Nv no video
X1900 + RadeonHD ... I have the Video (terminal only, didn't check the xorg, video on the RadeonHD) :) 

Debian 
Nv 6600 with Nv 7800Gtx Perfect video but only on first video board
Nv 7800Gtx  with Nv 6600 Perfect video but only on first video board
Video Boards Nv alone perfect like previus post
Radeon X1900  No video (terminal only Xorg error)
X1900 and Radeon HD (terminal only,Xorg error on video ,video only on the first video board)


YellowDog 6.5
Nv6600 and 7800gtx No video
X1900 Video but glitches  not usable 
X1900 and RadeonHd not tested but sure because really hold built will be same as previous post


On the X1900 where you can see Terminal only i found on terminal Xorg asking for X86 firmware for the video boards.... and there i have the idea to put a second Pcie in the machine 
PowerMac G5 have 4 Pcie slots from the down to up Pcie 16x, Pcie 4x, Pcie 8x, Pcie 4x ... i put the RadeonHd on the PCie 4x too and was working there too.. but for speed is better the 8x.
Have it running on 16x will be for sure better.
I will test with RadeonHd 6570 if it will work on Lubuntu without system freeze on the 16x with radeonHd 1900x on the 8x slot.

---

### Post by yangdh on 2014-05-14
Thank you for your very informative explanations. It's really interesting! I would plan to get some hardware if you had a positive result about HD6570.  
PS: By "No video" do you mean a totally black screen even no Yaboot info, except your further explanations in parentheses?

---

### Post by luigiburdo on 2014-05-15
> **yangdh said:**
> Thank you for your very informative explanations. It's really interesting! I would plan to get some hardware if you had a positive result about HD6570.  
PS: By "No video" do you mean a totally black screen even no Yaboot info, except your further explanations in parentheses?

Hi Yangdh
Yaboot is an  open firmware (macos bios) software and all distros (old and ancient too)  it make a video exit  but only on the apple flashed video board,
after loading ramdisk and inizializing linux kernel  the video become black ( i cant see the loading modules too).
Note i test **with the ofonly **too for all the distros** without positive results**, Im sure is something related kernel signals probably in future will be better.

eg: the kernel of debian wheezy 7.5 is more older but much better optimized for Nv pcie gpu compared the Lubuntu/fedora/gentoo.

The other difference of the Debian compared with the other distro is: the X1900 is used but in terminal only (no xorg) after launching xinit i had there the message of 
**"no X86 bios found" **etc etc... (and there the idea... the lucky things was that i have a free 4650HD at home :P)
**Lubuntu/fedora/gentoo **look like the kernel dont like the macbios modded  Radeon (x1900) and pratically dont use this board for **use directly **the **4650 HD**.
If i dint have a RadeonHD card i will not have video at hall (only the yaboot).

---

### Post by luigiburdo on 2014-05-15
RadeonHD 6570 2gb come ... and ? :)

The board is working!!!!! :)
But ... a small problem i dont have chars on the screen :P 
I have windows and bars and backgrounds but no chars ... in console too .
I run Prboom the doom clone and the video is super fluid ! windows are resizing really smooth
Now i have to try to reinstall the Lubuntu hope this will fix the chars problem... 
Because it is a Radeon R600 i will try the Xeno74 Mesa Patch.

Will report soon .. and i will make a good video on youtube :D

Bad news The installer make this things too :( 
Here an image of the actual 6570 video exit

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/IMG_3635_zps7cec5746.jpg[/IMG]

---

### Post by xeno74 on 2014-05-15
> **luigiburdo said:**
> 
But ... a small problem i dont have chars on the screen :P 
I have windows and bars and backgrounds but no chars ... in console too.

The solution is to set the option "**RenderAccel**" to "**false**" in the xorg.conf file.

---

### Post by yangdh on 2014-05-15
> **luigiburdo said:**
> RadeonHD 6570 2gb come ... and ? :)

The board is working!!!!! :)
But ... a small problem i dont have chars on the screen :P 
I have windows and bars and backgrounds but no chars ... in console too .
I run Prboom the doom clone and the video is super fluid ! windows are resizing really smooth
Now i have to try to reinstall the Lubuntu hope this will fix the chars problem... 
Because it is a Radeon R600 i will try the Xeno74 Mesa Patch.

Will report soon .. and i will make a good video on youtube :D

Bad news The installer make this things too :( 
Here an image of the actual 6570 video exit


How about other distros like Fedora and Gentoo? Is it a problem with fonts rendering, or HW acceleration as xeno74 said? How much memory does your HD4650 have?

---

### Post by luigiburdo on 2014-05-16
Xeno thanks for your tip, but i have a big problem.
On lubuntu distro i cant enter in the /root where is the Xorg.conf.
This bug (no chars) is present in installation cd too , if eg. i dint have a RadeonHd 4450 to swap with the 6570 pratically will be impossible install lubuntu.
I have found how to go in the terminal mode screens on Lubuntu i have to push "control-alt-F(keys)" and had the opportunity there to read the X.log (in screen terminals the chars are ok) and there i read that the assigned vmem for the radeon 6570 is 128mb (!)
I had been try to go in irc for find the PPC developer for been allert about this GPUs are running but they are impossible to find.
Hope they are reading this thread.
 i had been noticied they about thru some others guys

---

### Post by luigiburdo on 2014-05-16
Hi yangdh,
like i wrote to xeno74 big problem is enter in the root for mod the conf..
The 4650hd is 512mb dd3 
the 6570hd is 2048mb ddr3 
but for what i had been understood only 128mb are assigned to Vmem... lather i will check better.
i will swap the  6570 with 4650hd and write you x.log that you requested days ago.

about the other distros i dint check how will be with Fedora and Gentoo first i have to check if this distro support the 6570 hd on powerpc side

i will try alternate installer for lubuntu hope will gave me more expert user options

---

### Post by xeno74 on 2014-05-16
> **luigiburdo said:**
> Hi yangdh,
like i wrote to xeno74 big problem is enter in the root for mod the conf..
The 4650hd is 512mb dd3 
the 6570hd is 2048mb ddr3 
but for what i had been understood only 128mb are assigned to Vmem... lather i will check better.
i will swap the  6570 with 4650hd and write you x.log that you requested days ago.

about the other distros i dint check how will be with Fedora and Gentoo first i have to check if this distro support the 6570 hd on powerpc side

i will try alternate installer for lubuntu hope will gave me more expert user options

Could you post the problems to the linux ppc mailing list, please? Link: [https://lists.ozlabs.org/listinfo/linuxppc-dev](https://lists.ozlabs.org/listinfo/linuxppc-dev)

---

### Post by luigiburdo on 2014-05-16
> **xeno74 said:**
> Could you post the problems to the linux ppc mailing list, please? Link: [https://lists.ozlabs.org/listinfo/linuxppc-dev](https://lists.ozlabs.org/listinfo/linuxppc-dev)
Hi Christian , i did ;)
hope some one will look at this thread :P

---

### Post by yangdh on 2014-05-16
> **luigiburdo said:**
> Xeno thanks for your tip, but i have a big problem.
On lubuntu distro i cant enter in the /root where is the Xorg.conf.
This bug (no chars) is present in installation cd too , if eg. i dint have a RadeonHd 4450 to swap with the 6570 pratically will be impossible install lubuntu.
I have found how to go in the terminal mode screens on Lubuntu i have to push "control-alt-F(keys)" and had the opportunity there to read the X.log (in screen terminals the chars are ok) and there i read that the assigned vmem for the radeon 6570 is 128mb (!)
I had been try to go in irc for find the PPC developer for been allert about this GPUs are running but they are impossible to find.
Hope they are reading this thread.
 i had been noticied they about thru some others guys
What's the VRAM size detected by kernel log? That could be known by "dmesg |grep 'VRAM'" in a terminal. Do you get a right vram size in Xorg.0.log when the HD4650 card is used?
So far as the root privilege is concerned, have you tried the methods discussed in the link as I mentioned in #40 of this thread?
[http://ubuntuforums.org/showthread.php?t=2142634](http://ubuntuforums.org/showthread.php?t=2142634)
Does "fc-cache -fv" in a terminal have any effect on the text of graphic interface?

---

### Post by luigiburdo on 2014-05-16
> **yangdh said:**
> What's the VRAM size detected by kernel log? That could be known by "dmesg |grep 'VRAM'" in a terminal. Do you get a right vram size in Xorg.0.log when the HD4650 card is used?
So far as the root privilege is concerned, have you tried the methods discussed in the link as I mentioned in #40 of this thread?
[http://ubuntuforums.org/showthread.php?t=2142634](http://ubuntuforums.org/showthread.php?t=2142634)
Does "fc-cache -fv" in a terminal have any effect on the text of graphic interface?

Hi yangdh,
i try the fc-cache -fv and the chars continue be lost on the 6570HD 
about the thread you mention for retrive the root privilege i tested but something is different and cant do the same procedures there described.
about the dmesg  i will test after work. 
About the Xorg.0.log didnt see if the vram was right there (i didnt check) will be my next test .
After work i will install the Lubuntu Alternate  and see if something differ for the root and so on and if i will be finally able to mod the Xorg.conf for make the 6570hd working 

See you soon

---

### Post by luigiburdo on 2014-05-16
Start working with the alternate installation "look like debian" .. but the installer hang with apt at 71% and stop installing ... :-(
note the root is not configurable here too "root is used by the system and isnt selectable"
return to desktop version ... will try if possible use the console for put noaccel

---

### Post by luigiburdo on 2014-05-16
Yungdh,

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/IMG_3637_zps4dd684d0.jpg[/IMG]

im downloading the last debian test 12/05/2014 will see if something is different there with the radeon 6570

on vgarrb the pci0a is the X1900 the other is the 6570

I had looked to Xorg.conf of debian wheezy stable and i found there are two cards and 4 screens there
probably every DVI are the screens?

---

### Post by luigiburdo on 2014-05-16
Last Debian test version is worst compared with wheezy it hang during the kernel mod loading ... tomorrow i will put the 4650 and wait for a better lubuntu

---

### Post by yangdh on 2014-05-16
> **luigiburdo said:**
> Hi yangdh,
i try the fc-cache -fv and the chars continue be lost on the 6570HD 
about the thread you mention for retrive the root privilege i tested but something is different and cant do the same procedures there described.
about the dmesg  i will test after work. 
About the Xorg.0.log didnt see if the vram was right there (i didnt check) will be my next test .
After work i will install the Lubuntu Alternate  and see if something differ for the root and so on and if i will be finally able to mod the Xorg.conf for make the 6570hd working 

See you soon
If you want to create/edit xorg.conf, you could do that way: (You have installed Lubuntu correctly with HD3640 card)
1). Put only x1900 card in you computer, get out the other one. 
2). Use Gentoo CD to boot to a console(That could no problem according to your previous posts). Now you have the root privilege.
3). Mount the HD where the xorg.conf file is located.
4). Create/Edit xorg.conf file in directory "/etc/X11" by nano or other text editors. Here you can tweak the options in graphics card sections.
5). Shutdown your computer, put your HD6570 in, get out Gentoo CD, and turn on the computer.
6). Wait for what happens.
Before doing you should know the BusIDs of x1900 and HD6570, and put them in the right card sections of xorg.conf accordingly(May be better to do that).
BusID can be know by 'lspci', you could use 'lspci -vvnn' for more detailed info.
Wish you a success!

---

### Post by luigiburdo on 2014-05-17
Thanks for tips... lets try but after last email from the mailing list of LinuxPPC devs im sure will be nothing to do because 
there is a bug on free desktop who need to be resolved by they

This is Christian bug evidence (Xeno74)
[https://bugs.freedesktop.org/show_bug.cgi?id=72877](https://bugs.freedesktop.org/show_bug.cgi?id=72877)

this is the problem of desktop decorations 
[https://bugs.freedesktop.org/show_bug.cgi?id=74939](https://bugs.freedesktop.org/show_bug.cgi?id=74939) 

Look like the other Powerpc architectures are affected by the same bugs 
(x 1000 not thanks probably by Xeno74 kernel patch?)

---

### Post by yangdh on 2014-05-17
> **luigiburdo said:**
> Thanks for tips... lets try but after last email from the mailing list of LinuxPPC devs im sure will be nothing to do because 
there is a bug on free desktop who need to be resolved by they

This is Christian bug evidence (Xeno74)
[https://bugs.freedesktop.org/show_bug.cgi?id=72877](https://bugs.freedesktop.org/show_bug.cgi?id=72877)

this is the problem of desktop decorations 
[https://bugs.freedesktop.org/show_bug.cgi?id=74939](https://bugs.freedesktop.org/show_bug.cgi?id=74939) 

Look like the other Powerpc architectures are affected by the same bugs 
(x 1000 not thanks probably by Xeno74 kernel patch?)
Thank you. Your rendering problems may concern with the EXA acceleration issues reported in the second link. The card acceleration can be disabled by passing parameters to the kernel when yaboot is called:
1). When yaboot is waiting for kernel selection, press <tab>.
2). Type "<kernel name>  radeon.noaccel=1"(without quotes), press <enter>.
The graphics card acceleration will be disabled.
If your problem is caused by the acceleration issues, you would have a correct graphics on HD6570.

---

### Post by luigiburdo on 2014-05-17
Lets try another time after i will put the 4650 the 6570 will be used for another incoming new and great ppc machine (top secret :P) :-)

---

### Post by xeno74 on 2014-05-17
Yeah Cyrus Plus: 

[http://www.a-eon.com/18-10-2013-1.pdf](http://www.a-eon.com/18-10-2013-1.pdf)
[http://www.a-eon.com/18-10-2013-3.pdf](http://www.a-eon.com/18-10-2013-3.pdf)
[http://www.a-eon.com/18-10-2013-6.pdf](http://www.a-eon.com/18-10-2013-6.pdf)
[http://www.a-eon.com/News_Release_A1-X5000.pdf](http://www.a-eon.com/News_Release_A1-X5000.pdf)

---

### Post by luigiburdo on 2014-05-18
There will be sure linux will work because a geek make all working :P:P:P

---

### Post by yangdh on 2014-05-18
> **luigiburdo said:**
> There will be sure linux will work because a geek make all working :P:P:P
Be just waiting for your great news(Please share with us)!

---

### Post by luigiburdo on 2014-05-18
> **yangdh said:**
> Be just waiting for your great news(Please share with us)!

There Xeno74 is more informed compared with me , he make the kernel fix for the x1000 for sure will be him who will make the same for X5000 :-D

About Lubuntu on G5 i return on the 4650hd and i have been update the system with last system updates... can say the system is really stable now ... i dont had crashes like before. im writing from there :P :P :P
Mesa continue gave me wrong colors but in future probably will be better ... now i will try again to install Xeno74 mesa patches hope something will change .
Sorry but i dont continue understand why the lubuntu devs make the root not available for users...

---

### Post by luigiburdo on 2014-05-18
i dont know how i did but finally it works :D  on 4650HD 
i update the not free drivers forcing aptitude ..
plus i installe the last Xeno74 patch ... 

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/IMG_3670_zps2d21657b.jpg[/IMG]


result :D 
now will test the cairo menu and something else who are using composition and so and so ... and naturally i will report like my usual :P

---

### Post by luigiburdo on 2014-05-18
A question to Xeno74...
Christian do you have the Gnash working in  lubuntu Firefox browser ?

I test some games like frogatto and quake 1 but there the colors continue be wrong ... xeno do you encounter there too this problem?
look like sdl continue have problem with direct video rendering

another thing after rebooting the glxgears return wrong

---

### Post by xeno74 on 2014-05-18
Hi Luigiburdo,

> **luigiburdo said:**
> A question to Xeno74...
Christian do you have the Gnash working in  lubuntu Firefox browser ?

No, I don't need flash on my A1-X1000.

> **luigiburdo said:**
> 
I test some games like frogatto and quake 1 but there the colors continue be wrong ... xeno do you encounter there too this problem?
look like sdl continue have problem with direct video rendering

Frogatto works with the right colors with the unofficial Mesa version 10.0.4 on Lubuntu 14.04 PowerPC:

[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1149&t=1[/IMG]

Screenshot in a bigger size: [http://forum.hyperion-entertainment.biz/download/file.php?id=1149&mode=view](http://forum.hyperion-entertainment.biz/download/file.php?id=1149&mode=view)

You have to start it in the same shell where did you set up the LD_LIBRARY_PATH.

> **luigiburdo said:**
> 
another thing after rebooting the glxgears return wrong

If you want that Mesa works system wide and after rebooting then you have to add the line **export LD_LIBRARY_PATH=** to the **.profile** file in your home directory.

---

### Post by luigiburdo on 2014-05-18
Thanks for the tip Christian , color are right now :D

.profile in /home directory ? strange  i dint have something here :-O

about gnash with this plugin the video on youtube run a 720p usually with html5 are 360p


another thing i founde this on glxinfo:

luigi@luigi-desktop:~$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV730
OpenGL version string: 2.1 Mesa 10.1.0
OpenGL shading language version string: 1.30
OpenGL extensions:
**OpenGL vendor string: VMware, Inc.**  ????
**OpenGL renderer string: Gallium 0.4 on softpipe**
OpenGL version string: 2.1 Mesa 10.1.0
OpenGL shading language version string: 1.30
OpenGL extensions:




Plus i have this message on some 3d software **" radeon: The kernel rejected CS, see dmesg for more information"**

---

### Post by luigiburdo on 2014-05-19
Retuning **about Radeon HD 6570 **display decoration problems
look like it is a **Big Endian bug that effected some  Radeon model  with X **
and this problem is related :
Evergreen / Northern Islands family cards[https://bugs.freedesktop.org/show_bug.cgi?id=74939](https://bugs.freedesktop.org/show_bug.cgi?id=74939)
 
but not effect the 4650 for example.

i have to say a big thank you to Michel D. from amd.com who is a  mesa and X developer  for all the explanation about.

---

### Post by luigiburdo on 2014-05-19
Xeno74 .profile found! and fixed :) thankyou
it was  [COLOR=#000000]in /home/username/ directory 


[/COLOR]

---

### Post by luigiburdo on 2014-05-29
Yesterday i had been put on my Quad a great SSHD segate 1tb only for Lubuntu...
Everything is speedy and faster ... only one big problem the mesa have color wrong . i had been try to simulate the before operation that i did but no result...
If i will success i promise will write all the step one by one here

---

### Post by luigiburdo on 2014-06-17
Experiments, Experiments and more test...
Yesterday i make a new one ,The 7800gtx on 16x bus and the 4650HD on 8x, i installed the debian wheezy 7.5 
I have the video On the Nvidia , and the Audio on the 4650HD ... 

next test 4650HD alone on 16x ... and try to see if the debian installer will run on this card
...
Nothing to do alone i dont have the video i try to boot from cdrom but without success.
look like debian need a ppc bios in video board for be initialized the video
Lubuntu not the board con work alone but the system is unstable.

---

### Post by luigiburdo on 2015-01-16
Yes im returning with news :-P
Ok last attempt to have Lubuntu 15.x and Ubuntu Mate running on Quad G5 and 7800gtx failed ... Totally Glitched graphic on my 7800gtx and no RadeonHD video.
But with Debian Jessie and wheezy with 3.16.rc kernel i menagade to have the linked images.
I cant make Gdm3 run on RadeonHD try to black list the nouveau and make the module  radeon load from beginning ... but nothing ... the video continue 
run on Nouveau ... Xorg -configure perfectly recognize the Radeon 6570 and set up it

probably i had miss something
Lets hope for the future!


[IMG]https://scontent-a-mxp.xx.fbcdn.net/hphotos-xap1/v/t1.0-9/10898166_10203398206337456_3605330630840272059_n.jpg?oh=24ab2aaea21047c01ca4e78361933309&oe=556B03FA[/IMG][IMG]https://fbcdn-sphotos-b-a.akamaihd.net/hphotos-ak-xpa1/t31.0-8/10920274_10203417919550274_5638957866983815826_o.jpg[/IMG][IMG]https://scontent-b-mxp.xx.fbcdn.net/hphotos-xpa1/t31.0-8/10863911_10203417919030261_4027029907276266662_o.jpg[/IMG]

---

### Post by rican-linux on 2015-01-16
This is off topic but I saw that someone was using gkrellm to monitor their cpu. I was wondering will gkrell work on powerbook g4? sensors-detect is not seeing my cpu. Thanks!

---

### Post by luigiburdo on 2015-01-19
and i can see the light at the end of the tunnel guys![IMG]https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-xpa1/t31.0-8/10838203_10203438280859294_9012045887265317943_o.jpg[/IMG]
I will test with Mate ... if there something will run too :)

---

### Post by rican-linux on 2015-01-19
Sweet! Share how you did it!

---

### Post by luigiburdo on 2015-01-20
Hi Rican,
i will do it but before is my intention first notice the Linux Kernel Developer because need to understand what they had been change
in the lastest kernel because the fans of Quad are spinning like a turbo jet ... 
this issue are not related the radeon card but related the kernel version up 3.16.. (needed for have the Radeon hd 6xxx working)
for sure with radeon hd 4xxx and 5xxx will be no problems with low kernel version, I will check it too with a radeon hd 4650HD 512mb ddr3 and report.
and if everything will run good write a small tutorial for have this gpus working in couple with nvidia card apple bios. 
My configuration is G5 Quad + nvidia 7800gtx 512mb and Radeon HD 6570 2gb ddr3 ;)

With Ubuntu,lubuntu or Mate right now i cant have video . In this distro the kernel are 3.11 (if i good understand) i have issue with 7800gtx too there.
Before i had the X1900gt and in couple with Radeon HD gave me the opportunity tu use the 4450 with lubuntu 14.04ts from very beginnning.

---

### Post by rican-linux on 2015-01-20
Check out this forum [thread]("http://forums.debian.net/viewtopic.php?f=7&t=105268") on fan speed on the G5.

---

### Post by luigiburdo on 2015-01-20
Thank you rican , 
will check it soon as possible and report :)

---

### Post by rican-linux on 2015-01-20
no worries, hope it helps!

---

### Post by luigiburdo on 2015-01-20
> **rican-linux said:**
> no worries, hope it helps!

Yes it work ! ... finnally i can stay quiet in my room! ;)

Thank you rican... now i can work in fixing Gallium/mesa on it ;)...
Hope soon i will report the success and the tutorial step by step for have RadeonHD 6xxx working on G5 quad ;)
Ah im pretty sure with this powermacs with pci slots will be able to use radeonhd with a pcie->pci adaptor.

---

### Post by rican-linux on 2015-01-20
awesome!

---

### Post by rsavage on 2015-01-21
> **luigiburdo said:**
> Yes it work ! ... finnally i can stay quiet in my room! ;)

Thank you rican... now i can work in fixing Gallium/mesa on it ;)...
Hope soon i will report the success and the tutorial step by step for have RadeonHD 6xxx working on G5 quad ;)
Ah im pretty sure with this powermacs with pci slots will be able to use radeonhd with a pcie->pci adaptor.

If the fix applies to Ubuntu, then please add it to the known issues page or FAQ section - [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_adjust_my_fan_limits.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_adjust_my_fan_limits.3F)

---

### Post by luigiburdo on 2015-01-21
Hi rsavage .
that fix is working for kernel 3.16 and up . on ubuntu and sons there is rightnow kernel 3.13 where this small issue isnt present (for now).
I just need to remember all the guys Lubuntu 14.04 ts working great with RadeonHD 4650 on PowerMac G5 in couple with a radeon apple firmware board.

---

### Post by luigiburdo on 2015-01-22
Ok let me  start a small tutorial here for have a radeon HD with Nvidia running "in software resterizer for now"
if some one wanna help for have the 3D Mesa/Gallium working any help will be apreciated.

Nvidia (apple bios) on 16x pcie Slot . RadeonHD on 8x pcie slot.
live or linux (depend of the distro) 
linux video=offb: off radeon.modeset=1

after installation as root
you need to have in /etc/apt/sources.list the notfree repository inserted and the backports too


do step by step
nano  /etc/modules <--insert  radeon 
nano /etc/modprobe.d/fbdev-blacklist.conf <- Insert blacklist nvidiafb 
nano /etc/modprobe.d/fbdev-blacklist.conf  <-insert blacklist nouveau
nano /etc/modprobe.d/radeon-kms.conf <-insert options radeon modeset=1
apt-get update
aptitude install  xserver-xorg-video-radeon     
aptitude install  firmware-linux-nonfree  

after all

/etc/init.d/gdm3 stop or /etc/init.d/lightdm stop
Xorg  --configure 
mv xorg.conf.new /etc/X11/xorg.conf

nano /etc/yaboot.conf 

insert after yourt initrd.img

"append="video=offb: off radeon.modeset=1"

Save

ybin -v
/etc/init.d/gdm3 start or /etc/init.d/lightdm start

reboot ... 
now you have a radeonHd working on G5 quad :)

---

### Post by luigiburdo on 2015-01-22
probably i found the way for Mate-ubuntu-lubuntu and Xubuntu too for have nvidia and radeon working both  !

[IMG]https://scontent-a-ams.xx.fbcdn.net/hphotos-xpa1/v/t1.0-9/10942755_10203455171281544_4976995945031155359_n.jpg?oh=9a71d65828770b00771ee250f7a19ff7&oe=5560B38C[/IMG]

---

### Post by Cris_Schweitzer on 2015-02-08
Would higher-end 6xxx cards, such as 6970s, 6850s, and 6790s work, assuming one had a way to power them?

---

### Post by luigiburdo on 2015-02-08
Hi Cris . It can, but there are some card that have problems with Xorg. .
There are some radeon hd that have problems with fonts and some other issue one of this is my 6570 :sad: 
for sure the 4xxx and 5xxx are working good , the 6xxx some series working without problems some others have this issues.
the 7xxx or other better and last i dont know ... the best is ask in the  linux kernel mailing lists what are the video board that are full  working on PPC hardware without issues with 3d too.

---

### Post by luigiburdo on 2015-03-25
Yes and start working with Radeon HD 6570 2gb in couple with nvidia too :) 

[IMG]https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-xap1/v/t1.0-9/11043534_10203812535495426_3916667371727547866_n.jpg?oh=787b2a271d5e7503276adbcb2e22a46e&oe=557B2D4E&__gda__=1437604891_fd903d6b7f7f231f3fdb2bb109210c8d[/IMG]

---

### Post by Casey_C on 2015-03-29
This is great! I also have a 2.5 quad and I just got a Radeon HD 4550 working in it :) Thank you for all your work and sharing this info! Have you been able to get hardware acceleration working instead of software rasterizer? It looked like you had hardware acceleration working in some older pics?

---

### Post by luigiburdo on 2015-03-29
Im happy my sharing help some one who have the great Quad G5 (underpowerd machine from apple... i wanna kill apple for this) working good :)
the 4xxx have the hardware acceleration working for sure on Mate and on Lubuntu 14.04 .
Right now im using the 6570 HD 2Gb no r600 driver loaded here ... but man wow the 2d is really really fast compared the 4650 .
Lets hope for the future ;-)

---

### Post by Casey_C on 2015-03-29
Yes! My Quad G5 is still my favorite computer after all these years! I'm planning to get a newer Radeon to try a newer card as well, but a friend gave me the HD 4550 for free so I tried it out.  I'm running Debian Wheezy. I wonder why I have only software rasterizer. Any ideas? I followed the instructions you posted on page 9.

---

### Post by luigiburdo on 2015-03-29
> **Casey_C said:**
> Yes! My Quad G5 is still my favorite computer after all these years! I'm planning to get a newer Radeon to try a newer card as well, but a friend gave me the HD 4550 for free so I tried it out.  I'm running Debian Wheezy. I wonder why I have only software rasterizer. Any ideas? I followed the instructions you posted on page 9.

On Wheezy there is not the opportunity for have the 3d running ... or better i try all that i know for have 3d with radeon but oly sw rendering come ... for sure one Ubuntu and Lubuntu everything working with 3d .
Now i have software resterized 6570hd  ... but will check better ;)

Edit WORKING !

---

### Post by luigiburdo on 2015-03-29
So wonderful and so smoth !! Apple I hate you!

here the The video!
[https://www.youtube.com/watch?v=MYgFfRLYhLU&list=UUkb4bw4N19d-x_tn2FXLojQ](https://www.youtube.com/watch?v=MYgFfRLYhLU&list=UUkb4bw4N19d-x_tn2FXLojQ)


[IMG]https://scontent-mxp.xx.fbcdn.net/hphotos-xpa1/t31.0-8/11080422_10203834957535963_4531489381273521074_o.jpg[/IMG]

---

### Post by Casey_C on 2015-04-01
I tried to install Lubuntu 14 using my nvidia 6600 (16x) and the Radeon 4550 (8x) but can't seem to get anywhere... I get video on only the nvidia display after installation. I tried editing the modprobe files and created xorg.conf per your instructions but then I boot to terminal and the system locks up on a black screen if I try to startx. Yaboot doesn't seem to make a difference. Any ideas?

---

### Post by luigiburdo on 2015-04-01
Hi Casey

do this :
from installation cd

```

live video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0

```

the line have to be exactly this if you make a small error you will not have video on radeon.
when you will see the desktop before the installation procedure make attention because if you will put the mouse pointer on the bottom or on the extreme left of the screen the pointer will desappear and you will need to stop the lightdm from the tty.
After when you installed everithing , when yaboot screen will appear push tab on keyboard and write

```

  Linux video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0

```


when the desktop will appear kill the lightdm push on keyboard Ctrl+Alt+F1

```

 sudo /etc/init.d/lightdm stop

```
and write in tty 
```

sudo aptitude remove xserver-xorg-video-fbdev 

```
with this you will kill the fbdev bug mouse pointer. 

after you will turnon the lightdm 
```

sudo /etc/init.d/lightdm start  

```

and you will not have any more the bug .

Ciao 
Luigi

---

### Post by Casey_C on 2015-04-01
Great I'll try this tonight after work! Wish me luck! Thanks for all your help :)

---

### Post by Casey_C on 2015-04-03
FINALLY! Working, very stable with hardware acceleration! I feel like I have a new PPC64 machine!

---

### Post by luigiburdo on 2015-04-03
Casey 
i suggest you to swap the kernel with 4.00rc3 because you will increase performance and will be much much more stable

here is my compiled one for G5 and RadeonHD [https://www.dropbox.com/sh/m8c9p3v99gsher3/AADP5l6UGWbroFrbXlqKBFyAa?dl=0]("http://www.dropbox.com/sh/m8c9p3v99gsher3/AADP5l6UGWbroFrbXlqKBFyAa?dl=0")

---

### Post by Casey_C on 2015-04-05
Ok, great, I will try it out, hopefully tomorrow! Also, I've discovered a way to operate our G5 machines with only the x86 Radeon card, in the 16x slot, with no Apple-flashed card. Boot into Open Firmware (press command + option + O + F). At the Open Firmware prompt, type "setenv boot-device hd:2,yaboot". Open Firmware should return "OK", then you can type "shut-down".  This tells Open Firmware not to check for video cards, just boot directly to yaboot. You can then take out the Apple-flashed card and put the Radeon card in the 16x slot. Note that when you startup the machine you will have no display until X loads, so if you need to reconfigure you will most likely need to put the Apple-flashed card in again.

---

### Post by luigiburdo on 2015-04-05
great tip :) thanks!
i was prefer stay on 8x because every time i put in 16x the radeon i face an instability on linux side. mac osx was running without problems on 8x slot.
during next days if you face freezing desktop this will because the16x slot, if you dont have this issue it means with that o.f. command you are able to fix some bus issue on the radeon too

---

### Post by Jos_Antonio_agro on 2015-04-09
Hello Luigi¡¡¡¡

Question for you:

G5 dual core (ppc)
Nvidia Geforce 6600

Can i install [COLOR=#444444][FONT=arial]ATI Radeon HD 4650 GV-R465OC-1GI de 1Gb Hd in other slot and make it works?

Thanks¡¡¡¡¡[/FONT][/COLOR]

---

### Post by luigiburdo on 2015-04-09
Juan Antonio ... if your G5 is equiped with pcie .. you can install all boards if compatible with linuxppc 
if your mac have pci probably you will need a pci-pcie adpatopr to put the pcie boards on your mac  and probably will work on linux ppc (never tested but i assume yes)
if is a pcix mac ... i dont know

---

### Post by Jos_Antonio_agro on 2015-04-09
Nvidia 6600 le is PCI-e, so my G5 is equiped with PCIe.
My question is about [COLOR=#444444][FONT=arial]ATI Radeon HD 4650, is it plug and play into G5, or do i need to flash this board? (i´m going to buy one)

Thanks again[/FONT][/COLOR]

---

### Post by luigiburdo on 2015-04-09
the new board work on Linux as Plug and play but in couple of Apple flashed boards . 
but not on Osx only on LinuxPPC 
Your mac need to have more pcie slots like is the Quad G5 . The 4650 is a good board but you can buy better one like is 5xxx serie too compatible with eg Lubunntu 14.04 and Mate too

---

### Post by Jos_Antonio_agro on 2015-04-09
Ok, i can get this one for 20 eur, so it´s a good deal.
I don´t need extra performance, i want to install Mate, and right now, Nvidia 6600 is not working with last version.
And [[FONT=verdana, arial][COLOR=#113311]ATI [/COLOR][/FONT]**RADEON HD 7450 1GB PCIE X16**]("http://www.milanuncios.com/tarjetas-graficas/ati-radeon-hd-7450-1gb-pcie-x16-157753653.htm")??

---

### Post by luigiburdo on 2015-04-09
I had been buy for 25 euro an 5450 1Gb , i dont know 7450 if working never tested . 
I had test 6570 2GB (work on Lubuntu 14.4.2) 5450 1GB and 4650  512mb (work on Lubuntu and Mate)

---

### Post by Jos_Antonio_agro on 2015-04-09
Finally i have bought [COLOR=#333333][FONT=Helvetica neue][B]ASUS ATI RADEON HD5450 1GB -> 20 eur
[/B][/FONT][/COLOR][FONT=Helvetica neue][B][SIZE=3]I will tell you how it works on Mate.
Thanks Luigi[/SIZE][/B][/FONT][COLOR=#333333][FONT=Helvetica neue]****[/FONT][/COLOR]

---

### Post by luigiburdo on 2015-04-09
when it come if you are in trouble ask!
you can see my post about the right setting for install mate

---

### Post by Jos_Antonio_agro on 2015-04-09
Thanks Luigi, last question, can i have a nvidia board + ati radeon? or should it be nvidia + nvidia OR ati radeon + ati radeon?

At this moment i have an nvidia 6600 LE, if i plug new RADEON HD will  Lubuntu work?

---

### Post by luigiburdo on 2015-04-09
the best is  have Nvidia on first pcie (primary) and radeon on the second one . 
Before the only way was have 2 radeon board on the mac for have the radeonhd working .. but now i found the way for have and nvidia and a radeonhd :)

---

### Post by Jos_Antonio_agro on 2015-04-09
Ok, i will tell you how it works on my mac.
Thanks

---

### Post by miklos3 on 2015-04-12
Ty invitation!

My G5 Quad: 8Gb ECC Transcend RAM, 2x160Gb Intel 320s SSD RAID, nVidia 6600LE card (soon it will be HD5450). My problem is electricity. This an monster bc eat a lot of power. How can fix this? I am not an typical linux user, just I want to use one which need a less power than 10.5.8 (bc one FHD movie eat 0,5-1kw electricity! New Intel processors eat 0,05 :-) ). I watched this [https://www.youtube.com/watch?v=1yyMJIb-ysk](https://www.youtube.com/watch?v=1yyMJIb-ysk) and want to know what U think Luigi. Ty.

---

### Post by luigiburdo on 2015-04-12
My friend yes it took power but linux drop down power draining switching the cpu goes at 1.250 mhz instead of 2500 mhz. for core.
In any way .. a pc workstation will drain energy like the quad too ... what took much energy are not the cpu but all the perifericals, the video boards and the monitor ;)
My energy payment dont change to much from when i sold my Imac 27 I7 (end 2010) and use only the quad  for every days things :-P

---

### Post by miklos3 on 2015-04-12
Ty, sounds good! :-) I have a mini also, but I don't like iOSemite and new mac concepts. :-P And the big problem under 10.5.8 no GPU decoding. NV 7800gt and gtx a good card, but to much electricity bc only the CPU work under .mkv movies. This eat a lots of energy! Linux with ATI better if I want to see movies. 

One more question: I turned off top fans. Bc less noise and etc. Bad for sensors?

---

### Post by luigiburdo on 2015-04-12
Why you turned off top fans ? my machine is not macking too much noises .. or better say in standard working situations (browsing internet , watch movies with vlc and so and so) it is more less noiseless than the PS4 when play games! 
Had you been make the fan calibrations with ASD 2.63 ? how much is your cpus temeratures in not working operations ? for me is 35 max 37 celsious ... but in not doing nothing 28-30 celsius and this are on Leopard
vlc for beig movies dont take too much cpu and use  gpu for overlay decoding ... for sure the nv 6600ne is slower compared the 7800gtx for hardware decoding procedures.. and yes with radeonhd you will have hardware decoding too ;-)

---

### Post by miklos3 on 2015-04-12
With ASD all good, same temps, but I thought not necessary to cool SSD and cards, less noise and electricity, just idk its good or bad in the long run, I will see :-)

---

### Post by Jos_Antonio_agro on 2015-04-12
Hello everybody. I have updates:


Tested Debian 7.8 Wheezy.
I can only run desktop at 1280x1024, at this resolution all works great, but if i want to change resolution to 1920x1080 (max resolution supported), i can only see a portion of desktop.

I´m going to test now Debian Jessie RC2.

---

### Post by luigiburdo on 2015-04-12
> **Jos_Antonio_agro said:**
> Hello everybody. I have updates:


Tested Debian 7.8 Wheezy.
I can only run desktop at 1280x1024, at this resolution all works great, but if i want to change resolution to 1920x1080 (max resolution supported), i can only see a portion of desktop.

I´m going to test now Debian Jessie RC2.

Where on 6600 or on Quadro Fx ??

---

### Post by Jos_Antonio_agro on 2015-04-12
Hello Luigi, still using nvidia 6600. Tomorrow should arrive ATI RADEON HD. Any ideas?

---

### Post by luigiburdo on 2015-04-12
i dont know my friend ... everything was working good on wheezy 7.6 with 6600 i had 1080p too and was better compared the 7800gtx too 
probably they make some strange bugged update with last kernel or xorg

---

### Post by Jos_Antonio_agro on 2015-04-12
I´m going to test JEssie, with update kernel to see if it works.

---

### Post by luigiburdo on 2015-04-12
I hope for you on 7800 gtx and radeonhd dont was work

---

### Post by Jos_Antonio_agro on 2015-04-13
Good morning.

Hardware:

[SIZE=2]Powerpc G5 (ppc). Nvidia Geforce 6600 LE
[/SIZE][h=1]Display: AOC I2369VM - 23" LED Display (1920 x 1080 con tecnología LCD, 5 ms),[/h][TABLE="width: 641"]
[TR]
[TD="class: label, bgcolor: #F5F5F5"][SIZE=2]HDMI[/SIZE][/TD]
[TD="class: value"][SIZE=2]2[/SIZE][/TD]
[/TR]
[TR]
[TD="class: label, bgcolor: #F5F5F5"][SIZE=2]VGA[/SIZE][/TD]
[TD="class: value"][SIZE=2]1[/SIZE][/TD]
[/TR]
[/TABLE]

I connect G5 with a DVI-VGA converter, and then with a VGA cable to display.


More updates:

Tested Debian Jessie RC2 - not working, i can only see a small portion of screen. No mouse.
Tested Debian 7.6 - same output as 7.8 but, distintc resolution, i can get 1440 x 900.

So:

Debian Jessie RC2: not working
Debian 7.8: 1280 x 1024
Debian 7.6: 1440 x 900

Waiting for ATI RADEO HD.
Thanks for support.

---

### Post by luigiburdo on 2015-04-13
Jos Antonio, if you have a free hd and spare time , you can test the OpenSuse 13.2 it was working with my Quad and 7800gtx and sure will work with your 6600 too.
note it use grub and not yaboot ... but is really professional distro (Open Suse is the son of Red Hat)

---

### Post by Jos_Antonio_agro on 2015-04-14
Hello, i can´t believe it, all is working now.

I received yesterday ASUS HD RADEON 5450 1GB. Plug it on the second slot, with NVIDIA Geforce 6600 LE 128 mb on the first one, but not video signal detected.

Then, i turn on Mac OS, and checked System Properties to test HD RADEON, but MAC OS can´t recognize board. At this point i realize that MAC OS display resolution was 1400x900, so i changed to 1900x1080 and restart MAC. Then,i started Debian 7.6 and voila, full resolution with NVIDIA 6600.

Tested with

Ubuntu 12
Ubuntu 14
Ubuntu 15.04
Lubuntu 14

All works fine, i don´t understand anything.

Now, how can i make HD RADEON 5450 works on ubuntu and/or MAC OS 10.5.8?

I´ve also read, that G5 Late 2005 (PPC based) only support 1BG on combined video boards, so if i have RADEON 1Gb + Nvidia 128mb thats over 1gb, could it be???
Is there any ROM to flashpc ATI RADEON 5450? or another way to make it works into ubuntu?

Thanks for your support Luigi

---

### Post by xeno74 on 2015-04-14
> **Jos_Antonio_agro said:**
> Hello, i can´t believe it, all is working now.

I received yesterday ASUS HD RADEON 5450 1GB. Plug it on the second slot, with NVIDIA Geforce 6600 LE 128 mb on the first one, but not video signal detected.

Then, i turn on Mac OS, and checked System Properties to test HD RADEON, but MAC OS can´t recognize board. At this point i realize that MAC OS display resolution was 1400x900, so i changed to 1900x1080 and restart MAC. Then,i started Debian 7.6 and voila, full resolution with NVIDIA 6600.

Tested with

Ubuntu 12
Ubuntu 14
Ubuntu 15.04
Lubuntu 14

All works fine, i don´t understand anything.

Now, how can i make HD RADEON 5450 works on ubuntu and/or MAC OS 10.5.8?

I´ve also read, that G5 Late 2005 (PPC based) only support 1BG on combined video boards, so if i have RADEON 1Gb + Nvidia 128mb thats over 1gb, could it be???
Is there any ROM to flashpc ATI RADEON 5450? or another way to make it works into ubuntu?

Thanks for your support Luigi

That's fantastic! Well done!!!!! Could you post a screenshot of Ubuntu 15.04 in the 15.04 test thread, please? Link: [http://ubuntuforums.org/showthread.php?t=2264322&page=26&p=13264298#post13264298]("http://ubuntuforums.org/showthread.php?t=2264322&page=26&p=13264298#post13264298").

Thanks in advance!

---

### Post by Jos_Antonio_agro on 2015-04-14
Of course, do you need i test some version in particular?

---

### Post by Jos_Antonio_agro on 2015-04-14
Luigi, a question for you, in G5 dual core, late 2005) manuals says:

"Combined maximum video RAM for all graphics cards is 1 GB"

If this is true, i can´t put RADEON HD 5450 1Gb with NVIDIA 6600 LE 128mb.....

---

### Post by Cris_Schweitzer on 2015-04-14
I got my 6970 to work with the software rasterizer using the instructions on page 9. Could someone explain to me how I can switch to the hardware rasterizer? Also, I can't create newmodes in XrandR. XrandR gives me an error about gamma. Is the XrandR issue due to the fact that hardware rasterization is not on?

---

### Post by luigiburdo on 2015-04-14
Here my Video with RadeonHD 6570 2Gb ddr3 running on Lubuntu
[https://www.youtube.com/watch?v=so35SrThHUs](https://www.youtube.com/watch?v=so35SrThHUs)


**Cris_Schweitzer **
i never tested the 6970 but probably it will run

Download the Xeno74 parch for ubuntu 14.10 and install it :-) 

[http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html ]("http://http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html")


here the instruction for install it from Xeno74

> 
1. Extract MesaLib-10.0.4-powerpc-unofficial.tar.bz2

2. Rename the original r600_dri.so to r600_dri.so.bak: sudo mv /usr/lib/powerpc-linux-gnu/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri/r600_dri.so.bak

3. Copy the patched r600_dri.so to /usr/lib/powerpc-linux-gnu/dri: sudo cp mesa-10.0.4/lib/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri

4. Rename the original LibGL.so.1.2.0 to LibGL.so.1.2.0.bak: sudo mv /usr/lib/powerpc-linux-gnu/mesa/libGL.so.1.2.0 /usr/lib/powerpc-linux-gnu/mesa/libGL.so.1.2.0.bak

5. Copy the patched LibGL.so.1.2.0 to /usr/lib/powerpc-linux-gnu/mesa: sudo cp mesa-10.0.4/lib/LibGL.so.1.2.0 /usr/lib/powerpc-linux-gnu/mesa

6. You can test it with glxgears: vblank_mode=0 glxgears



We have to say really big thankyou to this guy and to a-eon opensource group for have the radeonhd  3d running with right colors on PowerMacs !

[B]Cris_Schweitzer 
let us know how this card run on PowerMacs! 
[/B]

---

### Post by miklos3 on 2015-04-14
The little HD 5450 (y) :-) Another peripherals. USB3 doesn't work in this old architecture. But this yes: [http://www.sonnettech.com/product/temposatapro6gbpcie2.html](http://www.sonnettech.com/product/temposatapro6gbpcie2.html) make sense? :-/

---

### Post by luigiburdo on 2015-04-14
Miklos3 ...everything will work on PowerMacs if someone will make drivers ;-)

---

### Post by miklos3 on 2015-04-14
ok :-) the problem: [http://forums.macrumors.com/showthread.php?t=1262839](http://forums.macrumors.com/showthread.php?t=1262839) possible to solve this under linux? :-)

---

### Post by luigiburdo on 2015-04-14
If usb 3.0 sonnet board is supported by linux kernel it will work on powerpc macs for sure

---

### Post by luigiburdo on 2015-04-14
Jose Antonio, 
when the machine was born there was not video board with up of 256mb 512mb was only for ultra professional computer ... i have the feeling the 1gb will work on your mac :)

---

### Post by luigiburdo on 2015-04-14
miklos3
> My G5 Quad: 8Gb ECC Transcend RAM, 2x160Gb Intel 320s SSD RAID, nVidia  6600LE card (soon it will be HD5450). My problem is electricity. This an  monster bc eat a lot of power. How can fix this? I am not an typical  linux user, just I want to use one which need a less power than 10.5.8  (bc one FHD movie eat 0,5-1kw electricity! New Intel processors eat 0,05  :smile: ). I watched this [https://www.youtube.com/watch?v=1yyMJIb-ysk](https://www.youtube.com/watch?v=1yyMJIb-ysk) and want to know what U think Luigi. Ty. 				

My reply to Shiunbird ;-) 

[https://www.youtube.com/watch?v=so35SrThHUs](https://www.youtube.com/watch?v=so35SrThHUs)

---

### Post by miklos3 on 2015-04-14
Yes, I saw, I wrote "cool" :-) the quad is an amazing machine, not a passing love for me, and I hope the cooling system will be stable a long time :-D

---

### Post by luigiburdo on 2015-04-14
This why i have another cpus modules with complete cooling system spare ;-)

---

### Post by Jos_Antonio_agro on 2015-04-15
Hello Luigi, i have tried yesterday with your step-by-step manual for Radeon, but not lucky (Debian 7.8)
There is something strange here. With Debian 7.8 just installed, if i go to Sound Properties, i can see RADEON board (HD5000/HD6000 series).
I will post a screencaptura this afternoon for you.
Thanks

---

### Post by luigiburdo on 2015-04-15
hi Jos_Antonio, 
debian dont work at all with radeon, you will able to have it in software resterized mode it measn no 3d and no 2d video acceleration.
Yes you will able to see the board as audio board and actived drm too but without results.

---

### Post by Cris_Schweitzer on 2015-04-15
I couldn't get the hardware rasterizer to work. Can someone give me a detailed explanation of how to install the hacked mesa libraries? I am using Debian. Is there an issue with hardware rasterization in Debian?

---

### Post by luigiburdo on 2015-04-15
on debian only software resterized mode , the Gallium Mesa 3d work only on Lubuntu 14.04.2 Desktop for 6xxx series on quad g5 .

---

### Post by rican-linux on 2015-04-15
Why does it work on Ubuntu and not Debian?

---

### Post by luigiburdo on 2015-04-15
Rican exactly i dont know : i had been try in 100 ways for make debian work with Radeon in 3d mode. the only thing i didnt test was use the Xeno Patch with debian

---

### Post by Cris_Schweitzer on 2015-04-15
Does it also work in Ubuntu-MATE 14.04?

---

### Post by luigiburdo on 2015-04-15
Cris 
download Lubuntu 14.04.2 iso it will work with your 6xxx and remember for the 6xxx you need to install the Xeno74 mesa patch

---

### Post by miklos3 on 2015-04-15
Omg. So hard to find on the net (eBay etc.) a good mac 7800gtx or x1900gt. A lot of fake or very expensive. :-)

---

### Post by luigiburdo on 2015-04-15
Mac PPC 7800gtx 512mb was never released ... but i can confirm for sure the flashed on is working really great on MacOsX (i have a flashed one too ;-))

---

### Post by miklos3 on 2015-04-15
how much? :-D but under certain situations radeon faster than gtx right? It was a long time ago, I don't remember but in this time I prefer Ati i know :-)

---

### Post by luigiburdo on 2015-04-15
Miklos i had been buy it from Usa one years ago and was expensive i dont remeber the price what i remember good was the shipping prize the half of the board prize and the customs fees...
I had x1900gtx 256mb too ... it was much faster in 3d but slowest in 2d compared the nvidia. Everything is in relations of what you are doing with your mac. If 3D and 3d gaming better the ATI for the 
video play and browsing better the nvidia... nvidia is 54gbs bus transfers and fastest ram dac

Quake gl 640x480 on x1900gt = 870 fps - 845fps on Nvidia  7800gtx
Quake 3 640x480  on  x1900gt = 390 fps  - 365fps on Nviida 7800gtx

---

### Post by Cris_Schweitzer on 2015-04-15
I prefer Ubuntu-MATE. Would Ubuntu-MATE work with hardware rasterization?

---

### Post by miklos3 on 2015-04-15
video play and browsing much more important for me, perhaps I look a simple 7800 GT (~50 USD) but not a very very important now :-)

---

### Post by rican-linux on 2015-04-15
I would get the patched source code and recompile in debian.

---

### Post by luigiburdo on 2015-04-15
Miklos3
If the 256mb version is much slower compared 512mb

---

### Post by luigiburdo on 2015-04-15
6570 didnt was working with mate 14.04.1 but work on Lubuntu 14.04.2 
Gave a try with 69xx im sure lubuntu will work

---

### Post by miklos3 on 2015-04-15
> **luigiburdo said:**
> Miklos3
If the 256mb version is much slower compared 512mb

Yes, I looking at stats. My eyes open and later I will see. Flashed or not, need a good one!

---

### Post by luigiburdo on 2015-04-15
MiKlos3 u can use this sito for comparisons of oldest gpu 

[http://www.gpureview.com/show_cards.php](http://www.gpureview.com/show_cards.php)

---

### Post by miklos3 on 2015-04-15
ohh no, thanks! time travel for me this :-)

---

### Post by Jos_Antonio_agro on 2015-04-15
hello,i&#7743; trying this: [https://wiki.debian.org/AtiHowTo](https://wiki.debian.org/AtiHowTo)

root@debian:/home/jose# lspci -nn | grep VGA
0000:0a:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV43 [GeForce 6600 LE] [10de:0142] (rev a2)
0001:08:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450/6350] [1002:68f9]


From sys.log

Apr 15 23:19:26 debian kernel: [    0.086117] vgaarb: device added: PCI:0000:0a:00.0,decodes=io+mem,owns=none,locks=none
Apr 15 23:19:26 debian kernel: [    0.086170] vgaarb: device added: PCI:0001:08:00.0,decodes=io+mem,owns=none,locks=none
Apr 15 23:19:26 debian kernel: [    0.086203] vgaarb: loaded
Apr 15 23:19:26 debian kernel: [    0.086209] vgaarb: bridge control possible 0001:08:00.0
Apr 15 23:19:26 debian kernel: [    0.086217] vgaarb: bridge control possible 0000:0a:00.0

root@debian:/home/jose# lspci
0000:00:0b.0 PCI bridge: Apple Inc. CPC945 PCIe Bridge
**0000:0a:00.0 VGA compatible controller: NVIDIA Corporation NV43 [GeForce 6600 LE] (rev a2)**
0001:00:00.0 Host bridge: Apple Inc. U4 HT Bridge
0001:00:01.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-X bridge (rev a3)
0001:00:02.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-X bridge (rev a3)
0001:00:03.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:04.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:05.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:06.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:07.0 PCI bridge: Apple Inc. Shasta PCI Bridge
0001:00:08.0 PCI bridge: Apple Inc. Shasta PCI Bridge
0001:00:09.0 PCI bridge: Apple Inc. Shasta PCI Bridge
0001:01:07.0 Unassigned class [ff00]: Apple Inc. Shasta Mac I/O
0001:01:0b.0 USB controller: NEC Corporation USB (rev 43)
0001:01:0b.1 USB controller: NEC Corporation USB (rev 43)
0001:01:0b.2 USB controller: NEC Corporation USB 2.0 (rev 04)
0001:03:0c.0 IDE interface: Broadcom K2 SATA
0001:03:0d.0 Unassigned class [ff00]: Apple Inc. Shasta IDE
0001:03:0e.0 FireWire (IEEE 1394): Apple Inc. Shasta Firewire
0001:05:04.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5780 Gigabit Ethernet (rev 03)
0001:05:04.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5780 Gigabit Ethernet (rev 03)
**0001:08:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450/6350]**
0001:08:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]


So, i have added this to xorg.conf

Section "Device"
    BusID    "PCI:8:0:0"
EndSection

---

### Post by Vt3c on 2015-04-15
I wish that I could get my G4 running well. So far every distro I've tried either doesn't want to work, or causes the graphics card to have an epileptic seizure.

---

### Post by luigiburdo on 2015-04-16
jos antonio , belive me you will come crezy try to make debian run with 3d acceleration...
with radeonhd use maate or lubuntu ...


this is the kernel config ```

live video=offb:off video=nouveaufb:off video=radeonfb:off radeon.modeset=1 nouveau.modeset=0


```

you need to turn off openfirmware gpu or the radeon will not run

---

### Post by Jos_Antonio_agro on 2015-04-16
Hello Luigi, thanks again for your help. 

Debian 7.8 is the more stable version right now for my G5.  That´s the reason to try and try to make radeon works.
Latests versions os mate or lubunto don´t work in my G5, it´s hard to find a good one.
Have you a link to a stable version to try?
By the way, i´m burning a lot od dvd´s, is there any procedure to install from bootable usb in a G5 (ppc)?

---

### Post by luigiburdo on 2015-04-16
jos antonio i use the rewritable dvd :)
i know debian is stable .... but i was unable to use it with 6570 and swapped with lubuntu

---

### Post by Cris_Schweitzer on 2015-04-16
My install of Lubuntu failed. The installation gave no errors. When the system rebooted after installing, the first stage of Yaboot loaded as usual, but when it tried to load the second stage, it did not load and instead showed a flashing finder logo in a folder. Does anyone know how to fix this?

---

### Post by luigiburdo on 2015-04-16
Cris. 
use on yaboot sceen:

```


Linux video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0



```

when the system loaded you need to disinstall the fbdev : sudo aptitude remove xserver-xorg-video-fbdev . 
and after you need to install the Christian mesa parch .

Remember to put the "append" line that i wrote before in yaboot.conf  or every time you will need to hand write it .

sudo nano /etc/yaboot.conf 
and make like i write here :

```

image=/boot/vmlinux-4.0.0-rc3
        label=Linux
        read-only
        initrd=/boot/initrd.img-4.0.0-rc3
        append="quiet splash video=offb:off video=radeonfb:off video=nouveaufb:off nouveau.modeset=0 radeon.modeset=1"


```

after:
sudo ybin -v

I suggest to install my kernel 4  rc3 much more stable with radeon.

---

### Post by Cris_Schweitzer on 2015-04-16
The system has the error before reaching the second stage bootstrap.

---

### Post by luigiburdo on 2015-04-16
ummm ... something was wrong with yaboot probably?

---

### Post by miklos3 on 2015-04-17
Luigi. If Radeon X1900GT so so noisy. The MSI technology. ;-) Very nice and cool I think. 

[IMG]http://techreport.com/r.x/computex-2006/msi-radeon-front.jpg[/IMG]

[IMG]http://techreport.com/r.x/computex-2006/msi-radeon.jpg[/IMG]

---

### Post by miklos3 on 2015-04-18
oops!!! 

[URL="https://www.youtube.com/watch?v=BXOa1Ys86VY"][SIZE=3]SATA III / USB3.0 combo card works on PowerMac G5
[/SIZE][/URL]

---

### Post by luigiburdo on 2015-04-18
On linux works because the board drivers is supported by the kernel ;-)

---

### Post by miklos3 on 2015-04-18
2015 omg, and a very usable machine! :-) thx Luigi your videos! And thx also to Christian Zigotzky & Shiunbird ;-)

---

### Post by Cris_Schweitzer on 2015-04-19
Why does the hardware rasterizer not work in Debian? I can't seem to get Lubuntu to boot up, so Debian with the software rasterizer is the only option. Is there any way at all to use hardware rasterization in Debian?

---

### Post by luigiburdo on 2015-04-19
> **Cris_Schweitzer said:**
> Why does the hardware rasterizer not work in Debian? I can't seem to get Lubuntu to boot up, so Debian with the software rasterizer is the only option. Is there any way at all to use hardware rasterization in Debian?

The problem there is not the mesa patch for radeon made by xeno for ubuntu and sons...
I never have the 3d acceleration working on debian only software with RadeonHD

---

### Post by Cris_Schweitzer on 2015-04-19
> **luigiburdo said:**
> I never have the 3d acceleration working on debian only software with RadeonHD

And why is that the case? What causes 3D acceleration not to work under Debian?

---

### Post by luigiburdo on 2015-04-19
I dont Know.
probably the r600 dont work. I had been try everything without success....

---

### Post by rican-linux on 2015-04-19
have you added the nonfree firmware?

---

### Post by luigiburdo on 2015-04-20
Yes Rican i did it was the first thing i was did and without success ... but the strange things look like in Ubuntu and sons the firmware non free was not needed for have the radeon working with 3d too

---

### Post by Jos_Antonio_agro on 2015-04-20
> **luigiburdo said:**
> jos antonio , belive me you will come crezy try to make debian run with 3d acceleration...
with radeonhd use maate or lubuntu ...


this is the kernel config ```

live video=offb:off video=nouveaufb:off video=radeonfb:off radeon.modeset=1 nouveau.modeset=0


```

you need to turn off openfirmware gpu or the radeon will not run


Hello Luigi, i will try this, problema here is my G5 doesn´t show video on power on if i has the RADEON pluged, how do you get this?

---

### Post by luigiburdo on 2015-04-20
You will not have the video on radeon on power on because you will need the apple bios vga board . you need a apple flashed in couple with x86 gpu because only flashed will show the openfirmware and so and so.

how i fixed ? simple i have 2 video board on my quad . one on the first pcie second on the 3rd  and one monitor with more than 1 plugin or 2 monitors

---

### Post by Jos_Antonio_agro on 2015-04-20
Hey Luigi, that´s the way i have my video boards.

Slot 1: Nvidia Geforce 6600 Le -> DVI to VGA --------------------- VGA   MONITOR1 (i have only 1 monitor)
Slot 2: Ati RadeonHD 5450 (not flashed) -> HDMI -------------------------------  HDMI  MONITOR1 

Should this work with Mate???
Could i try this configuration with Ubuntu Mate live cd? What else do  i need?

---

### Post by luigiburdo on 2015-04-20
nothing like this is perfect ;-) remember to use the 8x pcie slot for the radeonhd usually it is the 3rd from the bottom to top.
like this will work with mate 14.04.1 just use my kernel lines and instruction wrote on previous posts :)

---

### Post by luigiburdo on 2015-04-21
For ALL i make instruction for do everything here [http://ubuntuforums.org/showthread.php?t=2274612](http://ubuntuforums.org/showthread.php?t=2274612)

---

### Post by miklos3 on 2015-04-26
Look at this PPC machine: [http://www.linuxjournal.com/magazine/power](http://www.linuxjournal.com/magazine/power) 


[LIST]
[*]Quad-core 2.5GHz IBM 970MP
[*]8 DDR2 slots for up to 32GB RAM
[*]Extended ATX motherboard
[*]Quiet, easy access to internals
[*]4 SAS hot-swap drive bays
[*]2x8 PCIE, 1x16 PCIE, PCI-X
[*]XGI XP 10 graphics card with 1 VGA, 1 DVI port
[*]Dual Gigabit ethernet
[*]4 USB v2.0 ports
[*]2 RS-232 serial ports
[*]1 VGA and 1 DVI graphics port
[/LIST]

Just too big and noisy! But little bit stronger than Mac G5 quad.

---

### Post by luigiburdo on 2015-04-28
probably it can be overclocked to 3.0 ghz ... because it is a real 2.5 ghz cpu and not an overclocked one like is the Quad G5 it is a 2.3 overclocked to 2.5 this is why it is wather cooled

---

### Post by miklos3 on 2015-04-29
PC2-6400 on G5 Quad?? [http://www.crucial.com/usa/en/power-mac-g5-%28quad-2*5ghz-ddr2%29/CT715674](http://www.crucial.com/usa/en/power-mac-g5-%28quad-2*5ghz-ddr2%29/CT715674)

---

### Post by luigiburdo on 2015-04-29
yes can possible but it will run at same speed of old g5 ram ... no improvments

---

### Post by miklos3 on 2015-04-29
ty! :-) maybe the good CAS latency & other timing will help a little bit, but idk which is the better PC2-4200 ram module, HyperX CL3 etc., but old rams always expensive than newest :-/

---

### Post by luigiburdo on 2015-04-30
yes can help ... but here there is not a problem of ram my friend ... The Quad problem is not good support of the machine first from apple because cut totally the upgrades in 2009 and this machine (where im writing right now) is really capable in 2015 ... second the not full support from  linux too probably because the devs dont have a 970Mp machine

---

### Post by luigiburdo on 2015-04-30
just some benchmark on PowerMac with Blender and ... this are the result . I love this machine!


this is the Blender 2.69 on Lubuntu PPC 14.04.2
Multi Thread
[http://i1249.photobucket.com/albums/hh511/tlosm/BenchmarkG5/blender269_zps0mijwirf.png](http://i1249.photobucket.com/albums/hh511/tlosm/BenchmarkG5/blender269_zps0mijwirf.png)

Sigle Thread
[http://i1249.photobucket.com/albums/hh511/tlosm/BenchmarkG5/blender_single_269_zpsnw6q3j1h.png](http://i1249.photobucket.com/albums/hh511/tlosm/BenchmarkG5/blender_single_269_zpsnw6q3j1h.png)

check the ps3... Oh my god Quad kill it!

4280 00:09:56.00 1x Sony PlayStation 3 IBM Cell 3192MHz 1 PS3 256MB Linux Yellowdog 5.0.2 2.45 test.blend IBM claims this is fast! Slow! 2008-01-27 17:15:53

here all the blender bench
[http://www.eofw.org/bench/](http://www.eofw.org/bench/)

---

### Post by Cris_Schweitzer on 2015-05-19
> **luigiburdo said:**
> probably it can be overclocked to 3.0 ghz ... because it is a real 2.5 ghz cpu and not an overclocked one like is the Quad G5 it is a 2.3 overclocked to 2.5 this is why it is wather cooled
How do you overclock a G5?

---

### Post by luigiburdo on 2015-05-19
No, 
the Quad G5 2.5 ghz is already overclocked by apple :) this is why is water cooled ... and is better dont touch it

---

### Post by miklos3 on 2015-05-22
but underclocking (if U want to save your nrg and money :-) ) 

[https://developer.apple.com/library/mac/qa/qa1141/_index.html](https://developer.apple.com/library/mac/qa/qa1141/_index.html)

---

### Post by luigiburdo on 2015-05-23
Heheh .. i know good it ;-) but save money but will run with less core :-P

---

