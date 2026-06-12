---
title: "[SOLVED] connect / disconnect script for pppd"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by directcharitycontribution on 2007-04-15
Please help, how to modify this script, found via launchpad, to make launcher for adsl connection to use 'sudo killall pppd' for connect and 'sudo pppd call speedtch' for reconnect:

You can place the script anywhere you like, just make it executable. I placed it in /usr/local/bin,
#! /bin/sh
# Simple connect / disconnect script for ppp
# written by Jeffry Johnston, 2004
TITLE="Dial-up Connection"
ICON=/usr/share/icons/hicolor/48x48/apps/modem.png
ps ax | grep [/]pppd > /dev/null
if [ $? == 0 ] ; then
   zenity --question --text="Disconnect?" --title="$TITLE" --window-icon=$ICON
   if [ $? == 0 ] ; then
       poff
   fi
else
   zenity --question --text="Connect?" --title="$TITLE" --window-icon=$ICON
   if [ $? == 0 ] ; then
       pon
   fi
fi





unfriendly configuration is also discussed here at launchpad [http://www.google.co.uk/search?num=50&hl=en&safe=off&rlz=1B3GGGL_enGB212GB212&q=linux+pppoeconf+gui+&btnG=Search&meta=]("http://www.google.co.uk/search?num=50&hl=en&safe=off&rlz=1B3GGGL_enGB212GB212&q=linux+pppoeconf+gui+&btnG=Search&meta=")

---

### Post by paparucino on 2007-04-29
> **directcharitycontribution said:**
> Please help, how to modify this script, found via launchpad, to make launcher for adsl connection to use 'sudo killall pppd' for connect and 'sudo pppd call speedtch' for reconnect:

You can place the script anywhere you like, just make it executable. I placed it in /usr/local/bin,
#! /bin/sh
# Simple connect / disconnect script for ppp
# written by Jeffry Johnston, 2004
TITLE="Dial-up Connection"
ICON=/usr/share/icons/hicolor/48x48/apps/modem.png
ps ax | grep [/]pppd > /dev/null
if [ $? == 0 ] ; then
   zenity --question --text="Disconnect?" --title="$TITLE" --window-icon=$ICON
   if [ $? == 0 ] ; then
       poff
   fi
else
   zenity --question --text="Connect?" --title="$TITLE" --window-icon=$ICON
   if [ $? == 0 ] ; then
       pon
   fi
fi

The code is correct, the only problem you could encounter is you dont' have the image modem.png, but this is paltry, the script works even without that file.

To run it, change the permissions with following command

```

sudo chmod +x *<the name of the file>*

```

---

### Post by directcharitycontribution on 2008-02-20
will use app launcher applet with terminal command

---

