---
title: "Launcher not working"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by purebuilt on 2007-12-01
I can't get any Launchers to launch programs. I downloaded netscape navigator and unpacked the tar file into a /home/name/navigator directory but when I create the launcher to launch  /home/name/navigator/navigator it does not work.

Here's the folder contents:

```
:~/navigator$ ls
active-update.xml             libsoftokn3.chk
browserconfig.properties      libsoftokn3.so
chrome                        libssl3.so
components                    libxpcom_compat.so
defaults                      libxpcom_core.so
dictionaries                  libxpcom.so
extensions                    libxpistub.so
greprefs                      mozilla-xremote-client
icons                         navigator
install_flash_player_9_linux  navigator-bin
install.log                   old-homepage-default.properties
libfreebl3.chk                plugins
libfreebl3.so                 readme.txt
libmozjs.so                   removed-files
libnspr4.so                   res
libnss3.so                    run-mozilla.sh
libnssckbi.so                 searchplugins
libplc4.so                    updates
libplds4.so                   updates.xml
libsmime3.so                  xpicleanup

```

The launcher opens a script file:

```
#!/bin/sh
#
# ***** BEGIN LICENSE BLOCK *****
# Version: MPL 1.1/GPL 2.0/LGPL 2.1
#
# The contents of this file are subject to the Mozilla Public License Version
# 1.1 (the "License"); you may not use this file except in compliance with
# the License. You may obtain a copy of the License at
# http://www.mozilla.org/MPL/
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

## $Id: mozilla.in,v 1.12.8.1 2005/09/20 21:13:03 dbaron%dbaron.org Exp $
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
  MOZ_USER_DIR=".mozilla/navigator"
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

moz_libdir=/usr/lib/navigator-9.0.0.1
MRE_HOME=/usr/lib/mre/mre-9.0.0.1

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
      run_moz="$dist_bin/run-mozilla.sh"
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
```

I have gotten it working on another system but can't figure out why launchers don't work on my laptop running the same Ubuntu 7.10 system.
Not being able to set up a simple launcher that works is becoming a real problem and I really need some help or Ubuntu will just be useless for me.

Thanks.

DB

---

### Post by jken146 on 2007-12-01
If you want to run the script, you need to make it executable first. ```
chmod +X /home/name/navigator/navigator
```

---

### Post by purebuilt on 2007-12-01
I tried it. It did not work. What next? I admit I'm totally ignorant of Ubuntu but why is this so hard and why can't anyone tell me what to do just to run navigator on my system?

When you guys download software from a tar file how do *you* get set it up to run?

Thanks

DB

---

### Post by markharding557 on 2007-12-01
can you run the program from its executable? this way you will know whether it works and if it is only a launcher problem

---

### Post by purebuilt on 2007-12-01
As far as I know there is no exe file. Would the +X command have made one?

Is this just something that isn't done? Does everyone use the repositories?
I'd gladly pay someone to download the tar ball from netscape, extract it and then create a launcher and them me how it was done.
I even tried copying the director and launcher from the other computer where it is working and it does not work. Any ideas?

Obviously I need to do this, but I am not sure how. Just trying to learn here:

>  Tarballs often contain the source code of the program, and need to be compiled in order to be used.
[Note] 	

Compiling programs requires some packages that are not installed by default. You can install these all at once by installing the build-essential package.

DB

---

### Post by Aerin on 2007-12-03
Try running run-mozilla.sh It should show a dialog asking whether you want to display or run, click on run. 

If that doesn't work, you should make it executable by using: 
```
chmod +x run-mozilla.sh
```

---

