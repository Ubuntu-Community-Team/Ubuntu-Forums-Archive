---
title: "Installing Ming (Flash Creation Program)"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-06-01
A while back, when I was young, bored, and running windows, I downloaded a trial of flash. I could never afford the -huge- wad of cash necessary to poichase the full thing, so after my 14days that was that. *sniffles*
 Now I'm on Ubuntu, I thought I'd check out if there were any flash creation programs for linux. I found Ming.

 I have build-essential.

 I tried doing the installation (from the un-tarred folder) this way:
Right clicky 'ming-0.3.0' and opening in terminal. (same as cd to the directory)
Type ./configure.
Type make
Type sudo make install  (and insert password)

 Well, ./configure told me this:
```
raavea@bernard:~/Documents/Downloads/ming-0.3.0$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for python... /usr/bin/python
checking for PrintGifError in -lgif... no
checking for PrintGifError in -lungif... no
checking for png_read_image in -lpng... yes
checking for compress2 in -lz... yes
checking for sin... no
checking for sin in -lm... yes
configure: creating ./config.status
config.status: creating Makefile.config
config.status: creating src/ming.h
config.status: creating util/ming-config
config.status: creating src/ming_config.h
```

So I thought, oh, that looks okay. Whee. And typed make. Which gave me this:
```
raavea@bernard:~/Documents/Downloads/ming-0.3.0$ make
make -f Makefile-real all
make[1]: Entering directory `/home/raavea/Documents/Downloads/ming-0.3.0'
(cd src && make dynamic CFLAGS="-g -O2 -Wall -I.  -fPIC")
make[2]: Entering directory `/home/raavea/Documents/Downloads/ming-0.3.0/src'
gcc -g -O2 -Wall -I.  -fPIC   -c -o blocklist.o blocklist.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o displaylist.o displaylist.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o fill.o fill.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o font_util.o font_util.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o ming.o ming.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o movie.o movie.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o movieclip.o movieclip.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o position.o position.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o shape_cubic.o shape_cubic.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o shape_util.o shape_util.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o text_util.o text_util.c
gcc -g -O2 -Wall -I.  -fPIC   -c -o gc.o gc.c
cd blocks && make CFLAGS="-g -O2 -Wall -I.  -fPIC -I.."
make[3]: Entering directory `/home/raavea/Documents/Downloads/ming-0.3.0/src/blocks'
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o action.o action.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o bitmap.o bitmap.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o block.o block.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o browserfont.o browserfont.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o button.o button.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o character.o character.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o cxform.o cxform.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o dbl.o dbl.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o error.o error.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o fillstyle.o fillstyle.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o font.o font.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o fontinfo.o fontinfo.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o fromswf.o fromswf.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o gradient.o gradient.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o imports.o imports.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o input.o input.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o jpeg.o jpeg.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o linestyle.o linestyle.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o matrix.o matrix.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o method.o method.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o morph.o morph.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o mp3.o mp3.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o output.o output.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o outputblock.o outputblock.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o placeobject.o placeobject.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o rect.o rect.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o shape.o shape.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o sound.o sound.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o soundinstance.o soundinstance.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o soundstream.o soundstream.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o sprite.o sprite.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o text.o text.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o textfield.o textfield.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o utf8.o utf8.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o videostream.o videostream.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o pngdbl.o pngdbl.c
make[3]: Leaving directory `/home/raavea/Documents/Downloads/ming-0.3.0/src/blocks'
cd actioncompiler && make CFLAGS="-g -O2 -Wall -I.  -fPIC -I.."
make[3]: Entering directory `/home/raavea/Documents/Downloads/ming-0.3.0/src/actioncompiler'
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o compile.o compile.c
gcc -g -O2 -Wall -I.  -fPIC -I..   -c -o listaction.o listaction.c
bison --defines --debug -p swf4 swf4compiler.y
make[3]: bison: Command not found
make[3]: *** [swf4compiler.tab.h] Error 127
make[3]: Leaving directory `/home/raavea/Documents/Downloads/ming-0.3.0/src/actioncompiler'
make[2]: *** [libming.so.0.3.0] Error 2
make[2]: Leaving directory `/home/raavea/Documents/Downloads/ming-0.3.0/src'
make[1]: *** [dynamic] Error 2
make[1]: Leaving directory `/home/raavea/Documents/Downloads/ming-0.3.0'
make: *** [all] Error 2
```

And I thought... Errr... Might as well go the whole hog and try install anyhow. So I did, which gave me this:
```
raavea@bernard:~/Documents/Downloads/ming-0.3.0$ sudo make install
Password:
make -f Makefile-real install
make[1]: Entering directory `/home/raavea/Documents/Downloads/ming-0.3.0'
install -d /usr/local/lib
install -d /usr/local/include
install -c -m 0644 src/ming.h /usr/local/include
install -c -m 0644 src/ming_config.h /usr/local/include
install -c -m 0644 mingpp.h /usr/local/include
(cd src && make dynamic CFLAGS="-g -O2 -Wall -I.  -fPIC")
make[2]: Entering directory `/home/raavea/Documents/Downloads/ming-0.3.0/src'
cd blocks && make CFLAGS="-g -O2 -Wall -I.  -fPIC -I.."
make[3]: Entering directory `/home/raavea/Documents/Downloads/ming-0.3.0/src/blocks'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/raavea/Documents/Downloads/ming-0.3.0/src/blocks'
cd actioncompiler && make CFLAGS="-g -O2 -Wall -I.  -fPIC -I.."
make[3]: Entering directory `/home/raavea/Documents/Downloads/ming-0.3.0/src/actioncompiler'
bison --defines --debug -p swf4 swf4compiler.y
make[3]: bison: Command not found
make[3]: *** [swf4compiler.tab.h] Error 127
make[3]: Leaving directory `/home/raavea/Documents/Downloads/ming-0.3.0/src/actioncompiler'
make[2]: *** [libming.so.0.3.0] Error 2
make[2]: Leaving directory `/home/raavea/Documents/Downloads/ming-0.3.0/src'
make[1]: *** [dynamic] Error 2
make[1]: Leaving directory `/home/raavea/Documents/Downloads/ming-0.3.0'
make: *** [install] Error 2
```

 Basically, my question being: what's wrong, how do I fix it, and if I can't how do I remove what's been done so far?

---

### Post by [S|G] on 2006-06-01
Judging from the error messages, you need to install bison to make it work. Google pointed me at [http://www.gnu.org/software/bison/](http://www.gnu.org/software/bison/) when I did a search for bison. I also checked on the repos, and there are bison packages there :)

You should try
```

sudo apt-get install bison

```
Also, you might need either bison++ or bison-1.35 to make it work. I'm going to give it a try myself in a moment, a flash tool for linux greatly interests me :)

---

### Post by Raavea on 2006-06-03
Wahey.
 I eyed up the reports and tried your suggestion of installing Bison (bog-standard Bison, from the synaptic repositories), but got the same errors.

 Tried again a few days later and I got new, different errors! I think that it didn't register I'd installed Bison because I didn't re-start my terminal.

 Anyhow, the new errors mentioned a command 'flex'. So I thought, what the hell. Hunted in the repositories and found Flex! Installed Flex, and (I haven't tried yet but there weren't any errors!) I have installed ming! :D

---

