---
title: "Epson scanner"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by arijarot on 2006-08-31
Hello, 

I realize that a similar question has already been posted back in 2005 ([http://ubuntuforums.org/showthread.php?t=80693)](http://ubuntuforums.org/showthread.php?t=80693)), but no one replied... I am having the same problem: "Error: Failed to start scanner. Error during device I/O." Difference is I am running Dapper and my model is an Epson perfection 2450 photo.

I would really appreciate any help on this, thank you.

A

---

### Post by flightmaker on 2007-05-19
I've seen this problem many times with the same model scanner.

Just came over from FC5, where the scanner ws working but the USB mass storage was all broken for me.

What solved the scanner problem for me on FC5 ws to connect the scanner using the IEEE instead of the USB connection. It also worked on an old machine which only had USB1.0 sockets. I have a suspicion that something is not talking USB2.0 correctly, but I can't confirm this.

I just installed Dapper and can't get the scanner to work properly at all now. xsane fired it up once but i'm not sure how I managed it. Have you had any success with it since you posted this thread?

---

### Post by arijarot on 2007-05-20
I wish you would have posted earlier because I don't remember exactly what I did. I know that I dl a backend version of the xsane from the web. I'm not sure which site it was, but a good starting point would be [http://http://www.sane-project.org/]("http://http://www.sane-project.org/"). It worked most of the time with this solution, but was a little wonky in how I got it to work (i.e., which options I selected). Hope this helps to at least set you in the right direction!:)

---

### Post by arijarot on 2007-07-03
Update/potential resolution: 

In synaptics, install **libsane-extras** backend for the espson 2450 or in the terminal type ```
sudo apt-get install libsane-extras
```.

---

