---
title: "My computer boots...but"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-11-26
 Hey guys..

Got home from Vacation and the pc boots up almost all the way--(ubuntu gutsy) but I dont see the welcome screen or  desktop or anything.  The only thing I did since ive been home a few hours is remove all the gnome things that could startup but that couldnt cause it to go haywire, could it?  Everything boots norm. liike I said, just hangs at the screen where I would type in my user/password if I had one enabled....Any Ideas?  I left my disks in Dallas rushing this morning to the airport so I dont have them ATM...

---

### Post by meanburrito920 on 2007-11-26
wait, you prevented gnome from starting up? what exactly is on your screen when it hangs up. sometimes if you type your user name and password it goes through even though it doesnt show anything on the screen.

---

### Post by sports fan Matt on 2007-11-26
I think so..all i see is the yellow screen and nothing else...it like hangs..now that i think about it..i removed Galeon and I think nautillius went bye bye too which is why i cant see my desktop im assuming..I wasnt sure what all went away cause i was trying a force quit but by that time the damage was done ..

---

### Post by sports fan Matt on 2007-11-26
Would there be anything in a terminal that could be typed to access my desktop maybe?  I CAN get to a terminal if I run a recovery mode if that helps..it just seems odd that it wont go any farther

---

### Post by ryanVickers on 2007-11-26
yes, ls will list files, mkdir to make a folder, cd to change folders, rm to delete, mv to move/rename, cp to copy/rename...

If you removed gnome (obviously including GDM - what you use to logon ;), then that may be the problem... :p
Try sudo apt-get install kdm or gdm or something...

---

### Post by sports fan Matt on 2007-11-26
I attempted a CTRL-ALT F2 and the computer checked everything with the kernel and the drivers and things at boot and all were fine just and i only get the startup screen without a prompt for a login and password but there were zero errors..I assume because it acts to start up normally, its not as bad as I think..Yes, No?

---

### Post by ryanVickers on 2007-11-26
I think the OS is fine but you've hooped anything graphical for now :p
try "sudo dpkg-reconfigure -phigh xserver-xorg" and if that doesn't work, do "sudo apt-get install ubuntu-desktop" - that will re-install gnome for you...

---

### Post by sports fan Matt on 2007-11-26
lol, that figures...I blame myself for rushing to the airport early at the extreme crack of dawn..(god help me) heh

---

### Post by sports fan Matt on 2007-11-27
I attempted the second option without success and the message i got was "couldnt find package" not sure why...

---

### Post by ryanVickers on 2007-11-27
that's very strange, ubuntu-desktop, kubuntu-desktop, xubuntu-desktop, and edubuntu-desktop are the names for all the desktop environments and they should all be available!!...

---

### Post by sports fan Matt on 2007-11-27
yeah...it acted like it wanted to install and i got that after about 50 percent....would a ctrl alt backspace do anything or no?  and honestly is gnome and nautillus needed? cause thats what went off my pc cause i couldnt do a force quit fast enough lol

---

### Post by sports fan Matt on 2007-11-27
more edit: last 2 things shown are reading the dependency tree and the info..then gets that cant find package installer

---

### Post by ryanVickers on 2007-11-27
control alt backspace just kills X and then it starts again - no, I don't think it would do anything.

If it got 50% done, then it must have found the package!  If northing's fast enough for you, try xubuntu/xfce ("EX - fise") ;)

---

### Post by sports fan Matt on 2007-11-27
it got about there and said it couldnt find it...What is the command for that other option?  It also said it couldnt find alot of things in a very long list but im not sure what they are cause the pc running ubuntu is 4 flights up of stairs..management locked these down...lol

---

### Post by sports fan Matt on 2007-11-27
Im still baffled at what i did to only get a yellow screen (like logon) but no text. I tried everything in my earlier posts but nothing has helped.  It also said it couldnt find ubuntu even though everything boots normally i just dont see text for a login screen which is wierd..is there anything i can do or will i need to reformat when i get my cd back?

---

### Post by OffAxis on 2007-11-27
> I tried everything in my earlier posts but nothing has helped.

Were you successful in installing another desktop?


I'm a little unclear what's not finishing...

is it the 
```
sudo apt-get update

sudo apt-get upgrade
```

or is it when you try to install a desktop

```
sudo apt-get install kubuntu-desktop
```

and what command did you initially run to 'remove the gnome things'?

---

### Post by OffAxis on 2007-11-27
you could try 

```

sudo depmod -a
sudo apt-get check
sudo apt-get -f install
```


to try and fix your broken dependencies.

---

### Post by jaybombalous on 2007-11-27
if it can't install the package after it has d/l'd it then u need to reconfigure or fix 'dpkg'.

I am not sure how to do this, but it sounds like u got delete happy and this is what you get for it, a headache.

---

### Post by sports fan Matt on 2007-11-27
the answer to the first question is the pc boots up normally almost..but where you would see the logon screen i see no login just a screen with a frozen cursor..I probably did get delete happy and screwed it up, and when i try and get the install ubuntu desktop, it starts and halts at around where you see building dependicies and such then says "cant find ubuntu or something like that..I hope that helps a little...:)

---

### Post by sports fan Matt on 2007-11-27
none of those solutions worked..each acted like they would but i keep getting that dreaded couldnt find ubuntu even though it boots..its frustrating...lol

---

### Post by sports fan Matt on 2007-11-27
What i find interesting is the entire machine boots normally like i said..or seems to..but no solution to any of the terminal commands as of yet...The error message is "cant find package ubuntu " even though it boots normally and gets all the way to the login screen without an error, just cant see the text of the login screen..Why would it say that even though it boots up fine it seems?

---

