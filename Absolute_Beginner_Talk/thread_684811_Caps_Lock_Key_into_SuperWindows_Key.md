---
title: "Caps Lock Key into Super/Windows Key"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by cperalta1 on 2008-02-01
Hello all,

For three days now I've been trying to reassign the Caps Lock key as a Super/Windows Key on my Thinkpad.  I've read all the threads but still can't figure it out.

Will someone please give me a (very detailed) step by step?

Thanks in advance.

Chris

---

### Post by cperalta1 on 2008-02-01
anyone?

---

### Post by Whiffle on 2008-02-01
make a file called .Xmodmap  in your home directory,

put this in it:
```

! No Caps Lock
clear lock
! Caps Lock as Win key
add mod4 = Caps_Lock

```


log out, log in, it should work.

---

### Post by cperalta1 on 2008-02-01
Okay, 

I went into terminal and typed in "sudo gedit", then copied and pasted the lines into the Unsaved Document 1.  Then I clicked file >save as and named it ".Xmodmap" and saved it in my HOME.  Restarted and opened up a text editor and checked Caps Lock and it works normally (No Win Key).  If I open up my Home folder there are only two files "Chris" & ".Xmodmap".  I opened .Xmodmap just to make sure it was written correctly and it is.  

Please excuse my ignorance, but am I screwing something up here???

I'm baffled!

---

### Post by drs305 on 2008-02-01
Here is another way to do it. 

In terminal, run
```
xev
```
When you enter a keystroke, it will tell you the keycode and name. Hit the two keys you want to change and note the keycodes/names.

Then run in terminal:
```
xmodmap -e &#8220;KEYCODE <number> = <KEYSYMNAME>"
```
with the keycode being the key you want to change and NAME being the name of the new key.

I changed a division key to a tab key, so the command I ran was:
```
xmodmap -e "keycode 112 = Tab"
```

I then went to System, Preferences, Sessions and added a startup script so the key change would be effective on every boot. The line in the startup command line was:
xmodmap -e "keycode 112 = Tab"

If you have questions you can find more information by typing:
```
man xmodmap
```

I'd give you the codes for the specific keys you are trying to change but I've already reprogrammed them to something else.  ;-)

---

