---
title: "How to Enable root account?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by poision_heart on 2007-10-29
Hi there i am new in ubuntu world.Can you please guide me how to enable root account?And also guide me how computer icon will come on desktop?Thanks in advance.

---

### Post by Maestro23 on 2007-10-29
RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

I don't know what you're looking for with your 2nd question. Can you explain?

---

### Post by poision_heart on 2007-10-29
Hi i want "computer" launcher on desktop for easy access of drives on my laptop.Computer  is located under places of gnome menu.Well thanks for that link.

---

### Post by por100pre1 on 2007-10-29
> **poision_heart said:**
> And also guide me how computer icon will come on desktop?
[B]
gTweakUI - Nautilus[/B] will do the task:

```
sudo aptitude install gtweakui
```

You'll find it in **System> Preferences**. :)

---

### Post by bapoumba on 2007-10-29
> **poision_heart said:**
> Hi i want "computer" launcher on desktop for easy access of drives on my laptop.Computer  is located under places of gnome menu.Well thanks for that link.
Open gconf-editor > Apps > Nautilus > Desktop > Tick computer_icon_visible
All set!

---

### Post by poision_heart on 2007-11-01
Hi i ve tried gconf theory but nothing happened.May be something lacking from my side.Can you please guide me in easy way please.Thanks

---

### Post by por100pre1 on 2007-11-01
> **poision_heart said:**
> Hi i ve tried gconf theory but nothing happened.May be something lacking from my side.Can you please guide me in easy way please.Thanks

Have you tried **gTweakUI - Nautilus**? It can't be easier than that.

---

### Post by bodhi.zazen on 2007-11-01
To enable your root account :

```
sudo passwd
```

Enter a new password.

To disable it again :

```
sudo passwd root -L
```

---

