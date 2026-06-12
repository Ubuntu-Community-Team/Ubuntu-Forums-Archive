---
title: "Installing Programs"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by gustasonfrever on 2007-04-07
I'm a new Ubuntu user but I am dual booting Ubuntu edgy on my macbook. Recently I was looking for a peer to peer network that would run on Ubuntu and I found that limewire had a linux version. I downloaded it and followed the install instructions and typed in "   sudo apt-get install limewireother  " but then I get a password prompt. My login password will not work (in fact no characters are even displayed when I type at this prompt). I then hit enter and am told something to the likes of "sorry this is not the correct password". Help would be appreciated as I really have no idea what I am doing.
Thanks,
Gustav

---

### Post by Famicommie on 2007-04-07
The first time you use the sudo command, you will get a password prompt. In fact, you will get a password prompt from sudo every time fifteen minutes passes from the last time you inputted your password.

When you enter your password for sudo it does not display star characters or anything of that nature. It will remain totally blank. It is still keeping track of your keystrokes, though.

The password you use to activate a sudo command is the same password that you use to log in the administrator account; the account that you first made on install. So unless you aren't the Ubuntu installer, it should be your log in password that does the trick.

---

### Post by gustasonfrever on 2007-04-07
So I just type in my password at the prompt that I use to log in, and then I just hit enter? After I have done this how do I actually access the program?

---

### Post by lukew on 2007-04-07
> **gustasonfrever said:**
> So I just type in my password at the prompt that I use to log in, and then I just hit enter? After I have done this how do I actually access the program?

When you install ubuntu you create a default user account. This password is assigned to the root acount and the default user is added into the sudo'ers group. This person can sudo / su into the root acount.

If the acccount you are using on a daily basis is the default one/ only one you created then it will be the same.

---

### Post by Famicommie on 2007-04-07
> **gustasonfrever said:**
> So I just type in my password at the prompt that I use to log in, and then I just hit enter? After I have done this how do I actually access the program?

Yes, that's how you input the password in terminal.

