---
title: "Transparent decoration on window that has focus"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by sistoviejo on 2008-04-10
By default the windows that don't have focus have a transparent decoration. I want the window with focus to also be transparent.
I was able to set it at my desktop PC but forgot how to do it. All I know is that I did it without Emerald themer.
Any advice appreciated.

---

### Post by joshrobinson on 2008-04-10
do you have ccsm installed?

```
sudo apt-get install compizconfig-settings-manager
```
to open it run
```
ccsm
```

now look for the "trailfocus" plugin, its in the effects section
put a check in the box next to it if there isnt
then click it to open it, and where it says "opacity of focused windows"
move the slider so that it sets the transparency you want

---

### Post by sistoviejo on 2008-04-13
Actually I only want the window's title bar and the border to be transparent. Not the whole window. 
Sorry if I wasn't clear. Thanks anyway.
Any help appreciated.

---

### Post by mgmiller on 2008-04-13
Open the configuration editor:
```
gconf-editor
```
Then go to Apps>gwd
In the right pane look for entry  "metacity-theme-active-opacity"

If you click it, you can change the value to whatever you want.  
1.0 is opaque, 0.5 is half transparent, etc.  I have mine set to 0.67 and it looks good to me.

The change takes place as soon as you hit enter.

Have fun.

---

### Post by sistoviejo on 2008-04-13
That's it. thank you.

---

### Post by mgmiller on 2008-04-13
You're welcome...

:popcorn:

---

### Post by adamorjames on 2008-04-19
This was annoying me so much. Thank you.

---

### Post by mgmiller on 2008-04-19
:guitar:

---

### Post by m3alnemer on 2008-05-14
> **mgmiller said:**
> Open the configuration editor:
```
gconf-editor
```
Then go to Apps>gwd
In the right pane look for entry  "metacity-theme-active-opacity"

If you click it, you can change the value to whatever you want.  
1.0 is opaque, 0.5 is half transparent, etc.  I have mine set to 0.67 and it looks good to me.

The change takes place as soon as you hit enter.

Have fun.

This is great
I hope there were something that controlls the transparency of font and buttons. 
Thanks a lot!:)

M3alnemer

---

### Post by m3alnemer on 2008-05-14
After enabling the emerald window fire fox doesn't work
When i click on it Gusty logs off

---

### Post by mgmiller on 2008-05-15
> After enabling the emerald window fire fox doesn't work
When i click on it Gusty logs off

Your question has nothing to do with this thread.  You will get more help if you start a new thread and ask your question there.  For now, just try disabling emerald and see if you get back to normal.

Open the Run Application dialog box by hitting alt/F2 and then enter the following:
```
gtk-window-decorator --replace
```

It's important that you not run this from a terminal, use the Run Application dialog box instead.

---

