---
title: "About screen resolution"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Xanrov on 2008-03-08
First I'm new to Ubuntu and I'm surprised that the resolution of my ACER P203W screen, which was a nice 1600x1050 under Windows, cannot, under Ubuntu, be better than some 1280x1050.
Secondly I saw numerous posts on the subject, one of them saying that xorg-config should be edited. Well, I opened the file and nowhere I saw a list of resolutons where the "1600x1050" could be added.
But I saw much worse: the file itself appears to a newbie like me enticing people to run the command :
                  sudo dpkg -reconfigure -phigh xserver-xorg

Now this command should be added to the list of "Malware Threads" ! As soon as I had run it,  my xorg-config was gone and I was left with an untermensch resolution of 640x480. Of course reinstallation of Ubuntu took care of that. That was a good lesson acquired by some loss of time. (like all lessons)
Now, seriously, what exactly should I do to get this 1600x1050 resolution . I have some experience of the terminal and the command line but none of Unix arcane commands (except the most current ones)
Thanks in advance for any help

---

### Post by uberlube on 2008-03-08
First of all have you installed your graphic drivers?

---

### Post by darkworld on 2008-03-08
im no expert either but I think you can add the resolution to the resolutions line in xconfig.

---

### Post by szymon_g on 2008-03-08
wtf is wrong with sudo dpkg-reconfigure xserver-xorg :? it always worked on my laptop....

---

### Post by darkworld on 2008-03-08
does this help? I had cause to read it recently.[https://answers.launchpad.net/ubuntu/+question/8573]("https://answers.launchpad.net/ubuntu/+question/8573")

---

### Post by Xanrov on 2008-03-08
Well , thanks to all who responded . I just looked (respectfully) at xorg.conf ( after reinstallation of Ubuntu 7.10) and I saw my monitor name and a lot of resolutions ( including 1600x1050) but, curiously, they don't show on the "Screen resolution prefs" dialog box.

---

### Post by Xanrov on 2008-03-08
Well , as said Uberlube, it was a question of drivers and xorg.conf was faultless. I first tried to download the envy package which provides drivers for NVDIA ( my card) but I failed miserably to download anything, although following Alberto Milone's instructions to the letter. Downloading a package is something I have to learn.
Finally I found , almost by chance, an ATI driver asleep in the System -> Administration -> Restricted Manager menu, I activated it, rebooted , et voilà !
I'm  now happy with 1600x1050 resolution. 
Morality : Search and you will find.

---

### Post by halitech on 2008-03-08
if you have an ATI driver in the restricted manager, are you sure you have an Nvidia card? Normally that should only show drivers for hardware it actually sees in the machine.

---

