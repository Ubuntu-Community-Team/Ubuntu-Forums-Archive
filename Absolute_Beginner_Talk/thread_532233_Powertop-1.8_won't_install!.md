---
title: "Powertop-1.8 won't install!"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-08-22
I try to install Powertop-1.8 (and, yes, I do have the new kernel), but it won't install. These are the errors I get after 'make':
```
lcc -Os -g -Wall  -W -Wshadow   -c -o display.o display.c
display.c:32:21: error: ncurses.h: No such file or directory
display.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
display.c: In function ‘cleanup_curses’:
display.c:51: warning: implicit declaration of function ‘endwin’
display.c: In function ‘zap_windows’:
display.c:56: error: ‘title_bar_window’ undeclared (first use in this function)
display.c:56: error: (Each undeclared identifier is reported only once
display.c:56: error: for each function it appears in.)
display.c:57: warning: implicit declaration of function ‘delwin’
display.c:60: error: ‘cstate_window’ undeclared (first use in this function)
display.c:64: error: ‘wakeup_window’ undeclared (first use in this function)
display.c:68: error: ‘acpi_power_window’ undeclared (first use in this function)
display.c:72: error: ‘timerstat_window’ undeclared (first use in this function)
display.c:76: error: ‘suggestion_window’ undeclared (first use in this function)
display.c:80: error: ‘status_bar_window’ undeclared (first use in this function)
display.c: In function ‘setup_windows’:
display.c:94: warning: implicit declaration of function ‘getmaxyx’
display.c:94: error: ‘stdscr’ undeclared (first use in this function)
display.c:98: error: ‘title_bar_window’ undeclared (first use in this function)
display.c:98: warning: implicit declaration of function ‘subwin’
display.c:99: error: ‘cstate_window’ undeclared (first use in this function)
display.c:100: error: ‘wakeup_window’ undeclared (first use in this function)
display.c:101: error: ‘acpi_power_window’ undeclared (first use in this function)
display.c:102: error: ‘timerstat_window’ undeclared (first use in this function)
display.c:105: error: ‘suggestion_window’ undeclared (first use in this function)
display.c:106: error: ‘status_bar_window’ undeclared (first use in this function)
display.c:111: warning: implicit declaration of function ‘werase’
display.c:112: warning: implicit declaration of function ‘refresh’
display.c: In function ‘initialize_curses’:
display.c:117: warning: implicit declaration of function ‘initscr’
display.c:118: warning: implicit declaration of function ‘start_color’
display.c:119: warning: implicit declaration of function ‘keypad’
display.c:119: error: ‘stdscr’ undeclared (first use in this function)
display.c:119: error: ‘TRUE’ undeclared (first use in this function)
display.c:120: warning: implicit declaration of function ‘nonl’
display.c:121: warning: implicit declaration of function ‘cbreak’
display.c:122: warning: implicit declaration of function ‘noecho’
display.c:123: warning: implicit declaration of function ‘curs_set’
display.c:124: warning: implicit declaration of function ‘use_default_colors’
display.c:126: warning: implicit declaration of function ‘init_pair’
display.c:126: error: ‘COLOR_WHITE’ undeclared (first use in this function)
display.c:126: error: ‘COLOR_BLACK’ undeclared (first use in this function)
display.c:128: error: ‘COLOR_RED’ undeclared (first use in this function)
display.c:130: error: ‘COLOR_YELLOW’ undeclared (first use in this function)
display.c:131: error: ‘COLOR_GREEN’ undeclared (first use in this function)
display.c:132: error: ‘COLOR_BLUE’ undeclared (first use in this function)
display.c: In function ‘show_title_bar’:
display.c:142: warning: implicit declaration of function ‘wattrset’
display.c:142: error: ‘title_bar_window’ undeclared (first use in this function)
display.c:142: warning: implicit declaration of function ‘COLOR_PAIR’
display.c:143: warning: implicit declaration of function ‘wbkgd’
display.c:146: warning: implicit declaration of function ‘mvwprintw’
display.c:148: warning: implicit declaration of function ‘wrefresh’
display.c:150: error: ‘status_bar_window’ undeclared (first use in this function)
display.c:156: warning: implicit declaration of function ‘wattron’
display.c:156: error: ‘A_REVERSE’ undeclared (first use in this function)
display.c:158: warning: implicit declaration of function ‘wattroff’
display.c: In function ‘show_cstates’:
display.c:167: error: ‘cstate_window’ undeclared (first use in this function)
display.c:171: error: ‘A_BOLD’ undeclared (first use in this function)
display.c: In function ‘show_acpi_power_line’:
display.c:195: error: ‘acpi_power_window’ undeclared (first use in this function)
display.c: In function ‘show_wakeups’:
display.c:213: error: ‘wakeup_window’ undeclared (first use in this function)
display.c:228: error: ‘A_BOLD’ undeclared (first use in this function)
display.c: In function ‘show_timerstats’:
display.c:236: error: ‘timerstat_window’ undeclared (first use in this function)
display.c:244: error: ‘A_BOLD’ undeclared (first use in this function)
display.c: In function ‘show_suggestion’:
display.c:267: error: ‘suggestion_window’ undeclared (first use in this function)
make: *** [display.o] Error 1
```

---

### Post by splintercellguy on 2007-08-22
You need ncurses.

sudo apt-get install libncurses5-dev

---

### Post by st33med on 2007-08-22
Thanks! I knew I was missing a package, but I didn't know what.

---

### Post by shof2k on 2007-08-26
You also need kernel 2.6.21.  Feisty comes along with 2.6.20.

---

