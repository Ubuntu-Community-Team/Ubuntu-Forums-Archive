---
title: "kubuntu to ubuntu...uhoh"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by boblettoj99 on 2008-03-23
Ok, i am trying to change my kubuntu 7.10 to ubuntu.
i researched how to do it and ended up running:

```
sudo aptitude install ubuntu-desktop
```

seeing as it was gunna take ages (210mb to download and my internet still thinks its 56k) i went and made some food.
when i came back it was finished...surprisingly early.
so i logged out to see if i could change session to gnome...but UHOH
no gui, im stuck with a command line.

it comes up with welcome to ubuntu 7.10 and gives me a little login and password line and that works but its still all in text.

please help meeee, i miss my cube :(

---

### Post by scragar on 2008-03-23
few things you try, firstly and most importantly though```
startx
```just to see if you can get a gui working. If not post any error's back.

---

### Post by LaRoza on 2008-03-23
Where there any errors?

After logging in, what is the output of the command:

```

startx

```

---

### Post by Joeb454 on 2008-03-23
what happens if you try logging in, and then typing startx?

---

### Post by boblettoj99 on 2008-03-23
Sorry if it takes ages for me to reply, i have to restart into linux and then back into windoze every time.

when i typed startx it gave me just a black screen with a mouse...

---

### Post by boblettoj99 on 2008-03-23
ok i ran it again and did ran startx
same thing happened so i ctrl+alt+backspaced and saw some errors in commandline, dont know if they are to do with this or not:

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed
....
(EE) AIGLX: reverting to software rendering

anyone have any ideas?

---

### Post by boblettoj99 on 2008-03-24
please somebody, still no ubuntu :(

---

### Post by forrestcupp on 2008-03-24
Well, if it installed it that quickly on a 56k connection, maybe it didn't really download and install everything.  I would tell you to do a **sudo apt-get install ubuntu-desktop** again to make sure it really is completely installed, but I have absolutely no idea how to connect to dial-up from the command line.

If you borked your system that badly, you may end up having to back up your data from the CLI and reinstall.  It would be easier if you had an internet connection that is always on.

---

### Post by boblettoj99 on 2008-03-24
lol its not really dial up its just crap broadband!

how do you connect from a command line?
i tried sudo apt get bla blah.. but it said it couldnt fetch lots of things, i assume this is because of no connection

---

### Post by boblettoj99 on 2008-03-24
is there any option on the live cd to repair it or something?
iv just got sooo many programs i dont wanna get rid of them all :(

---

### Post by forrestcupp on 2008-03-24
So you have broadband?  Maybe the connection isn't your problem.  Try updating first.
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Joeb454 on 2008-03-24
Possibly, try booting the live CD and see if there is an option (underneath Start or Install Ubuntu) to "Repair Installation"

:)

---

### Post by boblettoj99 on 2008-03-24
forrestcupp: i tried what you said but it said it couldnt fetch data for every thing it was trying to download.
i do have broadband but for some reason it isnt connected???

joeb454: nope theres nothing there :( + this is a last resort :P

the exact error was:

```

Failed to fetch http://repo url here/so and so.gz 
could not resolve gb.archive.ubuntu.com

```

---

### Post by boblettoj99 on 2008-03-24
oh well, i give up!
im gunna reinstall kubuntu then try again when i get some internet!

thanks to everyone who helped!

---

### Post by luceerose on 2008-03-29
> **boblettoj99 said:**
> lol its not really dial up its just crap broadband!

how do you connect from a command line?
i tried sudo apt get bla blah.. but it said it couldnt fetch lots of things, i assume this is because of no connection

To connect from a command line just type in dhclient
Then try the sudo apt-get blah blah again.

As for your graphical problem, I don't know if I can help you.
I run Hardy(8.04) and when you login to a root shell it brings up a menu asking if you want to drop to root shell, resume boot, or run xfix to fix the xserver.

I'm not sure if 7.10 has xfix as well. But if typing xfix at  the command line works, that will enable you to boot into gui with basic video that pretty much works no matter what but without 3d acceleration. From there you may have to reinstall your video card drivers & so forth.

I switched my hard drive from one computer to another and ended up with no video, xfix worked for me in that situation.
Also I have an nvidia card that basically installed automagically under Ubuntu but with Kubuntu (on my other partition) I had to use EnvyNG to install it. Strangely, EnvyNG won't keep the refresh rate settings for me.
So, yeah, you can find some strange differences between the way gnome & kde behave themselves.

---

