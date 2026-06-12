---
title: "I moved from 2k and got it all installed but.."
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by sean_ on 2005-11-16
Hey, I just perfectly installed Ubuntu. But I have a problem. When I try to enter my password, it won't work! And, if it's possible, can I trace back my username/password with a command?

---

### Post by sean_ on 2005-11-16
Oh, I might add that I cannot insert a password too.

---

### Post by raublekick on 2005-11-16
where are you trying to put the password in? at the login screen? the terminal?

---

### Post by sean_ on 2005-11-16
[QUOTE=raublekick]where are you trying to put the password in? at the login screen? the terminal?[/QUOTE]

The login screen. The one that's fullscreen.

---

### Post by darth_vector on 2005-11-16
you can change your password by booting into single user mode. see the following link for instructions: [https://wiki.ubuntu.com/LostPassword?highlight=%28password%29](https://wiki.ubuntu.com/LostPassword?highlight=%28password%29)

what do you mean by "tracing"/"inserting" passwords?

---

### Post by sean_ on 2005-11-16
I meant getting your password back. I just moved to linux so I have no idea how to boot into single user mode. And the "insert password" thing, I meant it wouldn't let me type in my password. Where it says Password: it just has the letter underline thing. When I try to type the password, nothing comes up.

---

### Post by sean_ on 2005-11-16
So... Anyone have a clue..?

---

### Post by Pionner on 2005-11-16
Try swithing to a terminal pressing Ctrl+Alt+F1   (black full screen)

Then type your username and password.
Note that the password is not showed at all when you type it.

Does it work?

---

### Post by sean_ on 2005-11-16
No, it does not work. It just says Login Incorrect.

---

### Post by rfruth on 2005-11-16
Try the wiki.ubuntu.com lostpassword link provided by darth (above)

---

### Post by sean_ on 2005-11-16
[QUOTE=rfruth]And / or try the wiki.ubuntu.com\lostpassword linl provided by darth[/QUOTE]

Do you think I ignored that post? I did do that, and it wouldn't work, I am aware on what my pw is.

---

### Post by Pionner on 2005-11-16
I'm not an expert but I think the tip from darth-vector must work.

Did you boot on single-user mode at all?
You got some error with passwd?

---

### Post by sean_ on 2005-11-16
[QUOTE=Pionner]I'm not an expert but I think the tip from darth-vector must work.

Did you boot on single-user mode at all?
You got some error with passwd?[/QUOTE]
I told you i don't know how to boot into singleuser mode.

---

### Post by racecat on 2005-11-16
Sean. Follow the link in darth-vector's link. That is where the instructions are to change an unknown password. It looks pretty straight foreward. I assume you are on the forum with another box. If you run into problems, post back. Let us know how you make out.

Good luck,
Bill

---

### Post by sean_ on 2005-11-17
Infact, I am able to log in. But now I'm just stuck at the black screen logged in. How do I go to my desktop? Btw, it's just like the login screen but it shows I'm logged in. I'm able to do the commands, but my Desktop isn't showing at all. How do I get it to even show My Computer/Desktop stuff? Like I said, I'm just still at the black screen logged in.

Well, I meant how to make it show a GUI.

Edit 2:

Let me rephrase that. I need help loading the GUI.

---

### Post by darth_vector on 2005-11-17
you dont. you use this terminal only to change your password using

passwd <username>

then you restart

shutdown -r now

---

### Post by sean_ on 2005-11-17
[QUOTE=darth_vector]you dont. you use this terminal only to change your password using

passwd <username>

then you restart

shutdown -r now[/QUOTE]

I already have my password, I'm logged in already. But it's still in the screen. I tried shutdown -r but my own account doesn't have root access -.-

---

### Post by darth_vector on 2005-11-17
try pressing

Ctrl-Alt-7

does this fix the problem?

---

### Post by sean_ on 2005-11-17
[QUOTE=darth_vector]try pressing

Ctrl-Alt-7

does this fix the problem?[/QUOTE]
No, it does not.

---

### Post by darth_vector on 2005-11-17
are you still in single user mode? if so, then you have to reboot into multiuser mode. you may have do re-edit the grub kernel argument to do this.

if not, it sounds like something is broken.

---

