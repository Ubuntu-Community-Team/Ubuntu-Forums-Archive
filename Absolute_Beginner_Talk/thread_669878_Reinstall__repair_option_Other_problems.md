---
title: "Reinstall / repair option? Other problems"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Vanquish86 on 2008-01-16
Hello all. This is my first post on these forums, as you can obviously tell. =P

I installed Ubuntu yesterday. It's great, I'm in love. I made a couple of mistakes though. I was looking for all of the pretty 3d effects like I'd seen on my friends machine (he was running PC Linux though), so I went to the desktop effects section of this forum and read a couple of guides and posts. Long story short I installed a version of compiz-fusion using the guide that's for feisty. Since then the System->Preferences->Appearance window has had a "Custom" option in it besides the usual in the Visual Effects tab, with a preferences button next to it. When I clicked to use the custom option, I lost the title bars in all my windows. I rebooted and got them back, but they look different and don't have that snazzy rubber band effect when dragged, it's like a Windows 98 window now.

I'm trying to find a way to get it back to exactly the way it was when it was first installed, and potentially have some neat effects installed for my desktop (such as the cube, rain, snow, etc.)

 For the record I'm using the restricted nvidia drivers and they appear to be working fine... Or at least they were.

Also if anyone has any information or can point me in the right direction in regards to finding a way to get certain windows programs running on Ubuntu, such as MSN Messenger (although something like trillian would be fine as well), or Photoshop, I would greatly appreciate it.


Lol I think I went on a bit long in my very first post. I'm a complete newbie to Linux, but I'm learning!... If anyone has any complete beginners introduction guides to Linux / Ubuntu I'd also appreciate it.

Sorry for dumping this big load of.. something on you guys, but any help would be greatly appreciated. As of right now I'm not even sure how to go about unintalling Ubuntu (I'm dual booted with XP using the GRUB).

If noone can help me, I'd like to thank you all anyway for at least reading this novel of an introduction. =\

---

### Post by Vanquish86 on 2008-01-16
Anybody...? :(

---

### Post by eolson on 2008-01-16
Patience lad.   Someone will be along who has an idea.   I don't.

---

### Post by eolson on 2008-01-16
It doesn't appear as if anybody's awake

Try this from the terminal.  Won't hurt

  sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Vanquish86 on 2008-01-16
Hey thanks for the reply.
I ran the command you said, and reconfigured the video card to nvidia and the display to my LCD's native resolution. It looks awesome, but it's always looked awesome, it was already running the nvidia restricted drivers fine and in the proper resolution (if not the proper refresh rate, it's running at 50Hz instead of 60).

Thanks for the help though. Now I know what to do if my resolution ever messes up. =)

---

### Post by eolson on 2008-01-16
I got lucky.  Just took a guess.

---

### Post by Sef on 2008-01-16
> 
Also if anyone has any information or can point me in the right direction in regards to finding a way to get certain windows programs running on Ubuntu, such as MSN Messenger (although something like trillian would be fine as well), or Photoshop, I would greatly appreciate it.

Msn clones:  Ubuntu comes with Pidgin, which is like trillian (Applications > Internet > Pidgin).  If you just want an msn only clone, get amsn.  It is available in the repositories (0.96), or get the newest version (0.97) from [amsn's website]("http://www.amsn-project.net/index.php").

For photoshop, the equivalent is GIMP, which comes with Ubuntu.  (Applications > Graphics > GIMP Image Editor)

---

### Post by Vanquish86 on 2008-01-16
The resolution is fine, but the other problems still exist (the title bars looking different, the loss of visual effects, etc).

---

### Post by Vanquish86 on 2008-01-17
> **Sef said:**
> Msn clones:  Ubuntu comes with Pidgin, which is like trillian (Applications > Internet > Pidgin).  If you just want an msn only clone, get amsn.  It is available in the repositories (0.96), or get the newest version (0.97) from [amsn's website]("http://www.amsn-project.net/index.php").

For photoshop, the equivalent is GIMP, which comes with Ubuntu.  (Applications > Graphics > GIMP Image Editor)

Hmm. Very interesting. How does GIMP compare to PS in terms of options, etc.?

---

### Post by Het Irv on 2008-01-17
Try to reinstall the Ubuntu Desktop. (use add/remove programs to uninstall and then reinstall).  That might fix you problems with the Windows.  Just as a precaution you may want to let someone else confim my soultion because it may do more harm that good.

---

