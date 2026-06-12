---
title: "Welcome to the 10 Millionth noob post about scripts!"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Lotekx on 2008-01-12
I am trying to install jukebox3d to use with exaile and I am pretty sure I have to do some magic with this script. I can't figure out how, after reading the info file, the manual, and lurking for around an hour. 

```
#!/bin/bash
COMMAND="$1"
case "$COMMAND" in
	query)
		TRACK_TITLE=$(dbus-send --dest=org.exaile.DBusInterface --print-reply /DBusInterfaceObject org.exaile.DBusInterface.get_title | sed -rn -e 's/^\s*string\s*"([^"]*)"\s*$/\1/ p')
		[ "$TRACK_TITLE" ] || exit
		TRACK_ARTIST=$(dbus-send --dest=org.exaile.DBusInterface --print-reply /DBusInterfaceObject org.exaile.DBusInterface.get_artist | sed -rn -e 's/^\s*string\s*"([^"]*)"\s*$/\1/ p')
		TRACK_ELAPSED=$(dbus-send --dest=org.exaile.DBusInterface --print-reply /DBusInterfaceObject org.exaile.DBusInterface.current_position | sed -rn -e 's/^\s*double\s*([0-9.]+)\s*$/\1/ p')
		TRACK_DURATION=$(dbus-send --dest=org.exaile.DBusInterface --print-reply /DBusInterfaceObject org.exaile.DBusInterface.get_length | sed -rn -e 's/^\s*string\s*"([^"]*)"\s*$/\1/ p')
		ALBUM_TITLE=$(dbus-send --dest=org.exaile.DBusInterface --print-reply /DBusInterfaceObject org.exaile.DBusInterface.get_album | sed -rn -e 's/^\s*string\s*"([^"]*)"\s*$/\1/ p')
		ALBUM_GENRE=$()
		ALBUM_YEAR=$()
		ALBUM_COVER=$(dbus-send --dest=org.exaile.DBusInterface --print-reply /DBusInterfaceObject org.exaile.DBusInterface.get_cover_path | sed -rn -e 's/^\s*string\s*"([^"]*)"\s*$/\1/ p')
		{
		echo "$ALBUM_COVER"
		echo "$ALBUM_TITLE"
		echo "$TRACK_ARTIST"
		echo "$TRACK_ELAPSED"
		echo "$ALBUM_GENRE"
		echo "$TRACK_TITLE"
		echo "$TRACK_DURATION"
		echo "$ALBUM_YEAR"
		}
		;;
	play)
		exaile -a
		;;
	next)
		exaile -n
		;;
	prev)
		exaile -p
		;;
	stop)
		exaile -s
		;;
	*)
		echo "Unknown command : $COMMAND" 1>&2
		;;
esac 
```


Thank you very much, and I apologize in advance for asking the same remedial redundant question everyone else does.

---

### Post by mattismyname on 2008-01-12
I could try to help, but what exactly are you trying to do?  What end result are you trying to achieve?

---

### Post by Lotekx on 2008-01-12
I am trying to get exaile to interface with jukebox3d. The installer gave me four scripts depending on what Media player I use, and I have to manually install the script. I thought by putting that file in my bin folder, jukebox would than have permission to interact with exaile.

---

### Post by Dr Small on 2008-01-12
Are you having problems executing it?
If so, give it e**x**ecutable permissions ;)
```
chmod +x nameofscript
```

Dr Small

---

