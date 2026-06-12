---
title: "HAL fdi settings not all applied"
date: 2009-03-15
forum: Apple Hardware Users
---

### Post by philcolbourn on 2009-03-15
MacBook Pro 4,1. Ubuntu Intrepid 8.10.

I am customising my fdi settings. When I compare the output of synclient -l and Device Manager I get different values for some options.

eg 1. CircScrollTrigger: DM says 1 (the value I put in my fdi file) and synclient -l says 8. synclient is right in that '8' (AKA top-left-corner) is in-force.

eg 2. BottomEdge: DM says 720 (the value I set in my fdi file) as does synclient -l

Thinking that HAL may be processing the package fdi file:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

and my file:

/etc/hal/fdi/policy/21-x11-bcm5974-pc.fdi

I set the prefix to '21'

My file validates against the DTD and /usr/src/bcm5974-1.1.1/scripts/bcm5974-diagnostics says that all is good.

I have syslog'ing turned on and no fdi errors are logged.

Now, if I manually set the options with synclient Option=value I get the behaviour I am looking for.

So, any suggestions?

---

### Post by cyberdork33 on 2009-03-15
> **philcolbourn said:**
> MacBook Pro 4,1. Ubuntu Intrepid 8.10.

I am customising my fdi settings. When I compare the output of synclient -l and Device Manager I get different values for some options.

eg 1. CircScrollTrigger: DM says 1 (the value I put in my fdi file) and synclient -l says 8. synclient is right in that '8' (AKA top-left-corner) is in-force.

eg 2. BottomEdge: DM says 720 (the value I set in my fdi file) as does synclient -l

Thinking that HAL may be processing the package fdi file:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

and my file:

/etc/hal/fdi/policy/21-x11-bcm5974-pc.fdi

I set the prefix to '21'

My file validates against the DTD and /usr/src/bcm5974-1.1.1/scripts/bcm5974-diagnostics says that all is good.

I have syslog'ing turned on and no fdi errors are logged.

Now, if I manually set the options with synclient Option=value I get the behaviour I am looking for.

So, any suggestions?
Interesting. I am having a weird issue with this in Jaunty too... I think the one in /usr/share is the default and gets used if there is no other config (at least it should be working that way. You could move that file to your Desktop temporarily and see if that changes the behavior.

---

### Post by philcolbourn on 2009-03-15
> **cyberdork33 said:**
> Interesting. I am having a weird issue with this in Jaunty too... I think the one in /usr/share is the default and gets used if there is no other config (at least it should be working that way. You could move that file to your Desktop temporarily and see if that changes the behavior.

I removed the fdi file in /usr/share. Same problem. Maybe the driver is not reading all of the fdi settings?

The XxxxEdge seem ok.
FingerXxx don't work.
AccelFactor is ok.
Min/MaxSpeed are ok.
TapButtonX are ok.
ClickFingerX are ok.
CircularScrolling seems ok, but CircScrollXxx don't work.
XxxxScrollDelta don't work.
MaxTapTime doesn't work.

Others I can't tell yet.

---

### Post by philcolbourn on 2009-03-15
It seems that gsynaptics package installs a touchpad preferences application that overides some settings.

Most of my settings are now being used except:
MaxTapTime.

It is currently set to 180 but I have 128 in my fdi file.

---

### Post by philcolbourn on 2009-03-15
Circular scrolling is great - I wonder if I will get sick of it?

My settings are:

CircularScrolling       = 1
CircScrollDelta         = 0.3
CircScrollTrigger       = 1

The trigger is the top edge: start your scroll above the top edge, head towards the centre of the trackpad and then scroll using clockwise and anti-clockwise movements around the centre.

---

