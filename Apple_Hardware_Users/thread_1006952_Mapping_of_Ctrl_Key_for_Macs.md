---
title: "Mapping of Ctrl Key for Macs"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by undoIT on 2008-12-09
Currently the **Ctrl** key is mapped to **control** when running Ubuntu on a Mac. What do you think about mapping **Ctrl** to the **command** key? This would more accurately reflect the functionality in OS X.

The problem I'm running into is that when I am using an external mouse on my MacBook, I use it left handed. There is only one control key on Macs and it is on the left side of the keyboard. So, if I have my left hand on the mouse and need to do something that requires a **Ctrl** key combination it is pretty akward. And, the little **control** key is not all that convenient for regular usage.

---

### Post by _mario_ on 2008-12-10
what about leaving the mapping as is (i.e., ctrl key is control and cmd key is command) and adding a site to the forum that describes how to easily swap the keys if someone likes that?

ciao,
Mario

---

### Post by hyperboloid on 2008-12-10
> **_mario_ said:**
> what about leaving the mapping as is (i.e., ctrl key is control and cmd key is command) and adding a site to the forum that describes how to easily swap the keys if someone likes that?

ciao,
Mario

I agree with Mario. People choosing Ubuntu Linux expect the keys to work like in Linux. People who prefer Mac OS X like behavior should stick to OS X or reconfigure the settings.

---

### Post by undoIT on 2008-12-10
> **hyperboloid said:**
> People who prefer Mac OS X like behavior should stick to OS X.

No thanks, I never cared for OS X. In the few hours I have used Leopard, I already had the finder crash on me while doing the simple task of trying to open the Utilities folder. You have to run a command in terminal to view hidden files and folders (and after running that you get to see all the .DS_store files wasting space). It is difficult to navigate with the keyboard, etc etc...

Ubuntu is much better.

Another argument for mapping **Ctrl** to the **command** key is that most first time Ubuntu users who would be installing on their Mac are accustomed to OS X. It must be unintuitive for a long time Mac user to have **command** functionality mapped to the **control** key. It just seems to make more sense to have **Ctrl** mapped to **command** as default and then if somebody wants to change it they can remap the keys.

The best would be if Apple started building MacBooks with a standard keyboard, but that isn't gonna happen.

---

### Post by hyperboloid on 2008-12-10
[QUOTE=undoIT] 
Ubuntu is much better.
[/QUOTE]
I agree completely. 
[QUOTE=undoIT] 
Another argument for mapping **Ctrl** to the **command** key is that most first time Ubuntu users who would be installing on their Mac are accustomed to OS X. It must be unintuitive for a long time Mac user to have **command** functionality mapped to the **control** key. It just seems to make more sense to have **Ctrl** mapped to **command** as default and then if somebody wants to change it they can remap the keys.
[/QUOTE]
But a long time Mac user choosing to switch to Linux should expect some differences, and long time Unix/Linux hacks will certainly be very surprised to see Control be something different from Control. The most intuitive thing to map Control to would be ... Control, IMHO. 

Just because Apple has screwed things up with a non-standard keyboard I do not see that as a valid justification for perpetuating Apple's errors of judgement into Linux space. Linux is not Mac, and many folks prefer it that way.

This issue is not worth arguing over, since it is pretty easy to remap the key any way you like. That's what Linux is all about - you can configure anything the way you like it - unlike OS X. With respect for your viewpoint, I just don't agree that the default should cater to Apple's idiosyncrasies.

---

### Post by undoIT on 2008-12-10
That's why I started the thread. To find out if this is an issue for other people and if the majority thinks it would be good to change the default mapping. If not, then there is no point in changing it. 

I'm going to dig into the settings and see how difficult it is to change the default mapping. Never tried before.

I guess the real issue is that Apple's concept for keyboard layout sucks, at least IMO.

---

### Post by undoIT on 2008-12-10
Unless there is some new info I haven't found yet, it doesn't seem to be easy to change the mapping and the solution I found only half works.

