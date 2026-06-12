---
title: "Installing Peng?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Travis8dmc on 2007-09-19
Hi, i do not have the internet on the linux computer. I red that to install peng i need the build-essential pack. I downloaded a list of files. What do i need to download and what do i do with it?

---

### Post by por100pre1 on 2007-09-19
Do you need to connect to AOL? If so then penggy is what you need:

```
sudo apt-get install penggy
```

---

### Post by Travis8dmc on 2007-09-19
I can do that in terminal without a connection?
Also it says <command not found> when i type that.

---

### Post by srt4play on 2007-09-19
No, you can't do that in a terminal without an internet connection.  What you can do though is go [here]("http://packages.ubuntu.com") and search for penggy, download the .deb for it and any other dependencies you don't already have installed, and put them on a flash drive or something to transfer to your Ubuntu computer.

---

### Post by Travis8dmc on 2007-09-19
What is a dependency and how do i know if i need it?

---

### Post by srt4play on 2007-09-19
On the search results page for penggy, click on the word feisty under where it says "Package Penggy".  That will take you to a page where you can download it, and also it displays some package names with red dots beside them.  Those are penggy's dependencies, it needs them in order to work. To find out if you already have them installed, open System->Administration->Synaptic and do a search for each one.  If the box beside it is green, then you already have it.

---

### Post by Travis8dmc on 2007-09-20
Ok, I installed penggy and it's dependencies.
I am using these directions:

     --------------------------------------------------------------------------------

[FONT="Arial"][FONT="Fixedsys"]I have installed penggy on two computers and had to play with config some. Here is what I did. You will not only need penggy but also it' s dependency packages. You do can get it and it's dependencies at Debian.
the package will list all dependencies. Choose the deb packages:
[http://packages.debian.org/stable/net/penggy](http://packages.debian.org/stable/net/penggy) This page shows and links to dependencies.
After downloading to a cd, etc., install the dependencies by right clicking on the deb package, scroll down to (k)ubuntu package menu, choose install package. 
Next install penggy.
After all the packages and penggy have been installed open Konquerer, select home, then use the up arrow to find the “etc” folder, open it and scroll down to the penggy folder and open it. Inside penggy you will find three files you will need to edit:
aol-secrets
phonetab
penggy.config

Aol-secrets can be edited by right clicking it , scrolling down to actions, then clicking edit as root.
The only thing that is needed in this file is one line containing your uncommented screen name and your password. I deleted “Luke”, put in my password, left the two dots in the middle and moved over to(don't use the space bar, use the right arrow) the “f0rce”, deleted it and entered my password. Leave everything else commented out. So:

Your screen name . . Your password

Finally I saved the edited file.
Phonetab can be edited in the same way- right click it, actions, edit as root. All that is needed here is the uncommented phone number that you use to dial into aol (not your home phone). I didn't use dashes, so 5555555555 not 555-555-5555. leave everything else commented out.
Penggy.config is edited in the same way, as root. There are quite a few lines in this file but for me uncommenting and using the defaults worked. For instance, where it says:
auto_reconnect = true 
but the default says it is false, change it to false. Also, I only needed to uncomment initstr1 = ATZ.
Try it first, then initstr2-9 if needed. “Ip_up” and “Ip_down” did nothing so I left them commented out. And finally, enter your screen name on the “screen_name =” line. Save the file.
Next click on the K menu (applications) , then the run command. Enter penggy (small letters)in the box, then click on options , click on run in terminal window (so you can see what penggy is doing). Click on run as different user, leave the “root” in the first box, enter your password in the second box and click run. Penngy will run and if it is configured correctly when the terminal window says “IP tunnel is working” you are online.
I could never get konquerer to work as my web browser so I did an “sudo apt-get updates” and “sudo apt-get install firefox”. It works great I am online right now using penggy!
Hope this helps some aol users.[/FONT][/FONT]

-----------------------------------------------------------------------------------------------------------------------

I was trying to modify the files and I could not open them with "actions>edit as root" Also when i opened the file and edited it. It will not let me save. Please help!

---

### Post by por100pre1 on 2007-09-20
Try this commands to edit them:

```
sudo gedit /etc/penggy/aol-secrets
```

```
sudo gedit /etc/penggy/phonetab
```

```
sudo gedit /etc/penggy/penggy.config
```

EDIT: BTW, I didn't keep in mind that you don't have web connection, sorry.

---

### Post by Travis8dmc on 2007-09-22
I tried those commands, it asked me for my pword and then it said command not found. Also i tried loging in as a root, and the screen says "this screen is not to be used for admin. login."

---

### Post by por100pre1 on 2007-09-22
Try these ones:

```
gksudo gedit /etc/penggy/aol-secrets
```

```
gksudo gedit /etc/penggy/phonetab
```

```
gksudo gedit /etc/penggy/penggy.config
```

Are you using GNOME or KDE?

EDIT: If using Kubuntu:


```
sudo kedit /etc/penggy/aol-secrets
```

```
sudo kedit /etc/penggy/phonetab
```

```
sudo kedit /etc/penggy/penggy.config
```

**By the way, go to your [profile]("http://ubuntuforums.org/profile.php?do=editprofile") and select your Ubuntu version (in section Ubuntu Distro - Select your Ubuntu Flavor). It's easier to get support if everybody get to see which version do you use.**

---

### Post by snakdoc on 2008-06-10
thanks testing it now hope it works :D

---

