---
title: "HELP! Black Screen After Login"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Alienist on 2007-10-30
- Using Gusty with no (major) problems for several days, but now...

- While in a session, doing nothing abnormal, just web surfing, the whole desktop stops responding. I can't open programs, move windows, right-click, etc.

- I restart. I can get to the login screen, can enter name/password, the ubuntu music sounds, and then I either see the blank orange splash screen or a black screen. I have a movable cursor and that's it.

- I CAN'T LOAD THE DESKTOP

- I've tried reconfiguring xorg, loading a safe session and nothing works.

- Help! Thanks.

---

### Post by Six_Digits on 2007-10-30
Did you try:
```
sudo dpkg-reconfigure xserver-xorg
```

You don't recall the last thing you did?

---

### Post by Alienist on 2007-10-31
I've done that.

The only thing that I can think that I did before everything was FUBAR'd was I transfered some fonts into my .fonts folder. I can't see how that would do anything though. Thanks for responding.

---

### Post by Alienist on 2007-10-31
This sort of thing happens on every edition of Ubuntu I try. Things will go along fine, then a show-stopping bug appears and I go back to Windows. Say what you want about Windows, but I've never had to reinstall it because it stopped working. It's frustrating and sad and makes one realize that the average pc user is never going to be able to use linux because of these weird bugs that are impossible to get help in solving. 

*sigh* Well, it was fun for a few days.

---

### Post by alienexplorers on 2007-10-31
This may be related to your adding fonts.  You might have to delete them before you can move on.

---

### Post by Alienist on 2007-10-31
Really? I don't know why, but at this point I'm willing to try anything. 

How do I delete them if I can't load Gnome? Do I use a command line? They're in my .fonts folder. I'm assuming I can delete that from the terminal, but I'm ignorant as to how. 
Thanks.

---

### Post by Alienist on 2007-10-31
Update: Deleting that fonts folder from the command line worked.

I am curious why a font (that wasn't in use, just in the folder) caused Gnome to crash. I'm also curious which font it was. I had several hundred in there. Any ideas?

---

### Post by eSkel on 2007-11-13
I started having this problem a few days ago.
I would have to reboot and at the logon screen I would click the session icon at the bottom of the page and verify that the session was starting in Gnome.  I would get the black screen about once every 5 logons.

---

### Post by glaze0101 on 2008-01-19
There is something wonky here with fonts.  I keep having the same problem and it has to do with adding fonts.  I thought it was cause Id installed my fonts wrong the first time it happened.  I solved the porblem by making another user and I was going fine til today.  I tried to install fonts again and boom.  no gnome-panel, I think that is the core of it since I can load x just no panel so no navigation.

If anyone has thoughts on this Id appreciate it.

I am reviving this old post because I had thought it was just me til I saw this.

---