First I tried changing System > Preferences > Keyboard > Layouts

I set the keyboard model to: MacBook/MacBook Pro

That didn't change anything. There is no way to specifically map each key in those settings. So I searched and found this thread:

[http://ubuntuforums.org/showthread.php?p=4579588#post4579588](http://ubuntuforums.org/showthread.php?p=4579588#post4579588)

It looks like that hack for ~/.xmodmap only changes the left command key :(

---

### Post by beauman on 2008-12-11
Hi! 

I yesterday proposed in the [ wiki for MB 4,1/Intrepid]("https://wiki.ubuntu.com/MacBook/SantaRosa") to use the left cmd key for  middle mouse click and the right cmd key for  right mouse click emulation.

@ undoIT : When you have figured out, how to configure the keyboard and mouse exactly like on Mac, you should write a small separate wiki. You are very welcome to add a link to [this section here]("https://wiki.ubuntu.com/MacBook/SantaRosa#Middle&Right%20Click%20with%20Left&Right%20Cmd%20Keys"). It would be good, if you could find a way without mouseemu.

I think the idea is not too bad, I prefer the PC-style bindings, but Mac users who used my Intrepid-MacBook always get confused with  the layout. The default should be of cause Ubuntu-style, not Mac OS.

---

### Post by _mario_ on 2008-12-11
> **undoIT said:**
> Unless there is some new info I haven't found yet, it doesn't seem to be easy to change the mapping and the solution I found only half works.

First I tried changing System > Preferences > Keyboard > Layouts
I set the keyboard model to: MacBook/MacBook Pro
That didn't change anything.

the model defines where each key actually is and which keys are available. the layout is the most interesting point. however, there is no layout yet that gives an experience like OSX.

> **undoIT said:**
> 
There is no way to specifically map each key in those settings. So I searched and found this thread:
It looks like that hack for ~/.xmodmap only changes the left command key 

that's what the poster stated. if you like it: the attached xmodmap script allows to swap the left command and control keys (swap-left-command-and-control.xmodmap). additionally, it might be desirable to swap the corresponding right keys as well (swap-right-command-and-control.xmodmap), or map the right command key to control (map-right-command-to-control.xmodmap) in addition to the right control key.

please note, that swapping keys does affect **all** applications including the window manager and **all** keyboards. that means if you'd choose to attach a (normal PC-style) USB-keyboard, those keys will be swapped there as well.

ciao,
Mario

---

### Post by cyberdork33 on 2008-12-11
A key, by default, should perform the function that is printed on the key. If the user would like to change that function, it should be up to them to do so (not that it couldn't be made easier with an option in the keyboard config applet).

---

### Post by ronaldbe on 2008-12-12
Countering the "Stick to OS X" comment, if I had a choice to not use Linux I wouldn't waste the 20 GB of space on my HDD, however since I am required to use it for work then I have no choice. I agree with the original poster that it does feel more intuitive for us mac users since the CMD essentially the same as the CTRL key for the rest of the computer world. There should be an option in the prefs to allow for this...

---

### Post by undoIT on 2008-12-12
Another note on this. The function keys (F1 F2 etc) are mapped like OS X and are not standard. For example, let's say you want to rename a file. You hit F2 and instead of letting you rename the file, it turns up the brightness.

Just for the sake of consideration, let's forget what is printed on the key and think about what the key actually does. In OS X (which is what the Mac keyboard was designed for) the **command** key functions like the **Ctrl** key on any other PC. If we pretend that the **command** key were actually labeled "control" wouldn't it make sense to map **Ctrl** to the **command** key?

---

### Post by cyberdork33 on 2008-12-12
OK, I did a little experimenting. Note that this is with a full Apple Keyboard, not a portable and I am using Gnome.

Go to:
System > Preferences > Keyboard
On the Layouts Tab, select:
Keyboard Model: Apple > Macintosh
Make the Default Layout: USA
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96169&stc=1&d=1229119508[/IMG]

Click the Other Options Button...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96170&stc=1&d=1229119508[/IMG]
Under "Alt/Win key behavior"
"Left Alt is swapped with left Win-key." = swaps the left Cmd and Alt/Option keys (making it the same as a typical PC keyboard layout where the layout is Ctrl - Win - Alt - SpaceBar)
"Control is mapped to the Win-keys (and the usual Ctrl keys)." = Cmd and Ctrl perform the same function (Ctrl) allowing Cmd+c to be Copy, Cmd+v to be paste, etc.

I couldn't find anywhere to make the Ctrl key map to Cmd (or Win or Super for that matter)

---

### Post by undoIT on 2008-12-12
Aha! There it is. Thanks cyberdork! I now have both **command** keys mapped as **Ctrl**. No hacking. I think this would also be handy for Virtualbox users, because the action key is by default mapped to right Ctrl. It can be changed for Virtualbox, but it is nice to not have to.

The built-in screen shot utility is so handy. I just love Ubuntu. Now where is my print screen key? Oh yeah, I'm on my Macbook ;P

I now have 3 **Ctrl** keys. The only thing I'd like to adjust is to make the **control** key function as **Super**. I don't see any way to change this yet.

---

### Post by cyberdork33 on 2008-12-12
> **undoIT said:**
> I now have 3 **Ctrl** keys. The only thing I'd like to adjust is to make the **control** key function as **Super**. I don't see any way to change this yet.
Yea, I couldn't find anything for that either.

---

### Post by Rog-Mahal on 2008-12-12
Hmm, I have my layout as the Macbook/Macbook Pro and use the USA Macintosh scheme. Cyberdork's fix does not work. Any thoughts? (As a side note, I also still get that annoying X.org error every time I boot up saying that there is an error in my keyboard config)

---

### Post by cyberdork33 on 2008-12-12
> **Rog-Mahal said:**
> Hmm, I have my layout as the Macbook/Macbook Pro and use the USA Macintosh scheme. Cyberdork's fix does not work. Any thoughts? (As a side note, I also still get that annoying X.org error every time I boot up saying that there is an error in my keyboard config)
what does the keyboard config look like in your xorg.conf?

```
# Generic Keyboard section
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver    "kbd"
    Option    "XkbModel"    "pc105"
    Option    "XkbLayout"    "us"
    Option    "XkbOptions"    "grp:alt_shift_toggle"
EndSection
```

---

### Post by Rog-Mahal on 2008-12-13
Hmmm, my xorg.conf looks like this:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

...there is no entry for my keyboard. That might be the source of the problem. I haven't messed with xorg.conf before on this installation, so it couldn't have been something I did.

---

### Post by Rog-Mahal on 2008-12-13
.

---

### Post by cyberdork33 on 2008-12-13
technically it shouldn't be *needed* but it can hurt to try adding a section. If you are working on the Macbook (Pro) keyboard, you might want to verify with one of the other users in this thread.

---

### Post by el_heffe on 2008-12-14
> **undoIT said:**
> Aha! There it is. Thanks cyberdork! I now have both **command** keys mapped as **Ctrl**. No hacking. I think this would also be handy for Virtualbox users, because the action key is by default mapped to right Ctrl. It can be changed for Virtualbox, but it is nice to not have to.

The built-in screen shot utility is so handy. I just love Ubuntu. Now where is my print screen key? Oh yeah, I'm on my Macbook ;P

I now have 3 **Ctrl** keys. The only thing I'd like to adjust is to make the **control** key function as **Super**. I don't see any way to change this yet.

A couple of things:
Apple's OS, whether it is System 7,8, 9 or OS X, have always had a screenshot capability.  But I only know that because I have been an apple geek my whole life! :D
As for the key swapping, I was contemplating it, and may do it, but having a PowerBook G4 I might not put too much more effort into this.  I work on XP all day long so the ctrl keys are second nature to me.
Last, but not least- I really really like ubuntu, xubuntu to be specific.  Just so ya know! :p

---

### Post by Rog-Mahal on 2008-12-14
Following cyberdork's advice, can anyone with a Macbook (preferably 2,1) post their xorg.conf and their keyboard/ layout?

---

### Post by undoIT on 2008-12-14
> **el_heffe said:**
> A couple of things:
Apple's OS, whether it is System 7,8, 9 or OS X, have always had a screenshot capability.  But I only know that because I have been an apple geek my whole life! :D
As for the key swapping, I was contemplating it, and may do it, but having a PowerBook G4 I might not put too much more effort into this.  I work on XP all day long so the ctrl keys are second nature to me.
Last, but not least- I really really like ubuntu, xubuntu to be specific.  Just so ya know! :p
Hi el_heffe. I wasn't saying that OS X doesn't have this, I was just saying that I really like the screen shot utility in Ubuntu, especially the ability to capture the active window rather than the entire screen. :)

I did try Xubuntu recently and thought it was very cool. I wish I had more time to tinker with a bunch of different distros.

I have to say, having switched the **Ctrl** functionality to the **command** key and working primarily on my MacBook over the past couple days, it is a big improvement. It is much more intuitive and easy to use. I have no problem adjusting to getting a **Ctrl** click with my thumbs (like it would be in OS X) and now I can use my external mouse with my left hand and easily **Ctrl** select multiple items. Even though I haven't been much of a Mac user for the past 12 years, having **Ctrl** mapped to the **commmand** keys just works better for me.

Maybe this could be made the default for Ubuntu when installed on Macs? At the very least, it would be good to have this mapping when selecting the Mac keyboard layouts (along with **Super** mapped to **control** key) so that people can get a more seamless keyboard experience comparable to OS X. And, if people don't like it, they could switch to the standard keyboard layout with **Ctrl** mapped to **control** key. Just a suggestion.

With Ubuntu working better and better, my MacBook is becoming a sweet little machine :guitar:

---

### Post by Chrisj303 on 2008-12-14
> **undoIT said:**
> Hi el_heffe. I wasn't saying that OS X doesn't have this, I was just saying that I really like the screen shot utility in Ubuntu, especially the ability to capture the active window rather than the entire screen. :)


Mac O SX does that. 

You can;
1.capture entire screen
2.capture timed screen
3.capture selection.
4.capture selected window.


I agree with Cyberdork, by default the key should do what it says on the tin - anything else would just cause much confusion - and these boards have too much of that already.

---

### Post by undoIT on 2008-12-14
> **Chrisj303 said:**
> Mac O SX does that. 

You can;
1.capture entire screen
2.capture timed screen
3.capture selection.
4.capture selected window.

Yes. But I don't have to pay anything for Ubuntu, other than what I chose to donate. And, if I had the skills and wanted to improve the screen shot utility with my own code, I could do so legally.

---

### Post by cyberdork33 on 2008-12-15
> **undoIT said:**
> Yes. But I don't have to pay anything for Ubuntu, other than what I chose to donate. And, if I had the skills and wanted to improve the screen shot utility with my own code, I could do so legally.

OK, let's not make this ANOTHER Ubuntu vs OSX thread. The screenshot utilities in both OSX and Ubuntu are nice to have and a discussion on which is better is something that does not belong in this support forum.

I think the intention of the original comment was to point out the lack of a print screen key on the apple keyboard.

As for the defaults for the keys, I have already stated my stance there. It would be nice if it was more intuitive for the user to swap the keys if they like it better that way. A prompt during installation that asked 'default' or 'OSX-style' key mappings when an Apple Keyboard was chosen as the keyboard type would be ideal, but likely not worth the additional storage required on the cdrom.

---

### Post by undoIT on 2008-12-15
> **cyberdork33 said:**
> As for the defaults for the keys, I have already stated my stance there. It would be nice if it was more intuitive for the user to swap the keys if they like it better that way. A prompt during installation that asked 'default' or 'OSX-style' key mappings when an Apple Keyboard was chosen as the keyboard type would be ideal, but likely not worth the additional storage required on the cdrom.

How difficult is it to edit the mappings in System > Preferences > Keyboard > Layouts? I'm really swamped right now, but if somebody can point me to where the files are, I'd like to take a crack at editing one of the layouts in some spare time. I'd like to try editing the layout for MacBook/MacBook Pro, to map Ctrl to command and Super to control. Seems like it would be good, even if the default layout for install isn't changed, to have the Apple layouts more like OS X so people can get that without having to hack files and dig around for settings. Right now, there doesn't seem to be any difference from the standard layout when I select one of the Apple layouts.

---

### Post by cyberdork33 on 2008-12-15
> **undoIT said:**
> How difficult is it to edit the mappings in System > Preferences > Keyboard > Layouts? 
You have to 
a. know where to find the options to swap keys which is buried pretty deep
b. figure out what option does what since they do not seem to have good descriptions

Also, you were the one that seemed to be complaining that the option was hard to find... I was supporting your view :?

---

### Post by undoIT on 2008-12-15
> **cyberdork33 said:**
> Also, you were the one that seemed to be complaining that the option was hard to find... I was supporting your view :?

Agreed. I'd just like to help improve this if I can. Trying to figure out if it is something I could tackle or not. From what you said, probably not :(

Is there somewhere that these suggestions can be made, i.e. the "Ubuntu Keyboard Layout Team"?

---

### Post by _mario_ on 2008-12-15
> **undoIT said:**
> How difficult is it to edit the mappings in System > Preferences > Keyboard > Layouts? I'm really swamped right now, but if somebody can point me to where the files are, I'd like to take a crack at editing one of the layouts in some spare time.
as far as i know, GNOME keyboard preferences is a front-end for the definitions of the X server. these are located at /usr/share/X11/xkb/. you can run setxkbmap from the command line to test different settings...

> **undoIT said:**
> I'd like to try editing the layout for MacBook/MacBook Pro, to map Ctrl to command and Super to control. Right now, there doesn't seem to be any difference from the standard layout when I select one of the Apple layouts.
indeed there is. try to press 7, Shift+7, RightAlt+7, RightAlt+Shift+7 (RightAlt works as AltGr). that's Apple-style. you should get 7/|\, instead of 7/{&#8542; (PC-style) with german layout. all such combinations are Apple-like if you choose the 'Mac' variant. those combinations that aren't defined (used) by Apple remain PC-style. nice feature i think.

to not confuse you, you should know some facts/terms:
[LIST=1]
[*]there's no layout specific for MacBook/MacBook Pro. (the geometry subdirectory defines where each key is located, but that's irrelevant and only used to create a visible representation of the keyboard.
[*]the model defines which keys are available. there's no direct equivalent in X11. instead it's a hint (used in the rules subdirectory) to select appropriate keycode files (keycodes subdirectory).
[*]each key is assigned one (kernel-)keycode. these are assigned names in the keycode files.
[*]the term layout (files in the symbols subdirectory) refers to different local languages.
[*]there are different variants for each layout (subsections of the files in the symbols subdirectory), e.g., PC-style vs. Apple-style, or dead-keys vs. no dead-keys... you'll have to modify all of them to apply your change for all languages. perhaps it's possible to have something like those level3 or altwin hacks. then it's sufficient to write on additional file and apply it via rules.
[/LIST]

happy hacking!

ciao,
Mario

EDIT: looks like i forgot to refresh my tab ;-)

