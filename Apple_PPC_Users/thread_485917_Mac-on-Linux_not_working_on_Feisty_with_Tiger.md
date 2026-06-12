---
title: "Mac-on-Linux not working on Feisty with Tiger"
date: 2007-06-27
forum: Apple PPC Users
---

### Post by bipco on 2007-06-27
Hello

Mac-on-Linux is not working for me with Tiger (gets as far as the splash screen) - I've seen the stuff about building a new kernel and then building mol from the latest source. I tried building mol (without building a kernel) and got  some errors from make. I've got the kernel headers installed. Building the kernel looks complicated - do I have to do that to get mol to compile?

Thanks

Warren

---

### Post by aantn on 2007-06-27
Do you have a G5?

---

### Post by bipco on 2007-06-27
Not a G5 - a rather ancient G3 Lombard Powerbook.

I just tried with the source from sourceforge (previously tried the one pointed to on the Wiki page). I did notice I was missing a package but after installling that and trying again this is what I got with make:

+ Entering lxdialog
    Compiling    checklist.o         
In file included from checklist.c:24:
dialog.h:31:20: error: curses.h: No such file or directory
In file included from checklist.c:24:
dialog.h:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘use_colors’
dialog.h:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘use_shadow’
dialog.h:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘attributes’
dialog.h:143: error: expected ‘)’ before ‘*’ token
dialog.h:146: error: expected ‘)’ before ‘*’ token
dialog.h:147: error: expected ‘)’ before ‘*’ token
dialog.h:148: error: expected ‘)’ before ‘*’ token
dialog.h:149: error: expected ‘)’ before ‘*’ token
dialog.h:151: error: expected ‘)’ before ‘*’ token
checklist.c:31: error: expected ‘)’ before ‘*’ token
checklist.c:59: error: expected ‘)’ before ‘*’ token
checklist.c:95: error: expected ‘)’ before ‘*’ token
checklist.c: In function ‘dialog_checklist’:
checklist.c:117: error: ‘WINDOW’ undeclared (first use in this function)
checklist.c:117: error: (Each undeclared identifier is reported only once
checklist.c:117: error: for each function it appears in.)
checklist.c:117: error: ‘dialog’ undeclared (first use in this function)
checklist.c:117: error: ‘list’ undeclared (first use in this function)
checklist.c:117: warning: left-hand operand of comma expression has no effect
checklist.c:121: warning: implicit declaration of function ‘endwin’
checklist.c:122: warning: implicit declaration of function ‘fprintf’
checklist.c:122: warning: incompatible implicit declaration of built-in function ‘fprintf’
checklist.c:122: error: ‘stderr’ undeclared (first use in this function)
checklist.c:140: error: ‘COLS’ undeclared (first use in this function)
checklist.c:141: error: ‘LINES’ undeclared (first use in this function)
checklist.c:143: warning: implicit declaration of function ‘draw_shadow’
checklist.c:143: error: ‘stdscr’ undeclared (first use in this function)
checklist.c:145: warning: implicit declaration of function ‘newwin’
checklist.c:146: warning: implicit declaration of function ‘keypad’
checklist.c:146: error: ‘TRUE’ undeclared (first use in this function)
checklist.c:148: warning: implicit declaration of function ‘draw_box’
checklist.c:148: error: ‘attributes’ undeclared (first use in this function)
checklist.c:149: warning: implicit declaration of function ‘wattrset’
checklist.c:150: warning: implicit declaration of function ‘mvwaddch’
checklist.c:152: warning: implicit declaration of function ‘waddch’
checklist.c:156: warning: implicit declaration of function ‘print_title’
checklist.c:159: warning: implicit declaration of function ‘print_autowrap’
checklist.c:166: warning: implicit declaration of function ‘subwin’
checklist.c:191: warning: implicit declaration of function ‘print_item’
checklist.c:197: warning: implicit declaration of function ‘print_arrows’
checklist.c:200: warning: implicit declaration of function ‘print_buttons’
checklist.c:202: warning: implicit declaration of function ‘wnoutrefresh’
checklist.c:204: warning: implicit declaration of function ‘doupdate’
checklist.c:207: warning: implicit declaration of function ‘wgetch’
checklist.c:214: error: ‘KEY_UP’ undeclared (first use in this function)
checklist.c:214: error: ‘KEY_DOWN’ undeclared (first use in this function)
checklist.c:224: error: ‘FALSE’ undeclared (first use in this function)
checklist.c:225: warning: implicit declaration of function ‘scrollok’
checklist.c:226: warning: implicit declaration of function ‘wscrl’
checklist.c:235: warning: implicit declaration of function ‘wrefresh’
checklist.c:285: warning: incompatible implicit declaration of built-in function ‘fprintf’
checklist.c:286: warning: implicit declaration of function ‘delwin’
checklist.c:290: error: ‘KEY_LEFT’ undeclared (first use in this function)
checklist.c:291: error: ‘KEY_RIGHT’ undeclared (first use in this function)
make[2]: *** [../../obj-ppc/build/config/lxdialog/checklist.o] Error 1
make[1]: *** [sub-lxdialog-all] Error 2
make: *** [do-bootstrap] Error 2

Looks like I'm missing curses.h (at least) - so where should that come from - maybe I need some other packages?

Warren

---

### Post by Sultanqasim on 2007-10-23
You need to install ncurses-devel

Run the following command and then compile and you'ill be fine:

sudo apt-get install ncurses-devel

---

### Post by Sultanqasim on 2007-10-23
oops ignore my previous post, the correct command is:

apt-get install ncurses-dev


I was using suse and it has slightly different package names

---

### Post by frog_pilot on 2007-10-23
I did it as described in this [discussion]("http://ubuntuforums.org/showthread.php?t=565388") and my MOL is working fine with Tiger on G4 Dual.

---

### Post by ombra on 2008-05-15
Thank you for the hint, it also worked fo me

---

### Post by ombra on 2008-05-20
lateron i got a new error:

```
+ Entering Linux
In Datei, eingefügt von /home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/kernel_vars.h:22,
                 von /home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.c:28:
/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/mac_registers.h:114:1: Warnung: »BIT« redefiniert
In Datei, eingefügt von include/linux/kernel.h:15,
                 von /home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/archinclude.h:44,
                 von /home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.c:17:
include/linux/bitops.h:6:1: Warnung: dies ist die Stelle der vorherigen Definition
/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.c: In Funktion »find_physical_rom«:
/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.c:75: Fehler: Implizite Deklaration der Funktion »find_devices«
/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.c:75: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.c:75: Fehler: Implizite Deklaration der Funktion »find_type_devices«
/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.c:75: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.c:78: Fehler: Implizite Deklaration der Funktion »get_property«
make[5]: *** [/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod/_dev.o] Fehler 1
make[4]: *** [_module_/home/ombra/Desktop/mol-0.9.72_pre2/obj-ppc/build/src/kmod] Fehler 2
nm: '../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file
nm: '../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file
checker.pl failed
rm: Entfernen von „../../../obj-ppc/build/src/kmod/Linux/..//mol.ko“ nicht möglich: No such file or directory
make[3]: *** [all-local] Fehler 1
make[2]: *** [sub-Linux-all] Fehler 2
make[1]: *** [sub-kmod-all] Fehler 2
make: *** [sub-src-all] Fehler 2 
```

What does this mean and what can I do?

Thx in advance

---

