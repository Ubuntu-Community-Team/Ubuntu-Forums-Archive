---
title: "[SOLVED] wubi = ubuntu"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ~L~ on 2008-04-15
i downloaded ubuntu after i tested it on windows.
I deleted wubi after testing it and downloaded the full ubuntu disc. However the wubi interface looked better (transitions while clicking and stuff) why ?\
Can I install ubuntu wubi again on ubuntu normal , and then fully ubuntu but with the awesome wubi interface? thanks
all iwant is the cool interface of wubi with transitions while clicking and stuff

---

### Post by seepage87 on 2008-04-15
I haven't used wubi, but what you are describing may be a result of compiz not being turned on.  This should let you control the user interface enhancing graphical effects you were experiencing.  Try this:

Right Click on Desktop > Change Desktop Background > Select Visual Effect Tab and set it to extra, or something.

You can also customize them by installing the settings manager

```
sudo apt-get install compizconfig-settings-manager
```

or grab it using synaptic

---

### Post by Achtung on 2008-04-15
You need to enable desktop effects, which are probably enabled by default in the wubi install.

Install the restricted drivers for you video card if you haven't done so already.
Click System/preference/Appearance/visual effects. Enable visual effects.

To tweak the visual effects, install compizconfig settings manager.

Edited : Ha! just got beat to it ;)

---

### Post by seepage87 on 2008-04-15
Just a thought, wubi uses the Hardy beta, and you've probably installed Gutsy, so it might be a change in the UI in hardy (haven't tested it yet).  I think Hardy is being released in a little over a week though.

---

### Post by ~L~ on 2008-04-15
> **seepage87 said:**
> I haven't used wubi, but what you are describing may be a result of compiz not being turned on.  This should let you control the user interface enhancing graphical effects you were experiencing.  Try this:

Right Click on Desktop > Change Desktop Background > Select Visual Effect Tab and set it to extra, or something.

You can also customize them by installing the settings manager

```
sudo apt-get install compizconfig-settings-manager
```

or grab it using synaptic

it says 
couldnt find package  compizconfig-setting-manager
whats synoptic and how do i get it

---

### Post by prshah on 2008-04-15
> **~L~ said:**
> i downloaded ubuntu after i tested it on windows.
I deleted wubi after testing it and downloaded the full ubuntu disc. However the wubi interface looked better (transitions while clicking and stuff) why ?\
Can I install ubuntu wubi again on ubuntu normal , and then fully ubuntu but with the awesome wubi interface? thanks
all iwant is the cool interface of wubi with transitions while clicking and stuff

Press Alt+F2, then type in ```
compiz --replace
``` and press enter

If anything goes wrong, press Ctrl+Alt+F1 (that takes you to a black, basic screen) login with your username and password and give the command ```
metacity --replace
```

Then change back to GUI with Ctrl+Alt+F7

---

### Post by forrestcupp on 2008-04-15
> **~L~ said:**
> it says 
couldnt find package  compizconfig-setting-manager
whats synoptic and how do i get it

It's **compizconfig-settings-manager**.  You left the 's' out of settings.

The reason it worked in Wubi is because your video card drivers were already set up in Windows.  Wubi runs on top of Windows, so you didn't have to worry about that step.

What kind of video card do you have?  When you go to System->Preferences->Appearance and click the Visual Effects tab, what happens if you click anything other than None?

---

### Post by bodhi.zazen on 2008-04-15
> **forrestcupp said:**
> 
The reason it worked in Wubi is because your video card drivers were already set up in Windows.  Wubi runs on top of Windows, so you didn't have to worry about that step.

That is partially true. Wubi "installs" into a file which is used as a raw disk to install Ubuntu. The windows boot loader is then configured to boot Ubuntu. So while it installs within windows, it boots to Ubuntu. The windows drivers are not used (Wubi is not virtualization).

Other then installing within a file rather then a partition and using the windows boot loader it is otherwise ubuntu. They may have altered the default package list, I am not sure.

If you use wubi you can  install Ubuntu without haveing to partition your hard drive or install gurb.

> [color=lightgreen]Wubi Internals[/color]

How does Wubi work?

Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

[color=lightgreen]Is this running Ubuntu within a virtual environment or something similar?[/color]

No. **This is a real installation, the only difference is that Ubuntu is installed within a file as opposed to being installed within its own partition. Thus we spare you the trouble to create a free partition for Ubuntu.** And we spare you the trouble to have to burn a CD-Rom.

bold added by me for emphasis.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by forrestcupp on 2008-04-15
Wow.  I thought Wubi was more integrated into Windows than that.  If that's how it works, I really don't see any worthwhile benefit to a regular dual boot system.  I wonder if it's easier to share files between a Wubi install and Windows than it is in a VM.

---

### Post by bodhi.zazen on 2008-04-16
Yea, +1 on that. I think it *may* make some windows users more comfortable as they do not have to learn partition management or grub all at once.

---

