---
title: "i got ubuntu to work"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by yatesDELTA on 2006-03-03
YAAAY

it has taken me since saturday evening to around 11 last night. i was to tired ot post. but this is my first ever post on Linux. i have come to your world peoples

---

### Post by Klaidas on 2006-03-03
Congradulations, and welcome to Ubuntu! :)
Believe me, you'll love it ;)

---

### Post by TrendyDark on 2006-03-03
Congrats, if you have any questions for us, just ask. :) Welcome and enjoy!

---

### Post by cotcot on 2006-03-03
Welcome and a couple of usefull links (that I found too late when I started with Ubuntu) : 

A guide :  [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

General docs : [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Repository for codecs : [http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

---

### Post by yatesDELTA on 2006-03-03
well im not to sure if i like it yet and there is a lot of diference. but im gonna get used to it. xp was like this to begin with- i absolutly hated the hting but then i realise the greatness

anyways i cant wait to have some good fun with this

---

### Post by yatesDELTA on 2006-03-03
well im going to go back to windows and do a few things. i have stuff there that can NEVER be replaced, and i mean it. should be on linux later though

---

### Post by TrendyDark on 2006-03-03
Just curious, what is keeping Windows on your PC? I had it until yesterday, for TeamSpeak/Enemy Territory, but I've learned both are easy to configure in FreeBSD.

---

### Post by Swab on 2006-03-03
[QUOTE=yatesDELTA]well im going to go back to windows and do a few things. i have stuff there that can NEVER be replaced, and i mean it. should be on linux later though[/QUOTE]

What sort of stuff?

---

### Post by yatesDELTA on 2006-03-03
well im back as my XP drive is anoying me. it has loads of trojans and other errors which i cant be bothered to spend all afternoon removing
so im back
okay first thing, the duble systems. i have 2 HDDs. i would put them on one nbut they aint big enough. 
things that i need on xp inlcude my c++ compiler and my HTML editor and quite alot of graphics. Also my main email acoutn as i cant find my pop details.

---

### Post by Swab on 2006-03-03
[QUOTE=yatesDELTA]well im back as my XP drive is anoying me. it has loads of trojans and other errors which i cant be bothered to spend all afternoon removing
so im back
okay first thing, the duble systems. i have 2 HDDs. i would put them on one nbut they aint big enough. 
things that i need on xp inlcude my c++ compiler and my HTML editor and quite alot of graphics. Also my main email acoutn as i cant find my pop details.[/QUOTE]

OK... you can install the g++ compiler by typing:
sudo apt-get install g++

For HTML you could try bluefish... again
sudo apt-get install bluefish

Can't help with your pop details :)

---

### Post by yatesDELTA on 2006-03-03
sudo apt-get install g++
 is this ubuntus version of dos that i type it in?

also im having trouble downloading the latest MSN. i dont really like the messenger supplied

---

### Post by Swab on 2006-03-03
[QUOTE=yatesDELTA]sudo apt-get install g++
 is this ubuntus version of dos that i type it in?

also im having trouble downloading the latest MSN. i dont really like the messenger supplied[/QUOTE]

Yeah into the terminal... then it will ask for your password.. and install

Obviously there is no official microsoft messenger client for linux.. I really like Gaim, but if you don't there are others you could try, amsn comes to mind.  It can be installed through apt-get also.  But in this case you will need to enable extra repositories.  See[ this page]("https://wiki.ubuntu.com/AddingRepositoriesHowto") in the wiki for help.

---

### Post by yatesDELTA on 2006-03-03
thanks.

i just dont like the old MSNs as they are pretty wel  dodgy in my experience

---

### Post by yatesDELTA on 2006-03-03
okay then im stuck on repsitorys. i really dont have a lcue which to use. also binary or source? i know the meaning but i dont know which to chose

---

### Post by Swab on 2006-03-03
[QUOTE=yatesDELTA]okay then im stuck on repsitorys. i really dont have a lcue which to use. also binary or source? i know the meaning but i dont know which to chose[/QUOTE]

well, i'd start off with universe... edit your /etc/apt/sources.list file and uncomment the universe lines... nothing to it.

1. open up terminal
2. type "sudo gedit /etc/apt/sources.list" in the terminal
3. enter your password
4. uncomment the commented out universe lines and save file
5. type "sudo apt-get update" in terminal

---

### Post by yatesDELTA on 2006-03-03
how do i uncommenet?

---

### Post by Swab on 2006-03-03
[QUOTE=yatesDELTA]how do i uncommenet?[/QUOTE]

example:
# this is a commented line
this in an uncommented line


So just delete the #.. just like comments in code.

---

### Post by yatesDELTA on 2006-03-03
well im not sure if i even uncommented the right lines. anyways how do i install a program?
it all seems a bit diferent

---

### Post by KansasJoe on 2006-03-03
I know how you feel about site editor because I use dreamweaver on windows but another good one you should check out is NVU which can be used on windows or linux (slowly coming around to it but have all my templates on dreamweaver)

---

### Post by The Warlock on 2006-03-03
[QUOTE=yatesDELTA]well im not sure if i even uncommented the right lines. anyways how do i install a program?
it all seems a bit diferent[/QUOTE]

This is actually really cool, and it's something Windows will never have.

The Windows way is going to a webpage, downloading the program, installing the program, and periodically checking that webpage for updates and newer versions and such.

With Ubuntu, you just use apt. In the command prompt, type in ```
sudo apt-get install program-name
``` where "program-name" is the name of the package that you want to install. (The "sudo" that preceeds system-changing commands like this is there so that the program that is run, in this case, apt-get, is run with administrator permissions. It will ask you for your password.)

Then, apt will find the program, download the program for you, and notify you whenever a new version becomes availiable. 

If you don't like to deal with the command line (you'll get over it eventually, as it's usually the quickest way to do something once you know how), there are graphical front-ends for apt. Look in the System menu, under "Administration", for Synaptic Package Manager and run that. Play around with it a bit. Installing and removing programs with packages is a lot cleaner in Linux than it is in Windows.

---

### Post by xhie on 2006-03-03
C++ compiler does not in any way shape or form equal XP. Nor does HTML :)

Or is there a specific IDE that your really attached to? Theres lots of other IDE's in the world, linux has some great alternatives to VS.NET, Theres a thread sticked in the programming forums about IDE's. Look around theres something that will probably fit your workflow. Me personally I like Anjuta for big stuff when I cant possably do without something graphical, but 99% of the time i'm a VI person. Just me though, everyone is differant. 

Now if you program for windows specifically that might be a problem hehe.

---

