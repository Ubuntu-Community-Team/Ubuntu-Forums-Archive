---
title: "Help needed!"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Keringe on 2006-09-28
My mom accidentally closed Xorg thinking Linux was like winblows and ran unnessecary apps. No I can't startup without running startx and I can't even switch users. My printer won't print black(might be the printer, not sure). .Also when I go back when typing there shows lines.How can you install Ardour? I can't figure it out.... Please help!

---

### Post by Keringe on 2006-09-28
Please can't anyone help??! How come my comment always goes for atealst 3 hours without being read when some get replied and reads within 10 minutes?

---

### Post by Albi on 2006-09-28
Wait, when you restart your computer, it doesn't start x anymore?

---

### Post by enopepsoo on 2006-09-28
does it give an error when you boot?

did you change your video driver recently?
:mrgreen:

---

### Post by Keringe on 2006-09-28
Nope qhen I restart it says I get an error that the xserver had been shut off and when I try to switch to a new user it says I can't because it only works correctly when I am on the console..

---

### Post by Keringe on 2006-09-28
No I haven't changed that either.... all I know is that it had something to do with my mother press ctrl+alt+delete then closing Xorg. I even reinstalled it as Icon 41 suggested

---

### Post by Albi on 2006-09-28
Hmm I don't know about the second error, maybe you're trying to run a second x-session without closing the first, which doesn't work properly with some graphics cards.

Under System Preferences Sessions, is show splash screen on startup enabled?

---

### Post by Keringe on 2006-09-28
Yes I will relog real quick and write down exactly what everything says

---

### Post by Mimsy on 2006-09-28
> **Keringe said:**
> How come my comment always goes for atealst 3 hours without being read when some get replied and reads within 10 minutes?

Because no one likes you. :p 

Lighten up, that was a joke. If you want your thread to get more immediate attention, you could try being a bit more descriptive in your thread titles. "Help needed" is kind of obvious, why else would you post?

If you describe the problem in the title of your thread, you also make it a lot easier for the ones who can help you to find you. That way, even though you have to wait for three hours (which is nothing, by the way, I've paid for slower tech support than that in the past) when you finally get a reply, it will be a helpful one.

You did ask.

/Mimsy

---

### Post by Keringe on 2006-09-28
OK thanks Mimsy, but here is the error

Failed to start X server(your graphical interface). It is likely it is not setup correctly. Would you like to view the X server output to diagnose the problem?

I noticed that Ubuntu also doesn't have very good grammar...

---

### Post by Johan! on 2006-09-28
try:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Albi on 2006-09-28
^what he said

---

### Post by Keringe on 2006-09-28
Nope, I tried then and Icon 41 told me ot just keep pressing enter. Is that true just keep everything blank or default?

---

### Post by Albi on 2006-09-28
Usually that will work, but if it didn't the first time, that means you gotta read what it says and actually pick the right thing.

---

### Post by Keringe on 2006-09-28
No, that isn't working.. unless I am putting in incorrect information.. if so I will correct it tomorrow. Thanks for all the help guys! Oh and if anything else pops into your heads I will gladly listen!

---

### Post by enopepsoo on 2006-09-28
I think you should try a backup of xorg.conf.  

I did a bad setup once and needed to restore my old xorg.conf to get back into X.

if it boots you into a CLI, try

cp /etc/X11/xorg.conf_[press tab]...

This will have nothing to do with your mom pressing ctrl-alt-delete, unless you have mapped that key combination to do something.  By default it does nothing in linux.  It is more likely that she rebooted it when **after** it had already frozen somehow.8)

---

### Post by Keringe on 2006-09-28
I have control alt delete set to system monitor and then she started closing programs left and right because she thought the computer was going slow because she was trying to look at like 15 videos at the same time..

---

