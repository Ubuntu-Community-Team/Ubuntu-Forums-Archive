---
title: "Remove Skype?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-02-01
How do I remove an application that was not installed with Add/Remove Applications? For example; Skype, RealPlayer, or any other application that is installed from their website. 

When I used skype before, I think it kept possession of the sound card, and caused the mic problems with Sound Recorder and  Audacity. I'd like to experiment more with  skype, but first I want to learn how to remove it.

Thanks  ):P

---

### Post by taurus on 2007-02-01
Try something like

Applications -> Accessories -> Terminal
```
sudo dpkg -r skype
```

---

### Post by RichPicker on 2007-02-01
That command "sudo dpkg -r skype" will completely romove skype, it's lib files, etc.?

The "-r" portion is the 'remove' command?

This is the same for realplayer?  "sudo dpkg -r realplayer"    ?

---

### Post by Brunellus on 2007-02-01
> **RichPicker said:**
> That command "sudo dpkg -r skype" will completely romove skype, it's lib files, etc.?

The "-r" portion is the 'remove' command?

This is the same for realplayer?  "sudo dpkg -r realplayer"    ?
try apt.  

sudo aptitude remove skype

---

### Post by Sef on 2007-02-01
> The "-r" portion is the 'remove' command?

Yes.

> sudo aptitude remove skype

That works only if you installed it with aptitude.

---

### Post by RichPicker on 2007-02-02
What is Aptitude?

---

### Post by lamego on 2007-02-02
To learn about a command, on the terminal type:
```
man command
```

---

### Post by RichPicker on 2007-02-02
Very cool Thank you much.

---

### Post by RichPicker on 2007-02-03
Two more questions:
Are these commands Linux or Unix, or both?
What book should I get to begin learning Linux?

---

### Post by Brunellus on 2007-02-05
> **RichPicker said:**
> Two more questions:
Are these commands Linux or Unix, or both?
What book should I get to begin learning Linux?
the commands are bash.  all operating systems that use bash will use those commands.  

We are now off-topic, but:  

Linux == the kernel.  Windows equiv:  KERNEL.DLL (?)
bash == the shell.  Windows equiv:  CMD.EXE.  (which itself is an equivalent to the old COMMAND.COM)

because *nix operating systems are so modular, it's possible to run different shells:  csh, tssh, sh, ash, zsh, and so forth.  But bash is the most popular one for Linux and many Free flavors of Unix, so it's the one that's taught/learnt.

I recommend Brian Ward's "How Linux Works," but others have other recommendations.

---

### Post by RichPicker on 2007-02-08
Thanks. I ordered that book from Amazon, but am going to cancel the order. There's no way I can learn linux. I've been trying to get this laptop set up, working on it daily through this forum and launchpad, for more than 2 weeks. Still the trackpad is nearly unusealbe, the screen is distorted, and I simply do not understand how to fix them. I am very very disappointed that I wasn't warned about how much linux I'd need to know to JUST get the machine set up and working. The ubuntu verbage tells only how easy , stable, and fee it is. It certainly is NOT free.

---

