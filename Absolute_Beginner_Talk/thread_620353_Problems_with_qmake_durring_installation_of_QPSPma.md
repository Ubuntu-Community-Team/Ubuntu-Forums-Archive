---
title: "Problems with qmake durring installation of QPSPmanager"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-11-22
I'm following this guide: [https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)

Yet when trying to do qmake I get the following output:

```
 
Usage: qmake [mode] [options] [files]

QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

Mode:
  -project       Put qmake into project file generation mode
                 In this mode qmake interprets files as files to
                 be built,
                 defaults to *.c; *.ui; *.y; *.l; *.ts; *.qrc; *.h; *.hpp; *.hh; *.hxx; *.H; *.cpp; *.cc; *.cxx; *.C
  -makefile      Put qmake into makefile generation mode (default)
                 In this mode qmake interprets files as project files to
                 be processed, if skipped qmake will try to find a project
                 file in your current working directory

Warnings Options:
  -Wnone         Turn off all warnings
  -Wall          Turn on all warnings
  -Wparser       Turn on parser warnings
  -Wlogic        Turn on logic warnings

Options:
   * You can place any variable assignment in options and it will be     *
   * processed as if it was in [files]. These assignments will be parsed *
   * before [files].                                                     *
  -o file        Write output to file
  -unix          Run in unix mode
  -win32         Run in win32 mode
  -macx          Run in Mac OS X mode
  -d             Increase debug level
  -t templ       Overrides TEMPLATE as templ
  -tp prefix     Overrides TEMPLATE so that prefix is prefixed into the value
  -help          This help
  -v             Version information
  -after         All variable assignments after this will be
                 parsed after [files]
  -norecursive   Don't do a recursive search
  -recursive     Do a recursive search
  -cache file    Use file as cache           [makefile mode only]
  -spec spec     Use spec as QMAKESPEC       [makefile mode only]
  -nocache       Don't use a cache file      [makefile mode only]
  -nodepend      Don't generate dependencies [makefile mode only]
  -nomoc         Don't generate moc targets  [makefile mode only]
  -nopwd         Don't look for files in pwd [project mode only]


```

:(

Sorry, I just recently installed Ubuntu after I heard Gutsy had ATI support for Compiz. :)

It works and looks so great

---

### Post by motin on 2008-02-03
The documentation is a bit outdated and shows how to install the older 1.3 version. 

Here is a newer (albeit in spanish): [http://gamerkore.blogspot.com/2007/12/qpspmanager-202-en-ubuntu-gutsy.html](http://gamerkore.blogspot.com/2007/12/qpspmanager-202-en-ubuntu-gutsy.html)

Basically:

1. Remove conflicting (old) packages:
```
sudo apt-get remove qt3-dev-tools libqt3-mt-dev 
```

2. Install correct dependencies:
```
sudo apt-get install build-essential libqt4-dev zlib1g zlib1g-dev qt4-dev-tools
```

Then follow the documentation but without entering the "src"-dir - just go into the qpspmanager-2.0.2 directory and run qmake etc...

Good luck!

---

