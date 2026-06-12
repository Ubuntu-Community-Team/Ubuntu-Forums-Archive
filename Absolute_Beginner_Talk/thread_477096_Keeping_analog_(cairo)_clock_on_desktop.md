---
title: "Keeping analog (cairo) clock on desktop"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by wink on 2007-06-18
> sudo apt-get install cairo-clock 

made the clock display on my desktop OK. However, the next time I booted up it had disappeared. If I go into terminal and enter > cairo-clock it is displayed again yet disappears the moment I close the terminal. 

This isn't a life-and-death issue but since I am still at the bottom end of the Ubuntu-Linux learning curve I'd appreciate it if someone could  explain why it is behaving this way, i.e., where did I go wrong.

Thanks,
wink

---

### Post by avik on 2007-06-18
So when you type that command, it runs in the foreground.  When you close the terminal, you're terminating cairo-clock.  Try this:

```
cairo-clock&
```

Notice the ampersand at the end, telling the program to run in the background.

Better yet, go to System->Administration->Startup Programs, and add cairo-clock, ensuring it starts up every time you log in.

Edit: Sorry, it's System -> Preferences -> Sessions -> Startup Programs.

---

### Post by mcduck on 2007-06-18
> **avik said:**
> So when you type that command, it runs in the foreground.  When you close the terminal, you're terminating cairo-clock.  Try this:

```
cairo-clock&
```

Notice the ampersand at the end, telling the program to run in the background.

Better yet, go to System->Administration->Startup Programs, and add cairo-clock, ensuring it starts up every time you log in.

It's System/Preferences/Session/Startup Programs ;)

---

### Post by wink on 2007-06-18
Thanks for your reply. Unfortunately tI have no Startup Programs entry under System > Adminstration. So I tried your suggestion (cairo-clock& from the terminal but  the behavior of the clock remained the same as I described it in my initial post. 

 Any idea what else to try?

---

### Post by croto on 2007-06-18
System -> Preferences -> Sessions -> Startup Programs

---

### Post by wink on 2007-06-18
> It's System/Preferences/Session/Startup Programs 

Aha! ;)

OK, I have added it to the startups and the behavior changed: it does show up on the desktop when I boot but only briefly. Then it's shown on the bottom panel as running in the background. 

Any way to make it stay on the desktop?

---

### Post by mcduck on 2007-06-18
> **wink said:**
> Aha! ;)

OK, I have added it to the startups and the behavior changed: it does show up on the desktop when I boot but only briefly. Then it's shown on the bottom panel as running in the background. 

Any way to make it stay on the desktop?

When you add it to your session startup don't put the '&' in the end of the command. Just use the 'cairo-clock'.

---

### Post by wink on 2007-06-18
> When you add it to your session startup don't put the '&' in the end of the command. Just use the 'cairo-clock'.

Actually I tried it both ways - with and without the ampersand - and the result is/was the same.

But at least I learned how to add/remove to the session startups.  ;)

---

### Post by avik on 2007-06-18
> It's System/Preferences/Session/Startup Programs

I'm really sorry about that! :redface:

I was using the Ratpoison Window Manager, not GNOME, so I couldn't check it.  Whoops.

---

### Post by wink on 2007-06-18
I> 'm really sorry about that!

I was using the Ratpoison Window Manager, not GNOME, so I couldn't check it. Whoops.

That's OK, you have been forgiven even though it isn't very nice to send a newbie (and an aged one at that)
chasing after phantoms. ;)

---

