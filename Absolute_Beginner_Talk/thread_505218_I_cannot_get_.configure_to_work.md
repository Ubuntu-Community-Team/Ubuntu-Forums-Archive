---
title: "I cannot get ./configure to work"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Matteran on 2007-07-20
Hi, I've looked through all the threads that include ./configure problems, and I'm getting probably as frustrated with this problem as I have with any computer problem ever.

Okay, I'm trying to install "Rise and Shine" (it's an alarm clock) that I downloaded the .tar.gz from Sourceforge.net

I extracted to the desktop, I've "cd"ed to every different folder in the extracted folder and have tried to run ./configure. In every folder I get "bash: ./configure: No such file or directory"

Okay, so the other threads say that not everything has a .configure file, which I haven't been able to find, there are .config files though. So I'm not sure about that... so, anyway, if ./configure doesn't work, just skip straight to "make" I've gone through and tried that in every folder as well, and get "make: *** No targets specified and no makefile found.  Stop." Okay, so I've gone out on whims and tried "sudo make install" everywhere, and get nothing...

I've never been able to get this to work on any program i've tried to compile. I'm really frustrated. I downloaded all of the dependancies listed in the "install.txt" and I have build-essentials.

Please help!! Thanks

I know that I could just boot into Windows and run that program and be fine, but I'm trying as hard as possible to stay away from Windows... I have XMMS alarm installed to, but I really need to wake up at a certain time tomorrow and I don't trust XMMS alarm yet, because i've never used it. And as luck would have it, my cell phone was stolen, so my regular alarm clock isn't available.

---

### Post by JesterDev on 2007-07-20
I´m not familiar with that particular program myself however there should be a configure or similar (make) file in the root of the directory where you extracted it to. The problem I think your having is that the file is not set as executable. As you no doubt have seen Linux is different in the way it handles files.  In order to make the file executable you will have to use chmod like so:

```

chmod a+x nameOfFile

```

Where nameOfFile is you would replace it with the name of the file i.e. <i>.configure</i>

I suggest reading this: [http://linuxreviews.org/beginner/]("http://linuxreviews.org/beginner/")

And reading a little bit about chmod here: [chmod man (manual)]("http://linuxreviews.org/man/chmod/")

Just so you know the above command will make the file executable to every user who uses your computer. 

Hope this helps!
JesterDev

---

