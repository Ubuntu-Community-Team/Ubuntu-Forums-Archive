---
title: "configure gives error message"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Dr. Cox on 2007-03-22
hi there, 

with most programs the routine ./configre, make, make install works rather well.

now i've come accross two problems:

[PHP]  creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for gdbm_open in -lgdbm... no
checking for floor in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/time.h... yes
checking for sys/timeb.h... yes
checking for unistd.h... yes
checking for working const... yes
checking whether time.h and sys/time.h may both be included... yes
checking return type of signal handlers... void
checking for ftime... yes
checking for select... yes
checking for strstr... yes
checking for gettimeofday... yes
updating cache ./config.cache
creating ./config.status
creating Makefile
creating tests/Makefile
creating books/Makefile
creating config.h
[/PHP]

after that make would only give me errors as well.

on another program only following errors appear:

[PHP]configure: Makefile configuration program for ChessDB
    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.4
    Your operating system is: Linux 2.6.17-10-generic
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.4 library: /usr/lib
    Location of Tk 8.4 library: /usr/lib
    Location of X11 library: /usr/lib
    Checking if your system already has zlib installed: yes.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile ChessDB.
[/PHP]

here is the respective ./confgure file:

[PHP]#!/bin/sh
# configure:
#    Makefile configuration script for ChessDB.
#
# This program tries to determine system-specific details needed
# for compiling ChessDB (such as the version of Tcl/Tk you have
# installed, and where to find the Tcl/Tk header and library 
# files), and creates the file "Makefile".


# Try to find the most recent version of Tcl/Tk 8.x that is installed,
# by searching the PATH directories for tclsh8.3, tclsh83, etc.  If no
# tclsh program with a version number in the file name is found, the
# default program to execute is just tclsh.
# The backslashes at the end of these lines are needed: \
tclsh=tclsh;

# This shell script code did not work for me in Linux so it is
# commented out for now; the configure script will just run in
# tclsh even if there is a more recent version.
## for tclver in 80 8.0 81 8.1 82 8.2 83 8.3 84 8.4 85 8.5; do \
##   IFS=:; \
##  for dir in $PATH; do \
##    if [ -x $dir/tclsh$tclver ]; then tclsh=$dir/tclsh$tclver; fi; \
##  done; \
## done

# Now execute this script using the best tclsh version found:
# The backslash at the end of this line is needed: \
exec $tclsh "$0" ${1+"$@"}


# tcl/lang/russian.tcl 
# Default values for Makefile settings:
#
set var(BINDIR) /usr/local/bin
set var(COMPILE) g++
set var(CC) gcc
set var(DEBUG) #-DASSERTIONS
set var(LANGUAGES) [list \
  tcl/lang/czech-basic.tcl \
  tcl/lang/czech-eco.tcl \
  tcl/lang/czech-help.tcl \
  tcl/lang/czech-tips.tcl \
  tcl/lang/deutsch-basic.tcl \
  tcl/lang/deutsch-eco.tcl \
  tcl/lang/deutsch-help.tcl \
  tcl/lang/deutsch-tips.tcl \
  tcl/lang/francais-basic.tcl \
  tcl/lang/francais-eco.tcl \
  tcl/lang/francais-help.tcl \
  tcl/lang/francais-tips.tcl \
  tcl/lang/hungary-eco.tcl \
  tcl/lang/hungary-basic.tcl \
  tcl/lang/hungary-help.tcl \
  tcl/lang/hungary-tips.tcl \
  tcl/lang/italian-basic.tcl \
  tcl/lang/italian-eco.tcl \
  tcl/lang/italian-help.tcl \
  tcl/lang/italian-tips.tcl \
  tcl/lang/korean-basic.tcl \
  tcl/lang/korean-eco.tcl \
  tcl/lang/korean-help.tcl \
  tcl/lang/korean-tips.tcl \
  tcl/lang/nederlan-basic.tcl \
  tcl/lang/nederlan-eco.tcl \
  tcl/lang/nederlan-help.tcl \
  tcl/lang/nederlan-tips.tcl \
  tcl/lang/norsk-basic.tcl \
  tcl/lang/norsk-eco.tcl \
  tcl/lang/norsk-help.tcl \
  tcl/lang/norsk-tips.tcl \
  tcl/lang/polish-basic.tcl \
  tcl/lang/polish-eco.tcl \
  tcl/lang/polish-help.tcl \
  tcl/lang/polish-tips.tcl \
  tcl/lang/portbr-basic.tcl \
  tcl/lang/portbr-eco.tcl \
  tcl/lang/portbr-help.tcl \
  tcl/lang/portbr-tips.tcl \
  tcl/lang/russian-basic.tcl \
  tcl/lang/russian-eco.tcl \
  tcl/lang/russian-help.tcl \
  tcl/lang/russian-tips.tcl \
  tcl/lang/serbian-basic.tcl \
  tcl/lang/serbian-eco.tcl \
  tcl/lang/serbian-help.tcl \
  tcl/lang/serbian-tips.tcl \
  tcl/lang/spanish-basic.tcl \
  tcl/lang/spanish-eco.tcl \
  tcl/lang/spanish-help.tcl \
  tcl/lang/spanish-tips.tcl \
  tcl/lang/swedish-basic.tcl \
  tcl/lang/swedish-eco.tcl \
  tcl/lang/swedish-help.tcl \
  tcl/lang/swedish-tips.tcl]
