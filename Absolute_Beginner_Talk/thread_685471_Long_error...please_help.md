---
title: "Long error...please help"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by djnet on 2008-02-02
so im trying to install freecnc++...a free version of red alert from westwood...

Heres all what i did, i ran the apt get commands, like the update, build essentials, install gcc-c++ and all that.

but when i try to run the make command on it I get this

```
cjay@Cjay-Linux:~/freecnc++$ make
make -C src
/bin/sh: --cflags: command not found
make[1]: Entering directory `/home/cjay/freecnc++/src'
g++ -Wall -Werror -g   -std=c++98 -Wconversion -W -Wno-unused -c freecnc.cpp -o freecnc.o -I./include  -I./include/lua
freecnc.cpp:13:17: error: SDL.h: No such file or directory
In file included from freecnc.cpp:15:
./include/common.h:5:23: error: SDL_types.h: No such file or directory
In file included from freecnc.cpp:16:
./include/config.h:6:23: error: SDL_video.h: No such file or directory
./include/config.h:7:24: error: SDL_keysym.h: No such file or directory
In file included from freecnc.cpp:18:
./include/graphicsengine.h:9:17: error: SDL.h: No such file or directory
In file included from freecnc.cpp:21:
./include/soundengine.h:9:23: error: SDL_audio.h: No such file or directory
./include/soundengine.h:10:23: error: SDL_mixer.h: No such file or directory
In file included from ./include/vfs.h:8,
                 from freecnc.cpp:22:
