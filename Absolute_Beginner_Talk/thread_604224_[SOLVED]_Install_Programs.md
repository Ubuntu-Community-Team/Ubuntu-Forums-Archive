---
title: "[SOLVED] Install Programs"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Jitudo on 2007-11-05
I just installed ubuntu for the first time today and so hello to everyone in the community.

I have alot of beginner questions, but for starters, how do you install programs? I cant do command prompt, so thats out of the questions.

What I am trying to install is the thinkfree premium software for linux, at thinkfree.com. I downloaded the software and it came onto my desktop, but when i double click it says:

"Could not open the file /home/asad/Desktop/TFO-3…4-linux-en-gui-premium.sh.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

And then it gives me a drop down menu to select character coding. Huh?

I tried going the synaptic package manager, thinking that the thinkfree software needs to be installed through this, but i couldnt find it anywhere. Then in the manager I click 'File' then 'Add downloaded packages'

I then went to where the file was on my desktop within the add package window and i found the file but couldnt select it, it was greyed out.

Here is the name of the file:

TFO-3.3.0884.44-linux-en-gui-premium.sh

I really would appreciate some help. Thanks. I hope no one minds if I bother you guys with more questions as the days go by as I am very eager to learn.

---

### Post by Maestro23 on 2007-11-05
Open a terminal: Apps>>Accessories>>Terminal 

Get to your Desktop. Then try the following 2 commands.

> cd ~/Desktop

sudo chmod + x filename.sh

./filename.sh

Welcome to Ubuntu.  Some links for future reference:

Installing Software in Ubuntu:
Installing Anything: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Psychocats Page: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Jitudo on 2007-11-06
I opened the terminal, but what do you mean by go to my desktop. within the terminal? how do I do that? I typed cd ~/Desktop and it said bash: CD: command not found.

I really have no idea how to use the terminal and if there was a gui way of doing things i would appreciate it so that I can learn how to do things from here on out.

---

### Post by lyndaj70 on 2007-11-06
welcome to the community!

To install programs:

System>Administration>Synaptic Package Manager.  Just browse or search... for example, type in dvd will bring up all sorts of goodies about playback and burning!

Good luck!
~Lynda

---

### Post by lyndaj70 on 2007-11-06
> **Jitudo said:**
> I opened the terminal, but what do you mean by go to my desktop. within the terminal? how do I do that? I typed cd ~/Desktop and it said bash: CD: command not found.

I really have no idea how to use the terminal and if there was a gui way of doing things i would appreciate it so that I can learn how to do things from here on out.

Your syntax is wrong.  Open the terminal and type this exactly, or copy and Paste:
```
cd Desktop/
```

Take care!
~Lynda

---

### Post by Jitudo on 2007-11-06
Thanks, I did that and now it says the desktop thing at the end of my computers name. Now what?

Is there a way to do this through the synaptic package manager? Do I always have to use the terminal to install programs I find online? Isnt there a way to add programs to the manager and install them there? Please read my posts above as I tried to do this very thing with this software but it didnt work.

---

### Post by daengbo on 2007-11-06
Jitudo,

Right-click on the file you downloaded. Go to the "Permissions" tab and click "Allow executing file as program." Close the dialog and double-click on the file. From the name of the file, I'd guess that it will open a GUI for installation.

Another option is to open a terminal and type 
sh Desktop/TFO-3.3.0884.44-linux-en-gui-premium.sh

Off-topic, have you looked at Google Docs? It's online and doesn't require any kind of installation. It will work on Windows, Linux, or Mac.

---

### Post by daengbo on 2007-11-06
Oh, there are even extensions to OpenOffice.org to open and save Google Docs files.

---

### Post by Jitudo on 2007-11-06
Ok so I got it to load through the terminal, thanks. But when the install box comes up for the software, it says it is putting it in this directory '/usr/local/tfo3.0_premium'. which is fine, because i have no idea where that is, but when I press enter, it says I have no write permissions for this directory and to choose another one. Ok, so then I go to select the directory to install it in and that box opens but its blank, as in entirely grey except the topbar that says 'select directory'. Do you think this is a problem with thinkfree or with linux? What should I do? I really need to use this software.

I do use google docs, but google docs isnt powerful enough, I dont know how much you know about thinkfree, but they have an awesome product. They have an offline version of their software which syncs with their online software, and so you have copies of docs in both places.

---

### Post by macdo on 2007-11-06
You need to install as root, I'd imagine. 
```
sudo sh Desktop/TFO-3.3.0884.44-linux-en-gui-premium.sh
```

That will ask you for your password.

---

### Post by Jitudo on 2007-11-09
Thanks, that worked. I appreciate it.

---