set var(LINK) g++
set var(OBJS) {$(SCIDOBJS)}
set var(OPTIMIZE) {-O2 -fno-rtti -fno-exceptions}
set var(PROFILE) {}
set var(SCIDFLAGS) {}
set var(SHAREDIR) /usr/local/share/chessdb
set var(SOUNDSDIR) /usr/local/share/chessdb/sounds
set var(TBDIR) /usr/local/share/chessdb/tablebases
set var(MANDIR) /usr/local/man 
set var(TB) {-DSCID_USE_TB -DT41_INCLUDE}
set var(TCL_VERSION) $tcl_version
set var(WARNINGS) -Wall
set var(ZLIB) -lz

set defaultVar(TCL_INCLUDE) {-I/usr/include}
set defaultVar(TCL_LIBRARY) {-L/usr/lib -ltcl$(TCL_VERSION) -ldl}
set defaultVar(TK_LIBRARY) \
    {$(TCL_LIBRARY) -ltk$(TCL_VERSION) -L/usr/X11R6/lib -lX11}


# findDir:
#    Returns the first directory in the list "path" that contains a
#    readable file matching the wildcard pattern "f".
#    If exp is provided, the directory of the first such file that also
#    has a line containing the regular expression "exp" is returned. If
#    none of the found files contains the expression, the first file
#    found is returned.
#
proc findDir {f path {exp ""}} {
    set best ""
    foreach dir $path {
        set p [file join $dir $f]
        if {![catch {glob $p}]} {
          if {$best == ""} { set best $p }
            if {$exp != ""} {
              if {[catch {exec grep -c $exp $p}] == 0} { return $dir } else {
                # puts "$p skipped, not right version"
              }
            } else {
                return $dir 
            }
        }
    }
    return $best
}


