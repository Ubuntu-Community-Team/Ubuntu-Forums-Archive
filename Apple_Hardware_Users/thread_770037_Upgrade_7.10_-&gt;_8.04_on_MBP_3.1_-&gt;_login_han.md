---
title: "Upgrade 7.10 -&gt; 8.04 on MBP 3.1 -&gt; login hangs?"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by sunbird on 2008-04-27
I left my computer upgrading overnight and woke up this morning with two issues. First, the computer was on, but frozen. The screen was dark, and keyboard/mouse activity would not wake it. I had to force it shut. Fearing the worst, I assumed my whole install might be busted.

But... it actually booted just fine. I get to the Hardy login screen and logged in, but logging in hangs. I left it for 5 minutes and still no desktop. Mouse/keyboard still worked so I could force gnome to quit and shutdown.

I haven't seen this issue on the forums and am wondering what I can do.

**Edit:** This is a [bug 218434]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434") with gnome-keyring-daemon and is also discussed in [here]("http://ubuntuforums.org/showthread.php?p=4751759") and [here]("http://ubuntuforums.org/showthread.php?p=4809163"). I reverted back to 7.10 until this is resolved.

---

