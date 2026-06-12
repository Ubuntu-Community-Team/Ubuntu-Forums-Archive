---
title: "This is A REALLY strange error"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by spamoom on 2006-04-07
hi there, i am very new to linux and ubuntu, but i would really appreciate some help. Right the problem... 
I have just installed the breezy badger version of ubuntu and once it has installed, i login and everything works excellently. Once i reset my laptop ubuntu loads up up to the brown loader then when my loading icon on the mouse appears the whole system freezes, but i can still Ctrl+alt+del to reset it. i have tried installing this about 3 times and it has always been the same error everytime.

 Please can someone help me with this problem?????

---

### Post by taurus on 2006-04-07
Could be a problem with your video card!  What video card do you have anyway?  Try using a generic driver for now until you install the right driver for it.  Hold down <Ctl><Alt>F2 to get to a console.  Log in with your username and password.  That would drop you into a prompt, waiting for your commands.  Type
```

sudo nano /etc/X11/xorg.conf  <-- that would be capital X11, not x11...

```
Now, scroll down toward the buttom of the file until you get to the section about your video card.  Replace whatever it says right now with the word vesa as in
```

Driver                    "vesa"

```
Save it and exit by holding down <Ctrl> while hitting x.  Say y at the question.  Now, reboot and see what happens...

---

### Post by spamoom on 2006-04-07
i am sorry, i am really new. When do i hold ctrl alt f2 down?

---

### Post by trent dillman on 2006-04-07
When you get to the borked screen.

Also, try this command:

```
rm -r /tmp/gconf*
```

---

### Post by taurus on 2006-04-07
[QUOTE=spamoom]i am sorry, i am really new. When do i hold ctrl alt f2 down?[/QUOTE]
Wait for the system to finish booting.  When you see the login screen (drum sound), that's where you do <Ctrl><Alt>F2.  ;)

---

### Post by spamoom on 2006-04-07
nope, now i cant even Ctrl alt DEl it it completely freezes.!:-k

---

### Post by trent dillman on 2006-04-07
boot into recovery mode and follow taurus's advice about changing to vesa.

---

### Post by spamoom on 2006-04-07
[QUOTE=taurus]Wait for the system to finish booting.  When you see the login screen (drum sound), that's where you do <Ctrl><Alt>F2.  ;)[/QUOTE]

it dont even get to that, it just freezes with a black screen and the while loadign thingy

---

### Post by spamoom on 2006-04-07
[QUOTE=taurus]Could be a problem with your video card!  What video card do you have anyway?  Try using a generic driver for now until you install the right driver for it.  Hold down <Ctl><Alt>F2 to get to a console.  Log in with your username and password.  That would drop you into a prompt, waiting for your commands.  Type
```

sudo nano /etc/X11/xorg.conf  <-- that would be capital X11, not x11...

```
Now, scroll down toward the buttom of the file until you get to the section about your video card.  Replace whatever it says right now with the word vesa as in
```

Driver                    "vesa"

```
Save it and exit by holding down <Ctrl> while hitting x.  Say y at the question.  Now, reboot and see what happens...[/QUOTE]

ok i got the file open but it is empty... this doesnt seem right to me:-k

---

### Post by taurus on 2006-04-07
/etc/X11/xorg.conf as in capital x and number eleven, X11, NOT capital x with two letter l's, Xll!

---

### Post by spamoom on 2006-04-07
[QUOTE=taurus]/etc/X11/xorg.conf as in capital x and number eleven, X11, NOT capital x with two letter l's, Xll![/QUOTE]


yea i put in X11 not Xll

but its blank :(

---

### Post by taurus on 2006-04-07
[QUOTE=spamoom]yea i put in X11 not Xll

but its blank :([/QUOTE]
Okay, what is the output of this command from a terminal or prompt,
```

ls -la /etc/X11 <--  again, capital x and number 11, X11  :) 

```

---

### Post by spamoom on 2006-04-07
[QUOTE=taurus]Okay, what is the output of this command from a terminal or prompt,
```

ls -la /etc/X11 <--  again, capital x and number 11, X11  :) 

```[/QUOTE]


well it looks like the result of a windows dir command

---

### Post by taurus on 2006-04-07
So what's the output of that command then?

---

### Post by spamoom on 2006-04-07
[QUOTE=taurus]So what's the output of that command then?[/QUOTE]

not sure what you mean, this is in it if it helps

-rw-r--r--  1 root root 3054 Apr  5 20:11 xorg.conf

---

### Post by taurus on 2006-04-07
[QUOTE=spamoom]not sure what you mean, this is in it if it helps

-rw-r--r--  1 root root 3054 Apr  5 20:11 xorg.conf[/QUOTE]
It's NOT empty!!!  Do you see the number 3054 there?  If the file is empty, it would have 0...  Okay, try this then.
```

cd /etc/X11
sudo nano xorg.conf

```

---

### Post by spamoom on 2006-04-07
oh my god, thanks very much. Changed value rebooting now. News in a min

EDIT: after reboot, it freezes at the black screen again

---

### Post by taurus on 2006-04-07
[QUOTE=spamoom]oh my god, thanks very much. Changed value rebooting now. News in a min

EDIT: after reboot, it freezes at the black screen again[/QUOTE]
What did you change it to, nv or vesa?  I recommand you change it to vesa this time...  And if it still freezes, then please post the content of your xorg.conf.
```

cd /etc/X11
more xorg.conf

```

---

### Post by spamoom on 2006-04-08
ok, im on ubuntu now. Are you sure it is the graphics card cause all i did was insert the live cd and it works. Also dont forget that i said it worked till i restarted it

---

### Post by spamoom on 2006-04-08
i still need help with the install though, everythign runs SLOW off the live cd

---

