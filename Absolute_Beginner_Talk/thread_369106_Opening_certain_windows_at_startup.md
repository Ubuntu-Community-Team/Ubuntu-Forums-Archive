---
title: "Opening certain windows at startup?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by geoffcj on 2007-02-24
Ok, so I got linux and beryl on my desktop, just spent 2 hours getting it to look super rad. Pretty fired up on my first Linux install.   (OK, so getting it to work with my 19" widescreen was a B*tch, but it's working now) 


What I'd love to do/have is to have a few firefox windows (gmail, google calendar, netvibes) that open and position themselves every time I start Linux.  

Is it possible?  How do I do it?   I'm still learning linux, so the clearer the better! 

Thanks, 
Geoff

---

### Post by gradedcheese on 2007-02-24
System->Preferences->Sessions takes care of that.

---

### Post by geoffcj on 2007-02-24
Graded cheese, 

Can you elaborate?   I see how maybe I could add something to the startup for firefox, but to open three windows of Firefox?  With different programs in each? 

Geoff

---

### Post by haricharan on 2007-02-24
you can use | symbol in Firefox at Edit->Preferences->Main->Home Page to set home page to more than one tab.
For example if you want gmail and google calendar as two tabs at startup of firefox u can type 
```
 www.gmail.com | www.google.com/calendar/
``` in the above mentioned location.
Then u can add firefox at startup in sessions, that wud bring up firefox as well as the tabs at system startup.

---

### Post by gradedcheese on 2007-02-24
FIrefox actually takes an optional command-line argument, for example:

```

firefox google.com

```

would cause a firefox window to open, with google.com loaded.  So you can add as many of those to your session as needed.  So, go to the "Startup Programs" tab and press "Add" and type "firefox url_goes_here" as the 'startup command', do this for each of the three things you need.

---

### Post by igknighted on 2007-02-24
Another option would be to open all the windows you want, then save the current session.  This way when you login you would go right to that state.

---

### Post by Arkian on 2007-02-24
> **gradedcheese said:**
> FIrefox actually takes an optional command-line argument, for example:

```

firefox google.com

```

Excellent - I didn't know that - thanks.

---

