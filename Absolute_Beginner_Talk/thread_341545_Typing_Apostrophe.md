---
title: "Typing Apostrophe"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Leonaken on 2007-01-18
I´m having an issue where I have to hit the Apostrophe key twice in order to get a ´ or a ¨, which is incredibly annoying when typing. I tried adding another keyboard layout into the Keyboard preferences, which didn´t help.

Any solutions?

---

### Post by Ragazzo on 2007-01-18
´ is a [dead key]("http://en.wikipedia.org/wiki/Dead_key") and called a backtick. Are you sure you're pressing the right key?

---

### Post by Leonaken on 2007-01-18
I´m pressing *the key next to the colon*. Is there a way to make it function as it would in Windows? I mean, one-touch **´**-typing action.

---

### Post by Ragazzo on 2007-01-18
It should be possible with xmodmap. Start program xev in terminal and press the key that should produce apostrophe and write down its keycode. Then you can use 

```

xmodmap -e "keycode 48 = apostrophe quotedbl"

```

"48" is the keycode, "apostrophe" is the letter when no modifier key (shift, alt...) is used, and "quotedbl" is the letter when shift is held down. If that works, then create file ~/.Xmodmap and add in it the line: keycode 48 = apostrophe quotedbl

And in Preferences->Sessions add "xmodmap ~/.Xmodmap" to startup programs.

I don't use the US layout so I'm not sure about the keycode.

---

### Post by irish_flu on 2007-01-18
I'm not sure what to make of that, Leonaken.  It works fine for me. I can use ' or " with one touch (well ok the second one is shift+touch, heh), just as I would in Windows....

Question, is your keyboard set to "US English" layout (if that's appropriate for you, anyway)?  Mine is set to that, and my model is listed as "Generic 104-key PC".

The keyboard control panel that information came from is located in (I'm using Gnome, I'll assume you are too) System --> Preferences --> Keyboard, then click the "Layouts" tab.

That's weird!  I've set up nothing special in regards to my keyboard layout, that's for sure.

---

### Post by Leonaken on 2007-01-19
> **Ragazzo said:**
> I don't use the US layout so I'm not sure about the keycode.

You got the keycode right (48 ), but the xmodmap command doesn´t seem to work.
```
me@system:~$ xmodmap -e keycode 48 = apostrophe quotedbl
xmodmap:  commandline:1:  bad keycode input line
xmodmap:  unable to open file '48' for reading
xmodmap:  unable to open file '=' for reading
xmodmap:  unable to open file 'apostrophe' for reading
xmodmap:  unable to open file 'quotedbl' for reading
xmodmap:  5 errors encountered, aborting.

```

---

### Post by Ragazzo on 2007-01-19
There should be double quotes around "keycode 48 = apostrophe quotedbl" but I think, as the other poster pointed out, that there is something wrong with your keyboard layout settings. You're using dead acute, not apostrophe, in your posts. Compare these: ´ '

---

### Post by mistaWAC on 2008-02-14
I´m having the same problem and am using ¨us:intl¨ layout.  The apostrophe works at home, but on me laptop it´s being a douchebag.  I tried that .Xmodmap thing and it didn´t work.  So am I just changing my layout?  If so, to what?

---

### Post by Agrajag27 on 2008-04-01
Anyone get a fix for this? I´m also set to US and have to hit the apostrophe twice for every use. This alone would drive me back to Windows. I write heavily every day and can´t have this going on. My boss is a grammar fanatic.

Same problem for the double-quotes. Have to hit it twice.

I´ve noticed that for some words that I can fast-type and it will give me a special case.

For example, the first line below is me typing fast:

What&#347;

Notice the apostrophe? It was added not when I typed it but when I typed the ¨s¨ key.

This next line is me typing slow:

What´s

I had to hit the apostrophe twice. I could even get used to the fast typing situation except it doesn´t always work (like for that last use in doesn´t).

---

### Post by jaimes on 2008-04-03
I had this same problem and the 'xmodmap -e "keycode 48 = apostrophe quotedbl"d' fixed it.

''''''''"""""""""""""""""""""''''''''''''''''''''''''''''''''''''''''''''''''''''

thanks.

---

