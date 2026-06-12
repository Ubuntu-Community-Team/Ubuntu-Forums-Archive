---
title: "Downloaded Firefox 1.5.0.7...what now?"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-09-15
I dl-ed Firefox 1.5.0.7 for linux from [http://www.mozilla.com/products/download.html?product=firefox-1.5.0.7&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-1.5.0.7&os=linux&lang=en-US)
and the 'firefox-1.5.0.7.tar.gz' file is sitting on my desktop -I double -click it and it extracts to a folder on my desktop.  -So what do I do now? -Should I extract it anywhere else? -Will it automatically overwrite Firefox 1.5.0.5?
   -Thanks for any help.

---

### Post by LookTJ on 2006-09-15
i believe here, [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

I installed mine and it erased my extensions cause i didn't follow the instuctions correctly

---

### Post by Najand on 2006-09-15
Why you are in hurry? There would be some official updates of firefox in repositories soon. I don't think there is a big difference between 1.5.0.7 and 1.5.0.5

Anyway, if you are looking for some capacities which 1.5.0.7 has and 1.5.0.5 doesn't, I can help you install it. Can you tell me what  files are there in that archive file?

---

### Post by aysiu on 2006-09-15
You have three options.

1. You can **install it manually** by copying and pasting the commands from this tutorial:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

2. You can **install it automatically** using this script: ```
#!/bin/sh
echo "Updating repositories list
"
sudo apt-get update
echo "
Making sure libstdc++5 and the old Firefox are installed
"
sudo apt-get -y install firefox libstdc++5
echo "
Backing up old Firefox preferences
"
cp -R ~/.mozilla ~/.mozilla_backup
echo "
Changing to home directory
"
cd
echo "
Downloading Firefox from the Mozilla site
"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.7/linux-i686/en-US/firefox-1.5.0.7.tar.gz
echo "
Unzipping the .tar.gz file
"
sudo tar -C /opt -x -z -v -f firefox-1.5.0.7.tar.gz
echo "
Removing the unzipped .tar.gz
"
rm firefox-1.5.0.7.tar.gz
echo "
Linking plugins
"
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
echo "
Linking launcher to new Firefox
"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
echo "
The new Firefox is installed."
``` There used to be a more sophisticated script developed by a forum member named *nanotube*, but the site where it's hosted appears to be down.

In the terminal, type ```
nano -B installnewfirefox
``` and paste (Shift-Insert) in the script, then save the file (Control-X, Y, Enter) and ```
chmod +x installnewfirefox
./installnewfirefox
```

3. Just **wait a week for the Ubuntu repositories Firefox** to get updated.

---

### Post by LookTJ on 2006-09-15
here are some changes


MFSA 2006-64  Crashes with evidence of memory corruption (rv:1.8.0.7)
MFSA 2006-62 Popup-blocker cross-site scripting (XSS)
MFSA 2006-61 Frame spoofing using document.open()
MFSA 2006-60 RSA Signature Forgery
MFSA 2006-59 Concurrency-related vulnerability
MFSA 2006-58 Auto-Update compromise through DNS and SSL spoofing
MFSA 2006-57 JavaScript Regular Expression Heap Corruption

---

### Post by aysiu on 2006-09-15
Oh, I found *nanotube*'s script: ```
#!/bin/bash
#
# installnewfirefox.sh
#               Script to automatically download and install the newest firefox version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installnewfirefox.sh  1.9  22-Aug-2006  nanotube@users.sf.net
# 
#
#######

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

## Set version-specific variables
if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

## Get the newest firefox release version from mozilla website
VERSION=`wget -q -O - http://www.mozilla.com |grep "product=" -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//'`

echo -e -n "The most recent release of firefox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
LOCALIZATIONS=( `wget -q -O - http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/ | grep 'a href="' | grep -v "xpi" | grep -v "Name" | sed -e 's/<img.*href="//' | sed -e 's/<a.*href="//' | sed -e 's@/">.*@@'` )

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for firefox. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${LOCALIZATIONS[$i]}"
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

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
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

## Proceed to download and install firefox.

echo -e "\nUpdating repositories list\n"
sudo aptitude update

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo aptitude install firefox libstdc++5

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup_`date -Iseconds`
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz.asc

echo -e "\nImporting Mozilla Software Releases public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
gpg --verify firefox-$VERSION.tar.gz.asc firefox-$VERSION.tar.gz

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -xzf firefox-$VERSION.tar.gz

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s -f $PLUGINPATH/* .

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

echo -e "\nThe new Firefox version $VERSION has been installed successfully."

exit
```

---

### Post by fiver22 on 2006-09-15
So I can just wait and Ubuntu will automatically update Firefox? -It didn't do an update from FF 1.5.0.5 to 1.5.0.6?
Or will the update be available through some other means?
Thanks again for all the replies -*and* your patience with my newbie-ish questions.
 
> **Najand said:**
> Why you are in hurry? There would be some official updates of firefox in repositories soon. (...) 

---

### Post by deadgobby on 2006-09-15
The last time FF updated, Ubie had updated too. So when your update icon come poping up, it may have the update for FF.
Gobby

---

### Post by fiver22 on 2006-09-15
But I didn't get an update notification for FF 1.5.0.5 to 1.5.0.6 -I'm still running FF 1.5.0.5 and use the update feature whenever it prompts me -am I missing something, deadgobby?
-Again, I appreciate your time.

> **deadgobby said:**
> The last time FF updated, Ubie had updated too. So when your update icon come poping up, it may have the update for FF.
Gobby

---

### Post by pommattski on 2006-09-15
> **fiver22 said:**
> But I didn't get an update notification for FF 1.5.0.5 to 1.5.0.6 -I'm still running FF 1.5.0.5...
IIRC, 1.5.0.6 was an update which was particular to Windows (Media Player plugin, I think), and was not necessary for Linux, and so was not issued via the repositories.

I would expect an update notification for 1.5.0.7 within a few days though, if previous updates are anything to go by.

---

### Post by fiver22 on 2006-09-15
That seems to explain it -Thanks, pommattski.

> **pommattski said:**
> IIRC, 1.5.0.6 was an update which was particular to Windows (Media Player plugin, I think), and was not necessary for Linux, and so was not issued via the repositories.

I would expect an update notification for 1.5.0.7 within a few days though, if previous updates are anything to go by.

---

### Post by deadgobby on 2006-09-15
what the last post said. Just sit back and let the Ubie crew do their hard working mojo. It will up date soon. I just waiting for flash 9 to come out. Grrrr
Gobby

---

### Post by Najand on 2006-09-15
Hmm, I am waiting for a skype to come out for Linux  (PPC Architecture)

---

### Post by fiver22 on 2006-09-15
With you on that, deadgobby. -Did you hear about: [http://blogs.adobe.com/penguin.swf/2006/09/customizing_ubuntu_live_cd_606_1.html](http://blogs.adobe.com/penguin.swf/2006/09/customizing_ubuntu_live_cd_606_1.html)   ?

> **deadgobby said:**
> (...) I just waiting for flash 9 to come out. Grrrr
Gobby

---

### Post by DLWood on 2006-09-15
Which brings up another question........Who is responsible for updating the repositories?

As an example, I installed Ubuntu 6.06 from the Live CD 2 weeks ago and had a few updates to install the first time I booted Ubuntu.  I installed all of them then and have had several since then (currently up-to-date).  The **Ekiga** that is now installed is version 2.01.  If you visit the Ekiga website, the latest version is 2.03.  I'd rather use the Synaptic Manager to update software, but if it takes weeks or months to update the repositories, then that's not very good.

Is it the developer or an Ubuntu team that's responsible?

What is the usual time lag from revision issue to repository update?

---

### Post by Najand on 2006-09-15
The Packages you download from repositories, are packages which are made for the kernel and batches Ubuntu is using now. That is why it is always late, because there is always someone needed to make the packages/test them/debug them and fix the bugs before sending them to repositories... So it is better to be patient and wait for packages from repositories get ready.

---