./include/../vfs/archive.h:5:23: error: SDL_types.h: No such file or directory
./include/common.h:87: error: &#8216;Uint8&#8217; does not name a type
./include/common.h:91: error: &#8216;Uint16&#8217; does not name a type
./include/common.h:110: error: &#8216;Uint32&#8217; does not name a type
./include/common.h:111: error: &#8216;Uint8&#8217; does not name a type
./include/common.h:112: error: &#8216;Uint8&#8217; does not name a type
./include/common.h:113: error: &#8216;Uint16&#8217; does not name a type
./include/common.h:118: error: &#8216;Uint16&#8217; does not name a type
./include/common.h:119: error: &#8216;Uint16&#8217; does not name a type
./include/config.h:12: error: &#8216;Uint8&#8217; does not name a type
./include/config.h:21: error: &#8216;Uint32&#8217; does not name a type
./include/config.h:22: error: &#8216;Uint16&#8217; does not name a type
./include/config.h:23: error: &#8216;Uint8&#8217; does not name a type
./include/config.h:27: error: &#8216;SDL_GrabMode&#8217; does not name a type
./include/config.h:28: error: &#8216;SDLKey&#8217; does not name a type
./include/config.h:29: error: &#8216;Uint8&#8217; does not name a type
./include/config.h:30: error: &#8216;Uint8&#8217; does not name a type
./include/game.h:20: error: &#8216;Uint8&#8217; does not name a type
./include/message.h:14: error: &#8216;Uint32&#8217; has not been declared
./include/message.h:27: error: &#8216;Uint32&#8217; does not name a type
./include/message.h:33: error: &#8216;Uint32&#8217; does not name a type
./include/message.h: In constructor &#8216;Message::Message(const char*, int)&#8217;:
./include/message.h:17: error: &#8216;class Message&#8217; has no member named &#8216;deltime&#8217;
./include/message.h: At global scope:
./include/message.h:41: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
./include/message.h:41: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/message.h:49: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
./include/message.h:49: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/graphicsengine.h:23: error: &#8216;Uint16&#8217; does not name a type
./include/graphicsengine.h:27: error: &#8216;Uint16&#8217; does not name a type
./include/graphicsengine.h:31: error: ISO C++ forbids declaration of &#8216;SDL_Rect&#8217; with no type
./include/graphicsengine.h:31: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/graphicsengine.h:35: error: expected `;' before &#8216;void&#8217;
./include/graphicsengine.h:35: error: &#8216;SDL_Surface&#8217; has not been declared
./include/graphicsengine.h:42: error: &#8216;SDL_Surface&#8217; has not been declared
./include/graphicsengine.h:45: error: &#8216;SDL_Rect&#8217; has not been declared
./include/graphicsengine.h:46: error: &#8216;SDL_Rect&#8217; has not been declared
./include/graphicsengine.h:46: error: &#8216;SDL_Rect&#8217; has not been declared
./include/graphicsengine.h:48: error: &#8216;Sint16&#8217; has not been declared
./include/graphicsengine.h:48: error: &#8216;Sint16&#8217; has not been declared
./include/graphicsengine.h:49: error: &#8216;Sint16&#8217; has not been declared
./include/graphicsengine.h:49: error: &#8216;Sint16&#8217; has not been declared
./include/graphicsengine.h:49: error: &#8216;Uint16&#8217; has not been declared
./include/graphicsengine.h:49: error: &#8216;Uint32&#8217; has not been declared
./include/graphicsengine.h:50: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
./include/graphicsengine.h:50: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/graphicsengine.h:51: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
./include/graphicsengine.h:51: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/graphicsengine.h:52: error: &#8216;Uint16&#8217; does not name a type
./include/graphicsengine.h:53: error: &#8216;Uint16&#8217; does not name a type
./include/graphicsengine.h:54: error: &#8216;Uint16&#8217; does not name a type
./include/graphicsengine.h:55: error: &#8216;SDL_Rect&#8217; does not name a type
./include/graphicsengine.h:58: error: &#8216;Uint8&#8217; does not name a type
./include/graphicsengine.h:59: error: &#8216;Uint8&#8217; does not name a type
./include/graphicsengine.h:62: error: ISO C++ forbids declaration of &#8216;Uint8&#8217; with no type
./include/graphicsengine.h:62: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/graphicsengine.h:64: error: &#8216;Uint32&#8217; was not declared in this scope
./include/graphicsengine.h:64: error: template argument 1 is invalid
./include/graphicsengine.h:64: error: template argument 2 is invalid
./include/inifile.h:39: error: &#8216;Uint32&#8217; has not been declared
./include/inifile.h:42: error: &#8216;Uint32&#8217; has not been declared
./include/inifile.h:43: error: &#8216;Uint32&#8217; has not been declared
./include/inifile.h:44: error: &#8216;Uint32&#8217; has not been declared
./include/soundengine.h:20: error: &#8216;Uint8&#8217; was not declared in this scope
./include/soundengine.h:20: error: template argument 1 is invalid
./include/soundengine.h:20: error: template argument 2 is invalid
./include/soundengine.h:20: error: invalid type in declaration before &#8216;;&#8217; token
./include/soundengine.h:23: error: ISO C++ forbids declaration of &#8216;Mix_Chunk&#8217; with no type
./include/soundengine.h:23: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/soundengine.h:27: error: &#8216;Uint32&#8217; does not name a type
./include/soundengine.h:55: error: &#8216;Uint8&#8217; has not been declared
./include/soundengine.h:75: error: &#8216;SDL_AudioCVT&#8217; does not name a type
./include/soundengine.h:76: error: &#8216;SDL_AudioCVT&#8217; does not name a type
./include/../vfs/archive.h:19: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:20: error: &#8216;Uint32&#8217; has not been declared
./include/../vfs/archive.h:22: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:23: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:24: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:25: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:26: error: &#8216;readLine&#8217; declared as a &#8216;virtual&#8217; field
./include/../vfs/archive.h:26: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
./include/../vfs/archive.h:31: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:32: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:33: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:34: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:35: error: &#8216;Uint32&#8217; has not been declared
./include/../vfs/archive.h:36: error: &#8216;Uint32&#8217; has not been declared
./include/../vfs/archive.h:37: error: &#8216;Uint32&#8217; has not been declared
./include/../vfs/archive.h:39: error: &#8216;Uint32&#8217; has not been declared
./include/../vfs/archive.h:39: error: &#8216;Uint32&#8217; has not been declared
./include/../vfs/archive.h:40: error: &#8216;Uint32&#8217; has not been declared
./include/../vfs/archive.h:40: error: &#8216;Sint32&#8217; has not been declared
./include/../vfs/archive.h:42: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:43: error: &#8216;Uint32&#8217; does not name a type
./include/../vfs/archive.h:44: error: &#8216;getPath&#8217; declared as a &#8216;virtual&#8217; field
./include/../vfs/archive.h:44: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
./include/vfs.h:17: error: expected `)' before &#8216;filenum&#8217;
./include/vfs.h:27: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:31: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:35: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:39: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:43: error: &#8216;Uint32&#8217; has not been declared
./include/vfs.h:48: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:52: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:56: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:60: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:86: error: &#8216;Uint32&#8217; has not been declared
./include/vfs.h:90: error: &#8216;Sint32&#8217; has not been declared
./include/vfs.h:94: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:98: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h:108: error: &#8216;Uint32&#8217; does not name a type
./include/vfs.h: In destructor &#8216;VFile::~VFile()&#8217;:
./include/vfs.h:23: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: In member function &#8216;char* VFile::getLine(char*, int)&#8217;:
./include/vfs.h:45: error: &#8216;class Archive&#8217; has no member named &#8216;readLine&#8217;
./include/vfs.h:45: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: In member function &#8216;void VFile::writeLine(const char*)&#8217;:
./include/vfs.h:66: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: In member function &#8216;int VFile::vfs_printf(const char*, ...)&#8217;:
./include/vfs.h:73: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: In member function &#8216;int VFile::vfs_vprintf(const char*, char*)&#8217;:
./include/vfs.h:79: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: In member function &#8216;void VFile::flush()&#8217;:
./include/vfs.h:83: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: In member function &#8216;void VFile::seekSet(int)&#8217;:
./include/vfs.h:88: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: In member function &#8216;void VFile::seekCur(int)&#8217;:
./include/vfs.h:92: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: In member function &#8216;const char* VFile::getPath()&#8217;:
./include/vfs.h:105: error: &#8216;class Archive&#8217; has no member named &#8216;getPath&#8217;
./include/vfs.h:105: error: &#8216;filenum&#8217; was not declared in this scope
./include/vfs.h: At global scope:
./include/vfs.h:123: error: &#8216;const char* VFS_getFirstExisting&#8217; redeclared as different kind of symbol
./include/vfs.h:122: error: previous declaration of &#8216;const char* VFS_getFirstExisting(const std::vector<const char*, std::allocator<const char*> >&)&#8217;
./include/vfs.h:123: error: &#8216;Uint32&#8217; was not declared in this scope
./include/vfs.h:123: error: expected primary-expression before &#8216;...&#8217; token
./include/vqa.h:12: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:13: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:14: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:15: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:16: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:17: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:18: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:19: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:20: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:21: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:22: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:23: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:24: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:25: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:26: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:27: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:28: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:29: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:30: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:49: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:50: error: &#8216;SDL_Surface&#8217; has not been declared
./include/vqa.h:52: error: &#8216;Uint8&#8217; has not been declared
./include/vqa.h:53: error: &#8216;Uint8&#8217; has not been declared
./include/vqa.h:54: error: &#8216;SDL_Color&#8217; has not been declared
./include/vqa.h:61: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:62: error: &#8216;Uint16&#8217; does not name a type
./include/vqa.h:63: error: ISO C++ forbids declaration of &#8216;Uint8&#8217; with no type
./include/vqa.h:63: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/vqa.h:64: error: ISO C++ forbids declaration of &#8216;Uint8&#8217; with no type
./include/vqa.h:64: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/vqa.h:65: error: ISO C++ forbids declaration of &#8216;Uint8&#8217; with no type
./include/vqa.h:65: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/vqa.h:66: error: ISO C++ forbids declaration of &#8216;Uint32&#8217; with no type
./include/vqa.h:66: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/vqa.h:67: error: &#8216;Uint8&#8217; does not name a type
./include/vqa.h:68: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:70: error: &#8216;Sint32&#8217; does not name a type
./include/vqa.h:71: error: &#8216;Sint32&#8217; does not name a type
./include/vqa.h:82: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:85: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:86: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:87: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:88: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:89: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:90: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:91: error: &#8216;Uint32&#8217; does not name a type
./include/vqa.h:92: error: &#8216;Uint32&#8217; does not name a type
./include/wsa.h:14: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
./include/wsa.h:14: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/wsa.h:15: error: ISO C++ forbids declaration of &#8216;Uint8&#8217; with no type
./include/wsa.h:15: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/wsa.h:16: error: ISO C++ forbids declaration of &#8216;Uint8&#8217; with no type
./include/wsa.h:16: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./include/wsa.h:17: error: &#8216;SDL_Color&#8217; does not name a type
./include/wsa.h:18: error: &#8216;Uint8&#8217; does not name a type
./include/wsa.h:21: error: &#8216;Uint16&#8217; does not name a type
./include/wsa.h:22: error: &#8216;Uint16&#8217; does not name a type
./include/wsa.h:23: error: &#8216;Uint16&#8217; does not name a type
./include/wsa.h:24: error: &#8216;Uint16&#8217; does not name a type
./include/wsa.h:25: error: &#8216;Uint16&#8217; does not name a type
./include/wsa.h:26: error: &#8216;Uint32&#8217; does not name a type
./include/wsa.h:27: error: ISO C++ forbids declaration of &#8216;Uint32&#8217; with no type
./include/wsa.h:27: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
freecnc.cpp: In function &#8216;int main(int, char**)&#8217;:
freecnc.cpp:86: error: &#8216;SDL_INIT_VIDEO&#8217; was not declared in this scope
freecnc.cpp:86: error: &#8216;SDL_INIT_AUDIO&#8217; was not declared in this scope
freecnc.cpp:86: error: &#8216;SDL_INIT_TIMER&#8217; was not declared in this scope
freecnc.cpp:86: error: &#8216;SDL_Init&#8217; was not declared in this scope
freecnc.cpp:87: error: &#8216;SDL_GetError&#8217; was not declared in this scope
freecnc.cpp:97: error: &#8216;SDL_ShowCursor&#8217; was not declared in this scope
freecnc.cpp:119: error: &#8216;Uint8&#8217; was not declared in this scope
freecnc.cpp:119: error: expected `;' before &#8216;ret&#8217;
freecnc.cpp:124: error: &#8216;ret&#8217; was not declared in this scope
freecnc.cpp:126: error: &#8216;ret&#8217; was not declared in this scope
freecnc.cpp:130: error: &#8216;const struct ConfigType&#8217; has no member named &#8216;intro&#8217;
freecnc.cpp: In function &#8216;void cleanup()&#8217;:
freecnc.cpp:201: error: &#8216;SDL_Quit&#8217; was not declared in this scope
make[1]: *** [freecnc.o] Error 1
make[1]: Leaving directory `/home/cjay/freecnc++/src'
make: *** [default] Error 2

