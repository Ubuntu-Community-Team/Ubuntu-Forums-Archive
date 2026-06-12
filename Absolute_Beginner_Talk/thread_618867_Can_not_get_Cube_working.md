---
title: "Can not get Cube working"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by siftride on 2007-11-20
OK I i have the latest version of ubuntu. I have the cube enabled on Compiz however evertime i do alt ctrl left click its dragging the mouse and creating the shadow box in whatever shape it command it to do. How do you get the cube to work Any help please. Be easy im a beginner.

---

### Post by RussianVodka on 2007-11-20
Is "Rotate Cube" enabled? Cube is quite useless if it can't rotate.

---

### Post by siftride on 2007-11-20
Yes it is enabled

---

### Post by DutyDuty on 2007-11-20
Are you using compiz or metacity?

---

### Post by siftride on 2007-11-20
Im using compiz i don't know if i have metacity

---

### Post by LowSky on 2007-11-20
is viewport switcher enabled?

---

### Post by siftride on 2007-11-20
Yes it is enabled

---

### Post by Sims2789 on 2007-11-20
> **siftride said:**
> OK I i have the latest version of ubuntu. I have the cube enabled on Compiz however evertime i do alt ctrl left click its dragging the mouse and creating the shadow box in whatever shape it command it to do. How do you get the cube to work Any help please. Be easy im a beginner.

Try a different keyboard command to activate it that doesn't involve the mouse.

---

### Post by ajkirchner on 2007-11-20
Isn't it CTRL + **ALT** + Left Drag ? Check your key bindings...

---

### Post by siftride on 2007-11-20
Where are my key bindings?  I tried ctrl+alt=left drag nothing

---

### Post by wasmuthk on 2007-11-20
Do you have enough virtual desktops? I struggled with this same problem for a long time and it finally worked if I setup 4 columns by 2 rows (or the reverse)

It started working for me just fine.

---

### Post by siftride on 2007-11-20
Are you talking about when you go into Compiz and in general options you do that cause i had it at both 4 and i tried the other way still nothing works....What about in Appearance preference in visual effects its on none and when i try to go to custom i get a message saying i wont do it

---

### Post by overdrank on 2007-11-20
> **siftride said:**
> OK I i have the latest version of ubuntu. I have the cube enabled on Compiz however evertime i do alt ctrl left click its dragging the mouse and creating the shadow box in whatever shape it command it to do. How do you get the cube to work Any help please. Be easy im a beginner.

Hi you can use this command to install the manager
```
sudo apt-get install compizconfig-settings-manager
```
Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked.

---

### Post by siftride on 2007-11-20
I did that originally and this is what i get

compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by smacattack on 2007-11-20
I'm not really sure what you've tried exactly... but did you try using just the keyboard?

the default should be Ctrl+Alt+Left Arrow key


edit: also maybe try the expo plugin and confirm when you go into expo mode you see 4 screens side by side

---

### Post by siftride on 2007-11-20
When i hit the Ctrl+Alt+Left arrow key it goes to the second screen that i see on the lower left corner.  I also do have the expo plugin enabled and i don't see 4 screens side by side.

---

### Post by smacattack on 2007-11-20
Okay let's take a step back.

In the compiz config manager, you should have 'Desktop Cube', 'Rotate Cube', and 'Viewport Switcher' all enabled. 

Desktop wall should be disabled with those other things on but confirm that.

Lastly, in the 'General' options... the Horizontal Desktop size should be 4, the Vertical Desktop size should be 1, and you should set the number of desktops to 1.

Also, what do you see in expo if not 4 screens along side one another?

---

### Post by siftride on 2007-11-20
Ok I do have Desktop Cube, Rotate Cube and Viwport enabled and expo enabled in the section "Desktop."  I don't see anything at all in expo.  Also i adjusted the size to 4-1-1 in general options

---

### Post by smacattack on 2007-11-21
the defaults for expo should be fine. just try using the default key binding I believe its Super+E (ie windows key + E) or you can set it to something else. try that out and you should see 4 desktops alongside one another regardless of the cube settings

let me know.

---

### Post by siftride on 2007-11-21
I still don't see 4 desktops

---

### Post by smacattack on 2007-11-21
what compiz plugins do you have working?

---

### Post by siftride on 2007-11-21
I have Enhanced Zoom desktop, Negative, Desktop Cube, Expo, Rotate Cube, View Port Swicher
Animations, Fading Windows, Window Decoration, Jpeg, Png, Svg Text, Dbus, Regex machting
Resize Info, Video Playback, Workaround, Application Switcher, Extra Wm Actions, Move Window
Place Windows, Scale, Snapping Windows and Resize Window

---

### Post by smacattack on 2007-11-21
nono, i mean like actually working, not just enabled. I'm just wondering how it is that you know compiz is even running properly in the first place. Like does the zoom or any of the other plugins you mentioned work?

---

### Post by siftride on 2007-11-21
Count to think of it none that i none of them are working, zoom doesn't work

---

### Post by smacattack on 2007-11-21
If none of the plugins are working I imagine it's a video card related issue (drivers etc) which is beyond me... unfortunately. If you post what your video card is someone may be able to help you out.

take care.

edit: oh i was just thinking... how is it exactly that you are starting compiz? are you going into 'Appearance' in system preferences or are you starting it from terminal?

if you haven't tried starting it from terminal type      'compiz --replace'  (minus quotes)      and post the output

---

### Post by siftride on 2007-11-21
Thank you for your time and effort my Video Card is a Nivida G Force Fx 5200

What i usally did to go into compiz is go into system-prefrence and advance desktop settings

When i went into the term and typed compiz --replace i got this

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 11
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity

---

### Post by smacattack on 2007-11-21
weird that it says there's less than 65000 whatever memory. that is your problem right there I imagine. Again I don't know much about video cards but that is you best lead.

Anyone have any advice?

take care.

---

