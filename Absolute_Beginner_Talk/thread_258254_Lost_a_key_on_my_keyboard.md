---
title: "Lost a key on my keyboard"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-09-15
The letter "p" is in my password, and it works on startup, but not after 6.06 is done loading. I can't access any administrative functions. Any ideas? I don't recall having done more than glanced at keyboard options. Please help! Without the "p" all I've got is an assword.

---

### Post by Brunellus on 2006-09-15
wow.  that's pretty weird.  are you sure it's not a hardware failure?

btw,off-topic this reminds me of that t-shirt:  without ME, you're just AWESO.

---

### Post by Anduu on 2006-09-15
> **ricardisimo said:**
> Without the "p" all I've got is an assword.

LOL

Seriously tho I would try another keyboard just to be sure.

---

### Post by Jukey on 2006-09-15
I may have read about this somwhere. Did you accidentally press a letter while you were in a program menu? That may have over written the shortcut with the letter "P". 

Just a theory. 


good luck with the problem!

---

### Post by ricardisimo on 2006-09-15
> **Jukey said:**
> I may have read about this somwhere. Did you accidentally press a letter while you were in a program menu? That may have over written the shortcut with the letter "P". 

Just a theory. 


good luck with the problem!

That's kinda what I was afraid of, but like I said, I was looking to see if there was an Ubuntu correlate to "US-International" in Windows (standard layout, but with a few accented vowels and such for writing letters to the Old Country). The letter "P" has nothing to do with it. I mean, I can see maybe experimenting with the vowels, or trying to get a Ç or Ñ, but I didn't even do that. If I changed "P" to something else, how would I check?

---

### Post by ruedu on 2006-09-15
If you're on a laptop, make sure your number lock is not on.

---

### Post by ricardisimo on 2006-09-15
> **ruedu said:**
> If you're on a laptop, make sure your number lock is not on.

Not an issue, but thanks. Also, I would suspect the hardware if even only just once the "p" failed to work on startup, or alternately, did work afterwards. I'd very much like to avoid buying anything.

---

### Post by ruedu on 2006-09-15
Does the P key EVER work?  Can you use it in the grub menu?

---

### Post by ricardisimo on 2006-09-15
> **ruedu said:**
> Does the P key EVER work?  Can you use it in the grub menu?

It works on every boot-up, but not ever after that.

---

### Post by ricardisimo on 2006-09-16
Someone asked if it worked in GRUB. Please bear with this n&#363;b, and walk me through how I would try that. Does this just mean in a terminal window? Also, how can I check to see what the key IS doing while it appears to do nothing. Is there a way to trace this?

---

### Post by mixmaster on 2006-09-16
Does shift-p work to give you a capital P?  If so, a temporary workaround is CAPS-LOCK shift-p to get a lower case P.

Not a solution but at least you get admin function back while you try something else.

---

### Post by ricardisimo on 2006-09-16
Nothing.

---

### Post by editrix on 2006-09-17
> **ricardisimo said:**
> Someone asked if it worked in GRUB. Please bear with this n&#363;b, and walk me through how I would try that. Does this just mean in a terminal window? Also, how can I check to see what the key IS doing while it appears to do nothing. Is there a way to trace this?

If you can get into a terminal, type

xev

That should start a little program with a window with a square box inside it. Type one key (any key) and the terminal should tell you what the key returns.

---

### Post by ricardisimo on 2006-09-19
> **editrix said:**
> If you can get into a terminal, type

xev

That should start a little program with a window with a square box inside it. Type one key (any key) and the terminal should tell you what the key returns.

Thanks for the tip! This definitely confirms that the key works, but its output has been altered somehow. Here's what I get when I press the "p" key:

> KeyPress event, serial 26, synthetic NO, window 0x3200001,
    root 0x3e, subw 0x0, time 3356694493, (242,271), root:(257,366),
    state 0x10, keycode 33 (keysym 0x1008ff31, XF86AudioPause), same_screen YES,    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3200001,
    root 0x3e, subw 0x0, time 3356694583, (242,271), root:(257,366),
    state 0x10, keycode 33 (keysym 0x1008ff31, XF86AudioPause), same_screen YES,    XLookupString gives 0 bytes:

