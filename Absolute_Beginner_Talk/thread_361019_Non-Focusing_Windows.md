---
title: "Non-Focusing Windows"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Teh Dust on 2007-02-13
Something interesting has happened to my computer and I have no idea why.
Whenever I open a new window, the window will not automatically focus itself. I have to click somewhere before it appears.

I checked around and tried some different settings in beryl with no luck.

Any help or suggestions would be greatly appreciated because this is really annoying.

---

### Post by sardion on 2007-02-13
I had this happen once.  Never could fix it, had to just blast all my beryl settings and start over.  I think its an artifact of an upgrade.  But if you remove the .beryl folder (which will erase all your settings in beryl), and then reboot, it should be ok.

---

### Post by ksenos on 2007-02-17
I am having a different issue with window focus. The past few days I can't bring a windows in front without either clicking on the title bar or the task bar (or by ALT+TAB). If for example there is a chat window that i need to bring in front and I try to click inside the window, instead coming in front it stays there without even taking focus. Sometimes though, when I switch on my computer, the problem doesn't appear. What's wrong?

---

### Post by ThrobbingBrain66 on 2007-02-17
It sounds like both problems are related to Focus Stealing Prevention (FSP).  I believe the option is in General Options in beryl settings.  I prefer to have it set to 'None'.

---

### Post by ksenos on 2007-02-17
> **ThrobbingBrain66 said:**
> It sounds like both problems are related to Focus Stealing Prevention (FSP).  I believe the option is in General Options in beryl settings.  I prefer to have it set to 'None'.

Beryl? I don't use beryl! :confused:

---

### Post by v8YKxgHe on 2007-02-17
I had this problem with Beryl! I thought it was a bug, but after updating to the latest SVN release it still happened. It's actually in one of the options.

The problem you're having is if you click _IN_ the window, the window doesn't get taken to the front, the only way it will come to the front is if you click the Window border, correct?

I'm not on Ubuntu at the moment, but it is in Beryl - I think it's the main options with the Auto  Raise and options like that. I can't remember the exact wording, but it is in there, play around with the main Auto raise type options.

---

### Post by v8YKxgHe on 2007-02-18
K, I'm on Ubuntu with Beryl now and just found the option for you. Open up Beryl Settings Manager:

General Options->Focus & Raise->Raise On Click = tick.

---

