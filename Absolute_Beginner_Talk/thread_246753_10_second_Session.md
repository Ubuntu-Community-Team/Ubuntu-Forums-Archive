---
title: "10 second Session"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by blingenfelter on 2006-08-29
I did something...I'm fairly new to Ubuntu...and now I can't log on. I was loading software from the repositories using Synaptic package manager - trying to tweak my desktop - and the next time I logged on, I got this error:
[COLOR="Blue"]
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.
[/COLOR]
I viewed the .xsession-errors file and this is what it said.

[COLOR="Blue"]/etc/gdm/PreSession/Default: Registering you session with wtmp and utmp

/etc/gdm/PreSession/Default: running/usr/bin/sessreg -a -w /var/log/wtmp -u /var/lib/gdm/:0.Xservers" -h "" -l ":0" "blingenfelter"
etc/gdm/Xsession: Beginning session setup...
/home/blingenfelter/.Xsession: line 2: xcompmgr: command not found[/COLOR]

I can log into the failsafe session, but don't know where to begin to fix the normal login problem.

Thanks,
Ben

---

### Post by meng on 2006-08-29
Are you out of diskspace?
df -h
may help tell you if you're not sure.

---

### Post by blingenfelter on 2006-08-29
Plenty of diskspace.

---

### Post by blingenfelter on 2006-08-29
incidentally, I went ahead and loaded Compmgr, since it couldn't find it, and it only changed the error to 

[COLOR="Red"]/etc/gdm/PreSession/Default: Registering you session with wtmp and utmp

/etc/gdm/PreSession/Default: running/usr/bin/sessreg -a -w /var/log/wtmp -u /var/lib/gdm/:0.Xservers" -h "" -l ":0" "blingenfelter"
etc/gdm/Xsession: Beginning session setup...
[/COLOR]
It only got rid of the last line from earlier. :mad:

---

### Post by blingenfelter on 2006-08-29
This is the text of Xsession, where the login process seems to fail.

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
  for F in $(ls $1); do
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

### Post by blingenfelter on 2006-08-29
There's also a file in GDM entitled XKeepsCrashing ----  Shell Script....

Is this normal?

---

### Post by Ragazzo on 2006-08-29
> **blingenfelter said:**
> There's also a file in GDM entitled XKeepsCrashing ----  Shell Script....

Is this normal?

I have XKeepsCrashing too. What is in /home/blingenfelter/.Xsession?

---

### Post by blingenfelter on 2006-08-29
xcompmgr -c -f -F -r12.000000 -o0.750000 -l-15.000000 -t-15.000000 -I0.028000 -o0.030000 -D10.000000 &


That's it, when "displayed"

---

### Post by Ragazzo on 2006-08-29
> **blingenfelter said:**
> xcompmgr -c -f -F -r12.000000 -o0.750000 -l-15.000000 -t-15.000000 -I0.028000 -o0.030000 -D10.000000 &


That's it, when "displayed"

Try renaming the file ~/.Xsession to Xsession.bak and login.

---

### Post by blingenfelter on 2006-08-29
That worked. What do you think it was? and do you think it will continue to happen if I don't change something else?

---

### Post by Ragazzo on 2006-08-29
> **blingenfelter said:**
> That worked. What do you think it was? and do you think it will continue to happen if I don't change something else?

There is a package called xcompmgr in Synaptic. Maybe you had it installed first but another package removed it later and forgot to handle ~/.Xsession file.

---

### Post by blingenfelter on 2006-08-29
Thank you very much for your help.

---

### Post by Toxicity999 on 2006-08-29
And as for it failing even after you had it installed could be an issue with your graphics card not liking that much... I'm not sure how xcomp is recieved accross the boards, but just an assumption.

---

