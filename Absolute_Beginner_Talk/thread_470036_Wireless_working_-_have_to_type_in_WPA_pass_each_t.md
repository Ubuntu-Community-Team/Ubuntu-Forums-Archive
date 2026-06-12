---
title: "Wireless working - have to type in WPA pass each time"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by bren on 2007-06-10
Each time I boot and wireless starts to connect a screen comes up asking me to enter my WPA password (feisty).    I have NetworkManager Applet 0.6.4 installed.

When i enter the pass it  starts correctly

See attached screenshot

Any answers on why this pass is not saved?

Bren

---

### Post by gerscht on 2007-06-10
that's to unlock your keyring.
If you use the same passwords on your keyring as in your normal login, follow these instructions([http://ubuntuforums.org/showthread.php?t=463639](http://ubuntuforums.org/showthread.php?t=463639)) to get rid of the second authentication

---

### Post by bren on 2007-06-11
hi gerscht

thanks for you reply.... after my first post i did some more searching and found the same thread (i didnt know to search for keyring the first time).

at the moment i dont want to use the same login so will continue to type the pass each time.

i hope this is something that will be fixed for the next release?

bren

---

### Post by ugm6hr on 2007-06-11
This removes the keyring:
rm $HOME/.gnome2/keyrings/default.keyring
(or just delete the file in Nautilus)

If you reboot - it will ask for a new keyring password (as well as the WPA key when you connect).  Just make the keyring password something simpler than a 64-digit key (I used "z").  That way you can just type "z" each reboot to connect to wifi.

Now I use Wicd rather than Network Manager - so I don't have this problem.

---

### Post by bren on 2007-06-12
thanks ugm6hr for your answer 

so are you saying that the keyword password is different to the WPA key?    And that is the keyword pass that it is asking me for each time?    And that so far I have by mistake made my keyring and WPA passwords the same and have confused them?

i.e. if i make my password for the keyring z and the WPA password (which is on my router) is a long sentence then people trying to access my network via wireless  will not just have to guess "z"?

will have a look at wicd on the web too...

thanks
bren

---

### Post by c_plus_plus on 2007-06-12
the keyring is a password stored only on your computer. If you type in the password that you set fo r your keyring, the keyring will remember the wpa password for you. There are three different passwords here:
1. wpa password
2. keyring password
3. login password

if you make 2 and 3 the same, you can follow the instructions in the thread gerscht linked to.

---

### Post by ugm6hr on 2007-06-12
> **bren said:**
> thanks ugm6hr for your answer 

so are you saying that the keyword password is different to the WPA key?    And that is the keyword pass that it is asking me for each time?    And that so far I have by mistake made my keyring and WPA passwords the same and have confused them?

i.e. if i make my password for the keyring z and the WPA password (which is on my router) is a long sentence then people trying to access my network via wireless  will not just have to guess "z"?

will have a look at wicd on the web too...

thanks
bren

As c_plus_plus says - they are different. The keyring password only keeps your WPA connection secure from other users of your computer.  It has nothing to do with your wireless connection at all, it merely "protects" the WPA password that is stored on your computer.  It's rather like having a "Master password" on Firefox - which allows you to protect the variety of different internet passwords stored on your computer with one single password.  For most home users, this is not a major security risk.

If you want to have a look at Wicd:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
I recommend the 1.2.9 testing (rather than the stable 1.2.7) version for Feisty - since I found 1.2.7 totally unstable.  You do have to ensure that wifi radar and Network Manager are uninstalled first though.  It's slightly less automatic with connecting, but is more configurable, and didn't cause intermittent dropped connections for my atheros card.

---

### Post by bren on 2007-06-12
hi guys

ok thanks i now understand keyring pass holds other passes.

i followed the thread link you suggested which tells you how to make your login pass = keyring pass [http://ubuntuforums.org/showthread.php?t=463639](http://ubuntuforums.org/showthread.php?t=463639)

Since my existing login and keyring passes were different i deleted my existing keyring (rm ~/.gnome2/keyrings/default.keyring)

I rebooted and connected wireless expecting to be asked for a new keyring pass as per screen in post #1

But i just got a wireless pass dialog.
After i entered my wpa pass i got got connected to wireless.

So, how do i prompt keyring manager to ask me for a new keyring pass?

thanks
bren

---

### Post by ugm6hr on 2007-06-12
> **bren said:**
> So, how do i prompt keyring manager to ask me for a new keyring pass?


I think you have to logout and back in (or reboot) after deleting the previous keyring.

---

### Post by bren on 2007-06-12
hi ugm6hr

rebooting didnt do it

but running sys / admin / keyring mgr once did

thanks to all for your help 

now up and running

bren

---

