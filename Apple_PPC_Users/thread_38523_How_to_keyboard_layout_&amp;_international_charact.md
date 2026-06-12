---
title: "How to: keyboard layout &amp; international characters?"
date: 2005-05-31
forum: Apple PPC Users
---

### Post by ipixel on 2005-05-31
Could one of the more experienced Ubuntu/Kubuntu users answer:

1) Which keyboard layout should a desktop Mac user select? 
Apple has used basically the same desktop layout since the original iMac, so I'm guessing there MUST be a layout that is fully compatible in the Ubuntu/Kubuntu list of pre-installed models, however every one I pick is wrong.

2) Using the specified keyboard layout, how can one type the following characters:

a) © - copyright symbol
b) ç - c cedilla
c) ñ, ã, õ  - n, a and o with tilde (used in Spanish and Portuguese)
d) ü, ä, ö - u, a and o with umlaut (used in German, French and Portuguese)
e) ?, ?, ?, ?, ? - c, g, h, j and s with circumfles (used in Esperanto)
f) ? - u with breve (used in Esperanto)

Regardless of whichever keyboard layout I pick, I can NEVER type these characters. Are there options that should be turned on somewhere? What do we need to do?

-----------------
This has been a *REAL* deal breaker for me. I have been forced to go back to MacOS, as in the Mac I can type all of the above characters simply using the 'US Extended' keyboard layout. In Ubuntu/Kubuntu, I've struggled for over 2 weeks, and still cannot find a way to type them all.

Any help or hints much appreciated.

---

### Post by calum on 2005-06-01
I used XKeyCaps to get things to my liking on my Powerbook... might work for you too.  [This version](http://pbbuttons.sourceforge.net/projects/xkeycaps/download.html) includes a Powerbook keyboard map, which might be a good starting point.

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=ipixel]Could one of the more experienced Ubuntu/Kubuntu users answer:

1) Which keyboard layout should a desktop Mac user select? 
Apple has used basically the same desktop layout since the original iMac, so I'm guessing there MUST be a layout that is fully compatible in the Ubuntu/Kubuntu list of pre-installed models, however every one I pick is wrong.

2) Using the specified keyboard layout, how can one type the following characters:

a) © - copyright symbol
b) ç - c cedilla
c) ñ, ã, õ  - n, a and o with tilde (used in Spanish and Portuguese)
d) ü, ä, ö - u, a and o with umlaut (used in German, French and Portuguese)
e) ?, ?, ?, ?, ? - c, g, h, j and s with circumfles (used in Esperanto)
f) ? - u with breve (used in Esperanto)

Regardless of whichever keyboard layout I pick, I can NEVER type these characters. Are there options that should be turned on somewhere? What do we need to do?

-----------------
This has been a *REAL* deal breaker for me. I have been forced to go back to MacOS, as in the Mac I can type all of the above characters simply using the 'US Extended' keyboard layout. In Ubuntu/Kubuntu, I've struggled for over 2 weeks, and still cannot find a way to type them all.

Any help or hints much appreciated.[/QUOTE]
 Maybe this can be of some help (this is for PCs, not Macs, and is for GNOME users, though): 


