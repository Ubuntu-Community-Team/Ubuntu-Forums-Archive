---
title: "Beryl Super Key"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-12-04
This is going to sound stupid I know but what is the super key in Beryl?  I have it installed I just want to try all of the effects.

---

### Post by jordanmthomas on 2006-12-04
It's the Windows button on your keyboard.  (usually)

---

### Post by JayTee on 2006-12-04
> **gentlemanmasher said:**
> This is going to sound stupid I know but what is the super key in Beryl?  I have it installed I just want to try all of the effects.

The question didn't sound stupid at all to me. I'd never heard of the Windows key referred to as the "Super" key until I started running Beryl. It's certainly not self-evident. It may be the Linux slang for it so we can all avoid having to use that W word.

---

### Post by kelbizzle on 2006-12-04
Theres no such thing as a stupid question. :-D It'd be more stupid if you didn't ask. Knowlegde is power.

---

### Post by stupidkid on 2006-12-04
> **kelbizzle said:**
> Theres no such thing as a stupid question.
Yea, just a lot of inquisitive idiots. :p

---

### Post by gentlemanmasher on 2006-12-07
This is why I love Ubuntu.  Never feel dumb for asking a question.

---

### Post by blacklantern on 2006-12-16
Actually, the windows key is not working for me. Might I have something else being set as the super key by default?

---

### Post by mcduck on 2006-12-16
make sure that you have right keyboard configuration in System/Preferences/Keyboard. 101-button keyboards don't have the super key so if your configuration is set to 101 the button won't work.

Generic 105-key should work, if any of other options doesn't fit.

btw, it's the 'Windows-key' that's strange slang. It's not their invention, Super key was used on some Unix systems before Windows. The original logo on the key was a diamond or a square standing on it's corner..

---

### Post by blacklantern on 2006-12-16
The layout was originally 'Unknown.' I changed it to the only Generic 105 option I saw:

Generic 105-key (Intl) PC. 

Even after I restart my machine, the super-key doesn't seem to be doing anything.

Of course, this is only eye-candy. I'm sure people have way more serious problems than me.

---

### Post by jordanmthomas on 2006-12-16
Maybe try going to system | preferences | keyboard
then, go to the layout tab and click on Alt / Win behavior
Tell it to map super to the winkeys...although this is already the default behavior, maybe it will help some.

If for some reason it doesn't, you can run xev from a terminal and hit your windows key to see what it is recognized as.

---

### Post by blacklantern on 2006-12-17
I had already tried to explicitly assign the super key to the windows key, but to no avail. When I run xev and press the windows key, it looks like it registers as the super key:

```

KeyRelease event, serial 31, synthetic NO, window 0x2600001,
        root 0x52, subw 0x0, time 240209430, (222, 118), root:(277, 624),
        state 0x0 keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
        XLookupString gives 0 bytes:
        XFilterEvent returns: False

```


Also, if it helps, I'm using a logitech MX DUO wireless keyboard.

---

