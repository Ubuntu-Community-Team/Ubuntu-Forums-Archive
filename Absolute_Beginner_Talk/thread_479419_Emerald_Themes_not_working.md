---
title: "Emerald Themes not working????"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-20
I have Beryl installed and it works fine, but the emerald themes do not work at all.  I pick different themes and nothing changes on screen.  I tried removing beryl, beryl menager, nvidia driver and reinstalled it all but it does not help.

What else can I try?  I don't want to wipe the drive and reinstall Ubuntu as I just did.

Thanx

---

### Post by drivel on 2007-06-20
Are you sure that the beryl's working?

---

### Post by Alex&amp;Linux on 2007-06-20
Heyo bagrol1  

Same thing happened to me, brief little quirks that are forgotten along with their solution, but I think I may be able to help you!

In terminal (or launch app [alt+f2]:

 beryl-manager

Make sure that your window decorator is "beryl default, emerald"
That sould fix it!

---

### Post by bagrol1 on 2007-06-20
Thanx, I hope that it will work when I try it tonight.

Another thing I'd like to ask is how to fix Beryl. Last night while trying to fix the Emerald themes I kept clicking on all the options randomly.  At one point I clicked on "Use glx" from use Nvidia drivers and the system froze.  Upon rebooting Beryl is not loaded automatically so I can work but the moment I switch to Beryl the system freezes.  How can I change the settings back to the Nvidia driver?????

---

### Post by wbwooodford on 2007-06-20
So how do you make emerald your default window decorator?

---

### Post by Alex&amp;Linux on 2007-06-20
> **bagrol1 said:**
> Thanx, I hope that it will work when I try it tonight.

Another thing I'd like to ask is how to fix Beryl. Last night while trying to fix the Emerald themes I kept clicking on all the options randomly.  At one point I clicked on "Use glx" from use Nvidia drivers and the system froze.  Upon rebooting Beryl is not loaded automatically so I can work but the moment I switch to Beryl the system freezes.  How can I change the settings back to the Nvidia driver?????

Im assuming you were using beryl-manager to change settings...not sure where the glx selection is (im at work now, and at the office, we use windows 98 ;) )

If you can open beryl-manager, you should be able to find the related options, probably in "advanced beryl options"

If youre completely stuck with a broken beryl, reinstall usually wont help as there are config files that remain!
To start fresh, enter terminal and 

  find ./beryl  [this is in your home dir I believe]

That should show you a few files, which all need to be removed!
If you cant do this with the teriminal...well..thats the only way I know how to, happy to try and help :)

---

### Post by Alex&amp;Linux on 2007-06-20
> **wbwooodford said:**
> So how do you make emerald your default window decorator?

Choosing this using beryl-manager (under window decorator) should default it to so when beryl is launched, either at startup or manually.

Though in my session manager (System -> Preferences -> Sessions) I add "emerald" as well as "beryl-manager"
Takes care of everything nicely!

---

### Post by wbwooodford on 2007-06-21
I tried to manually start emerald tonight and got this message.

Anyone seen this before?
[INDENT][I]benjamin@ClassLaptop:/usr/bin$ ./emerald
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/I][/INDENT]:(

---

