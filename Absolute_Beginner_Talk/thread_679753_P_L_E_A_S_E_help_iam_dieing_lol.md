---
title: "P L E A S E help iam dieing lol"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Forked Tongue on 2008-01-27
First of all let me thank you for even checking my thread :)


Ok so basically iam "growing" more gray hair lol

well the problem is i got used to Windows and the simplicity, i know what your thinking right now, is that how can i say that because Ubuntu is WAY much simpler lol but thats what i see it, maybe iam wrong, iam only human... or am i lol

but to give you a real life example lol

its been now over a "MONTH" and iam still trying to install this thing called "Compiz" so i can get better graphical features ... i want to see that Cube thing !! lol .... and unfortunately untill now i couldnt ...

also iam trying to install my graphics drivers so i can "At Least" run the cool screen servers lol and untill now i do not know how to do that lol


So Every time i run Ubuntu it simply goes like this :)

1.Happy with Ununtu :)
2.Trying to install Graphic Drivers :)
3.Fail to understand how to install the Graphic drivers ....
4.Sad
5.Try installing Compiz :)
6.Fail to understand how to install Compiz ....
7.Sad
8.Play Chess ...
9.Lose to the Computer ....
10.Sad
11.Turn off Ubuntu and go back to Windows to kick some PC *** lol

thats it EVERYTIME !!!!! lol

wish there was like a simple way to do this. simply a click of a button .... i realy realy realy realy miss the "Setup.exe" button :(

So could you PLEASE, and i mean Please in red huge font letters lol, help me. i need something simple something that is not so complicated.

because everytime i ask for help i get some strange lines saying this is for some kindda terminal !?!?

and belive you me, iam right now walking in Real Life and i got a Question mark over my head lol


So by now i think i have accomplished to actually let you Ladies & Gents know that you are talking to a complete 100% class A "NOOB" lol

but i want to learn, so kindly tell me what to do :)

if my case is hopless lol then just let me know so i can uninstall ubuntu lol


Many thanks and appreciation in advance :)

Regards,
Forked.

---

### Post by FuturePilot on 2008-01-27
For the graphics driver check the Restricted Driver Manager. System>Administration>Restricted Driver Manager. Compiz is already install.

---

### Post by Ub1476 on 2008-01-27
Assuming you have a fresh and clean install type this into the terminal:

```
lspci | grep VGA

compiz
```

There are ways to do this graphical, but this is **much** faster:)

---

### Post by mikewhatever on 2008-01-27
For graphics drivers, System --> Admin --> Restricted Drivers, and try to enable it. If not successful, report what went wrong and the exact model of the card.
Compiz is preinstalled, so you don't need to install it. I would be wise to remove anything you have installed so far. What you do need to run the cube is the restricted driver and the package called compizconfig-settings-manager.

---

### Post by jan quark on 2008-01-27
I had to install xserver-xgl from the synaptics packagemanager to run compiz
then I had to choose during my log in another session namely the run xclient session

---

### Post by bumanie on 2008-01-27
knowing your machine specifications would help, could you please post them including model and make of graphics card

---

### Post by candtalan on 2008-01-27
The use of compiz will depend on what graphics video card you have. If it does not do the 3d graphics stuff then it will not run.

Note that compiz is already  installed when you have ubuntu 7.10
If the setting in 'Appearance' cannot be changed then consider the graphics card?

I often use kubuntu and it is harder to get runniing in this.

---

### Post by AutumnPhoenix on 2008-01-27
perhaps try xubuntu...my computer seemed to reject pure ubuntu but the graphics are snazzy on my lappy with xubuntu.

---

### Post by Forked Tongue on 2008-01-27
Ok...... well .... lol

Iam now talking to you from my PC ....

Why ? .... well simply lol ive gone to Restricted drivers ... and i found my ATI Drivers were there ... so as a Noob :)

i clicked on them to get installed lol

and now my Ubuntu wont start :)

so ... what am i supposed to do lol ?

Format ?

Many thanks ladies & gents for your time and help :)

Regards,
Forked.

---

### Post by Therion on 2008-01-27
This link should help you get the Cube, and some other neat stuff, up and running in Compiz.  

[How to Set Up Compiz Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion").

---

### Post by Forked Tongue on 2008-01-27
Allrighty

My laptop is up and running now, i think Ubuntu felt bad for me or something lol

any way, now after my ATI drivers from "Restricted Drivers" is up and running i can now see at least the cool Screen Savers ! :)

however ... when ever i go to Appearance, and chose Hight ..

it shows me this error window ... need the translation into easy English please :)

