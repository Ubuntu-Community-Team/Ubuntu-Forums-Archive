---
title: "Remapping command key to be the control key in 2011"
date: 2011-05-14
forum: Apple Hardware Users
---

### Post by unagimiyagi on 2011-05-14
Hi folks,

Is there a way to easily make the command key function as the control key on a macbook pro in these modern times of 2011?

I tried one of the command-line based tutorials and couldn't get it to work.  Seeing as I have little idea as to what I was doing, I'm going to need a gui.  The interesting thing is that I have actually done this in Lucid Lynx before, on my own, with little help.  But come Natty, nothing appears to be working.  I would think that this is a common question, so I'm sure there is something simple I'm overlooking.

Thanks!

---

### Post by samuaz on 2011-05-15
+1 need cmd button!!

---

### Post by unagimiyagi on 2011-05-29
> **samuaz said:**
> +1 need cmd button!!


Does anyone have a natty-specific tutorial on remapping the command keys to be the control keys on a macbook pro?

I changed my keyboard model to a macbook pro and it doesn't seem like anything happened, even after rebooting.

Thanks

---

### Post by zacbarton on 2011-05-30
Have a look under keyboard -> layouts tab -> options button. I think you are after the "Ctrl key position" or "Alt/Win key behavior".

---

### Post by unagimiyagi on 2011-05-30
> **zacbarton said:**
> Have a look under keyboard -> layouts tab -> options button. I think you are after the "Ctrl key position" or "Alt/Win key behavior".


Thanks, but this only partially works.

What I want (and others) is for the command keys to be a control key, exactly like it is on a mac.  And then the alt keys to remain alt keys.

The problem is that there is no mapping for changing the command key to be a control key.  I believe that the command key is called the super key or windows key.  We need a way to map the right super key to a right control key.  Apple keyboards have only one actual control key.  I've looked at tutorials and no one has gotten this to work in natty, when this change was very simple in lucid lynx.  One step forward, two steps back.  I'm still not sure what specifying my keyboard as being a macbook pro even did in the keyboard settings.  Anyone know?

---

### Post by drhoda on 2011-05-31
so from your post I see two issues (correct me if I am wrong):

Issue 1 - mapping the command key to a control key (the post above took care of this one for me)

Issue 2 - keeping the alt key (also labled option on my macbook pro 4,1) an alt key

---

### Post by unagimiyagi on 2011-05-31
Hi,

Yes, you are understanding my problem.  I do not see how you got the command keys, the two keys immediately to the left and to the right of the keyboard, to both become control keys.  Am I missing a setting or something? Please explain if you can. 

Thanks!

---

### Post by k4r1m on 2011-06-09
anyone figured this out?

---

### Post by unagimiyagi on 2011-06-09
[COLOR=#000000][FONT=Arial]CREDIT TO IDIOTPRONE on these forums!

create a new file in your home directory.  
One way you can do this is by typing in at the command line:

nano ~/.Xmodmap[/FONT][/COLOR]

Then add the following lines to this new file:

```


[COLOR=#000000][FONT=Arial]  ![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  ! clean most of the modifiers[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  clear control[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  clear mod4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  clear mod1[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]  ![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  ! left side[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  ! keycode 64 is right alt[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  keycode  64 = Super_L[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  ! key code 133 should be the command key, if not check with the program xev[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  keycode 133 = Alt_L Meta_L[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  add mod4 = Super_L[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  add mod1 = Alt_L Meta_L[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  add control = Control_L[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]  ! right side[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  ! key code 134 should be the command key. i not have a mac[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  keycode 134 = Alt_R Meta_R[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  ! kdecode 108 is the right alt key[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  keycode 108 = Control_R[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  ! change mod4 to to mod1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  add mod1 = Alt_R Meta_R
[/FONT][/COLOR][COLOR=#000000][FONT=Arial] add control = Control_R[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]then run at the command line:  xmodmap ~/.Xmodmap[/FONT][/COLOR]
This registers the new keyboard map.

[COLOR=#000000][FONT=Arial]Then  in Ubuntu Natty 11.04, you need to go into keyboard shortcuts.   redefine alt+tab to something else, like alt+d.  Then redefine it right  back to alt+ tab.  You need to redfine it in order to make the new alt  key work like it should.  You may or may not need to do these steps.  [/FONT][/COLOR]I found that I had to b/c the alt key was not remapped in the shortcuts; it was "sticky" or something.

---

### Post by theelee12 on 2011-06-21
Easier way!!!!! Go to System, Preferences, Keyboard, Layouts, Options, Alt/Win key behavior, select Win key as control, done!

---