[http://ubuntuforums.org/showthread.php?t=30070](http://ubuntuforums.org/showthread.php?t=30070)

---

### Post by ipixel on 2005-06-25
Sorry, but none of the help proposed above seems to work.

XKeyCaps no longer works in Ubuntu - you cannot scroll properly to select the appropriate keyboard layouts, and the whole thing behaves *really* buggy, and ends up being of no help at all.

The thread pointed to above sheds absolutely no light whatsoever on how to type the characters I need, using a standard Apple USB extended keyboard. Which keyboard layout should I choose? The methods described (pressing Control or Option + a sequence of unicode codes or numbers) produces absolutely nothing, regardless of whatever options I might have selected.

So, it's back to OS X for me. I cannot live without being able to type the characters I need, and after wasting a PHENOMENAL amount of time browsing through manuals, searching on Google - and other search engines, installing several (totally useless) packages, and posting several messages on user help boards (such as this) and receiving absolutely NO useful help whatsoever - apart from a couple of well-intentioned replies - I think it is quite obvious that this system is *most certainly* NOT ready for international. 

Please, if anyone is interested, post a bug relating to this inability to select and type international and alternate characters.

Thanks.

---

### Post by Rxke on 2005-06-29
This is a serious irritation for me, too.
Using the french qwerty layout, on one of those original 'small' keyboards that came with the first colored towers and iMacs,  I'm frustrated after a new install to find the '@' character is not where it's supposed to be, and don't start me about international chars, I could go on all night...  And having to edit my keyboard layout, it's not compatible with the 'it just works' adage of Ubuntu.
We should clamour  to add some generic mac layouts in the installer, there are maybe 4 or five models since the newworld macs came out... So that wouldn't be too much to ask, no?

---

### Post by maximum on 2005-06-29
[QUOTE=ipixel]Sorry, but none of the help proposed above seems to work.

XKeyCaps no longer works in Ubuntu - you cannot scroll properly to select the appropriate keyboard layouts, and the whole thing behaves *really* buggy, and ends up being of no help at all..... cuttttt
[/quote]

Hi,

ie used the xmodmap solution for my pbook and imac

note: the article is in italian but the layout is for spanish layout too but you can adapt it easly

here the link:

[http://www.maximumdebian.org/modules.php?op=modload&name=News&file=article&sid=358](http://www.maximumdebian.org/modules.php?op=modload&name=News&file=article&sid=358)

i hope that can help


best,
MaX

---

### Post by M-Rick on 2005-07-18
[QUOTE=Rxke]This is a serious irritation for me, too.
Using the french qwerty layout, on one of those original 'small' keyboards that came with the first colored towers and iMacs,  I'm frustrated after a new install to find the '@' character is not where it's supposed to be, and don't start me about international chars, I could go on all night...  And having to edit my keyboard layout, it's not compatible with the 'it just works' adage of Ubuntu.
We should clamour  to add some generic mac layouts in the installer, there are maybe 4 or five models since the newworld macs came out... So that wouldn't be too much to ask, no?[/QUOTE]

right, i am agree

---

### Post by ixx on 2005-08-22
For CJK I suggest [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/), but for spanish, portugese, french, german, esperanto and other such language after having all the correct fonts installed (which seems to happen by default with ubuntu) then you can easily use xmodmap for adding the ability to type fun characters like &#265;, &#285;, &#365;, etc..

I personally only care to use esperanto characters right now... So I created a xmodmap file to turn the windows keys into AltGr (mode switch key.. common on international keyboards).

Here is what I have:

! ---------- CUT HERE -------------

! Uzi AltGr kun ne internacia klavoj
! left/right windows-logo key
! in "windows" keyboards the postion of the key is annoying, is where AltGr
! usually resides, so go define it as AltGr
keycode 115 = Mode_switch
keycode 116 = Mode_switch

! &#265;i tiu de [http://bertilow.com/komputo/linukso.html](http://bertilow.com/komputo/linukso.html)
! Baza solvo por tajpado de Esperantaj supersignaj literoj estas uzado de la
! klavo AltGr. Por fari tion oni skribu en sia dosiero “.Xmodmap” la jenajn
! liniojn, kiuj modifas la aktualan klavararan&#285;on:

keycode 54 = C NoSymbol ccircumflex
keycode 42 = G NoSymbol gcircumflex
keycode 43 = H NoSymbol hcircumflex
keycode 44 = J NoSymbol jcircumflex
keycode 39 = S NoSymbol scircumflex
keycode 30 = U NoSymbol ubreve

! Tiam AltGr-c kreas “c”-on kun cirkumflekso, kun aldona majuskliga klavo &#285;i
! kreas “C”-on kun cirkumflekso, k.t.p.

! ---------- CUT HERE -------------

Save that to a file (say .xmodmap-eo).  Then type 'xmodmap <filename>' (eg. xmodmap .xmodmap-eo).  You can add that to your startup file (possibly .xsession or .xinitrc) if desired.

So WindowsKey+C creates &#265; ( use shift+AltGr+c to get &#264; ).

If you need multiple layouts you could have multiple xmodmap files.. and even have say Shift-Ctrl+F# switch between them (you would have to set that up of course.. look into gnome hot keys.. or whatever other solution you want to use).

---

### Post by BROKEN_LADDER on 2005-11-14
[http://ubuntuforums.org/showthread.php?t=90040](http://ubuntuforums.org/showthread.php?t=90040)

that should answer all your problems folks.  i've seen all the bad help, and finally figured it out myself.

---

### Post by Rxke on 2005-11-15
Very good one, i bookmarked it and rated that thread "excellent" rightaway! :thumbsup:

---

