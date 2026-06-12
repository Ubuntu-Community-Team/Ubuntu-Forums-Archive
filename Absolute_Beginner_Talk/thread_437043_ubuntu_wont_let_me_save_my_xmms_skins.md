---
title: "ubuntu wont let me save my xmms skins"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by blackmajik2021 on 2007-05-08
when it try to save my xmms skins to the folder they need to be in "/usr/share/xmms/skins" ubuntu tells me that i cant save the file because im not allowed to modify that folder? Im really not getting this.

---

### Post by taurus on 2007-05-08
Try to use sudo if you want to write to /usr/share/xmms/Skins.

```
sudo mv **filename** /usr/share/xmms/Skins
```
Otherwise, save it to ~/.xmms/Skins.

---

### Post by blackmajik2021 on 2007-05-08
i dont know what sudo is, i just installed the OS last night. also, it wont let me chose where to save it with text ( icant type in a location) it forces me to use the browser because the input box is greyed out.

---

### Post by taurus on 2007-05-08
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by NeoLithium on 2007-05-08
sudo stands for Super User Do; it allows you to use the system administrator permissions for the command you are typing, in a safer manner than logging in as root.  You'll see it a lot when installing programs and modifying file contents, things like that.

For XMMS, if you didn't really want to use that, you can keep the skins in your own personal folder, which is
/home/YOURUSERNAME/.xmms/Skins/

---

### Post by blackmajik2021 on 2007-05-08
ok i saved them in my username folder and when i go to skin browser they wont show up. whats up with that? when i click them it says i cant open that type of file.

---

### Post by taurus on 2007-05-08
What's the output of this command from a terminal then?

```
ls -la ~/.xmms/Skins
```

---

### Post by H.E. Pennypacker on 2007-05-08
taurus, why are you making references to the terminal when the guy said he JUST installed Ubuntu?  He does not know what sudo is, and you are directing him towards the terminal.  That does not make any sense.  It only makes the new person raise his eyebrows.  

blackmajick, please press ALT-F2, and type "gksudo nautilus."  Don't add the period, and don't add the quotation marks.  Just type that into the window (the "run window")  that pops up after pressing ALT-F2.  After you've typed in the above, a new window will pop up asking for your password.  Enter your password.  You should now have the file manager (the window you're used to already when browsing your files) opening up.  Go to the /usr/share/xmms/skins/ folder, and take whatever you downloaded, and put it into this folder.

You should now be able to select your your new theme from XMMS.

You were not able to do what you wanted to do, because you were trying toa ccess a restricted directory.  Any place other than your home folder is restricted, and going anywhere restircted requires your password.

Do yourself a favor and dump XMMS.  Install Audacious instead.  Support dedicated to XMMS is not provided ANYWHERE.  Audacious DOES have its own dedicated forums in case you have any questions.  Besides, its better than XMMS.

Go to the Audacious website for more information and downloads:

[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

If you decide you want Audacious instead, install it using Automatix.  Get Automatix from [www.getautomatix.com](www.getautomatix.com).  

Let us know if you have any other problems, but PLEASE avoid the command line/terminal.  Whenever you are asking for support, kindly let people know you want GUI instructions, not some cryptic commands using something from the 1990s.

---

### Post by Sef on 2007-05-08
> Let us know if you have any other problems, but PLEASE avoid the command line/terminal. Whenever you are asking for support, kindly let people know you want GUI instructions, not some cryptic commands using something from the 1990s.

Actually the command line is safer than automatix.   With automatix you could end up breaking your system and having to reinstall.  Also automatix is third party software and not supported by Ubuntu.  

There is nothing cryptic about installing with the command line.  

```
sudo apt-get update
```

```
sudo apt-get install (program name)
```

---

### Post by H.E. Pennypacker on 2007-05-08
Sef, I am perfectly comfortable using CLI, but I realize it is not appropriate for beginners.  As long as people continue to push CLI, people will continue to think about Linux as being something from the 90s.  So, you think you're helping someone by advocating the terminal, but you're really adding to the negative view of Linux (that it is too difficult to use).

---

### Post by zenwhen on 2007-05-08
> **H.E. Pennypacker said:**
> Sef, I am perfectly comfortable using CLI, but I realize it is not appropriate for beginners.  As long as people continue to push CLI, people will continue to think about Linux as being something from the 90s.  So, you think you're helping someone by advocating the terminal, but you're really adding to the negative view of Linux (that it is too difficult to use).

Please stop pushing your opinions on others who wish to help. People will help others how they wish to help. You can not control that, but can offer help in the manner you wish to.

---

### Post by matthew on 2007-05-09
> **H.E. Pennypacker said:**
> taurus, why are you making references to the terminal when the guy said he JUST installed Ubuntu?That's like saying, "Why are you making references to the accelerator pedal when the guy just wants to learn to drive a car?"

Anyone who wants to learn to use something new will have to realize that the thing they are learning may already have established methods for doing things that work very well. These methods will seem foreign and difficult at first, but with just a little bit of time and practice, they will enable to user to be far more adept than enabling people to avoid adapting.

Taurus was doing this user a genuine and kind service.

> **H.E. Pennypacker said:**
> Sef, I am perfectly comfortable using CLI, but I realize it is not appropriate for beginners.  As long as people continue to push CLI, people will continue to think about Linux as being something from the 90s.  So, you think you're helping someone by advocating the terminal, but you're really adding to the negative view of Linux (that it is too difficult to use).Linux is based on Unix, which is from the 1960's, not the 90's. It hasn't changed a whole lot behind the scenes because it was made well to begin with. Things that have changed have generally been additions to functionality.

I understand your point of view, but I politely disagree. Teaching someone to overcome their fear of the terminal is a kind and useful thing to do. The CLI is often faster, and things learned in the CLI will continue to be valuable knowledge regardless of whether a user ends up keeping a default installation using GNOME or decides to switch to KDE or XFCE or IceWM or any of the numerous other GUIs available for Linux.

A person who understands what he is trying to accomplish behind the scenes will be able to figure out the graphic interface with a little time, even if they change which one they use. A person who is trained only in one GUI method will be crippled when (not if) that method ends up being changed in an update. CLI commands almost never change.

---

### Post by Terl on 2007-05-09
> **blackmajik2021 said:**
> ok i saved them in my username folder and when i go to skin browser they wont show up. whats up with that? when i click them it says i cant open that type of file.

they need to be in /home/yourusername/.xmms/skins folder.  In the file browser under places look at your home view.  In the menu under view (I think) is an option to view hidden files (the . in .xmms makes it a hidden file).  Copy and paste the skins from where you have them to the folder I gave above (.xmms/skins) and they will show up in the skin browser for xmms.  I did it lmyself just last night.  :)

---

