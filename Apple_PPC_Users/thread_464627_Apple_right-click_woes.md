---
title: "Apple right-click woes"
date: 2007-06-04
forum: Apple PPC Users
---

### Post by CaptainSchnitz on 2007-06-04
Hi out there!

Recently installed Feisty on an iBook G4. The laptop has only a one button mouse, and by default the middle and right click buttons are mapped respectively to F11 and F12. I'm not happy with this setup - F12 is just a silly location for a right mouse button, so I thought I'd see about remapping the keys.

I found two ways to do this on the forums - the first was a small script that only seemed to work about half the time, and caused a long delay when logging in, as well as leaving F12 mapped as right-click when I want to be able to use that key as a Beagle shortcut. A most inelegant fix. The second fix I have seen, and that I need help with, is a modification to the contents of /etc/sysctl.conf. I have altered the following lines as follows:

```
dev/mac_hid/mouse_button2_keycode = 113
dev/mac_hid/mouse_button3_keycode = 116
```

These keycodes were obtained by running xev. After altering /etc/sysctl.conf, I ran

```
sudo sysctl -p /etc/sysctl.conf
```

and rebooted. Nothing! Right-click is not only not mapped to the new keys, it is still located on F12 - something which I find totally mystifying given that sysctl.conf no longer has any reference to that keycode. It's making me wonder if the instructions to map to F11 and F12 are actually located elsewhere.

Any help that anyone can provide would be most appreciated. I am finding this incredibly frustrating.

---

### Post by 3rdalbum on 2007-06-05
Are you using an Apple mouse with your iBook?

Generic USB mice for PCs will work fine with your iBook running Ubuntu, enabling you to right-click, scroll wheel and middle-click. The same mouse will also work with the Mac OS as a single-button mouse.

---

### Post by tactus on 2007-06-05
Using an external mouse is kind of obvious, but I think the thread starter wants to know how to remap the keyboard mouse-keys correctly. I am sorry that I don't have anything to contribute here, my powerbook is just serving as a personal server, but it sure would be interesting to hear if someone could enlighten this.

---

### Post by johne on 2007-06-05
this is very similar to what i have been researching. so far i have only found one app called mouseemu, but i have never been able to get it work properly. i hope someone takes an interest in fixing this app considering f12 is so absurd for a right-click.

---

### Post by stmiller on 2007-06-05
This is possible to do. The problem is that the button 'control' is currently mapped in Linux for being the 'control' button. So it would have to be mapped to F12, probably. To make room for the right click to be control. I'll poke around and see what I can find...

---

### Post by johne on 2007-06-06
> **stmiller said:**
> This is possible to do. The problem is that the button 'control' is currently mapped in Linux for being the 'control' button. So it would have to be mapped to F12, probably. To make room for the right click to be control. I'll poke around and see what I can find...

rock on!

---

### Post by stmiller on 2007-06-06
Okay I got it. Unfortunately the way Linux works with the control button, it NEEDS the control button to stay as it is. So you can remap the middle and right click to other buttons, though.

Open a terminal and type

$ sudo gedit /etc/sysctl.conf

and then alter the end so it looks like this:

```
# Emulate the middle mouse button with F11 and the right with F12.
#dev/mac_hid/mouse_button_emulation = 1
#dev/mac_hid/mouse_button2_keycode = 87
#dev/mac_hid/mouse_button3_keycode = 88

dev/mac_hid/mouse_button3_keycode = 125
dev/mac_hid/mouse_button2_keycode = 126
dev/mac_hid/mouse_button_emulation = 1
```

You will have to reboot to see the changes.

You are commenting out (turning off) the F11 and F12 that ubuntu defaults with with the '#' symbol. And instead putting in lines that make:

'Apple button' - right click, and 
'Fn+Apple' to be middle click.

Okay see how this works. If you want to go back to defaults, you can just remove my lines at the end, and 'uncomment' the default ubuntu F11 and F12 stuff.

---

### Post by calinb on 2007-06-07
> **CaptainSchnitz said:**
> <snip>
The second fix I have seen, and that I need help with, is a modification to the contents of /etc/sysctl.conf. I have altered the following lines as follows:
<snip>
The only solution I've found acceptable is mouseemu.  I'm running Feisty on a G4 mini.   I have ctl+click mapped to a virtual middle mouse button click and command+click (wireless Apple keyboard) mapped to a virtual right mouse button click.  The option key (alt key?) is mapped to scroll.  If I hold down the option key and move the mouse up and down, the scroll bars move (no clicking).  I particularly like pasting highlighted text with the virtual middle mouse button--true "Linux style!"

I retained the F11 and F12 mappings, though I agree they are very inconvenient.

-Cal

Here's my  /etc/default/mouseemu file:
```

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default.
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


MID_CLICK="-middle 0 87"         # F11 with no modifier
MID_CLICK="-middle 29 272"       # Left Ctrl + click
RIGHT_CLICK="-right 0 88"        # F12 with no modifier
RIGHT_CLICK="-right 125 272"     # Left Apple Key (LEFTMETA) + click
SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```

