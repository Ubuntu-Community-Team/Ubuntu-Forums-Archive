---
title: "compilation failed, aborting install.....wine"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2005-12-20
While following this link [http://www.ubuntuforums.org/showthread.php?t=29996&highlight=howto+wine]("http://www.ubuntuforums.org/showthread.php?t=29996&highlight=howto+wine")everything appeared to be going smoothly, up until I issued the './tools/wineinstall' command. It began compiling for 10 or so minutes, was able to answer yes to run as root, a few minutes later I get the following:

> make[2]: Leaving directory `/home/rosso/cvs/wine/programs/winefile'
make[2]: Entering directory `/home/rosso/cvs/wine/programs/winemenubuilder'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/rosso/cvs/wine/programs/winemenubuilder'
make[2]: Entering directory `/home/rosso/cvs/wine/programs/winemine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/rosso/cvs/wine/programs/winemine'
make[2]: Entering directory `/home/rosso/cvs/wine/programs/winepath'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/rosso/cvs/wine/programs/winepath'
make[2]: Entering directory `/home/rosso/cvs/wine/programs/winetest'
[B]make[2]: *** No rule to make target `../../dlls/d3d9/tests/d3d9_test.exe.so', needed by `d3d9_test.exe.so'.  Stop.
make[2]: Leaving directory `/home/rosso/cvs/wine/programs/winetest'
make[1]: *** [winetest] Error 2
make[1]: Leaving directory `/home/rosso/cvs/wine/programs'
make: *** [programs] Error 2

Compilation failed, aborting install.
rosso@Gianuntu:~/cvs/wine$ pwd
/home/rosso/cvs/wine
rosso@Gianuntu:~/cvs/wine$[/B]
. Does anyone please have any insight to what happened? I would appreciate the help.

Thank you :)

---

### Post by Enter on 2005-12-20
i installed wine in synaptic and then just entered "wine" in the terminal it gave me a lot of text and then gave me this
Wine 20050725
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
enter@localhost:~$

tested it on winamp and it worked :D
dont know if this helps :D

---

### Post by Il_Tuo_Nome on 2005-12-20
To install through Synaptic was my next step. Before I do that I was hoping someone had a resolution of some sort to my above problem? If not, could someone at least tell me if I go ahead and install through synaptic, will it overwrite what I've already done or will it cause some conflictions?

thanks

---

### Post by Enter on 2005-12-20
im new here but it looks like if you can install it via synaptic, better install it via synaptic
i thnk in synaptic it will show that its installed just mark it for reinstall or something, or if its not marked just install it then go to terminal write wine it then mill configure it self or something

Sorry i can say more its my 3rd day only and this way worked for me so... thats all i can suggest

---

### Post by Il_Tuo_Nome on 2005-12-20
I think you're right, better that way

Thank you for suggestion :)

---

