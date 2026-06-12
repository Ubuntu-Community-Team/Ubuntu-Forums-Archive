---
title: "problem with installing Live CD (X server ?)"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by _lik_ on 2008-01-22
Ok, I wanted to install Live Cd and some time after installation started the message appeared saying:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

And after that the screen goes very messy, so I can not press any button. Then it stays like that and after I press few buttons the installation ends and Linux doesn't show up.
I downloaded Ubuntu (6.10 version I guess) for AMD64. I have HP laptop with Vista installed, nVidia graphic cards, 2 Gb RAM,...

How can I solve this?

---

### Post by _lik_ on 2008-01-22
Ok, I wanted to install Live Cd and some time after installation started the message appeared saying:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

And after that the screen goes very messy, so I can not press any button. Then it stays like that and after I press few buttons the installation ends and Linux doesn't show up.
I downloaded Ubuntu (6.10 version I guess) for AMD64. I have HP laptop with Vista installed, nVidia graphic cards, 2 Gb RAM,...

How can I solve this?

---

### Post by Rocket2DMn on 2008-01-22
Why 6.10 and not 7.10?  If you've already installed, you can get to a TTY (a terminal) by pressing CTRL+ALT+F1 and logging in.  Once there you can run this command which will ask questions about your hardware - do your best to answer.  Select the "nv" driver for your graphics card and on the resolutions question, use TAB to move around and SPACEBAR to select your monitor's max resolution and everything less
```
sudo dpkg-reconfigure xserver-xorg
```

If you haven't completed the install yet, you can use the alternate install cd from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom.  This will give you a text based installer which works very well.  If you still have trouble with X after install, run the command above and post back if you still have problems :)
Welcome to Ubuntu!

---

### Post by jflarm on 2008-01-22
You can also try the "Safe Graphics Mode"...it's the second option after booting the LiveCD.

---

### Post by bodhi.zazen on 2008-01-22
threads merged

---

### Post by _lik_ on 2008-01-22
Version 7.10 doesn't exist on the page I downloaded from. Here it is:
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Can you explain what was wrong when I tried to install it for the first time? And there is no text based installer on the same website. Or maybe I am doing it all wrong

---

### Post by Rocket2DMn on 2008-01-22
> **bodhi.zazen said:**
> threads merged

We know how much you love doing that!

Back on topic, that page appears to be VERY MUCH outdated.  Get the latest from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box for alternate install (unless you want to try the 7.10 LiveCD first which will probably work, esp. since you were using a much older version).  There is an alternate CD from the page you were on, but don't use it, get the latest (If you had 5.10 the "alternate" was probably just the "install" instead of "live" cd).  5.10 is 2 1/2 years old and is no longer supported.

---

### Post by _lik_ on 2008-01-22
ok, are you seure it is a live CD? I will let it install and try again tomorrow, it is going to take a little while to download....

---

### Post by _lik_ on 2008-01-22
And I never had (couldn't install) any version of Ubuntu before

---

### Post by Rocket2DMn on 2008-01-22
> **_lik_ said:**
> And I never had (couldn't install) any version of Ubuntu before

That's OK, we're here to help with the transition.  We all started at some point.

---

### Post by _lik_ on 2008-01-22
one more thing. why is this tread so different than any other. Something happened to it.

---

### Post by _lik_ on 2008-01-22
I don't get this  thing. Forget about Ubuntu for now

---

### Post by jflarm on 2008-01-22
I think you made two threads with the same subject and they merged them

---

### Post by Rocket2DMn on 2008-01-22
> **_lik_ said:**
> one more thing. why is this tread so different than any other. Something happened to it.

An administrator merged the 2 threads you started because they were the same.  Other than that, you're thread isn't very different from others that are posted here.  Your problem is fairly typical and easily fixed by using the latest version or using the alternate install cd.

> **_lik_ said:**
> I don't get this  thing. Forget about Ubuntu for now

:(  What don't you get?  We'd be happy to explain anything that confuses you.  The only problem you had was that the GUI wouldn't load, but that's an easy fix once you have Ubuntu installed.  Did you want technical details?

---

### Post by _lik_ on 2008-01-22
I can't fix the problem and therfore it can not be installed. I don't think I need techical details anymore, I won't understand it probably. This was my third cd burned with Live CD on it, and it finished in the trahs. This downloading and waiting to see that Linux can not be installed is very dissapointing. I ll stick with Vista untill I find someone here at university who could install it for me.

---

### Post by Rocket2DMn on 2008-01-22
> **_lik_ said:**
> I can't fix the problem and therfore it can not be installed. I don't think I need techical details anymore, I won't understand it probably. This was my third cd burned with Live CD on it, and it finished in the trahs. This downloading and waiting to see that Linux can not be installed is very dissapointing. I ll stick with Vista untill I find someone here at university who could install it for me.

That's why I suggested the Alternate CD, it's not a LiveCD so it doesn't load into Ubuntu, it's just for installing through an intuitive text based interface.  After installing, the GUI will probably work fine, but if for some reason it doesn't, it's an easy troubleshoot.

---

### Post by _lik_ on 2008-01-23
> **Rocket2DMn said:**
> That's why I suggested the Alternate CD, it's not a LiveCD so it doesn't load into Ubuntu, it's just for installing through an intuitive text based interface.  After installing, the GUI will probably work fine, but if for some reason it doesn't, it's an easy troubleshoot.

Easy troubleshoot but for an CS and Computer Engineering majors. For me, it is kind a hard. I want to close this tread. thank you for your help

---

### Post by Rocket2DMn on 2008-01-23
Well said, but we really are here to help the technically challenged as well.  Sorry if Ubuntu doesn't work out for you, we don't preach that it's for everybody.  Perhaps when the time is right you'll give it another shot.
Until that time, take care.

---

