---
title: "problems installing pidgin latex plugin"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Jawsman on 2007-12-14
I tried compiling this package with the 'make' command, but this quite agressive error ocurred:

```
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gcc  -fPIC -c LaTeX.c -o LaTeX.o   -DHAVE_CONFIG_H
En el fichero incluído de LaTeX.c:32:
LaTeX.h:45:36: error: libpurple/conversation.h: No existe el fichero ó directorio
LaTeX.h:47:29: error: libpurple/debug.h: No existe el fichero ó directorio
LaTeX.h:48:31: error: libpurple/signals.h: No existe el fichero ó directorio
LaTeX.h:49:32: error: libpurple/imgstore.h: No existe el fichero ó directorio
LaTeX.h:50:28: error: libpurple/util.h: No existe el fichero ó directorio
LaTeX.h:51:30: error: libpurple/notify.h: No existe el fichero ó directorio
LaTeX.h:52:30: error: libpurple/server.h: No existe el fichero ó directorio
LaTeX.h:53:27: error: libpurple/log.h: No existe el fichero ó directorio
LaTeX.h:54:31: error: libpurple/version.h: No existe el fichero ó directorio
In file included from LaTeX.c:32:
LaTeX.h:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_blacklisted’
LaTeX.h:101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘latex_to_image’
LaTeX.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘analyse’
LaTeX.h:119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pidgin_latex_write’
LaTeX.h:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘message_send’
LaTeX.c:34:19: error: stdio.h: No existe el fichero ó directorio
LaTeX.c:35:20: error: string.h: No existe el fichero ó directorio
LaTeX.c:36:20: error: unistd.h: No existe el fichero ó directorio
LaTeX.c:47: error: expected ‘)’ before ‘*’ token
LaTeX.c: En la función ‘getdirname’:
LaTeX.c:99: error: ‘NULL’ no se declaró aquí (primer uso en esta función)
LaTeX.c:99: error: (Cada identificador no declarado solamente se reporta una vez
LaTeX.c:99: error: ara cada funcion en la que aparece.)
LaTeX.c:101: aviso: declaración implícita incompatible de la función interna ‘strrchr’
LaTeX.c:101: error: ‘G_DIR_SEPARATOR’ no se declaró aquí (primer uso en esta función)
LaTeX.c:107: aviso: la devolución crea un puntero desde un entero sin una conversión
LaTeX.c:111: aviso: declaración implícita incompatible de la función interna ‘malloc’
LaTeX.c:114: aviso: declaración implícita incompatible de la función interna ‘memcpy’
LaTeX.c: En la función ‘getfilename’:
LaTeX.c:122: error: ‘NULL’ no se declaró aquí (primer uso en esta función)
LaTeX.c:124: aviso: declaración implícita incompatible de la función interna ‘strrchr’
LaTeX.c:124: error: ‘G_DIR_SEPARATOR’ no se declaró aquí (primer uso en esta función)
LaTeX.c:127: aviso: declaración implícita incompatible de la función interna ‘malloc’
LaTeX.c:127: aviso: declaración implícita incompatible de la función interna ‘strlen’
LaTeX.c:128: aviso: declaración implícita incompatible de la función interna ‘strcpy’
LaTeX.c:133: aviso: declaración implícita incompatible de la función interna ‘malloc’
LaTeX.c:133: aviso: declaración implícita incompatible de la función interna ‘strlen’
LaTeX.c:136: aviso: declaración implícita incompatible de la función interna ‘memcpy’
LaTeX.c: En la función ‘searchPATH’:
LaTeX.c:144: error: ‘NULL’ no se declaró aquí (primer uso en esta función)
LaTeX.c:161: aviso: declaración implícita incompatible de la función interna ‘malloc’
LaTeX.c:161: aviso: declaración implícita incompatible de la función interna ‘strlen’
LaTeX.c:163: aviso: declaración implícita incompatible de la función interna ‘strcpy’
LaTeX.c: En la función ‘execute’:
LaTeX.c:231: aviso: declaración implícita incompatible de la función interna ‘strlen’
LaTeX.c:232: error: ‘NULL’ no se declaró aquí (primer uso en esta función)
LaTeX.c:237: aviso: declaración implícita incompatible de la función interna ‘malloc’
LaTeX.c:241: aviso: declaración implícita incompatible de la función interna ‘strcpy’
LaTeX.c:242: aviso: declaración implícita incompatible de la función interna ‘strcat’
LaTeX.c: En el nivel principal:
LaTeX.c:291: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_blacklisted’
LaTeX.c:306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘latex_to_image’
LaTeX.c:380: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘analyse’
LaTeX.c:522: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pidgin_latex_write’
LaTeX.c:555: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘message_send’
LaTeX.c:589: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_load’
LaTeX.c:604: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_unload’
LaTeX.c:615: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘info’
LaTeX.c:651: error: expected ‘)’ before ‘*’ token
LaTeX.c: En la función ‘PURPLE_INIT_PLUGIN’:
LaTeX.c:655: error: expected ‘{’ at end of input
make: *** [LaTeX.o] Error 1

```

I do have pidgin and latex installed
any idea of what is happening?

I also have imagemagick installed

---

### Post by llamakc on 2007-12-14
```

sudo apt-get install libpurple-dev

```

---

### Post by Jawsman on 2007-12-17
thanks for the help

heres how to solve this:

[http://ubuntuforums.org/showthread.php?t=597966&highlight=pidgin+latex]("http://ubuntuforums.org/showthread.php?t=597966&highlight=pidgin+latex")

---

