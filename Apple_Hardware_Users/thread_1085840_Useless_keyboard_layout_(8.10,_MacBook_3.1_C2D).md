---
title: "Useless keyboard layout (8.10, MacBook 3.1 C2D)"
date: 2009-03-03
forum: Apple Hardware Users
---

### Post by Eirik W on 2009-03-03
Hello,

I have recently installed Ubuntu 8.10 (single boot, 32-bit) on my Apple MacBook (3.1/late 2007 edition), and apart from one major issue, I am quite satisfied with my new operating system -- and I would rather not have to go through the hassle of installing another distribution, or even OS X, to fix it.

My problem is with keyboard layouts. I am a writer, and as it turns out, a range of symbols and signs is either fully unavailable or very inconveniently located on my keyboard after the switch -- ranging from the crucial and commonplace apostrophe and dollar sign, to more exotic ones, such as braces, brackets, backslash and so forth. I have tried both the "Macintosh" and "Macintosh (eliminate dead keys)" layouts for my language, Norwegian, as well as changing the keyboard model from the default, "Generic 105-key keyboard (Intl)" to "Apple", "Apple Laptop", "MacBook/MacBook Pro (Intl)" and "MacBook/MacBook Pro". The last two options produce the following error message:

```
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10502000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

These commands produce the following output:

```
$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "no", "mac", ""
_XKB_RULES_NAMES(STRING) = "evdev", "apple", "no", "mac", "apple:badmap"
$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
layouts = []
model = macbook78
options = [compat   apple:badmap]
```

Ideally, I would like a keyboard layout which corresponds to the Norwegian layout used in Mac OS X, which I -- perhaps naively? -- expected to get after having selected the Macintosh (Norwegian) layout. If that is unattainable, it is still absolutely necessary that the apostrophe be readily available, preferrably through a key combination which is as simple as possible. I also need access to braces, brackets and backslash. Why do these things have to be so complicated in GNU/Linux? I can only imagine how someone less technologically literate than me would struggle with this situation...

Although this issue has probably been brought up on numerous other occasions, I still think it is legitimate to create a new thread, as a) this concerns the latest version of Ubuntu, which many of the other threads produced by moderate googling do not and b) I have found no resources pertaining to my particular keyboard layout.

Thanks in advance!

---

### Post by cyberdork33 on 2009-03-03
Unfortunately, I think this is a bug and there is no immediate fix for this sort of thing. You can use methods of keymapping to map one key to another value, but the real problem with your layout is that the layout is buggy, and your language is not the only one. Have a look though launchpad.net where the bugs against ubuntu are kept.

---

### Post by Eirik W on 2009-03-03
If it can be done through keymapping, then keymapping it is. How does that work?

Also, what is the locus of the issue -- GNOME, some underlying Ubuntu oddity or something altogether different?

---

### Post by cyberdork33 on 2009-03-03
> **Eirik W said:**
> If it can be done through keymapping, then keymapping it is. How does that work? Look into xmodmap?

> **Eirik W said:**
> Also, what is the locus of the issue -- GNOME, some underlying Ubuntu oddity or something altogether different?
There are kernel issues, and there are Gnome layout issues.

---

### Post by _mario_ on 2009-03-05
> **Eirik W said:**
> 
Also, what is the locus of the issue -- GNOME, some underlying Ubuntu oddity or something altogether different?

neither of them. in contrast to cyberdork's reply, the problem (and the only one) is the X server itself, because you're trying to use the norwegian layout in particular its apple variant. there aren't much people in the world requiring this setup, and hence, this layout is simply buggy. 

using the model "Generic 105-key keyboard (Intl)" (auto-detected) or "MacBook/MacBook Pro (Intl)" shouldn't make any difference - both should work correctly. however, the latter one has to be set by GNOME during session startup which causes the error you observed - a known bug in Intrepid.

in order to solve your keyboard problem it's sufficient to find a working less buggy layout and/or variant. did you try the standard (PC-style) norwegian layout? does it work?

ciao,
Mario

ps: intrepid uses the evdev driver/framework for input instead of the older xinput, where the kernel emits different keycodes. maybe not all layouts are adapted properly. hence, jaunty might work better.

---

### Post by cyberdork33 on 2009-03-05
> **_mario_ said:**
> ps: intrepid uses the evdev driver/framework for input instead of the older xinput, where the kernel emits different keycodes. maybe not all layouts are adapted properly. hence, jaunty might work better.Well, that would be the kernel issues I was referring to, but they might not be a problem anymore.

The layouts are screwed up for several languages of Apple keyboards, so don't feel left out :)

---

### Post by Joushou on 2009-03-12
Same problems with apple-layout in danish :/
And it's getting really annoying... wasting a lot of time looking for { and } on the keyboard when programming... also $ and @... and actually all other special characters...

Oh yeah, and remember, it's not a bug, but a "randomly generated feature" ;)

UPDATE:
Also, i've just checked the graphical representation of the keyboard layout, "Denmark Macintosh", and theres only 2 differences between "Denmark" and "Denmark Macintosh", and it's the same on both intrepid and jaunty... can't be a bug, just "unfinished work" i think :/

---

### Post by cyberdork33 on 2009-03-12
> **Joushou said:**
> UPDATE:
Also, i've just checked the graphical representation of the keyboard layout, "Denmark Macintosh", and theres only 2 differences between "Denmark" and "Denmark Macintosh", and it's the same on both intrepid and jaunty... can't be a bug, just "unfinished work" i think :/well, that would be a bug then :)

---

### Post by Joushou on 2009-03-12
Hmm? I don't think a wrong keymap would be a bug... unless it actually got the right keymap, but can't figure out how to read it :)
Anyway, i hope this is gonna get fixed soon, it's driving me nuts... and i'm too lazy to remap the keys myself :) (144 entries, mapped to option, shift and shift-option... just too much, and i don't know the position of all spec. chars anyway :P)

---

### Post by cyberdork33 on 2009-03-13
> **Joushou said:**
> Hmm? I don't think a wrong keymap would be a bug... unless it actually got the right keymap, but can't figure out how to read it :)
Anyway, i hope this is gonna get fixed soon, it's driving me nuts... and i'm too lazy to remap the keys myself :) (144 entries, mapped to option, shift and shift-option... just too much, and i don't know the position of all spec. chars anyway :P)
If there is an (reasonable) expected functionality, and appears that it should already work (i.e. If the layout is there for me to select), and it does not work, then that is a bug. It would not be a bug necessarily if the layout did not exist, and instead might be considered a feature request (though I think that it could be argued a bug still in that case as well.)

---

### Post by _mario_ on 2009-03-13
> **Joushou said:**
> Hmm? I don't think a wrong keymap would be a bug... unless it actually got the right keymap, but can't figure out how to read it :)

since keymaps are usually somewhat standardized, this is definitely a bug.

> **Joushou said:**
> 
Anyway, i hope this is gonna get fixed soon, it's driving me nuts... and i'm too lazy to remap the keys myself :) (144 entries, mapped to option, shift and shift-option... just too much, and i don't know the position of all spec. chars anyway :P)

sorry, but don't expect it to be fixed soon. we've heard the same problems 2 years ago in gutsy and it's sill not working.

however, what about contributing to free software and fixing your keymap yourself? i can help you, but i don't know how a danish keyboard looks like.

for a quick check: do the standard (PC-style) layouts (dk(basic), dk(nodeadkeys)) work? if yes it's usually only a matter of a few keys to get the mac variant right, e.g., 18 keys for the german layout. and you can use OSX to determine how it should be.

ciao,
Mario

---

### Post by Joushou on 2009-03-13
Well, i still wouldn't call it a bug (It shows me what it's giving me, therefore the keymapper is giving me the right results, just wrong keymap), but lets just call it a bug :D

And sure, i don't mind doing it myself, just don't know where/how the keymaps are stored.
PC-layout "works" from the live-cd (Currently redownloading, i messed up the FS of both osx and ubuntu yesterday), but theres no ISO_Level3_Shift key (alt-gr), so many spec. chars are unavaliable... and when i was within the OS, it set Alt_L to be ISO_Level3_Shift, therefore no real alt key...
Can you map it to use alt instead of level3-shift?

But anyway, if you could give me a hint or 2 about generating a new keymap (I know how to change it live with xmodmap, but this doesn't seem optimal), i'll throw a danish keymap together :) (And i believe Danish and Norwegian keyboards are the same, except æ, å and ø are different (ö or something), so that would solve the original problem aswell :) )

---

### Post by _mario_ on 2009-03-13
> **Joushou said:**
> 
And sure, i don't mind doing it myself, just don't know where/how the keymaps are stored.

keymaps are stored in /usr/share/X11/xkb/symbols/. each file is one layout, e.g., de or dk. (some are helpers or common subsets.) each file is divided into sections that start with some flags, the keyword 'xkb_symbols', and its name. these sections (some are for internal use only) usually refer to different variants of the same layout.

a section might contain:
```
include "latin(type2)"
```
which states to include section type2 from file latin into this section to inherit all mappings from there.

the most important lines look like this:
```
key <AE11> { [      plus,   question,    plusminus, questiondown ] };
```
this line defines 4 keysyms for a key named '<AE11>'. those 4 keysyms correspond to the 4 shift states:
[LIST=1]
[*]plain key
[*]shift + key
[*]level3-shift + key
[*]level3-shift + shift + key
[/LIST]
you may also use NoSymbol to omit one of them.

one short note about keycodes: keycode names such as '<AE11>' are defined in /usr/share/X11/xkb/keycodes. however, there are 2 files important. xfree86 if you're using the older xinput driver, and evdev if you're using the newer evdev driver. check your Xorg startup messages. if you didn't configure anything else it's most likely evdev.

to get the key's name do the following:
[LIST=1]
[*]run xev and press your key.
[*]the output contains:
```

