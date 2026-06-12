---
title: "1280x800 - intel mobile"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Eddy Van Halen on 2007-07-10
Hello people, 

Don't get mad at me, I've seen previous posts. But I didn't understood a thing how to do it, actually achieve what I am after.

At the moment I can't choose proper resolution (1280x800) It's a laptop wide-screen 15.4. The highest it's shown is 1024x800.

So could anyone explain me, what to do, all the step how to get proper resolution on? 

I think that's the thread that explains it, but It doesn't say what to do.

Sorry if i sound stupid.
Thanks to anyone who will help me.

---

### Post by dmfield on 2007-07-10
Never apologise for sounding stupid.. Its the stupid, who learn the fastest, because they ask questions..

OK, this may work, it may not, but its worth a try

Open a Terminal and type 

> cd /etc/X11/Lets backup your xorg.conf first

this should take you to the area which ahs your screen configurations in it.

> sudo cp xorg.conf xorg.conf.justincase(if it all goes wrong, and after a reeboot you get a text screen, login with your usual details and they type
> 
cd /etc/X11> sudo rm xorg.conf> sudo mv xorg.conf.justincase xorg.confthen

> sudo reboot
This will put it all back to how it was
now we need to edit the file xorg.conf to do this type

> sudo gedit xorg.confThis should open a text editor with a load of config looking lines of text in it.. if it does, carry on..

Use the search in Gedit and look for this line

> Section "Screen"under this section should look something like this

>  Identifier      "Default Screen"
        Device          "ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS"
        Monitor         "DELL E153FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480You need to add the following to each depth line

> 
Modes  **"1280x800" **"1024x768" "832x624" "800x600" "720x400"there will probably be 6 occurences of this under

Depth 1
Depth 4
Depth 8
Depth15
Depth 16
Depth 24

Chence each one, then save the the file, and reboot..(or press CTRL Alt and Backspace)

If the gnome screen comes back up for a login, hurrah! login, and you should be able to now change the resolution to 1280x800

if not, then refer to the backup section you did (you did do it didn't you?) at the top of this page..

Let me know..

---

### Post by Eddy Van Halen on 2007-07-10
All right dude,

do you have to become 'boot@pcname" before you start all that or not? 

I'm gonna reinstall linux after tomorow cause I've done something wrong.  

Also,

The screen section was different from what you wrote.

Section "Screen"
Identifier"Default Screen"
Device"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Monitor"Generic Monitor"
DefaultDepth24
SubSection "Display"
Depth1
Modes"1280x800"
EndSubSection
SubSection "Display"
Depth4
Modes"1280x800"
EndSubSection
SubSection "Display"
Depth8
Modes"1280x800"
EndSubSection
SubSection "Display"
Depth15
Modes"1280x800"
EndSubSection
SubSection "Display"
Depth16
Modes"1280x800"
EndSubSection
SubSection "Display"
Depth24
Modes"1280x800"
EndSubSection
EndSection

:S  Do you have msn messenger, skype or something like that? 

And there's a way of fixing linux? :D

---

### Post by isaacj87 on 2007-07-10
Whoa whoa...hold on...simpler way...

I noticed you've got an intel i915

just do this

Go to System->Administration->Synaptic and do a search for 915resoluion (search it with no spaces)

install that package, reboot and that should be the end of your resolution problem :). It was made specifically to help correct issues with the intel chipsets.

Let me know if it works for you.

---

### Post by Eddy Van Halen on 2007-07-10
> **isaacj87 said:**
> Whoa whoa...hold on...simpler way...

I noticed you've got an intel i915

just do this

Go to System->Administration->Synaptic and do a search for 915resoluion (search it with no spaces)

install that package, reboot and that should be the end of your resolution problem :). It was made specifically to help correct issues with the intel chipsets.

Let me know if it works for you.

oh damn, sorry for your wasted time. Right dude. I'd try that after you tell me how to reinstall linux or uninstal em before installing again , thanks :)

---

### Post by isaacj87 on 2007-07-10
What's wrong with your comp...what are its symptoms?

To do a reinstall, just pop the liveCD back in there and repeat the process you first did.

Plus, i'm using AIM and MSN via gaim...screenname is xdemon869 (AIM)...if you find having to post every second a little irritating.

---

### Post by rugbeeprop on 2007-07-10
Thanks. It works for me. (I add the screen resolution and refresh rate)


:KS

---

### Post by isaacj87 on 2007-07-10
Glad to hear it...i love that little package..it's a lifesaver

---

