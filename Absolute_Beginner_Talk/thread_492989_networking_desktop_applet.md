---
title: "networking desktop applet"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by r_rehashed on 2007-07-05
hi all.

I removed the Networking Desktop Applet that comes in Feisty by default, by mistake.

i tried Network Monitor from 'Add to Panel' but it's different  and i used to use the default applet to connect/disconnect at will - so easy just a click.

I tried searching but can't find it anywhere in Applications/Places/System.

I need the default applet, so please help me.

even if the post is silly, i take a chance since this is 'Absolute Beginner's Talk'. :)

any help is greatly appreciated.

---

### Post by orb9220 on 2007-07-05
No problem just open your sessions manager.
System>Preferences>Sessions

Then on Startup programs look for Network Manager and check if it is checked if not checked then just check it. If it is not listed there then select new and for name type in **Network Manager** and for command type in **nm-applet --sm-disable** and click ok. 

Now Ctrl-Alt-Backspace or Logout and back in.

Hope this helped.

---

