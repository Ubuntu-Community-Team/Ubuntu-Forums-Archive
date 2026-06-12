---
title: "Xsession does not execute"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by ohanyan on 2007-12-04
I was installing tecplot and it may have been something that I did, but my Xsession simply does not work any more, so I have to log in with Failsafe mode.  I do not have any reason to believe that the tecplot installation itself has anything to do with it, but I'm willing to try suggestions.  I've been at this for hours: I have reinstalled gdm, bash, updated my system, restarted my computer a million times.  :mad:  I'm just confused :confused:  Please help.... thanks in advance.

ohanyan@fiedler:/etc/gdm$ echo $SHELL
/bin/bash
ohanyan@fiedler:/etc/gdm$ 


**************************************************************
ohanyan@fiedler:~$ cd /etc/gdm/
ohanyan@fiedler:/etc/gdm$ ./Xsession
./Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
./Xsession: Starting the failsafe xterm session.
exec: 147: xterm: not found
ohanyan@fiedler:/etc/gdm$ 
****************************************************************

ohanyan@fiedler:/etc/gdm$ bash ./Xsession
./Xsession: Beginning session setup...
./Xsession: Starting the failsafe xterm session.
./Xsession: line 146: exec: xterm: not found
ohanyan@fiedler:/etc/gdm$ 


***************** /etc/profile *******************************************

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
[[ -f "/etc/autopackage/paths-bash" ]] && . "/etc/autopackage/paths-bash"

***************** etc/gdm/Xsession ************************************
#!/bin/sh
#
# This is SORT OF LIKE an X session, but not quite.  You get a command as the
# first argument (it could be multiple words, so run it with "eval").  As a
# special case, the command can be:
#  failsafe - Run an xterm only
#  default - Run the appropriate Xclients startup (see the code below)
#  custom - Run ~/.xsession and if that's not available run 'default'
#
# (Note that other arguments could also follow, but only the command one is
# right now relevant and supported)
#
# The output is ALREADY redirected to .xsession-errors in GDM.  This way
# .xsession-errors actually gets more output such as if the PreSession script
# is failing.  This also prevents DoS attacks if some app in the users session
# can be prodded to dump lots of stuff on the stdout/stderr.  We wish to be
# robust don't we?  In case you wish to use an existing script for other DM's,
# you can just not redirect when GDMSESSION is set.  GDMSESSION will always
# be set from gdm.
#
# Also note that this is not run as a login shell, this is just executed.
#
# based on:
# $XConsortium: Xsession /main/10 1995/12/18 18:21:28 gildea $

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ]; then
    if [ -n "$zenity" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | $xmessage -center -file -
    fi
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ]; then
    if [ -n "$zenity" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | $xmessage -center -file -
    fi
  fi
}

errormsg () {
  # exit script with error
  message "$*"
  exit 1
}

internal_errormsg () {
  # exit script with error; essentially a "THIS SHOULD NEVER HAPPEN" message
  # One big call to message() for the sake of xmessage; if we had two then
  # the user would have dismissed the error we want reported before seeing the
  # request to report it.
  errormsg "$*" \
           "Please report the installed version of the \"xfree86-common\"" \
           "package and the complete text of this error message to" \
           "<debian-x@lists.debian.org>."
}

run_parts () {
  # until run-parts --noexec is implemented
  if [ -z "$1" ]; then
    internal_errormsg "run_parts() called without an argument."
  fi
  if [ ! -d "$1" ]; then
    internal_errormsg "run_parts() called, but \"$1\" does not exist or is" \
                      "not a directory."
  fi
  for F in $(/bin/ls $1); do
    if expr "$F" : '[[:alnum:]_-]\+$' > /dev/null 2>&1; then
      if [ -f "$1/$F" ]; then
        echo "$1/$F"
      fi
    fi
  done
}
# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
ALTUSERXSESSION=$HOME/.Xsession

# this will go into the .xsession-errors along with all other echo's
# good for debugging where things went wrong
echo "$0: Beginning session setup..."

