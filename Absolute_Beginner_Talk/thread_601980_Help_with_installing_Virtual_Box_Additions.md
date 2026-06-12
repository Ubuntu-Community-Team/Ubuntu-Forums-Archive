---
title: "Help with installing Virtual Box Additions"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by neekz on 2007-11-03
Hello, I am using Gutsy Gibbon(x86) and I have Virtual Box running with Windows xp installed. I want to use a usb device and so far I have done so many work arounds to get it to work to just fail to realize that I need Additions installed so I click device and VB downloaded the additions iso and placed it in my .virtual box folder but I don't know what to do next. I am really new and searched google a lot before making this thread any help will be greatly appreciated.

 btw. Windows xp is saying that I activated XP with my key too may times, has anyone encountered this?? if so what did you do to resolve this problem?? I feel like calling them and cussing them out because if it wasn't for all the crashes I wouldn't have reformatted that many times.

---

### Post by P4man on 2007-11-03
First of all, to use USB, you have to use the binary version of virtualbox, not the opensource one which is in the Ubuntu repositories. The OSE version doesnt support USB! Go to innoteks website and download the binary instead.

To install the addons, select it from the menu, then, if nothing happens in your VM, just go to "my computer", open the CD and you will see the addon installer.

Lastly, about the activation.. yeah, that was bound to happen. As far as windows is concerned, you installed it on a different machine. It makes no difference between a virtual and a real one. I'm not too sure if the EUL actually allows you to run 2 copies on the "same" machine, one in a VM and one for real. You could try calling them to reactivate, but I don't know if that won't cause trouble with your existing installation. The solution I used was.. well.. you know, slightly less legal :)

---

