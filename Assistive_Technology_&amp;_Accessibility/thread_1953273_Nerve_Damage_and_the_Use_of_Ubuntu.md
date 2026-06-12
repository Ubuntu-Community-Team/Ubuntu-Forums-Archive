---
title: "Nerve Damage and the Use of Ubuntu"
date: 2012-04-06
forum: Assistive Technology &amp; Accessibility
---

### Post by demarshall on 2012-04-06
Hello:

I have been using Ubuntu for at least a few years prior to which I used other distros. I would not want to have to go back to using Windoze but from what I can tell speech recognition is not at a usable stage for those who have limited use of their hands and finders for typing. Am  I wrong? Can somebody direct me to a pp or apps that I can use for this? After typing just this much my fingers are hurting. Back in the '90s I believe that Dragon was available for Linux.

Thank you very much for your attention.

---

### Post by 23dornot23d on 2012-04-06
From what I can see voxforge was set up for this and to help people could leave
voice recordings .... but when I look in the downloads the latest seem around 2 years ago ....

[http://www.repository.voxforge1.org/downloads/Nightly_Builds/](http://www.repository.voxforge1.org/downloads/Nightly_Builds/)

[http://en.wikipedia.org/wiki/Speech_recognition_in_Linux#Current_development_status](http://en.wikipedia.org/wiki/Speech_recognition_in_Linux#Current_development_status)

______________________________________

[B]There is a video here for Julius
[/B]
[http://www.youtube.com/watch?v=s1srNOk2ISI](http://www.youtube.com/watch?v=s1srNOk2ISI)


**This is the link to there site ,,,**

[http://julius.sourceforge.jp/en_index.php](http://julius.sourceforge.jp/en_index.php)

---

### Post by lovinglinux on 2012-04-06
Another thing that might help is the OnBoard virtual keyboard, which is installed by default. It has a feature that allows you to type without clicking the mouse, just hovering it. Additionally, it has interesting configuration options, that allows you to use it without obstructing your view.

Check this article:

[http://iloveubuntu.net/ubuntu-1110s-default-virtual-keyboard-onboard-096-released-exciting-new-features](http://iloveubuntu.net/ubuntu-1110s-default-virtual-keyboard-onboard-096-released-exciting-new-features)

---

### Post by demarshall on 2012-04-06
Thanks for suggesting Voxforge and Julius, 23dornot23d. Those are the companies whose programs that I checked and found that there had been some work done on them but not enough to make them to the the point of Dragon Naturally Spoeaking. BTW IBM had a program that they called Via Voice and I'm 99% sure that they had a version for Linux.

David



> **23dornot23d said:**
> From what I can see voxforge was set up for this and to help people could leave
voice recordings .... but when I look in the downloads the latest seem around 2 years ago ....

[http://www.repository.voxforge1.org/downloads/Nightly_Builds/](http://www.repository.voxforge1.org/downloads/Nightly_Builds/)

[http://en.wikipedia.org/wiki/Speech_recognition_in_Linux#Current_development_status](http://en.wikipedia.org/wiki/Speech_recognition_in_Linux#Current_development_status)

______________________________________

[B]There is a video here for Julius
[/B]
[http://www.youtube.com/watch?v=s1srNOk2ISI](http://www.youtube.com/watch?v=s1srNOk2ISI)


**This is the link to there site ,,,**

[http://julius.sourceforge.jp/en_index.php](http://julius.sourceforge.jp/en_index.php)

---

### Post by demarshall on 2012-04-06
Thanks lovinglinux. My hand hurts to use the mouse as well. I guess I should have said that. 

I would hate to go back to using Windoze, especially for email. I think that is the least secure area of all M$ OSs.

David


> **lovinglinux said:**
> Another thing that might help is the OnBoard virtual keyboard, which is installed by default. It has a feature that allows you to type without clicking the mouse, just hovering it. Additionally, it has interesting configuration options, that allows you to use it without obstructing your view.

Check this article:

[http://iloveubuntu.net/ubuntu-1110s-default-virtual-keyboard-onboard-096-released-exciting-new-features](http://iloveubuntu.net/ubuntu-1110s-default-virtual-keyboard-onboard-096-released-exciting-new-features)

---

### Post by QIII on 2012-04-06
I have heard that it is possible to use VirtuallySpeaking in a Windows virtual machine in Virtualbox and transfer text out to a Linux host.  More detail I don't know.

BTW ...  I broke my neck in the Army about 20 years ago.  Didn't paralyze me, but it did a lot of damage to my brachial nerves.  Hands shake like h....  I'm a software developer, so it's a bit of a pain.  Fortunately, I'm not just a code monkey these days, so I can relax a bit.

Best of luck to you from one who understands.

---

### Post by demarshall on 2012-04-07
Thank you very much, QIII! I'll investigate that when I can. I've discovered mostly today that a prescription cream helps stave off the painful numbness so that I can accomplish a little bit without too much pain.

---

### Post by lovinglinux on 2012-04-08
Just received this and thought it might help.

[http://dot.kde.org/2012/04/08/simon-speech-recognition-project-moves-kde](http://dot.kde.org/2012/04/08/simon-speech-recognition-project-moves-kde)

---

### Post by kd7swh on 2012-04-08
History:
____

Dragon has a long history. First it was developed by Dragon Systems, then it was purchased by Lernout & Hauspie.

Lernout & Hauspie did develop a Linux SDK but they went out of business and sold their software to ScanSoft and then ScanSoft was later purchased by Nuance.

____

Basically, there are some older Dragon engine development tools but no real application for Linux using the Dragon engine at this time.

People have reported success running older versions of Dragon NaturallySpeaking in wine but this would not be my suggestion.

If you are looking for a native solution, I would suggest looking at some work out of Carnegie Mellon University (CMU).

The CMU guys are still developing Sphinx, an open source project for speech recognition.

Sphinx is the only open project of it's kind, that I'm aware of. It is in active development and is making strides in catching up with Dragon.


Other tools such as Dasher and GOK maybe helpful for entering text.
I would encourage you to look over the GNOME accessibility web page to get familiar with some of the other tools that are available: 

[http://projects.gnome.org/accessibility/solutions.html](http://projects.gnome.org/accessibility/solutions.html)

---

### Post by ridetheteapot on 2012-04-09
hey, I just want to add a couple of things here, but I am no expert on speech to text software.

There is another open source project called julius that is similar to sphinx. Currently (or recently at least) the OLPC project has been using julius to develop a voice note-taking application for their charity laptops.

The sphinx engine was used in a project called Gnome Voice Control (which if you google the page, they have a video demonstration of it in use). How well it integrates with gnome 3 beats me though, and its looks like the project has been stale for about a year.

[http://en.wikipedia.org/wiki/Speech_recognition_in_Linux](http://en.wikipedia.org/wiki/Speech_recognition_in_Linux) a list of more tools as well as the general state of things.

I think though that in order to get a functional system your going to just want to use dragon in wine. The last version I saw reported to work with wine is DNS9 - but you can still buy it, and at a huge discount. Which is great because it's not exactly cheap software.

If you do go that route, you will want to check out some guides on howto set it up. You probably should also check out a project called platypus [http://thenerdshow.com/platypus.html](http://thenerdshow.com/platypus.html). It will integrate dragon with your desktop.


Edit___
by the way, above there is the simonspeaks link, that project is also based around julius.

---

### Post by demarshall on 2012-04-16
Thank you so much for everybody's input. I'll check these things out. I knew about most of them before and for some reason not very much work is being done on them. How are we ever going to get to computers like the ones on Star Trek where you can talk to them and do everything through voice command?

---

### Post by jonathonblake on 2012-04-30
> **demarshall said:**
> How are we ever going to get to computers like the ones on Star Trek where you can talk to them and do everything through voice command?

Back in 1999 I saw a demo that appeared to be capable of doing everything that HAL could do, with two exceptions:
[LIST]
[*]Lip Read;
[*]Go "crazy";
[/LIST]

That was the first and last time I ever saw a mention of that demo.

IBM did have a voice recognition/speech to text program for Linux. When the Windows rights were sold, either IBM agreed to not distribute a *Nix program, or else it sold the *Nix rights with the Windows rights. (I've seen claims for both propositions.)

The big stumbling block for everybody --- it literally has put the field 20+ years behind --- is patents.

A more solvable obstacle is the amount of disk space to store the data required for the speech to text transformation. What is needed is something that can hold at least as much data as a Backblaze Storage Pod, and is as inexpensively as one, but more reliable for daily data transfer of the entire pod.


jonathon

---

### Post by Glyncsymn on 2012-06-04
i have heard about CVD crystal vapour deposition tech ,which is used for fabrication of chips,wires,and all electronic device. I want to know how these tech. can be used to improve diamond quality i.e. how to remove nitrogen vacancy from diamond?

---

