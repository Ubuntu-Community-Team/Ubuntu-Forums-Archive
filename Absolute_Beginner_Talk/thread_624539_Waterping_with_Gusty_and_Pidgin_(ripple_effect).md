---
title: "Waterping with Gusty and Pidgin (ripple effect)"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by zerofxC on 2007-11-27
Firstly i take no credit for the coding in this post.

After searching for weeks for a working how too i compiled my own how to from various posts arround the net. Hope it helps guys...

Open a new terminal

Create a new file called waterping.sh in /usr/local/bin/ using:

sudo gedit /usr/local/bin/waterping.sh

in the file paste:

[COLOR="Red"]#!/bin/bash 
#Panel layout - Top || Bottom || Left || Right 
LAYOUT="Top" 

if [ "x$1" == "x" ]; then 
echo "Please specify the icon name, f. ex. 'pidgin' as parameter 1"; 
exit 0 
fi 

WINFO=`xwininfo -root -tree -name "$LAYOUT Expanded Edge Panel"| grep "$1" | cut -d ')' -f 2-` 
WIW=`echo $WINFO | cut -d 'x' -f 1` 
WIH=`echo $WINFO | cut -d 'x' -f 2 | cut -d '+' -f 1` 
WIX=`echo $WINFO | cut -d '+' -f 4` 
WIY=`echo $WINFO | cut -d '+' -f 5` 
let WAX=WIX+WIW/2 
let WAY=WIY+WIH/2 

dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/point org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:'amplitude' double:1 string:'x' int32:$WAX string:'y' int32:$WAY
[/COLOR]
save the file and exit

Next you will need to change the permissions of waterping.sh and make it exicutable.

cd /usr/local/bin/   (if you are not already in the dir)

then

sudo chmod a+x waterping.sh

Next open pidgin and go to Preferences>Sounds and change the sound method to “command”.

Then paste:
 [COLOR="Red"]/usr/local/bin/waterping.sh pidgin[/COLOR] 
into “Sound Command”

You may need to change sound events to suit when you want the ripples to come.

Finally go to System>Preferences>Advanced Desktop Settings and enable the water plugin and the dBus plugin.

---

### Post by wheredidrealitygo on 2007-11-27
I'm SO testing this when I get home from work.

---

### Post by dfreer on 2007-12-14
Can we get a screenshot/screencast for this, or an explanation of what it does?

---

### Post by jordank on 2007-12-14
yeah, i'd love to know exactly what this is?
and a confirmation if it works?

---

### Post by wheredidrealitygo on 2007-12-14
I can confirm that it works (or did work, seems to not want to at the moment, so no screenshot unfortunately), basically what it does is instead of playing a sound every time that you receive a notification from pidgin, a ripple effect will spread outward from the top left corner of the screen above every window, down towards the middle of the screen. 

I find it to be a little too subtle.

One thing I noticed as well, it doesn't differentiate, it will do the same thing from someone signing on, to someone messaging you. I disabled it within a few days, I kept missing messages.

It definitely has potential though.

---

### Post by IgnacioMiller on 2007-12-14
Wow man, that's pretty sweet. Keep up the good work!

---

### Post by zerofxC on 2007-12-14
> **wheredidrealitygo said:**
> One thing I noticed as well, it doesn't differentiate, it will do the same thing from someone signing on, to someone messaging you. I disabled it within a few days, I kept missing messages.

It definitely has potential though.
Firstly, thanks for the feed back! if anyone has any tweeks for the code or anything that will help in its development it would be great! So, now onto the problem...

Its easily solved. 

In the Preferences>Sounds tab in pidgin there are some options (near the bottom) that tell pidgin which events to play sounds on... as pidgin is calling the script as a sound it will run the script every time an event happens. If that makes any sence.

Im not sure which ones i have selected but i have it so it runs the script every time someone sends an IM.

By trial and error you will be able to find which ones to de-select.

Oh and for people who want to see what it looks like have a look here 
[http://www.youtube.com/watch?v=-nI3tTctdM4]("http://www.youtube.com/watch?v=-nI3tTctdM4")

---

### Post by aswinms on 2007-12-20
> **wheredidrealitygo said:**
> 

One thing I noticed as well, it doesn't differentiate, it will do the same thing from someone signing on, to someone messaging you. I disabled it within a few days, I kept missing messages.

It definitely has potential though.


I tried it too, works fine... If only there was a way to enable this effect along with the default sound, there wouldn't be problems of missing mails.
:)