---

### Post by undoIT on 2008-12-15
Thanks Mario. All of the info is very encouraging.

Maybe it will sink in better after I get some caffeine in me :)

I'm wondering, if I do figure this out is it possible to add another keyboard layout, i.e. "OSX Style" or something along those lines? What is the procedure for getting something like that included in Jaunty?

btw, There isn't really an equivalent for Super / Win-key in OS X is there?

---

### Post by cyberdork33 on 2008-12-15
> **_mario_ said:**
> as far as i know, GNOME keyboard preferences is a front-end for the definitions of the X server. these are located at /usr/share/X11/xkb/. you can run setxkbmap from the command line to test different settings... Yes, and there is the added complication that there is a kernel-level to this as well...

In fact, the whole Apple Keyboard section of the layouts are a bit messy right now. There are various Apple Keyboards, some have numpads, others do not. Keys are in different locations on certain keyboards. Then add in the Macbook( pro) keyboards that are not consistent between models, and on top of all that there are various international layout differences as well... There are actually a few bugs in launchpad.

> **undoIT said:**
> btw, There isn't really an equivalent for Super / Win-key in OS X is there?
It has been long assumed that the Command key is the equivalent to Super / Win, mainly because it is a key that Apple keyboards have and other keyboards do not, AND Apple Keyboards do not have the WIN key. This made even more sense when it was referred to as the Apple-key.

