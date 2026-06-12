---
title: "xgl on widescreen display"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by mbstrlbstr on 2006-07-28
I installed XGL on my Insirion 8500 lappy recently and the image is distorted. The cube only reaches a square instead of filling the whole widescreen display. Also, there are no buttons on the taskbars. Any help would be appreciated.

---

### Post by shaunsagirl on 2006-07-28
You must likely just have to deal with it.

---

### Post by arsenic23 on 2006-07-28
I was going to sugest you try the Compiz forums...  but apparently you've already done that : )

[http://www.compiz.net/viewtopic.php?id=2268](http://www.compiz.net/viewtopic.php?id=2268)

---

### Post by MarkSheely on 2006-07-28
Interesting - I've got xgl/compiz running on my widescreen inspiron (an e1705) without that problem - 

What method did you use to setup xgl/compiz?  Which graphics card do you have in your laptop?

I think we can probably get to the bottom of this.

--Mark

---

### Post by mbstrlbstr on 2006-07-31
Sorry for the delay of posting. I appreciate the response. I used the installation found here
[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

I have an ati radion installed on the laptop.

Update, I reinstalled the ati driver, and xgl/compiz. Now when I load it up, the screen is fine, but there are no borders around windows, and no hotkeys work? What have I done? Can't change desktop screens by clicking on them either.

---

### Post by arsenic23 on 2006-07-31
Ok, I'm not going to read that entire tutorial cause I'm pressed for time.  But depending on what version of compiz your running you may need to switch from gnome-window-decorator to cgwd.  To test this make sure cgwd is installed and run cgwd from the terminal.  If this works then just replace gnome-window-decorator with cgwd in the script you put at /usr/bin/startcompiz .

What you should have now if you used the turorial you linked:
> #!/bin/sh 
killall gnome-window-decorator 
wait 

gnome-window-decorator & 
compiz --replace gconf &

What you should have afterward (I think):
> killall gnome-window-decorator 
wait 

cgwd & 
compiz --replace gconf &

I use a toggle script which looks like this:
> #!/bin/bash
if ps -A | grep -e "compiz.real$" > /dev/null; then
        killall cgwd
        metacity --replace &
else
        cgwd &
        compiz --replace gconf &
        xmodmap -e "keycode 22 = BackSpace Delete"
fi

I hope this helps a least a little.

---

### Post by MarkSheely on 2006-07-31
I had the same result when I used that method, and I'm using an nVidia card - no borders, no hotkeys, etc.  You'll want to try a different method. I have found this method to work well:

[http://ubuntuforums.org/showthread.php?t=222034](http://ubuntuforums.org/showthread.php?t=222034)

My suggestion: install the ati drivers the way you did previously, and then follow the tutorial above from the beginning to where he writes "Now we need to install and configure the Nvidia Glx drivers for Xorg...".  Then skip to where he writes "Now lets setup your gnome login to load Xgl instead of Xorg..." and follow along to the end.

I'd be very surpirsed if this didn't work like a charm.  Post back to let us know how things work out.

--Mark

---

