---
title: "Uninstalling Compiz"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by DRoll221 on 2007-05-13
Can anyone give me a walkthrough as to how to uninstall compiz, I get several errors when I type "compiz-tray-icon" in the terminal, and then it says compiz unexpectedly crashed, which is becoming expected for me. here is what it gives me in the terminal: 

(compiz-tray-icon:13822): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:13822): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:13822): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:13822): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


Help is much appreciated.

---

### Post by overdrank on 2007-05-13
> **DRoll221 said:**
> Can anyone give me a walkthrough as to how to uninstall compiz, I get several errors when I type "compiz-tray-icon" in the terminal, and then it says compiz unexpectedly crashed, which is becoming expected for me. here is what it gives me in the terminal: 

(compiz-tray-icon:13822): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:13822): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:13822): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:13822): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


Help is much appreciated.

Hi you can use synaptic package manager to remove compiz! Its under system, administration.:)

---

### Post by Ateo on 2007-05-13
Hmm.

Why use compiz-tray-icon? Just remove that and start Compiz via System -> Preferences -> Desktop Effects. Is there really a need for a compiz tray icon? I mean really?

It's not compiz that bailing out on you, it's the systray icon plugin.. Boot that to the curb. =)

---