state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,

```
the keycode is important. (the keysym serves well to later check the result.)
[*] now run:
```

# grep 54 xfree86
<AB03> =  54;

```
[*]the name to specify a rule for is: <AB03>
[/LIST]

> **Joushou said:**
> 
PC-layout "works" from the live-cd (Currently redownloading, i messed up the FS of both osx and ubuntu yesterday), but theres no ISO_Level3_Shift key (alt-gr), so many spec. chars are unavaliable... and when i was within the OS, it set Alt_L to be ISO_Level3_Shift, therefore no real alt key...
Can you map it to use alt instead of level3-shift?

by default (in linux not OSX), level3-shift should be mapped to the right alt key, while the left one is meta (what we usually call alt). in a german layout i don't have to do anything. it just works, as expected. it should do as well in danish, because the last line in section dk(basic) is:
```
include "level3(ralt_switch)"
``` to accomplish exactly that.

> **Joushou said:**
> 
But anyway, if you could give me a hint or 2 about generating a new keymap (I know how to change it live with xmodmap, but this doesn't seem optimal), i'll throw a danish keymap together :)

just edit and fix the existing one. happy hacking. ;-) or: for better testing create a new file like dk-fixed and run:
```
setxkbmap -model pc105 -layout dk-fixed -variant mac
```
to immediately activate your mapping. if you'd like to get it upstream, it's advisible to check and maybe fix all of them.

ciao,
Mario

---

### Post by Joushou on 2009-03-13
Well, the problem with using right alt-key is... that there isn't one on danish mbp3,1 ;)
It's an extra return button... But i guess i can survive with a remap (Maybe remap that to alt, to get the special chars right...)
I just wish it was more flexible (like, setting "keycode 64 + keycode 50 = )", so i could use my only option/alt-key for both meta and iso-level3-shift...)

I'll have a look at it this weekend, and see how much i'll get done... and ofcourse, it's easier to get it upstream if you've fixed everything, but then again, i'm still lazy... i'll see what i can do though :)

---

### Post by Joushou on 2009-03-13
Heh, i just checked the directory macintosh_vndr... it contains the correct danish keyboard layout :)

Adding the basic section (and ofcourse, renaming it) works, but the subsections gives it hickups (And ofcourse, it's a very "detailed" "error loading keymap" message...).
But the most important part, is that i've figured that X actually does accept shift, alt and shift+alt as modifier keys, instead of ISO_Level3_Shift, meaning that it's possible to complete the macintosh keymap, and still maintain alt functionality on my alt key :D (Instead of remapping it to level3)

Do you have any idea why subsections might complain (Syntax should be OK, everything but the title is copy-pasted from the macintosh_vndr, and it works there...)

---

### Post by buntuLo on 2009-03-13
> **_mario_ said:**
> keymaps are stored in /usr/share/X11/xkb/symbols/
(...)
great explanation, thank you very much Mario!

i managed to trace back the correct rule for the only key which was not properly mapped for me, the '§/±' key. i found it in the 'macintosh' variant of the 'us' layout.
```
setxkbmap -model macbook79 -layout us -variant mac
```

i tried all possible keyboard models in system settings before, now i realise that the important setting is the layout variant, more than the model. 'generic pc 105' or 'Macbook/Pro/Intl' doesn't make any difference for me, while with the 'mac' variant i get the perfect keyboard layout :~)

i actually have a dutch keyboard, but this is supposed to be identical to the us one (apart from the size of the return key, they say..). if anybody in here with a standard-us keyboard on Macbook/Pro 5,1 confirms me that they also have the '§/±' key just below 'esc' and this configuration works, i can add it in the wiki pages.

still, 'eject' and 'audiomute' do not work for me, even though xev shows a correct configuration for them.
kmix pops up the volume status and does nothing for 'audiomute', i guess it has to do with the buggy alsa support for this machine.
while i don't have any idea about the 'eject' key, xev gives me:
keycode 169 (keysym 0x1008ff2c, XF86Eject)
any hint about it?

ciao, Lo.

---

### Post by _mario_ on 2009-03-16
> **Joushou said:**
> Heh, i just checked the directory macintosh_vndr... it contains the correct danish keyboard layout :)
congrats! btw: dk(mac) in symbols/ states that the definition is "Copied from macintosh_vndr/dk". but obviously it is not.

> **Joushou said:**
> 
Adding the basic section (and ofcourse, renaming it) works, but the subsections gives it hickups (And ofcourse, it's a very "detailed" "error loading keymap" message...).

setxkbmap internally uses xkbcomp the XKB keymap compiler to generate a machine description out of these plain files. hence, just invoke the compiler manually for checking (it looks like this tool always exits with error code 1.):
```
xkbcomp -w 10 /usr/share/X11/xkb/symbols/dk
```

> **Joushou said:**
> 
But the most important part, is that i've figured that X actually does accept shift, alt and shift+alt as modifier keys, instead of ISO_Level3_Shift, meaning that it's possible to complete the macintosh keymap, and still maintain alt functionality on my alt key :D (Instead of remapping it to level3)
how does this work? technically and conceptionally? i mean: if you press alt+c, what is it? '¢' (cent symbol with my layout) or menu shortcut with character 'c'? that's the main idea behind alt(meta) and altgr(iso-level3).

> **Joushou said:**
> 
Do you have any idea why subsections might complain (Syntax should be OK, everything but the title is copy-pasted from the macintosh_vndr, and it works there...)
attach the source! otherwise: no ;-)

ciao,
Mario

---

### Post by Joushou on 2009-03-16
> **_mario_ said:**
> congrats! btw: dk(mac) in symbols/ states that the definition is "Copied from macintosh_vndr/dk". but obviously it is not.
Well, i after a couple of days of use, i figured that it was only partial done aswell... but it got the @ right :D

> **_mario_ said:**
> setxkbmap internally uses xkbcomp the XKB keymap compiler to generate a machine description out of these plain files. hence, just invoke the compiler manually for checking (it looks like this tool always exits with error code 1.)
The compiler doesn't say anything either, with highest warning level :/
(Heres the modified parts of dk: [http://paste.org/5951](http://paste.org/5951) (I removed the original mac subsection))

> **_mario_ said:**
> how does this work? technically and conceptionally? i mean: if you press alt+c, what is it? '¢' (cent symbol with my layout) or menu shortcut with character 'c'? that's the main idea behind alt(meta) and altgr(iso-level3).
Sure, i get your point... But i believe it would write "c" if you're in a text-field accepting it... I can't remember how OS X handled it, but having to use the right hand for level3 isn't optimal, and i also want alt on the correct key... i'll see how it works when i figure how to define my own modifier-maps...

> **_mario_ said:**
> attach the source! otherwise: no ;-)
Tsk, your psychic abilities suck ;)

You don't know how hard it is to make a keymap, when you don't know the names of the characters... and when i don't know the os x keymap fully, it makes this even more fun :D
Also, i can tell my bash-fu has degraded a bit... my fancontrol script is having some odd bugs... :/

Anyway, thanks for the help so far... lets see how much i get out of this :)

---

### Post by kevpatts on 2010-02-11
> **Joushou said:**
> Heh, i just checked the directory macintosh_vndr... it contains the correct danish keyboard layout :)

Adding the basic section (and ofcourse, renaming it) works, but the subsections gives it hickups (And ofcourse, it's a very "detailed" "error loading keymap" message...).
But the most important part, is that i've figured that X actually does accept shift, alt and shift+alt as modifier keys, instead of ISO_Level3_Shift, meaning that it's possible to complete the macintosh keymap, and still maintain alt functionality on my alt key :D (Instead of remapping it to level3)

Do you have any idea why subsections might complain (Syntax should be OK, everything but the title is copy-pasted from the macintosh_vndr, and it works there...)
Joushou, would you be able to tell me which file you modified and what you did to achieve this? I'm in Ireland and Having trouble that if I change my keyboard Model to either "MacBook Pro" or "MacBook Pro (Intl)" BOTH my ALT keys return ISO_Level3_Shift (layout: Great Britain).

The keys return keycodes 64 and 108 but I can't find any mapping of either of these codes to anything really. I'm using evdev driver.

---

### Post by Joushou on 2010-02-12
The keycodes-mapping can be found in /usr/share/X11/xkb/keycodes/evdev. As you can see, it handles 64 as LALT and 108 as RALT, so it's mapped correctly there.

The keymap itself is located in /usr/share/X11/xkb/symbols/gb. As you can see, it includes "level3(ralt_switch_multikey)", and there RALT is mapped to ISO_LEVEL3_Shift.

I've just checked your keymap, and it doesn't seem it defines a function for LALT... add this in between the other mapped keys of gb, in the profile you're using:

key <LALT> {
    type[Group1]="TWO_LEVEL",
    type[Group2]="TWO_LEVEL",
    type[Group3]="TWO_LEVEL",
    type[Group4]="TWO_LEVEL",
    symbols[Group1] = [ Alt_L, Meta_L ],
    symbols[Group2] = [ Alt_L, Meta_L ],
    symbols[Group3] = [ Alt_L, Meta_L ],
    symbols[Group4] = [ Alt_L, Meta_L ]
    };
  modifier_map Mod1    { <LALT> };

If you'd rather have LALT to be iso_level3_shift, change the "include level3(ralt_switch_multikey)" to "include level3(lalt_switch)", and change the L's above to R's (RALT, Alt_R and Meta_R).

Hope that helps!

---

