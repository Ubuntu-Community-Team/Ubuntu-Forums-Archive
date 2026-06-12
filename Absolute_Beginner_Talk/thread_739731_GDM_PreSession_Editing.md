---
title: "GDM PreSession Editing?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by SaikoRonin on 2008-03-30
I recently installed a gdm theme and a splash and got that working nicely.  However I noticed the Tan color popping up before and after the splash.

I looked at other posts and found a way to minimize this annoyance, 

Going into /etc/gdm/PreSession/Default 

Then changing the hex value for the backcolor from #dab082 to #000000(black)
```

	# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#dab082"
 	fi
```

Now Im kind of new to ubuntu and I cannot program at all, and this is where I need help.

I would like to change the backcolor to an image file, and basically extend the splash screen so that you would never see the plain "color" screen at all.

It should be a simple code to do that,  However if we wanted to get technical with it we could figure out a way to actually pull the file location of the users splash screen image and put it right into the code so that less tech savvy people wouldnt have to go into the file to edit it.  And this could be an update, or it would save us from having to edit the file every time we change splash screens.

Im sure a lot of people would find this bit of code useful, and if I knew any coding Id write it myself.

---l- Ronin

---

### Post by c-ron on 2008-03-30
/etc/gdm/PreSession/Default lets you choose the background color, not specify an image.

---

### Post by c-ron on 2008-03-30
/etc/gdm/PreSession/Default lets you choose the background color, not specify an image.

One suggestion would be to use your GDM theme's background color (and if that fails, default to black):

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
if [ "x$XSETROOT" != "x" ] ; then

	CHECKBACKCOLOR="OK"
	if [ "x$GDM_GREETER_TYPE" = "xTHEMED" ]; then
		BACKCOLOR=`gdmflexiserver -a --command="GET_CONFIG greeter/GraphicalThemedColor $DISPLAY"`

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
		BACKTYPE=`gdmflexiserver -a --command="GET_CONFIG greeter/BackgroundType $DISPLAY"`

		# Skip if background type does not include a color
		if [ "x$BACKTYPE" = "xOK 1" ] || [ "x$BACKTYPE" = "xOK 2" ]; then
			BACKCOLOR=`gdmflexiserver -a --command="GET_CONFIG greeter/BackgroundColor $DISPLAY"`

			CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
			if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
				BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
			else
				BACKCOLOR=""
			fi
		fi
	fi
  
	# Default value
	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#000000"
 	fi

	"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

exit 0

exit 0

```

---

### Post by SaikoRonin on 2008-03-30
[http://ubuntuforums.org/showthread.php?p=4616734#post4616734]("http://ubuntuforums.org/showthread.php?p=4616734#post4616734")

I posted the question in the programming section.  I guess im not looking for a simple quick fix.   A moderator can close this.  I already changed the color to black, I was looking for a way to change the actually coding and get rid of the presession using a back color at all at that time but instead extending the splash screen, it would make the whole boot up look a   lot smoother.

---

### Post by AlistairH on 2008-03-30
Do what I did... rename the /etc/gdm/PreSession/Default file.

If your gdm background is the same as your desktop background you'll go straight to your desktop in a beautifully smooth transition.

---

