---
title: "Sticky keys - hope this helps"
date: 2008-06-04
forum: Assistive Technology &amp; Accessibility
---

### Post by dryder on 2008-06-04
For those who are having trouble with the system turning off sticky-keys if two keys are pressed or if a modifier key is pressed with another key, I found a setting in Configuration Editor which has stopped that misbehaviour - for me. So, in case it helps others:

In Assistive Technologies Preferences > Keyboard Accessibility > Accessibility tab, I have always set:
1. Simulate simultaneous keypress - **ticked**
2. Disable sticky keys if two keys are pressed - [COLOR="Red"]**never ticked**[/COLOR]
Notifications: General:
3. Beep when accessibility features are turned on or off - **ticked**
4. Beep when toggle key is pressed - **ticked**
Sticky Keys:
5. Beep when a modifier key is pressed - **ticked**

However, despite 2. above, I found 100% of the time pressing a modifier key and another key undid my settings. Very annoying with a trembling hand!

Then I looked in Configuration Editor:
Applications > System Tools > Configuration Editor > desktop > gnome > accesibility > keyboard.

I noticed that '&#65279;**stickykeys_two_key_off**' was still ticked which did not seem logical given my choices. So I unselected it and since then have not had a problem.

Hope this helps and works for you - sorry, I don't know a CLI way of doing it.

David

**Administrators - can this be made sticky? It appears to be a/the solution judging by Launchpad bug reports posts.**

---

### Post by Paul S on 2008-06-05
Yes, it's a great help.  I couldn't figure out why sticky keys work so well on kde and xfce, but shut off quickly on gnome.  This seems to be the fix!

---

### Post by truant on 2008-06-06
Dryder, you're my hero.  Thanks also to Paul for hitting up the bugs in launchpad so I knew to come here.

One thing it might be worth mentioning for other people, is where the launcher for Configuration Editor is (I typed gconf-editor into a terminal, but I know some users are less confident with the commandline)

---

### Post by dryder on 2008-06-15
The plot thickens -

My computer suddenly switched itself off on Friday night. Turned on computer and continual "beep-beep-beep..."

Techinician comes out Sunday. Reseats (just pushes in) all boards, memory and CPU.

Turn on computer. Recovers from sudden turn off.

Aha - Assistive Technology settings need redoing. OK.

Firefox mod to backspace key to make it go back a page still works - great!

Two keys pressed at once - oops, Sticky keys turns off.

Check Configuration Editor as in first post and '&#65279;stickykeys_two_key_off' is ticked again! Untick it as per my first post and all is OK.

So, doesn't Assistive Technologies have a user configuration file somewhere that remembers a user's settings like other apps do and can recover properly after a crash?

Writers of this App - please ... if other apps and setings are remebered why aren't Assistive Technolgies'?

More work on this app methinks, please?

Paul S - where is the Launchpad bug report you filed?

---

### Post by izmeh on 2008-07-13
if you don't have the option in menus

```
sudo /.gconf/desktop/gnome/accessibility/keyboard
```

---

### Post by dryder on 2008-07-13
> if you don't have the option in menusIf you mean Applications>System Tools>Configuration Editor, it is in the menus and accessible.
If you mean System>Preferences>Assistive Technologies, it also is in the menu.

I am referring to the config file that loads at start-up. If there is a 'default' file that loads if the file with my changed settings is not available I would like to know where it is so I can modify the 'default' settings.

> sudo /.gconf/desktop/gnome/accessibility/keyboarddoesn't do anything in terminal -'command not found'.
David

---

### Post by Paul S on 2008-08-02
> **dryder said:**
> 
Paul S - where is the Launchpad bug report you filed?

I must be losing my mind, because I can't find it anymore.  But, I did file another related one on OOO misbehaving [https://bugs.launchpad.net/ubuntu/+bug/240933](https://bugs.launchpad.net/ubuntu/+bug/240933)

Sorry for the late reply.

---

### Post by workshop1702 on 2009-03-23
absolutley fantastic , i have been trying to cure this for over 18months my sticky keys stays on know even if i press two keys together , your suggestion to use the configuration manager and untick 'stickykeys_two_key_off has worked a treat just a shame i didnt come across you 18 months ago . thanks very much you have definatley made my day . Andrew

---

