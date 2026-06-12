---
title: "What's the right question?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Warrem on 2007-01-03
Hello again,
I guess I didn't ask the correct question when I asked about installing scanModem. However, what I should of asked is how to get software from an outside source, that is, something not already in the Add/Remove or Synaptic Package Manager and my laptop not being connected to the Internet. (I got scanModem by downloading it from my XP Desktops' CD.) 
So let me ask this another way. Let's say from time to time I may want to install Linux/Ubuntu software that is not supported. How do you get the download to the Add/Remove &/or the SPM area of Ubuntu. I'm sure I missed something somewhere in "Moving to Ubuntu Linux" and Linux for Non-Geeks". Both books were very helpful to me. But I'm sure I missed this. 
In fact, I've read many, many posts and none seem to specifically explains this. Perhaps this is so obvious that I should have gotten it already?](*,) 
So did I at least ask the right question?
Warren

---

### Post by riven0 on 2007-01-03
I'm not sure if I'm getting this, but you want to move a downloaded package to Add & Remove or Synaptic? I don't really think that's possible. 

What you would do is download the package, from say the [Debian package repository]("http://www.debian.org/distrib/packages"), and then you would install it by either double-clicking on the package, or doing sudo dpkg -i whatever_program through the terminal.

Did that answer the question?:confused:

EDIT: But once the program is installed, it should appear in Synaptic.

---

### Post by kebes on 2007-01-03
I'm not sure if I exactly understand the question... are you asking "How do I install software on Ubuntu if that software is not in the normal repository?" (The repository is what Add/Remove and Synaptic use.)

If that's your question, then the asnwer is (unfortunately) "it depends." If the software is specifically designed for Ubuntu, then the provider/company/whoever will often make an "alternate repository" available. You can then add this repository to your repo-list (in Synaptic) and the new software will appear in the list. Then you install it the usual way.

Often software will be designed for Linux but not specifically for Ubuntu. In that case you will need to download a file, and inside the file will be instructions. Depending on the software the instructions may be simple (just copy a file) or more complicated (may need to run various commands, etc.).

If the software is not Linux software, but was designed for Windows, then normally you cannot run it. (However there is a program called Wine that can run some Windows software quite well.)

This guide:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Also has instructions for various modes of installing. (Including the 'manual way' which is what you seem to be referring to.)

I'm not sure if I've answered your question properly, but I hope this helps.

---

