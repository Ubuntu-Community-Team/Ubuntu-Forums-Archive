---
title: "accidently changed system variables"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by jargoman on 2007-05-09
in an attempt to learn shell scripting I accidentally changed many of my system variables with such stupidity as 

$ BASH_VERSION=

I was wondering if there is a command that will reset my system variables to there default settings. The only thing I can think of so far is to boot up my live disk and jot them down. 

Also are they stored in one file somewhere so I would only have to copy and paste perhaps.

---

### Post by neodarksaver on 2007-05-09
use the live cd. Your linux partition on your hard drive is same as /media/disk from livecd. you can edit ur file there.

---

### Post by Spinelli on 2007-05-09
> **jargoman said:**
> in an attempt to learn shell scripting I accidentally changed many of my system variables with such stupidity as 

$ BASH_VERSION=

I was wondering if there is a command that will reset my system variables to there default settings. The only thing I can think of so far is to boot up my live disk and jot them down. 

Also are they stored in one file somewhere so I would only have to copy and paste perhaps.

Did you edit a configuration file and add BASH_VERSION= or did you just type it at the prompt?
Typing BASH_VERSION= and the prompt will only take effect for the current session. To fix that just logout and log in again.

---

### Post by jargoman on 2007-05-09
I only typed it at command prompt. 
I thought it was a permanent change to my system but now realize it's not 
thank you

---

