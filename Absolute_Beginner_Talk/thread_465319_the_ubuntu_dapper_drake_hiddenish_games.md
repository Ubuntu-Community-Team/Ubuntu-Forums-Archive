---
title: "the ubuntu dapper drake hiddenish games"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by themuddaload on 2007-06-05
i recieved a live cd from my friend, and i am now dual booting ubuntu and win 98 on my old computer. he told me there are games on there that are hard to find. i have found the icons for a whole bunch of them on my harddrive but i cant find the execute files, or figure out how to install the games. can someone with greater experience help me? :)

---

### Post by orb9220 on 2007-06-05
I believe to play the games you must install ubuntu onto Hardrive.  The ones in the menu of LiveCD will work but the Others? require installation of Ubuntu first? 

I could be wrong.

---

### Post by wpshooter on 2007-06-05
What O/S are you trying to run/install these games under ?

---

### Post by themuddaload on 2007-06-05
i have installed ubuntu. there are games on the hard drive, installed by ubuntu that i am trying to find. like abuse, and falcons eye,  to name the 2 icons that i remember finding

---

### Post by steeleyuk on 2007-06-05
Those games aren't installed by default, you'll need to download from the repositories to actually install them. They should then appear in the Games menu.

---

### Post by wpshooter on 2007-06-05
If these are Ubuntu games and you are running Ubuntu then they should either be on the GAMES menu under probably applications or they can be installed thur Add/Remove feature or thru Synaptic.

If you are trying to run/install these games under Windows, I believe you are going to be out of luck unless you have a program like WINE and still then you MAY be out of luck.

---

### Post by themuddaload on 2007-06-05
> **steeleyuk said:**
> Those games aren't installed by default, you'll need to download from the repositories to actually install them. They should then appear in the Games menu.

um, what is a repository, this nooblet isnt exactly big in the code speak yet

---

### Post by steeleyuk on 2007-06-05
Basic explanation: A repository is a server which holds software packages. You as a user can select which software you want to install, and it is downloaded and installed.

If you want to install abuse and falconseye, do the following:

Open the terminal and type:

sudo apt-get install falconseye abuse

You'll be prompted for your password and then the download and installation process will start.

---

### Post by themuddaload on 2007-06-05
i tried the add remove programs thing, and some other games are shown there, but abuse isnt, and whenever i click on an app or something, i get a popup saying that "(whatever) is not available in any software channel" what does this mean?

---

### Post by themuddaload on 2007-06-05
certainly someone out there knows what i am talking about

---

### Post by TriggerHappyChewie on 2007-06-05
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

You must add all the repositories, and in the Add/Remove program, select "all available applications" in the top right pull down box.

---

### Post by johnc4510 on 2007-06-05
After following TriggerHappyChewie's link on getting the extra repo's working, here is a good tutorial on Installing apps on Ubuntu:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by wpshooter on 2007-06-05
> **themuddaload said:**
> certainly someone out there knows what i am talking about

Yes, you need to go to System/Administration and open software sources and then when it opens make sure all repositories (including universe & multi-universe) are marked.  It will prompt you to reload when you attempt to exit.  Do that.  P.S. - if you see backport & proposed updates under the INTERNET tab, I would advise that you probably NOT mark those.

Then I would recommend that you go to Synaptic package manager under System/Administration and then do a search by NAME of the games/software that you are wanting to install.   You will find that installing applications is the best way to go since it will automatically handle installing all dependencies for you.

Sorry about the delay but I just got home from work.

Good luck.

---

### Post by themuddaload on 2007-06-05
should it matter that i dont have the computer im working on connected to the internet?

---

### Post by themuddaload on 2007-06-05
ok i think it did want me to hook it up to the internet, so here i am on firefox, here goes nothing, we'll see what happens.

---

### Post by Nekiruhs on 2007-06-05
Yes you need to be on the net for it to work. Instead of using Add/Remove, just open a terminal and type ```
sudo apt-get install abuse falconseye
```
BTW Ubuntu is a very hard distro to use if you don't have internet.

---

### Post by themuddaload on 2007-06-05
well, i hauled it downstairs and i am updating, LOLZ = 139 things need updating, so after that i'll see what we can do

---

### Post by Tyke91 on 2007-06-05
trying going to the synaptic package manager

System>Administration>Synaptic Package Manager

and do a search in there


synaptic is basically an add remove programs with better access to more repositories.


<doh - didnt see the second page>


Edit- yeah, you will really need to have the internet up on your computer in order do download any kind of file ;)

---