---

### Post by undoIT on 2008-12-15
> **cyberdork33 said:**
> Yes, and there is the added complication that there is a kernel-level to this as well...

It has been long assumed that the Command key is the equivalent to Super / Win, mainly because it is a key that Apple keyboards have and other keyboards do not, AND Apple Keyboards do not have the WIN key. This made even more sense when it was referred to as the Apple-key.

Now that would be the day wouldn't it!? First, Apple starts using Intel processors. Then, they replace the four leaf clover key with a Win-key :P

Not just one Win-key, but two Win-keys for easy access to the start menu while using Windows on your Mac :shock:

---

### Post by _mario_ on 2008-12-15
> **cyberdork33 said:**
> 
Yes, and there is the added complication that there is a kernel-level to this as well...
this time: no. the kernel is no problem at all. besides function key behaviour that's done by software for increased flexibility, the kernel does nothing more than map each hardware-level scancode into a linux-kernel keycode.

> **cyberdork33 said:**
> 
In fact, the whole Apple Keyboard section of the layouts are a bit messy right now. There are various Apple Keyboards, some have numpads, others do not. Keys are in different locations on certain keyboards. Then add in the Macbook(Pro) keyboards that are not consistent between models, [...]
that's not the problem. each scancode sent by the hardware is nowadays well defined by the HID specification (human input devices), that's obeyed by the appropriate USB and bluetooth layers. that means it doesn't matter which keys are available nor where they are located, as long as the hardware sends the right scancode.

