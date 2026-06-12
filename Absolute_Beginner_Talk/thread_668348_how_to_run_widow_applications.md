---
title: "how to run widow applications?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by faust3x on 2008-01-15
I wanna run MSN messenger and IMVU

I installed ubuntu as my only OS, and I need something so I can install those programs.

---

### Post by Shinbu-Otaku on 2008-01-15
there is a program called aMSN that you can install, its basically a copy of it so you should already find it quite familiar

IMVU...im not sure what that is lol, what does the program do?

---

### Post by SunnyRabbiera on 2008-01-15
well there is wine, but I will warn you it might not work for everything.

---

### Post by faust3x on 2008-01-15
where do I get this wine?

---

### Post by SunnyRabbiera on 2008-01-15
read here:
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

hope you are not too afraid of the terminal.

---

### Post by faust3x on 2008-01-15
I went to get wine and got it how do I install it?

---

### Post by rowanparker on 2008-01-15
Sounds like someone jumped in at the deep end a little too fast.

There are many programs that do what you require (and more because their open) but they will be different. You can *try* and emulate Windows programs using Wine but it isn't the most stable of programs. Although the identical program is unlikely to work in Linux (e.g. Photoshop) but there are alternatives (Gimp and Pixel in this case).

---

### Post by rowanparker on 2008-01-15
> **faust3x said:**
> I went to get wine and got it how do I install it?
You tried searching?

---

### Post by Shinbu-Otaku on 2008-01-15
if you click the programs button on the top-left of the desktop, then choose the 'add/remove programs' option at the bottom, you can search for both Wine and aMSN and it will install it all for you.

---

### Post by Hallvor on 2008-01-15
> **faust3x said:**
> I wanna run MSN messenger and IMVU

I installed ubuntu as my only OS, and I need something so I can install those programs.

If you need windows applications that bad, you are probably better off using Windows. But on the other hand, there are linux equivalents for almost anything out there. 

If you want msn for linux, go for amsn. It looks just like the real thing, but without the adware!

```
sudo apt-get install amsn
```

Here is a list of linux equivalents:
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by SunnyRabbiera on 2008-01-15
okay more detail then:
go into your terminal by going to applications, then to accessories then to "terminal"
once that is open put this in:
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

after that is finished then put this in:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

after that is done go to system, then to administration then to synaptic package manager.
type in your password then once synaptic is loaded search for "wine"
for farther information use this guide:
[guide to synaptic]("http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic")

---

### Post by faust3x on 2008-01-15
ok, I dunno how to run wine and when I download IMVU from imvu.com it says it's for window based pcs, is there a way to emulate windows to run the game?

---

### Post by SunnyRabbiera on 2008-01-15
you may not be able to use imvu, remember most applications are windows only.
as for getting wine to work, what else do you need to know?
if you were able to install it I can teach you how to configure it

---

### Post by faust3x on 2008-01-15
> **SunnyRabbiera said:**
> okay more detail then:
go into your terminal by going to applications, then to accessories then to "terminal"
once that is open put this in:
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

after that is finished then put this in:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

after that is done go to system, then to administration then to synaptic package manager.
type in your password then once synaptic is loaded search for "wine"
for farther information use this guide:
[guide to synaptic]("http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic")

The second one to put in says 

Resolving wine.budgetdedicated.com... 81.171.111.184, 88.159.193.22
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:45:42 ERROR 404: Not Found.

---

### Post by SunnyRabbiera on 2008-01-15
hmm, the server might be down or having issues...
keep trying.
I am hoping you can get what i told you running.

---

