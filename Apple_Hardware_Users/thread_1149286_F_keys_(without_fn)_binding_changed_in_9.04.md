---
title: "F keys (without fn) binding changed in 9.04"
date: 2009-05-05
forum: Apple Hardware Users
---

### Post by jettjunker on 2009-05-05
I have a macbook 1,1, and I used to have my F keys (without fn) remapped to IA1-12, and just bound them for my own purposes.  But, now xmodmap ~/.xmodmap doesn't do anything; xev doesn't even report the keycodes anymore.  It's not a big deal for F1-5, since I use them for brightness/volume and that works relatively well out of the box (though buggy... mute also mutes Front [along with PCM and master], but doesn't unmute it, and the brightness controls are fickle), but I used to use F7 to open a terminal, and F8-10 for Amarok global shortcuts, and I'd really like that functionality back...

Any ideas?  What changed?

Also, I don't want F11/F12 to be middle/right-click...  I imagine it's part of the same solution as getting around this special keys binding for the rest of the F keys that I don't want.
EDIT: running "sudo apt-get remove mouseemu" solved the F11/12 issue, and now F11 maximizes and F12 opens a terminal.  I'm now most interested in getting F8-10 working.

---

### Post by cyberdork33 on 2009-05-05
So you want the Fx keys to be able to be mapped to certain functions? Maybe you do not want the default Fn key behavior?

---

### Post by jettjunker on 2009-05-05
Correct, and from what I understand that means I need to find out the keycodes (with xev, typically), and use xmodmap to label them differently (as semi-arbitrary names like IA8, rather then their special function).  But, while I know the keycodes, xmodmap ~/.xmodmap no longer relabels them.

I don't know entirely what's going on, but I get the impression that they are labeled for special functions (like alt, ctrl, etc) and I cannot simply relabel them like I used to -- I have to disable the special function assigned to those keys before I can do that.

---

### Post by cyberdork33 on 2009-05-05
well, if you want the key to perform the Fx function by default rather than the special function, you can do that:
[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

As for mapping the special keys to do something useful, some keys will require kernel mods to be able to send a code first (then you can map then to whatever you like). Someone had done this before with the expose keys so that you could use them with compiz. The post is here in the forum somewhere.

---

### Post by jettjunker on 2009-05-05
I'm not interrested in changing the fn behavior (I like having it perform actions while fn isn't pressed, and F# while it is).  But, in the "Mapping Keys" section it says:
*Since Xmodmap have been replace by X Keyboard Extension, it's impossible to use Xmodmap to proceed with the mapping. Configuration can be done using the Keyboard preference tool.*

So that might explain why I've been having so much trouble, but I can't find anything in the Keyboard preference tool to help me do what I want (I'm assuming that's referring to System > Preferences > Keyboard).  It allows swapping various special keys (like alt <-> tab), and the like, but nothing for unmapping the special events from F keys.

For the heck of it I tested turning keycode 35 (bracketright, "]") into IA13 with xmodmap, and it worked fine... So I'm still convinced that if I got the special events unmapped, and the keycodes reporting again, I could get them mapped to IA# as I like.

I guess I'll try looking into these "kernel mods" you speak of, but this is getting ridiculous...  What a change.  Still, thanks for your help.

---

