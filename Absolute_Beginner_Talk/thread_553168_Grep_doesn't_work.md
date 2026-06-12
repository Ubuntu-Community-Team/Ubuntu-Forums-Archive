---
title: "Grep doesn't work"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by urangela on 2007-09-17
I am running ubuntu studio on an acer aspire 5570z. I am in the process of setting up my audio, I typed the following command into the shell in order to locate my alsa drivers:
grep -i audio

The command went through, and nothing happened except the cursor blinked at me, finally I got fed up and hit ctrl-z. 

I tried grepping other things, the letter a, words, phrases, I have had the same problem. Everytime I just end up hitting ctrl-z to stop the program. Then I went into synaptic and reinstalled grep. Still nothing. I tried it both from the GUI terminal, and from a shell (alt - F1).  So, I tried my first command again: grep -i audio, and let it sit over night. When I checked it this morning, I was greeted by that same blinking cursor sitting on an empty screen. I have not been able to find a bug report of this anywhere, and I have been combing forums for the past 2 days. I would really appreciate any suggestions on how to fix this. I am happy to provide any system information, log files etc that might help; provided I can find them without using grep :(.

---

### Post by Celegorm on 2007-09-17
grep by default takes input from stdin- standard input. Meaning that the blinking cursor is waiting for you to type something. The way you probably want to use it most of the time is to 'pipe' the output from some other command to grep, eg. 'ls /usr/bin | grep deb' which would print out a list of all the files in /usr/bin with the string 'deb' in them. Here's a short grep tutorial with more detailed information [http://www.codecoffee.com/tipsforlinux/articles/25.html]("http://www.codecoffee.com/tipsforlinux/articles/25.html")

You might also try ```
locate audio
``` but that's probably going to give you a lot more output than you want.

---

### Post by urangela on 2007-09-17
Thankyou, very much!!! I feel a little silly, but I am going to try this as soon as I get home! thanks again!!

---

### Post by mali2297 on 2007-09-17
> **urangela said:**
> I am running ubuntu studio on an acer aspire 5570z. I am in the process of setting up my audio, I typed the following command into the shell in order to locate my alsa drivers:
grep -i audio


I'm not sure what you meant to do, but perhaps you were looking for this:
```

lspci | grep -i audio

```
That will search the output of lspci and print any line that contains the word *audio*. It is useful for checking which sound card you have.

---

### Post by urangela on 2007-09-18
Actually, yeah, I was trying to check out my sound card. For some reason, I was under the impression that grep was used to search for files Now, having read the man page I realize that it is for finding a regular expression within a file/block of data.  Thanks for the info!:guitar::guitar:

---

### Post by Arndt on 2007-09-18
> **urangela said:**
> Actually, yeah, I was trying to check out my sound card. For some reason, I was under the impression that grep was used to search for files Now, having read the man page I realize that it is for finding a regular expression within a file/block of data.  Thanks for the info!:guitar::guitar:

To search for files, given some knowledge of their names, you can use 'locate' or 'find'.

---

