---
title: "My keyboard sound keys"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-16
How do I get my volume up/down and mute buttons to do anything?

---

### Post by HDave on 2007-12-17
Typically they work out of the box with Ubuntu, though I did manage to screw it up myself.  This guide here will help:

[http://ubuntuforums.org/showthread.php?t=27039]("http://ubuntuforums.org/showthread.php?t=27039")

---

### Post by aktiwers on 2007-12-17
Just go to System => Preferences => KeyBoard shortcuts

And the first ones on the list.  Click it once with your mouse and hit the button you want to sound up. After that do the same with sound down and mute or whatever you like :)

---

### Post by Pogeymanz on 2007-12-17
Hmm.

Everytime I click one of my sound buttons to set the shortcut to it, the shortcut shows up blank. Then I tried one of the other buttons and it says that the shortcut is alread in use. Just for the hell of it I tried it out, but they still don't do anything.

And acutally, I added the "Volume control" to my top panel (the one with Applications) and even when I use the mouse on that to change the volume, nothing happens. I'm guessing it's just not connected to the right device. I'm much more concerned with my buttons, because I use them a lot.

I'm on an HP Compaq Presario V5000 in case that helps.

---

### Post by Pogeymanz on 2007-12-17
Can anybody help me out a little bit more?

---

### Post by kernel tom on 2007-12-17
Yeah well as far as the Volume button on your panel... Right click, and make sure it is set to control your "Master" volume device.  Also a regular left-click will open up the mixer, and make sure that you are effecting the Master volume...

as far as keyboard make sure xautomation is installed.
in the terminal

sudo apt-get install xautomation

then you would want to go into your keyboard properties and see that ur multimedia keys use some command to the effect of "xf86volumeup" or something to that effect.  I'd always logout/login to see if things take effect.

-kt

---

### Post by Pogeymanz on 2007-12-17
Well, there is some progress, but still not working.

The shortcuts now do say xf86volumeup, etc.

However, the buttons still don't change the volume. They do change the volume meter in my panel, though. I swear I've watched the Nelson Mandela video probably 50 times...

also, when I'm in the keyboard settings the command for these keys is aumix -v0, aumix -v-10, and aumix -v+10. How do I find out if aumix is the right command? Should it be alsamixer or something?

---

### Post by skrribble on 2007-12-17
right click on the volume icon in the panel and select Preferences... in that window, make sure that Master is selected, not PC speaker or anything else

---

### Post by Pogeymanz on 2007-12-17
It is. Anything else?

---

### Post by Pogeymanz on 2007-12-17
I'm really clueless here. What is aumix? What do I do?! :confused:

---

### Post by HDave on 2007-12-17
I had this problem once, but I found out that the volume control was changing my MICROPHONE volume not my speaker volume.

Tell us -- are you getting any sound at all?

Go to System->Preferences->Sound and tell us what you see.

What happens when you push the "test" button?  Do you hear sound?  Are the items set to autodetect?

Did you ever hear sound from this PC?

Since your keyboard keys are working...could be time for a new thread...

---

### Post by Pogeymanz on 2007-12-17
I do get sound. Good volume and everything. But I can only change the volume in the application that is playing the media.

I'm not sure where you're telling me to look; sorry. Should I be looking Applications -> Settings -> Mixer Settings?

If I go to Applications -> System, there is no "preferences."

---

### Post by HDave on 2007-12-17
Not a problem --

On the top panel of your workspace, do you see "Applications   Places    System"??

If so, click on System, it should pop-up a menu with preferences and administration and other stuff...

---

### Post by Pogeymanz on 2007-12-17
Sigh. Unfortunately I only have an Applications tab up there. I have the Xfce desktop if that changes anything. Where else can I access these options?

---

### Post by HDave on 2007-12-18
The only thing it changes is I can't help you...as I am running GNOME and am new to this whole linux thing.

I'd suggest starting a new thread with a title like "Sound Problem with Xfce" or something like that....

Sorry!

---

### Post by Pogeymanz on 2007-12-18
Okay. Big breakthrough! I accidently made my buttons not work again, but I think it's a step forward overall. Let me give a picture of what I have now:

I have sound. The sound is fine.

The volume control that I have in my top panel changes my volume if it's set to PCM and NOT Master.

But my volume-up,volume-down, and mute buttons on my keyboard don't do anything at all again.

If I open my Keyboard Settings and go to shortcuts it has commands "aumix -v0". "aumix -v-10", and "aumix -v+10" with the shortcuts being things like xf86AudioMute, etc.

If I try to change those shortcuts by clicking them and pushing the button on my keyboard, a blank appears.

So, let's see if someone can't help me some more...

---

