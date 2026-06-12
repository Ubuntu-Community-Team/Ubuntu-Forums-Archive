---
title: "Firefox Icon"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by bri_06 on 2006-09-20
I noticed that firefox doesn't have the 'fox/globe' icon or the 'fox/globe' image in the 'About Firefox'. Why is this and is there a way to change it?

I googled searched, but all I can find are icon programs for windows that you have to buy :rolleyes: . I did however come across this site ( [http://iconpacks.mozdev.org/packs/firefox2005.html](http://iconpacks.mozdev.org/packs/firefox2005.html) ) that has a very nice looking set. I did install it but nothing happened.

Thanks

---

### Post by slimdog360 on 2006-09-20
the ubuntu version of firefox is different so there are some patent issues. You can change it by downloading your own and then right click on the icon which you want to change-->configure or properites(something like that). There should be someting like "change icon" somewhere, Im using kde so its different then gnome.

---

### Post by Bree on 2006-09-20
[http://www.arsgeek.com/?p=320](http://www.arsgeek.com/?p=320)

here's a script to restore the original Firefox icons.

---

### Post by charles.g.moore on 2006-09-20
look over here tell me if it helped...
[http://www.ubuntuforums.org/showthread.php?t=261234](http://www.ubuntuforums.org/showthread.php?t=261234)

---

### Post by bri_06 on 2006-09-20
Bree.. I don't know how to do that, its all alien to me. Maybe if the site was more detailed I would understand it.

charles.g.moore.. I'm in the same lost boat as 'Monstroxus' is. More details in 'Step-By-Step' form would be nice.



I'm just a win user since 98, not a fancy coder. I only started using linux/ubuntu just a few days ago.

Thanks

---

### Post by Poeffie on 2006-09-20
It doesnt work for me, the .xpi package isnt valid :s

---

### Post by furste on 2006-09-20
> **bri_06 said:**
> Bree.. I don't know how to do that, its all alien to me. Maybe if the site was more detailed I would understand it.

charles.g.moore.. I'm in the same lost boat as 'Monstroxus' is. More details in 'Step-By-Step' form would be nice.



I'm just a win user since 98, not a fancy coder. I only started using linux/ubuntu just a few days ago.

Thanks

it's really very simple to follow the instructions for restoring mozilla icons, and i'm in the same windows-vet, linux-newbie boat as you.

in order to follow the website, go to the applications at the top-left corner of the screen in ubuntu. click 'accessories' and then 'terminal'. there, copy this:

```
sudo gedit /usr/local/bin/restore_mozilla_icons
```

and paste it (you'll have to use ctrl+shift+v in terminal, frustrating, i know) into the terminal window. press enter. enter your password (you can't see what you type, frustrating, i know).

a notepad-esque window should open.

copy and paste this into it:

```
#! /bin/sh

#
# Restore the original Firefox and/or Thunderbird icons.
#

#
# TODO: Create and implement SVG icons
#

FIREFOX_LIB="/usr/lib/firefox/"
FIREFOX_BIN="/usr/bin/mozilla-firefox"
THUNDERBIRD_BIN="/usr/bin/mozilla-thunderbird"

ICON_PACK_URL="http://ubuntu.globalvision.ch/mozilla_icons_dapper.tar.bz2"
ICON_PACK_FILENAME="mozilla_icons_dapper.tar.bz2"
TMP_DIR="/tmp/moz-icons"$$"/"

#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
echo -e "nAborted by user."
rm -rf $TMP_DIR
exit 2
}

#Input read function
readyn()
{
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
echo 1
return
fi
echo 0
}

#Check if run as root
if [ "$UID" -ne 0 ] ; then
echo "You must be root to do that!"
exit 1
fi

#Ask which icons to replace
replace_ff="0"
replace_ff_doc="0"
replace_tb="0"
replace_tb_pm="0"

if [ -x "$FIREFOX_BIN" ] ; then
#Firefox
echo -n "Replace the Mozilla Firefox program icon (y/n)? [y] "
if [ `readyn` -ne 0 ] ; then
replace_ff="1"
fi

#Firefox document
echo -n "Replace the Mozilla Firefox document icon (y/n)? [y] "
if [ `readyn` -ne 0 ] ; then
replace_ff_doc="1"
fi
fi

if [ -x "$THUNDERBIRD_BIN" ] ; then
#Thunderbird
echo -n "Replace the Mozilla Thunderbird program icon (y/n)? [y] "
if [ `readyn` -ne 0 ] ; then
replace_tb="1"
fi

#Thunderbird profile manager
echo -n "Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] "
if [ `readyn` -ne 0 ] ; then
replace_tb_pm="1"
fi
fi

if [ "$replace_ff" -eq "0" ] && [ "$replace_ff_doc" -eq "0" ] && [ "$replace_tb" -eq "0" ] && [ "$replace_tb_pm" -eq "0" ] ; then
echo "Nothing to do here."
exit 0
fi

#Ask for divert the original packaged files to alternate locations
divert="0"

echo -e "nDo you want to divert the original packaged files to alternate locations"
echo -n "(make the changes permanent) (y/n)? [y] "
if [ `readyn` -ne 0 ] ; then
divert="1"
fi

#Downloading
echo -en "nDownloading and replacing icons. Please wait..."

mkdir $TMP_DIR
wget $ICON_PACK_URL -O $TMP_DIR$ICON_PACK_FILENAME >/dev/null 2>&1
if [ ! -f $TMP_DIR$ICON_PACK_FILENAME ] ; then
echo -e "nCannot download icons. Please check your internet connection."
rm -rf $TMP_DIR
exit 1
fi
tar xjf $TMP_DIR$ICON_PACK_FILENAME -C $TMP_DIR

#Replace Firefox icon
if [ "$replace_ff" -gt "0" ] ; then
if [ ! -f $TMP_DIR"mozilla-firefox.png" ] || [ ! -f $TMP_DIR"mozilla-firefox.xpm" ] ; then
echo "Cannot continue (unavailable Firefox icon file)"
rm -rf $TMP_DIR
exit 1
fi

#Backup
cp -f /usr/share/pixmaps/firefox.png /usr/share/pixmaps/firefox.old.png
cp -f /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm
cp -f $FIREFOX_LIB"icons/default.xpm" $FIREFOX_LIB"icons/default.old.xpm"
cp -f $FIREFOX_LIB"chrome/icons/default/default.xpm" $FIREFOX_LIB"chrome/icons/default/default.old.xpm"

#Divert
if [ "$divert" -gt "0" ] ; then
dpkg-divert --rename /usr/share/pixmaps/firefox.png >/dev/null
dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null
dpkg-divert --rename $FIREFOX_LIB"icons/default.xpm" >/dev/null
dpkg-divert --rename $FIREFOX_LIB"chrome/icons/default/default.xpm" >/dev/null
fi

#Replace icons
cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/firefox.png
cp $TMP_DIR"mozilla-firefox.xpm" /usr/share/pixmaps/mozilla-firefox.xpm
cp $TMP_DIR"mozilla-firefox.xpm" $FIREFOX_LIB"icons/default.xpm"
cp $TMP_DIR"mozilla-firefox.xpm" $FIREFOX_LIB"chrome/icons/default/default.xpm"
echo -n "."
fi

#Replace Firefox document icon
if [ "$replace_ff_doc" -gt "0" ] ; then
if [ ! -f $TMP_DIR"mozilla-firefox-doc.png" ] ; then
echo "Cannot continue (unavailable Firefox document icon file)"
rm -rf $TMP_DIR
exit 1
fi

#Backup
cp -f $FIREFOX_LIB"icons/document.png" $FIREFOX_LIB"icons/document.old.png"

#Divert
if [ "$divert" -gt "0" ] ; then
dpkg-divert --rename $FIREFOX_LIB"icons/document.png" >/dev/null
fi

#Replace icons
cp $TMP_DIR"mozilla-firefox-doc.png" $FIREFOX_LIB"icons/document.png"
echo -n "."
fi

#Replace Thunderbird icon
if [ "$replace_tb" -gt "0" ] ; then
#TODO: if [ ! -f $TMP_DIR"mozilla-thunderbird.png" ] || [ ! -f $TMP_DIR"mozilla-thunderbird.svg" ] || [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
if [ ! -f $TMP_DIR"mozilla-thunderbird.png" ] || [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
echo "Cannot continue (unavailable Thunderbird icon file)"
rm -rf $TMP_DIR
exit 1
fi

#Backup
cp -f /usr/share/pixmaps/mozilla-thunderbird.png /usr/share/pixmaps/mozilla-thunderbird.old.png
#TODO: cp -f /usr/share/pixmaps/mozilla-thunderbird.svg /usr/share/pixmaps/mozilla-thunderbird.old.svg
cp -f /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm
cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.png /usr/share/pixmaps/mozilla-thunderbird-menu.old.png
#TODO: cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.svg /usr/share/pixmaps/mozilla-thunderbird-menu.old.svg
cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm
cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm
cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm
cp -f /usr/lib/mozilla-thunderbird/icons/default.xpm /usr/lib/mozilla-thunderbird/icons/default.old.xpm
cp -f /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm /usr/lib/mozilla-thunderbird/icons/mozicon16.old.xpm
cp -f /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm /usr/lib/mozilla-thunderbird/icons/mozicon50.old.xpm

#Divert
if [ "$divert" -gt "0" ] ; then
dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.png >/dev/null
#TODO: dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.svg >/dev/null
dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null
dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.png >/dev/null
#TODO: dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.svg >/dev/null
dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null
dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null
dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null
dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/default.xpm >/dev/null
dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm >/dev/null
dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm >/dev/null
fi

#Replace icons
cp $TMP_DIR"mozilla-thunderbird.png" /usr/share/pixmaps/mozilla-thunderbird.png
#TODO: cp $TMP_DIR"mozilla-thunderbird.svg" /usr/share/pixmaps/mozilla-thunderbird.svg
cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird.xpm
cp $TMP_DIR"mozilla-thunderbird.png" /usr/share/pixmaps/mozilla-thunderbird-menu.png
#TODO: cp $TMP_DIR"mozilla-thunderbird.svg" /usr/share/pixmaps/mozilla-thunderbird-menu.svg
cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/icons/default.xpm
cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm
cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm
echo -n "."
fi

#Replace Thunderbird profile manager icon
if [ "$replace_tb_pm" -gt "0" ] ; then
#TODO: if [ ! -f $TMP_DIR"mozilla-thunderbird-pm.png" ] || [ ! -f $TMP_DIR"mozilla-thunderbird-pm.svg" ] || [ ! -f $TMP_DIR"mozilla-thunderbird-pm.xpm" ] ; then
if [ ! -f $TMP_DIR"mozilla-thunderbird-pm.png" ] || [ ! -f $TMP_DIR"mozilla-thunderbird-pm.xpm" ] ; then
echo "Cannot continue (unavailable Thunderbird icon file)"
rm -rf $TMP_DIR
exit 1
fi

#Backup
cp -f /usr/share/pixmaps/mozilla-thunderbird-pm.png /usr/share/pixmaps/mozilla-thunderbird-pm.old.png
#TODO: cp -f /usr/share/pixmaps/mozilla-thunderbird-pm.svg /usr/share/pixmaps/mozilla-thunderbird-pm.old.svg
cp -f /usr/share/pixmaps/mozilla-thunderbird-pm.xpm /usr/share/pixmaps/mozilla-thunderbird-pm.old.xpm
cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.png
#TODO: cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.svg /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.svg
cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm

#Divert
if [ "$divert" -gt "0" ] ; then
dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm.png >/dev/null
#TODO: dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm.svg >/dev/null
dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm.xpm >/dev/null
dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png >/dev/null
#TODO: dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.svg >/dev/null
dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null
fi

#Replace icons
cp $TMP_DIR"mozilla-thunderbird-pm.png" /usr/share/pixmaps/mozilla-thunderbird-pm.png
#TODO: cp $TMP_DIR"mozilla-thunderbird-pm.svg" /usr/share/pixmaps/mozilla-thunderbird-pm.svg
cp $TMP_DIR"mozilla-thunderbird-pm.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm.xpm
cp $TMP_DIR"mozilla-thunderbird-pm.png" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png
#TODO: cp $TMP_DIR"mozilla-thunderbird-pm.svg" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.svg
cp $TMP_DIR"mozilla-thunderbird-pm.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm
echo -n "."
fi

echo " done !"

#Reload gnome-panel
echo -en "nShall I reload gnome-panel to apply the changes (y/n)? [y] "
if [ `readyn` -ne 0 ] ; then
killall gnome-panel
fi

rm -rf $TMP_DIR
exit 0
```

next, save the notepad-esque file.

then, go back to the terminal window. type this:

```

sudo chmod +x /usr/local/bin/restore_mozilla_icons
```

enter your password.

finally, type this into the terminal window:

```
sudo restore_mozilla_icons
```

and follow the directions that pop up.


good luck!

---

### Post by Poeffie on 2006-09-20
Thanks, it worked without any problem for me!

And can you do the trick with that nifty looking icon package too?

---

### Post by Bree on 2006-09-20
> **bri_06 said:**
> Bree.. I don't know how to do that, its all alien to me. Maybe if the site was more detailed I would understand it.

My apologies, I should have been clear. furste's post explains the site's instructions perfectly, though. :)

---

### Post by bri_06 on 2006-09-20
It Worked! :D 

furste.. Thanks for explaining it 'Step-By-Step'. I like that.

Thanks All

---

### Post by deadgobby on 2006-10-13
That work and nice!!!! :p :D :mrgreen:

---

