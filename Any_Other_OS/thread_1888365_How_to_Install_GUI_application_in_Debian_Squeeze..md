---
title: "How to Install GUI application in Debian Squeeze."
date: 2011-11-29
forum: Any Other OS
---

### Post by i D on 2011-11-29
Hello,
I have installed the Debian Squeeze to check out the textual based Linux. Well, I would like to ask you, whether is it possible to install the GUI based application in it and run them via terminal. I know the system will require some GUI application to create the interface but, yes can it be run hence?
I want to install the Evince application. Also would like to opt for GCC compiler.
Help me wherever i am wrong. 
Thank You.

---

### Post by BrokenKingpin on 2011-11-29
I don't think so, as the GUI applications require X Windows System. If you need GUI applications, but still a really light system just install OpenBox window manager. It uses minimal memory, and will allow you to run GUI applications. And you can still drop down to command line for most things.

---

### Post by snowpine on 2011-11-29
When you install evince, apt will install all "dependencies" including the X windows system. You will probably also want to install a desktop environment (Gnome, KDE, Xfce, etc) or windows manager (openbox, fluxbox, etc).

It is also possible to view a PDF from the console, without X, though you will not see any images, graphics, or formatting:

[http://www.linuxforums.org/forum/newbie/49048-can-i-view-pdf-files-command-line.html](http://www.linuxforums.org/forum/newbie/49048-can-i-view-pdf-files-command-line.html)
[http://www.cyberciti.biz/faq/open-a-pdf-file-under-linuxfreebsd/](http://www.cyberciti.biz/faq/open-a-pdf-file-under-linuxfreebsd/)

GCC obviously does not require X. My recommendation is to install the 'build-essential' package as that will give you GCC and more.

---

### Post by i D on 2011-12-03
Hey guys, thank you.
I installed the Debain and facing few problem. I am not able to use the normal 'apt-get install' commands. Nor the 'sudo' works. Can you give me a command line idea on how i can install envice package in debian. Also, can you please refer me to the debian shell scripts? I am having a feeling that debian has command line more limited. 
So, not able to work on it.
Thank You.

---

### Post by snowpine on 2011-12-03
> **i D said:**
> Hey guys, thank you.
I installed the Debain and facing few problem. I am not able to use the normal 'apt-get install' commands. Nor the 'sudo' works. Can you give me a command line idea on how i can install envice package in debian. Also, can you please refer me to the debian shell scripts? I am having a feeling that debian has command line more limited. 
So, not able to work on it.
Thank You.

Did you create a root password during installation? If so you can become root with "su" and the root password:

```
su
apt-get update
apt-get install evince
```

If you want to use sudo then you need to configure it first:

[http://wiki.debian.org/sudo](http://wiki.debian.org/sudo)

I highly recommend reading some basic Debian 101 documentation, as it sounds like you have many basic questions: [http://www.debian.org/doc/](http://www.debian.org/doc/)

It will actually take less time in the long run to simply read the directions rather than to constantly ask questions and then wait for a response from me. :)

---

### Post by BBQdave on 2011-12-03
> **i D said:**
> Hello,
I have installed the Debian Squeeze to check out the textual based Linux. Well, I would like to ask you, whether is it possible to install the GUI based application in it and run them via terminal. I know the system will require some GUI application to create the interface but, yes can it be run hence?
I want to install the Evince application. Also would like to opt for GCC compiler.
Help me wherever i am wrong. 
Thank You.

May I humbly suggest Undo-Redo...

Fresh install of **Debian 6** :)

I run** Debian 6** on an 8+ old notebook.  The default desktop is Gnome 2, the distro is very resource friendly.  And from the install you can choose to disable root and use SUDO (if you like).

I believe this would satisfy your GUI need, and you could easily hop into multiple terminal windows, as again, **Debian 6** is resource friendly.

Suggestion based on my use: Dell Inspiron 1100 with Celeron 4 @ 2.0GHz with 1 gig of ram.  Workload is graphic design, desktop publishing, web publishing.

---

### Post by lykwydchykyn on 2011-12-03
> **BBQdave said:**
> May I humbly suggest Undo-Redo...

Fresh install of **Debian 6** :)

I run** Debian 6** on an 8+ old notebook.  The default desktop is Gnome 2, the distro is very resource friendly.  And from the install you can choose to disable root and use SUDO (if you like).

I believe this would satisfy your GUI need, and you could easily hop into multiple terminal windows, as again, **Debian 6** is resource friendly.

Suggestion based on my use: Dell Inspiron 1100 with Celeron 4 @ 2.0GHz with 1 gig of ram.  Workload is graphic design, desktop publishing, web publishing.

Why reinstall the whole OS when you just need to install xorg and gnome???

Or just run tasksel as root and select "graphical desktop"??

---

### Post by i D on 2011-12-04
@Snowpine
Yes, I definitely created a root password. I will go through the documentation. 
Let me try the commands you suggested. Thank You.
Guys,
My necessity is not to get a GUI. I already know that i can use Desktop Enviroment, KDE, Gnome, LXDE, whatever... 
Rather my requirement is to use the text mode interface and run GUI enabled applications. I think this will consume less system resources but i think what I wish to do is like 'Growing trees without seedlings'. 
Let me try once again with the terminal whether the commands run or not. Will get back to you hence. :)

