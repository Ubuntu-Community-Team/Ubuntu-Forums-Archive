---
title: "Why's it not visible that you're typing a password in terminal?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by wie6Ein0 on 2007-05-25
I'm sometimes asked to enter my password when using the terminal, but it's not visible that I'm actually typing anything. Why?

For example, I'll do a "sudo install whatever" and then I get a "Password:________" within the terminal. I begin to type my password expecting to see either dots or asterisks, but NOTHING! I just type the password and press enter and it works fortunately...

I'm not saying that this is not normal, but I'd just like to know why it's the way it is...

---

### Post by cytutchi on 2007-05-25
it is normal to happen like this..

As you know its a different Operating System nad therefore the developers chose that by not seeing anything typed its even safer...this is how it was configured.

So this is how it was made to be.

That is one of the problems with Windows...some of the stuff that they did are taken today as granted and people forget that it could also be done with other ways...Linux systems give you the ability to twick the system as much as you want n bring it closer to your preferences n make it more personal!!..n off course different.

Thats what i have understood!

---

### Post by meborc on 2007-05-25
you can't see the password for security reasons - for example if you have somebody looking over your shoulder, they will not know how LONG your password is... pretty nifty :) i hate those ***** anyways

---

### Post by Bachstelze on 2007-05-25
It's like that for security reasons. If someone know how many cheracters there are in your password, it's more than half the job done for cracking it.

---

### Post by ruscoe on 2007-05-25
Something I like in KDE and have not been able to replicate in Gnome is the ability to choose how many asterisks you want to represent each character when you enter a password.

Anybody know if Gnome supports that?

---

### Post by mal on 2007-05-25
You might be interested in [this previous thread]("http://ubuntuforums.org/showthread.php?t=214393&highlight=password") initiated by aysiu.  It includes a good discussion of this issue.

Regards,

Mal

---

### Post by aysiu on 2007-05-25
Also, read this:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

P.S. The "it's for security reasons" line doesn't make sense, since you can see how many characters are in someone's password when she types it in the GUI (for Synaptic or Users Admin)--you can also listen to how many keys are pressed... or, better yet, just look at the keyboard.

---

### Post by meborc on 2007-05-26
[QUOTE=aysiu]P.S. The "it's for security reasons" line doesn't make sense, since you can see how many characters are in someone's password when she types it in the GUI (for Synaptic or Users Admin)--you can also listen to how many keys are pressed... or, better yet, just look at the keyboard.[/QUOTE]

i disagree... it is much harder to read from the keyboard then it is to see the lenght of the password on the screen... on the other hand, i'm not sure it is easy to "hide" (change) text in cli... it is easier just not to show :)

---

### Post by Bachstelze on 2007-05-26
> **aysiu said:**
> P.S. The "it's for security reasons" line doesn't make sense, since you can see how many characters are in someone's password when she types it in the GUI (for Synaptic or Users Admin)--you can also listen to how many keys are pressed... or, better yet, just look at the keyboard.

When you type your password in the GUI, the window usually disappears when you click OK. In the command-line, your password would stay visible on the screen for quite a while so anyone wanting to look at it would have easily the time to cound the stars, even if he/she entered the room after you're done typing.

No offence meant but it's funny how you think you can redesign a thirty-year-old OS...

---

### Post by kane77 on 2007-05-26
> **meborc said:**
> i disagree... it is much harder to read from the keyboard then it is to see the lenght of the password on the screen... on the other hand, i'm not sure it is easy to "hide" (change) text in cli... it is easier just not to show :)
actualy it's not that much harder :)

and the line "security reasons" does make sense.. the line in terminal stays longer that dialog window...

---

### Post by aysiu on 2007-05-26
Well, first of all, all I wanted was consistency. If the visual feedback was going to display in the GUI, I wanted it to also display in the terminal. If it wasn't going to display in the terminal, it would only make sense to also not display in the GUI. **For consistency's sake, so as not to confuse users**.

Secondly, if someone is standing behind you, she can **hear** how many times you're clacking the keys on your keyboard. The point of **also** looking at the keyboard is to **see** any of the keys your pressing. She may not see *all* of the keys you press, but she can certainly see more on your keyboard than she can by looking at the asterisks on the screen.

**Listening to key strokes and looking for keys pressed**: You hear how many key strokes are *and* may also see one or two of the actual characters in the password

**Listening to key strokes and looking at the asterisks**: You hear how many key strokes and have no idea what the actual keys are.

As for the disappearing thing: 

A) Why not also make the terminal feedback disappear then? You see the asterisks while you're typing. Once you hit *Enter* to go to the next line, the asterisks disappear. 

B) As I said before, if, in fact, someone is looking over your shoulder and isn't deaf, she can hear how many keys you've pressed, so the number of characters is easily obtained, so you don't get any added security by not displaying feedback... unless the person behind you is deaf. I've heard some pretty quiet keyboards, but I've never come across a *completely* silent keyboard.

P.S. There's absolutely no need to condescend to me. I've thought about this issue a lot and have argued about it for a very long time (see the thread above). I realize the developers are *not* going to change the behavior, but please don't make it sound as if it's so obvious that my suggestion doesn't make sense. The suggestion makes perfect sense... it just not going to be implemented.

---

### Post by seetho on 2007-05-26
I remember during my college days (a long long time ago) I managed to get the computer lab admin password by just looking at how she type it on the keyboard.  Sometimes I would just do something to lockup the terminal and I would call the admin to come unlock it.  She would then log in to the another terminal nearby and I would be watching.  The trick is to pick up just one key at a time.  After a while I would have the admin password!  (It was the boyfriend's name - not very secure either).  So be careful when you type in password even if nothing is shown on the screen.

Disclaimer:  I only used the password so that I could have more terminal time (than what was allocated to my account) to finish my assignments.  It was not for anything malicious.

---

### Post by Bachstelze on 2007-05-26
> **aysiu said:**
> P.S. There's absolutely no need to condescend to me. I've thought about this issue a lot and have argued about it for a very long time (see the thread above). I realize the developers are *not* going to change the behavior, but please don't make it sound as if it's so obvious that my suggestion doesn't make sense. The suggestion makes perfect sense... it just not going to be implemented.

That wasn't what I meant. I meant that it's been this way for more than thirty years. Surely someone though about it before you or I ;)

---

### Post by aysiu on 2007-05-26
> **HymnToLife said:**
> That wasn't what I meant. I meant that it's been this way for more than thirty years. Surely someone though about it before you or I ;)
In all fairness, thirty years ago, GUIs were not that popular (even twenty years ago, they weren't). So back then they decided "No feedback with the password." So then why did they decide however-many-years-ago (five? ten?) to make Linux GUIs give feedback for passwords?

As I said before, for me it's an issue of consistency. Inconsistency in user interface design confuses users, as you can see from the links in the first post in my thread. If there's going to be no feedback in the terminal, fine--don't put it in the GUI either, then.

I'm not trying to claim originality. I'm just expressing my opinion (which has been rejected by the Ubuntu devs). That's all.

---