```

oh and when i run ./configure i get this
```
cjay@Cjay-Linux:~/freecnc++$ ./configure
bash: ./configure: No such file or directory

```

Some please help me figure out this is...


Thanks in advanced

---

### Post by jordanmthomas on 2008-02-02
Have you installed libdevel/libsdl1.2-dev ?
That's where SDL.h is located, and having it would probably take care of a bunch of your compile errors.

---

### Post by djnet on 2008-02-02
is there a way to get that if its not on my synaptec list

---

### Post by djnet on 2008-02-04
please someone help

---

### Post by jordanmthomas on 2008-02-04
[http://packages.ubuntu.com/gutsy/libdevel/libsdl1.2-dev](http://packages.ubuntu.com/gutsy/libdevel/libsdl1.2-dev)

---

### Post by Nerdriot on 2008-02-11
Hey, I'm having a similar issue...

After installing libsdl1.2-dev, it seemed to want to compile, but ran across this error (I'm a total compiling noob0rcycle.):

```
:~/Games/freecnc++/src$ make
g++ -Wall -Werror -g  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -std=c++98 -Wconversion -W -Wno-unused -c freecnc.cpp -o freecnc.o -I./include  -I./include/lua
In file included from freecnc.cpp:21:
./include/soundengine.h:10:23: error: SDL_mixer.h: No such file or directory
./include/soundengine.h:23: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
./include/soundengine.h:23: error: expected ‘;’ before ‘*’ token
make: *** [freecnc.o] Error 1

