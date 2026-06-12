---
title: "sdl and script error help"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2007-08-11
hi, im trying to install a game, but when compiling i keep getting this error when i am running configure:

```

checking for sdl-config... no
checking for SDL - version >= 1.2.4... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.4 not found!
```

what do i need to do?

---

### Post by irishgoth8822 on 2007-08-11
i also just tried installing some libsdl packages that i thought might help, as well as autoconf to try and use the autogen.sh file, but now im getting this from the configure command:

```
./configure: line 5193: AM_BINRELOC: command not found
./configure: line 5195: AM_ICONV: command not found
./configure: line 5200: syntax error near unexpected token `$SDL_VERSION,'
./configure: line 5200: `AM_PATH_SDL($SDL_VERSION,'
```

and a 'command not found' when i run the autogen.sh script in terminal.

---

