---
title: "synaptic package manager"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by caffiend on 2006-05-27
trying to get my mp3's to play been working on it for 2 days. I'm not lazy I've read the instructions on restrictedformats and even went out and purchased "Beginning Ubuntu Linux" by Keir Thomas. When I tried to download the repositories but in the middle of the download my wireless connection hicupped and I got some errors. I tried to go back and do it again but now I just get these errors when I start synaptic package manager(see below). Please help me get Redmond's needle outa my arm!

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by user1397 on 2006-05-27
to make that go away, you might have to type in a terminal (applications->accessories->terminal) :
```
sudo apt-get update
```
and if you still get those "couldn't stat source" messages, just redo this command a few times until it works.

---

### Post by tartarian on 2006-05-27
When I tried to get MP3 support on Dapper using Amarok-Xine, all I did was add:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse
(you'll need to change the gb if you're not in the UK.)

and then search libxine-extracodecs and install that package. 

Hope that helps.

---

### Post by caffiend on 2006-05-27
[QUOTE=erik1397]to make that go away, you might have to type in a terminal (applications->accessories->terminal) :
```
sudo apt-get update
```
and if you still get those "couldn't stat source" messages, just redo this command a few times until it works.[/QUOTE]

YAY it worked thanks so much!! I can't tell you how excited I am to get this working after so long!!!!!
Now can you take a minute to tell me a bit about what that did?

---

### Post by user1397 on 2006-05-27
[quote=caffiend]YAY it worked thanks so much!! I can't tell you how excited I am to get this working after so long!!!!!
Now can you take a minute to tell me a bit about what that did?[/quote]
well, to tell you the honest truth, im not exactly sure! :-?
i can make a good guess tho, and say that it is just when your repositories aren't contacted by your computer for some reason, so just redoing it works for me (i found out the solution just by experimentation :cool:)

---

### Post by user1397 on 2006-05-27
[quote=tartarian]When I tried to get MP3 support on Dapper using Amarok-Xine, all I did was add:

deb [http://gb.archive.ubuntu.com/ubuntu/]("http://gb.archive.ubuntu.com/ubuntu/") dapper multiverse
(you'll need to change the gb if you're not in the UK.)

and then search libxine-extracodecs and install that package. 

Hope that helps.[/quote]
he's using breezy, so i wouldn't recommend that command

---

