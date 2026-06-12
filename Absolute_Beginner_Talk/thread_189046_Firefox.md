---
title: "Firefox"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Aurdal on 2006-06-04
Hey, I''m sure this has been asked many times before, but I am lazy and can't be bothered searching for it. :p

But how can I install the latest version of Firefox?

---

### Post by xXx 0wn3d xXx on 2006-06-04
You could try the following:

1. Update an existing firefox install.

2. Download the latest firefox and put it in a folder and then run the firefox script.

3. Try aysiu's script

4. Automatix:

> wget [http://beerorkid.com/arnieboy/automatix_6.1-3_i386.deb](http://beerorkid.com/arnieboy/automatix_6.1-3_i386.deb)
sudo dpkg -i automatix_6.1-3_i386.deb

start it from Applications > System Tools > Automaitx. Then check firefox and hit "ok."

---

### Post by Aurdal on 2006-06-04
I'm on the 64bit version of breezer, so I don't think Automatix is an option...
So, what's this aysiu's script?

---

### Post by aysiu on 2006-06-04
[QUOTE=Aurdal]I'm on the 64bit version of breezer, so I don't think Automatix is an option...
So, what's this aysiu's script?[/QUOTE] It's no longer my script--it's nanotube's, and it's excellent:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

Unfortunately, it installs the x86 version of Firefox, not the AMD64 version. For AMD64, you'll probably need Swiftfox, which doesn't currently have a script.

**Edit**: I hacked together this script for installing the 64-bit Swiftfox, but since I don't have an AMD64 computer, I can't test it.

1. Download the attached text file to your desktop.
2. In a terminal paste these commands: ```
cd ~/Desktop
mv installswiftfox64.sh.txt installswiftfox64.sh
chmod +x installswiftfox64.sh
./installswiftfox64.sh
```

---

### Post by Aurdal on 2006-06-04
I'm kind of getting the feeling that the 32bit version is better... Should I just install the 32bit version of Ubuntu instead?

---

### Post by nanotube on 2006-06-04
[QUOTE=aysiu]It's no longer my script--it's nanotube's, and it's excellent:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

Unfortunately, it installs the x86 version of Firefox, not the AMD64 version. For AMD64, you'll probably need Swiftfox, which doesn't currently have a script.[/QUOTE]
speaking of 64bit firefox... it doesn't seem that mozilla's official servers have a 64bit version of firefox. so... anyone have a good idea of how to get the official firefox on a 64bit machine? because once i know how it's done, i could update the firefox install script and it would work for 64bit stuff too. (or just make a different script for 64bit).

---

### Post by nanotube on 2006-06-04
[QUOTE=Aurdal]I'm kind of getting the feeling that the 32bit version is better... Should I just install the 32bit version of Ubuntu instead?[/QUOTE]

if you just installed a fresh system, and are not losing much by making a fresh install, then - YES, you definitely should. at this point running 64bit is not for the fainthearted...

---

### Post by aysiu on 2006-06-04
[QUOTE=nanotube]because once i know how it's done, i could update the firefox install script and it would work for 64bit stuff too. (or just make a different script for 64bit).[/QUOTE] You could make a Swiftfox script. Many Swiftfox fans, including 64-bit users, would probably love you for it.

---

### Post by Aurdal on 2006-06-04
I think I'll just do that then, as I just installed it Friday, and I've been away the whole weekend, so everything I'll lose will be what I've done today, and that I can probably do much faster now that I've already done it once... :)

So, 32bit it is then. :)

---

### Post by nanotube on 2006-06-04
[QUOTE=aysiu]You could make a Swiftfox script. Many Swiftfox fans, including 64-bit users, would probably love you for it.[/QUOTE]
hmm, i will put it on my list, then :) after the exam.

---

### Post by _simon_ on 2006-06-05
You don't actually need an install script for swiftfox.... you just download and unzip and it will work from whereever you put the folder...

---

### Post by aysiu on 2006-06-05
[QUOTE=_simon_]You don't actually need an install script for swiftfox.... you just download and unzip and it will work from whereever you put the folder...[/QUOTE] You don't need one, but it sure helps.

If you just use the unzipped folder...

1. Plugins (like Flash) won't work in Swiftfox
2. The command *swiftfox* won't work, and the command *firefox* will just launch Firefox instead of Swiftfox
3. If it's placed in the /home/username folder, it may not be available for other users on the system to user

---

### Post by _simon_ on 2006-06-05
1. True but you can manually install plugins. Flash is simple - copy the plugins from your firefox directory and paste them into the plugins folder in swiftfox.

