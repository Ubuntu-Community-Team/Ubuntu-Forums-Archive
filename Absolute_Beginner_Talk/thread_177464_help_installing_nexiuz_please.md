---
title: "help installing nexiuz please"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2006-05-16
i've downloaded "nexuiz_1.5-english-2.run" and i read this thread [http://www.ubuntuforums.org/showthread.php?t=124578&highlight=install+nexiuz](http://www.ubuntuforums.org/showthread.php?t=124578&highlight=install+nexiuz) and the reply makes no sense to me. when i try to run the file nothing seems to happen. althoug first it opened in gedit by default and then i tried to open it in a terminal and then nothing happens. can anyone help me please..........................

---

### Post by Sef on 2006-05-16
Where did you download it too? Your home directory, your desktop, or other?

---

### Post by e1ektrob0y on 2006-05-16
[QUOTE=Sef]Where did you download it too? Your home directory, your desktop, or other?[/QUOTE]
i downloaded it to the desktop.

---

### Post by mostwanted on 2006-05-16
do this:

```
chmod +x ~/Desktop/nexuiz_1.5-english-2.run
sudo ~/Desktop/nexuiz_1.5-english-2.run
```

First command makes it executable, second command runs it with super user privileges.

Edit: Hm, just saw the topic you linked to... this may not work afterall. Try it anyway (and show us the error message it outputs if it doesn't work).

---

### Post by e1ektrob0y on 2006-05-16
so it installed fine but then when i clicked "run" it didn't work. also it appears in "run applications" but nothing happens when i click run.
```
ales@dales-desktop:~$ chmod +x ~/Desktop/nexuiz_1.5-english-2.run dales@dales-desktop:~$ sudo ~/Desktop/nexuiz_1.5-english-2.run
Password:
Verifying archive integrity... All good.
Uncompressing Nexuiz 1.5-english Installer.................................................................

Gdk-WARNING **: locale not supported by C library
./nexuiz-sdl: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
dales@dales-desktop:~$
```

---

### Post by mostwanted on 2006-05-16
[QUOTE=e1ektrob0y]so it installed fine but then when i clicked "run" it didn't work. also it appears in "run applications" but nothing happens when i click run.
```
ales@dales-desktop:~$ chmod +x ~/Desktop/nexuiz_1.5-english-2.run dales@dales-desktop:~$ sudo ~/Desktop/nexuiz_1.5-english-2.run
Password:
Verifying archive integrity... All good.
Uncompressing Nexuiz 1.5-english Installer.................................................................

Gdk-WARNING **: locale not supported by C library
./nexuiz-sdl: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
dales@dales-desktop:~$
```[/QUOTE]

Install libstdc++ 5. You can get it from the repositories.

---

### Post by e1ektrob0y on 2006-05-17
ok i installed it and now i get this message:
```
dales@dales-desktop:~$ nexuiz
^7Nexuiz Linux 13:24:29 Feb 13 2006
^7Trying to load library... "libz.so.1" - loaded.
^7Compressed files support enabled
^7Added packfile data/data20060214.pk3 (2537 files)
^7Console initialized.
^7Playing registered version.
^7Initializing client
^7Trying to load library... "libvorbis.so.0" - loaded.
^7Trying to load library... "libvorbisfile.so.3" - loaded.
^7Ogg Vorbis support enabled
^7couldn't exec config.cfg
^7couldn't exec autoexec.cfg
^70 demo(s) in loop
^7No demos listed with startdemos
^7Starting video system
^7Video: fullscreen 800x600x32x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 800x600: <%
^7<%
^7Desired video mode fail, trying fallbacks...
^7Video: fullscreen 800x600x32x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 800x600: <%
^7<%
^7Video: fullscreen 800x600x16x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 800x600: <%
^7<%
^7Video: fullscreen 640x480x16x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 640x480: <%
^7<%
^7Video: window 640x480x16x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 640x480: <%
^7<%
^7Quake Error: Video modes failed
dales@dales-desktop:~$
```

---

### Post by mostwanted on 2006-05-17
[QUOTE=e1ektrob0y]ok i installed it and now i get this message:
```
dales@dales-desktop:~$ nexuiz
^7Nexuiz Linux 13:24:29 Feb 13 2006
^7Trying to load library... "libz.so.1" - loaded.
^7Compressed files support enabled
^7Added packfile data/data20060214.pk3 (2537 files)
^7Console initialized.
^7Playing registered version.
^7Initializing client
^7Trying to load library... "libvorbis.so.0" - loaded.
^7Trying to load library... "libvorbisfile.so.3" - loaded.
^7Ogg Vorbis support enabled
^7couldn't exec config.cfg
^7couldn't exec autoexec.cfg
^70 demo(s) in loop
^7No demos listed with startdemos
^7Starting video system
^7Video: fullscreen 800x600x32x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 800x600: <%
^7<%
^7Desired video mode fail, trying fallbacks...
^7Video: fullscreen 800x600x32x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 800x600: <%
^7<%
^7Video: fullscreen 800x600x16x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 800x600: <%
^7<%
^7Video: fullscreen 640x480x16x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 640x480: <%
^7<%
^7Video: window 640x480x16x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.7
^7Failed to set video mode to 640x480: <%
^7<%
^7Quake Error: Video modes failed
dales@dales-desktop:~$
```[/QUOTE]


Try installing sdl....

---

### Post by e1ektrob0y on 2006-05-17
[QUOTE=mostwanted]Try installing sdl....[/QUOTE]
this is what i have installed:
[IMG]http://i74.photobucket.com/albums/i247/dales618/Screenshot2sdl.png[/IMG]

its trying to use version 1.2.7 and i have 1.2.9. is there anyway to change which version it trys to use?

---

### Post by e1ektrob0y on 2006-05-23
bump

---

