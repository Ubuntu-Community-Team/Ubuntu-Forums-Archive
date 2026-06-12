---
title: "[SOLVED] Was xmodmap broken yesterday?"
date: 2008-12-02
forum: Apple Hardware Users
---

### Post by hyperboloid on 2008-12-02
Is anyone else noticing that xmodmap stopped working? I noticed it yesterday, 1 Dec 08. I think there were some updates installed yesterday, but I can't recall which ones. 

I have a file .Xmodmap in my $HOME containing just one line
```

keycode 66 = Pointer_Button2

```
which has been happily executed on startup to map my caps lock key to emulate a "middle click" on the mouse. Yesterday it stopped working. Running either of the commands 
```

me@laptop:~$ xmodmap .Xmodmap 
me@laptop:~$ xmodmap -e "keycode 66 = Pointer_Button2"

```
in a terminal has no effect.

---

### Post by _mario_ on 2008-12-02
> **hyperboloid said:**
> Is anyone else noticing that xmodmap stopped working? I noticed it yesterday, 1 Dec 08. I think there were some updates installed yesterday, but I can't recall which ones.
no. my xmodmap is still working. dpkg logs its actions in /var/log/dpkg.log*, but i didn't find anything that seemed relevant.

however, you can check that xmodmap is working like this:
[LIST=1]
[*]make sure it isn't executed by default. rename your file to something else. log out and log in (should restart X).
[*]save the old state:
```
xmodmap -pke > before
```
[*]run xmodmap manually the change you configuration.
[*]save the new state:
```
xmodmap -pke > new
```
[*]compare both states:
```
diff before new
```
[/LIST]
if the last command shows you what you just changed, xmodmap is working. (and i have no clue what's going on.)

ciao,
Mario

---

### Post by hyperboloid on 2008-12-02
> **_mario_ said:**
> no. my xmodmap is still working. dpkg logs its actions in /var/log/dpkg.log*, but i didn't find anything that seemed relevant.

however, you can check that xmodmap is working like this:
[LIST=1]
[*]make sure it isn't executed by default. rename your file to something else. log out and log in (should restart X).
[*]save the old state:
```
xmodmap -pke > before
```
[*]run xmodmap manually the change you configuration.
[*]save the new state:
```
xmodmap -pke > new
```
[*]compare both states:
```
diff before new
```
[/LIST]
if the last command shows you what you just changed, xmodmap is working. (and i have no clue what's going on.)


Thanks for the help, Mario. OK, I backed up the old file by "mv .Xmodmap .backup-Xmodmap" and then restarted X by CTRL-ALT-DELETE. Then I followed the above and got:
```

me@laptop:~$ xmodmap -pke > before
me@laptop:~$ xmodmap ~/.backup-Xmodmap 
me@laptop:~$ xmodmap -pke > new
me@laptop:~$ diff before new
59c59
< keycode  66 = Caps_Lock NoSymbol Caps_Lock NoSymbol Caps_Lock
---
> keycode  66 = Pointer_Button2

```
thus proving that xmodmap did as instructed. Yet it does not "work" in the sense that when I press the key nothing happens anymore. (Before Dec 1st, a key press would cause the contents of the copy buffer to be pasted at the current cursor location (in emacs, for instance). 

By the way, the key is working. Before I ran the test, I used it to toggle the "caps lock" behavior - it worked fine. However, after the test, the key does nothing anymore. 

Here's the contents of my /var/log/dpkg.log to show that there's nothing amiss there: 
> 
2008-12-01 07:08:01 startup archives unpack
2008-12-01 07:08:17 upgrade mbp-nvidia-bl-dkms 0.15 0.16
2008-12-01 07:08:17 status half-configured mbp-nvidia-bl-dkms 0.15
2008-12-01 07:08:40 status unpacked mbp-nvidia-bl-dkms 0.15
2008-12-01 07:08:40 status half-installed mbp-nvidia-bl-dkms 0.15
2008-12-01 07:08:40 status half-installed mbp-nvidia-bl-dkms 0.15
2008-12-01 07:08:40 status unpacked mbp-nvidia-bl-dkms 0.16
2008-12-01 07:08:40 status unpacked mbp-nvidia-bl-dkms 0.16
2008-12-01 07:08:41 startup packages configure
2008-12-01 07:08:41 configure mbp-nvidia-bl-dkms 0.16 0.16
2008-12-01 07:08:41 status unpacked mbp-nvidia-bl-dkms 0.16
2008-12-01 07:08:41 status half-configured mbp-nvidia-bl-dkms 0.16
2008-12-01 07:08:57 status installed mbp-nvidia-bl-dkms 0.16
2008-12-02 09:42:27 startup archives unpack
2008-12-02 09:42:42 upgrade applesmc-dkms 0.13.1 0.14.1
2008-12-02 09:42:42 status half-configured applesmc-dkms 0.13.1
2008-12-02 09:43:07 status unpacked applesmc-dkms 0.13.1
2008-12-02 09:43:07 status half-installed applesmc-dkms 0.13.1
2008-12-02 09:43:07 status half-installed applesmc-dkms 0.13.1
2008-12-02 09:43:08 status unpacked applesmc-dkms 0.14.1
2008-12-02 09:43:08 status unpacked applesmc-dkms 0.14.1
2008-12-02 09:43:09 startup packages configure
2008-12-02 09:43:09 configure applesmc-dkms 0.14.1 0.14.1
2008-12-02 09:43:09 status unpacked applesmc-dkms 0.14.1
2008-12-02 09:43:09 status half-configured applesmc-dkms 0.14.1
2008-12-02 09:43:25 status installed applesmc-dkms 0.14.1


Looks like the update to "mbp-nvidia-bl-dkms 0.16" must have borked something, but I can't imagine what.

---

### Post by _mario_ on 2008-12-03
> **hyperboloid said:**
> Thanks for the help, Mario. OK, I backed up the old file by "mv .Xmodmap .backup-Xmodmap" and then restarted X by CTRL-ALT-DELETE. Then I followed the above and got:
```

me@laptop:~$ diff before new
59c59
< keycode  66 = Caps_Lock NoSymbol Caps_Lock NoSymbol Caps_Lock
---
> keycode  66 = Pointer_Button2

```
thus proving that xmodmap did as instructed.
we're now sure that xmodmap does work. running xev and pressing your offending key should give something like:
```
KeyRelease event, serial 34, synthetic NO, window 0x4800001,
    root 0x13b, subw 0x0, time 27898490, (75,69), root:(1092,586),
    state 0x400, keycode 116 (keysym 0xfeeb, Pointer_Button3), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
(i'm using a different key and a different mouse button ;-))

if that does work, you can check whether "mouse keys" in gnome-keyboard-properties are enabled. sometimes this options gets disabled on my machine. i still don't know why.

ciao,
Mario

---

### Post by hyperboloid on 2008-12-03
Mario, you're awesome!  Just for the record, xev reports that everything looks OK:
```
 
KeyRelease event, serial 34, synthetic NO, window 0x2e00001,
    root 0x13b, subw 0x2e00002, time 1978233, (39,46), root:(502,735),
    state 0x0, keycode 66 (keysym 0xfeea, Pointer_Button2), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
so I went to System -> Preferences -> Keyboard and examined the "Mouse Keys" tab as you suggested. There is a check box labeled "Pointer can be controlled using the keypad" which was in an unchecked state, even though I recall enabling it long ago. Once I again enabled that option, the missing functionality was immediately restored.

One wonders why Gnome would randomly change such things, but at least the mystery is solved. Thanks a heap.

---