---

### Post by JillSwift on 2007-12-20
Could always throw an esdplay in there for sound.

---

### Post by pjones0404 on 2007-12-20
this installed perfectly.

a few things i would like to see. either a larger wave from the corner or a way to set it to the middle of the screen. I really like the fact that it is a different visual look but it is almost too subtle.

great work though.

---

### Post by zerofxC on 2007-12-20
> **pjones0404 said:**
>  a few things i would like to see. either a larger wave from the corner or a way to set it to the middle of the screen.

You can Use the xwininfo command. I'm not sure if you have to sudo xwininfo or not as i haven't got linux at work and can't test it

I think then you need to edit the line:
[COLOR="Red"]WINFO=`xwininfo -root -tree -name "$LAYOUT Expanded Edge Panel"| grep "$1" | cut -d ')' -f 2-` [/COLOR]
In you script file and replace the phrase "Expanded Edge Panel" with the result you get from xwininfo

You might need to edit the LAYOUT =
[COLOR="Red"]#!/bin/bash
#Panel layout - Top || Bottom || Left || Right
LAYOUT="Top" [/COLOR]

Im not to sure if this will work its just a rough guess, i can't really piece anything together with out linux infront of me.

Hope it helps anyway

Merry Christmas

---

### Post by pjones0404 on 2007-12-20
> **zerofxC said:**
> You can Use the xwininfo command. I'm not sure if you have to sudo xwininfo or not as i haven't got linux at work and can't test it

I think then you need to edit the line:
[COLOR="Red"]WINFO=`xwininfo -root -tree -name "$LAYOUT Expanded Edge Panel"| grep "$1" | cut -d ')' -f 2-` [/COLOR]
In you script file and replace the phrase "Expanded Edge Panel" with the result you get from xwininfo

You might need to edit the LAYOUT =
[COLOR="Red"]#!/bin/bash
#Panel layout - Top || Bottom || Left || Right
LAYOUT="Top" [/COLOR]

Im not to sure if this will work its just a rough guess, i can't really piece anything together with out linux infront of me.

Hope it helps anyway

Merry Christmas

thanks for the response.

i do not really understand the steps that u listed. i run the xwininfo command but am not sure what i need to copy into the script for the effect. If you or anyone else could provide a little more detail i would appreciate it.

---

### Post by zerofxC on 2007-12-20
Hi sorry, i was in the middle of a phone call at work when i was doing it.

If you post your response to xwininfo ill do my best to figure it out for you!

---

### Post by pjones0404 on 2007-12-21
when i run this command is ask to select a window. I dont know what one to select so i just choose the desktop. here is the output. let me know if it is something else that u need. 

xwininfo: Window id: 0xe0001f "Desktop"

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1280
  Height: 800
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1280x800+0+0


Thanks again for the help.

---

### Post by zerofxC on 2007-12-21
If you edit this bit first..... replacing the layout with "bottom" ...

[COLOR="Red"]#!/bin/bash
#Panel layout - Top || Bottom || Left || Right
LAYOUT="Bottom" 
[/COLOR]

Then replace LAYOUT Expanded Edge Panel with desktop like i have done below:

[COLOR="Red"]WINFO=`xwininfo -root -tree -name "$LAYOUT Desktop"| grep "$1" | cut -d ')' -f 2-`[/COLOR]

If this doesnt work i really don't know what to suggest but i'm almost certain its got something to do with this two bits of the scrip as they decide where the ripple appears.

I'll investigate more for you over christmas.

Thanks

---

### Post by pjones0404 on 2007-12-21
i tried the last instructions and there was no change to the effect. 

thanks for the response. i wait to see if this is something that can be changed.

---

### Post by MikeonTV on 2008-04-27
I'm getting no sound with it. works fine otherwise

---

### Post by zerofxC on 2008-04-28
You wont get any sound as you are replacing the sound command with a script...

So when pidgin would normaly play a sound it runs the script instead.

---

### Post by chickeninabiscuit on 2008-06-02
to play sounds with the effect just add this to the script:

```
sndfile-play %s
```

---

