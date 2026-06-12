---
title: "[SOLVED] Synaptic error"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-02-25
On opening both Synaptic and Add/Remove I get an error reads:-

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

As I have no idea what to do am hoping someone can point me. I really don't want to 'break' anything.

---

### Post by NightwishFan on 2008-02-25
I think all you need to do is open a terminal and type:
sudo dpkg --configure -a

Please correct me if I am wrong.

---

### Post by kellemes on 2008-02-25
> **NightwishFan said:**
> I think all you need to do is open a terminal and type:
sudo dpkg --configure -a

Please correct me if I am wrong.

You're correct indeed. ;-)

---

### Post by jan quark on 2008-02-25
```
sudo dpkg --configure -a
```

should solve this issue as stated above

if not try 

```
sudo apt-get -f install
```

---

### Post by kelinu on 2008-02-25
Hi...I'm having the same error as u r, and i tried the sudo thing ans it told me to type inmy password, but when i try to type it in nothing comes onto the sreen...?????What the heck is going on????

---

### Post by kellemes on 2008-02-25
> **kelinu said:**
> Hi...I'm having the same error as u r, and i tried the sudo thing ans it told me to type inmy password, but when i try to type it in nothing comes onto the sreen...?????What the heck is going on????

When typing your password nothing should come on screen, so enter the command, enter the password and <ENTER>

---

### Post by jan quark on 2008-02-25
it is completely normal that nothing is displayed when you enter your sudo password

it is just an additional security aspect

just type in your password and hit enter

---

### Post by newbeeman on 2008-02-25
Thank you.
Tried sudo dpkg --configure -a
This produced "setting up apt-file"  This has been flashing for 10 minutes.
Is this normal, or am I missing something?

---

### Post by kelinu on 2008-02-25
it tells me "sorry, try again" and i'm sure i'm typing it right.

---

### Post by newbeeman on 2008-02-25
> **kelinu said:**
> it tells me "sorry, try again" and i'm sure i'm typing it right.

Hey, 
you just highjacked my thread.
It is considered most impolite and screws up the answer process. Start your own thread.

---

### Post by NightwishFan on 2008-02-25
> **kelinu said:**
> it tells me "sorry, try again" and i'm sure i'm typing it right.

I will refuse to hijack your thread but this one post. I might as well point him out that linux is case sensitive so make sure caps lock isnt on or you are typing it in the correct context.

---

### Post by kelinu on 2008-02-25
hi ok nothing it worked thx everybody i found the prob

---

### Post by newbeeman on 2008-02-25
Some just highjacked my thread, it's still an issue would appreciate an answer.

---

### Post by NightwishFan on 2008-02-25
The process may just be taking a while. I am not sure as I never have had apt issues myself. Use the forum search for a similar issue perhaps.

---

### Post by newbeeman on 2008-02-25
Took your advice and tried the forum search again, this time I found a 
'sudo aptitude -f install'

That ran and now it's at ' Setting up apt file (2.0.8.2ubuntu2)...  
But that seems to be stuck as it's not moved in 10 minutes.
Any suggestions?

---

### Post by fenian on 2008-02-25
Try...

> sudo apt-get update

---

### Post by newbeeman on 2008-02-25
Tried that, it ran through the list of repositories then came back to the same error.
Help. I cannot add or remove programs or updates.

---

### Post by fenian on 2008-02-25
Try this reboot the computer into recovery mode (from the grub menu) and try to run...

> sudo dpkg --configure -a

again.

---

### Post by NightwishFan on 2008-02-25
Do what the post above me said. Just wait like 30 mins it might just need a while.

EDIT: Ill use mine as an example. When a command is done you will see:

kazuma@kazuma-desktop:~$ echo hello
hello
kazuma@kazuma-desktop:~$

when you see the "username@username-desktop:~$" it means the command is done until then just let it do its thing.

---

### Post by newbeeman on 2008-02-25
> **fenian said:**
> Try this reboot the computer into recovery mode (from the grub menu) and try to run...
again.

Thank you, Thank You. Fixed it.

---

