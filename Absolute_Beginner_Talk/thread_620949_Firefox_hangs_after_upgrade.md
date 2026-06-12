---
title: "Firefox hangs after upgrade"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2007-11-23
Hello!

After I did apt-get upgrade, about a week ago, my firefox started to hang.

When I try to start firefox it opens the window, hangs and go grey.. My hdd then begins to do a rhythmic noise and nothing else works. 

However I am able to do alt + F1 and go into "command-mode" where several infos pops up every time the rhythmic noise comes. I then quickly type in "sudo shutdown -r now" between the infos and it manages to reboot after sometime. 

Anyone got a helping hand? 

Urk

---

### Post by LaRoza on 2007-11-23
Use Opera?

I am not familiar with using/upgrading FF on Ubuntu. 

How often does it do this?

---

### Post by urk_nono on 2007-11-23
Haven't tried using Opera yet, might give it a go.

It hangs everytime I open Firefox, if I don't it runs smooth as usual.

---

### Post by LaRoza on 2007-11-23
Did you try Firefox 3? Extensions won't work, except for Adblock and a few others, but I hear it is very good.

---

### Post by urk_nono on 2007-11-23
Not too fan of using betas, haven't had too good experiences with it. I'll try Opera though, used it when I was a windows-slave. 

Thanks for quick replies btw!

---

### Post by LaRoza on 2007-11-23
Sorry I couldn't figure out FF, but I gave up on it a while ago. When FF 3 comes out, I'll look into, but Opera is perfect.

---

### Post by ukripper on 2007-11-23
You can use another variant from fox family  iceape-browser and it is in repo


[http://packages.ubuntu.com/gutsy/web/iceape-browser](http://packages.ubuntu.com/gutsy/web/iceape-browser)

---

### Post by lgambett on 2007-11-23
Try to launch firefox from a terminal, not from the GUI, and when the error manifests itself give a look to the messages there... then post into the forum. I have the latest nonbeta Firefox version running on Kubuntu Gutsy, without problems.
Ciao,
Luca

---

### Post by urk_nono on 2007-11-23
Ukripper: Thanks for the advise!

lgambett: Ah! Haven't even thought of that! Those lines in "command" just gave me a headache. I'll do it when I get home. I'm still running Feisty due to some random freezes in Gutsy.

---

### Post by urk_nono on 2007-12-01
Found someone with the same issue as me [here]("http://ubuntuforums.org/showthread.php?t=590242").

However, when I do **gksudo firefox** it works :confused:

I get no error report when I type just **firefox** in terminal, it just hangs as described above.

---

