---
title: "How can I make waste work?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by NorthernPaladin on 2007-02-02
Ok, I searched the forums and found this [http://www.ubuntuforums.org/showthread.php?t=22244](http://www.ubuntuforums.org/showthread.php?t=22244)
The problem is, I don`t understand what I should do, I`m total n00b to linux. Could somebody give step-by-step directions to me, every command and so on?

---

### Post by CroEragon on 2007-02-02
You maybe wondering why it takes 59 minutes to anybody answer your post. Im delighted you Use ubuntu, but you have wrong approach with this. We volunteer here to help people and we will help almost always. But we provide help, not work for you. When you run into problems you do research, you use Google, build in search, try to find problem by your self and provide informations if you are asking for help. You do  not do your work for you, nobody pays us. We will point you into right direction and HELP.
So next time be absolute sure you cant do it yourself, do research and learn about things and possible problems you can encounter. I installed Ubuntu on main family computer that musn't be out of service longer than two hours. So I  spent 4 months on live CD, researching, reading about how my hardware will work with Ubuntu, reading several guides that are talking about same thing, and going thought hills of informations trying to avoid common errors and problem. After then i installed Ubuntu with basic knowledge of it and knowing how to do things and solve problems even before i encounter them. And it went smoothly. with 45 minutes of downtime.
You see what im talking about???

---

### Post by NorthernPaladin on 2007-02-02
I`m sorry if I sounded demanding or something like that. The reason for that is that I haven`t slept in couple days because I`ve tried to make things work, but haven had succes. So I`m little p*****d of, and I tried to google it, searched the forum for it, but I still can`t get it working. I just thought that I misunderstood something somewhere and thats why I asked detailed help. Sorry if it went the wrong way. The reason why I haven`t studied linux as much as I should have is that I don`t have much free time, have to do school work and  go to therapy for hour or two every day.
The problem in here is this: I downloaded the zip file (linux server/client) from [http://sourceforge.net/project/showfiles.php?group_id=82356](http://sourceforge.net/project/showfiles.php?group_id=82356), then I started to read the instructions in the thread that I put link, but I just don`t understand.

---

### Post by psyne on 2007-02-02
Seems pretty straight forward

Download waste-linux-1.5-beta-3.zip from here:

[http://umn.dl.sourceforge.net/sourceforge/waste/waste-linux-1.5-beta-3.zip](http://umn.dl.sourceforge.net/sourceforge/waste/waste-linux-1.5-beta-3.zip)

Extract the zip file

Add the multiverse repositories

```
echo deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse | sudo tee -a /etc/apt/sources.list
```

Update your Source

```
sudo apt-get update
```

Install libwxgtk2.5.3

```
sudo apt-get install libwxgtk2.5.3
```

After it is installed

```
./waste
```

Looking at the last time this was updated and the fact that the linux version comes with Windows documentation it does not seem very well supported. Have you considered an alternative such as nicotine which has a HOWTO for installation.

[http://ubuntuforums.org/showthread.php?t=12656](http://ubuntuforums.org/showthread.php?t=12656)

---

### Post by NorthernPaladin on 2007-02-02
The reason why I need waste is that my friends already have it up and running(and they have windows, would nicotine work for them?), so I need to just join.
When I typed "sudo apt-get update"  the last line said  "W: Some index files failed to download, they have been ignored, or old ones used instead." Is that a problem?
When I type ./waste it says Permission denied.What should I do?

---

### Post by NorthernPaladin on 2007-02-09
bump

---

### Post by Perfect Storm on 2007-02-09
I don't know the application but try with
sudo waste

or 

sudo sh waste

and see what comes up.

---

### Post by NorthernPaladin on 2007-02-09
northernpaladin@northernpaladin:~/Desktop/waste$ sudo sh waste
Password:
waste: 1: Syntax error: word unexpected (expecting ")")
northernpaladin@northernpaladin:~/Desktop/waste$ sudo waste
sudo: waste: command not found
northernpaladin@northernpaladin:~/Desktop/waste$

---

### Post by MrKlean on 2007-02-09
NP..I'm a newbie to, but I try and help ppl instead of taking 2 paragraphs to tell you why I won't!  I would make sure you're in the directory where the program is...then try typing the suggestions above..or try ./waste.  You'll find MOST ppl will help here,  we were ALL new at one time and sometimes finding the solution... searching...leaves you with more questions.  I've done that...and after the solution was shown to me... a light came on....and made it easier the next time.  Sooooooooo...ask away.... and those that can help will...those that can't will chide you about asking LOL!!

---

