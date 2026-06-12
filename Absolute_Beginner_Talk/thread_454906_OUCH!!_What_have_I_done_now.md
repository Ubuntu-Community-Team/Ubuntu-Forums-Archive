---
title: "OUCH!! What have I done now"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Big_Kiwi on 2007-05-26
Hi all I need some big time help!!![-o<[-o<

Was playing around with the settings, YES I KNOWTHATS A BIG NO! NO! but I did it any way and now I found out why i shpould not do it:frown::frown:

Any way I hope some one can help me get my system back up.

what happened? well I was changing some of the settings for my mouse and Keyboard, as well as trying to install wine, and came across something about the passwords and switching them off at first I read the warning and left them allown but then I had to do it and turned off the password option and ignored the warning and then______ you gessed it, it through me in to a doss text setup.

so now when I boot up Ubuntu starts then sends me to like a doss screen ans asks me for my username and password and then nothing just the $ prompt.

what do I do to get back in to the ubuntu windows:(

---

### Post by aloshbennett on 2007-05-26
just a thought, if you could get your original xconf file, try to restore it. Emacs leaves a backup file when you edit something.

---

### Post by dave-5B on 2007-05-26
once you have logged in type startx at the command prompt
this starts the X11 server which GNOME runs on ("ubuntu windows")
If it works: look in the settings for "login window" (via the system menu in gnome)
If it doesnt work: im guessing you were messing with the file /etc/X11/xorg.conf, try posting the contents of that on here (or the bits you changed)

---

### Post by WinterWeaver on 2007-05-26
ok... when you are at the little prompt, type the following:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That will restore your xorg file.

Now type exit
and restart your pc.

hope it helps. ^_^

WW

---

### Post by Big_Kiwi on 2007-05-26
thanks Dave-5B startx works i am in>

But now I have another problem when I go in to login window I get this message "GDM (The GNome display Manager) is not running, how can I re start the GDM?

---

### Post by Outrunner on 2007-05-26
```
sudo /etc/init.d/gdm start
```

---

### Post by irish_flu on 2007-05-26
> **Big_Kiwi said:**
> 
Was playing around with the settings, YES I KNOWTHATS A BIG NO! NO! but I did it any way and now I found out why i shpould not do it:frown::frown:


Hey man, don't be hard on yourself.  Look at it this way: you played around, you had a problem, and with a little help from your friends you fixed that problem!  I bet you learned some stuff, became more comfortable working in the terminal (command prompt) environment, and generally you now know even more about your system than you did before.

Remember, the "tech support" person at your work or school doesn't know "everything", because that's impossible.  They have experience, so either they've seen the problem before or it gives them an idea as to how a new situation might turn out, and when they don't have experience with something that tech support person turns to his/her friends, a web forum like this one, a book, etc.

Well, you obviously know how to ask other people and work through your problem; that's half of it.  By doing this, you're gaining experience.  In other words, though it might have been frustrating I think you should consider that you've had a good day!

... and if you had never played around in the first place, you would have never had this experience. Playing around is the best way to learn what to do in case stuff breaks.  :KS:

---

### Post by Big_Kiwi on 2007-05-26
Thanks for those words of encouragement irish, it makes me fell better, But I just have one last thing to do, thanks to outrunner I can now get in to my GDM system BUT!  when I start up I get the Ubuntu loading screen then it goes into a dos like screen where I have to log in ect and then enter sudo /etc/init.d/gdm start each time.

Before I messed with the it used to load straight in to Ubuntu how can I get back to that?:):)

---

### Post by dave-5B on 2007-05-27
try

sudo dpkg-reconfigure gdm

---

