---
title: "Touchpad Stray Scolling"
date: 2009-07-14
forum: Apple Hardware Users
---

### Post by raronson on 2009-07-14
Hi,

I've been stuggling with the 'appletouch.fdi' config for awhile now, and I'm still having issues with unintentional scrolling.  I 've been keeping the config file open, saving changes, and reloading the module in a seperate workspace--and it's getting old.

Unintentional scrolling defined as:

The act or instance of vertical scrolling when placing hands on macbook(4,1) keyboard to begin typing.  Affects all applications with vertical scrollbar.  I've found that this is related to the value:

    <merge key="input.x11_options.VertScrollDelta" type="string">90</merge>

in the /etc/hal/fdi/policy/appletouch.fdi file.  As you can see, I have it set at 90 at the moment, which helps with the problem a bit, but seriously gimps my two-fingered scrolling.

Other values of interest:

        <merge key="input.x11_options.RightEdge" type="string">1200</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

I've set these as high as 6000 each, but it doesn't seem to help. And,

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>

Which intuitively, I think has something to do with touchpad sensitivity (that could be setting off the unintentional scroll), but it might be related to tapping, which I have disabled.  Changing the values doesn't seem to help.

Further notes:

The unintentional scroll happens because the meaty part of my thumb hovers over the lower right section of the pad when I set my hands down for typing.  I've tried to be more conscious of this, but it feels very unnatural when I do so and distracts me from the focus of the moment (which is typing something).  I'm not sure if the hit registers as pressure on the pad, which sets off the scroll, or registers as something two-finger scroll.  

Options:

.watch your hands when you type, you gorilla (actually I have normal hands and I play guitar, which says something about percision and dexterity).
.disable two-fingered scrolling (no, thanks).
.keep increasing the value of VertScrollDetla (serious affects ability to use scrolling)


Here is the output of /etc/hal/fdi/policy/appletouch.fdi

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1200</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>

        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
    
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.30</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.65</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.1</merge>
    <merge key="input.x11_options.VertScrollDelta" type="string">90</merge>
    <merge key="input.x11_options.HorizScrollDelta" type="string">90</merge>

  </match>
 </device>
</deviceinfo>

```Thanks for any help!  It's really annoying, and I have to keep switching focus to tinker with it, which distracts me from using my laptop.

---

### Post by raronson on 2009-07-15
Hmm.  I can't believe other Apple users aren't having this problem, or have accepted the limitations.  I'll keep working this and post a solution.  I just figured someone would be quick to flex their digital kung foo.

---

### Post by raronson on 2009-07-17
Fixed.  If you're having the same issue as I described, this may help you--though don't ask me what anything means :)  I just brute-forced the values to get an acceptable configuration.

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">1280</merge>
        <merge key="input.x11_options.LeftEdge" type="string">800</merge>
        <merge key="input.x11_options.RightEdge" type="string">800</merge>
        <merge key="input.x11_options.BottomEdge" type="string">1280</merge>

        <merge key="input.x11_options.FingerLow" type="string">25</merge>
        <merge key="input.x11_options.FingerHigh" type="string">15</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>

        <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">1</merge>
    
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.30</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.65</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.1</merge>
    <merge key="input.x11_options.VertScrollDelta" type="string">50</merge>
    <merge key="input.x11_options.HorizScrollDelta" type="string">90</merge>

  </match>
 </device>
</deviceinfo>

```

---

### Post by issih on 2009-07-17
I suggest you play with syndaemon

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

which is described in there somewhere.

It locks out the touchpad whilst you are typing to avoid unintended mouse events.

If you are activating this unintended scrolling as you hands move to the keys this might not be useful, but it works here.

Hope that helps

---

### Post by raronson on 2009-07-17
Thanks, issih.  That's a good link.  My problems are fixed (or at least acceptable now), but I'll definitely go back and read that article and follow all the links.  It looks like it has all the info I wanted to know.  Thanks again.

---