### Post by jordanmthomas on 2006-12-17
Well, you have a few options:
1.  In system | preferences | keyboard --> Layout Options, you can try to pick a keyboard that will work for you...or 
2.  ```
nano ~/.Xmodmap
```
put this in there:
```
keycode 115 = Super_L
```
Then, go to system | preferences | sessions 
and add this to be started upon login
```
/usr/bin/xmodmap $HOME/.Xmodmap
```, where $HOME is your home directory (not sure if variables work in this location, but they should, so $HOME might work by itself

Before you add it to the startup, try running the xmodmap command in a terminal to make sure it doesn't complain about Super_L not being valid.  If it does, I am not sure what you need to do.  :(

****edit****  d'oh!  it seems your key is already recognized as Super_L.  I should totally learn to read.  So basically, beryl should see it fine.  I am not sure what the problem is.  I'll leave all the stuff I typed above in case it might help someone else though.  :-k

---

### Post by steveneddy on 2006-12-17
> **gentlemanmasher said:**
> This is going to sound stupid I know but what is the super key in Beryl?  I have it installed I just want to try all of the effects.

The "Super" key is the windows key on the left. The right windows key is called the "Hyper" key.

This goes back the old days of Unix, before windows. Too bad that it couldn't have stayed that way.

---

### Post by tristangrimaux on 2006-12-20
Same thing here: int keyboard 105, it's a Logitech iTouch Keyboard, the win keys are detected as 115 and 116 (Super_L and Super_R) but the super keys are not working as a composition keys, I depress the Super_L and any other key and I get the code of the other key.

---

### Post by lyceum on 2006-12-20
Is there a way to re-assign the super key to some other key? That seems like an easier solution, but it may not be.

:-k

---

### Post by SmiLey497 on 2006-12-20
my super key didn't work so i changed the button command to shift :)

---

### Post by lyceum on 2006-12-20
> **SmiLey497 said:**
> my super key didn't work so i changed the button command to shift :)

How did you do that? Mine doesn't work either and I'd rather just use another button

---

### Post by jornahow on 2006-12-20
I don't know if this will help you, but when i had problems activating some of the beryl functions like cube rotation when the key and mouse click combos did not work , I stumbled on the beryl settings menu general and some specific options; under the keyboard tab there is a "grab key" function.  I used this to  see how beryl recognized various keys, including my windows keys (identified by beryl as super right and super left).  I then used those values to configure keyboard and mouse combos for the functions i wanted to implement and they worked.  hope this helps.

jornahow

---

### Post by VortexICS on 2006-12-23
What happens to users that have Thinkpads ? TP do not have superkeys (winkeys)

---

### Post by rusty4r on 2007-02-25
Speaking of alternate keyboards, my usual keyboard is Micro Smart Office keyboard and even the "F" keys at the top do not work. I couldn't find a linux driver for it so now it's sitting in the corner and I'm using a plain keyboard that I hate. 
anybody know how to get my "F" keys working on the other keyboard?

---

### Post by linbetwin on 2007-02-26
I found a fix to make the Super key work with Beryl. I thought the problem only existed in KDE, but it seems it affects GNOME too.

[http://ricaradu.blogspot.com/2007/02/how-to-enable-super-key-when-using.html](http://ricaradu.blogspot.com/2007/02/how-to-enable-super-key-when-using.html)

---

### Post by antiwhack on 2007-03-17
so yeah, first post.
I fixed the problem by loading up in GNOME instead of XGL and going to System > Preferences > Keyboard >> Layout Options and changing the Alt/Win key behavior to "Super is mapped to the Win-Keys"

Make sure you have the 105-key set up as well in the layout tab.

---

### Post by the_master on 2007-05-05
I've tried everyone in this thread and some others, and still nothing.  My super key doesn't work, and for some reason when i try to start rain in beryl it doesn't work, but yet shift works any other time.  anyone have an ideas?

---

### Post by kpel on 2007-05-05
> **the_master said:**
> I've tried everyone in this thread and some others, and still nothing.  My super key doesn't work, and for some reason when i try to start rain in beryl it doesn't work, but yet shift works any other time.  anyone have an ideas?

As stupid as it'll sound I'm going to toss it out there anyway: make sure your keyboard doesn't have a switch to turn off the 'Windows' keys.  Mine does and it drove me nuts until I remembered it as I'd always left it off in XP so that I wouldn't accidentally minimize a game.

---

### Post by the_master on 2007-05-05
> **kpel said:**
> As stupid as it'll sound I'm going to toss it out there anyway: make sure your keyboard doesn't have a switch to turn off the 'Windows' keys.  Mine does and it drove me nuts until I remembered it as I'd always left it off in XP so that I wouldn't accidentally minimize a game.

Unfortunately i don't, it wouldn't be that easy, but thanks for trying.

---

### Post by overdrank on 2007-05-05
> **linbetwin said:**
> I found a fix to make the Super key work with Beryl. I thought the problem only existed in KDE, but it seems it affects GNOME too.

[http://ricaradu.blogspot.com/2007/02/how-to-enable-super-key-when-using.html](http://ricaradu.blogspot.com/2007/02/how-to-enable-super-key-when-using.html)

Hello you know if it is posted here I will try it and it works thanks! :guitar:

---

### Post by Campingman on 2007-05-05
Another stupid question, what is the super key supposed to do, mine does nothing.

---

### Post by freebird54 on 2007-05-05
Another Hijack attempt. :)  Anyone how to FAKE a Super key?  Still have a 101 keyboard going...

---

### Post by the_master on 2007-05-05
> **overdrank said:**
> Hello you know if it is posted here I will try it and it works thanks! :guitar:

Did you get it to work in kde or ubuntu?  Cause i couldn't find how to fix it in ubuntu in that link.

---

### Post by prof1337 on 2007-07-14
Sorry to bring up an old thread with my first post, but I think I found a solution to this problem on [[COLOR="Blue"]this blog[/COLOR]]("http://tnlessone.wordpress.com/2007/01/21/playing-with-beryl/"):

> Today I played a bit with Beryl. But firstly I needed to get the Super Key (Windows Key on Keyboard) working, this was accomplished by modifying Keyboard Section “InputDevice” in /etc/X11/xorg.conf with the following :
```
Option "XkbOptions" "altwin:super_win"
```

In my particular situation, the super key wasn't working at all--it seemed like it was pressed down all the time. Adding just this one line to my xorg.conf finally fixed the issue. I hope this helps!

---

### Post by OutCell on 2007-07-30
What about thinkpad keyboards?

---

### Post by mintochris on 2007-12-01
i had an issue where this would randomly disable itself for everything except zooming after afew boots, and swapping the setting in system | preferences | keyboard between default and map super to win (the same thing!) would fix it for the next few boots. I resolved it in the end by sticking with the latter (map super to win) and restarting repeatedly. It seemed sticking with one of them eventually cleared it up. Not much help to you at the moment, but my problem started with your symptoms!

---

