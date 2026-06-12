---
title: "Ok...very new...need help :("
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by djnet on 2008-02-01
I have been trying to install a freecnc which is a free version of command and conquer red alert... i try to run the make command...and it gives me this

ok new set of problems... i ran the make command...and i get this

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

---

### Post by spiderbatdad on 2008-02-01
```
sudo apt-get install build-essential
```

---

### Post by jaytek13 on 2008-02-01
Do this

```

sudo apt-get install build-essential

```

And that will install all the tools you need to be able to compile it.

---

### Post by djnet on 2008-02-01
ok i did that, and it stuck at this

```
Media change: please insert the disc labeled
 'Edubuntu 7.04 _Feisty Fawn_ - Release i386 Binary-1 (20070415)'
in the drive '/cdrom/' and press enter

```

and i put the disk in and it didn't continue

---

### Post by spiderbatdad on 2008-02-01
not sure if that package is part of edubuntu. Do you have synaptic package manager...look for it in there.

---

### Post by djnet on 2008-02-01
I got it, wrong disk lol...thanks guys

---

### Post by djnet on 2008-02-01
ok new set of problems... i ran the make command...and i get this

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
./include/common.h:87: error: ‘Uint8’ does not name a type
./include/common.h:91: error: ‘Uint16’ does not name a type
./include/common.h:110: error: ‘Uint32’ does not name a type
./include/common.h:111: error: ‘Uint8’ does not name a type
./include/common.h:112: error: ‘Uint8’ does not name a type
./include/common.h:113: error: ‘Uint16’ does not name a type
./include/common.h:118: error: ‘Uint16’ does not name a type
./include/common.h:119: error: ‘Uint16’ does not name a type
./include/config.h:12: error: ‘Uint8’ does not name a type
./include/config.h:21: error: ‘Uint32’ does not name a type
./include/config.h:22: error: ‘Uint16’ does not name a type
./include/config.h:23: error: ‘Uint8’ does not name a type
./include/config.h:27: error: ‘SDL_GrabMode’ does not name a type
./include/config.h:28: error: ‘SDLKey’ does not name a type
./include/config.h:29: error: ‘Uint8’ does not name a type
./include/config.h:30: error: ‘Uint8’ does not name a type
./include/game.h:20: error: ‘Uint8’ does not name a type
./include/message.h:14: error: ‘Uint32’ has not been declared
./include/message.h:27: error: ‘Uint32’ does not name a type
./include/message.h:33: error: ‘Uint32’ does not name a type
./include/message.h: In constructor ‘Message::Message(const char*, int)’:
./include/message.h:17: error: ‘class Message’ has no member named ‘deltime’
./include/message.h: At global scope:
./include/message.h:41: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
./include/message.h:41: error: expected ‘;’ before ‘*’ token
./include/message.h:49: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
./include/message.h:49: error: expected ‘;’ before ‘*’ token
./include/graphicsengine.h:23: error: ‘Uint16’ does not name a type
./include/graphicsengine.h:27: error: ‘Uint16’ does not name a type
./include/graphicsengine.h:31: error: ISO C++ forbids declaration of ‘SDL_Rect’ with no type
./include/graphicsengine.h:31: error: expected ‘;’ before ‘*’ token
./include/graphicsengine.h:35: error: expected `;' before ‘void’
./include/graphicsengine.h:35: error: ‘SDL_Surface’ has not been declared
./include/graphicsengine.h:42: error: ‘SDL_Surface’ has not been declared
./include/graphicsengine.h:45: error: ‘SDL_Rect’ has not been declared
./include/graphicsengine.h:46: error: ‘SDL_Rect’ has not been declared
./include/graphicsengine.h:46: error: ‘SDL_Rect’ has not been declared
./include/graphicsengine.h:48: error: ‘Sint16’ has not been declared
./include/graphicsengine.h:48: error: ‘Sint16’ has not been declared
./include/graphicsengine.h:49: error: ‘Sint16’ has not been declared
./include/graphicsengine.h:49: error: ‘Sint16’ has not been declared
./include/graphicsengine.h:49: error: ‘Uint16’ has not been declared
./include/graphicsengine.h:49: error: ‘Uint32’ has not been declared
./include/graphicsengine.h:50: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
./include/graphicsengine.h:50: error: expected ‘;’ before ‘*’ token
./include/graphicsengine.h:51: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
./include/graphicsengine.h:51: error: expected ‘;’ before ‘*’ token
./include/graphicsengine.h:52: error: ‘Uint16’ does not name a type
./include/graphicsengine.h:53: error: ‘Uint16’ does not name a type
./include/graphicsengine.h:54: error: ‘Uint16’ does not name a type
./include/graphicsengine.h:55: error: ‘SDL_Rect’ does not name a type
./include/graphicsengine.h:58: error: ‘Uint8’ does not name a type
./include/graphicsengine.h:59: error: ‘Uint8’ does not name a type
./include/graphicsengine.h:62: error: ISO C++ forbids declaration of ‘Uint8’ with no type
./include/graphicsengine.h:62: error: expected ‘;’ before ‘*’ token
./include/graphicsengine.h:64: error: ‘Uint32’ was not declared in this scope
./include/graphicsengine.h:64: error: template argument 1 is invalid
./include/graphicsengine.h:64: error: template argument 2 is invalid
./include/inifile.h:39: error: ‘Uint32’ has not been declared
./include/inifile.h:42: error: ‘Uint32’ has not been declared
./include/inifile.h:43: error: ‘Uint32’ has not been declared
./include/inifile.h:44: error: ‘Uint32’ has not been declared
./include/soundengine.h:20: error: ‘Uint8’ was not declared in this scope
./include/soundengine.h:20: error: template argument 1 is invalid
./include/soundengine.h:20: error: template argument 2 is invalid
./include/soundengine.h:20: error: invalid type in declaration before ‘;’ token
./include/soundengine.h:23: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
./include/soundengine.h:23: error: expected ‘;’ before ‘*’ token
./include/soundengine.h:27: error: ‘Uint32’ does not name a type
./include/soundengine.h:55: error: ‘Uint8’ has not been declared
./include/soundengine.h:75: error: ‘SDL_AudioCVT’ does not name a type
./include/soundengine.h:76: error: ‘SDL_AudioCVT’ does not name a type
./include/../vfs/archive.h:19: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:20: error: ‘Uint32’ has not been declared
./include/../vfs/archive.h:22: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:23: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:24: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:25: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:26: error: ‘readLine’ declared as a ‘virtual’ field
./include/../vfs/archive.h:26: error: expected ‘;’ before ‘(’ token
./include/../vfs/archive.h:31: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:32: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:33: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:34: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:35: error: ‘Uint32’ has not been declared
./include/../vfs/archive.h:36: error: ‘Uint32’ has not been declared
./include/../vfs/archive.h:37: error: ‘Uint32’ has not been declared
./include/../vfs/archive.h:39: error: ‘Uint32’ has not been declared
./include/../vfs/archive.h:39: error: ‘Uint32’ has not been declared
./include/../vfs/archive.h:40: error: ‘Uint32’ has not been declared
./include/../vfs/archive.h:40: error: ‘Sint32’ has not been declared
./include/../vfs/archive.h:42: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:43: error: ‘Uint32’ does not name a type
./include/../vfs/archive.h:44: error: ‘getPath’ declared as a ‘virtual’ field
./include/../vfs/archive.h:44: error: expected ‘;’ before ‘(’ token
./include/vfs.h:17: error: expected `)' before ‘filenum’
./include/vfs.h:27: error: ‘Uint32’ does not name a type
./include/vfs.h:31: error: ‘Uint32’ does not name a type
./include/vfs.h:35: error: ‘Uint32’ does not name a type
./include/vfs.h:39: error: ‘Uint32’ does not name a type
./include/vfs.h:43: error: ‘Uint32’ has not been declared
./include/vfs.h:48: error: ‘Uint32’ does not name a type
./include/vfs.h:52: error: ‘Uint32’ does not name a type
./include/vfs.h:56: error: ‘Uint32’ does not name a type
./include/vfs.h:60: error: ‘Uint32’ does not name a type
./include/vfs.h:86: error: ‘Uint32’ has not been declared
./include/vfs.h:90: error: ‘Sint32’ has not been declared
./include/vfs.h:94: error: ‘Uint32’ does not name a type
./include/vfs.h:98: error: ‘Uint32’ does not name a type
./include/vfs.h:108: error: ‘Uint32’ does not name a type
./include/vfs.h: In destructor ‘VFile::~VFile()’:
./include/vfs.h:23: error: ‘filenum’ was not declared in this scope
./include/vfs.h: In member function ‘char* VFile::getLine(char*, int)’:
./include/vfs.h:45: error: ‘class Archive’ has no member named ‘readLine’
./include/vfs.h:45: error: ‘filenum’ was not declared in this scope
./include/vfs.h: In member function ‘void VFile::writeLine(const char*)’:
./include/vfs.h:66: error: ‘filenum’ was not declared in this scope
./include/vfs.h: In member function ‘int VFile::vfs_printf(const char*, ...)’:
./include/vfs.h:73: error: ‘filenum’ was not declared in this scope
./include/vfs.h: In member function ‘int VFile::vfs_vprintf(const char*, char*)’:
./include/vfs.h:79: error: ‘filenum’ was not declared in this scope
./include/vfs.h: In member function ‘void VFile::flush()’:
./include/vfs.h:83: error: ‘filenum’ was not declared in this scope
./include/vfs.h: In member function ‘void VFile::seekSet(int)’:
./include/vfs.h:88: error: ‘filenum’ was not declared in this scope
./include/vfs.h: In member function ‘void VFile::seekCur(int)’:
./include/vfs.h:92: error: ‘filenum’ was not declared in this scope
./include/vfs.h: In member function ‘const char* VFile::getPath()’:
./include/vfs.h:105: error: ‘class Archive’ has no member named ‘getPath’
./include/vfs.h:105: error: ‘filenum’ was not declared in this scope
./include/vfs.h: At global scope:
./include/vfs.h:123: error: ‘const char* VFS_getFirstExisting’ redeclared as different kind of symbol
./include/vfs.h:122: error: previous declaration of ‘const char* VFS_getFirstExisting(const std::vector<const char*, std::allocator<const char*> >&)’
./include/vfs.h:123: error: ‘Uint32’ was not declared in this scope
./include/vfs.h:123: error: expected primary-expression before ‘...’ token
./include/vqa.h:12: error: ‘Uint8’ does not name a type
./include/vqa.h:13: error: ‘Uint32’ does not name a type
./include/vqa.h:14: error: ‘Uint16’ does not name a type
./include/vqa.h:15: error: ‘Uint16’ does not name a type
./include/vqa.h:16: error: ‘Uint16’ does not name a type
./include/vqa.h:17: error: ‘Uint16’ does not name a type
./include/vqa.h:18: error: ‘Uint16’ does not name a type
./include/vqa.h:19: error: ‘Uint8’ does not name a type
./include/vqa.h:20: error: ‘Uint8’ does not name a type
./include/vqa.h:21: error: ‘Uint8’ does not name a type
./include/vqa.h:22: error: ‘Uint8’ does not name a type
./include/vqa.h:23: error: ‘Uint16’ does not name a type
./include/vqa.h:24: error: ‘Uint16’ does not name a type
./include/vqa.h:25: error: ‘Uint16’ does not name a type
./include/vqa.h:26: error: ‘Uint32’ does not name a type
./include/vqa.h:27: error: ‘Uint16’ does not name a type
./include/vqa.h:28: error: ‘Uint8’ does not name a type
./include/vqa.h:29: error: ‘Uint8’ does not name a type
./include/vqa.h:30: error: ‘Uint8’ does not name a type
./include/vqa.h:49: error: ‘Uint32’ does not name a type
./include/vqa.h:50: error: ‘SDL_Surface’ has not been declared
./include/vqa.h:52: error: ‘Uint8’ has not been declared
./include/vqa.h:53: error: ‘Uint8’ has not been declared
./include/vqa.h:54: error: ‘SDL_Color’ has not been declared
./include/vqa.h:61: error: ‘Uint32’ does not name a type
./include/vqa.h:62: error: ‘Uint16’ does not name a type
./include/vqa.h:63: error: ISO C++ forbids declaration of ‘Uint8’ with no type
./include/vqa.h:63: error: expected ‘;’ before ‘*’ token
./include/vqa.h:64: error: ISO C++ forbids declaration of ‘Uint8’ with no type
./include/vqa.h:64: error: expected ‘;’ before ‘*’ token
./include/vqa.h:65: error: ISO C++ forbids declaration of ‘Uint8’ with no type
./include/vqa.h:65: error: expected ‘;’ before ‘*’ token
./include/vqa.h:66: error: ISO C++ forbids declaration of ‘Uint32’ with no type
./include/vqa.h:66: error: expected ‘;’ before ‘*’ token
./include/vqa.h:67: error: ‘Uint8’ does not name a type
./include/vqa.h:68: error: ‘Uint32’ does not name a type
./include/vqa.h:70: error: ‘Sint32’ does not name a type
./include/vqa.h:71: error: ‘Sint32’ does not name a type
./include/vqa.h:82: error: ‘Uint32’ does not name a type
./include/vqa.h:85: error: ‘Uint32’ does not name a type
./include/vqa.h:86: error: ‘Uint32’ does not name a type
./include/vqa.h:87: error: ‘Uint32’ does not name a type
./include/vqa.h:88: error: ‘Uint32’ does not name a type
./include/vqa.h:89: error: ‘Uint32’ does not name a type
./include/vqa.h:90: error: ‘Uint32’ does not name a type
./include/vqa.h:91: error: ‘Uint32’ does not name a type
./include/vqa.h:92: error: ‘Uint32’ does not name a type
./include/wsa.h:14: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
./include/wsa.h:14: error: expected ‘;’ before ‘*’ token
./include/wsa.h:15: error: ISO C++ forbids declaration of ‘Uint8’ with no type
./include/wsa.h:15: error: expected ‘;’ before ‘*’ token
./include/wsa.h:16: error: ISO C++ forbids declaration of ‘Uint8’ with no type
./include/wsa.h:16: error: expected ‘;’ before ‘*’ token
./include/wsa.h:17: error: ‘SDL_Color’ does not name a type
./include/wsa.h:18: error: ‘Uint8’ does not name a type
./include/wsa.h:21: error: ‘Uint16’ does not name a type
./include/wsa.h:22: error: ‘Uint16’ does not name a type
./include/wsa.h:23: error: ‘Uint16’ does not name a type
./include/wsa.h:24: error: ‘Uint16’ does not name a type
./include/wsa.h:25: error: ‘Uint16’ does not name a type
./include/wsa.h:26: error: ‘Uint32’ does not name a type
./include/wsa.h:27: error: ISO C++ forbids declaration of ‘Uint32’ with no type
./include/wsa.h:27: error: expected ‘;’ before ‘*’ token
freecnc.cpp: In function ‘int main(int, char**)’:
freecnc.cpp:86: error: ‘SDL_INIT_VIDEO’ was not declared in this scope
freecnc.cpp:86: error: ‘SDL_INIT_AUDIO’ was not declared in this scope
freecnc.cpp:86: error: ‘SDL_INIT_TIMER’ was not declared in this scope
freecnc.cpp:86: error: ‘SDL_Init’ was not declared in this scope
freecnc.cpp:87: error: ‘SDL_GetError’ was not declared in this scope
freecnc.cpp:97: error: ‘SDL_ShowCursor’ was not declared in this scope
freecnc.cpp:119: error: ‘Uint8’ was not declared in this scope
freecnc.cpp:119: error: expected `;' before ‘ret’
freecnc.cpp:124: error: ‘ret’ was not declared in this scope
freecnc.cpp:126: error: ‘ret’ was not declared in this scope
freecnc.cpp:130: error: ‘const struct ConfigType’ has no member named ‘intro’
freecnc.cpp: In function ‘void cleanup()’:
freecnc.cpp:201: error: ‘SDL_Quit’ was not declared in this scope
make[1]: *** [freecnc.o] Error 1
make[1]: Leaving directory `/home/cjay/freecnc++/src'
make: *** [default] Error 2

```

---

### Post by djnet on 2008-02-01
I dont have that problem anymore...different set of problems, cuz i did that and it worked...now it gives me the new stuff

---

