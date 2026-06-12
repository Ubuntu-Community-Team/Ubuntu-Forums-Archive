---
title: "Several questions..."
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Lost Ninja on 2007-02-07
I'm not an absolute beginer at linux having used it remotly on my vhost for a couple of years. But for obvious reasons I never had to do what i am doing now there, just telnet/SSH... So I have questions that need answering.

Setup: I have two pcs next to each other, my newest machine is just running XP, the older machine is the Ubuntu machine (dual booted) but because MS is anal about people stealing its software I can only run one PC with windows :(... :). I got Ubuntu primarily as it was a single CD download and having heard good things about it. Also because the only other distro I have used, vhost, is a big install and I want ease of use. The two PCs in windows mode talk to each other mainly files stored on Max (new PC/Windows) being used on Min (old PC/Ubuntu).

Questions:
1) Is there any way to browse a shared windows directory from the Ubuntu machine? I have Apache on Max if that helps.

2) Is there any way to allow Open office on Min to connect to Max's MySQL DB?

3) How do I set my screen refresh? I have managed after much trials to install the correct Nvidia drivers, Automatix FTW :D but I am still limited to 60hz refresh. I need it to be more than 75hz as otherwise I get headaches. My monitor does support upto 85hz at 1024x768.

4) I'm using synergy to share mouse and keyboard from Max with Min. It works fine but I really need it to automatically start as soon as I login or better yet before hand. Is that possible? Or would it be something that it would need to be writen especially for? If its not possible is there a prduct/package that would work?

5) As the above but this time for a termainl window. Want it open as soon as I login, how should I do that?

6) How do I make shortcuts?

7) How do you run .run files, or do you?

Thanks in advance.

LN

---

### Post by DSn0wMan on 2007-02-07
> **Lost Ninja said:**
> I

Questions:
1) Is there any way to browse a shared windows directory from the Ubuntu machine? I have Apache on Max if that helps.

2) Is there any way to allow Open office on Min to connect to Max's MySQL DB?

3) How do I set my screen refresh? I have managed after much trials to install the correct Nvidia drivers, Automatix FTW :D but I am still limited to 60hz refresh. I need it to be more than 75hz as otherwise I get headaches. My monitor does support upto 85hz at 1024x768.

4) I'm using synergy to share mouse and keyboard from Max with Min. It works fine but I really need it to automatically start as soon as I login or better yet before hand. Is that possible? Or would it be something that it would need to be writen especially for? If its not possible is there a prduct/package that would work?

5) As the above but this time for a termainl window. Want it open as soon as I login, how should I do that?

6) How do I make shortcuts?

7) How do you run .run files, or do you?

Thanks in advance.

LN

I cant answer all your questions, but in my experience you can

1) Browse windoze share's with a samba client

3) I have found that the refresh rate is a limitation of the nVidia binary driver. The OSS driver can get higher refresh rates, but doesn't perform well in 3D acelleration.

4) 5) In your system menu (gnome) select session, and select the startup tab. You can add the programs that you want to start on startup to that window.

5) you can make shortcuts by using ln -s in the terminal (man ln for details), or right click a file in nautilus for shortcut options.

---

### Post by banditti on 2007-02-07
You would be better off asking each question seperately.

6. right click on desktop, create launcher
7. from a terminal session run (without quotes) "./path/file.sh"

---

### Post by dexter on 2007-02-07
I'll give these a shot

> **Lost Ninja said:**
> 
Questions:
1) Is there any way to browse a shared windows directory from the Ubuntu machine? I have Apache on Max if that helps.

Yes, you'll need to install Samba:
sudo apt-get install samba

After that, you can browse to your windows machine using Places, Network Servers. It also works in the other direction, windows will see your ubuntu shares

> **Lost Ninja said:**
> 
2) Is there any way to allow Open office on Min to connect to Max's MySQL DB?

Probably yes, as I don't have much experience with this, I'll let someone else clarify this.

> **Lost Ninja said:**
> 
3) How do I set my screen refresh? I have managed after much trials to install the correct Nvidia drivers, Automatix FTW :D but I am still limited to 60hz refresh. I need it to be more than 75hz as otherwise I get headaches. My monitor does support upto 85hz at 1024x768.

Can you select it in System->Preferences->Screen Resolutions ?

> **Lost Ninja said:**
> 
4) I'm using synergy to share mouse and keyboard from Max with Min. It works fine but I really need it to automatically start as soon as I login or better yet before hand. Is that possible? Or would it be something that it would need to be writen especially for? If its not possible is there a prduct/package that would work?

To start it as soon as you login: go to System->Adminstration->Sessions->Tab called Startup Programs, you can add a line here to start up your program

> **Lost Ninja said:**
> 
5) As the above but this time for a termainl window. Want it open as soon as I login, how should I do that?

Same as above, add the command gnome-terminal to you startup programs (assuming you're using gnome here)

> **Lost Ninja said:**
> 
6) How do I make shortcuts?

Shortcuts are called links: right click the file you want the link to point to and click Make Link
> **Lost Ninja said:**
> 
7) How do you run .run files, or do you?


Go to the folder where you're .run file is with the terminal (use cd to change directories), once there type ./name.run, were name is the name of the .run file. If this doesn't work, you'll have to make it executable first, for that type chmod+x name.run

---

### Post by Lost Ninja on 2007-02-07
Hmm...

Installed Samba, if I try and connect from windows I get a password confirmation, but no username/password combination works. Any ideas?

---

### Post by jackrobinson on 2007-02-07
> **Lost Ninja said:**
> Hmm...

Installed Samba, if I try and connect from windows I get a password confirmation, but no username/password combination works. Any ideas?

follow this howto for samba:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by airtonix on 2007-03-26
you can also make symlinks (windows shortcuts are a pale 3rd world clone of linux symlinks) by ctrl+shift draggin a file.....just like you do in windows.

in windows a shortcut is basically a batch file (.bat or for the linux peeps a bash script) that basically runs the target operation....thats it.

you cant make a shortcut of "My Documents" folder into the root of your LAMP root folder (c:/xamp/apache2/htdocs/) and then explore all your files from a browser as if the shortcut were a folder......no in the browser this shortcut is nothing but a text-file. windows does not translate the functionality for upper level programs.

however windows does have junctioning. which again is yet another third world attempt at symlinks. lol (ms dont recomend yusing it as it guffs up your drives)

---

