---
title: "Remapping windows key?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Blyn on 2007-06-18
So... i've finally got feisty running smoothly and there was one question that i couldn't seem to find an answer for:

Is there any way of mapping actions to the windows key so that combinations can be used.  With the default keymapper, if i try to give an action (say open the menu) to the windows key, "Super L" does come up but it't can't be combined (e.g. "Super L + T" can't be done).  Is there some way i can remap the windows key so that this is possible, or will another keymapper take care of this problem... or is there another solution.  Thanks for any help!.

---

### Post by nitro_n2o on 2007-06-18
go to System->preferences->Keyboard shortcuts

---

### Post by allix on 2007-06-18
[From this post]("http://ubuntuforums.org/showpost.php?p=2340405&postcount=3")

> System > Preferences > Keyboard > Layout Options
Change the Alt/Win Key behaviour from *Default* to *Super is mapped to the Win-Keys (Default)*

Then map the win-key shortcuts in System -> Preferences -> Keyboard shortcuts.

---

### Post by krandun on 2007-06-20
Is there a terminal app to do this?
I would like to re-map my Windows and Menu keys in Fluxbox, but I don't have a System menu, &c...

Update: Oh, duh. Fluxbox 'keys' file accepts "Super_L" and "Super_R" as keys, or <Mod4> for either win key.

---

### Post by mattm591 on 2007-06-26
sorry to jump on this thread but I'm trying to do this but can't seem to use the "Super" or windows key in combination with any others.

I want super + L to lock, super + R to show the run and just super to show applications but this doesn't seem possible as it won't let me use super more than once.

Anyone know how I can do this?

---

### Post by krandun on 2007-06-26
Sorry about that. I got confused between all the threads I'm watching about mapping the Windows key. The keys file is something Fluxbox uses to map keys to actions. I'm using Fluxbox, so OBVIOUSLY the question must have been in the Fluxbox key mapping thread.
All that stuff probably isn't really what you want to know, I just didn't bother to re-read the thread before I opened my big mouth. :)

---

### Post by mattm591 on 2007-06-26
Thanks for the reply.

What is the keys file? I'm trying to remap them in the keyboard shortcut app which won't let me use the super key in combination with another (I also only have one super key).

---

### Post by RedSquirrel on 2007-06-26
> **mattm591 said:**
> Thanks for the reply.

What is the keys file? I'm trying to remap them in the keyboard shortcut app which won't let me use the super key in combination with another (I also only have one super key).

I have two super keys, "Super_R" and "Super_L". In Fluxbox, I normally set both to be ":RootMenu" (opens the right-click menu).

I experimented with other settings just now to see how it would go. I can set something like "Super_L x" to open an xterm, and "Super_L l" to open the right-click menu. In other words, I can get my "Super_L" key to do different things with different combinations.

The important thing I discovered is that I must press _**and release**_ "Super_L" and then press the second key in the combination, which is not the usual way of doing combinations; normally you would hold the first key down and then press the second key. Interesting. :o

If you're using Fluxbox, the keys file is found at ~/.fluxbox/keys. You can find more information about this file in the Fluxbox man page:

```
man fluxbox
```

---

