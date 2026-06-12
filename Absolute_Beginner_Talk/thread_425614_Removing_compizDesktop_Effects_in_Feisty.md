---
title: "Removing compiz/Desktop Effects in Feisty"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-04-27
Hello, everyone.

I just removed all of the compiz/Desktop Effects packages from Feisty and installed Beryl.  I noticed, however, that ubuntu-desktop was removed upon uninstalling compiz.  Will this hurt my system in any way, and if so, what should I do to resolve this?

Thanks, everyone.

Take care.

---

### Post by Belyel on 2007-04-27
Nope, ubuntu-desktop is a meta-package.  A meta-package keeps information about what should be installed as a group, so when you install "ubuntu-desktop,"  it grabs all the software that makes up the ubuntu desktop.  Removing the links won't remove the actual software.  If you're concerned, you can always ,"sudo apt-get install ubuntu-desktop" but that will probably reinstall compiz.

---

### Post by orb9220 on 2007-04-27
You don't have to unistall compiz to run beryl. All I did was unselct desktop effects.
Now under Beryl manager I can select Beryl,compiz,metacity. 

Can switch back and forth with no problems.

---

### Post by RKCole on 2007-04-28
Thanks.  All is well, then! :)

---

### Post by nemesisrobot on 2007-04-28
nope removing compiz won't hurt your system.

---

### Post by bobbob94 on 2007-04-28
A long way off, but if/when you come to upgrade from feisty to gutsy gibbon, it would be wise to put ubuntu-desktop back first tho (but otherwise you'll be fine without it as everyone else has said)

---

