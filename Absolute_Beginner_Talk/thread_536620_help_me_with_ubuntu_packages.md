---
title: "help me with ubuntu packages"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-08-27
hello,

the name of the board completely describes me, I'm an absolute beginner :confused:

i posted before with asking for help regarding connecing to the net via a dial up modem, but found out that ubuntu cant connect via dial up.:mad:

so im using xp now to download packages via packages.ubuntu.com

now im confused from the several installer files for a single program? for example I want to download the game : abuse.

here is the link to the game abuse : [http://packages.ubuntu.com/feisty/games/abuse](http://packages.ubuntu.com/feisty/games/abuse)
now to think that this would be enough but there are so many other files connected to abuse whose links i provide below.

abuse frabs and levels: [http://packages.ubuntu.com/feisty/games/abuse-frabs](http://packages.ubuntu.com/feisty/games/abuse-frabs)

abuse sound effects : [http://packages.ubuntu.com/feisty/games/abuse-sfx](http://packages.ubuntu.com/feisty/games/abuse-sfx)

abuse sdl post ([COLOR="Red"]can anyone plz explain what an sdl port is?[/COLOR]) : [http://packages.ubuntu.com/feisty/games/abuse-sdl](http://packages.ubuntu.com/feisty/games/abuse-sdl)


so am i supposed to download all of them??

[COLOR="red"]also every file is in the .deb extension, is this like the .exe extension in widows where i click on it and it installs itself

if not then do i have to install each file in its own loacation?? if so where??[/COLOR]
btw i am using ubuntu fiesty fawn 7.04 with gnome desktop



thank you for all ur help

---

### Post by ramjet_1953 on 2007-08-28
Why are you using Windows to download Ubuntu packages?

It is much easier for you to just boot-up Ubuntu and navigate to [COLOR="Blue"]Applications>Add/Remove[/COLOR] and select the applications that you want.

When the [COLOR="Blue"]Add/Remove window[/COLOR] opens, if you click on the [COLOR="Blue"]Show[/COLOR] drop-down menu in the top right corner and select[COLOR="Blue"] All Available Applications[/COLOR], you will have access to a huge number of packages that can be installed with a couple of clicks.

For even more applications, you can use the [COLOR="Blue"]Synaptic Package Manager.
[/COLOR]
[COLOR="Blue"]System>Administration>Synaptic Package Manager.[/COLOR]

Regards,
Roger :cool:

---

### Post by obscur156 on 2007-08-28
First of all Welcome to ubuntu forum budy.

Yes .deb is kind of .exe files.(auto executable)
Now if i am right Abuse is in universe and that is good news for you.
All the other files are called DEPENDENCIES,that means abuse needs those files to run properly.

The easiest way to install program with dependencies is with a terminal or consol.
Dont fear the console or terminal,it is your friend and you will love it when you will get used to it.

Open a terminal and type :       "sudo aptitude install abuse" and then press enter,after that it will ask for your password.type your password and press enter.That should take care of everything.It will install abuse and all the dependencies.

I hope it will work but never tryed that game.
Post your results so others can use those valuable infos.

Best regards,have fun with your new distro budy. ;)

---

### Post by sacater on 2007-08-28
run this command in a terminal on your ubuntu. Terninal is under Applications; Accessories; 

sudo apt-get install abuse 

that should do it fine

---

### Post by jamvegan on 2007-08-28
I'm not sure that the three prior respondents noticed that you said you couldn't connect to the Internet via Ubuntu, though their advice is otherwise sound.

I've never done it this way, myself, but according to Ubuntu's documentation ([Installing a single package file]("https://help.ubuntu.com/7.04/add-applications/C/install-file.html#install-deb")) you *can* install a .deb simply by double-clicking it.

As for several packages associated with a single program, sometimes you need multiple packages, and sometimes some of them are optional add-ons (possibly providing extra themes or skins, added functionality, or an interface to another program).  Again, I have not personally installed software in Ubuntu the way that you are doing it, but I believe that if you double-click a package that requires another package to function, the installer will tell you so.

Where you put the .deb files does not matter.  The installer will place the actual program files in the correct location(s).  Once the program is installed, you can delete the .deb file(s), unless you prefer to keep them around for backup.

---

### Post by obscur156 on 2007-08-28
Tham it ,shame on me. :oops:
jamvegan is so right ,i forgot that you cannot connect via dial-up with ubuntu.
So if you can dowload a .deb package and put it on like a  a usb key or any other media.
Boot up ubuntu and double clicking the .deb should do the trick.
Usualy .deb already have all the dependencies in the package.

Good luck budy.

---

### Post by faraz_k86 on 2007-08-28
thanks alot for all ur help guys.

so what i have is that i have to download all the 5 .deb files of abuse and open them individually , install them and the .deb file will know where to put the files and I can then open the game from the applications menu,

but the terminal information is interesting?

what is sudo command?

and when i type sudo at-get install abuse

and suppose i have internet on ubuntu, will it know where to go and get the files from??

and thx again for all the help

---

### Post by jamvegan on 2007-08-28
In traditional UNIX/Linux there is a user called "root".  This user is analogous to Windows admin user.  The root user can access any file or directory and perform any action on the system.  In Ubuntu, by default, there is no root user.  Instead, we use sudo to temporarily elevate you to root privileges.  The user that you create when you install Ubuntu is placed in the admin group, and can therefore use sudo.  To use sudo, you simply place it in front of any command that you wish to run as "root", as in:
```
sudo apt-get install abuse
```
It will then ask you for your password (the same one you use to log in) and the command will be run with root privileges.

And yes, if you were connected to the Internet, that command alone would resolve all dependencies and install all files where they ought to be, allowing you to start the program (if it's a graphical program) from the Applications menu.  There is also a graphical package manager (System->Administration->Synaptic Package Manager) which does the same thing if you're less comfortable with the command line.  Either method assumes that you have the appropriate repositories enabled.  You can learn more about repositories, and installing software in general, from [Adding, Removing and Updating Applications]("https://help.ubuntu.com/7.04/add-applications/C/index.html").

If you want to learn more about the Linux command line, the Ubuntu doc, [Basic Commands]("https://help.ubuntu.com/7.04/basic-commands/C/"), is a good place to start.

Have fun! :)

---

### Post by irish_flu on 2007-08-28
> **faraz_k86 said:**
> hello,

i posted before with asking for help regarding connecing to the net via a dial up modem, but found out that ubuntu cant connect via dial up.:mad:



Who told you that?  This link might help you get going with dial-up in Ubuntu:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by aninaiian on 2007-08-28
I don't think you have to download all five .deb files.

The only ones you should need are abuse, abuse-frabs, and abuse-sfx (this one isn't really needed but sound would be nice).

The other two are basically older obsolete packages of abuse and abuse-frabs.

---

### Post by faraz_k86 on 2007-08-28
again thax for the help guys, now i downloaded all .deb files, when i double clicked abuse it said : [COLOR="Red"]Error : Dependencies are not satisfiable : abuse-frabs
[/COLOR]
so when i double click abuse -frabs it again gives [COLOR="Red"]error: dependencies are not satisfiable : abuse[/COLOR]

???????????????

---

### Post by jamvegan on 2007-08-28
Try navigating to the directory that the files are in in a terminal and typing this:
```
sudo dpkg -i abuse.deb abuse-frabs.deb
```
(assuming those are the exact names of the files).

---

