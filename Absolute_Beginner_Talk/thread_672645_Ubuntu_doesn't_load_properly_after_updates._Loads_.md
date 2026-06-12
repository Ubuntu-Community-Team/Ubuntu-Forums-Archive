---
title: "Ubuntu doesn't load properly after updates. Loads gdm instead"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Ludford on 2008-01-19
I recently had a wubi install of ubuntu fiesty and everything was going swimmingly until I hit the updates manager.

It installed several updates (not to 7.10) and asked me to restart.

Now when I load it up I get the same screen you get when you're turning it off "running boot scripts... etc". and then I get told the Xserver isn't configured. And I get dumped into GDM.

I thought a simple sudo dpkg-reconfigure-xserver-xorg would work but after I input the command nothing happens... In fact no commands work like shutdown restart startx etc.

Any ideas?

---

### Post by unarmedninja on 2008-01-19
i had a similar problem.  I read this on digg which helped me out.  the update to xorg removed an nvidia module so xserver didnt start for me either.  I installed the older version of xserver-core and reinstalled the nvidia drivers and everything is back the way it used to be.

hope this helps.

[http://digg.com/linux_unix/Ubuntu_update_break_java_wxwidgets_and_wxpython_application](http://digg.com/linux_unix/Ubuntu_update_break_java_wxwidgets_and_wxpython_application)

---

### Post by Ludford on 2008-01-20
Will this worK? because no commands will work. And all I get is a black screen with a flashing curser like command line.

---

### Post by Ludford on 2008-01-20
No it doesn't, No commands work in the black screen command line thing I have... How do I fix this?

---

### Post by banewman on 2008-01-20
You should have an option to boot to the rescue kernel at startup - try the commands from there :)

---

### Post by Ludford on 2008-01-20
I only get Ubuntu and XP in my boot menu since I used Wubi so as not to mess with Windows's MBR.

I think the problem is that I am not being promoted for a username and password... So is there anyway to login to the command line

---

### Post by Ludford on 2008-01-20
Ok I solved this by pressing Ctrl+Alt+F2... it then prompted me for my username and password.

I could then use sudo dpkg-reconfigure xserver-xorg.

And can now login. My desktop effects are gone. So I guess I'll have to re-install my nvidia drivers using Envy.

---

### Post by bwtranch on 2008-01-20
I don't know about you, but Envy has never worked for me, and I seriously doubt that it will work in this case. The OEM website is where you need to go.

---

### Post by Ludford on 2008-01-20
> **bwtranch said:**
> I don't know about you, but Envy has never worked for me, and I seriously doubt that it will work in this case. The OEM website is where you need to go.

I tried it just to see, And it seems to be working. Desktop effects are now working and I have a Nvidia settings screen similar to windows in Applications>System Tools

I think it's fixed woo :)

---

