---
title: "Am I using Kubuntu or Ubuntu???"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-11
Hi
Earlier this week, I installed what I thought was an ability to switch between a Gnome or KDE desktop environment.
The command I used was 

```
sudo aptitude install kubuntu-desktop

```

Now while I can switch desktops (and have a lot more apps available) I'm surprised to find that on bootup (and shutdown) a Kubuntu logo is present. However, the login page shows an Ubuntu (notice the absence of an initial K) logo.

Is this normal? If not, what can I do to rectify things)?

Thanks
Paul

---

### Post by reacocard on 2006-08-11
that's normal. if you prefer the ubuntu boot-up art, just uninstall the kubuntu-artwork-usplash package.

---

### Post by user1397 on 2006-08-11
> **reacocard said:**
> that's normal. if you prefer the ubuntu boot-up art, just uninstall the kubuntu-artwork-usplash package.nope, actually that will do nothing.  just follow my guide (the first link in my sig) and you'll see at the bottom of the guide the exact answer to your question.

---

### Post by PaulFXH on 2006-08-12
Hi erik1397

Thanks for your reply.

The dpkg-reconfigure fix for my problem shown in your HowTo worked perfectly for me.
However, I liked your guide so much, that I installed the xfce and edubuntu packages as well with the result that my login page now shows ebuntu (although the boot and shutdown screens are ubuntu).
The ebuntu login screen also resembles the Breezy login page (although I'm using Dapper) in that no Options are shown in the bottom LHS and are replaced by language and session radio buttons.
Do you have a fix for this, too?

Thanks again
Paul

---

### Post by user1397 on 2006-08-12
> **PaulFXH said:**
> Hi erik1397

Thanks for your reply.

The dpkg-reconfigure fix for my problem shown in your HowTo worked perfectly for me.
However, I liked your guide so much, that I installed the xfce and edubuntu packages as well with the result that my login page now shows ebuntu (although the boot and shutdown screens are ubuntu).
The ebuntu login screen also resembles the Breezy login page (although I'm using Dapper) in that no Options are shown in the bottom LHS and are replaced by language and session radio buttons.
Do you have a fix for this, too?

Thanks again
Paulhave you tried the very bottom of my guide?  the part about the display manager?  i believe it goes : ```
sudo dpkg-reconfigure gdm
```and select gdm as default.  you might also want to change the login screen preferences here: system > administration > login window

---

### Post by PaulFXH on 2006-08-12
Hi 
Thanks for your reply.
Once again your guide helped me out of this problem.

Actually, it seems that the dpkg-reconfigure gdm command didn't do the trick but the login window preferences did.

Thanks again and best wishes
Paul

---

### Post by user1397 on 2006-08-12
> **PaulFXH said:**
> Hi 
Thanks for your reply.
Once again your guide helped me out of this problem.

Actually, it seems that the dpkg-reconfigure gdm command didn't do the trick but the login window preferences did.

Thanks again and best wishes
Paulno prob.  anytime

---

### Post by DiscoKiller on 2006-08-12
> **erik1397 said:**
> no prob.  anytime

that about sums up the vibe of this community...


Peace out

DK

---

### Post by PaulFXH on 2006-08-13
I would just like to add my voice to DiscoKiller's.
I'm a new Linux user and there's a lot I like about it. One of these is how easy it is to get civilized help on this forum.
After spending quite some time as a Windows user on the Microsoft.Public groups where frayed tempers and insults are not uncommon, I really find the atmosphere here to be very significantl;y more helpful.
Thanks to everybody for giving me this impression

Paul

---