> **cyberdork33 said:**
> 
It has been long assumed that the Command key is the equivalent to Super / Win, mainly because it is a key that Apple keyboards have and other keyboards do not, AND Apple Keyboards do not have the WIN key. This made even more sense when it was referred to as the Apple-key.
fortunately, Apple obeys the specification as well. but sometimes Apple prints "strange" labels on their keys (e.g., the "Help"-key in place of insert which nevertheless emits the right scancode) or omits some keys PC users essentially need (e.g., PGUP/PGDN, Insert, Delete). In fact, the Command key **is** the Win key (emits the same scancode) with a different label printed on it and swapped with the Alt key.

the main difficulty is the Xorg keyboard configuration derived from XFree86, that's more difficult than necessary and very poorly documented.

ciao,
Mario

---

### Post by undoIT on 2008-12-15
> **_mario_ said:**
> fortunately, Apple obeys the specification as well. but sometimes Apple prints "strange" labels on their keys (e.g., the "Help"-key in place of insert which nevertheless emits the right scancode) or omits some keys PC users essentially need (e.g., PGUP/PGDN, Insert, Delete). In fact, the Command key **is** the Win key (emits the same scancode) with a different label printed on it and swapped with the Alt key.

the main difficulty is the Xorg keyboard configuration derived from XFree86, that's more difficult than necessary and very poorly documented.

