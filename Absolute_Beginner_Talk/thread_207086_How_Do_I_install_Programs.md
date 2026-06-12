---
title: "How Do I install Programs?"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by KLoWnTaZ on 2006-07-01
LoL ok I am totally new to this world. I decided to break away from the grind and learn a new OS. I just installed and updated my first copy of ubuntu. Now I wanna listen to music so I downloaded xmms-1.2.10 now how the heck do I install it hehe I am such a noob...

Thanks for the help

---

### Post by mcduck on 2006-07-01
Here's a link to help you: [How to install *ANYTHING* in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by jakez on 2006-07-01
Maybe this will help:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
Greetz

---

### Post by woedend on 2006-07-01
no problems.
go to system -> administration -> synaptic package manager

for the time being this is the easiest way.
You may need to add repos along the way - From ubuntuguide -
To enable the extra Universe and Multiverse repositories

   1. Settings -> Repositories
   2. In the Installation Media tab, click Add. There are three separate repositories; Dapper Drake, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes
   3. You should now see those three repositories under Channels. Make sure Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse) appears under each repository 

Click the refresh/reload button in synaptic, then search for xmms.  When you find it, right click and mark for installation.

edit: nevermind...see above posts they are much more in depth :)

---

### Post by KLoWnTaZ on 2006-07-01
Thanks Very Much But my sounds don't work LoL just my luck :p I have onboard sigmatel sound driver for windows where would I find it for ubuntu?

---

### Post by u.b.u.n.t.u on 2006-07-01
Installing software other than synaptic is risky and a pain. It isn't easy like windows.

To play music you need codecs. Use synaptic to find and install gstreamer. There are many of them. I install everything with the name "gstreamer".

Ubuntu isn't XP. Linux is more advanced in some areas and more backward in others. Installing software is one area where all of Linux are in the dark ages.

---

### Post by u.b.u.n.t.u on 2006-07-01
[QUOTE=KLoWnTaZ]Thanks Very Much But my sounds don't work LoL just my luck :p I have onboard sigmatel sound driver for windows where would I find it for ubuntu?[/QUOTE]

Check out:

System > Preferences > Sound

If you have more than one sound device, make sure the correct one is selected.

---

### Post by KLoWnTaZ on 2006-07-01
Only one sound card selected. HDA intel.
If i need codecs where do I get them also I have no system sounds so is it codecs of some driver problem. I know I have to stop thinking in windows terms but this is my first day :)

---

### Post by richbarna on 2006-07-01
[QUOTE=KLoWnTaZ]Only one sound card selected. HDA intel.
If i need codecs where do I get them also I have no system sounds so is it codecs of some driver problem. I know I have to stop thinking in windows terms but this is my first day :)[/QUOTE]

Don't worry about thinking in windows terms, you are new. Once you get a feel for the system and read the forum for information, you will soon get the hang of it. Remember that many users here still dual-boot with windows.

People may give you commands to copy and paste into your "Terminal" (applications/accessories/terminal), although it's probably different for you than GUI's and point and click, it is very effective.

For your drivers and other extras, I recommend Automatix. It will install many things for you. Take a look at my "sig".
|
|
v

---

### Post by woedend on 2006-07-01
what kind of message are you getting when you try to play?  Do you hear any of the startup sounds?
Its probably not a codec issue as XMMS will play most formats by default.

---

### Post by givré on 2006-07-01
For codec -> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Baasha on 2006-07-01
If this is a new install, look around for the program that adjusts sound levels.  It is not under Preferences>Sound but is hidden away somewhere else.  Maybe someone more knowledgable can tell you where it is.

Anyway, I too am a newbie, and had the same problem.  After lots of head scratching I finally figured out that the Ubuntu program comes with all the sound levels turned down to zero.  Kind of dumb, but that's the way it is.  You probably don't have a problem at all, it is just that the sound is turned way down.

---

### Post by KLoWnTaZ on 2006-07-01
I am totally lost on how to install Automatrix. Do i Have to bash line terminal or synaptic I don't see anything to download All i see is instructions. Sorry to be such a pain guys... Will some one walk me thru install?

---

### Post by givré on 2006-07-02
To install automatix -> [http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)
To use it -> automatix in a terminal

---

### Post by KLoWnTaZ on 2006-07-02
[QUOTE=givré]To install automatix -> [http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)
To use it -> automatix in a terminal[/QUOTE]

To me those instructions make no sence I tried entering them in the terminal.
Nothing...
:::HELP:::

---

### Post by givré on 2006-07-02
Come on, it not so hard.
I will try to make it more easier.
1. Open a terminal
2. You need to change your repository liste to install automatix:
```
sudo gedit /etc/apt/sources.list
```
3. At the end of the files, add the repo where you can download automatix:
deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main
4. Close gedit
5. Add the key of the repo to have no warning. Copy/paste in the same terminal:
```
wget http://www.beerorkid.com/automatix/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
```
6. Update your package list and install automatix. Copy/paste in the same terminal:
```
sudo apt-get update
sudo apt-get install automatix
```
7. That's it. To launch it, simply launch ```
automatix
```from a terminal.
I cann't make it simplier

If you have a problem, tell me the errors you have

---