# findTclTkPaths:
#    Finds all details of the Tcl/Tk installation.
#    Returns 1 on success, 0 on failure.
#
proc findTclTkPaths {} {
    global tclv tclv_nodot var
    set success 1
    array set opt {}

    # headerPath: List of possible locations for tcl.h and tk.h
    set headerPath {
        /usr/include
        /usr/local/tcl/include
        /usr/local/include
        /usr/X11/include
        /usr/X11R6/include
        /usr/local/X11/include
        /opt/tcltk/include
        /usr/X11R/include
    }
    lappend headerPath "/usr/local/include/tcl${tclv}"
    lappend headerPath "/usr/local/include/tk${tclv}"
    lappend headerPath "/usr/local/include/tcl${tclv_nodot}"
    lappend headerPath "/usr/local/include/tk${tclv_nodot}"
    lappend headerPath "/usr/include/tcl${tclv}"
    lappend headerPath "/usr/include/tk${tclv}"
    lappend headerPath "/usr/include/tcl${tclv_nodot}"
    lappend headerPath "/usr/include/tk${tclv_nodot}"

    # libraryPath: List of possible locations of Tcl/Tk library.
    set libraryPath {
        /usr/lib
        /usr/local/tcl/lib
        /usr/local/lib
        /usr/X11R6/lib
        /opt/tcltk/lib
    }
    lappend libraryPath "/usr/lib/tcl${tclv}"
    lappend libraryPath "/usr/lib/tk${tclv}"
    lappend libraryPath "/usr/lib/tcl${tclv_nodot}"
    lappend libraryPath "/usr/lib/tk${tclv_nodot}"

    # Try to add tcl_library and auto_path values to libraryPath,
    # in case the user has a non-standard Tcl/Tk library location:

    if {[info exists ::tcl_library]} {
        lappend headerPath \
            [file join [file dirname [file dirname $::tcl_library]] include]
        lappend libraryPath [file dirname $::tcl_library]
        lappend libraryPath $::tcl_library
    }
    if {[info exists ::auto_path]} {
        foreach name $::auto_path {
            lappend libraryPath $name
        }
    }

    # x11Path: List of common locations of the X11 library files.
    set x11Path {
        /usr/lib
        /usr/X11/lib
        /usr/X11R6/lib
        /usr/local/X11/lib
        /usr/local/X11R6/lib
        /usr/X/lib
        /usr/local/X/lib
        /usr/openwin/lib
    }

    if {! [info exists var(TCL_INCLUDE)]} {
        puts -nonewline {    Location of "tcl.h": }
        set opt(tcl_h) [findDir "tcl.h" $headerPath "TCL_VERSION.*$tclv"]
        if {$opt(tcl_h) == ""} {
            puts "not found"
            set success 0
        } else {
            puts $opt(tcl_h)
        }

        puts -nonewline {    Location of "tk.h": }
        set opt(tk_h) [findDir "tk.h" $headerPath "TK_VERSION.*$tclv"]
        if {$opt(tk_h) == ""} {
            puts "not found"
            set success 0
        } else {
            puts $opt(tk_h)
        }
    }

    set opt(tcl_lib) ""
    set opt(tk_lib) ""

    if {! [info exists var(TCL_LIBRARY)]} {
        puts -nonewline "    Location of Tcl $tclv library: "
        set opt(tcl_lib) [findDir "libtcl${tclv}.*" $libraryPath]
        if {$opt(tcl_lib) == ""} {
            set opt(tcl_lib) [findDir "libtcl${tclv_nodot}.*" $libraryPath]
            if {$opt(tcl_lib) == ""} {
                puts "not found"
                set success 0
            } else {
                set opt(tcl_lib_file) "tcl${tclv_nodot}"
                puts $opt(tcl_lib)
            }
        } else {
            set opt(tcl_lib_file) "tcl\$(TCL_VERSION)"
            puts $opt(tcl_lib)
        }
    }

    if {! [info exists var(TK_LIBRARY)]} {
        puts -nonewline "    Location of Tk $tclv library: "
        set opt(tk_lib) [findDir "libtk${tclv}.*" $libraryPath]
        if {$opt(tk_lib) == ""} {
            set opt(tk_lib) [findDir "libtk${tclv_nodot}.*" $libraryPath]
            if {$opt(tk_lib) == ""} {
                puts "not found"
                set success 0
            } else {
                set opt(tk_lib_file) "tk${tclv_nodot}"
                puts $opt(tk_lib)
            }
        } else {
            set opt(tk_lib_file) "tk\$(TCL_VERSION)"
            puts $opt(tk_lib)
        }

        puts -nonewline {    Location of X11 library: }
        set opt(x11_lib) [findDir "libX11*" $x11Path]
        if {$opt(x11_lib) == ""} {
            puts "not found"
            set success 0
        } else {
            puts $opt(x11_lib)
        }
    }

    # If all files were found, assemble the TCL_INCLUDE, TCL_LIBRARY
    # and TK_LIBRARY settings:

    if {$success} {
        if {! [info exists var(TCL_INCLUDE)]} {
            set var(TCL_INCLUDE) "-I$opt(tcl_h)"
            if {$opt(tcl_h) != $opt(tk_h)} {
                append var(TCL_INCLUDE) " -I$opt(tk_h)"
            }
        }
        if {! [info exists var(TCL_LIBRARY)]} {
            set var(TCL_LIBRARY) "-L$opt(tcl_lib) -l$opt(tcl_lib_file) -ldl"
        }
        if {! [info exists var(TK_LIBRARY)]} {
            set var(TK_LIBRARY) {$(TCL_LIBRARY)}
            if {$opt(tk_lib) != $opt(tcl_lib)} {
                append var(TK_LIBRARY) " -L$opt(tk_lib)"
            }
            append var(TK_LIBRARY) " -l$opt(tk_lib_file)"
            if {$opt(x11_lib) != $opt(tcl_lib) && $opt(x11_lib) != $opt(tk_lib)} {
                append var(TK_LIBRARY) " -L$opt(x11_lib)"
            }
            append var(TK_LIBRARY) " -lX11"
        }
    }
    return $success
}


