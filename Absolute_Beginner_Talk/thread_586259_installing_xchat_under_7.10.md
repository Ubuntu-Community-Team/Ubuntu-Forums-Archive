---
title: "installing xchat under 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by furriner on 2007-10-22
Under Gutsy Gibbon, when I type xchat it tells me;

The program 'xchat' is currently not installed.  You can install it by typing:
sudo apt-get install xchat
You will have to enable component called 'universe'
bash: xchat: command not found

What is this universe component and how do I enable it? Typing the apt-get line without enabling universe results in it not being able to find the xchat package.

---

### Post by Jimmyfj on 2007-10-22
You can install Xchat from Synaptic. This will fetch all depending programs/files for you as well. Else you can try installing Xchat from Programs>Add/Remove Programs.

Edit: Just installed Xchat from Programs>Add/Remove Programs and it works fine

---

### Post by Lord_Dicranius on 2007-10-22
"Universe" might be referring to the universe repository.  You can enable that from Synaptic(System>Administration>Synaptic) by going "Settings>Repositories" and checking the box next to "community-maintained Open Source software (universe)".  Then just put "xchat" in the search line, check for install, then click apply at the top of that Synaptic window.  As Jimmyfj said, this'll install all of the dependencies as well.

---