ciao,
Mario

That explains to me better why it is good to keep Ctrl mapped to the control key, since beyond what is printed on the keys, there is actually a scancode for each key. It is just too bad that Apple decided to make the scancode for the command key the same as the Winkey and that they called the label the other key "control".

Irregardless, it works better for me with Ctrl on the command key in Ubuntu.

---

### Post by _mario_ on 2008-12-15
> **undoIT said:**
> That explains to me better why it is good to keep Ctrl mapped to the control key, since beyond what is printed on the keys, there is actually a scancode for each key. It is just too bad that Apple decided to make the scancode for the command key the same as the Winkey and that they called the label the other key "control".

in fact, it was Mircosoft to 'invent' the Win key, not the other way around. and control emits the scancode intended for control. that's correct.

however, to get (again) more technical, it seems like there are 2 approaches conceivable:
[LIST=1]
[*]patch the kernel driver to emit swapped keycodes. that's easy to accomplish, but very unlikely to get accepted upstream.
[*]hack the X keysym definition one more time.
[/LIST]

i chose to try the latter one... and it turned out, that it's not that difficult. here we go:
[LIST=1]
[*]unpack and copy the attached file to /usr/share/X11/xkb/symbols/. ideally this stuff should be added to the ctrl file, but it's easier in a separate file and won't be clobbered by upgrades. please also note that by default this file does nothing.
[*]add the second line below in /usr/share/X11/xkb/rules/base between the other two (at line 884), so it looks like this:
```

! option        =       symbols
  altctrl:super_ctrl    =       +altctrl(super_ctrl)
  grp:shift_toggle      =       +group(shifts_toggle)

```
[/LIST]

