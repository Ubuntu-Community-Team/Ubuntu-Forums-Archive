---
title: "Trouble with adept upgradables (broken status) this is going to be long, sorry."
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by 56Kmodem on 2006-02-19
Hi, 

I am very confused. I was using Adept for the first time to check for upgrades and have run into many unknowns.  First off, is there a help manual for adept? When I click on the help manager handbook I get nothing - I guess it's not installed - just keeps trying to open then times out. I would love a tutorial that is extensive and detailed - truly step by step - I would save a lot of questions here. I found the kde help on installing packages but it was more like an overview and didn't explain things well - at ;

---

### Post by nalmeth on 2006-02-19
Basically, adept is just a front-end for series of terminal commands. Since adept is flaky for you right now, use a terminal until you get it sorted out.
APPLICATIONS --> ACCESSORIES --> TERMINAL
copy and paste these commands (highlight to copy text, and middle button or left and right together to paste -- makes things much easier) you will be prompted for your password:
```
sudo apt-get update
sudo apt-get upgrade
```
update will check all your current versions of all your software, and upgrade will download and install all available upgrades and their dependencies. If there are problems, post the output here
Were you trying to do more than update?

---

### Post by 56Kmodem on 2006-02-19
Nalmeth,

 This was an accidental half-finished post - kind of indicative of how the day has been going. :roll:  Could you please read and maybe respond to my later post which, I hope, explains things better?

Thanks

---

