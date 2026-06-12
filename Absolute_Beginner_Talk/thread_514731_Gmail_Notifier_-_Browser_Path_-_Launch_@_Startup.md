---
title: "Gmail Notifier - Browser Path - Launch @ Startup"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2007-08-01
Just installed Gmail Notify for Ubuntu.
When I click "Go to inbox" it doesn't take me there.  I think I need to put something in the "browser path" field, at the moment it says: www-browser
Anyone know what I need to put in there to get it to launch Firefox?

Also, is there any way I can make the application load on system startup?

Thanks again :)

---

### Post by mathewb on 2007-08-01
browser path is the command to run to launch your web browser. changing that to "firefox" will get it to launch firefox.

as for auto-starting with the desktop:
1) open System->Preferences->Sessions
2) it should be at "Startup Programs"
3) Select New
4) Enter whatever you want for name, and "gmail-notify" for command
5) select ok and close the Sessions window.

it should auto-start the next time you log in.

---

### Post by AnotherMuggle on 2007-08-01
> **mathewb said:**
> browser path is the command to run to launch your web browser. changing that to "firefox" will get it to launch firefox.

as for auto-starting with the desktop:
1) open System->Preferences->Sessions
2) it should be at "Startup Programs"
3) Select New
4) Enter whatever you want for name, and "gmail-notify" for command
5) select ok and close the Sessions window.

it should auto-start the next time you log in.

Thanks for the advise.  Not home at the moment but will give it a shot when I get back.
Much appreciated.

---

### Post by syntheticintel on 2008-04-11
thanks for the advice man. 
It was helpful, got it to work.

---

