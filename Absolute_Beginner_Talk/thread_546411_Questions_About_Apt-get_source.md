---
title: "Questions About Apt-get source"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Linux_Man on 2007-09-08
To get some more speed from Ubuntu (7.04) on Firefox mostly, I decided to compile it from souce. After checking synaptic and doing a "complete removal" (And then clicking apply) So I then did sudo apt-get build-deb firefox then sudo apt-get -b source firefox
After checking to make sure that source was enabled in synaptic. After an hour or so of constant processing, finally it was done and I did dpkg -i for all the firefox versions, after getting a strange error message on "Add/remove programs" and doing the steps (Apt-get update and something else with a flag of f that I can't remember) It worked again. However the Update manager keeps saying that I need to update firefox to version 2.0.0.6 even though that was the version I compiled, also my cookies, and boomarks are still existing as are my settings even in about:config. Did I really compile Firefox right? And why is the update manager telling me that Im outdated? 

The Help/About Firefox displays

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)

---

### Post by Happy_Man on 2007-09-08
I'm thinking that Ubuntu considers its version of Firefox is more recent than the compiled version (even though it's really not....). There's a command to have Apt ignore updates for certain packages, but I'm not sure it'll work for compiled apps.

---

### Post by Linux_Man on 2007-09-08
Ok, thanks, I mostly wanted to know if this was default behaviour or if somehow I compiled a bad version of Firefox and really the web browser needs to be the most secure.... Also, how can I get updates on it without running it as root? Or is running it as root be a risk I have to take to update it? Because Im sure that Ubuntu's Binary package will overwrite my compiled version because I don't want to spend another hour or two redownloading and compiling it.

---

