---
title: "Installation teTeX 3: problems from terminal.c"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by igor1102828 on 2007-01-04
Hello, everybody!

I am absolutely new in LINUX, have installed  Ubuntu 6.06 and now trying to install teTeX. There is a problem that I don't know how to handle. I'd greatly appreciate any help!

 The file world.log gives the following:
===========================
gcc  -g -O2   -o ginfo  dir.o display.o dribble.o echo-area.o filesys.o footnotes.o gc.o indices.o info-utils.o info.o infodoc.o infomap.o m-x.o man.o nodemenu.o nodes.o search.o session.o signals.o terminal.o tilde.o variables.o window.o doc.o ../lib/libtxi.a

terminal.o: In function `terminal_goto_xy':/usr/local/teTeX/tetex-src-3.0/utils/texinfo /info/terminal.c:236: undefined reference to `tgoto'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:236: undefined reference to `tputs'
terminal.o: In function `terminal_clear_to_eol':/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:273: undefined reference to `tputs'
terminal.o: In function `terminal_clear_screen':/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:285: undefined reference to `tputs'
terminal.o: In function `terminal_up_line':/usr/local/teTeX/tetex-src-3.0/utils/texinfo /info/terminal.c:297: undefined reference to `tputs'
terminal.o: In function `terminal_down_line':/usr/local/teTeX/tetex-src-3.0/utils/texin fo/info/terminal.c:309: undefined reference to `tputs'
terminal.o:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:321: more undef ined references to `tputs' follow
terminal.o: In function `terminal_delete_lines':/usr/local/teTeX/tetex-src-3.0/utils/te xinfo/info/terminal.c:366: undefined reference to `tgoto'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:366: undefined reference to `tputs'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:370: undefined reference to `tputs'
terminal.o: In function `terminal_insert_lines':/usr/local/teTeX/tetex-src-3.0/utils/te xinfo/info/terminal.c:390: undefined reference to `tgoto'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:390: undefined reference to `tputs'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:394: undefined reference to `tputs'
terminal.o: In function `terminal_begin_using_terminal':/usr/local/teTeX/tetex-src-3.0/ utils/texinfo/info/terminal.c:136: undefined reference to `tputs'
terminal.o: In function `terminal_prep_terminal':/usr/local/teTeX/tetex-src-3.0/utils/t exinfo/info/terminal.c:145: undefined reference to `tputs'
terminal.o: In function `terminal_end_using_terminal':/usr/local/teTeX/tetex-src-3.0/ut ils/texinfo/info/terminal.c:167: undefined reference to `tputs'
terminal.o:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:176: more undef ined references to `tputs' follow
terminal.o: In function `terminal_get_screen_size':/usr/local/teTeX/tetex-src-3.0/utils /texinfo/info/terminal.c:494: undefined reference to `tgetnum'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:482: undefined reference to `tgetnum'
terminal.o: In function `terminal_initialize_terminal':/usr/local/teTeX/tetex-src-3.0/u tils/texinfo/info/terminal.c:540: undefined reference to `tgetent'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:554: undefined reference to `tgetstr'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:580: undefined reference to `tgetstr'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:581: undefined reference to `tgetstr'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:582: undefined reference to `tgetstr'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:583: undefined reference to `tgetstr'
terminal.o:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:586: more undef ined references to `tgetstr' follow
terminal.o: In function `terminal_initialize_terminal':/usr/local/teTeX/tetex-src-3.0/u tils/texinfo/info/terminal.c:618: undefined reference to `tgetflag'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:629: undefined reference to `tgetstr'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:630: undefined reference to `tgetstr'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:631: undefined reference to `tgetstr'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:632: undefined reference to `tgetstr'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:634: undefined reference to `tgetstr'
terminal.o:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:635: more undef ined references to `tgetstr' follow
terminal.o: In function `terminal_initialize_terminal':/usr/local/teTeX/tetex-src-3.0/u tils/texinfo/info/terminal.c:618: undefined reference to `tgetflag'
:/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c:621: undefined reference to `tgetstr'
collect2: ld returned 1 exit status
make[4]: *** [ginfo] Error 1
make[4]: Leaving directory `/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/local/teTeX/tetex-src-3.0/utils/texinfo/info'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/teTeX/tetex-src-3.0/utils/texinfo'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/local/teTeX/tetex-src-3.0/utils/texinfo'
make: *** [all] Error 1

===========================
The commands

    sudo apt-get install build-essential
    sudo apt-get install g++ build-essential

are performed, so, the C/C++ compilers should be installed.

The relevant part of the file /usr/local/teTeX/tetex-src-3.0/utils/texinfo/info/terminal.c

( the lines where the terminal.c cannot find the functions) is given below
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

/* Move the cursor to the terminal location of X and Y. */
void
terminal_goto_xy (int x, int y)
{
  if (terminal_goto_xy_hook)
    (*terminal_goto_xy_hook) (x, y);
  else
    {
      if (term_goto)
236 -->     tputs (tgoto (term_goto, x, y), 1, output_character_function);
    }
}

=============================
273 -->    send_to_terminal (term_clreol);
=============================
285 -->    send_to_terminal (term_clrpag);
=============================
297  -->   send_to_terminal (term_up);

+++++++++++++++++++++++++++++++++++++

Sincerely, Igor

---

### Post by tzulberti on 2007-01-04
I can see that you aren't using apt... One of the great things about Ubuntu is the apt command...
You should type the following:
sudo apt-get install tetex

You MUST read about apt... It is a great command, which takes care of installing every program.

---

