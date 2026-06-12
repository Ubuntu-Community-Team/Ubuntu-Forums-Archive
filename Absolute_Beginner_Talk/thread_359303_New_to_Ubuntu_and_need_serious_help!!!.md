---
title: "New to Ubuntu and need serious help!!!"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Uugah on 2007-02-11
Hi all, I am totally new to Ubuntu and Linux? as well. I got here simply for the fact that with XP and this new Vista being so greedy about how many machines or times it can be installed I thought it was time to stop feeding Bill Gates and his money machine!

Anyways, I have installed this Ubuntu and I am having trouble finding some down to earth instructions on how to get things like downloaded programs or even other programs from a CD to install. I have read about using this Synaptic Package Manager and have tried to use it but to no avail.

I am thinking that there are some other programs that I need to install prior to using this in order to get all of this to come together.I also tried to install a .deb program as 1 article I read said this is what controls(for lack of a better word) these types of programs.This also got me nowhere. Add/Remove programs showed a downloaded program but was grayed out and I wasn't able to do anything with it.

Please help me find the key to start this thing as I am very limited to time and only have a small portion of my weekend to devote to search and destroy!

Thanks all!

---

### Post by oilchangeguy on 2007-02-11
there are several books available on ubuntu, check your local bookstore. and there's lots of help here in the forum as well.

---

### Post by meng on 2007-02-11
Tell us what you want to install, we can tell you the easiest way to install it.

---

### Post by Hranj on 2007-02-11
hopefully this will get you started.

[How to install anything in ubuntu]("http://www.cutlersoftware.com/ubuntuinstall/")

You might also want to take a look at a program called Automatix. It will install a lot of the programs like flash and java for you as well as some other programs and plugins. I cant find the link i usually use on the forums but a google search can fix anything.

---

### Post by Zuuswa on 2007-02-11
What problems are you having with synaptic??  I use it to install 99% of all the programs I use!  Just use the search button and enter some keywords or functions you want from a program and it will list the available ones to download.  Then right click on them and select install package.  If you are having trouble finding where the package is installed or how it is running, try looking it the differant menus under applications.  Some programs are run in a console, and can usually be run by just typing the name of the program into a console/terminal.

---

### Post by nickoli_02 on 2007-02-11
Welcome to linux! You may feel a little lost and confused at first, but stick with it and try to resist that temptation of going back to familiar old Windows...
With time you will become much more comfortable with linux and (hopefully) will never have the need to go back to windows. That's where I'm at right now, and I've only started using linux since June 2006.

---

### Post by Uugah on 2007-02-11
Thanks for all the quick replies........:grin: 

O.k. for instance, I wanted to show the weather icon or at least have the weather on my desktop so all I have to do is click the little temp icon instead of having to get to it via starting up a new web browser. I downloaded the installer which is twctool.exe from the weather channel home page which would have installed a weather tool bar and a nice icon showing the current temp for my area.

Also, 1 of my kids wanted to play a game she has on CD and I cannot get either of these to install as it tells me there isn't a program suitable for installing this type of file.

I did notice that there are a slew of programs already available to me in the Add/Remove section and i'm wondering if some or most of these shouldn't be installed prior to trying anything else? If not then what am I missing? I am familiar with the old DOS setup as this is what i was used to back in the old 4086-88 days. But for me, that's like asking me to remember what my first bike's color was and how the ride was..........LOL

---

### Post by meng on 2007-02-11
Your first problem is trying to run/install .exe files in Ubuntu. These are Windows executables. Ubuntu is a different operating system.

---

### Post by nickoli_02 on 2007-02-11
First thing you'll probably want to do is open a terminal and type:

```
sudo apt-get update
sudo apt-get upgrade
```

This ensures all the packages on your system are up-to-date. As for your daughter's game, it's most likely for Windows. You can't natively run windows applications in linux, but there is a program called WINE that allows you to use windows applications in linux.

As for the weather icon, right-click the top taskbar and click "Add to Panel". There's a weather reporter there waiting to be added! You can configure it to report weather for your specific location.

---

### Post by Uugah on 2007-02-11
Thanks again.......I forgot about that game and should have realized that!!!......HEHE

O.k., I will try the update using the apt command and go from there.......so much to learn and get familiar with but I already like most of what I see here and wonder why it took me sooooo long to get this far.

---

