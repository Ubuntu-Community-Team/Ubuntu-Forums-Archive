---
title: "[SOLVED] MS Windows Ctrl + Alt + Delete: any equivalent in Ubuntu?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-04-13
Hello all,

I'm looking for an equivalent of MS Windows Ctrl + Alt + Delete that calls the running apps and processes tabs. This way, I could set/edit priorities or do a straight killall on any unresponsive app.

Any ideas?

---

### Post by KitChy on 2007-04-13
system>admin>system monitor

---

### Post by jbowman86 on 2007-04-13
ctr alt del will show u the current processes and system monitor after u have added the ctr alt del package that can be added using automatix2. run a search on the web for automatix website and follow the instructions

---

### Post by eentonig on 2007-04-13
Avoid automated third party script. Because they keep you dumb on what's going on in your systems. And if things then get broken, you'll have a harder time figuring out where it went wrong.

jbowman86, what's the name of that package? Is it in the repo's,

---

### Post by the8thstar on 2007-04-13
Wow, that was quick! Thank you guys for your posts, tips and answers! I'll try the advice right away!

---

### Post by bcmiller on 2007-04-13
> **eentonig said:**
> Avoid automated third party script. Because they keep you dumb on what's going on in your systems. And if things then get broken, you'll have a harder time figuring out where it went wrong.

jbowman86, what's the name of that package? Is it in the repo's,

This is the absolute beginners section.  Why not advise him to use Linux from Scratch or even better he should write out the sourcecode on a bar napkin so he really knows what he's doing?

Automatix does prevent you from learning about linux but that wasn't the goal of this users question.  Ubuntu also prevents you in many ways from learning linux as well.  It's called "making it easy". 

If you want to install stuff easy get Automatix2 and enjoy using your computer.  If you ever find youself needing to fix a broken computer you will find plenty of help here.  If you really want to learn linux please visit [www.slackware.com](www.slackware.com) :p

I used Automatix and installed the Alt+Ctrl+Del program and it's a great ad.

---

### Post by happy-and-lost on 2007-04-13
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

But I prefer <Alt><F2> + xkill for sorting out misbehaving apps :twisted:

---

### Post by aktiwers on 2007-04-13
```
 sudo apt-get install htop
```
in Terminal will install a Terminal based one :)

Run the program afterwords by typing 
```
htop
```
in Terminal.

---

### Post by Drithyin on 2007-04-13
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME)

---

### Post by u04f061 on 2007-04-13
> Automatix does prevent you from learning about linux but that wasn't the goal of this users question. Ubuntu also prevents you in many ways from learning linux as well. It's called "making it easy".

why you are preventing some one from learning Linux. Wow Linux is new world. explore it.find more and more. don't hesitate from commands. It is the true knowledge

---

### Post by bcmiller on 2007-04-13
> **u04f061 said:**
> why you are preventing some one from learning Linux. Wow Linux is new world. explore it.find more and more. don't hesitate from commands. It is the true knowledge

I am not looking to get into a whole debate on this issue. 

I am not preventing anyone from doing anything.  I am also not insisting that they must learn linux to use linux.  That is the whole beauty of using Ubuntu.  It just works so you don't have to and arnieboy put a lot of work into making a tool that makes the easiest linux even easier ([Automatix2]("http://www.getautomatix.com/")).  

I agree that ppl shouldn't shy away from the CLI and I took the time to learn linux myself and I am still learning more each day.  I just think that there is nothing wrong with using tools that work.

---

### Post by the8thstar on 2007-04-14
I appreciate everyone's replies and help. As a recent migrant from MS Windows, I am used to thinking and using the computer in a certain way to look for files, launch programs, tweak settings, etc... Ubuntu/Linux is fairly similar and yet quite different.

Automatix is a nice package for the newbie. It should probably be part of the install distro (all commercial considerations set aside, if any) as an option which the user could pick. Actually, I installed most of the programs that are present in Automatix myself already, by learning my way around through trial and error and reading posts in forums like this one. I am learning something new everyday! Ubuntu seems to be greatly customizable indeed. 

Yet my purpose is not to use Ubuntu as a toy or computer experiment. The Ubuntu OS is a tool, not an end in itself. I'm expecting the OS to be up and running to launch the programs that I need, when I need them. In other words, I prefer to be the driver of my car and enjoy the ride, instead of being the mechanic fixing it. Don't get me wrong, art for art is a great thing, but I think it's just missing the point.

Anyway, thanks again for the great help! 

The 8th

---

### Post by KIAaze on 2007-04-14
Altough this is not exactly what you asked for, here are some other keyboard shortcuts that you might find useful in case your computer seems to be freezed:
CTRL+ALT+BACKSPACE -> kill X
CTRL+ALT+Fn -> switch to virtual terminal n (+F7 for the GUI)
This last one is basically like a shortcut to a console (use ctrl+alt+F1 for example). That way you can use "ps" to list processes ("ps -u <username>" to list your own) and then "kill -9 <process ID>" to kill them.

[http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-8.html]("http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-8.html")

---

### Post by u04f061 on 2007-04-14
> CTRL+ALT+BACKSPACE -> kill X
as far as i think it will log you out.

---

