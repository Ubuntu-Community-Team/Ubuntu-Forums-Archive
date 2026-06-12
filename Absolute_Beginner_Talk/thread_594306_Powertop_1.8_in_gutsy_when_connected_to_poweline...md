---
title: "Powertop 1.8 in gutsy when connected to poweline... Senseless?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-27
Do it have some sense to use Powertop on a intel laptop when connected to the powerline in order to reduce the global power consumption?   Does Powertop only works when in Battery mode?

---

### Post by Delvien on 2007-10-28
> **Kosimo said:**
> Do it have some sense to use Powertop on a intel laptop when connected to the powerline in order to reduce the global power consumption?   Does Powertop only works when in Battery mode?

It will only pick up ACPI when running on the battery. Mine doesnt allow me to turn off stuff unless ACPI is active and working from the battery. So in answer to your question, no. But the amount that is drawn from the wall is so minimal compaired to a desktop PC you really wont be saving that much power if you WERE able to reduce the power consumption. 

Mine usually goes from 29 watts to 18ish watts, 11 watts is nothing compaired to what a desktop sucks up.

---

### Post by Kosimo on 2007-10-30
In my case works:
I can disable the AC97 sound driver, and reduce the USB power usage and activate the wireless power saving mode. It doesn't show the power consumption but I guess it works even in powerline.

By the way, powertop has reached the version 1.9 already. Witch is not included in repositories.
Does anybody knows how to install it? I tried downloading the source code but after make I get this error:

