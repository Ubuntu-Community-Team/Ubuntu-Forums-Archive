---
title: "How do you reset sound volume control to default?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by livewire94 on 2007-06-15
After playing around with the volume control settings, muting, unmuting, I haven't had luck increasing the volume in tvtime.  So now I want to reset my volume control / mixer settings back to default.  Anyone know how to do that?

Thanks

---

### Post by pete83 on 2007-06-15
The most failsafe way I know of changing the volume is to go to a terminal and type

```
alsamixer
```

---

### Post by livewire94 on 2007-06-15
Ok.  typed Alsamixer in terminal but how do you reset everything in alsamixer to the default settings.  I want to reset all the settings in alsamixer to default.

Thanks

---

### Post by pete83 on 2007-06-16
```

   Alsamixer: General Controls
       The  Left  and  right  arrow  keys  are  used to select the channel (or
       device, depending on your preferred terminology). You can  also  use  n
       ("next") and p ("previous").

       The  Up  and  Down Arrows control the volume for the currently selected
       device. You can also use + or - for the same purpose. Both the left and
       right signals are affected. For independent left and right control, see
       below.

       The B or = key adjusts the balance of volumes on left and  right  chan&#8208;
       nels.

       M toggles muting for the current channel (both left and right).  If the
       hardware supports it, you can mute  left  and  right  independently  by
       using , (or <) and . (or >) respectively.

   View Mode Controls
       Function  keys  are  used  to change view modes.  You can switch to the
       help mode and the proc info mode via F1 and F2 keys, respectively.   On
       terminals  that  can&#8217;t  use  function keys like gnome-terminal, ? and /
       keys can be used alternatively for help and proc modes.

       F3, F4 and F5 keys are used to switch to playback, capture and all view
       mode,  respectively.  TAB key toggles the current view mode circularly.


```

Now, if it used to be louder, and you want to make it just like default, make it louder.
If it used to be quieter, and you want it to be like default, make it quieter.
If it used to be not muted but now it is muted, then unmute it.

I know this is not exactly what you were asking for, but most computers only have about 3 to 5 volume bars that you need to change.

If you really want to get the "default" settings, the volume states of your sound card, as well as I can determine, are stored in the file /var/lib/alsa/asound.state.  So you could try deleting it to get the default values. Then again, who knows what will happen if you delete it...

---