2. If you have an icon to launch it or menu item you can just edit it, ok so you're stuck if you use terminal :(

3. I didn't think of that - I'm the only user of this machine.

---

### Post by nanotube on 2006-06-05
[QUOTE=_simon_]1. True but you can manually install plugins. Flash is simple - copy the plugins from your firefox directory and paste them into the plugins folder in swiftfox.

2. If you have an icon to launch it or menu item you can just edit it, ok so you're stuck if you use terminal :(

3. I didn't think of that - I'm the only user of this machine.[/QUOTE]
well, and this stuff is exactly what the script would automate. :)

but at any rate... who can tell me if this "swiftfox" is really much faster on a normal x86 32 bit system? and if faster, how? faster rendering pages, faster starting up,...?

---

### Post by aysiu on 2006-06-05
[QUOTE=nanotube]well, and this stuff is exactly what the script would automate. :)

but at any rate... who can tell me if this "swiftfox" is really much faster on a normal x86 32 bit system? and if faster, how? faster rendering pages, faster starting up,...?[/QUOTE] I found it a little faster (maybe a fraction of a second per webpage) on my computer, but I think the appeal of a Swiftfox script would be for those with 64-bit systems, since the regular script installs the x86 version of Firefox.

---

### Post by nanotube on 2006-06-07
[QUOTE=aysiu]I found it a little faster (maybe a fraction of a second per webpage) on my computer, but I think the appeal of a Swiftfox script would be for those with 64-bit systems, since the regular script installs the x86 version of Firefox.[/QUOTE]
well... i took my stats exam today, which, as it happens, was the last exam i have to take, so i took the time and threw together the swiftfox install script. it is still basically using the firefox script framework, with some minor changes.

here is the script:

```

#!/bin/bash
#
# installswiftfox.sh
#               Script to automatically download and install the newest release version of swiftfox for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installswiftfox.sh  1.0  06-Jun-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Set version-specific variables
if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

## Get the newest swiftfox release version from getswiftfox.com
VERSION=`wget -q -O - http://getswiftfox.com/releases.htm |grep "<title>" |awk '{print $2}' |cut -d\< -f1`

echo -e -n "The most recent release of swiftfox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://getswiftfox.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on getswiftfox.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on getswiftfox.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
PROCESSORS=( `wget -q -O - http://getswiftfox.com/releases.htm |grep "href=\"rel-" | sed -e 's/.*href="rel-//' -e 's/\.htm.*//' |sort | uniq` )

