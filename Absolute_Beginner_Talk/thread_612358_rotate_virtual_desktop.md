---
title: "rotate virtual desktop"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-11-13
I was wondring how to rotate a virtual desktop.  I know wmctrl does not work for rotating virtual desktop.  I was wondering if there was a program or some script that would rotate a virtual desktop.  Thanks

---

### Post by Dr Small on 2007-11-13
> **endlessurf said:**
> I was wondring how to rotate a virtual desktop.  I know wmctrl does not work for rotating virtual desktop.  I was wondering if there was a program or some script that would rotate a virtual desktop.  Thanks
What exactly are you using for your 'virtual desktop', VirtualBox ?

---

### Post by endlessurf on 2007-11-13
under compiz setting, there are two options.  one is virtual desktop and the other is number of desktop.  I can rotate to any number of desktops but I was wondering if there was a way to rotate virtual desktops from the comand line

---

### Post by jordanmthomas on 2007-11-13
You can do it with dbus.
You can search for how to do it yourself or give me a little bit and I can see if I can find how.

---

### Post by endlessurf on 2007-11-13
thanks for the reply jordanmthomas.  I have been looking for this for awhile now.

---

### Post by jordanmthomas on 2007-11-13
Well, my dbus is refusing connections for some reason, so I can't test it, but I did find this link:
[http://forum.beryl-project.org/viewtopic.php?t=4093](http://forum.beryl-project.org/viewtopic.php?t=4093)
It's from back in the beryl days but it still works the same.

Put this in a file (rotate.sh, for example)
```
#!/bin/bash
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/[COLOR="Red"]$1[/COLOR]/allscreens/[COLOR="#ff0000"]$2[/COLOR] org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` $3 $4 $5 $6 $7 $8 $9
```
make it executable
```
chmod +x rotate.sh
```
and run it like so:
```
./rotate.sh rotate rotate_right
```
What this does is sort of hard to explain, especially since I'm only vaguely familiar with it, but I'll give it a go.
Alright, here goes:

See the $1 and $2 in the script?  When you run the script, this is the first and second argument, respectively (rotate, rotate_right)
Each plugin in compiz can be accessed by sending a certain "location" through dbus
```
[COLOR="Navy"]org.freedesktop.compiz /org/freedesktop/compiz[/COLOR]/[COLOR="Red"]$1[/COLOR]/allscreens/[COLOR="SeaGreen"]$2[/COLOR] [COLOR="Purple"]org.freedesktop.compiz.activate[/COLOR] 
```
Ok, now what does all this mean?
The Navy-colored part is the "base location" for compiz as dbus sees it.
Next, is the red $1.  This is the plugin you wish to access (rotate in this case)
Next, is allscreens, which means what you think it does
The green $2 is the part of plugin $1 you'd like to access
After that is what you'd actually like to DO (activate the rotate_right part of the rotate plugin)

Like I said, I can't confirm this even works right now, but it should.

More information (not really too useful for what you're wanting to do though)
[http://compiz.org/Scripting_Compiz](http://compiz.org/Scripting_Compiz)

Hope this helps.  If not, compiz has forums at [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/) and I'd sure you'd be able to get great help there.

**edit**
I hope you were asking how to rotate the cube with a script and not change the number of desktops you have with a script.

---

### Post by endlessurf on 2007-11-14
we're not worthy, we're not worthy


Thanks for the info,  I have been looking for this for awhile.  I'll have to look into dbus more now that i have an idea what it does.  I'll try the script that you gave me and let you know.

thanks again

---

### Post by endlessurf on 2007-11-14
oh so sweet, thanks so much.

---

### Post by jordanmthomas on 2007-11-14
I take it it worked?

..I wish it worked for me.  :)

---

### Post by endlessurf on 2007-11-14
thanks so much again,  the chmod did not work for me, I had to right click and enable it that way.  then in terminal change directories to my desktop and run ./rotate ect......   

for anyone else that reads this and is interested they can go into the file
/usr/share/compiz/rotate.xml
to find different rotation options to use.


thanks a million

---

### Post by endlessurf on 2007-11-14
I guess my last question would be how to run one file to make it all rotate.

---

### Post by endlessurf on 2007-11-14
#!/bin/bash
cd /home/endlessurf/Desktop   # location of where ever you had put your rotate.sh


./rotate.sh rotate rotate_right

---

### Post by jordanmthomas on 2007-11-14
Another way that you might like would be to make two separate scripts, one for left and one for right by hardcoding it in the script:

make a file called rotate_left
```
#!/bin/bash
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/[COLOR="#ff0000"]rotate[/COLOR]/allscreens/[COLOR="Red"]rotate_left[/COLOR] org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` $3 $4 $5 $6 $7 $8 $9
```

make a file called rotate_right
```
#!/bin/bash
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/[COLOR="#ff0000"]rotate[/COLOR]/allscreens/[COLOR="Red"]rotate_right[/COLOR] org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` $3 $4 $5 $6 $7 $8 $9
```

(make them executable, of course)

Then, you could copy them somewhere in your executable path (/usr/local/bin is probably where I'd put them)
```
sudo cp ~/Desktop/rotate_left /usr/local/bin
sudo cp ~/Desktop/rotate_right /usr/local/bin

```

Then, you can run rotate_left or rotate_right from anywhere without worrying where the script is (maybe you could put some cool buttons on your panel for rotating or something).
```
rotate_left
``` would rotate left

---

### Post by endlessurf on 2007-11-14
so jordanmthomas my last question for you would be....in my car pc  I have two options.  1) us wmctrl to rotate desktops and have the flames burn up the screen to rotate from mythtv to say gps/musc/whatever or 2) run the scipt and have the cube be zoomed out then rotated to the correct gps/music/whatever....????

---

### Post by jordanmthomas on 2007-11-14
I'm not sure I understand your question?

---

### Post by endlessurf on 2007-11-14
i am running myth tv in my car and have been using wmctrl to rotate to a different desktop.    When I do this compiz "burns" the window down revealing the next desktop underneath.  Where if I use the script, it will rotate the cube to a different virtual desktop.  I was just wondering about your opinion.

---

### Post by jordanmthomas on 2007-11-14
Ah, I see.
For me it would depend on how fluidly the burn burns.  On my computer, a fullscreen burn is a little slow, so I'd go with the cube.

If the fire is fast on your computer, I'd go with it for coolness factor.

---

