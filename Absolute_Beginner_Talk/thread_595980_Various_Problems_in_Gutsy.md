---
title: "Various Problems in Gutsy"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Ohs0Ahxi on 2007-10-29
I Performed a clean install of Gutsy last night on the whole it went well, only a couple of minor problems;

1) Session information. I've tried adding various screenlets, docks to my startup programs but they aren't saved. Never had the problem in Feisty and searching didn't seem to turn up much about the problem.

2) I'm using emerald and for some reason it doesn't seem to apply to Amarok, when i open Amarok it takes up the whole screen and has no title bar with min,max,close.

---

### Post by conjur3r on 2007-10-29
1) Open up System > Preferences > Sessions then click on the Session Options tab.  Make sure the checkbox to automatically remember your running apps is selected.

2) Not quite sure sorry.

---

### Post by Ohs0Ahxi on 2007-10-30
> **conjur3r said:**
> 1) Open up System > Preferences > Sessions then click on the Session Options tab.  Make sure the checkbox to automatically remember your running apps is selected.


Tried that, also tried saving currently running. It doesn't remember anything.

---

### Post by bllambert on 2007-10-30
I have the exact same problem with screenlets.  I ended up uninstalling it.

---

### Post by rudeboyskunk on 2007-10-30
Do you get a strange error message every time you log in telling you that your sessions cannot be saved?  That happened to me once, answered in this thread [here]("http://ubuntuforums.org/showthread.php?t=594059").

I think Amarok has sort of its own interface independent to that of Emerald, Compiz, etc.

I'm not familiar with screenlets, but if they're the same thing as gDesklets, use that instead.

---

### Post by Ohs0Ahxi on 2007-10-30
Theres no messages, and it doesn't seem to be the problem in the post you linked to.

Screenlets was just an example its the same problem with anything i try and add to my startup programs.

The problem with Amarok seems to have cured itself after numerous reboots.

---

### Post by conjur3r on 2007-10-31
It's a completely clean install isn't it? You didn't retain the home partition from a previous install?  If it is, that's the strangest I've heard.  Those settings are stored in your ~/.gnome2/session file so see if you have write access to it??

---

### Post by Ohs0Ahxi on 2007-10-31
Yep was a fresh install so I don't think it should have retained any settings/information.

Ive got read/write on ~/.gnome2/session

Glad its not just me its confused then.
Setting it to remember whats running when closed worked slightly in that it remembered pidgin & Firefox, but not kiba-dock or any screenlets. 

Just seems very odd nothing I add stays in the list

---

### Post by Jaco Du Toit on 2007-10-31
I can't duplicate your problem on my side, however I did find this post. Maybe it is relevant:

[https://answers.launchpad.net/ubuntu/+question/12430]("https://answers.launchpad.net/ubuntu/+question/12430")

---

### Post by Ohs0Ahxi on 2007-10-31
> **Jaco Du Toit said:**
> I can't duplicate your problem on my side, however I did find this post. Maybe it is relevant:

[https://answers.launchpad.net/ubuntu/+question/12430]("https://answers.launchpad.net/ubuntu/+question/12430")

awesome thanks for that. I wasnt sure what command to use to run the sessions manager from the terminal.

```
rm ~/.config/autostart
mkdir ~/.config/autostart
```

and now it works, Still not sure what went wrong in the first place but its sorted now

---

### Post by zeltak on 2007-11-02
hi

i have the same problem with amarok (rebooting dosent work...) has anyone else having this problem and or knows how to solve it?

zeltak

---

