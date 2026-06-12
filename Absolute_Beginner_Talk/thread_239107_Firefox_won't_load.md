---
title: "Firefox won't load"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2006-08-18
My Firefox doesn't load sometimes. I click on the browser icon and the busy icon appears for a few seconds and then disappears, and then nothing happens - no error messages, nothing. Sometimes it's so bad I just give up and use windows, like I am now. I don't know if it could be any of my extensions. My extensions are:
Mouse gestures
Netcraft toolbar
McAfee Site Advisor
NoScript
SpoofStick
SuperT (a tabbed browsing extension)

I'm new to Linux/Ubuntu, so if possible try to keep it simple.
Thanks in advance

---

### Post by bogoliubov on 2006-08-18
One way of finding out what the problem is might be to open up a terminal:
*Program-> Accessories -> Terminal.*
Then type:
firefox
and press enter. Usually when something's not working you'll get some output from the program.

---

### Post by bodhi.zazen on 2006-08-18
I only use a few of your extensions: NoScript and SuperT. 

Don't know about: Mouse gestures, Netcraft toolbar, McAfee Site Advisor, or SpoofStick.

If nothing else rename your firefox configuration files in your home directory. They are "hidden"  or dot (.) files.

Not sure what they are ? .mozilla, .moxilla-firefox, .firefox.

at the terminal type mv .mozilla .mozilla.bak

If firefox works great, delete the back up (.bak)directory.

Otherwise, type firefox in a terminal and post any error messages.

---

### Post by harpo_the_whale on 2006-09-26
Having exactly the same problem and I'm pretty sure it's Mcafee Site Advisor 23.0 causing your problem. I'm assuming your running the latest versions of Firefox & your extensions? You'll need to disable Site Advisor and we'll see if it works for you. I also run No Scripts. Didn't have a problem myself with Site Advisor untill I upgraded from 21.0 to 23.0. Let me know.

Harpo

---