---

### Post by i D on 2011-12-04
Hey I think I will go for redownload. Can you tell me which rom should I download? 
Should i  opt for netinst Cd ?

---

### Post by i D on 2011-12-04
Hello mates,
Finally I got the error which i required and further will look improvement into my problem. 
Here's what I want to know further:
[[IMG]http://img847.imageshack.us/img847/1917/deb1.png[/IMG]](http://imageshack.us/photo/my-images/847/deb1.png/)
Where is the Documentation file Located in the System?
Also, is there any specific file in which the system documentation is located?
Thank You.

---

### Post by tartalo on 2011-12-04
You are trying to run evince as root, don't do that. To go back to normal user:

```
exit
```

The documents are where it says /usr/share/doc/... anyway it's talking about boring legal information, you might be more interested in the man command, example:

```
man man
```

EDIT: You might want to have a look here too:
[http://linuxcommand.org](http://linuxcommand.org)

---

### Post by i D on 2011-12-04
> You are trying to run evince as root, don't do that. To go back to normal user:
Thanks, but Since i am not having any Desktop environment i won't be able to run Evince.
> man man
Great, thanks for introducing me to this command. And i am taking some lessons at the linuxcommand.org. Great site. 
thank you mate.

---

### Post by lykwydchykyn on 2011-12-04
I'm not clear on your objective here.  Is it more important to use evince or to stay on a purely CLI interface?

If you can get the frambebuffer working, there are programs that will let you view pdf's in the framebuffer without X11.  Otherwise, you just need to install X and a window manager/Desktop environment of some sort.

---

### Post by i D on 2011-12-05
> I'm not clear on your objective here.  Is it more important to use evince or to stay on a purely CLI interface?My motto was to run the GUI based applications like gedit, evince etc... The necessity was to run the Linux/Debian on really low speed machines... 
CLI interface assured me a great portability of doing tasks yet, GUI is necessity to deal with the Real life tasks. I know a lot of porting has been done on the portable gadgets supporting ARM infrastructure. And I gave a thought on running it on the CLI interface that will consume low power and low memory resources.

---

### Post by lykwydchykyn on 2011-12-05
> **i D said:**
> My motto was to run the GUI based applications like gedit, evince etc... The necessity was to run the Linux/Debian on really low speed machines... 
CLI interface assured me a great portability of doing tasks yet, GUI is necessity to deal with the Real life tasks. I know a lot of porting has been done on the portable gadgets supporting ARM infrastructure. And I gave a thought on running it on the CLI interface that will consume low power and low memory resources.

If it's just a question of keeping the resource usage low, you should look into using a low-powered X server like Xvesa or Xfbdev instead of a full Xorg.  Check out some uber-light distros like tinycore or slitaz to see what they're using (Xvesa, I think).

Alternately, like I mentioned before, there's the framebuffer.  Not a lot of software supports the framebuffer, but you can do a lot more with it than you might think initially.

---

