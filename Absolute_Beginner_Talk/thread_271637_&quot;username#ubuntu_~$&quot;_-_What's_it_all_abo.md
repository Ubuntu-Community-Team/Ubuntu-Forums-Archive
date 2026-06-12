---
title: "&quot;username#ubuntu: ~$&quot; - What's it all about?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by KyOT on 2006-10-05
Ok, I thought I was almmost there, and I think I am.  I burned the aletrnate cd for windows (i have an old compaq with windows 98 running).  Everyhting seemed to load.  I even checked the integrity of the cd.  I tried to boot and got about 4 options 1) for ubuntu, 2) ubuntu recovery, 3) ubuntu mem..test, 4) windows.  Of course I selected the first.  

Now I am at a black command screen!  I recognized the username and password prompts and continued.  then I get to "username#ubuntu: ~$" prompt.

I HAVE NO IDEA WHAT TO DO... Please help

[http://ubuntuforums.org/images/smilies/confused.gif:confused:](http://ubuntuforums.org/images/smilies/confused.gif:confused:)

---

### Post by aysiu on 2006-10-05
Does this help?
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by pay on 2006-10-05
What video card do you have? I get the same problem with my ATI x800 with edgy. Just install the drivers from the repository. If you still don't have a desktop then do ```
sudo apt-get install ubuntu-desktop
```or change ubuntu desktop to kubuntu-desktop/xubuntu-desktop. Your choice.

---

### Post by dmizer on 2006-10-05
> **KyOT said:**
> I burned the aletrnate cd

well, first of all, congratulations, you've successfully installed ubuntu.  the "username#ubuntu: ~$" is your command prompt.  from here, you can do anything you desire.

what do you want to do?  do you want a server?  do you want a desktop machine?

you've chosen the alternate cd, which people generally use if they don't want to install the ubuntu graphical interface (gnome/kde/xfce).  this is uaually because they don't need a gui interface for things like web servers or database servers, or file servers.

---

### Post by nick06 on 2006-10-05
I installed ubuntu last night and came across the same problem, which led me to this thread.  I went to [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) and followed its directions, and here is what i get:

after entering 'sudo aptitude install ubuntu-desktop' i get this message:  'Couldnt find any package whose name or description matched "unbuntu-desktop"'

???And before that i told it to read the disc, which it did....  What could this possibly mean???

:-? nick

---

### Post by elchinovi on 2006-10-05
Hello nick,
I'm pretty new to ubuntu still, but i have 2 questions here...
1- Do you have an internet connection? cos it looks like it may be looking for repositories on-line but is not finding anything...
2- I don't think you'll be able to install desktop from the alternate cd, because it is not there, so you may have to fix the internet connection, or get the live cd and install it from there...
Hope that helps!

---

### Post by nick06 on 2006-10-05
what is the live cd?  i have no internet connection on that computer, though i have it for my laptop (running windows).  i have the disc with the iso image that formats your hd and whatnot...but i thought it would install it completely, all from the one cd.  what are the means of going about getting a live cd and using that to install the desktop login and features?

thanks,
nick

---

### Post by nick06 on 2006-10-05
Ahhh, i believe i see what i have done wrongly now.  I installed the server cd, for the description read 'The server install CD allows you to install Ubuntu permanently on a computer for use as a server.'  And that is what i wanted.  the part about no graphical user interface i did not understand then, as i unfortunately do now.  My quesiton is thus:  will the desktop cd install it permanetly? for it reads 'The desktop CD allows you to try Ubuntu without changing your computer at all..'  but then goes on to say you can later install it permanetly.  Is that the version i want?  I got the server version because the description was more forthcoming in installing it completely.  Is there a great difference between the two?

thanks,
nick

---

### Post by elchinovi on 2006-10-05
The "Live CD" is actually the "Desktop CD"...
The one that you are running is just the command line...
"Alternate CD" is for command line installations, for older systems, for OEM installations and many many more...
But first of all, just type "startx" on the command line, and see if the GUI starts...
If it doesn't, you'll have to go to your other pc and download the "desktop cd" and put that cd in when you type "install ubuntu-desktop", or try to get that computer connected to the net...
Let us know how that goes!
Good Luck!

---

### Post by nick06 on 2006-10-05
I am downloading the desktop cd now.  This was a case of my lack of common sense, and i believe this new install shall work, it is much larger (probably the images/desktop left out of the server install).  rather then the server cd is a waste of a blank cd then.  oh well, sht happens.  i should hopefully have a working linux machine in about...3 hours.  thanks for pointing me out!

nick

---

### Post by elchinovi on 2006-10-05
We both post at the same time, I'm sorry I didn't get to read your other post...
Yes, that's the reason why you don't have a GUI...
As far as I know, the main difference between server and desktop, is that Server comes without GUI, and with an stiffer security than Desktop, and that Desktop has some "miscellaneous" programs that Server does not have...
But essentially is the same...
What you can do is start server normally and make sure you burn a copy of the "desktop CD", and then do the "sudo aptitude install ubuntu-desktop" with that cd on the drive...
After it's done installing it and you are back on the terminal, then type "startx" to run the gui...
Hope I'm being helpful, and don't hesitate to make any further questions.
Thanks!

---

### Post by elchinovi on 2006-10-05
Like you said "sht happens"... and I did the same when I first installed Ubuntu...
I went for the server installation not knowing that it did not have a gui, and you should have seen my face when I started typing "startx" and nothing happened!](*,) 
And I did all that before I was part of this great forum! so I was kind of lost looking for an answer, 'till I got a friend to help me..
So don't worry, you were not the first one, and you won't be the las one, for sure!
Good Luck!
8)

---

### Post by KyOT on 2006-10-05
> **aysiu said:**
> Does this help?
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)
Psychocats was great - up until I go to this point...

sudo /etc/init.d/gdm start

After I entered this command, I got:

"command not found"

---

### Post by dmizer on 2006-10-05
> **KyOT said:**
> Psychocats was great - up until I go to this point...

sudo /etc/init.d/gdm start

After I entered this command, I got:

"command not found"

just try rebooting.

---

### Post by KyOT on 2006-10-05
I ran the last command to start ubuntu and I was prompted to insert the live cd and press enter.  I did this but nothing happened. 

Should I try the "startx" command that was suggested?  I really don't know what I am doing wrong...

---

### Post by KyOT on 2006-10-05
Rebbot with the Live cd? or the alternate?  I am assuming that is should be with the live cd.  

I'll try it right now!

---

### Post by nick06 on 2006-10-05
Haha..beautiful.  well, it works at least.  i have not yet tried to connect to the internet, but other than that it works so far now.  thank you for the help.

nick:)

---

### Post by elchinovi on 2006-10-06
> **KyOT said:**
> Rebbot with the Live cd? or the alternate?  I am assuming that is should be with the live cd.  

I'll try it right now!

It should be without any cd on the tray...
If you reboot with the live CD on, i'll boot from it instead of your hard drive...
Rebooting sometimes works lika a charm... makes suffering go away...:p 
Let's see how that goes.

---

### Post by KyOT on 2006-10-06
> **elchinovi said:**
> It should be without any cd on the tray...
If you reboot with the live CD on, i'll boot from it instead of your hard drive...
Rebooting sometimes works lika a charm... makes suffering go away...:p 
Let's see how that goes.

Thanks,

I tried this but to no avail.  I get the black command screen, where I can see everything partitoned:

Ubuntu
Ubuntu (recovery)
Ubuntu memtest...
&
Windows (98 bytheway)
 
So I know ubuntu has been installed and partitioned.  The problem happens after this...

I select the first option and the boot begins.  Then I reach the  ubuntu login.  So I login.

Then I end up right back at the  "username#ubuntu: ~$" prompt.

I have tried every command I could think of and that has been suggested in this thread, on psychocats, and on herman's "bigpond".  I usually get as far as:

sudo apt-get instal ubuntu-desktop

At this point the computer asks me to change media, and put in the Live CD.  I do this, but for some reason it will not read.  I can hear the cd running, but nothing else happens.  The screen keeps saying "insert disk and press enter"  - which I keep doing and I get the same directions "insert disk..."

Any ideas.  Greatly appreciated.:confused:

---

### Post by elchinovi on 2006-10-06
I have 2 quick questions, and they may be a bit dumb...
1- when you installed form the "Alternate CD", do you remember which one did you select from the list? (Install to the HD, OEM mode, or Server)
2- Do you have access to an internet connecion?
Thanks.

---

### Post by KyOT on 2006-10-06
> **elchinovi said:**
> I have 2 quick questions, and they may be a bit dumb...
1- when you installed form the "Alternate CD", do you remember which one did you select from the list? (Install to the HD, OEM mode, or Server)
2- Do you have access to an internet connecion?
Thanks.

Thanks for your response.  And to answer your questions....

1- when you installed form the "Alternate CD", do you remember which one did you select from the list? (Install to the HD, OEM mode, or Server)
[COLOR=Blue]I do not remember.  It wasn't the server (at least i think because I don't think I burned the server cd)[/COLOR]

2- Do you have access to an internet connecion?
[COLOR=Blue]Not on that computer[/COLOR]

---

### Post by calvinthomas on 2006-10-06
Have you tried sudo dpkg-reconfiure xserver-xorg and choosing the vesa driver? I had to do that when I first installed because ubuntu couldn't recongnise my graphics card correctly.

Alternatively you may not have gdm installed, in which case you'll get no screen at all and need to install it!

Calv

---

### Post by elchinovi on 2006-10-06
> **KyOT said:**
> Thanks for your response.  And to answer your questions....

1- when you installed form the "Alternate CD", do you remember which one did you select from the list? (Install to the HD, OEM mode, or Server)
[COLOR=Blue]I do not remember.  It wasn't the server (at least i think because I don't think I burned the server cd)[/COLOR]

2- Do you have access to an internet connecion?
[COLOR=Blue]Not on that computer[/COLOR]

As far as I know, that "Server" option from the "Alternate CD" is not real "Server" like the one that you can download the iso and burn it, but a "shaved down" version of it, with no GUI and just a few programs installed so you can install it on a much older pc.
I don't think that you have the "OEM version" 'cos this one gives you a "oem@localhost:~$" command line, so then you type "sudo oem-config-prepare" to turn it into a normal install...
But back to the other problem... is there n way to get that pc connected to internet?
a hub, a crossover cable, usb adapter, nothing to do the trick?
I'm running out of options (I don't have too many, I'm still kind of new), but you can keep trying...
If nothing else works, you can try booting to the "Alternate CD" or since you already have the Live CD doing a clean install of the Desktop version.
You can always do that as a last resource.
Good Luck!

---

### Post by dmizer on 2006-10-07
do ifconfig and see if you show an ip address.  if you have an ip address, then you have an internet connection.  if you have an internet connection, try this:

```
sudo nano /etc/apt/sources.list
```
put a # mark in front of the lines that say something about "deb cdrom"
then hit ctrl+x hit y to confirm the change, and enter to save it.

then retry:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by KyOT on 2006-10-07
> **dmizer said:**
> do ifconfig and see if you show an ip address.  if you have an ip address, then you have an internet connection.  if you have an internet connection, try this:

```
sudo nano /etc/apt/sources.list
```put a # mark in front of the lines that say something about "deb cdrom"
then hit ctrl+x hit y to confirm the change, and enter to save it.

then retry:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

Thanks so much!

I will try all of these suggestions!

---

