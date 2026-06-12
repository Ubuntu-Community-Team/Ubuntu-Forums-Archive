---
title: "[SOLVED] problem with kde in ubuntu"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-02-07
Hi, I`ve been getting ahead of myself and made a small error and I don`t know how to get out of it.
 I`m running Gutsy on my laptop and tried to install kubuntu desktop but it didn`t work. All the packages were downloaded (I`m pretty sure) but nothing was installed. The compiz cube rotated and the terminal disappeared when it was asking which desktop I want as my default. I couldn`t find it again. 
  sudo install kubuntu-desktop doesn`t work because I don`t know where it is.
  sudo apt-get remove kubuntu-desktop doesn`t work because it hasn't installed. 
 This has not caused me a problem (I have restarted and everything seems to be working), I just dont want all these files I`ve downloaded (28 minutes worth) to cause me a problem later on.
How do I remove the files I haven`t installed yet?
 Any help would be greatly appreciated./

---

### Post by kesman on 2008-02-07
**sudo install kubuntu-desktop** won't work because "install" is not a command. Use sudo apt-get install kubuntu-desktop instead. If you installed the packages with apt-get, it's quite impossible NOT to install them but just download, if you didn't force apt to only download them.

---

### Post by jaytek13 on 2008-02-07
If you're sure that nothing was installed at all and just want to get rid of the packages that were downloaded

```
sudo apt-get clean
```

will accomplish this


But what do you mean by you can't do sudo apt-get install kubuntu-desktop because you don't know where it is?

---

### Post by nothingspecial on 2008-02-07
Thank you for your prompt reply. I did what you said and the terminal install screen has reappeared as it was before I lost it. As you can see I`m very new to this. I`ll try and take it from here.

---

### Post by nothingspecial on 2008-02-07
jaytek13, thank you. I don`t know, I must have typed something incorrectly. I`think I`ll try what you said and mess with kde when I`m a bit better at this.
ps how do I thank you both and mark this thread as solved(sorry for the stupid question)

---

### Post by kesman on 2008-02-07
Go to thread tools and set as solved. For the thanking thing, I have no idea, it must be a new feature...

---

### Post by jaytek13 on 2008-02-07
"Thread tools" at the top of the page lets you mark as solved, and the star next to the quote button is for thanks... but are you sure it's solved? I'd restart first and make sure everything is a-okay.

Or just a cntl-alt-backspace... As the other person said, it's not really possible to do a sudo apt-get install package w/o having the install take place after it's downloaded the packages unless it freezes or something. Particularly since you were receiving prompts about choosing the default desktop would incline me to believe it did do at least some installation. It may have altered some configuration files.

---

