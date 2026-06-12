---
title: "Firestarter Issue"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by buddah3618 on 2007-07-24
Hi

I don't know if this has been posted before, tried looking. This might be an easy one for someone. I am a fairly new Linux/Ubuntu user. I had put Firestarter in my start-up items, but kept getting a meesage at boot-up saying that I didn't have permission to run Firestarter - that I needed to be logged in as the "root". So, I removed firestarter from the start-up list, but am still getting that message at boot-up. Even though I removed it from the start-up. How can I resolve this ?  I know, I think, that I have to alter a file, but which one & where is it ??

Thanks
buddah3618

---

### Post by Al3xK3aton on 2007-07-24
Try logging in as root. In fact, I advise using root as your primary account, because it's much more powerful.

---

### Post by Seisen on 2007-07-24
**Never, Ever **log in as root unless it is absolutely necessary to fix a problem. For one that is the easiest way to hose your system and two its a major security risk!!

---

### Post by bradmayne on 2007-07-24
he's right when i was a n00bie i thought doing everything from root was the best way.  Boy was I wrong!  the sudo command is there for a reason.  Use it only when needed!

---

### Post by pistcivet on 2007-07-24
See here:
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

However, Firestarter doesn't need to be "running" to protect you.
Firestarter is just an easy way to configure iptables.

If you feel the need to see the Firestarter tray icon at start up,
the link above tells you how.

---

### Post by buddah3618 on 2007-07-25
> **buddah3618 said:**
> Hi

I don't know if this has been posted before, tried looking. This might be an easy one for someone. I am a fairly new Linux/Ubuntu user. I had put Firestarter in my start-up items, but kept getting a meesage at boot-up saying that I didn't have permission to run Firestarter - that I needed to be logged in as the "root". So, I removed firestarter from the start-up list, but am still getting that message at boot-up. Even though I removed it from the start-up. How can I resolve this ?  I know, I think, that I have to alter a file, but which one & where is it ??

Thanks
buddah3618


As I had stated before, I HAD it in the start-up, but removed it. I kept getting a message saying that I didn't have permission to run it. But, even after I removed it I kept getting that message. What I need to know is how can I stop that message from coming up. Also, I was thinking, when I login as the root, I have firestarter in the start-up on that account. Could it be causing this issue in the other account since root settings affect the whole system? 

Thank-you
buddah3618 :)

---

### Post by pistcivet on 2007-07-25
When you are in the "Sessions" dialog do you see Firestarter mentioned in either the
"Current Session" or "Startup Programs" tabs?
If you see it in the "Current Session" you can highlight it, and at the bottom there is a drop down
menu you click, then select "Trash". Save the session and reboot.

(I'm running Absolute not Ubuntu right now, so I hope I have the names close to correct)

Also wondering if you opened Synaptic, found Firestarter and selected "mark for complete removal"?

P.S.
There is no root account in Ubuntu, so you cannot "log in as root".
The first user you create has sudo privileges, other users can too, if you give it to them.
If you did something to enable a root account in Ubuntu, it was unnecessary and unwise.

---

### Post by buddah3618 on 2007-07-26
Hey - I just uninstalled/reinstalled it & now it seems to be behaving itself. LOL ( so far ).
Thank-you for all your help. I don't know why I didn't think of it myself. Thanks again though. :)  

P.S.  Hey pistcivet - I just wanted to say that Ubuntu does have a root account that is normally hidden. I had to enable it so I could login in order to do AVG updates, then I switch back to my other account for everyday work. But, that is another issue - still trying to get that one answered.

Thanks
buddah3618

---

### Post by Seisen on 2007-07-26
> **buddah3618 said:**
> Hey - I just uninstalled/reinstalled it & now it seems to be behaving itself. LOL ( so far ).
Thank-you for all your help. I don't know why I didn't think of it myself. Thanks again though. :)  

P.S.  Hey pistcivet - I just wanted to say that Ubuntu does have a root account that is normally hidden. I had to enable it so I could login in order to do AVG updates, then I switch back to my other account for everyday work. But, that is another issue - still trying to get that one answered.

Thanks
buddah3618

For avg just run it from the terminal and put gksudo in front of the command.

---

### Post by buddah3618 on 2007-07-28
OK, but what is the command to do that?  I am fairly new at Linux/Ubuntu. I know that it would start like this " sudo .... " , but what is the rest?

Thanks
buddah3618

---

