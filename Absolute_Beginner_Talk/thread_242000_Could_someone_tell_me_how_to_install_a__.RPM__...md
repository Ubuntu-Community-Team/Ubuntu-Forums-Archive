---
title: "Could someone tell me how to install a  .RPM  ..??"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-08-23
prboom-2.4.5-1.i386.rpm

Whats the easiest way..??

Thanks:tongue:

---

### Post by deadgobby on 2006-08-23
That is very simple to do and happy to give you a link to help you out.
[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)
 Please book mark.

---

### Post by crispy_420 on 2006-08-23
Use alien to convert .rpm to .deb. Just search the forums for an exact how to.

---

### Post by jason.b.c on 2006-08-23
> **crispy_420 said:**
> Use alien to convert .rpm to .deb. Just search the forums for an exact how to.

I don't have alien and i can't get it....Why can't i install alien..??

```
jason@Hp-Vectra-VL:~$ sudo apt-get install alien
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://cipherfunk.org breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package alien
jason@Hp-Vectra-VL:~$

```

I do have the extra repo's enabled , **universe and multiverse**...

So why can't it even be found..??

---

### Post by BatteryCell on 2006-08-23
Did you run apt-get update and then try again?

---

### Post by jason.b.c on 2006-08-23
Ok i've got alien now...

Does this mean my game is installed..?
```
jason@Hp-Vectra-VL:~$ sudo alien -i /home/jason/Desktop/prboom-2.4.5-1.i386.rpm jason@Hp-Vectra-VL:~$


```

If so , How do i launch it...??
```
jason@Hp-Vectra-VL:~$ prboom
prboom: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
jason@Hp-Vectra-VL:~$


```

---

### Post by jason.b.c on 2006-08-23
*bump*

---

### Post by nalmeth on 2006-08-23
alien just turns the rmp into a deb, in the folder from which you ran it.

sudo dpkg -i prboom-2.4.5-1.i386.deb

---

### Post by jason.b.c on 2006-08-24
In the folder...???  What folder..??

> jason@Hp-Vectra-VL:~$ sudo dpkg -i prboom-2.4.5-1.i386.deb
Password:
dpkg: error processing prboom-2.4.5-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 prboom-2.4.5-1.i386.deb
jason@Hp-Vectra-VL:~$



---

### Post by nalmeth on 2006-08-24
Whoops, I totally misread your last post dude!

I suppose the -i option installs the .deb for you too does it?

It looks like you're missing some libraries or something. It was indeed successfully installed.

---

### Post by jason.b.c on 2006-08-24
Man , What the hell.???

> jason@Hp-Vectra-VL:~$ sudo alien -i /home/jason/Desktop/prboom-2.4.5-1.i386.rpm jason@Hp-Vectra-VL:~$ sudo dpkg -i prboom-2.4.5-1.i386.deb
dpkg: error processing prboom-2.4.5-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 prboom-2.4.5-1.i386.deb
jason@Hp-Vectra-VL:~$



](*,)

---

### Post by nalmeth on 2006-08-24
Prboom is already installed, thats what I meant to say. sudo alien -i aparently installs the created .deb for you too. I was previously not aware of this. I usually just run 
sudo alien xyz.rmp 
sudo dpkg -i xyz.deb
```
jason@Hp-Vectra-VL:~$ prboom
prboom: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
```
You're missing some SDL libraries.. I had a similar problem recently and couldn't figure it out. I haven't gone back to try yet either, but will PM you if I find out what needs to be done

---

### Post by jason.b.c on 2006-08-24
So it's not gonna work..??  , Ah crap...:roll:    Dang it , i want some cool games in here...

---

### Post by nalmeth on 2006-08-24
Theres a lot to go around:
[http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games)

---

### Post by diepruis on 2006-08-24
Try this:

```

sudo aptitude update
sudo aptitude install libsdl-mixer1.2

```

Then try running it again. Let us know if it works.

---

### Post by jason.b.c on 2006-08-24
Nope.! , Still nothin'...

> jason@Hp-Vectra-VL:~$ sudo apt-get install libsdl-mixer1.2
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libsdl-mixer1.2
0 upgraded, 1 newly installed, 0 to remove and 192 not upgraded.
Need to get 132kB of archives.
After unpacking 340kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libsdl-mixer1.2 1.2.6-1.1 [132kB]Fetched 132kB in 41s (3156B/s)
W: Couldn't stat source package list [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package libsdl-mixer1.2.
(Reading database ... 61921 files and directories currently installed.)
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.6-1.1_i386.deb) ...
Setting up libsdl-mixer1.2 (1.2.6-1.1) ...

