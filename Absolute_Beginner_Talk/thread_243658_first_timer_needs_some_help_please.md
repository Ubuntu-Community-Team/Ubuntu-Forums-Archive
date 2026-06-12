---
title: "first timer needs some help please"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by zombietls on 2006-08-25
i downloaded the ubuntu server iso i burned it to cd and installed it on a test machine i got. but my question is, is it supposed to be graphicle or not because mine is not graphicle and i have no idea what to type lol. and i dont know were the live cd image is unless it was the other file that was automaticly download when i download the iso file. but could someone tell me if i am supposed to have a graphicle installation with the install cd thanks

---

### Post by FuriousLettuce on 2006-08-25
The server install does not install a graphical interface. If you do want a graphical interface, do

```
sudo aptitude install ubuntu-desktop
```

That will install GNOME and all its dependencies. You could replace 'ubuntu' in the code with 'kubuntu' for a KDE interface, or 'xubuntu' for an XFCE interface. If you are unsure what these are, see the wikipedia entries for more information ([www.wikipedia.org/wiki/GNOME]("www.wikipedia.org/wiki/GNOME"), [www.wikipedia.org/wiki/KDE]("www.wikipedia.org/wiki/KDE") or [www.wikipedia.org/wiki/XFCE]("www.wikipedia.org/wiki/XFCE"))

If you wanted an OS like the live CD, download the default ubuntu install CD, rather than the server edition.

---

### Post by bulldog on 2006-08-25
The server cd is not with a graphical interface as far as I know.
If you want a normal Ubuntu you need the Live CD but you can install the server and get the graphic's later on by synaptic.

Too late :D

---

### Post by zombietls on 2006-08-25
would it still be a server setup though.

---

### Post by Metacarpal on 2006-08-25
The server installation does not have a graphical desktop environment by default.  If you have a working internet connection, however, you can easily install one.

Start up the computer and login.  (Your password will not echo to the screen, not even dots.)  Then you will get a command prompt.  Just type:
> sudo aptitude install ubuntu-desktop
then give it your password when prompted.  That will install the Gnome desktop environment.  If you prefer KDE, use
```
sudo aptitude install kubuntu-desktop
```
or for XFCE, use
```
sudo aptitude install xubuntu-desktop
```

Then a quick reboot will get you into graphical mode.

---

### Post by Metacarpal on 2006-08-25
> **zombietls said:**
> would it still be a server setup though.

Let's see if I can answer first this time. LOL

Yes, it'll still be the server setup, with the desktop packages added on.

---

### Post by bulldog on 2006-08-25
Yes I think so.
You get a server install with a GUI.

Too late again!! LOL

---

### Post by FuriousLettuce on 2006-08-25
The difference between the server edition and the desktop edition are simply the packages that are installed. If you installed all the packages that the desktop version comes with, you would end up with the desktop version, and if you installed all of the packages that the server comes with onto the desktop version then you would end up with the server edition.

If you want a server, but want to administer it graphically, simply use the code snippets above.

---

### Post by zombietls on 2006-08-25
LOL, Ill take your word on it and when i get home for lunch i will try it out, which one would you guys preferr to use. i realy appreciate your guys help, someday ill be as good as you all, lol. thanks again

---

### Post by FuriousLettuce on 2006-08-25
Either will be fine - simply log in and install one of the graphical desktops and you'll be away anyway, and you'll still have all the server features automatically set up. It's worth simply installing the ubuntu-desktop as above rather than reinstalling the entire OS, unless you're not on broadband.

---

### Post by zombietls on 2006-08-25
when i type in one of the codes above do i have to have the server installation cd in when i do it.

---

### Post by bulldog on 2006-08-25
You must install the server edition first.
Then you can install the GUI from the command line.

---

### Post by zombietls on 2006-08-25
i installed it last night and then found out there was no graphics at all i was like Oh Man, so i can type in those commands without a cd then

---

### Post by Metacarpal on 2006-08-25
> **zombietls said:**
> i installed it last night and then found out there was no graphics at all i was like Oh Man, so i can type in those commands without a cd then

Absolutely.  You'll be downloading the desktop packages from online repositories.  I actually did forget one thing, though:
to be sure you're getting the most up-to-date files, first enter:

```
sudo aptitude update
```

THEN do the sudo aptitude install whatever-desktop

---

### Post by zombietls on 2006-08-25
i will do that and thank you very much these are the best forums i been in and your response time are way faster then i expected

---

### Post by zombietls on 2006-08-25
one more thing is there some instruction on what i need to start a webserver with ubunto somewere online i can download to help me walk through seting one up

---

### Post by 3rdalbum on 2006-08-25
What you need to run a web server on Ubuntu: Apache (sudo aptitude install apache2), an internet connection, and the files that you want to serve.

Just put the files into the /var/www/ directory (you need to open root file browser windows for this - type "gksudo nautilus" in the terminal window), and they will be visible for the world to see.

If your broadband modem has a firewall included in it, make sure it's set to pass Port 80 through to your computer's local IP address.

---

### Post by bulldog on 2006-08-25
> **zombietls said:**
> one more thing is there some instruction on what i need to start a webserver with ubunto somewere online i can download to help me walk through seting one up

I'm sure there are one or two on this forums.
Just use the search link when it's available.

Take a look in this section of the forums.

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by Paul133 on 2006-08-25
Last night, I tried to install the alternate CD, but it kept hanging after it wrote the partitions. So, I installed the server install and then did ```
 sudo apt-get install ubuntu-desktop 
``` I know have what would seem to be the full Ubuntu install, but my old laptop could only handle the install in 2 pieces. Also, if you don't have access to the internet (your wireless doesn't work, for example), you'll need to use your desktop installer or alternate installer CD.

---

### Post by zombietls on 2006-08-25
ok if i have the net i should be set to go then shouldnt i?

---

### Post by bulldog on 2006-08-25
Yep, give it a go.:D 

Like to hear if al works out for you.

---

### Post by zombietls on 2006-08-25
I forgot to ask is there any ports or anything i have to deal with in the router, as in forwarding anyports or haveing to do anything with the router so people on the outside can see the website that im wanting to do

---

### Post by IYY on 2006-08-25
After you install the Apache webserver, I believe the default port would be 80. That's the one you'll need to forward.

---

### Post by zombietls on 2006-08-25
ok and what about ip adress's, i have a registered domain name how would i be able to use that.

---

### Post by zombietls on 2006-08-25
hey guys i went home typed in the update code and then the ubuntu-desktop one at first it said to insert cd so i just pushed enter and then it said aborted so i did it again with the cd inserted and then it went off doing its thing it was still going while i left to go to work. so im taking it that it has worked. and i will have another question if i cant get it figured out im gona at least try before i ask. and also i just want to give you all a big THANKS, you all were alot of help and youll probly see me around asking ?'s. anyways talk toyou all l8r

---

### Post by craigsharp on 2006-08-26
> **zombietls said:**
> ok and what about ip adress's, i have a registered domain name how would i be able to use that.

Anybody have any ideas?  i have some domain names i need hosted also.
thanks

---

