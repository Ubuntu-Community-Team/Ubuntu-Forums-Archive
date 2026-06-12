---
title: "Firefox Will Not Load"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by Luggy on 2005-07-21
Today when I booted up Ubuntu I got that red dot in the corner that tells me there are updates required. So I update all the things that need updating and now firefox wont load up.

```
paul@ubuntu:~$ firefox
*** loading the extensions datasource
Segmentation fault
``` 

Any ideas as to what's going wrong and how I can fix it?

---

### Post by musicman2059 on 2005-07-21
Everyone's having problems with 1.0.6.  I would recommend removing it for the time being and see if you can get your hands on 1.0.5 or 1.0.4.

---

### Post by fishfork on 2005-07-21
If you're running ordinary Ubuntu, you'll still have firefox 1.0.2, so that shouldn't be your problem. Unless you've got the backports repositories enabled? What do you get when you type the following?
```
cat /etc/apt/sources.list
```

---

### Post by nighttime on 2005-09-29
[QUOTE=Luggy]Today when I booted up Ubuntu I got that red dot in the corner that tells me there are updates required. So I update all the things that need updating and now firefox wont load up.
```
paul@ubuntu:~$ firefox
*** loading the extensions datasource
Segmentation fault
``` 
Any ideas as to what's going wrong and how I can fix it?[/QUOTE]
Hey! I have the exact same problem! Haven't been able to sole it though... except maybe for this...

```
sudo firefox
```

That works... ofcourse it's really annoying having to do it every single time you wanna open firefox... I'm looking for a better solution

---

### Post by GMachine_24 on 2005-09-29
You can use synaptec to remove mozilla-firefox and then I just installed the mozilla browser until the firefox gang get with it. the mozilla browser is good.
gmachine

---

### Post by Perfect Storm on 2005-09-30
I would recommend epiphany browser. It's alot faster than firefox and better intergrated into gnome.

```

sudo apt-get install epiphany-browser
sudo apt-get install epiphany-extensions
killall gnome-panel

```

Applications ---> Internet ---> Epiphany Web Browser


.:=The AI Dude=:.

Edit: By the way It's not a good Idea to run firefox or any other browser with sudo (or su for that matter), because of security reasons).

---

### Post by wmcbrine on 2005-09-30
I've had no problems with any version of Firefox here. Those with problems, try creating a fresh profile, or starting Firefox in safe mode.

sudo is definitely a bad idea. The reason it helps, in this case, is probably because it implies a new profile, since FF is now running as user "root". Creating a new profile in your regular account should have the same effect.

If you don't care about preserving any old settings or extensions, just "rm -r ~/.mozilla", and a new profile will be created the next time you start Firefox.

P.S. The same thing happens in Windows -- most problems stem from the profile. Only the location of the profile is different.

---

