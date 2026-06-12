---
title: "Disabling touchpad"
date: 2013-09-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ncFP8RY on 2013-09-15
Is there any way to completely disable the touchpad on an Asus SonicMaster under Ubuntu 12.04?

I have tried the "disable while typing option" but is only stays disabled until I accidentally brush against the touchpad and next time I look up, I find I have overtyped in some random area of the doc. I have been told that the correct solution is to learn to touch type, but I have never been able to do that. I also tried a piece of cardboard glued over the danger area but I am worried that might damage the screen when the lid is closed.

Thanks in advance

---

### Post by Linuxisfast on 2013-09-16
[http://www.webupd8.org/2011/02/touchpad-indicator-now-automatically.html](http://www.webupd8.org/2011/02/touchpad-indicator-now-automatically.html)

---

### Post by sudodus on 2013-09-16
In versions where Touchpad Indicator works, fine :-)

Otherwise a simple way to disable the touchpad is to include a simple function in .bashrc and call it from a terminal window (I do it directly after login from an autostarted terminal window).

So if you add the following lines at the end of your [FONT=courier new]**.bashrc**[/FONT] file

```
alias TT='touchpad-toggle'

###

function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}

####

alias TT
```

You can easily toggle the touchpad on/off with the ***TT***.

---

