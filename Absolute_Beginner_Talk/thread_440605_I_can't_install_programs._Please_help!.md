---
title: "I can't install programs. Please help!"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by tchase on 2007-05-11
I am a brand new Ubuntu user and I can't figure out how to install programs. I am having a problem with my wireless card, and everyone is telling me to install ndiswrapper an 7z. I downloaded both of them on another computer (since I don't have an internet connection) and transferred them to my desktop. I'm having a hard time figuring out how to use the command terminal and the synaptic manager to install them. I'm following directions I found at: [http://v6000z.googlepages.com]("http://v6000z.googlepages.com") and it keeps saying the file doesn't exist or something. I think I'm not using the command terminal properly, or I am saving the programs in the wrong place, I don't know? Please help me!

---

### Post by Bachstelze on 2007-05-11
Here's how to install Ndiswrapper "The Ubuntu Way" (TM) :

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

---

### Post by carlosqueso on 2007-05-11
you should try to find your programs from [http://packages.ubuntu.org](http://packages.ubuntu.org) if you don't have a net connection.  Then you can install them by going to the directory that they are in and typing ```
sudo dpkg -i <name of .deb file
```

---

