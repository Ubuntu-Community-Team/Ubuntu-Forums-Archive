---
title: "Another install help"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by sweatyfish on 2007-04-12
Hello, 

Last night I have taken the third try at ubuntu. All other times I have gotten frustrated over installing things and taken it off my computer and put windows back on. 

This time, I installed Ubuntu Ultimate 1.3 on VMware Server. This way I can learn linux and still keep Windows. Everything is running perfect... except for my audio and video. Of course, I need to install the drivers for that.

I have gotten the drivers, somehow, on my desktop. But the installer file is .rpm and not .deb

I should note that this computer that I am virtually running Ubuntu on has no internet on it. I simply want to install the .rpm file that is on the desktop. I have tried following another website instructions, but none seem to work. (i think the page was called "install ANYTHING in Ubuntu") I would lauch "konsole" and type the commands I read something like "sudo alien -i /home/terence/desktop/thefile.rpm" but then it told me that it couldnt find the file(which i dont understand as I was looking right at it and I typed the name right). Soooo, i just typed "sudo alien -i" and then dragged the file onto the konsole and selected paste. That seemed to work as it told me something about --scripts? then wouldnt do anything. So I restarted konsole and put in "sudo alien -i '/home/terence/desktop/thefile.rpm' --scripts" I put in my password, but nothing happened.

---

### Post by mrmonday on 2007-04-12
I am not sure how to help, as those commands seem right, but i noticed you said 'This way I can learn linux and still keep Windows.' You know you can have both installed? when you install, you can re-partition your hard drive, so you can choose ubuntu, or windows at start up.

---

### Post by sweatyfish on 2007-04-12
I have tried that, buttttt... I have Vista. And it seems that grub messes up my Vista bootloader. After installing Ubuntu beside Vista, I cannot boot into Vista. I tried alot, but ultimately had to reinstall. 

If my commands seem right, what is supposed to happen next? Should something tell me everything installed? Should I see a .deb on the desktop?

---

### Post by johnnymac on 2007-04-12
So - here's how you do RPMs

1.  get blah.rpm
2.  sudo alien blah.rpm (will make blah.deb)
3.  sudo dpkg -i blah.deb --scripts

---

### Post by sweatyfish on 2007-04-12
"get blah.rpm"?
Wouldnt that require internet?
I dont have internet on that computer, as I have the .rpm file on the desktop.

---

### Post by johnnymac on 2007-04-12
Yeah - I'm assuming you already have the .rpm file.  So, say you have the RPM file in your home directory:

open terminal:
```

cd $HOME
sudo alien blah.rpm
sudo dpkg -i blah.deb --scripts

```

---

### Post by sweatyfish on 2007-04-12
So I will put each of those lines one at a time in the konsole, right? 

Thank you

I will try this when I get home.

WAIT! Maybe because I am using Konsole instead of Terminal?

---

