---
title: "New and VERY Confused"
date: 2019-03-02
forum: Any Other OS
---

### Post by s.us.anna on 2019-03-02
Hi. My name is Susanna, I got a Chromebook this past Christmas, and I've got a little sister that wants to play this game Mine-craft with me. I was googling tonight and saw that there was a way to do it in a Chromebook if I installed Linux, and, well, here we are. I used this link to get me as far as I am now: [https://platypusplatypus.com/chromebooks/get-crouton-on-chromebook-guide-tutorial/](https://platypusplatypus.com/chromebooks/get-crouton-on-chromebook-guide-tutorial/) -- and I'm all good up until Step 8, and that's where things start to get a little rough. When I go to update Linux using the line of code given, I'm met with an error that says that the command 'apt-get' isn't found. I've done some more googling (please help) and found that there's other commands you can use, like wget, but those come up empty, as well. I decided to brush past the update part initially and go to the next bit about installing programs on Linux, which is where I'm met by my next problem--a program called Konsole that also is not found, and I cannot get because I can't use apt-get or find aaaannnnyyyy way to figure out how to *get *apt-get. I had to power-wash the Chromebook and start over, but seeing as I ended up in the same place and equally frustrated, I figured it was probably time to find somewhere to reach out and ask for help from someone that actually knows what they're doing. I apologize if this wasn't very coherent in a way that can get me any answers and also if this is posted in the wrong sub-forum or whatever it's called, but it's 2AM, I'm sick, and I'm entirely too dumb for coding stuff once the directions I'm given stop making sense :lol::lol::lol::lol:

Thank you for any and all help you can give ):P):P

---

### Post by The Cog on 2019-03-02
wget is not going to help - it's very different. You have to use apt-get (or in recent versions, **apt update** works the same).

But mainly, the screenshot shows something horrible happening - all the error messages above. I've never seen a chromebook so I don't know crouton, but I think something went wrong enough for the Linux desktop to have shut down. I'm not sure if you still have linux running there, or whether it has stopped completely and left you in crouton. The line near the bottom of the error messages about unmounting suggests to me that linux is no longer running at all. I'm sorry, I can't help you with that - hopefully someone else can. But your problem is with the install and crouton, not with apt-get.

If you ever get to step 8 wihtout a crash, the instructions on step 8 are wrong. They should be three separate commands. 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install
```
but the third command needs to know what to install, e.g. **sudo apt-get install mahjongg**. For now, if you ever get this far, I suggest you ignore the third command, and just do an update and an upgrade once the basic installation is working.

---

### Post by kc1di on 2019-03-02
Hello Susanna and Welcome to Ubuntu Forums,

I have do not direct experience with Crouton but [this tutorial]("https://tutorials.ubuntu.com/tutorial/install-ubuntu-on-chromebook#0") maybe clearer than the one your using.

---

### Post by Frogs Hair on 2019-03-03
Crouton is not supported by Ubuntu or Chrome Book so moved. Chrome OS is not based on any other operating system.  

[https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)

---

