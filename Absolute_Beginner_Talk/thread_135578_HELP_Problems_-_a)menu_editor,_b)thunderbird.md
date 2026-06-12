---
title: "HELP? Problems - a)menu editor, b)thunderbird"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by xx75 on 2006-02-24
Hello interested ones-

I am in need of some assistance with 2 issues:

[COLOR="Red"]a)[/COLOR]  I am unable to access the applications menu editor... to edit my applications (der!). When I click the icon in the menu bar it just hangs for a while then does nothing. I had a stab at trying to enter through terminal with gmenu-simple-editor but I can't add icons to my menu this way.

Also...

[COLOR="Red"]b)[/COLOR]  I just installed thunderbird 1.5 following the ubuntu wiki guide and can not run thunderbird from terminal (bash: thunderbird: command not found). I Can, however, run it by going to it's directory folder and double clicking on the thunderbird icon. And I can't add an application menu icon (see problem [COLOR="Red"]a)[/COLOR])

Please be gentle for I am still a newbie.
Any help is greatly appreciated. [COLOR="Navy"]Thanks team![/COLOR]:-D

cheerio
xx75

---

### Post by Adrenal on 2006-02-24
See? Newbies? This is the sort of post you should be aiming for. This is the sort of post that gets help

Anyhoo, not sure about your first problem, your second should be remedied by running mozilla-thunderbird

---

### Post by andrewsawyer on 2006-02-24
b) try mozilla-thunderbird

a) I've not got Breezy, however I'm sure there is a how-to thread in the tips and tricks section or maybe on [www.ubuntuguide.org](www.ubuntuguide.org) giving a program you can download to get another menu editor.  Dapper comes with Alacarte Menu Editor - maybe you can download that through Synaptic?

Edit: justed checked re a).  Try the following:

```
sudo apt-get install smeg
``` to install the menu editor shown on ubuntuguide.org.  You should be able to run it from terminal with the command 'smeg'.

---

### Post by xx75 on 2006-02-24
Hi Adrenal & andrewsawyer

Thanks for the quick responses
I did mozilla-thunderbird and this was the result
> 
run-mozilla.sh: Cannot execute /opt/thunderbird/mozilla-thunderbird-bin.


any suggestions?

as for smeg, it worked like a charm, thanks!\\:D/

---

### Post by andrewsawyer on 2006-02-24
Odd.  try
```
/usr/bin/mozilla-thunderbird
```

If that doesn't work, then check where Thundebird is installed to using 
```
whereis mozilla-thunderbird
``` and it should be in a /bin directory somewhere.  Type in the full location of the address - as per above code.

If neither of those work, I'm afraid I'm stumped!

---

### Post by xx75 on 2006-02-24
Thanks again-

Ok, here's what i got
> 
mozilla-thunderbird: /usr/bin/mozilla-thunderbird /etc/mozilla-thunderbird /usr/bin/X11/mozilla-thunderbird


Tried both bin files with the same result as before.

When i said before that I double clicked on an icon to get it working, it was an sh file, not a bin, and it gave me the options to run, run in terminal, display or cancel. Unfortunately I am very new to all this so I don't even know if this makes a difference.

Thanks again, again

---

### Post by andrewsawyer on 2006-02-24
Can you post the contents of the sh script please?  Sorry - I skipped the section about the fact it was v1.5 - whoops!

---

### Post by xx75 on 2006-02-24
Cool -

Here is what it says -

> 
#!/bin/sh
#
# ***** BEGIN LICENSE BLOCK *****
# Version: MPL 1.1/GPL 2.0/LGPL 2.1
#
# The contents of this file are subject to the Mozilla Public License Version
# 1.1 (the "License"); you may not use this file except in compliance with
# the License. You may obtain a copy of the License at
# [http://www.mozilla.org/MPL/](http://www.mozilla.org/MPL/)
#
# Software distributed under the License is distributed on an "AS IS" basis,
# WITHOUT WARRANTY OF ANY KIND, either express or implied. See the License
# for the specific language governing rights and limitations under the
# License.
#
# The Original Code is mozilla.org Code.
#
# The Initial Developer of the Original Code is
# Netscape Communications Corporation.
# Portions created by the Initial Developer are Copyright (C) 1998
# the Initial Developer. All Rights Reserved.
#
# Contributor(s):
#
# Alternatively, the contents of this file may be used under the terms of
# either the GNU General Public License Version 2 or later (the "GPL"), or
# the GNU Lesser General Public License Version 2.1 or later (the "LGPL"),
# in which case the provisions of the GPL or the LGPL are applicable instead
# of those above. If you wish to allow use of your version of this file only
# under the terms of either the GPL or the LGPL, and not to allow others to
# use your version of this file under the terms of the MPL, indicate your
# decision by deleting the provisions above and replace them with the notice
# and other provisions required by the GPL or the LGPL. If you do not delete
# the provisions above, a recipient may use your version of this file under
# the terms of any one of the MPL, the GPL or the LGPL.
#
# ***** END LICENSE BLOCK *****

## $Id: mozilla.in,v 1.5.4.1 2005/09/20 21:13:05 dbaron%dbaron.org Exp $
## 
## Usage:
##
## $ mozilla [args]
##
## This script is meant to run the mozilla-bin binary from either 
## mozilla/xpfe/bootstrap or mozilla/dist/bin.
##
## The script will setup all the environment voodoo needed to make
## the mozilla-bin binary to work.
##

