---
title: "Mac Volume Keys?"
date: 2009-07-08
forum: Apple Hardware Users
---

### Post by zacharyrs on 2009-07-08
How can I get my MacBook volume keys (the three keys next to numlock on the top row of the keyboard) to actually work with the volume on U? When I click on one of the volume keys it doesn't change the volume and I have to do it manually :(

---

### Post by bear24rw on 2009-07-08
in keyboard shortcuts you can assign them to run the command
```
amixer set master +5%
```
```
amixer set master -5%
```
I dont remember the exact syntax so try them in the terminal first and see if they work

---

### Post by zacharyrs on 2009-07-08
> **bear24rw said:**
> in keyboard shortcuts you can assign them to run the command
```
amixer set master +5%
``````
amixer set master -5%
```I dont remember the exact syntax so try them in the terminal first and see if they work

Hey, review attached screenshot. I'm not sure what I'm doing :) I appreciate your help :)

---

### Post by bear24rw on 2009-07-08
try Master with capital M i dont think the +5% and -5% are right though im trying to remember/look up

EDIT

amixer set Master 10%-
amixer set Master 10%+

try those, also alsamixer will allow you to see your current volume

---

### Post by Richardcavell on 2009-07-08
Have you installed the package pommed? It enables all your hotkeys.

Richard

---

### Post by cyberdork33 on 2009-07-09
> **Richardcavell said:**
> Have you installed the package pommed? It enables all your hotkeys.

Richard
you do not use pommed anymore (especially on newer Intel Mac), it only creates issues as the capability is built into the kernel. You should follow the docuementation for your mac version here:

[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by zacharyrs on 2009-07-09
Hi, I added the above to the terminal, but it does nothing. I select any of my three volume keys (including mute) and it does nothing. Any help would be greatly appreciated.

---

### Post by Breath! on 2009-07-10
System> Prefrences> Keyboard Shortcuts 

Find the three items, Volume Up, Volume Down and Mute. Click that crazy list of numbers and letters and it will change to 'New Accelerator...' . Now press the Volume Up key. Repeat those steps for the other two keys.

---

### Post by zacharyrs on 2009-07-12
> **Breath! said:**
> System> Prefrences> Keyboard Shortcuts 

Find the three items, Volume Up, Volume Down and Mute. Click that crazy list of numbers and letters and it will change to 'New Accelerator...' . Now press the Volume Up key. Repeat those steps for the other two keys.

Hi, I tried this and this does not work. The three volume keys were selected as the keyboard shortcuts, but to no avail. 

Any help on figuring other options for this would be greatly appreciated :)

---