now the following line should activate a keyboard layout with both command and control keys swapped similar to the xmodmap script i posted earlier:
```
setxkbmap -v -model pc105 -layout de -variant mac -option -option altctrl:super_ctrl -option altwin:ctrl_win

```

replace the layout (de) and the variant (mac) with whatever you like. not all layouts have the same variants. have a look at /usr/share/X11/xkb/symbols/<your language> to get the variants available. 'mac' is usually defined.

please also note that in the above command '-option' comes twice by intention. to revert back to the previous setting, use the same command without the last two options (-option altctrl:super_ctrl -option altwin:ctrl_win) or restart X.

having a symbols fragment like this now allows to easily add a switch to GNOME keyboard properties. in fact, the others work like this as well. have a look at the list at the very end of /usr/share/X11/xkb/rules/base. feel free to send it upstream if you like it (and it works ;-)).

ciao,
Mario

EDIT: sorry, undoIT for finding a solution. i did expect much more troubles while writing my previous posts. but on the other hand, i thought about it while driving home and felt like i had to try that since i (tried to) understand this keyboard stuff once before.

---

### Post by cyberdork33 on 2008-12-15
> **undoIT said:**
> That explains to me better why it is good to keep Ctrl mapped to the control key, since beyond what is printed on the keys, there is actually a scancode for each key. It is just too bad that Apple decided to make the scancode for the command key the same as the Winkey and that they called the label the other key "control".

Control has always been where it is... even before Apple and Windows. It is Microsoft that decided to use CTRL for so many shortcuts when it already was associated with a large number of events. (Ctrl+C is used to kill a running command in dos, and on the *nix commandline. Microsoft decided to make this "Copy" and this functionality eventually found its way into the Linux desktop as well.) Apple decided, that instead of stealing replacing shortcuts that already exist, they should add a new key for GUI shortcuts.

This is why just swapping Ctrl and Cmd is not "right". What you want is to switch the Linux shortcuts to use Super instead of Control. (but swapping the keys will get close enough to what you want).

---