moz_pis_startstop_scripts()
{
  MOZ_USER_DIR=".thunderbird"
  # MOZ_PIS_ is the name space for "Mozilla Plugable Init Scripts"
  # These variables and there meaning are specified in
  # mozilla/xpfe/bootstrap/init.d/README
  MOZ_PIS_API=2
  MOZ_PIS_MOZBINDIR="${dist_bin}"
  MOZ_PIS_SESSION_PID="$$"
  MOZ_PIS_USER_DIR="${MOZ_USER_DIR}"
  export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR
  
  case "${1}" in
    "start")
      for curr_pis in "${dist_bin}/init.d"/S* "${HOME}/${MOZ_USER_DIR}/init.d"/S* ; do
        if [ -x "${curr_pis}" ] ; then
          case "${curr_pis}" in
            *.sh) .  "${curr_pis}"         ;;
            *)       "${curr_pis}" "start" ;;
          esac
        fi
      done
      ;;
    "stop")
      for curr_pis in "${HOME}/${MOZ_USER_DIR}/init.d"/K* "${dist_bin}/init.d"/K* ; do
        if [ -x "${curr_pis}" ] ; then
          case "${curr_pis}" in
            *.sh) . "${curr_pis}"        ;;
            *)      "${curr_pis}" "stop" ;;
          esac
        fi
      done
      ;;
    *)
      echo 1>&2 "$0: Internal error in moz_pis_startstop_scripts."
      exit 1
      ;;
  esac
}

#uncomment for debugging
#set -x

moz_libdir=/usr/local/lib/thunderbird-1.5
MRE_HOME=/usr/local/lib/mre/mre-1.5

# Use run-mozilla.sh in the current dir if it exists
# If not, then start resolving symlinks until we find run-mozilla.sh
found=0
progname="$0"
curdir=`dirname "$progname"`
progbase=`basename "$progname"`
run_moz="$curdir/run-mozilla.sh"
if test -x "$run_moz"; then
  dist_bin="$curdir"
  found=1
else
  here=`/bin/pwd`
  while [ -h "$progname" ]; do
    bn=`basename "$progname"`
    cd `dirname "$progname"`
    progname=`/bin/ls -l "$bn" | sed -e 's/^.* -> //' `
    if [ ! -x "$progname" ]; then
      break
    fi
    curdir=`dirname "$progname"`
    run_moz="$curdir/run-mozilla.sh"
    if [ -x "$run_moz" ]; then
      cd "$curdir"
      dist_bin=`pwd`
      found=1
      break
    fi
  done
  cd "$here"
fi
if [ $found = 0 ]; then
  # Check default compile-time libdir
  if [ -x "$moz_libdir/run-mozilla.sh" ]; then
    dist_bin="$moz_libdir"
  else 
    echo "Cannot find mozilla runtime directory. Exiting."
    exit 1
  fi
fi

script_args=""
debugging=0
MOZILLA_BIN="${progbase}-bin"

if [ "$OSTYPE" = "beos" ]; then
  mimeset -F "$MOZILLA_BIN"
fi

pass_arg_count=0
while [ $# -gt $pass_arg_count ]
do
  case "$1" in
    -p | --pure | -pure)
      MOZILLA_BIN="${MOZILLA_BIN}.pure"
      shift
      ;;
    -g | --debug)
      script_args="$script_args -g"
      debugging=1
      shift
      ;;
    -d | --debugger)
      script_args="$script_args -d $2"
      shift 2
      ;;
    *)
      # Move the unrecognized argument to the end of the list.
      arg="$1"
      shift
      set -- "$@" "$arg"
      pass_arg_count=`expr $pass_arg_count + 1`
      ;;
  esac
done

export MRE_HOME

## Start addon scripts
moz_pis_startstop_scripts "start"

if [ $debugging = 1 ]
then
  echo $dist_bin/run-mozilla.sh $script_args $dist_bin/$MOZILLA_BIN "$@"
fi
"$dist_bin/run-mozilla.sh" $script_args "$dist_bin/$MOZILLA_BIN" "$@"
exitcode=$?

## Stop addon scripts
moz_pis_startstop_scripts "stop"

exit $exitcode
# EOF.


:-k 

Sorry for the delay

xx75

---

### Post by andrewsawyer on 2006-02-24
Hmmm... well, it looks like this actually configures variables and what not each time you load thunderbird.  For this reason I'm not sure that running mozilla-thunderbird directly would work.

With a standard Thunderbird 1.0.7 or whatever that comes with Breezy, you should just be able to run mozilla-thunderbird, however you are getting errors when doing this with 1.5, because a whole load of stuff needs to be set on the system before Thunderbird 1.5 can run.  This is why you run the script to get Thunderbird working.

You should be able to use smeg to change the link to Thunderbird to point to the shell script, and to get Thunderbird to run from Terminal, try ./<script.sh>, replacing <script.sh> with the name of the script. Basically just type ./ before it.

I hope this helps.

---

### Post by xx75 on 2006-02-24
Thanks mate, your bloods worth bottling!

It works fine now through the menu :D 

From terminal I needed to do this -
```

cd /opt/tunderbird
./thunderbird

```

I'm still unfamiliar with a lot of commands, there's probably a better way to do it but with my limited knowledge this is all I could figure out.

Anyway, it works a treat, so I am stoked!

I appreciate your time

Thanks a gazillion

xx75

---

