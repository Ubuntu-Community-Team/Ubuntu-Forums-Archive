---
title: "Get laptop to go on standby when the lid is shut"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-03
I recently put Kubuntu on my laptop and I was wondering how I can make it so when I close my lid the computer goes on standby

also, how do I get it so the screen goes dim when I unplug it from the wall

---

### Post by jpkotta on 2007-12-04
There are a bunch of scripts in /etc/acpi that control what happens when certain events (like the closing lid) take place.  I would try simply adding the suspend script to the lid script.  Sorry I can't be more descriptive than that, but my laptop isn't here and I haven't messed with this stuff for months.  There may be an easier way to go about this.  

The way my backlight works is it's completely handled by the BIOS, not the OS.  The BIOS knows what mode the laptop is in (AC vs. battery), and has two separate settings for the modes.  So to set the backlight in a sane way I would plug it in, change the brightness (with the Fn key in my case), then unplug it and change the brightness again.  The BIOS remembers these settings and keeps them independent.  YMMV.

---

### Post by jpkotta on 2007-12-04
Ah!  The scripts are on my desktop too.  It doesn't suspend and I'm not taking the time to learn how to make it do so.

In /etc/acpi/lid.sh:
```
grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"           
            . /usr/share/acpi-support/screenblank
        fi
    done
    /etc/acpi/sleep.sh
else

```

Note the /etc/acpi/sleep.sh line.

Again, I don't know for sure if this works, or if it is the easiest way to go.

---

### Post by jpkotta on 2007-12-04
You may also want to try /etc/acpi/events/lidbtn:
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
#action=/etc/acpi/lid.sh
action=/etc/acpi/sleep.sh

```

---

### Post by Dapman01 on 2007-12-06
> **jpkotta said:**
> You may also want to try /etc/acpi/events/lidbtn:
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
#action=/etc/acpi/lid.sh
action=/etc/acpi/sleep.sh

```

Ok, I did this and the laptop does go on standby, but when I open the lid, my screen is grey and black and the grey and black go nuts, after about 30 seconds of this the computer goes back in standby.  Once in a while it will go back to the desktop.

---

### Post by asmiller-ke6seh on 2007-12-06
I am a Gnome user, so it will probably be different for you, however:

I was able to find all of these settings in the power management application.

---

### Post by Dapman01 on 2007-12-06
does anyone know where the power managenment is in kubuntu

---