LIMIT=${#PROCESSORS[*]}

## Get user choice of localization

echo "Please choose your processor architecture for swiftfox. Enter the number of your choice from the list below. If you are not sure which one fits your CPU, please check the list on http://getswiftfox.com/releases.htm"
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${PROCESSORS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen CPU architecture \"${PROCESSORS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install swiftfox.

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Swiftfox from the Swiftfox site\n"
wget -c http://getswiftfox.com/builds/releases/swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2
check_exit_status

echo -e "\nDownloading Swiftfox md5 sum from the Swiftfox site\n"
wget -c http://getswiftfox.com/builds/releases/md5sum-${PROCESSORS[$CHOICE]}
check_exit_status

echo -e "\nVerifying md5sum...\nIf the script terminates at this point, the download was corrupt, and you should delete the swiftfox downloads and run this script again.\n"
md5sum --check md5sum-${PROCESSORS[$CHOICE]} --status
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -j -v -f swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2 md5sum-${PROCESSORS[$CHOICE]}
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/swiftfox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking firefox launcher to Swiftfox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/swiftfox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/swiftfox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nSwiftfox version \"$VERSION\" for architecture \"${PROCESSORS[$CHOICE]}\" has been installed successfully."

exit

```

please feel free to give it a testing, and see if it works as advertised. i tested up to the part where it starts actually downloading swiftfox. everything else is pretty straightforward, so shouldn't be any errors.
once i get confirmation that it works, we can do the usual script linking thing, aysiu, if you feel up to it. :)

---

### Post by aysiu on 2006-06-07
You are fast, nanotube! Thanks for cooking that up. I'm sure many Swiftfox fans will appreciate it.

I can do some testing, but unfortunately I can't test for AMD64. I don't have a 64-bit processor. I'll try it for one of the other architectures, though.

---

### Post by nanotube on 2006-06-07
[QUOTE=aysiu]You are fast, nanotube! Thanks for cooking that up. I'm sure many Swiftfox fans will appreciate it.

I can do some testing, but unfortunately I can't test for AMD64. I don't have a 64-bit processor. I'll try it for one of the other architectures, though.[/QUOTE]
well, presumably, if it works for one, it will work for any of them, since any other is just a simple change of variable. so if it works for you on whatever architecture you choose, i'll take it as confirmation that it works. 

also, i'm not /that/ fast. it's easy when you have to build off an existing script. all i had to do is basically figure out how to parse the swiftfox page to get the latest version and the list of architectures, and then everything else plugged right in from our earlier installfirefox script, basically. ;)

---

### Post by aysiu on 2006-06-07
Well, maybe it's because I don't know anything about programming, but from an end-user's standpoint, it *seems* fast.

Apparently, the download part isn't working. I don't know if the script is querying the wrong address or if the Swiftfox site is down... ```
Downloading Swiftfox from the Swiftfox site

--17:05:01--  http://getswiftfox.com/builds/releases/swiftfox-1.5.0.4-celeron4.tar.bz2
           => `swiftfox-1.5.0.4-celeron4.tar.bz2'
Resolving getswiftfox.com... 208.113.157.188
Connecting to getswiftfox.com|208.113.157.188|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:05:02 ERROR 404: Not Found.

Previous command did not complete successfully. Exiting.
``` I tried Celeron 3 and Celeron 4.

---

### Post by nanotube on 2006-06-07
[QUOTE=aysiu]Well, maybe it's because I don't know anything about programming, but from an end-user's standpoint, it *seems* fast.

Apparently, the download part isn't working. I don't know if the script is querying the wrong address or if the Swiftfox site is down... ```
Downloading Swiftfox from the Swiftfox site

--17:05:01--  http://getswiftfox.com/builds/releases/swiftfox-1.5.0.4-celeron4.tar.bz2
           => `swiftfox-1.5.0.4-celeron4.tar.bz2'
Resolving getswiftfox.com... 208.113.157.188
Connecting to getswiftfox.com|208.113.157.188|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:05:02 ERROR 404: Not Found.

Previous command did not complete successfully. Exiting.
``` I tried Celeron 3 and Celeron 4.[/QUOTE]

aha, heh. well, turns out that this is due to the celeron3 and 4 links being just redirects to the pentium3 and 4. man, it's always things like that, when a site is not designed with a view to automatic processing :)
well, that was easy enough to fix - i just removed the celeron3 and celeron4 from list of available architectures, because they are not separate from the pentium3 and 4. it's lucky that you tested the celerons, since they had this unique problematic detail about them. 

here is the updated script:

```

#!/bin/bash
#
# installswiftfox.sh
#               Script to automatically download and install the newest release version of swiftfox for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installswiftfox.sh  1.0  06-Jun-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Set version-specific variables
if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

## Get the newest swiftfox release version from getswiftfox.com
VERSION=`wget -q -O - http://getswiftfox.com/releases.htm |grep "<title>" |awk '{print $2}' |cut -d\< -f1`

echo -e -n "The most recent release of swiftfox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://getswiftfox.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on getswiftfox.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on getswiftfox.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
PROCESSORS=( `wget -q -O - http://getswiftfox.com/releases.htm |grep "href=\"rel-" | sed -e 's/.*href="rel-//' -e 's/\.htm.*//' -e 's/celeron/pentium/' |sort | uniq` )

LIMIT=${#PROCESSORS[*]}

## Get user choice of localization

echo "Please choose your processor architecture for swiftfox. Enter the number of your choice from the list below. If you are not sure which one fits your CPU, please check the list on http://getswiftfox.com/releases.htm"
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${PROCESSORS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen CPU architecture \"${PROCESSORS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install swiftfox.

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Swiftfox from the Swiftfox site\n"
wget -c http://getswiftfox.com/builds/releases/swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2
check_exit_status

echo -e "\nDownloading Swiftfox md5 sum from the Swiftfox site\n"
wget -c http://getswiftfox.com/builds/releases/md5sum-${PROCESSORS[$CHOICE]}
check_exit_status

echo -e "\nVerifying md5sum...\nIf the script terminates at this point, the download was corrupt, and you should delete the swiftfox downloads and run this script again.\n"
md5sum --check md5sum-${PROCESSORS[$CHOICE]} --status
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -j -v -f swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2 md5sum-${PROCESSORS[$CHOICE]}
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/swiftfox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking firefox launcher to Swiftfox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/swiftfox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/swiftfox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nSwiftfox version \"$VERSION\" for architecture \"${PROCESSORS[$CHOICE]}\" has been installed successfully."

exit

```

please test again and see if that works.

---

### Post by aysiu on 2006-06-08
I'm still getting the same error.

The file it's trying to download is *swiftfox-1.5.0.4-celeron3.tar.bz2*.

**Edit**: The Pentium 3 download appears to be working, though.

Since I've tested so many times, though, a lot of the script doesn't work when its re-run. For example, I had to delete the .mozilla_backup folder. Also, the links to the plugins make the script exit: ```
Linking plugins

ln: creating symbolic link `./libunixprintplugin.so' to `/usr/lib/firefox/plugins/libunixprintplugin.so': File exists
```

---

### Post by nanotube on 2006-06-08
[QUOTE=aysiu]I'm still getting the same error.

The file it's trying to download is *swiftfox-1.5.0.4-celeron3.tar.bz2*.

**Edit**: The Pentium 3 download appears to be working, though.

Since I've tested so many times, though, a lot of the script doesn't work when its re-run. For example, I had to delete the .mozilla_backup folder. Also, the links to the plugins make the script exit: ```
Linking plugins

ln: creating symbolic link `./libunixprintplugin.so' to `/usr/lib/firefox/plugins/libunixprintplugin.so': File exists
```[/QUOTE]

heh, more good catches there aysiu. i have (i think) taken care of these problems. the ln command should no longer complain if destination file exists. the backup command will create a dated/timed backup file, so there should be no repeats (the downside being that it will generate multiple backups if run multiple times... but extra backups is not a bad thing, i'd say).

here is the new script. please test again :) note that it should no longer be attempting to download the celeron files (as they don't exist). if it does, let me know.

```

#!/bin/bash
#
# installswiftfox.sh
#               Script to automatically download and install the newest release version of swiftfox for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installswiftfox.sh  1.0  06-Jun-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Set version-specific variables
if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

## Get the newest swiftfox release version from getswiftfox.com
VERSION=`wget -q -O - http://getswiftfox.com/releases.htm |grep "<title>" |awk '{print $2}' |cut -d\< -f1`

echo -e -n "The most recent release of swiftfox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://getswiftfox.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on getswiftfox.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on getswiftfox.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
PROCESSORS=( `wget -q -O - http://getswiftfox.com/releases.htm |grep "href=\"rel-" | sed -e 's/.*href="rel-//' -e 's/\.htm.*//' -e 's/celeron/pentium/' |sort | uniq` )

LIMIT=${#PROCESSORS[*]}

## Get user choice of localization

echo "Please choose your processor architecture for swiftfox. Enter the number of your choice from the list below. If you are not sure which one fits your CPU, please check the list on http://getswiftfox.com/releases.htm"
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${PROCESSORS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen CPU architecture \"${PROCESSORS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install swiftfox.

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup_`date -Iseconds`
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Swiftfox from the Swiftfox site\n"
wget -c http://getswiftfox.com/builds/releases/swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2
check_exit_status

echo -e "\nDownloading Swiftfox md5 sum from the Swiftfox site\n"
wget -c http://getswiftfox.com/builds/releases/md5sum-${PROCESSORS[$CHOICE]}
check_exit_status

echo -e "\nVerifying md5sum...\nIf the script terminates at this point, the download was corrupt, and you should delete the swiftfox downloads and run this script again.\n"
md5sum --check md5sum-${PROCESSORS[$CHOICE]} --status
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -j -v -f swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f swiftfox-$VERSION-${PROCESSORS[$CHOICE]}.tar.bz2 md5sum-${PROCESSORS[$CHOICE]}
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/swiftfox/plugins/
sudo ln -s -f $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking firefox launcher to Swiftfox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/swiftfox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/swiftfox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nSwiftfox version \"$VERSION\" for architecture \"${PROCESSORS[$CHOICE]}\" has been installed successfully."

exit

```

---

### Post by aysiu on 2006-06-08
It worked flawlessly, nanotube. Where are you going to post the script?

---

### Post by nanotube on 2006-06-08
[QUOTE=aysiu]It worked flawlessly, nanotube. Where are you going to post the script?[/QUOTE]
i guess the usual, somewhere on my pykeylogger site.
here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)

---

### Post by aysiu on 2006-06-08
[QUOTE=nanotube]i guess the usual, somewhere on my pykeylogger site.
here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)[/QUOTE]  Linked to. Thanks again for all your hard work.

---

### Post by nanotube on 2006-06-08
[QUOTE=aysiu]Linked to. Thanks again for all your hard work.[/QUOTE]
you too :D

---

