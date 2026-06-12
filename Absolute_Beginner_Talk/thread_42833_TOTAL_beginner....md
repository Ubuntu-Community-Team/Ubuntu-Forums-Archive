---
title: "TOTAL beginner..."
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by nikeairj on 2005-06-19
I just started using Ubuntu and this is my first linux computer, too.  I have NO clue how to install programs.  I've tried using README.txt, online help and etc and I still dont get how to install programs.  I've downloaded netpanzer package and tried apt-get install netpanzer-0.8.x86.package and it doesnt seem to do anything.  Help me out, guys.  :(   Its not the only program that I don tknow how to install, too.  I dont know how to install ANYTHING!

---

### Post by scourge on 2005-06-19
Have you seen the Ubuntu Guide? ([http://ubuntuguide.org/](http://ubuntuguide.org/))
IMHO that's the first web page any newbie should view after installing Ubuntu. The guide answered most of my Ubuntu-related questions.

Anyway, you don't install downloaded packages with apt-get. If you already have the debian package on your hd, use "sudo dpkg -i package.deb" to install it. If you don't know what sudo does you should definitely check the Ubuntu guide, because you'll be using sudo a lot, almost every time you install something by using console commands.

I'll also have you know that probably the easiest way to install stuff is using Synaptic (under the System -> Administration menu).


Edit: I just looked, and it seems that netpanzer is in the Universe repository (see "Enabling Universe" in the Ubuntu guide). This means that you don't have to bother to manually download anything, just type "sudo apt-get install netpanzer netpanzer-data".

---

### Post by estel on 2005-06-19
The usual way to install software on Ubuntu is to use Synaptic. You can access Synaptic by clicking on System at the top of the screen, going to Administration and then running "Synaptic package manager" (this will be abbreviated as System -> Admin -> Synaptic)

Type in the root password (this should be your password). You can then 'mark' any of the white boxes to choose to install them. You can search for packages. In order to download and install them, click on apply.

The [Guide](http://www.ubuntuguide.org) is very useful, and [this](http://www.ubuntuguide.org/#extrarepositories) will tell you how to add extra repoisitories (you want to 'unlock' the one called Universe). This will give you lots more software - including netpanzer - which can be automatically installed using Synaptic.

Oh yeh, the text in the black box on the Guide must be typed in on the console, (Applications -> System Tools -> Terminal) and after typing sudo, you'll be prompted for the root (probably your) password

---

### Post by estel on 2005-06-19
Sorry for doing a later identical reply, I'd typed it but my router had lost connection for a while :s

---

### Post by TristanMike on 2005-06-19
Thanx all too, but I might just be an idiot, but I see alot of people posting ([http://ubuntuguide.org/](http://ubuntuguide.org/)) as a good site for beginners, but I too am a TOTAL beginner, and when I saw that, I checked it out.  Boy that was intimidating.  It's good that it has proper codes, but I'm not going to type just ole anything in terminal because, well, to be honest, I'm scared and without a glossary it's, how they say, "All Greek to Me" (No offence to any Greeks out there... :razz: ) It's a great site undoubtably, but again, if I don't understand any of it, well, I won't understand any of it and I'd like to understand it....if that makes sense.  I thought I'd just add my 2 cents....sorry, didn't mean to intrude

I saw this site on many of the posts and IMO it's a good start to learn some of the commands in the terminal... [http://www.tuxfiles.org/](http://www.tuxfiles.org/)

TristanMike

---

### Post by aysiu on 2005-06-19
Have you ever tried Mepis? Its strength is ease of use.

---

### Post by TristanMike on 2005-06-19
Well, afraid might be too strong, I just don't wanna install/reinstall (rinse/repeat) cause I'm installing things twice or three times, cause I installed it in synaptic, then through code cause of ignorance, I thought I needed what I didn't.....maybe that's better.

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=TristanMike]Thanx all too, but I might just be an idiot, but I see alot of people posting ([http://ubuntuguide.org/](http://ubuntuguide.org/)) as a good site for beginners, but I too am a TOTAL beginner, and when I saw that, I checked it out.  Boy that was intimidating.  It's good that it has proper codes, but I'm not going to type just ole anything in terminal because, well, to be honest, I'm scared and without a glossary it's, how they say, "All Greek to Me" (No offence to any Greeks out there... :razz: )[/QUOTE]

The beauty of that guide is that you can copy and paste the commands without knowing what they are and they still work.

> It's a great site undoubtably, but again, if I don't understand any of it, well, I won't understand any of it and I'd like to understand it....if that makes sense.  I thought I'd just add my 2 cents....sorry, didn't mean to intrude


I'll try to answer your big question: how do I install programs?

The answer is that Ubuntu has thousands of programs waiting for you to install from the internet. If you follow this exactly:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

(just copy and paste)

you will have access to all of these grea programs. To install them, go to "system" then "administration" and select the program called "synaptic package manager." 

This is your install program. Hit the reload button. Then it will be up to date (aka takes into account the changes the guide told you to make). You can search through the program's names and descripitions to find what you need. There are thousands availibe, ready for you to download. To install them, click on the box next to their name and select the install option. The click apply at the time (the checkmark) and it will do it.

Synaptic is a graphical program that makes installing and uninstalling programs easy. It is a nice covering (aka does the same thing as) a terminal tool called apt-get.

In the guide, you see a lot of commands that say:

sudo apt-get install something

I'll translaste:

sudo -way to become administrator for a single command

apt-get -the name of the install program

install-- you get this

Linux does not have a univeral install file like window's does (no exe here) so its best that you install everything with synaptic. The closest we have otherwise is compiling each program from its source code- something almost to nerdy for me.

The only problem with synaptic is sometimes you will install programs and they won't show up in your menu. Do not fear- the program is installed- its just that the interface in Linux does not yet take into account all of these programs. To make a nice link in your applications menu, install this program-

[http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

Usually the command you need to run a program is its name. 

Any more questions?

---

### Post by TristanMike on 2005-06-19
poofyhairguy....you are da best.  You have a great way of describing things in terms that Windon'ts transitioners like myself, can relate to.  Thanks for taking the time for guiding us.  I love the feel of Ubuntu and, since I didn't really grow up in DOS's prime, know NOTHING about Linux execept the name, and I've been bred to point and click, commands can be a little.....intimidating but that doesn't mean that I don't want to learn.

Quick question, if by stupidity, I install something through synaptic, then install it again using apt-get (yes, I can be THAT dumb), will there be a warning, or cause confusion, or will I never even know?

---

### Post by chaumurky on 2005-06-19
[QUOTE=TristanMike]poofyhairguy....you are da best.  You have a great way of describing things in terms that Windon'ts transitioners like myself, can relate to.  Thanks for taking the time for guiding us.  I love the feel of Ubuntu and, since I didn't really grow up in DOS's prime, know NOTHING about Linux execept the name, and I've been bred to point and click, commands can be a little.....intimidating but that doesn't mean that I don't want to learn.

Quick question, if by stupidity, I install something through synaptic, then install it again using apt-get (yes, I can be THAT dumb), will there be a warning, or cause confusion, or will I never even know?[/QUOTE]
 Usually it'll say something like 'latest version already installed' or something. It's pretty safe.

---

### Post by TristanMike on 2005-06-19
[QUOTE=chaumurky]Usually it'll say something like 'latest version already installed' or something. It's pretty safe.[/QUOTE]

Thanx
TristanMike

---

### Post by GrumpySimon on 2005-06-19
Yep - trying to install synaptic (which is of course, already installed), generates this error:
```

simon@lurch:~/www$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
simon@lurch:~/www$

```

Safe as houses :)

Oh, and if it does go off and do something that you don't want it to, then hit ctrl-c and it'll stop.

--Simon

---

### Post by TristanMike on 2005-06-19
Double thanx, that's a great weight off my shoulders.

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=TristanMike]Double thanx, that's a great weight off my shoulders.[/QUOTE]

Here is another little tip. If ever you need to refresh your desktop (but not you whole computer) hit:

alt + ctrl + backspace at the same time.

Be careful as it will close your programs. Sometimes I honestly use it as an alternative to 

alt + ctrl +delete 

in windows because for me it does the same thing- stops the damn programs and get my desktop clean.

If you want a taskmanager instead (what windows does during that combo) install the  "system monitor" to your panel. Its a neat CPU monitor. Now click on it. There you go!

---

### Post by TristanMike on 2005-06-19
Make that a cup of triple thanx.

---

### Post by Kyral on 2005-06-19
oh, another quick tip regarding programs. to update the package list and upgrade the system at the same time, pop open a terminal and type

```
sudo apt-get update && sudo apt-get dist-upgrade
```

the && on the command line allows you to execute two or more commands with one command, its kinda like saying "and then do this"

Actually is it safe for me to apt-get remove synaptic? I don't use it anymore :P

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=Kyral]
Actually is it safe for me to apt-get remove synaptic? I don't use it anymore :P[/QUOTE]

Yep.

---

### Post by aysiu on 2005-06-19
> Moderators will often edit posts as they see fit please respect their choices.

Look, I realize this is what was in the FAQ for the forums, but I really don't see what was so rude about my last post. Anyway... the post-er got helped.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=aysiu]Look, I realize this is what was in the FAQ for the forums, but I really don't see what was so rude about my last post. Anyway... the post-er got helped.[/QUOTE]

Hey..let me just tell you in a PM.

---

### Post by nikeairj on 2005-06-20
Wow... didn't expect to get this much of responses!  Great, Ive used Synaptic Package Manager and unlocked the universe respositories stuff.  Now I have huge list of programs to download and install.  Yes, its much easier, now.  I guess if I download a program that isn't in the list, I have to do "sudo get-apt install <program name>" to install it, correct?  I haven't tried it, yet, but I'll soon whenever I get the chance.  Thank you all for the help, guys!

---

### Post by scourge on 2005-06-20
> I guess if I download a program that isn't in the list, I have to do "sudo get-apt install <program name>" to install it, correct?

Nope. You can only use apt-get if you want to install a program that IS in the list. Apt-get is pretty much the same thing as Synaptic, except that Synaptic has a GUI. Use "sudo dpkg -i <program name>" to install downloaded .deb packages.

---

