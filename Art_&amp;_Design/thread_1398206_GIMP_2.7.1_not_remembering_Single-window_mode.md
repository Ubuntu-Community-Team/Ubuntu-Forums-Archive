---
title: "GIMP 2.7.1 not remembering Single-window mode"
date: 2010-02-04
forum: Art &amp; Design
---

### Post by Mustache Villain on 2010-02-04
Every time I close GIMP it forgets the Single-window setting and I have to choose it again. I know version 2.7.1 of GIMP is really unstable and buggy. I was just wondering if anyone else is having this issue and if anyone found a work around for this?

---

### Post by Psumi on 2010-02-04
Where IS that setting by the way, I want to try single-window mode.

Yes, I have the GIMP ppa version installed: 2.7.1

---

### Post by Mustache Villain on 2010-02-04
> **Psumi said:**
> Where IS that setting by the way, I want to try single-window mode.

Yes, I have the GIMP ppa version installed: 2.7.1

Goto: **Windows** > **Single-window mode**

---

### Post by Psumi on 2010-02-04
Opening recently closed docks/windows or the toolbox will crash gimp when in single-window mode, how nice. :(

---

### Post by Mustache Villain on 2010-02-04
It's been pretty stable for me, I grabbed it from this PPA:

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn")

I see an entry for "*(single-window-mode yes)*" in **~/..gimp-2.7/gimprc**, it just won't remember the Single-window mode setting after restart for some reason.

---

### Post by Psumi on 2010-02-04
> **Mustache Villain said:**
> It's been pretty stable for me, I grabbed it from this PPA:

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn")

I see an entry for "*(single-window-mode yes)*" in **~/..gimp-2.7/gimprc**, it just won't remember the Single-window mode setting after restart for some reason.

That's where I grabbed it from too.

---

### Post by Mustache Villain on 2010-02-04
I always try to remove old config files from the previous version of the software I'm upgrading. It might cure your crashing or it might not, give it a try.

---

### Post by 23dornot23d on 2010-02-04
Same problem ... GIMP 2.7.1 does not remember single window mode at the moment.
________________________________________________________
But since loading it from the same place as Psumi and yourself .... 

I have no crashing problems it used to lock up when leaving on my earlier version of it  ..... 

( but not now I only get script errors on the Script-Fu addons and FxFoundary )
Example ..... below ....
Plug-In "script-fu"
(/usr/local/lib/gimp/2.0/plug-ins/script-fu)
called deprecated procedure 'gimp-undo-push-group-start'.
It should call 'gimp-image-undo-group-start' instead!

The items I have done quick tests on in G'MIC seems to work ok though ....

Regular array
Faded array
Mirrored array
Image grid
Rotated tiles
Normalized tiles

( G'MIC - Everything in Arrays and Frames works for me .... still going through the list .....        )
( G'MIC - Everything in Artistic  works for me ..... this is just for info ... so people will know ..... )
Been through the full list in G'MIC ,,,, not had any problems .......



If you run GIMP from a 'Konsole' window .... it will/should show the reason why its crashing .........

[IMG]http://i47.tinypic.com/w6v1xh.jpg[/IMG]



Although it gives all the fatal errors at the beginning it still runs ..... and works .....
guess it just does not load in the relative items .....

---

### Post by leonardo_neo on 2010-02-18
I am experiencing the crashing problem too.

I am going to unstall this and install the previous version.

---

### Post by 23dornot23d on 2010-02-18
I quite like the options in both versions ,,,, single window is sometimes useful .....

But a lot of the script files crash for other things that I use ....

Therefore it would be nice to have two versions to run in the same desktop ......

I can do it at the moment by virtual box or swapping systems .... but I wondered if there was

a better way to do this .... 

( I once downloaded the git files into a opt directory ..... but it still complained to run the two in the same desktop ........ one after the other ..... 

(I don't need to run them together at the same time .... ) just to run individually one maybe now and the other for a different type of edit .....  )

until the scripts are sorted out 2.7.1 is only half functional really ....... for me ...... but I do like it. ......
its going to be excellent once completed ........ at 2.8 or 2.10 .....

---

### Post by hxcobd on 2010-02-20
Is single-window mode new in 2.7.0 or something? I don't see it in 2.6.7...

And the 2.7 install wouldn't even open for me, just sat at the opening screen for about 30 seconds and crashed over and over.

---

### Post by Sockerdrickan on 2010-02-20
> **hxcobd said:**
> Is single-window mode new in 2.7.0 or something?
Yes.

---

### Post by jdorenbush on 2010-09-14
I'm experiencing this problem too. Gimp remembers which docks are open, but it doesn't remember the dock positions/sizes or single window mode.

Anyone find a solution yet, or is this a known-bug?

---

### Post by BlazeFire247 on 2010-09-14
As far as I know, GIMP won't have the single-window mode run on startup yet. This might be a bug, because whenever I use single-window mode, close GIMP and open it again, the icon is ticked.

---

### Post by drBouvierLeduc on 2010-09-16
A developper is attempting to enable saving single-window mode in Gimp :
It doesn't seem to be an easy task, see for yourself :
[http://lightningismyname.blogspot.com/2010/06/progress-saving-single-window-mode.html](http://lightningismyname.blogspot.com/2010/06/progress-saving-single-window-mode.html)

---

### Post by kayosiii on 2010-09-17
Keep in mind that uses the old Linux versioning system.

major_version_number.minor_version_number.update_number

when minor version number is even its a stable version
when it is odd its a development version.

So don't expect everything to work.

Having said that I would really like to see this feature finished.

---

### Post by Billisnice on 2010-09-26
I am using 2.7.1 and have the same problem the single window does not keep after closing and reopening. 

I love a single window. I alway click around and loose focus of the multi window mode. Hopefully it will save keystrokes.

---

### Post by -Robert- on 2010-09-29
Try this: [http://www.omgubuntu.co.uk/2010/09/gimpbox-gives-stable-versions-of-the-gimp-single-window-mode/](http://www.omgubuntu.co.uk/2010/09/gimpbox-gives-stable-versions-of-the-gimp-single-window-mode/)

I tested it on GIMP 2.7.2 and it seems to work.

---

### Post by michaelmrose on 2011-11-08
How to make gimp open in single window mode automatically.

A) Install xdotool
B) define a hotkey in preferences to enter single window mode ex. super + w
C) Put the following script somewhere you can execute it
--------------------------------------------

#!/bin/sh
gimp &  
sleep 2
xdotool key super+w

-------------------------------------------

xdotool executes the key combo given to it, the & tells the script not to wait until gimp is finished to move on with the rest of the script and the sleep is in seconds.  

You may need to make the sleep longer if it takes longer to start gimp as gimp needs to be started before it receives the keypress.

---

### Post by prokoudine on 2011-11-15
> **michaelmrose said:**
> How to make gimp open in single window mode automatically.

Oh come on. Just install a newer dev version.

---