# testzlib_sh:
#    Script used to test if the system has zlib installed.
#
set testzlib {#!/bin/sh
CC=gcc
cat <<EOF > testzlib.c
#include <zlib.h>
int main()
{
    z_streamp z;
    deflateInit(z, 0);
    return 0;
}
EOF

$CC -o testzlib testzlib.c -lz
if [ -f testzlib ]; then
    exit 0
else
    exit 1
fi
}

# systemHasZlib:
#    Determines if the system has zlib installed. If not, the Zlib
#    version that comes with ChessDB will be used.
#
proc systemHasZlib {} {
    set systemHasZlib 0
    flush stdout
    if {[catch {open testzlib.sh w} f]} { return 0 }
    puts $f $::testzlib
    close $f
    set result 0
    if {! [catch {exec sh testzlib.sh} err]} { set result 1 }
    catch {file delete -force testzlib.sh}
    catch {file delete -force testzlib.c}
    catch {file delete -force testzlib}
    return $result
}


# checkZlib:
#    Checks whether the system has the zlib compression library installed,
#    if necessary. 
#
proc checkZlib {} {
    global var
    if {[string first "DZLIB" $var(SCIDFLAGS)] >= 0} {
        set var(ZLIB) {}
        set var(OBJS) {$(SCIDOBJS) $(ZLIBOBJS)}
        return
    }
    puts -nonewline "    Checking if your system already has zlib installed: "
    flush stdout
    if {[systemHasZlib]} {
        puts "yes."
        set var(ZLIB) {-lz}
        set var(OBJS) {$(SCIDOBJS)}
    } else {
        puts "no."
        append var(SCIDFLAGS) " -DZLIB"
        set var(ZLIB) {}
        set var(OBJS) {$(SCIDOBJS) $(ZLIBOBJS)}
    }
}

# writeMakefile:
#    Creates the Makefile using Makefile.conf and the configured
#    settings.
#
proc writeMakefile {{type ""}} {
    global var defaultVar
    set default 0
    set success 0
    if {$type == "default"} {
        set default 1
        set var(CONFIG_RESULT) \
            {You have not run "./configure" yet.  The default settings are:}
    } else {
        set success [findTclTkPaths]
        set var(CONFIG_RESULT) \
            {Sorry, "./configure" was not successful. The default settings are:}
        if {$success} {
           set var(CONFIG_RESULT) \
               {The settings determined by "./configure" are:}
        }
    }

    foreach name {TCL_INCLUDE TCL_LIBRARY TK_LIBRARY} {
        if {! [info exists var($name)]} { set var($name) $defaultVar($name) }
    }

    checkZlib

    if {[catch {set from [open "Makefile.conf" r]}]} {
       puts "Error opening file for reading: Makefile.conf"
       exit 1
    }
    if {[catch {set to [open "Makefile" w]}]} {
       puts "Error opening file for writing: Makefile"
       exit 1
    }

    set line [gets $from]
    while {1} {
        set line [gets $from]
        if {[eof $from]} { break }
        foreach sub [array names var] {
            set first [string first "@$sub@" $line]
            if {$first >= 0} {
                set last [expr $first + [string length $sub] + 1]
                set pre [string range $line 0 [expr $first - 1]]
                set post [string range $line [expr $last + 1] end]
                set line $pre
                append line $var($sub)
                append line $post
            }
        }
        if {[string compare "!" [string index $line 0]]} {
            puts $to $line
        }
    }

    close $from
    close $to
    if {$default} {
        puts {The default Makefile was written.}
    } elseif {$success} {
        puts {The Makefile configured for your system was written.}
        puts {Now just type "make" to compile ChessDB.}
    } else {
        puts {Not all settings could be determined!}
        puts {The default Makefile was written.}
        puts {You will need to edit it before you can compile ChessDB.}
    }
}


