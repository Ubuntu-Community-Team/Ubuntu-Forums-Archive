---
title: "Password to Restart"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by ninboy on 2008-04-02
Hello everyone! I hope you're having a good day.

I have a question. I remember some years ago, a distro (not ubuntu, I don't remember which one) allowed to add password to a PC so it cannot be restart without it.

For security reasons, I want to add a password so it cannot be shut down or restarted when the screen is locked. Actually, when I lock the screen, anyone can click the "Switch user" button and the ask the machine to be restarted.

Thank you everyone! i really appreciate if someone can help me to do this or tell me is this is impossible...

---

### Post by zvacet on 2008-04-02
> anyone can click the "Switch user" button and the ask the machine to be restarted.

Even worst.If somebody else have access to your comp that person can boot in recovery mode and run commands to erase your HDD.In short,there is no 100% security if other person have acces to your comp.

---

### Post by ninboy on 2008-04-02
So, if someone has physical access to mi machine, I can do nothing? Of course they can force the PC to shut down taking down the energy, but then I can do nothing to protect reboots from the software?

---

### Post by Patb on 2008-04-02
There are all sorts of measures you can take.  For a start, you may get some good ideas on locking down your computer from [this link]("http://ubuntuforums.org/showthread.php?t=707688").

Cheers Pat.

---

### Post by zvacet on 2008-04-02
> So, if someone has physical access to mi machine, I can do nothing?

You can encrypt all HDD and then you will have to type password if you want to work.Even that can be cracked if you are against somebody who know what to do.But you can add password if you want to.

```
sudo cp /boot/grub/menu.lst /boot/grub.menu.lst.bak
```

```
gksudo gedit /boot/grub/menu.lst
```

You will find line **password topsecret**

Replace  **topsecret** with your password.Now  go to the line 

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

Replace # alternative=true to # alternative=false

Save file and close it.In terminal

```
sudo update-grub
```

---

### Post by hyper_ch on 2008-04-02
even if the machine is encrypted, with physical access they can still wipe your harddisks...

---

### Post by ninboy on 2008-04-02
Thanks all for the answers!

Well... I'm facing two people here that doesn't know too much about computer, they are the regular day-to-day users (they just use the PC for chatting, surfing the web, make some documents). I've created their accounts in Ubuntu.

The problem is sometimes I go to bed and leave ubuntu updating, or downloading something, and when I come from the college in the afternoon, they restarted the PC to go into windows. As you can imagine, that's sucks pretty bad.

So I'm not playing against some hackers who want to wipe my HD, just some end-users who doesn't know they can screw my system forcing the PC to restart even when my account is open...

That's the reason I want to add some password to the restart function in Ubuntu... Maybe hide the Restart and Shut Down button in the login screen can do the trick too...

---

### Post by bcl1713 on 2008-04-02
<ctrl><alt>F1 dumps over to a terminal that you cannot restart from without being logged in and having root access and odds are they don't know that <ctrl><alt>F6/F7 will bring them back to your x-session.  This won't stop them from hitting the button on the front of the machine though. :)

---

### Post by aysiu on 2008-04-02
> **ninboy said:**
> 
The problem is sometimes I go to bed and leave ubuntu updating, or downloading something, and when I come from the college in the afternoon, they restarted the PC to go into windows. As you can imagine, that's sucks pretty bad.

So I'm not playing against some hackers who want to wipe my HD, just some end-users who doesn't know they can screw my system forcing the PC to restart even when my account is open... I think the problem here is that you can't stop them from forcing your PC to shut down. If you just hold the power button down, it'll shut down, password or not. The problem here is a lack of respect. Just say "Hey, please don't restart my computer if I'm in the middle of something." If they can't listen to that, don't let them use your computer.

---

### Post by ninboy on 2008-04-02
> **bcl1713 said:**
> <ctrl><alt>F1 dumps over to a terminal that you cannot restart from without being logged in and having root access and odds are they don't know that <ctrl><alt>F6/F7 will bring them back to your x-session.  This won't stop them from hitting the button on the front of the machine though. :)

I think that's the best solution so far... Thanks for the idea!

> **aysiu said:**
> I think the problem here is that you can't stop them from forcing your PC to shut down. If you just hold the power button down, it'll shut down, password or not. The problem here is a lack of respect. Just say "Hey, please don't restart my computer if I'm in the middle of something." If they can't listen to that, don't let them use your computer.

That's a little complicated, but I think is like that... That's the real problem. I think I'll hide the Window partition in my disk so they're forced to use the guest user in ubuntu...

Thank you all!

---

### Post by ghost_ryder35 on 2008-04-02
> **ninboy said:**
> I think that's the best solution so far... Thanks for the idea!



That's a little complicated, but I think is like that... That's the real problem. I think I'll hide the Window partition in my disk so they're forced to use the guest user in ubuntu...

Thank you all!
Have you tried locking your session so they can not use the computer and putting a note on the monitor "DO NOT TOUCH, UPDATING"  It might work.  End users always get scared of DO NOT TOUCH signs :)

---

