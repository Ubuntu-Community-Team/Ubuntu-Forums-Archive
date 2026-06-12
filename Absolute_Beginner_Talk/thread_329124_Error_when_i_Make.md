---
title: "Error when i *Make*"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Torn on 2007-01-01
make
make  all-am
make[1]: Entering directory `/home/outlaw/Desktop/3ddesktop-0.2.9'
if g++ -DHAVE_CONFIG_H -I. -I. -I.    -Wall -O3 -DQT_CLEAN_NAMESPACE -DSHAREDIR=\"/usr/local/share/3ddesktop\" -DSYSCONFDIR=\"/usr/local/etc\"   -g -O2  -MT 3ddeskd.o -MD -MP -MF ".deps/3ddeskd.Tpo" -c -o 3ddeskd.o 3ddeskd.cpp; \
        then mv -f ".deps/3ddeskd.Tpo" ".deps/3ddeskd.Po"; else rm -f ".deps/3ddeskd.Tpo"; exit 1; fi
In file included from 3ddeskd.cpp:56:
face.hpp:26:20: error: GL/glu.h: No such file or directory
In file included from arrange.hpp:29,
                 from 3ddeskd.cpp:57:
xutil.hpp:32:20: error: GL/glx.h: No such file or directory
face.hpp: In member function &#65533;&#65533;&#65533;void Face::load_texture_data(int, unsigned char*)&#65533;&#65533;&#65533;:
face.hpp:244: error: &#65533;&#65533;&#65533;gluBuild2DMipmaps&#65533;&#65533;&#65533; was not declared in this scope
face.hpp:246: error: &#65533;&#65533;&#65533;gluBuild2DMipmaps&#65533;&#65533;&#65533; was not declared in this scope
win.hpp: At global scope:
win.hpp:29: error: &#65533;&#65533;&#65533;GLXContext&#65533;&#65533;&#65533; does not name a type
win.hpp:34: error: ISO C++ forbids declaration of &#65533;&#65533;&#65533;XVisualInfo&#65533;&#65533;&#65533; with no type
win.hpp:34: error: expected &#65533;&#65533;&#65533;;&#65533;&#65533;&#65533; before &#65533;&#65533;&#65533;*&#65533;&#65533;&#65533; token
3ddeskd.cpp: In function &#65533;&#65533;&#65533;void render_scene()&#65533;&#65533;&#65533;:
3ddeskd.cpp:1073: error: &#65533;&#65533;&#65533;glXSwapBuffers&#65533;&#65533;&#65533; was not declared in this scope
3ddeskd.cpp: In function &#65533;&#65533;&#65533;void load_digits()&#65533;&#65533;&#65533;:
3ddeskd.cpp:2219: error: &#65533;&#65533;&#65533;gluBuild2DMipmaps&#65533;&#65533;&#65533; was not declared in this scope
3ddeskd.cpp: In function &#65533;&#65533;&#65533;void load_background_image()&#65533;&#65533;&#65533;:
3ddeskd.cpp:2305: error: &#65533;&#65533;&#65533;gluBuild2DMipmaps&#65533;&#65533;&#65533; was not declared in this scope
make[1]: *** [3ddeskd.o] Error 1
make[1]: Leaving directory `/home/outlaw/Desktop/3ddesktop-0.2.9'
make: *** [all] Error 2

---

### Post by meng on 2007-01-01
You realize that 3ddesktop can be installed from repositories, don't you?

---

### Post by Torn on 2007-01-01
im new to this, but, i looked into the .rpm and i did get that to come up in synamtic and installed... but when i try to run the command i got nothing

---

### Post by meng on 2007-01-01
(They're debs not rpms)
Did you run:
3ddesk --acquire
?

---

### Post by Torn on 2007-01-01
3ddesk --acquire
bash: 3ddesk: command not found

il try installing off a deb then

---

### Post by meng on 2007-01-01
Wait a tick .. Go to Synaptic package manager and install it from there. Don't download the debs manually!

---

### Post by meng on 2007-01-01
On second thoughts, I think you need to stop and read about how to install software in Ubuntu. For 3ddesktop you will also need extra repositories (universe), so look here.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

You can use Synaptic, or else from the command line (once universe enabled), run:
sudo aptitude install 3ddesktop

---

