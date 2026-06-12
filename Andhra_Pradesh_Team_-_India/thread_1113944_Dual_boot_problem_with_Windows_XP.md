---
title: "Dual boot problem with Windows XP"
date: 2009-04-02
forum: Andhra Pradesh Team - India
---

### Post by abhinandan321 on 2009-04-02
Hii guyz..
I am facing some problem, every time i boot ubuntu ultimate after woking on windows, the system doesn't work properly and hangs every time after it reaches the welcome screen and does not mount the disks.It takes tens of reboots to recover from this problem.My windows system has vorus in it due to which i have to open my disks with a right click explore in wondows, this may b the reason ..please help.

---

### Post by thesandeep on 2009-04-06
Hi Abhinandan,
I have got few questions to you before giving any suggestion to your problem.

Do you have any Internet connection to your machine?
Do you have any Anti virus installed in your XP?
- If yes is it up to date in virus definitions?

Did you update ubuntu regularly (all the patches/updates etc)? Generally it automatically prompts you to install, you have to allow it to install them.


If you are using windows, you have to got an anti virus software which is up to update -- This is blind fold rule 1

If you want to use ubuntu to its extreme, you need to have an Internet connection which can be accessed though ubuntu :) (Some Dial-up connections are not recognized by ubuntu due to lack of h/w support i.e. modem support to Linux) -- This is blind fold rule 2


For disabling autorun for drives in windows you can erase the autorun.inf file by below steps.

1. Start your XP in safe mode/safe mode with command prompt (F8 or F10 while booting windows)
2. Go to C:\ in the command prompt
3. Try giving the below commands one after another
```
attrib autorun.inf -S -H -R 
```
```
erase autorun.inf
```
```
echo '' > autorun.inf
```
```
attrib autorun.inf +S +H +R 
```

4. Repeat the step 2 and 3 for other hard disk drives as well to disable autorun. 

PS: You can straight away delete the autorun.inf file in safe mode, but viruses generally have tendency to recreate them.

I am not saying this is the only resolution to your problem, but this is one of the way in which I have solved this problem once. :)

C ya.

Guys, Please correct me if anywhere I mentioned anything wrongly.

---

### Post by aiser on 2009-12-01
;)

---

