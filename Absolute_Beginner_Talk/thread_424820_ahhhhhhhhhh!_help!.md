---
title: "ahhhhhhhhhh! help!"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Psyclown on 2007-04-27
(excuse bad grammar, spelling, and typing in this.. i've been wrestling with terminal all day and im lavishing the freedom of being able to make typos and having the reader still know what you mean. ^_^)

argh so lost, just swiched from windows to ubuntu and i cant do anything. i tried to load WINE but when i run /home/myusername/tools/wineinstaller i get this

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Configure failed, aborting install.

so then i trid to get gcc and how the hell do you do that?? i mean i tried to download it but like.. where the hell do i put all that data? i can't find just a normal package and ALL IW ANNA DO IS RUN EXE's.... heeeeelp meeeeeeee *explodes* i tried downloading the sorce.. nope. and i don't know 1/4 of all the terminal commands... wtf? 

also anytime i try to run a apt-get i get this 

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

and that was when i wasnt running ANYTHING else and i just tried an apt-get clean

nope. 

sooo lost. 

i've spent a total of 7 hours looking up the docs and crap but nothing. mostly i would like help with the GCC side of things cause that should get win working wich ideally would make verything else run smoothly. thanks  guys!

---

### Post by wirelessmonkey on 2007-04-27
Command Line fix  -- sudo apt-get install build-essential

or 

Open synaptic search for build-essential, install. 


Now, try running the wineinstaller again. 


You need to have build tools installed on your system. Build-essential installs such goodies as GCC, make, automake, and others.


Post again if you get stuck.


WM

---

### Post by Psyclown on 2007-04-27
downloading now.. will post oncec done, if this works i officially love you (in a strictly hetero way)

---

### Post by zvacet on 2007-04-27
```
winecfg
```

---

### Post by Psyclown on 2007-04-27
while i am waiting though.. when i toss the command line version it asks me for a password.. and it isnt my user password.. wtf is up with that?

---

### Post by seshomaru samma on 2007-04-27
it is your user password

---

### Post by dreadlord_chris on 2007-04-27
Is there a particaular reason you are compiling wine from source? Do you realize there is a binary package (already compiled) in the repositories?

---

### Post by Psyclown on 2007-04-27
meh. i got wine up but now when i install apps it doesnt let me see them. even if i go to winecfg and add them in manually it still doesnt come up in wine under programs. any ideas?

---

### Post by az on 2007-04-27
Wine applications do not show up in the menu.

What do you need wine for?

---

### Post by Psyclown on 2007-04-27
only the realtek driver i installed shows up and i need it for WoW and itunes and maybe oblivion. now yet ANOTHER problem i ran into is i cant set my res to above 640x480. i just threw in a new video card and it has power.. but im not sure if im using it to display... sigh* this ubuntu thing is almost seeming like more trouble than its worth

---

### Post by az on 2007-04-28
> **Psyclown said:**
> only the realtek driver i installed shows up and i need it for WoW and itunes and maybe oblivion. now yet ANOTHER problem i ran into is i cant set my res to above 640x480. i just threw in a new video card and it has power.. but im not sure if im using it to display... sigh* this ubuntu thing is almost seeming like more trouble than its worth

If you change your video card, boot into recovery mode and run


dpkg-reconfigure -phigh xserver-xorg

and then

init 2

Are you trying to install a windows driver using wine?  You can't do that.  

For all issues, read the documentation in help.ubuntu.com/community

---

### Post by adza on 2007-04-28
i've had another issue with wine install.. will post here instead of creating a new one... the ./configure runs fine... however.. the gcc fails... here's the last of the code..

/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/adza/net_downloads/wine-0.9.36/dlls/ddraw'
make[1]: *** [ddraw] Error 2
make[1]: Leaving directory `/home/adza/net_downloads/wine-0.9.36/dlls'
make: *** [dlls] Error 2

---

