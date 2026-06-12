---
title: "Installing Beryl from terminal."
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-24
Well.. 3 days ago I remember coming across a thread that informed me how to install Beryl via the terminal, it was very easy. And like a 1 line code.

I no longer can find that thread, my friend needs it as he would like to use Beryl. I can not find it for him, would anyone here who has experience with Beryl please explain what that code is to type in a Terminal to bring up the Beryl installer.

Also after you install Beryl and restart you open up a Terminal and type

& Beryl-Manager

correct?

---

### Post by Cypher on 2007-04-24
If you have Feisty installed, you can enable Desktop-Effects which uses COMPIZ and that might work just as well.

If it's not installed, then
```

sudo apt-get install desktop-effects

```

Enable it by going to System->Preferences->Desktop Effects.

---

### Post by marko_4454 on 2007-04-24
> **Zaosyn said:**
> Well.. 3 days ago I remember coming across a thread that informed me how to install Beryl via the terminal, it was very easy. And like a 1 line code.

I no longer can find that thread, my friend needs it as he would like to use Beryl. I can not find it for him, would anyone here who has experience with Beryl please explain what that code is to type in a Terminal to bring up the Beryl installer.

Also after you install Beryl and restart you open up a Terminal and type

& Beryl-Manager

correct?

just remember that linux is case-sensitive so Beryl-Manager is NOT beryl-manager
also....the "&" is at the end of the command.
so it would be something like this:
```
beryl-manager &
```

---

### Post by mills on 2007-04-24
did you install with that command ? if so

type "history" in the terminal see if the command is still there?

---

### Post by johnny4north on 2007-04-24
i found this command line to install beryl and emerald theme -

sudo apt-get install beryl beryl-manager emerald-themes

---