# First read /etc/profile and .profile
test -f /etc/profile && . /etc/profile
test -f "$HOME/.profile" && . "$HOME/.profile"
# Second read /etc/xprofile and .xprofile for X specific setup
test -f /etc/xprofile && . /etc/xprofile
test -f "$HOME/.xprofile" && . "$HOME/.xprofile"

# Translation stuff
if [ -x "/usr/lib/gdm/gdmtranslate" ] ; then
  gdmtranslate="/usr/lib/gdm/gdmtranslate"
else
  gdmtranslate=
fi

# Note that this should only go to zenity dialogs which always expect utf8
gettextfunc () {
  if [ "x$gdmtranslate" != "x" ] ; then
    "$gdmtranslate" --utf8 "$1"
  else
    echo "$1"
  fi
}

zenity=`which zenity 2>/dev/null`
xmessage=`which xmessage 2>/dev/null`

command="$1"

if [ -z "$command" ] ; then
  command=failsafe
fi

if [ x"$command" = xfailsafe ] ; then
  if [ -n "$zenity" ] ; then
    "$zenity" --info --text "`gettextfunc "This is the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upper left corner"`"
  else
    echo "$0: Starting the failsafe xterm session."
  fi
  exec xterm -geometry 80x24+0+0
fi

# clean up after xbanner
freetemp=`which freetemp 2>/dev/null`
if [ -n "$freetemp" ] ; then
	"$freetemp"
fi

usermodmap="$HOME/.Xmodmap"
userxkbmap="$HOME/.Xkbmap"

if [ -f "$userxkbmap" ]; then
    setxkbmap `cat "$userxkbmap"`
    XKB_IN_USE=yes
fi

# xkb and xmodmap don't play nice together
if [ -z "$XKB_IN_USE" ]; then
    if [ -f "$usermodmap" ]; then
       xmodmap "$usermodmap"
    fi
fi

unset XKB_IN_USE

# Normalize languages, some places/distros screw us up in /etc/profile,
# so in case the user did select a language
if [ -n "$GDM_LANG" ]; then
  LANG="$GDM_LANG"
  export LANG

  if [ -n "$LC_ALL" ]; then
    if [ "$LC_ALL" != "$LANG" ]; then
      LC_ALL="$LANG"
    fi
  else
    unset LC_ALL
  fi

  if [ -n "$LANGUAGE" ]; then
    if [ "$LANGUAGE" != "$LANG" ]; then
      LANGUAGE="$LANG"
    fi
  else
    unset LANGUAGE
  fi

  if [ -n "$LINGUAS" ]; then
    if [ "$LINGUAS" != "$LANG" ]; then
      LINGUAS="$LANG"
    fi
  else
    unset LINGUAS
  fi
fi

# The default Debian session runs xsession first, so we just do that for
# "custom"
if [ "x$command" = "xcustom" ] ; then
  shift
  set default $*
fi

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run_parts $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
fi


echo "$0: Executing $command failed, will try to run x-terminal-emulator"

if [ -n "$zenity" ] ; then
	"$zenity" --info --text "`gettextfunc "I could not start your session and so I have started the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upper left corner"`"
fi

exec x-terminal-emulator -geometry 80x24+0+0

---

### Post by m0biu5 on 2007-12-04
```
exec: 147: xterm: not found
```

It seems like you don't have xterm, and the script is trying to use that. Can you check to make sure xterm is installed?

---

### Post by ohanyan on 2007-12-04
every command in xsession executes fine on the terminal. This used to work. I DO have xterm

Thanks

---

### Post by m0biu5 on 2007-12-04
...and GDM is running? Also, try commenting out line 20 of /etc/profile. You can restart GDM with ```
/etc/init.d/gdm restart
```

---

### Post by ohanyan on 2007-12-05
I restarted it. no better.

And it is running.


root@fiedler:/etc# gdm
GDM already running. Aborting!

---

### Post by ohanyan on 2007-12-05
Also

/etc/gdm/Xsession does not work
but
. /etc/gdm/Xsession does

How do I make it execute the command this way at login?

Thanks

---