```

Any ideas? Please and thank you. :)

---

### Post by Nerdriot on 2008-02-11
Scratch that. Fixed it by installing the libsdl-mixer1.2-dev

Now, a new problem. I'm COMPLETELY lost on this one:

```
Going to use Linux specific settings
make -C src
make[1]: Entering directory `/home/ben/Games/freecnc++/src'
g++ -Wall -Werror -g  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -std=c++98 -Wconversion -W -Wno-unused -c game/dispatcher.cpp -o game/dispatcher.o -I./include  -I./include/lua
./include/structure.h:268: error: ISO C++ forbids declaration of &#8216;BuildingAnimEvent&#8217; with no type
./include/structure.h:268: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
make[1]: *** [game/dispatcher.o] Error 1
make[1]: Leaving directory `/home/ben/Games/freecnc++/src'
make: *** [default] Error 2

```

Wow. Wtf does that mean? I am a lost, lost young man....

Thanks for the help, anyone :)

---

### Post by Nerdriot on 2008-02-14
Superbump!

---

### Post by RJARRRPCGP on 2008-02-14
You're probably required to update the C++ compiler-related stuff. 

I gotten at least similar errors, including the dreaded "ISO C++ forbids X" error message until I updated what appeared to be C++ compiler-related.

---

### Post by Nerdriot on 2008-02-14
Well, this may sound completely supernoob, but how do I do that? ;x

---