### Post by undoIT on 2008-12-15
> **cyberdork33 said:**
> Control has always been where it is... even before Apple and Windows. It is Microsoft that decided to use CTRL for so many shortcuts when it already was associated with a large number of events. (Ctrl+C is used to kill a running command in dos, and on the *nix commandline. Microsoft decided to make this "Copy" and this functionality eventually found its way into the Linux desktop as well.) Apple decided, that instead of stealing replacing shortcuts that already exist, they should add a new key for GUI shortcuts.

This is why just swapping Ctrl and Cmd is not "right". What you want is to switch the Linux shortcuts to use Super instead of Control. (but swapping the keys will get close enough to what you want).

That is an interesting bit of keyboard history. And we have mechanical typewriters to thank for the QWERTY layout, which was designed to keep the commonly used letters spaced apart to reduce jamming. It's amazing that we are still using this layout even though the reason for it is obsolete.

I think most people just want to have whatever is least encumbering. The best keyboard layout I have used is the one on my Dell XPS M1330. I have also seen this layout on other laptops like the HP Pavilion dv5t (not sure who was the first to use this modified layout). All of the extra keys I need are there (Num Lk, Prnt Scrn, Insert, Delete, Home, Page Up, Page Dn, and End). I use Delete quite a bit and it is handy to have it top right most corner. The Page Up, Page Down navigation is laid out in a column to the right of Enter, which makes it very easy to navigate large documents and hit the Enter key. And, the layout is very balanced. All the keys fit perfectly in the space alloted which is aesthetically pleasing.

I am very efficient with that keyboard layout and wish I could have the same layout on my Macbook. Anyways, switching the Linux shortcuts to use Super instead of control does help and seems to be more inline with what Apple intended when creating a new key rather than messing up Ctrl.

---

### Post by cyberdork33 on 2008-12-16
> **undoIT said:**
> Anyways, switching the Linux shortcuts to use Super instead of control does help and seems to be more inline with what Apple intended when creating a new key rather than messing up Ctrl.

but you can do whatever you want ;)

---

### Post by alexhrdr on 2008-12-16
> **cyberdork33 said:**
>  What you want is to switch the Linux shortcuts to use Super instead of Control.

Wow.  I never realized the history there.  Pretty cool.  Windows is already using their Super key more and more so I don't think there's much chance of setting this whole keyboard conflict to rest.

---

### Post by undoIT on 2008-12-16
> **cyberdork33 said:**
> but you can do whatever you want ;)

Yep. And I did :D

I'm going to read over Mario's instructions again and see if I can figure out how to map Super functionality to the control key.

---

### Post by undoIT on 2008-12-16
Maybe somebody should file a bug report with Dell. Since they are selling M1330s with Ubuntu preloaded and providing driver support with DKMS, you'd think this wouldn't be an issue.

---

### Post by SphereCat1 on 2009-02-10
Thanks for the scripts, _mario_! Exactly what I was looking for. :D

SphereCat1

---

### Post by eitan on 2009-04-22
an alternative..

i've been swapping cmd and ctrl for about a year now and i love it.  i do it via xmodmap:

~$ cat .xmodmap

!
! Swap Control_L and Super_L
!

remove mod4 = Super_L
remove control = Control_L
keysym Control_L = Super_L
keysym Super_L = Control_L
add mod4 = Super_L
add control = Control_L


this has been working mostly fine.

once in a while, while working, i'll notice the mapping is lost.  so i drop to a terminal and run xmodmap .xmodmap from my home dir and i'm back in business.

i map command-space to invoke gnome-do. 
i certainly prefer delegating metakeypresses to my thumb over my pinky.

i might try the xkb approach mentioned in this thread.

thanks,
/ eitan

---

### Post by zachwill on 2009-10-03
> **eitan said:**
> 
i map command-space to invoke gnome-do. 
i certainly prefer delegating metakeypresses to my thumb over my pinky.


ha, that's funny. i found this thread to do exactly this--especially since i'm used to using quicksilver in this way.


thanks for the help everyone.

---

