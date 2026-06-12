---
title: "Xubuntu Session Management question"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by cybrkup on 2007-02-12
I've been running Kubuntu but decided today to switch to Xubuntu for the speed and I'm now a lot more familiar with Linux overall. Anyway, my question is this: is there any setting or other application that will allow me to switch to a different user without logging off the current user?

I can do that in KDE, but not Xubuntu. Since only my wife and I use the computer this is pretty useful. Whenever you log off all your applications end, but I want to keep everything as it was. 

Any suggestions?

Thanks in advance. 

CybrKup

---

### Post by Richard Kut on 2007-02-15
Hello cybrkup! You wrote:

> Whenever you log off all your applications end, but I want to keep everything as it was. 

When you logout (or shutdown), there is a checkbox on the panel that appears which says "Save session". This will restore any running applications the next time that you login.

You also wrote:

> 
is there any setting or other application that will allow me to switch to a different user without logging off the current user?

I am not in front of my Xubuntu box right now, but if there isn't a menu-click option then there is always the "old fashioned" way. Try this when you are already logged in to your session. Hit Ctrl+F1 to launch a virtual terminal. Have your wife enter her username and password. Then type

startx -- :1

This should start a new GUI session for your wife.

So now you are both logged in. To switch back to your first session, hit Ctrl+Shift+F7. To switch back to your wife's session, hit Ctrl+Shift+F8.

I hope that the above works for you. Please update this post if you have any trouble. Good luck!

---

### Post by cybrkup on 2007-02-15
Great. Thanks for the suggestion. 

FYI, another idea somebody else shared with me was to use the command > gdmflexiserver

It sounds similar to what you have. 

Thanks again.

---

