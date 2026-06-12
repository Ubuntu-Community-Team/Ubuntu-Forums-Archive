---
title: "changing workspace switch hotkey"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by e6600 on 2008-02-24
its kind of a hassle to have ctrl-alt-right/left arrow keys to switch workspaces
how can i change/customize this?
thanks

---

### Post by y-lee on 2008-02-24
In menu go to System->Preferences->Keyboard Shortcuts and you should be able to find it and change it :)

---

### Post by aktiwers on 2008-02-24
System => Preferences => Keyboard Shortcuts

Or install compizsettings-manager:
```
 sudo apt-get install compizconfig-settings-manager
```
And run it:
```
ccsm
```
And change the action under Desktop Cube or Desktop Wall or whatever you are using :)

---

### Post by northern lights on 2008-02-24
If you're running Gutsy, it ships with compiz-fusion. If you haven't done so yet, you gotta install ccsm in order to customize desktop management. Run ```
sudo apt-get install compizconfig-settings-manager
```
Now navigate to "System > Preferences > Advanced Desktop Effects Settings". In the "Desktop" section check what plugin your using (Desktop Wall, Plane or Cube), double-click the active one and under the "Actions" tab change the hotkey.

[EDIT] - late - [/EDIT]

---

### Post by e6600 on 2008-02-24
thanks guys!!

---

