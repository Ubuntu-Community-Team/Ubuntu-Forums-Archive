---
title: "Sound Icon?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Pixcalcis on 2007-11-26
when i first put Gutsy G]ibbon on my computer, a neat little volume meter popped up on my screen to show me my volume level when i used the volume buttons on my keyboard,  however it promptly stopped showing up after i restarted my system for the first time and I cant figure out how to get it to come back.. i saw one post (below) saying it is from the desktop effects and you will get a smaller one from having desktop effects turned off. I get no icon at all with effects on or off. I have a custom effects scheme going and I cant find a setting for the volume meter.  Anyone willing to nudge me in the right direction would be appreciated
  

[http://ubuntuforums.org/showthread.php?t=527369&highlight=volume+meter"]("http://ubuntuforums.org/showthread.php?t=527369&highlight=volume+meter"")

---

### Post by jken146 on 2007-11-26
Right-click on a panel (aka "taskbar") and choose 'Add to Panel'.  Add a volume control icon.

---

### Post by Pixcalcis on 2007-11-26
.i have the volume control on my taskbar already and nothing will pop up when i used these buttons on my keyboard. What i am referring to is a little piece of eye candy that pops up when i hit my volume + and - buttons on my keyboard that will tell me the volume level right then.

As of right now  I get nothing that tells me what my  actual volume level is when i use these buttons.  The volume level coming out of my speakers  will indeed go up or down, but the volume control applet in my task bar will still say volume is at max even when i have it turned all the way down.

---

### Post by erginemr on 2007-11-27
Hello,

Your problem is indeed very strange and unfortunately, I do not have a direct answer to solve it. It seems the on-screen (OSD) volume bar is something directly integrated into Gnome and apparently there is no setting in gconf-editor that will enable / disable or affect it somehow. 

However, you may consider playing with the settings under Main Menu -> Preferences -> Sound. Please check the screenshots that I have attached. There in the second shot, the list box allows you to select which volume section (master, line-in, microphone, etc.) will be controlled by the keyboard buttons. Make sure that it refers to "master".

And good luck with your (very rare) problem.

---

### Post by Mixmastermichael on 2007-11-27
I am having the same problem now.  

my volume controls on my keyboard as well as the other controls (play, pause, fast forward) were working great up until about a week ago.

I think it started after one of the updates.  I was hoping this problem was common and that they would fix it with the next update, but no such luck.  It is really annoying me now.

If you could please help in anyway, I would really appreciate it

---

### Post by erginemr on 2007-11-27
> **Mixmastermichael said:**
> I am having the same problem now.  

my volume controls on my keyboard as well as the other controls (play, pause, fast forward) were working great up until about a week ago.

I think it started after one of the updates.  I was hoping this problem was common and that they would fix it with the next update, but no such luck.  It is really annoying me now.

If you could please help in anyway, I would really appreciate it

Do you mean the volume controls on your keyboard do not work anymore, or they work but you cannot see the on-screen volume bar?

---

### Post by Mixmastermichael on 2007-11-27
> **erginemr said:**
> Do you mean the volume controls on your keyboard do not work anymore, or they work but you cannot see the on-screen volume bar?


No, the volume controls on my keyboard all of the sudden don't work anymore at all.  The volume isn't effected at all when I try and use the keyboard volume keys or play /pause.

I can manually control the volume on the taskbar though.

So I guess the real question is to how to get my keyboard controls working again?

---

### Post by Pixcalcis on 2007-11-27
> **erginemr said:**
> 
However, you may consider playing with the settings under Main Menu -> Preferences -> Sound. Please check the screenshots that I have attached. There in the second shot, the list box allows you to select which volume section (master, line-in, microphone, etc.) will be controlled by the keyboard buttons. Make sure that it refers to "master".

.

yes it was selected as master

---

### Post by Pixcalcis on 2007-11-27
> **Mixmastermichael said:**
> 

So I guess the real question is to how to get my keyboard controls working again?

did you try what he suggested I do?  Go under preference's--> sounds and then making sure that master is selected to be controlled with the keyboard?

---

### Post by erginemr on 2007-11-27
> **Mixmastermichael said:**
> No, the volume controls on my keyboard all of the sudden don't work anymore at all.  The volume isn't effected at all when I try and use the keyboard volume keys or play /pause.

I can manually control the volume on the taskbar though.

So I guess the real question is to how to get my keyboard controls working again?

OK. I guess you have lost the shortcuts to the actions related to the volume change. Try this please:

There should be a dialog under Main Menu -> System -> Preferences -> Keyboard Shortcuts, where there should be a setting for volume increase, decrease and mute. 

Click on each one and click on the corresponding accelerator on your keyboard. Say for volume mute, click on the associated button on your keyboard. And check whether your shortcuts now work.

Good luck...

---

### Post by Mixmastermichael on 2007-11-27
OK, I think this is leading somewhere...

When I go to keyboard shortcuts and try to edit them in "new accelerator," the keyboard doesn't respond at all to my actions from the keyboard volume keys.

However, if I try to use other keys for the shortcuts, they work.  For example "F11" is now my mute key.

Thanks a lot for the help, I really appreciate it, but would you happen to have any other ideas to get the keyboard controls working again?

---

### Post by erginemr on 2007-11-28
> **Mixmastermichael said:**
> OK, I think this is leading somewhere...

When I go to keyboard shortcuts and try to edit them in "new accelerator," the keyboard doesn't respond at all to my actions from the keyboard volume keys.

However, if I try to use other keys for the shortcuts, they work.  For example "F11" is now my mute key.

Thanks a lot for the help, I really appreciate it, but would you happen to have any other ideas to get the keyboard controls working again?

I believe the solution will evolve from within "xmodmap". To begin with, you may read the following articles:

[http://www.g-schnabel.net/xe4500/](http://www.g-schnabel.net/xe4500/)
look for the section "Enable the five One-Touch buttons and the audio buttons"

and

[http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325)
look for the section "File: ~/.Xmodmap"

I am also working on it and will come up with a more in-depth explanation soon.

---

### Post by erginemr on 2007-11-28
Well, there is a program "xev" that will respond to mouse and keyboard actions. The program is graphical, yet to see the results, you need to run it from the console.

So, please open up a terminal (gnome-terminal will do) and issue "xev" from there. Move away the mouse so that the program will not trap mouse actions, but let it remain as the active window (i.e. has focus) anyway. 

Do you see any reaction on the console output when you press those keyboard multimedia keys?

the key q:
KeyPress event, serial 30, synthetic NO, window 0x2800001,
    root 0x3f, subw 0x0, time 2240021009, (330,210), root:(335,259),
    state 0x10, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XmbLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

Multimedia Key for Calculator: (when already assigned)
KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  15  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

Volume Mute: (when not assigned, works with 0xa0 as shortcut)
KeyPress event, serial 30, synthetic NO, window 0x2800001,
    root 0x3f, subw 0x0, time 2240254524, (234,-8), root:(239,41),
    state 0x10, keycode 160 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

Volume Down: (when not assigned, works with 0xae as shortcut)
KeyPress event, serial 30, synthetic NO, window 0x2800001,
    root 0x3f, subw 0x0, time 2240257489, (234,-8), root:(239,41),
    state 0x10, keycode 174 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

Volume Up: (when not assigned, works with 0xb0 as shortcut) 
KeyPress event, serial 30, synthetic NO, window 0x2800001,
    root 0x3f, subw 0x0, time 2240260390, (234,-8), root:(239,41),
    state 0x10, keycode 176 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

Here I have pressed the key "q" (it could be any other key) just to show you on what to expect: Its keycode is 24 and its keysym is 0x71, which you need to assign to the shortcut keyboard accelerator.  
The problem is, sometimes no keysym is assigned and we need it to assign to the accelerator. 
But before that, check that your volume keys (the real hardware) are working. The program should output some message when you press them. When there is an already assigned shortcut (ex. the mm key for the calculator, to which the Gnome calculator has already been assigned, the message is like this:

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  15  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

When, on the other hand, no shortcut is assigned to the mm key, the resulting message comes out like this:

KeyPress event, serial 30, synthetic NO, window 0x2800001,
    root 0x3f, subw 0x0, time 2240254524, (234,-8), root:(239,41),
    state 0x10, keycode 160 (keysym 0x0, NoSymbol), same_screen YES,

Here the two things to pay specific attention are keycode and keysym.

So STEP-1:

If you have received any input from the terminal, your mm (multimedia) keys do work. Better off if you happen to receive the keycodes as 160, 174 and 176, because these are the same as mine and the corresponding keysyms for them are as follows:

* Volume Mute Button: keycode 160 -> keysym 0xa0 -> Use gconf-editor to assign 0xa0 manually to volume mute.

* Volume Down Button: keycode 174 -> keysym 0xae -> Use gconf-editor to assign 0xae manually to volume down.

* Volume Up Button: keycode 176 -> keysym 0xb0 -> Use gconf-editor to assign 0xb0 manually to volume up.

See the attached screenshots for the location of the corresponding key in gconf-editor. 

See if this works. If not, then you will have to resort to "xmodmap", which will be STEP-2.

---

### Post by erginemr on 2007-11-28
STEP-2: If the above technique does not work (but provided that xev reacts to your mm keys), then we should mess up with "xmodmap".

Xmodmap is a keyboard mapping utility for the X window system. This way, you may force any key on your keyboard to behave differently. For instance, you may shift "p & q" keys (which is True, if both p and q are True, bad joke), or have some rarely used keys on your keyboard issue special symbols.

For our case, we shall attempt to map the keyboard volume keys to special terms that are used for audio keys under X11. To customize xmodmap, you should create a hidden configuration file .xmodmaprc in your home folder:

gedit ~/.xmodmaprc

and inside it you should copy and paste the following:

keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume

Here, if the keycodes you have found are different than the above, you should correct them accordingly.

Save it and restart the X server by Ctrl + Alt + BackSpace, when your new settings for xmodmap should activate with a selection dialog. Select .Xmodmap from the list (If you see two config files in the selection list, the other file is just its backup created by Gedit.). Go back to the keyboard shortcuts dialog, activate "new accelerator..." and press the three volume keys. (See the screenshots below.)

Hopefully, you should have it working now.

---

### Post by Mixmastermichael on 2007-11-29
Thanks for the help!  When I tried your first process, I got no response when I would press the volume or multimedia keys in "xev."  Other keyboard functions appeared to work, I got this response when I pressed the "q" key:
KeyPress event, serial 31, synthetic NO, window 0x3600001,
    root 0x52, subw 0x0, time 2317255070, (185,-379), root:(862,235),
    state 0x0, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XmbLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3600001,
    root 0x52, subw 0x0, time 2317255138, (185,-379), root:(862,235),
    state 0x0, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

For your second step, since my multimedia keys apparently aren't working even when in "xev" terminal, I didn't proceed. I was able to create the hidden file in my home folder though.  Any other ideas?  (Which I really appreciate)

---

### Post by erginemr on 2007-11-29
You are welcome, but I wish we could have solved the problem in the first place. Now that your multimedia keys do not work, the subject boils down to whether they are dead (i.e. hardware failure) or not and the way to make sure is:

1 - Checking their functionality under Windows, if you are dual booting Linux with Windows.

2- Checking them with a fresh Live CD, which you had mentioned was once working in one of oyur previous posts as: "No, the volume controls on my keyboard all of the sudden don't work anymore at all."

---

### Post by erginemr on 2007-11-29
You can also assign another keyboard combination scheme to the volume shortcuts. Back in Windows and with a run of the mill keyboard w/o any mm keys, I was using the following combination with a memory resident 3rd party utility to manipulate the sound level:

To Increase Volume: Ctrl + "NumPad +"
To Reduce Volume: Ctrl + "NumPad -"
To Mute / Unmute Volume: Ctrl + "NumPad *"

which I believe is a very slick way to control the sound level. You can assign these or any combo you like and live happily ever after with it.

---

### Post by Mixmastermichael on 2007-11-30
okay, I think I will just stick with the keyboard volume controls I have set up for a while.

I don't have access to a windows drive currently, but I might want to check to see if the controls work on that operating system sometime this winter.

I will post in this board when I see the results.

Thanks for all the help though.

Take it easy.

---

### Post by erginemr on 2007-11-30
Okey dokey.

Have fun.

---

### Post by Mixmastermichael on 2008-01-02
bump.

Ok so I was finally able to check with a windows machine, and the sound and play / pause buttons on my keyboard work on that operating system, so I have no idea what the problem is now,

---

### Post by erginemr on 2008-01-02
I am sorry to say this but...
Bumpety bumpety bump! :confused:

I hope someone else will soon come forward with a solution to your case.

---

