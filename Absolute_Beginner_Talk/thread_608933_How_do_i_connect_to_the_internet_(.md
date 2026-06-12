---
title: "How do i connect to the internet? :("
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by ryan666th on 2007-11-10
Can anyone please help me? I installed ubuntu 7.10 on my other computer thinking it was user friendly and have been a little dissapointed. I have a Sagem 800 fast usb adsl modem with talktalk (a bt service) and have no clue how I can connect to the internet because the cd I used on windows to setup my modem ect and connect will not work on ubuntu. It loads but then when i click on the icons that usually run an auto install it says that there is not a program capable of running this?? 

Im not the greatest person with computers but i do reasonably well with other operating systems  and just cannot figure this one out. 

Anyhelp at all would be most appreciated all the best

---

### Post by Scheater5 on 2007-11-10
I'm afraid I'm not familiar with that exact modem, but what you must understand my friend is that Ubuntu is not Windows.  And programs designed to run on Windows or Mac (like your auto-install CD, I assume) will not work on Ubuntu.  
But take heart.  This does not mean all is lost.  First of all, have you tried getting on the internet yet?   If it's an ethernet connection, I can almost guarantee you should be able to connect to the internet without your autoinstall CD - just plug in and surf away.  If it's a PPPoE modem (which I guess it is, since you called it a "modem") try configuring PPPoE with the number ad your password that you used in Windows and see if it won't let you connect (I'm sorry, I'm not at an Ubuntu computer - someone else will have to verify if Gnome-PPP is installed by default and where it is).  
If it is a PPPoE modem, and it won't let you connect, or you can't find the settings manager, you're going to have to connect to the internet briefly through another means (like ethernet) and either install Gnome-PPP or download the drivers for your modem.   
Let us know how it goes, and we will be more able to help you when we know more about the problem.

---

### Post by ryan666th on 2007-11-10
ok ill give it a go and let you know whats going on thanks for your help :)

---

### Post by Botondus on 2007-11-10
I've never used an external USB modem like that on linux and it seems there aren't any official ubuntu drivers for this particular one but there are 3rd party drivers which is good news, but it needs a bit of patience and tinkering to install it.
I never actually needed to do this myself but if i had to install it i would try like this. Open a terminal and type:

```
sudo apt-get install eagle-usb-data eagle-usb-modules-source eagle-usb-utils 
```

After these are installed you can find further instructions for configuring in the readme file
```
/usr/share/doc/eagle-usb-utils/README.Debian
```

And also the online documentation
[http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc](http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc)

---

### Post by Tux.Ice on 2007-11-10
that is so satanist ryan666th

---

### Post by ryan666th on 2007-11-10
Thanks for the help guys but I have officially quit trying to run ubuntu which is a shame as its pretty cool but an operating system i cant use the internet with makes my pc pretty useles lol 

I did follow what the help and support said and downloaded the firmware and then went through the commands ect. I managed to get a ping and get my modem lights to become stable but unfortunetly when I got to one of the commands it just said something along the lines of unable to blah blah blah blah then when i had to save the username password VP VC ect it said unable to save file blah blah blah doesnt exist so sorry ubuntu but its back to windows for me lol

---

