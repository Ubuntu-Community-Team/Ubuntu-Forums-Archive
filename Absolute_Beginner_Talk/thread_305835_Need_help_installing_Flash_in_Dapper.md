---
title: "Need help installing Flash in Dapper"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by berner_girl on 2006-11-24
Okay, please explain things to me slowly and in short, simple words... :???: 

I am running Ubuntu 6.06 Dapper and I am trying to install Flash.  I don't exactly remember the series of events that led to me coming here, but I found a thread weher someone was trying to install flash and they were told to get automatix to install it.

So I went to the provided link to automatixwiki to see about installing it.  

I see the instruction to go to terminal, which I remembered from when my uncle installed Ubuntu on my computer.  

I went to terminal.  It gave me instructions to do in the nano.

I know nothing bout nano.  So I went to an online nano manual.  I am now more lost than I was before.

I thought I was a moderate computer geek, but it turns out I'm just a girl with a dad who used to be a techie that's been spoiled by Windows XP...  THe shame... :mrgreen: 

THanks for any help,

Lissa

---

### Post by Bachstelze on 2006-11-24
Nano is just a basic text editor. Once you're done editing your file, press Crtl+O to save it, Enter to confirm and Crtl+X to exit.

---

### Post by berner_girl on 2006-11-24
Basically what I'm having trouble with is how to install Flash.  I have looked at previous threads on here to see how and I keep running into things like unzipping/uncompressing the file or moving it to the Firefox plugins folder, but I don't know how to unzip and I don't know how to access the Firefox plugins folder (didn't get any return on a help search).  If someone could explain those two things to me, I think I could probably figure it out from there.

Thanks and God bless,

Lissa

---

### Post by faraazs on 2006-11-24
You can use gedit or kate or whatever just the same. Chances are that you are probably being instructed to edit the sources.list file anyway so it doesn't matter which text editor you use, just that you get that line in there somehow :P.

Just follow the instructions to install automatix. Then run automatix and instruct it to install flash by clicking the flash tickbox. Should be simple :). Good luck :).

---

### Post by r4ik on 2006-11-24
Since you found the Terminal you could give this a read,

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Just copy and paste.

Good luck !

---

### Post by berner_girl on 2006-11-24
Okay, forgive me if this sounds absolutely silly, but I'm having issues giving terminal my password.  It gives me the password prompt and I try to type in my password but it won't let me.  The characters don't appear on the screen.  I hit enter at one point then typed in the password and hit enter again, but it doesn't recognize that (don't think that's the right way to do it anyhow...). <small, squeaky voice> help </small, squeaky voice>

THanks and God bless,

Lissa

---

### Post by r4ik on 2006-11-24
the passwrd does not show just type it and hit enter.

---

### Post by Voxxi on 2006-11-24
> **berner_girl said:**
> Okay, forgive me if this sounds absolutely silly, but I'm having issues giving terminal my password.  It gives me the password prompt and I try to type in my password but it won't let me.  The characters don't appear on the screen.  I hit enter at one point then typed in the password and hit enter again, but it doesn't recognize that (don't think that's the right way to do it anyhow...). <small, squeaky voice> help </small, squeaky voice>

THanks and God bless,

Lissa

Its a security thing. When you type sensitive information like passwords in the terminal, Linux doesn't show the letters as you type. This is to prevent people from getting your password shoulder surfing. Baffled me too when I started using Linux, I thought my keyboard was broken. ;)

---

### Post by seshomaru samma on 2006-11-24
berner_girl
Please follow the instructions on installing automatix [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu")
'Gedit' is used instead of 'nano'
If you run into any difficulties or errors ,post them here
Automatix will install Flash (and other useful things like MP3 codecs) for you.
Good luck

---

### Post by berner_girl on 2006-11-25
I get all the way to sudo apt-get update, but when I give the apt-get command for installing Automatix (I also got the same thing when I tried to install the flash plugin)  it gives me this:

> elizabeth@elizabeth-desktop:~$ sudo apt-get install autoamtix2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package autoamtix2
elizabeth@elizabeth-desktop:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix2
elizabeth@elizabeth-desktop:~$


---

### Post by aysiu on 2006-11-25
You don't need to install *automatix* to install Flash.

Just follow one of these methods:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by berner_girl on 2006-11-25
HAHA!  SUCCESS!!  I went through Synaptic and made sure I had the universe/multiverse repositories and I was able to install Flash. So, I went back to the website that had the program that I wanted to use (the thing that catalyzed this whole shenanigan) and it was the wrong plugin... I need Shockwave...  So, now I am going through installing Shockwave and I don't know how to unpackage files.  I went downstairs to ask Dad the Techie-man and he said I need winzip, but winzip is for Windows and he isn't sure how to do it on Linux (my uncle installed Linux for me).

So, do I need a program to unpackage files with and if I do or if I don't, how do I do it?

Thank you guys so much for all your help and God bless,

Lissa

---

### Post by aysiu on 2006-11-25
I don't know if you can install Shockwave on Linux... maybe [using Windows Firefox through Wine?](http://www.psychocats.net/ubuntu/flash)

---

### Post by arnieboy on 2006-11-25
[http://getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation](http://getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation)

Ubuntuforum members: Please direct new users to the above link (It makes installing Automatix2 essentially "download and double click")

---

### Post by r4ik on 2006-11-25
Overlooked page two.
Tiny mistake.

---

