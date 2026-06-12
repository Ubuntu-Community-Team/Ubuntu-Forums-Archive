---
title: "Compiz"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by bondi007 on 2008-03-15
I have got a Lenovo R61i and when I install ubuntu 7.10 it all works fine and when I install all the packages for compiz I seem to get nothing when I set the cube and wobbly windows, no cube, no wobbly windows even tho I checked them,

Any help would be great 
Bondi :)

---

### Post by PurposeOfReason on 2008-03-15
What packages did you install? 7.10 comes with all, except for compiz-config, that you need. Also, please post what graphics card and driver you have.

---

### Post by bondi007 on 2008-03-15
compiz
compiz-bcop
compiz-core
compiz-dev
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
compizconfig-backend-gconf
compizconfig-settings-manager
emerald

and the graphics I think this is it but im not 100% sure if it for the graphics... GM965

Any Ideas 
Bondi

---

### Post by glennric on 2008-03-15
Did you enable desktop effects?  Go to System->Preferences->Appearances and click on the Desktop Effects tab.

---

### Post by bondi007 on 2008-03-15
doesnt let me choose custom desktop effects

any Ideas 
Bondi

---

### Post by bondi007 on 2008-03-15
Ive attached a screenshot by the way.

Bondi

---

### Post by v1cho on 2008-03-15
Run in terminal: 
```
compiz --replace
```
and post here the output ;)

---

### Post by bondi007 on 2008-03-15
Here you go..

```
user@user-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
```


Bondi

---

### Post by glennric on 2008-03-15
You can try editing /usr/bin/compiz
```
sudo gedit /usr/bin/compiz
```
and finding the line that is blacklisting your video card and commenting that out by putting a # before the line.  Then try "compiz --replace".
This may not work though or you may have problems with compiz.  Your card is blacklisted because compiz doesn't work well with it.

---

### Post by bondi007 on 2008-03-15
```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T
```

Is it this, if so what exactly do I do and where sorry I didnt understand you :(

Bondi

---

### Post by Paqman on 2008-03-15
It looks like Compiz have blacklisted your card (Intel 965) because "XV does not play with XAA under compiz, only with EXA", whatever that means.

You could try the steps for [ignoring the blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist), but i'd suspect they've blacklisted your card with good reason.

Basically it looks like your hardware isn't compatible with Compiz at the moment.

---

### Post by bondi007 on 2008-03-15
I still don't get this sorry, all I want to do is be able to get compiz running so its all good


Bondi

---

### Post by v1cho on 2008-03-15
> **bondi007 said:**
> ```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T
```

Is it this, if so what exactly do I do and where sorry I didnt understand you :(

Bondi

Put a # at the beginning of this line:
```
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
```
then go to: System > Preferences > Appearance > Visual Effects (it's a tab) and switch it to Normal :)

---

### Post by bondi007 on 2008-03-15
I did that and the line went blue and I saved it and then set the visual affect to normal but I still don't get anything.

Is this normal so I have to set anything else 

Cheers
Bondi:)

---

### Post by bondi007 on 2008-03-15
It works now after editing that, TY

---

### Post by sasquatch74 on 2008-03-15
Hi,
I've got a R61 with the Intel video card as well.  You may have trouble playing videos with the way you fixed your compiz issue, but I'm not sure.  You could try playing a video to see if it works.  If you cannot play videos, then you could try the instructions in [this]("http://ubuntuforums.org/showthread.php?t=707473&highlight=intel+965") post, which worked for me.  Good luck and welcome to Ubuntu.

---

### Post by p221072 on 2008-03-15
Just add a '#' in front of the line with your graphic card, like this:
```
...
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
...
```
so your card is not blacklisted anymore.
To me it worked fine, but you could experience some problems since compiz is not working perfectly with those intel boards.
Thank you all

EDIT:
sorry I've seen the answer was already posted too late
(is there anyway to delete a post? )

---