---

### Post by farbird on 2007-06-17
is there a way to emulate a right click after a delayed click on the apple's mouse?

---

### Post by sirrahn on 2007-06-20
Hi

Its very strange but neither of these seems to work for me.

I've seen instructions to edit mouseemu before and can find and edit the file, but the it never seems to work, i.e. the mouse button isn't emulated.  That's the case even if I reboot, and if I change the option so as to avoid using the control key (on the basis of device that this may not work).

I just looked at /etc/sysctl.conf as suggested by stmiller, but the version I've got does not include anything to do with emulating  mouse buttons. i.e.

# Emulate the middle mouse button with F11 and the right with F12.
#dev/mac_hid/mouse_button_emulation = 1
#dev/mac_hid/mouse_button2_keycode = 87
#dev/mac_hid/mouse_button3_keycode = 88

You'd think I was using another distribution or something like that, but i am funning Ubuntu feisty!

sirrahn

---

### Post by ChillMonkey on 2007-08-23
> **stmiller said:**
> 

dev/mac_hid/mouse_button3_keycode = 125
dev/mac_hid/mouse_button2_keycode = 126
dev/mac_hid/mouse_button_emulation = 1[/CODE]

You will have to reboot to see the changes.


so... i want to use:

fn+option : middle-click
fn+apple : right-click

according to xev that's keycodes 113 and 116, respectively, on my Powerbook G4. 
now i edited sysctl.conf accordingly and reboot. no go. what's happening? can i just '/etc/init.d/mouseemu stop' and expect the sysctl settings to take over?

also, why do i have to reboot? shouldn't i be a able to just 'sudo sysctl -w dev/mac_hid/mouse_button3_keycode=116' for example and have it take effect?

just curious, fluxbox is a pain to use when i have to hit F12 to bring up my menu all the time.

---

### Post by RedSquirrel on 2007-08-23
> **ChillMonkey said:**
> so... i want to use:

fn+option : middle-click
fn+apple : right-click

according to xev that's keycodes 113 and 116, respectively, on my Powerbook G4. 
now i edited sysctl.conf accordingly and reboot. no go. what's happening? can i just '/etc/init.d/mouseemu stop' and expect the sysctl settings to take over?

also, why do i have to reboot? shouldn't i be a able to just 'sudo sysctl -w dev/mac_hid/mouse_button3_keycode=116' for example and have it take effect?

just curious, fluxbox is a pain to use when i have to hit F12 to bring up my menu all the time.

You don't have to right-click to bring up the Fluxbox menu.

You can set the Fluxbox right-click menu to show up on pretty much any keyboard shortcut you like. Just add it to your ~/.fluxbox/keys file.

```
*shortcut-key-combination* :RootMenu
```See [http://fluxbox-wiki.org/index.php/Keyboard_shortcuts](http://fluxbox-wiki.org/index.php/Keyboard_shortcuts).

I use

```
Super_L :RootMenu
Super_R :RootMenu

```but those are the MS Windows keys on my keyboard. You may use whatever you find is suitable for you. :)

---

### Post by ChillMonkey on 2007-08-24
why didn't i think of that. thanks. that makes flux easier to use, but the right-click emulation in general is still a pain. hopefully will figure something out soon.

---

### Post by jso2897 on 2007-08-27
3rdalbum provided the solution. You don't need a special mouse - a regular USB mouse works fine.

Once again, the forum comes through. Thank you all for your help and suggestions!:KS

---

### Post by Gen2ly on 2007-08-29
This is strange.  Before for me too I used to be able to alter these parameters of the kernel.  Now mapping seems off.  I guess that the mac hid is busted.  I saw all this because benazo's method (which I hadn't tried before)  works.  Here's what I did:

```
echo "xmodmap -e 'keycode 116 = Pointer_Button2'" > /etc/conf.d/local.start
echo "xmodmap -e 'keycode 108 = Pointer_Button3'" > /etc/conf.d/local.start
echo "xkbset m" > /etc/conf.d/local.start
```

I'm not sure if Ubuntu has a local.start, don't have me ubuntu box with me.  If you do you can just restart the boot script, no need to reboot.

Oop sry, the boot script is already loaded before x starts.  However its asy enough to put this in a scipt.

---

### Post by kattefisk on 2007-09-04
I have tried several things now, but no matter what, I just can not get the right mouse button to work.

mouseemu did not work and it somehow managed to disable F12 as a right mouse button, so now I do not have any right mouse button at all, and it is getting a bit annoying.
I also tried to edit sysctl.conf without getting any closer to a solution. Does anyone know what the problem could be?

And where is the apostrophe? I cant write can't (norwegian mac layout).

---

### Post by jso2897 on 2007-09-04
I apologize if I'm being a pill, but while I don't have a solution to your problem, I do know how to make it go away. Just take a regular old USB mouse from a PC, reset everything to default, and plug  'er in.
No more problem.

---