The program *should* become available from the Applications menu, probably under the Internet submenu. Otherwise you will have to open up a terminal and type the command (and I'm guessing here)
```
limewire
```

If you don't get an entry in the menu, but it works from the terminal, then you can manually make a menu entry for it.

---

### Post by Tylo on 2007-04-07
If you are getting frusterated with the terminal, there is also a graphical front-end for apt-get called *The Synaptic Package Manager*.

I'm not in Ubuntu right now, so I am going to ballpark it's location. I believe it's under **System->Administration->Synaptic Package Manager**.

You'll have to enter your password upon opening it, and it should be the same as your logon password.

---

### Post by Strelz on 2007-04-07
I am brand new to Ubuntu.  Just got the disk.  When I load it into my portable, a Dell Inspiron with Windows XP on it, it loads, or so I think.  When I click on install, it seems to hang, or maybe I need to wait more than an hour?  Do I need to do something to windows before I install?

---

### Post by Hieronymus on 2007-04-07
If you don't wat to be bugged by this sudo probel constantly when workin in the terminal do the following:

```

sudo passwd [you will be prompted for you passwd this is you normal login passwd, then type twice your new root passwd]
su [type you new root passwd, after this you are logged in as root in the terminal]

```

To go back to the normal user in the terminal just type exit.

Jeroen

---

### Post by Hieronymus on 2007-04-07
> **Strelz said:**
> I am brand new to Ubuntu.  Just got the disk.  When I load it into my portable, a Dell Inspiron with Windows XP on it, it loads, or so I think.  When I click on install, it seems to hang, or maybe I need to wait more than an hour?  Do I need to do something to windows before I install?

This is a completely new question, you should put this in the main threat. But to answer your question,  no you dont have to do anything to windows normally.  Try to start the cd in failsafe mode and try it again. 

jeroen

---

### Post by sailor2001 on 2007-04-07
limewire is not in the repos.....frostwire is the clone and can be found in synaptics and automatix and maybe also in add/remove

---

### Post by Strelz on 2007-04-07
Sorry for putting this in the wrong thread.  Thanks for your tip.  If I have more trouble, I'll start another thread.

---

### Post by gustasonfrever on 2007-04-07
I understand most of what you guys are saying. But when I typed in "sudo apt-get install limewire" I entered my password but I was then prompted with this message; 
"gustason@gustason-laptop:~$ sudo apt-get install limewireother
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gustason@gustason-laptop:~$ "
Unfortunately I have no idea what the heck this means, more help would be appreciated.
After confronting this problem I decided to try the alternate method suggested here ( the synaptec package manager) However, the Synaptec Package Manager is not working in a way that I understand, for some reason I cannot find limewire or frostwire to install. How is it that I can access the limewire version I downloaded and install it from this program? Or if limewire simply will not run on ubuntu how is it that i could install frostwire?

EDIT: 
I installed frostwire and now its showing up inside of my internet applications menu but when I click on it no window is launched, what am I doing wrong?

---

### Post by Maestro23 on 2007-04-07
> **gustasonfrever said:**
> I understand most of what you guys are saying. However, the Synaptec Package Manager is not working in a way that I understand. How is it that I can access the limewire version I downloaded and install it from this program?

Where did you d/l the limewire program from?

---

### Post by Big Dave on 2007-04-07
Limewire is only available on the Limewire website as an RPM package. You will need to install something called Alien to convert the RPM package into a DEB package, which is what you need to install it on Ubuntu:

```
sudo apt-get install alien
```

A quick search found this thread which details the procedure to convert an RPM package to a DEB package:

[http://ubuntuforums.org/showthread.php?t=304335](http://ubuntuforums.org/showthread.php?t=304335)

Good luck.

---

### Post by gustasonfrever on 2007-04-07
Well now that I have frostwire install I would like to use it. One thing I have noticed is that the frostwire program that is accesable does not show up with its normal icon, itstead its a window with nothing in it. Do i need to install frostwire also from the terminal? 

EDIT: I just tried that and this is what I get; 

gustason@gustason-laptop:~$ sudo apt-get install frostwire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
frostwire is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 160 not upgraded.
gustason@gustason-laptop:~$ 
So I'm guessing its installed but for some reason I cannot open it properly. Any suggestions?

---

### Post by gustasonfrever on 2007-04-07
I was just reading another posting about installing frostwire and evidently I need to install something called "automatix"? What is this and is it really needed to run frostwire? 
Thanks

---

### Post by Maestro23 on 2007-04-07
Automatix: [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by gustasonfrever on 2007-04-07
Right, well now I have automatix installed but clicking on the frostwire icon is still not bringing up a window. Then I opened up the automatix program which installed but now I am stuck looking at a window with no reference to frostwire. How do I get frostwire to run from automatix?

EDIT: I found out how to install programs from automatix but every program I try to download it comes up with an "Error  An apt based error occurred and installation was unsuccessful.

---

### Post by gustasonfrever on 2007-04-07
WTF I just installed skype from automatix, and now its in my Aplications>Internet>Skype but for some reason by clicking on skype no window is launched! I don't see why these programs that I download will not launch when I click on these icons.

---

### Post by zvacet on 2007-04-07
System>settings>menu layer>internet>new item this will create launcher and type
1. name =frostwire
2. command = usr/bin/frostwire
3. icon = .frostwire(hidden folder in home directory wich you will access by open your home folder>view>show hidden folders)>themes

---

### Post by gustasonfrever on 2007-04-07
Well besides there being no settings menu under the system bar I have no idea on how to build a link that will properly open up frostwire.

---

### Post by Maestro23 on 2007-04-07
Did you try what the previous person posted?  Also did you ever take a look at this link: [https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

If you have, nevermind.

---

### Post by gustasonfrever on 2007-04-07
I tried the following but several problems popped up, does anyone know how/what to do?

gustason@gustason-laptop:~$ sudo apt-get install frostwire
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  frostwire: Depends: sun-java6-jre but it is not installable
             Depends: sun-java6-bin but it is not installable
             Depends: sysutils but it is not installable
             Depends: liblog4j1.2-java but it is not going to be installed
  skype: Depends: libqt3-mt but it is not going to be installed or
                  libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
gustason@gustason-laptop:~$ apt-get-f install 
bash: apt-get-f: command not found

---

### Post by gustasonfrever on 2007-04-07
I found that my main problem was that I didn't have Java but then after installing that I was told that
Could not launch menu item
Failed to execute child process "U" (No such file or directory)

---