W: Couldn't stat source package list [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
jason@Hp-Vectra-VL:~$ prboom
prboom: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory
jason@Hp-Vectra-VL:~$



What next..?

---

### Post by diepruis on 2006-08-24
Try:

```

sudo aptitude install libsdl-net1.2

```

---

### Post by jason.b.c on 2006-08-24
> **diepruis said:**
> Try:

```

sudo aptitude install libsdl-net1.2

```

How 'bout this..?
> jason@Hp-Vectra-VL:~$ sudo apt-get install libsdl-net1.2
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libsdl-net1.2
0 upgraded, 1 newly installed, 0 to remove and 192 not upgraded.
Need to get 9676B of archives.
After unpacking 65.5kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe libsdl-net1.2 1.2.5-3 [9676B]Fetched 9676B in 3s (2429B/s)
W: Couldn't stat source package list [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package libsdl-net1.2.
(Reading database ... 61928 files and directories currently installed.)
Unpacking libsdl-net1.2 (from .../libsdl-net1.2_1.2.5-3_i386.deb) ...
Setting up libsdl-net1.2 (1.2.5-3) ...

W: Couldn't stat source package list [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
jason@Hp-Vectra-VL:~$



Next.?

---

### Post by diepruis on 2006-08-24
Try running the program again :)

---

### Post by jason.b.c on 2006-08-24
Hell Yes..!

> jason@Hp-Vectra-VL:~$ prboom

prboom v2.4.5 ([http://prboom.sourceforge.net/](http://prboom.sourceforge.net/))
M_LoadDefaults: Load system defaults.
 default file: /home/jason/.prboom/prboom.cfg
 found /home/jason/.prboom/doom2.wad
IWAD found: /home/jason/.prboom/doom2.wad
PrBoom (built Aug 12 2006), playing: DOOM 2: Hell on Earth
PrBoom is released under the GNU General Public license v2.0.
You are welcome to redistribute it under certain conditions.
It comes with ABSOLUTELY NO WARRANTY. See the file COPYING for details.
V_Init: allocate screens.
 found /usr/share/games/doom/prboom.wad
D_InitNetGame: Checking for network game.
W_Init: Init WADfiles.
 adding /home/jason/.prboom/doom2.wad
 adding /usr/share/games/doom/prboom.wad
W_InitCache

M_Init: Init miscellaneous info.
R_Init: Init DOOM refresh daemon -
R_LoadTrigTables: Endianness...ok.
R_InitData: Textures Flats Sprites Tranmap build [........]
R_Init: R_InitPlanes R_InitLightTables R_InitSkyMap R_InitTranslationsTables R_InitPatches
P_Init: Init Playloop state.
I_Init: Setting up machine state.
I_InitSound: open /dev/sequencer: No such file or directory
 configured audio device with 1024 samples/slice
I_InitSound: sound module ready
S_Init: Setting up sound.
S_Init: default sfx volume 8
HU_Init: Setting up heads up display.
I_InitGraphics: 640x480
I_UpdateVideoMode: 640x480 (fullscreen)
V_InitMode: using 8 bit video mode
I_SetRes: Using resolution 640x480
I_UpdateVideoMode: 0xe0000000, SDL buffer, direct access
ST_Init: Init status bar.
Couldn't load MIDI from /tmp/prboom-music-csFXW3: /etc/timidity/timidity.cfg: No such file or directory
G_DoPlayDemo: playing demo with doom/doom2 v1.9 compatibility
Couldn't load MIDI from /tmp/prboom-music-csFXW3: /etc/timidity/timidity.cfg: No such file or directory
Using normal BSP nodes!
G_DoPlayDemo: playing demo with doom/doom2 v1.9 compatibility
Using normal BSP nodes!
I_ShutdownMusic: removing /tmp/prboom-music-csFXW3
I_ShutdownSound:







prboom v2.4.5 ([http://prboom.sourceforge.net/](http://prboom.sourceforge.net/))
jason@Hp-Vectra-VL:~$



---

### Post by Paul133 on 2006-08-24
So that worked...?

---

### Post by diepruis on 2006-08-24
Yeah, I'm also wondering. Was that a **good** hell yes, or a **bad** hell yes?

---

### Post by jason.b.c on 2006-08-25
> **diepruis said:**
> Yeah, I'm also wondering. Was that a **good** hell yes, or a **bad** hell yes?

No it's a **good hell yes** , It works...\\:D/

---

### Post by diepruis on 2006-08-26
\m/ Hell yeah! \m/

---

