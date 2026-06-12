---
title: "Network manager dissapeared!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Unreal223linux on 2007-06-15
What can I do if the network manager icon in my gnome bar thing dissapears? I looked in the add to panel dialog box and its not there anymore either.. My wireless is still working but what if I need to connect somewhere other then home! :(

Anyone know how to get it back and have any idea why it left? I didn't do anything different and it just left after a reboot. :(

Help greatly appreciated!

---

### Post by PartisanEntity on 2007-06-15
Did you perhaps remove the notification area from your panel?

---

### Post by Unreal223linux on 2007-06-15
Nope, I didn't do anything. I can't even add it back to the panel because its not listed in the applets thing.

---

### Post by shelzmike on 2007-06-15
Maybe this will help - (Unless of course you already tried this)

Although you have obviously had it installed once, try this from the terminal:

```
sudo apt-get install network-manager-gnome network-manager-pptp
```

Then:

```
sudo NetworkManager restart
```

Same thing happened to me once. The worse that can happen is that it will tell you that it is alredy installed. Let me know how it turns out and we can troubleshoot further if needed.

---

### Post by Unreal223linux on 2007-06-15
Thanks, I was having pretty bad luck with wifi anyway(low signal strength) so I installed mint linux and it seems to be working much better! If my icon disappears again I'll give this a shot. 
Thanks for the help. :)

---

### Post by all4als on 2007-06-27
I don't remember removing my icon from my panel either. Now mine icon is gone. I did the above code by copy and insert into the terminal, I then restarted, and I still do not have the icon. Can you offer another suggestion? I usually go between two networks, and it was handy to have. thank for your help.

This is how it was resolved for me. Sorry I am slow. [http://ubuntuforums.org/showthread.php?t=419129&highlight=missing+icon+network+manager](http://ubuntuforums.org/showthread.php?t=419129&highlight=missing+icon+network+manager)

---