> /powertop-1.9$ make
cc -Os -g -Wall  -W -Wshadow   -c -o powertop.o powertop.c
cc -Os -g -Wall  -W -Wshadow   -c -o config.o config.c
cc -Os -g -Wall  -W -Wshadow   -c -o process.o process.c
cc -Os -g -Wall  -W -Wshadow   -c -o misctips.o misctips.c
cc -Os -g -Wall  -W -Wshadow   -c -o bluetooth.o bluetooth.c
cc -Os -g -Wall  -W -Wshadow   -c -o display.o display.c
display.c:32:21: error: ncurses.h: No such file or directory
display.c:38: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
display.c:39: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
display.c:40: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
display.c:41: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
display.c:42: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
display.c:43: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
display.c:44: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
display.c: In function &#8216;cleanup_curses&#8217;:
display.c:51: warning: implicit declaration of function &#8216;endwin&#8217;
display.c: In function &#8216;zap_windows&#8217;:
display.c:56: error: &#8216;title_bar_window&#8217; undeclared (first use in this function)
display.c:56: error: (Each undeclared identifier is reported only once
display.c:56: error: for each function it appears in.)
display.c:57: warning: implicit declaration of function &#8216;delwin&#8217;
display.c:60: error: &#8216;cstate_window&#8217; undeclared (first use in this function)
display.c:64: error: &#8216;wakeup_window&#8217; undeclared (first use in this function)
display.c:68: error: &#8216;acpi_power_window&#8217; undeclared (first use in this function)
display.c:72: error: &#8216;timerstat_window&#8217; undeclared (first use in this function)
display.c:76: error: &#8216;suggestion_window&#8217; undeclared (first use in this function)
display.c:80: error: &#8216;status_bar_window&#8217; undeclared (first use in this function)
display.c: In function &#8216;setup_windows&#8217;:
display.c:94: warning: implicit declaration of function &#8216;getmaxyx&#8217;
display.c:94: error: &#8216;stdscr&#8217; undeclared (first use in this function)
display.c:98: error: &#8216;title_bar_window&#8217; undeclared (first use in this function)
display.c:98: warning: implicit declaration of function &#8216;subwin&#8217;
display.c:99: error: &#8216;cstate_window&#8217; undeclared (first use in this function)
display.c:100: error: &#8216;wakeup_window&#8217; undeclared (first use in this function)
display.c:101: error: &#8216;acpi_power_window&#8217; undeclared (first use in this function)
display.c:102: error: &#8216;timerstat_window&#8217; undeclared (first use in this function)
display.c:105: error: &#8216;suggestion_window&#8217; undeclared (first use in this function)
display.c:106: error: &#8216;status_bar_window&#8217; undeclared (first use in this function)
display.c:111: warning: implicit declaration of function &#8216;werase&#8217;
display.c:112: warning: implicit declaration of function &#8216;refresh&#8217;
display.c: In function &#8216;initialize_curses&#8217;:
display.c:117: warning: implicit declaration of function &#8216;initscr&#8217;
display.c:118: warning: implicit declaration of function &#8216;start_color&#8217;
display.c:119: warning: implicit declaration of function &#8216;keypad&#8217;
display.c:119: error: &#8216;stdscr&#8217; undeclared (first use in this function)
display.c:119: error: &#8216;TRUE&#8217; undeclared (first use in this function)
display.c:120: warning: implicit declaration of function &#8216;nonl&#8217;
display.c:121: warning: implicit declaration of function &#8216;cbreak&#8217;
display.c:122: warning: implicit declaration of function &#8216;noecho&#8217;
display.c:123: warning: implicit declaration of function &#8216;curs_set&#8217;
display.c:124: warning: implicit declaration of function &#8216;use_default_colors&#8217;
display.c:126: warning: implicit declaration of function &#8216;init_pair&#8217;
display.c:126: error: &#8216;COLOR_WHITE&#8217; undeclared (first use in this function)
display.c:126: error: &#8216;COLOR_BLACK&#8217; undeclared (first use in this function)
display.c:128: error: &#8216;COLOR_RED&#8217; undeclared (first use in this function)
display.c:130: error: &#8216;COLOR_YELLOW&#8217; undeclared (first use in this function)
display.c:131: error: &#8216;COLOR_GREEN&#8217; undeclared (first use in this function)
display.c:132: error: &#8216;COLOR_BLUE&#8217; undeclared (first use in this function)
display.c: In function &#8216;show_title_bar&#8217;:
display.c:142: warning: implicit declaration of function &#8216;wattrset&#8217;
display.c:142: error: &#8216;title_bar_window&#8217; undeclared (first use in this function)
display.c:142: warning: implicit declaration of function &#8216;COLOR_PAIR&#8217;
display.c:143: warning: implicit declaration of function &#8216;wbkgd&#8217;
display.c:146: warning: implicit declaration of function &#8216;mvwprintw&#8217;
display.c:148: warning: implicit declaration of function &#8216;wrefresh&#8217;
display.c:150: error: &#8216;status_bar_window&#8217; undeclared (first use in this function)
display.c:156: warning: implicit declaration of function &#8216;wattron&#8217;
display.c:156: error: &#8216;A_REVERSE&#8217; undeclared (first use in this function)
display.c:158: warning: implicit declaration of function &#8216;wattroff&#8217;
display.c: In function &#8216;show_cstates&#8217;:
display.c:167: error: &#8216;cstate_window&#8217; undeclared (first use in this function)
display.c:171: error: &#8216;A_BOLD&#8217; undeclared (first use in this function)
display.c: In function &#8216;show_acpi_power_line&#8217;:
display.c:195: error: &#8216;acpi_power_window&#8217; undeclared (first use in this function)
display.c: In function &#8216;show_wakeups&#8217;:
display.c:213: error: &#8216;wakeup_window&#8217; undeclared (first use in this function)
display.c:228: error: &#8216;A_BOLD&#8217; undeclared (first use in this function)
display.c: In function &#8216;show_timerstats&#8217;:
display.c:236: error: &#8216;timerstat_window&#8217; undeclared (first use in this function)
display.c:244: error: &#8216;A_BOLD&#8217; undeclared (first use in this function)
display.c: In function &#8216;show_suggestion&#8217;:
display.c:267: error: &#8216;suggestion_window&#8217; undeclared (first use in this function)
make: *** [display.o] Error 1


---

