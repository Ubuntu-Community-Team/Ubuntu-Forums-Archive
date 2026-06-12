---
title: "How does ubuntu work?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Titi on 2007-01-18
hi all
i've been using ubuntu for over a year now. i'm still using windows, but i'm planning to completely migrate to ubuntu after my exams.
i'm studying civil engineering (electronics) and i'm in my third year now. so i know the very basic principles of how computers work. how chips and stuff are built etc...
but i'd like to know how linux (in particular ubuntu) works on a pc. how it differs from windows, what the exact differences are between distributions. i've read that ubuntu exists out of layers. for example the X-server is such a layer (correct me if i'm wrong). but i've failed to find a satisfying explanation of how these layers interact etc...
for example, you can restart gnome without restarting the computer. or your x-server may fail, but "linux is still running", just without the gui. 
could someone explain this to me, or refer to a decent explanation?
thanks in advance

---

### Post by deadgobby on 2007-01-18
Linux is many many many of things. I sound like Carl Sagan there. Any ways you want to know how Linux works and here is a link to that question.
[http://www.comptechdoc.org/os/linux/howlinuxworks/](http://www.comptechdoc.org/os/linux/howlinuxworks/)
 Linux in short is based off of Unix. Unix has been around since Bill Gates was still a seed. You ask a very vast and good question. 
Good luck on your study.
Gobby

---

### Post by Sqwishy on 2007-01-18
> **Titi said:**
> hi all
for example, you can restart gnome without restarting the computer. or your x-server may fail, but "linux is still running", just without the gui. 
 Yes, you have x and then it runs some sort of enviroment, wether it be kde or gnome or enlightenment. These are 'layers' in a sense. if X fails you have a terminal you can try to fix it with, lots of time you might edit you're x11 config file and it wont work, like when i was trying to get my mx revolution mouse i kept on typeing in the wrong stuff so x never worked, but instead of giving a windows-like blue screen of death, X crashed and i can fix my problems through the terminal.

---

### Post by jd65pl on 2007-01-18
If you want to learn more about linux you could try gentoo or if you really want a ground up approach try linux from scratch.

---

### Post by deadgobby on 2007-01-18
> **jd65pl said:**
> If you want to learn more about linux you could try gentoo or if you really want a ground up approach try linux from scratch.
That would be the challenge for any one. :)

---

### Post by jd65pl on 2007-01-18
Linux from scratch is a project I have started it but can't dedicate too much time to it due to revising for end of semester exams, other projects and training to my 5 peaks 3 days mountain climb challenge

shameless... sponsor me its for charity link [http://jamie.dumbill.googlepages.com/fivepeaks](http://jamie.dumbill.googlepages.com/fivepeaks)

Linux from scratch
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by irish_flu on 2007-01-18
Consider Linux the "Kernel", sort of like the Windows NT kernel which powers XP.  Consider X and Gnome (or KDE, etc) to be similar to the "Windows Explorer" environment, which runs your desktop.

Windows, although it's less common to do, doesn't have to run the GUI either.  You can still make a windows box boot to "Command Prompt Only".

One big difference, from my point of view (I'm no expert, FYI) is that Windows stores many settings in the "Registry", while Linux stores stuff like that in configuration files.

There are many similarities, though.  They both have a kernel to talk to the hardware, they both have an API (applications programming interface) built on top of that, and they both have a GUI environment built on top of that in which to easily access your programs and to offer a common interface for them.

---

### Post by jd65pl on 2007-01-19
Theres alot less functionality from windows prompt!

---

### Post by Titi on 2007-01-20
thanks for the info. i'll check out the website.

---

### Post by confused57 on 2007-01-20
Might want to read this also:
[http://www.faqs.org/docs/Linux-HOWTO/From-PowerUp-To-Bash-Prompt-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/From-PowerUp-To-Bash-Prompt-HOWTO.html)

You might want to download a copy of the "Ubuntu Book":
[http://www.ubuntuforums.org/showthread.php?t=339531&highlight=Ubuntu+Book](http://www.ubuntuforums.org/showthread.php?t=339531&highlight=Ubuntu+Book)

---

### Post by old_geekster on 2007-01-20
> **deadgobby said:**
> Linux is many many many of things. I sound like Carl Sagan there. Any ways you want to know how Linux works and here is a link to that question.
[http://www.comptechdoc.org/os/linux/howlinuxworks/](http://www.comptechdoc.org/os/linux/howlinuxworks/)
 Linux in short is based off of Unix. Unix has been around since Bill Gates was still a seed. You ask a very vast and good question. 
Good luck on your study.
Gobby
Since I was around when Bill was a seed, I will give you a history lesson.  ( I am an old_geekster, ya know!)  I lived in the Seattle area for years.  There are many urban legends about Bill and Paul Allen, but this one is true.  I read an article about the Unix developer in a business magazine in the early eighties.

Bill built M$ DOS around the "Unix" kearnel.  He actually screwed the developer of Unix out of his fair share of the profits.  Bill went to him with a proposal to pay him so much ($15) for every Unix system that sold with a new thing called a PC.  However, production was going too slowly, so Bill talked him into taking a lump sum instead.  The figure that I saw was about $30,000.  The guy was an idea man (his own description of himself), not a businessman.  This is obvious.  In fact, he went to college to get a MBA, so the next time that he had a good idea, he would know how to make money on it.

So you see, Bill simply didn't develop Unix further, for whatever reason, but he certainly knew about it.

Your comment made me think of this story.  Sorry to boot-leg the thread, but I thought this may be of interest to my Linux friends.

---