[IMG]http://xs223.xs.to/xs223/08040/geerror637.png[/IMG]

Regards,
Forked.

---

### Post by stoodleysnow on 2008-01-27
Firstly, one can overuse expressions such as 'lol' :roll:
and secondly, what do you mean by it won't start?
what screens do you see on attempting to start? any errors or does it just show something like
```
forkedtongue@snakecomputer:~$ 
```
because if that is what you end up with, it's basically the computer failing to put that particular restricted driver with that particular card. So it does the next best thing and gives you a command line prompt from which you can manually alter stuff. In that case you will need to reconfigure xorg.conf.
A format should not be necessary at this point.
So what do you get?

---

### Post by Forked Tongue on 2008-01-27
ok then no more "lol" 

well my Laptop started now i just said that, i don't know why it stopped working and i don't know why it suddenly chose to start working again ......

now when it magically started working again, it gives me this pop up window above my post when ever i try to click on High on the Visual effects.

---

### Post by Sockerdrickan on 2008-01-27
One can not overuse "lol" :KS

---

### Post by stoodleysnow on 2008-01-27
> **Forked Tongue said:**
> Allrighty

My laptop is up and running now, i think Ubuntu felt bad for me or something lol

any way, now after my ATI drivers from "Restricted Drivers" is up and running i can now see at least the cool Screen Savers ! :)

however ... when ever i go to Appearance, and chose Hight ..

it shows me this error window ... need the translation into easy English please :)

[IMG]http://xs223.xs.to/xs223/08040/geerror637.png[/IMG]

Regards,
Forked.

Well in that case try checking Synaptic Package Manager. Make sure all results from searches for Compiz and Compizconfig-settings-manager are installed. Then (reboot if you like) and try again.

---

### Post by Therion on 2008-01-27
Are you familiar with how to use Synaptic?  You need to install a couple things to get this error to go bye-bye.

Navigate to System--> Administration--> Synaptic Package Manager

Use the Search tool and search for **xserver-xgl**
Install it.

Then search for **compizconfig-settings-manager**
Install it.

You may need to reboot at that point, I'm not sure (it's early here and I'm on my first cup o' joe, so bear with me).  
Then, try to enable the Advanced Desktop Effects option.

---

### Post by ugm6hr on 2008-01-27
When asking for help, it is useful to provide some information.

The most important fact: **What graphics card do you have?**

You mention ATI driver - so presumably it is an ATI card.... Yes?  Assuming it has 3D acceleration capability, there are 2 options for you:

This is the "official" way, which will give you least grief.
[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

If that doesn't work - report back and we'll try a different approach.

If you don't know what "Terminal" is - see the link below in my signature (Enter Code....)

PS: If you don't know what graphics card you have - in Terminal:
```
lshw -C display
```

EDIT: Therion has distilled out the important bits of my link above (I was too slow :(

---

### Post by Forked Tongue on 2008-01-29
> **Tux0r said:**
> One can not overuse "lol" :KS

EXACTLY !! lol lol lol lol lol

---

### Post by Forked Tongue on 2008-01-29
> **Therion said:**
> Are you familiar with how to use Synaptic?  You need to install a couple things to get this error to go bye-bye.

Navigate to System--> Administration--> Synaptic Package Manager

Use the Search tool and search for **xserver-xgl**
Install it.

Then search for **compizconfig-settings-manager**
Install it.

You may need to reboot at that point, I'm not sure (it's early here and I'm on my first cup o' joe, so bear with me).  
Then, try to enable the Advanced Desktop Effects option.

YES !!!! Thank you thank you thank you !!

its working lol

however wow .... i can actually see blood coming outta my Laptop lol Ubuntu graphics is killing it haha

guess its time to go Laptop shopping !


What do you think guys ? Toshiba or HP ? or whats even better than those two ?

Iam looking for a Gaming PC that can run Ubuntu to the max graphical effects and ofcourse not that expensive

most of my friends are saying go with HP.

Once again thanks ALL for the help and the time, i really do Appreciate it alot :)


Regards,
Forked.

---

### Post by thiebaude on 2008-01-29
Go with Dell

---

### Post by NullHead on 2008-01-29
I also would go with Dell.

---

### Post by Therion on 2008-01-29
Another Dell vote here.  

I just helped a woman configure a Dell desktop (in keeping with her $1,000-or-less budget) and was surprised at what we were able to put together with that.  Those sub-$1K boxes are as close to a "Mission: Impossible" as I want to come.

That being said, two of my co-workers have outstanding laptops, both assembled by Acer, and they got them for a song, comparatively speaking.

---

