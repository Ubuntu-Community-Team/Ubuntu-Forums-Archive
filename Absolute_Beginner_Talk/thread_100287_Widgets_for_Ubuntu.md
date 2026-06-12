---
title: "Widgets for Ubuntu"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Thunk on 2005-12-07
Where and how do I get widgets for Ubuntu?

---

### Post by snowjunkie on 2005-12-07
I assume you are talking about gdesklets?

sudo apt-get install gdesklets
sudo apt-get install gdesklets-data

(someone correct this if I'm wrong on the command line syntax)

---

### Post by Gray. on 2005-12-07
Not really wrong but could combine in the same line.
```
sudo apt-get install gdesklets gdesklets-data
```
Make sure universe repo is enabled.

---

### Post by Thunk on 2005-12-07
Thanks, I'll try that.

---

### Post by Pablo_Escobar on 2005-12-07
I also recommend adesklets -> Less resources consuming, but there are only few widges created (most pretty fine).

adesklets are in the repos.

---

### Post by kingsidy on 2005-12-07
After you install gdesklets, if you want whichever widgets you are running, make sure to add to your startup list so that it starts each time the system boots. I use starter bar, so it starts automatically each time i boot up.
The startup is located in System > preferences > Session, then click on the startup tab, click add, and then type in gdesklets

---

### Post by mistergq on 2005-12-07
Here is a howto to do this: [http://www.ubuntuforums.org/showthread.php?t=77694](http://www.ubuntuforums.org/showthread.php?t=77694)

---

### Post by Thunk on 2005-12-13
Thanks!

Is there a good resource of widgets other than gdesklets.gnomedesktop.org?

---

