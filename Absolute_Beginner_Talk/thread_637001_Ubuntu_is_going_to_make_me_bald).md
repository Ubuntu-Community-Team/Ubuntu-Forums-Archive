---
title: "Ubuntu is going to make me bald:)"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by v.alari on 2007-12-10
According the helpful similar threads bit, Im not the only one lol. Okay so I installed Ubuntu recently and nothing worked of course, well sure it ran and all but Im not satisfied with that, 800x600 screen res was pissing me off, the no nvidia drivers, then about 4 more things. Since google and I go way back we worked most of it out. Right now though I am about ready to do something irrational for frustration. 

I cannot get Abiword, Adblock. Adept Manager, Akregator, Amarok....,....XFE 4 Menu Editor, XFE 4 Print Dialog, XFE 4 Print Manager to install. Everything save idk probablt 10% of the list says it cannot install on my hardware with a response similar to this:
              "Canonical Ltd. provides technical support and security updates for (program).
A(Program) cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

Also I input the wrong information into Pidgin for MSN Messenger and it couldnt load my account. Ok, fine, but it would be nice if Pidgin would ACTUALLY open to allow me to change the error it tells me is wrong, Instead it was kind enough to inform me of the error, tell me I needed to change it, tell me how, then close and refuse to open with repeated attempts and reboots so I could idk maybe fix it.

That all said Im actually enjoying myself, Its fun to learn something new and I havent been seriously challenged by a computer OS since C64 when I was 5 and just learning for the first time. I might be making this harder on myself than I need to, Im sure Ill never actually USE Akregator for instance but the skills are interchangable so it would be nice to know how to install it. Thanks

---

### Post by LaRoza on 2007-12-10
What are your system specs?

I have no problem with resolution, and Pidgin works perfectly.

---

### Post by v.alari on 2007-12-10
OOOOOHHH yes, and as LaRoza was kind enough to mention in his Thanks post, how do I get Wine loaded, I have loaded it into my synaptics list but the libaudio2 and binmf...nv figured that out myselfby accident lol

---

### Post by v.alari on 2007-12-10
nah I got my res working, I think I glitched out pidgin somehow because when it tries to load it cant login to MSN and quit without so much as showing me anything but a error window(no main window). 

AMD64 ~2.3ish (Ubuntu 7.10 32-bit)
DVD writer
CD writer
Flash card drives
Floppy drive (cause I had one laying around so I put it in)
6100k8ma winfast mobo
onboard everything for now
1.5GB Ram

---

### Post by jaybombalous on 2007-12-10
```
uname -a
```

paste the results here.

---

### Post by v.alari on 2007-12-10
Linux (my computer name) 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by v.alari on 2007-12-10
*bump*

---

### Post by jaybombalous on 2007-12-10
are u sure u have the right repository selected?

it sounds like u have 64 bit software and trying to install it on a 32 bit platform. But I have never seen this so I don;t know what to tell you.

---

### Post by v.alari on 2007-12-10
i am pretty sure I downloaded the 32 bit version but if I am wrong I dont know how to select a different repository or check which is selected. I went to software sources but couldnt find mention anywhere of either 64 or 32 but the top 3 options were checked and so was source code.

---

### Post by v.alari on 2007-12-10
OK so on my new hairstyle courtesy of Ubuntu, all the programs just started working for download, the error message disappeared and they started loading. I didnt do anything so yay but wth??? lol I must have done something wrong lol. thanks for the help though. Pidgin stilldoesnt work but ill just reload it from scratch. Thanks Jay

---

### Post by skrribble on 2007-12-10
if you have not already done so, i would first go to system>admin>software sources and make sure all of the repos are selected (main, universe, multiverse and restricted)

then go back and try again to install all of your programs with whatever method you would like (add/remove under applications, synaptic, or "sudo apt-get install (package) in the terminal).

as for pidgin not working correctly, i would probably just trying uninstalling it and then reinstalling it, using:
```
sudo apt-get remove pidgin

```then ```
sudo apt-get install pidgin
```
in the terminal

---

