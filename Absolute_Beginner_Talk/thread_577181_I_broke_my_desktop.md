---
title: "I broke my desktop"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2007-10-15
I just upgraded to Gutsy yesterday.  Jeez - what a hassle.  I had a lot of problems getting my FGLRX back online.  Basically it involved a lot of uninstalling and reinstalling.  But, eventually, I got it back the way I wanted it.

Problem 2: Compiz was CRAZY!  I had Compiz-Fusion before the upgrade, but I suppose some of the packages and plugins I had were incompatible with Gutsy's built-in version.  So, some repo-changing, and more uninstalling and reinstalling I had it back online.

Now to the problem at hand: I broke my desktop.  Has anyone else noticed that after the upgrade to Gutsy your initial login looks a little funky?  A big ugly brown screen, perhaps?  Maybe your login splash screen has gone missing (I haven't even tackled that issue yet)?  Well, I started on the brown screen.  I found that I was not alone, and that others users had complained of it.  So I read through this thread: [Fade to brown]("http://ubuntuforums.org/showthread.php?t=477704&highlight=fade+to+brown&page=2") and edited my /etc/gdm/PreSession/Default file accordingly.  This resulted in a missing desktop.

It's not that it's just black - which it is - but it doesn't even seem to be there.  For instance, clicking on it produces no results, whether it be with the right or left mouse button.  Also, my desktop icons have disappeared.

Does anyone out there know how to fix this?  Or, at least, can anyone post their /etc/gdm/PreSession/Default file here, so that I may compare it to this one?

```
#!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#
PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

# Set background color
XSETROOT=`gdmwhich xsetroot`
if [ "x$XSETROOT" != "x" ] ; then

	CHECKBACKCOLOR="OK"
	if [ "x$GDM_GREETER_TYPE" = "xTHEMED" ]; then
		BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/GraphicalThemedColor $DISPLAY"`

		CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
		if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
			BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
		else
			BACKCOLOR=""
		fi
	fi

	# If we tried to load the themed backgroundcolor, but failed, then try loading plain color
	if [ "x$CHECKBACKCOLOR" != "xOK" ] || [ "x$GDM_GREETER_TYPE" = "xPLAIN" ]; then

		# Background type can be 0=None, 1=Image & Color, 2=Color, or 3=Image 
		BACKTYPE=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundType $DISPLAY"`

		# Skip if background type does not include a color
		if [ "x$BACKTYPE" = "xOK 1" ] || [ "x$BACKTYPE" = "xOK 2" ]; then
			BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundColor $DISPLAY"`

			CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
			if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
				BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
			else
				BACKCOLOR=""
			fi
		fi
	fi

	Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#000000"
 	fi

	"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

exit 0
```

Thanks,

-Mike

---

### Post by mikeserv on 2007-10-16
Bump.

---

### Post by sayuki288 on 2007-10-16
sudo aptitude install ubuntu-desktop

---

