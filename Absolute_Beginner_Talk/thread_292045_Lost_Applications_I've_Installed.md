---
title: "Lost Applications I've Installed"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by drisley on 2006-11-03
I am new to Ubuntu and Linux in general. I am a long-time Windows guy, so I am giving Ubuntu a try and am running up into brick walls. The biggest problem I'm having is that when I install software, it sometimes is completely lost. For example, I tried to install Synergy via the Synaptic Package Manager. It says it was installed. Yet, I cannot find it ANYWHERE.

I read somewhere that installing Debian menu was good for seeing all applications installed. Same problem with this! It says Debian menu is installed. I even see if when I go into Menu Layout. However, it is italicized and will not allow me to select it. And Debian does not appear in my applications menu. I have run every terminal command I could find on various threads talking about this. Nothing.

This is incredibly frustrating. I want to like this thing, but so far I'm thinking Windows is much easier to use.

Any help would be grand.

---

### Post by ibanezix on 2006-11-03
Installing with Synaptic wouldn't need this but you might want to try 

sudo killall gnome-panel

that will refresh the menus. Other than that, all applications I 've installed with Synaptic have created their own menu entries.

---

### Post by justifier on 2006-11-03
often to start a program type the name of the program in terminal. you can acess terminl in applications > acessories > terminal

---

### Post by Marsolin on 2006-11-03
Unfortunately some apps, and [Synergy]("http://linuxappfinder.com/package/synergy") is one of them, don't include menu entries. I agree that it is very frustrating. There are two executable files included with it: synergyc and synergys. synergyc is the client and synergys is the server. Run synergys first on the system that you want to control and then run synergyc on the system you want to do the controlling from. You will need to run them from the terminal though.

---

### Post by Arby on 2006-11-03
A couple of points.

Firstly, the suggestion to refresh the panel is a good one, sometimes this is necessary before new stuff appears. Although if you have rebooted at all during this time then that should happen automatically. 

Another option is to add programs to the menu manually. Some programs automatically add themselves to the menu, some don't, it depends on the people who wrote the program. To add programs to the menu, navigate via system settings or menu layout to wherever you would edit the menu.

You should then have options to add an entry. Do so, you will have a box to enter the command to actually launch the program.

Hopefully there should be a button labelled browse or similar. Press that, you can then navigate to the directory where the program lives. If you're a long time windows user you're probably looking for an equivalent to C:\Program Files. 

On linux the nearest equivalent is the following. Program executables are located in either /usr/bin or sometimes /usr/local/bin. Synaptic usually puts stuff in the first one. 

So navigate to that folder and find the file named synergy (or whatever) and click on it. Click Ok and save your changes to the menu. With any luck you should have a new entry on your menu now.

Hope that helps.
Sorry for the vagueness, I'm at work and stuck on a Windows box so I'm guessing a bit exactly where things are.

---

### Post by drisley on 2006-11-03
It's coming together, however I have all but written off Synergy for now. Most programs I install seem to show up, but still have not managed to get Synergy or Debian menu to function.

Using Synergy on Windows was a breeze. Different story for Linux.

---

### Post by OffHand on 2006-11-03
> **drisley said:**
> It's coming together, however I have all but written off Synergy for now. Most programs I install seem to show up, but still have not managed to get Synergy or Debian menu to function.

Using Synergy on Windows was a breeze. Different story for Linux.
Getting used to a new OS and making a setup that suites your needs usually takes a bit of pain and effort. I enjoyed the learning process myself. Once you have configured your machine the way you like, it will be a joy forever. 
Just remember: no operating system is perfect.

---

### Post by whein on 2006-11-03
I found myself in a very similar situation when I plunged down the Ubuntu path this summer for the first time.  I found that it is often enough to click on the properties of the installed package in Synaptic and click on the tab that says what was installed and to which directory.  Still a little cryptic, but it usually heads me in the right direction.  Another trick I've picked up along the way is to search the forums and the web for other people who have installed the program.  Usually I can find a HOWTO install or configure or other.  A bit more work than I'm used to, but then again, when something doesn't work in Windows, I usually just ignore it or delete it outright.  At least now I have the option to look under the hood and twiddle around before throwing up my hands and looking for a replacement app that plays better.  :)
A word of caution, when randomly executing files just installed, it is often a good idea to run them with only the --help or -? arguments (or better yet, read their man pages or README files) to avoid doing really nasty things to your system by accident.  With great power comes great danger so don't just execute every random snippet of code you find.  Make sure you understand what it will do first.
-Will

---

