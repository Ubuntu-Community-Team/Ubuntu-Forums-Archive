---
title: "trackball explorer1.0 PS2/USB"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by joethesmith on 2007-06-09
I have this mouse and at startup the 4/5 buttons do not function properly, after some searching I learned to type the following in terminal and it works. 
```
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11"
```
 how do i have this be automatic at startup?

Thanks
Joe

---

### Post by Skrynesaver on 2007-06-09
You can create a script with this line in it and call your script from /etc/X11/Xsession

---

### Post by joethesmith on 2007-06-09
and how might I do that?

---

### Post by Skrynesaver on 2007-06-09
create a directory in /etc/X11 called scripts
create a file called config_mouse.sh
this file will contain the following
```

#! /bin/sh
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11"

```
make the file executable 
chmod 755 config_mouse.sh

Then add the following line to the end of your /etc/X11/Xsession file
/etc/X11/scripts/config_mouse.sh

---

### Post by joethesmith on 2007-06-09
It still is not working at startup, but i am able to run that script manually and it works. here is what i have at in my Xsession file

```
#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 1507M 2004-09-13 07:36:26Z (local) $

set -e

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
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
ERRFILE=$HOME/.xsession-errors

# attempt to create an error file; abort if we cannot
if touch "$ERRFILE" 2> /dev/null && [ -w "$ERRFILE" ] &&
  [ ! -L "$ERRFILE" ]; then
  chmod 600 "$ERRFILE"
elif ERRFILE=$(tempfile 2> /dev/null); then
  if ! ln -sf "$ERRFILE" "${TMPDIR:=/tmp}/xsession-$USER"; then
    message "warning: unable to symlink \"$TMPDIR/xsession-$USER\" to" \
             "\"$ERRFILE\"; look for session log/errors in" \
             "\"$TMPDIR/xsession-$USER\"."
  fi
else
  errormsg "unable to create X session log/error file; aborting."
fi

exec >>"$ERRFILE" 2>&1

echo "$PROGNAME: X session started for $LOGNAME at $(date)"

# sanity check; is our session script directory present?
if [ ! -d "$SYSSESSIONDIR" ]; then
  errormsg "no \"$SYSSESSIONDIR\" directory found; aborting."
fi

# Attempt to create a file of non-zero length in /tmp; a full filesystem can
# cause mysterious X session failures.  We do not use touch, :, or test -w
# because they won't actually create a file with contents.  We also let standard
# error from tempfile and echo go to the error file to aid the user in
# determining what went wrong.
WRITE_TEST=$(tempfile)
if ! echo "*" >>"$WRITE_TEST"; then
  message "warning: unable to write to ${WRITE_TEST%/*}; X session may exit" \
          "with an error"
fi
rm -f "$WRITE_TEST"

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

exit 0

# vim:set ai et sts=2 sw=2 tw=80:
/etc/X11/scripts/config_mouse.sh
```

---

### Post by Skrynesaver on 2007-06-09
The command "exit 0" causes the script to terminate, try calling the script before this line

---

### Post by joethesmith on 2007-06-09
I moved the line above the exit 0. so now it looks like this:
```
SESSIONFILES=$(run_parts $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
fi
/etc/X11/scripts/config_mouse.sh
exit 0

# vim:set ai et sts=2 sw=2 tw=80:
``` however it still doesnt run at startup, do i need to have anything written before it?

---

### Post by Skrynesaver on 2007-06-09
My sincere apologies, The Xsession script is the wrong place to do this.
You should just add the line

pointer = 1 2 3 4 5 8 9 6 7 10 11 

to a file called .Xmodmap in your home directory.
On login gnome should ask if you wish to use this modmap and all should work.  Sorry again for unintentionally misleading you

---

### Post by joethesmith on 2007-06-09
its no big deal, i highly appiciate the help.  but now for a really dumb question. 
I am not able to find .Xmodmap in my home directory, and a search is coming up empty for the file

---

### Post by Skrynesaver on 2007-06-09
Apologies in order again, I was less than clear, you should create the file 
.Xmodmap
This causes modmap to be triggered when you login and it then "runs" the contents of the file

---

### Post by joethesmith on 2007-06-09
That worked perfectly! \\:D/

thank you very much.

---

