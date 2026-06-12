---
title: "[SOLVED] what is &amp;quot;wine&amp;quot; and how do I use it?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-11-28
I have spent enough time on these forums to have gathered that Wine is some kind of software that allows certain .exe files to run in linux. I think. Actually I have no idea if that is right but I am working from that assumption.

Anyway, there are only a few programs that I really need to run that I can't find replacements for in linux. The first is a program that runs my EVDO wireless card (OK that one I bet can be worked around using some complicated tweaks but remember, I am an "Absolute Beginner") and the other is Microsoft Streets and Trips. I need to know if Wine can come to my rescue and if so, how do I implement it?

---

### Post by skyjacker on 2007-11-28
> **boriquajake said:**
> I have spent enough time on these forums to have gathered that Wine is some kind of software that allows certain .exe files to run in linux. I think. Actually I have no idea if that is right but I am working from assumption.

Anyway, there are only a few programs that I really need to run that I can't find replacements for in linux. The first is a program that runs my EVDO wireless card (OK that one I bet can be worked around using some complicated tweaks but remember, I am an "Absolute Beginner") and the other is Microsoft Streets and Trips. I need to know if Wine can come to my rescue and if so, how do I implement it?Most of what you need to know about Wine can be found here:
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by philinux on 2007-11-28
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

I found that installing wine from synaptic ensures full compatibility with the current ubuntu version.

---

### Post by atomkarinca on 2007-11-28
You can find [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3962") about how other people experienced Streets and Trips via wine. You can install wine through Add/Remove... and [Wine Application Database]("http://appdb.winehq.org") is a very helpful site for wine users. You can search for the program you want to use beforehand.

---

### Post by boriquajake on 2007-11-28
> **skyjacker said:**
> Most of what you need to know about Wine can be found here:
[http://www.winehq.org/](http://www.winehq.org/)


Thanks, I was able to follow their instructions and install Wine from the terminal but I am still not sure how to use it. I will go play around some more. 

Thanks again for steering me in the right directions.

---

### Post by Phrellex on 2007-11-28
I am not sure that you can emulate computer drivers on wine or am I mistaking? Wouldn't it be better to find a Linux version counterpart. Also wine can be installed via the website Wine HQ, here is a link to the version downloads,  [http://www.winehq.org/site/download]("http://www.winehq.org/site/download"). It will require you to add wine to your sources by the instructions. Making it available to auto update and to be found in the repositories.

---

### Post by boriquajake on 2007-11-28
> **Phrellex said:**
> I am not sure that you can emulate computer drivers on wine or am I mistaking? Wouldn't it be better to find a Linux version counterpart..

I imagine that you are right. How do I do that? I googled the drivers looking for linux versions and I have entered the make and model information on these forums but I am stuck. Any suggestions?

---

### Post by Phrellex on 2007-11-28
Yeh, when I just now searched it nothing was really displayed. You sure Ubuntu does not have any generic workable drivers currently active?

---

### Post by staticvoid on 2007-11-28
> **boriquajake said:**
> Thanks, I was able to follow their instructions and install Wine from the terminal but I am still not sure how to use it. I will go play around some more. 

Thanks again for steering me in the right directions.

If you have the program you want (taken from C:/Program Files/*program directory*) then you just right click on the main .exe file and choose "Open with Wine", or in the terminal run 
```
wine
```
and then the name of the program, for example:
```
wine photoshop.exe
```
you may have to input your serial numbers again if you just copy a directory.

Best of luck!!

sv :popcorn:

---

### Post by philinux on 2007-11-28
If you download a setup type .exe file to your desktop just double clicking it will fire up the wine installer.

---

### Post by staticvoid on 2007-11-28
sometimes..

---

### Post by boriquajake on 2007-11-28
Holy crap, that is awesome.

OK, so when you say > (taken from C:/Program Files/*program directory*) does that mean I just have to have a valid copy of the software installed and workable on the windows portion of the HDD? I ask because once I got Wine installed I saw that when I go to "applications" then "Wine" then one of the options is "browse C drive, but I when I select that nothing happens.

p.s. There are a lot of technology memes that I don't get. For one, I don't understand the popcorn smiley. What does that mean?

---

### Post by boriquajake on 2007-11-28
Is it normal to feel guilty about taking advantage of the expertise of the people on the forum?:)

---

### Post by civic_si on 2007-11-28
in order to use the drivers in Linux you need to use NDISwrapper. That was the old way if using wireless drivers.

---

### Post by eldepeche on 2007-11-28
Wine makes a fake Drive C in your Ubuntu home directory. You can't share programs between Wine and a Windows installation. For one, Wine can't run programs off an NTFS partition. You will have to install each program you want to run under Wine individually.

---

### Post by Hairy_Palms on 2007-11-28
in order to start figuring your wireless card open Applications->Accessories->Terminal from the main menu, and type lspci and copy+paste the output here

---

### Post by boriquajake on 2007-11-28
> **Hairy_Palms said:**
> in order to start figuring your wireless card open Applications->Accessories->Terminal from the main menu, and type lspic and copy+paste the output here


Thank you very much for the offer to help, but that is one problem I have already solved. Someone had me do just that and a few steps later I was connected. Thanks again.

---

### Post by boriquajake on 2007-11-28
> **eldepeche said:**
> Wine makes a fake Drive C in your Ubuntu home directory. You can't share programs between Wine and a Windows installation. For one, Wine can't run programs off an NTFS partition. You will have to install each program you want to run under Wine individually.

OK, so as long as I didn't lose/throw away my discs I have a chance at being good to go. Thanks again, all.

---