Can anyone tell me if this is meaningful? It seems to me that the relevant bit of info is the "XLookupString gives 0 bytes:", but I have no clue how to proceed from here. I'd be glad to also post another key's return value as well. In fact, why not do that right now. Here's "l":

> KeyPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x3e, subw 0x0, time 3356914088, (190,363), root:(205,458),
    state 0x10, keycode 46 (keysym 0x6c, l), same_screen YES,
    XLookupString gives 1 bytes: (6c) "l"
    XmbLookupString gives 1 bytes: (6c) "l"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3200001,
    root 0x3e, subw 0x0, time 3356914173, (190,363), root:(205,458),
    state 0x10, keycode 46 (keysym 0x6c, l), same_screen YES,
    XLookupString gives 1 bytes: (6c) "l"

Thanks in advance for any further help.

---

### Post by ricardisimo on 2006-09-19
Please ignore the emoticons above. Don't know how to turn those off.

---

### Post by ricardisimo on 2006-09-19
Thanks for the tip! This definitely confirms that the key works, but its output has been altered somehow. Here's what I get when I press the "p" key:

Quote:
KeyPress event, serial 26, synthetic NO, window 0x3200001,
root 0x3e, subw 0x0, time 3356694493, (242,271), root257,366),
state 0x10, keycode 33 (keysym 0x1008ff31, XF86AudioPause), same_screen YES, XLookupString gives 0 bytes:
XmbLookupString gives 0 bytes:
XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3200001,
root 0x3e, subw 0x0, time 3356694583, (242,271), root257,366),
state 0x10, keycode 33 (keysym 0x1008ff31, XF86AudioPause), same_screen YES, XLookupString gives 0 bytes:
Can anyone tell me if this is meaningful? It seems to me that the relevant bit of info is the "XLookupString gives 0 bytes:", but I have no clue how to proceed from here. I'd be glad to also post another key's return value as well. In fact, why not do that right now. Here's "l":

Quote:
KeyPress event, serial 29, synthetic NO, window 0x3200001,
root 0x3e, subw 0x0, time 3356914088, (190,363), root205,45,
state 0x10, keycode 46 (keysym 0x6c, l), same_screen YES,
XLookupString gives 1 bytes: (6c) "l"
XmbLookupString gives 1 bytes: (6c) "l"
XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3200001,
root 0x3e, subw 0x0, time 3356914173, (190,363), root205,45,
state 0x10, keycode 46 (keysym 0x6c, l), same_screen YES,
XLookupString gives 1 bytes: (6c) "l"
Thanks in advance for any further help.

---

### Post by latecomer on 2006-09-19
I think the relevant bit may be (keysym 0x1008ff31, _XF86AudioPause_). 
Have a look in System -> Preferences -> Keyboard Shortcuts and scroll down to Sound. Did you make p a shortcut for 'play (or play/pause)' or for 'pause'? Try disabling them both if they're enabled. Or maybe you assigned the audiopause-function to p in some audio-app? 
These are just guesses, btw.
0 bytes is normal for keys that don't actually put anything on screen, like the functionkeys, shift, ctrl etc.

---

### Post by ricardisimo on 2006-09-19
PPPPPPPPPPP!!!!!!!!!!!!!! ppppppppppppppppppppp!!!!!!!!!!!!!!!!!!!!
You rock, my friend! Are you sure this is your "First Cup of Ubuntu"? Thanks bunches. Copy and Paste for one letter was getting tiresome, to say the least. No more asswords for my comuter! ;)

---

### Post by Anduu on 2006-09-19
I love a happy ending \\:D/

---

### Post by Brunellus on 2006-09-20
> **Anduu said:**
> I love a happy ending \\:D/
best support thread I've read this week.  way to go, guys!

---

### Post by latecomer on 2006-09-20
> **ricardisimo said:**
>  Are you sure this is your "First Cup of Ubuntu"? 

First cup yes, but I think I like the taste :razz:
Cheers!

---

