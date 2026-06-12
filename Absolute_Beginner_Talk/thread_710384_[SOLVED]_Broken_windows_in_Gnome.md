---
title: "[SOLVED] Broken windows in Gnome"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by wooly on 2008-02-28
My Ubuntu 7.10 install is only a week old.
 I ran Update and it started to download 190 files.
Because I'm connected over dial-up, I disconnected after 8 hours.
I also downloaded some media 3rd-party packages for totem before the updates were all downloaded. So maybe that's what caused this:

Now all windows load on top of the taskbar.
I can't drag them away.
The Minimize and Close-Window buttons are missing.
When I click the Show-Desktop icon, the message is something like:
"Your Window Manager doesn't support the Show Desktop icon or you are not running a Window Manager".

Any suggestions?

---

### Post by Joeb454 on 2008-02-28
Hmmm...what happens if you hold down the Alt key and then try and drag the Windows about? (You don't have to click the title bar for this)

---

### Post by sayakb on 2008-02-28
> **wooly said:**
> My Ubuntu 7.10 install is only a week old.
 I ran Update and it started to download 190 files.
Because I'm connected over dial-up, I disconnected after 8 hours.
I also downloaded some media 3rd-party packages for totem before the updates were all downloaded. So maybe that's what caused this:

Now all windows load on top of the taskbar.
I can't drag them away.
The Minimize and Close-Window buttons are missing.
When I click the Show-Desktop icon, the message is something like:
"Your Window Manager doesn't support the Show Desktop icon or you are not running a Window Manager".

Any suggestions?

Install emerald 
```
sudo apt-get install emerald
```

And replace the current WM w/ emerald:
```
emerald --replace
```

---

### Post by wooly on 2008-02-28
Joeb454, 
The window won't drag with Alt, either.

---

### Post by Joeb454 on 2008-02-28
Ok, you could try installing emarald as suggested above, or you could hit alt+F2, and type ```
compiz --replace
``` as I think that should be installed by default...

Also try substituting compiz for metacity in the above command.

---

### Post by wooly on 2008-02-28
Joeb454,
Alt+F2 doesn't work either, but I can drag the taskbar over to the right where it won't get covered up, and get the terminal from there.

compiz is not installed.

metacity --replace 
I gave that command & hit return, there is no response and no terminal prompt. I'll give it a few minutes.

Thanks for your help.

Would this fix my problem? (from another post):
     sudo apt-get remove ubuntu-desktop 
...And then:
    sudo apt-get install ubuntu-desktop

I'm thinking I can disable all the repos except the Ubuntu CD, I won't have to download the desktop (I'm assuming it's a big file)

---

### Post by wooly on 2008-02-28
Never mind about re-installing the desktop, the window behavior is fixed. 
I guess it was the command:
   metacity --replace 
...that fixed it.

Joeb454, thanks again for your help!

---

### Post by Joeb454 on 2008-02-28
No worries...I'd check System>Preferences>Appearance though.

And then choose the Visual Effects tab, and make sure "None" is the option selected :)

There's a little thanks button on my posts too (the gold star) :lolflag: I'm joking, you don't have to use it (I'm really not that vain ;))

---

### Post by wooly on 2008-02-28
I re-booted and the window problem is back, 
although now I know that metacity --replace fixes it, at least for that session.

Guess I will remove & install  ubuntu-desktop.

---

### Post by Oldsoldier2003 on 2008-02-28
> **wooly said:**
> I re-booted and the window problem is back, 
although now I know that metacity --replace fixes it, at least for that session.

Guess I will remove & install  ubuntu-desktop.
remove emerald and make sure you turn off desktop effects, that might help in stabilizing your system

---

### Post by Joeb454 on 2008-02-28
This is what I suggested in my last post - to ensure that desktop effects are disabled :)

---