# usage:
#     Explains the usage of this script, then exits
#
proc usage {} {
    puts {Valid options are:}
    puts {  BINDIR       The location for chessdb executables for "make install".}
    puts {  COMPILE      Your C++ compiler. Default: "g++".}
    puts {  CC           Your C compiler. Default: "gcc".}
    puts {  DEBUG        Debugging flags. Use DEBUG="-DASSERTIONS" for assertions.}
    puts {  LANGUAGES    Multi-language support. Use LANGUAGES="" for English only.}
    puts {  LINK         Your C++ linker. Default: "g++".}
    puts {  MANDIR       Directory for manual pages. Default: "/usr/local/man".}
    puts {  OPTIMIZE     C++ optimizations. Default: "-O2 -fno-rtti -fno-exceptions".}
    puts {  PROFILE      Used for profiling the source code. Default: none.}
    puts {  SCIDFLAGS    ChessDB customization flags. Default: none.}
    puts {  SHAREDIR     Location of ChessDB data (ECO, spelling) files for "make install".}
    puts {  SOUNDSDIR    Location of ChessDB sounds files  (wav files) for "make install".}
    puts {  TB           Tablebase support. Use TB="" to exclude Tablebase code.}
    puts {  TCL_INCLUDE  Compiler directives for including Tcl.}
    puts {  TCL_LIBRARY  Compiler directives for linking Tcl.}
    puts {  TCL_VERSION  Your Tcl/Tk version. Example: TCL_VERSION="8.3".}
    puts {  TK_LIBRARY   Compiler directives for linking Tcl/Tk.}
    puts {  WARNINGS     C++ compiler warnings. Default: "-Wall".}
    puts {}
    puts {  This configure program should find the proper values for the options}
    puts {  starting with TCL_ and TK_ automatically, so you should only use those}
    puts {  options if it fails to find your Tcl/Tk installation.}
    puts {}
    puts {Example usage:}
    puts {  ./configure LANGUAGES="tcl/francais.tcl" BINDIR="/usr/local/bin"}
    puts {}
    exit 1
}

########################################

puts "configure: Makefile configuration program for ChessDB"

# Parse command-line arguments:
set default 0

foreach arg $argv {
    if {![string compare "default" $arg]} {
        set default 1
    } else {
        set temp_idx [string first "=" $arg]
        if {$temp_idx > 0} {
            set temp_var [string range $arg 0 [expr $temp_idx - 1]]
            set temp_value [string range $arg [expr $temp_idx + 1] end]
            set var($temp_var) $temp_value
        } else {
            puts "Invalid argument: $arg"
            usage
        }
    }
}

if {$default} {
    writeMakefile default
    exit 0
}

if {[file readable "Makefile"]} {
    puts {    Renaming "Makefile" to "Makefile.bak"}
    catch {file rename -force "Makefile" "Makefile.bak"}
}

set tclv $var(TCL_VERSION)
set tclv_nodot [expr round($tclv * 10)]

puts "    Tcl/Tk version: $tclv"
puts "    Your operating system is: $tcl_platform(os) $tcl_platform(osVersion)"

writeMakefile

### End of configure script ###
[/PHP]

excuse the long posts. i have installed build-essential. are the errors somehow related? 

i've also found where tcl.h and tk.h are. but how do i tell the configure script? i'm just really lost. 

any help is appreciated.

cheers

---

### Post by AtrejuT on 2007-03-22
I guess you'll need to install
tcl8.4-dev
tk8.4-dev

since these contain the header files it complains are missing.

Let me know if that helps.

---

### Post by taurus on 2007-03-22
Looks like you need the development packages for both tk & tcl.

```
sudo aptitude update
sudo aptitude install tk-dev tcl-dev
```

---

### Post by Dr. Cox on 2007-03-22
thanks guys,

installing tcl-dev and tk-dev solved one of my error messages. the first program now gives me still the following errors:

[PHP]creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for gdbm_open in -lgdbm... no
checking for floor in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/time.h... yes
checking for sys/timeb.h... yes
checking for unistd.h... yes
checking for working const... yes
checking whether time.h and sys/time.h may both be included... yes
checking return type of signal handlers... void
checking for ftime... yes
checking for select... yes
checking for strstr... yes
checking for gettimeofday... yes
updating cache ./config.cache
creating ./config.status
creating Makefile
creating tests/Makefile
creating books/Makefile
creating config.h
[/PHP]
looks better than last time, though.  more importantly, after trying to run make anyways, it produced the following output:

