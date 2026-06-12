---
title: "The networkApplet manager Keyring problem"
date: 2009-05-16
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-16
I've Googled this and see there are tons of people who have a problem like mine or something similar, and I also see that most of them don't seem to be able to fix it.

Ever since I got my wireless working every time it starts up I get the window that says "The application &#8220;NetworkManager Applet&#8221; (usr/bin/nm-applet) wants access to the default keyring, but it is locked." So i have to give it my password, and it goes away.

I have autologin enabled (apparently this is related) but none of the fixes I have seen mentioned seems to work, and in fact most of them seem to involve prefs or pref managers that aren't even on my machine, as near as I can tell.

I'd really like the machine to just start up without any prompts that require user interaction; it's just a testing machine with nothing of any value at all on it so security is just not an issue.

Can no one rid me of this troublesome prompt? :D

Thanks.

PowerMac G4 Sawtooth, Ubuntu 9.04

---

### Post by cyberdork33 on 2009-05-16
Since this "problem" is not mac specific, you may find better info in the greater forum.

---

### Post by Benboom on 2009-05-17
Okay; I thought this might be a PPC specific thing like some of the other issues I had getting stuff running. I'll post it in the General forum.

Thanks.

---

### Post by cyberdork33 on 2009-05-17
> **Benboom said:**
> Okay; I thought this might be a PPC specific thing like some of the other issues I had getting stuff running. I'll post it in the General forum.

Thanks.
nope this is definitely generic since it occurs on every machine I have (including non-apple).

---

### Post by Benboom on 2009-05-17
Solved this way (for me, anyway):

"Re: Howto: Get Network Manager to stop asking you for your keyring password (pam_keyr 

I might have had another problem as the rest of you, but all i had to do is check one box to fix this problem. This is what i did. Also, i have 9.04. 

Menu > Preferences> Network Connections.

Then i clicked on my Wireless that i have connect automatically when i boot up. Clicked on Edit. And at the very bottom it has a box to make the connection available to all users. Check that box. 

That fixed it for me. No codes or terminal or anything."

---