[PHP]gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c attacks.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c crazy.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c epd.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c learn.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c partner.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c seval.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c ttable.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c book.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c ecache.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c eval.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c moves.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c search.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c sjeng.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c utils.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c newbook.c
newbook.c:27:18: error: gdbm.h: No such file or directory
newbook.c:35:2: error: #error You need the GNU DBM library (GDBM). Go to ftp.gnu.org
newbook.c:114: error: expected ‘)’ before ‘binbook’
newbook.c:158: error: expected declaration specifiers or ‘...’ before ‘GDBM_FILE’
newbook.c: In function ‘replay_game’:
newbook.c:320: error: ‘binbook’ undeclared (first use in this function)
newbook.c:320: error: (Each undeclared identifier is reported only once
newbook.c:320: error: for each function it appears in.)
newbook.c: At top level:
newbook.c:326: error: expected ‘)’ before ‘binbook’
newbook.c: In function ‘build_book’:
newbook.c:377: error: ‘GDBM_FILE’ undeclared (first use in this function)
newbook.c:377: error: expected ‘;’ before ‘binbook’
newbook.c:393: error: ‘binbook’ undeclared (first use in this function)
newbook.c:393: error: ‘GDBM_NEWDB’ undeclared (first use in this function)
newbook.c:393: error: ‘GDBM_FAST’ undeclared (first use in this function)
newbook.c:435: error: too many arguments to function ‘replay_game’
newbook.c: In function ‘choose_binary_book_move’:
newbook.c:453: error: ‘GDBM_FILE’ undeclared (first use in this function)
newbook.c:453: error: expected ‘;’ before ‘binbook’
newbook.c:456: error: ‘datum’ undeclared (first use in this function)
newbook.c:456: error: expected ‘;’ before ‘index’
newbook.c:457: error: expected ‘;’ before ‘data’
newbook.c:469: error: ‘binbook’ undeclared (first use in this function)
newbook.c:469: error: ‘GDBM_READER’ undeclared (first use in this function)
newbook.c:514: error: request for member ‘dptr’ in something not a structure or union
newbook.c:515: error: request for member ‘dsize’ in something not a structure or union
newbook.c:517: error: ‘data’ undeclared (first use in this function)
newbook.c: In function ‘book_learning’:
newbook.c:596: error: ‘GDBM_FILE’ undeclared (first use in this function)
newbook.c:596: error: expected ‘;’ before ‘binbook’
newbook.c:599: error: ‘datum’ undeclared (first use in this function)
newbook.c:599: error: expected ‘;’ before ‘index’
newbook.c:600: error: expected ‘;’ before ‘data’
newbook.c:610: error: ‘binbook’ undeclared (first use in this function)
newbook.c:610: error: ‘GDBM_WRITER’ undeclared (first use in this function)
newbook.c:635: error: request for member ‘dptr’ in something not a structure or union
newbook.c:636: error: request for member ‘dsize’ in something not a structure or union
newbook.c:638: error: ‘data’ undeclared (first use in this function)
newbook.c:686: error: ‘GDBM_REPLACE’ undeclared (first use in this function)
make[2]: *** [newbook.o] Fehler 1
make[2]: Verlasse Verzeichnis '/home/jac/chess/senja/Sjeng-Free-11.2'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/jac/chess/senja/Sjeng-Free-11.2'
make: *** [all-recursive-am] Fehler 2
[/PHP]

what can i do?

---

### Post by taurus on 2007-03-22
There is a problem with one of the programs that you try to compile from, newbook.c.  What are you trying to build (website if there is one) anyway?

---

### Post by Dr. Cox on 2007-03-22
i'm trying to build a computer chess engine. sjeng it's called. from the installation instructions it should be fairly simple.  this error wasn't mentioned on the web page.

by the way, what are gnu dbm libraries anyways. couldn't find tehm via apt-cache search....

---

### Post by taurus on 2007-03-22
Try to install both gdbm and gdbm-dev.

```
sudo aptitude install gdbm gdbm-dev
```

p.s.  You can use synaptic to search for gdbm.

---

### Post by Dr. Cox on 2007-03-23
thanks to all of you. that fixed my problem!

why aren't all these building requirements not included in a regular ubuntu install?

---

