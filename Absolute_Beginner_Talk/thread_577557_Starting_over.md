---
title: "Starting over"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-16
The other day I tried to start from scratch and reinstall 7.04.  The problem is there was nothing really wrong with my current instillation other than I can't get commercial DVD's to play. So  I was going to start from scratch just because I have the time and I can.  When I booted from the DVD, it would not start the install process. when presented with the choice to install or start Ubuntu it would alway start Ubuntu. Since I have a working instillation that makes sense.

What do I have to do if I want to start from fresh and reinstall a new copy. Once I figure this out I may hold of until i can download 7.10

Since I am on the subject of 7.10 I purchased a rather lengthy book (Sams Ubuntu Unleashed) on 7.04 to help me along.
How much will this book still be relevant when 7.10 hits the street?

thanks
Ron

---

### Post by LowSky on 2007-10-16
Most of the CLI commands will be the same, and some of the GUI references have changed. Nothing too drastic.

By the way Ubuntu cannot play commercial DVDs without you installing the codecs.
Give this a good look
[http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624")

---

### Post by Dr Small on 2007-10-16
Just a quick question.
Did you try running this commercial DVD through VLC player ? It should have played it.

Dr Small

---

### Post by tshirtz1013 on 2007-10-16
" Since I am on the subject of 7.10 I purchased a rather lengthy book (Sams Ubuntu Unleashed) on 7.04 to help me along.
How much will this book still be relevant when 7.10 hits the street? "

Ubuntu is based on a flavor of Linux called Debian, and any book that has information about Debian and any release of Ubuntu, will have heaps full of good information.  There are many changes in 7.10 but most are changes that fix small quirks or other annoyances. Just like those windoze books for dummies, any book bought about Ubuntu is going to serve as a great and helpful resource, regardless of the version you are running.

As for the DVD, once you have it in your drive, you should be able to boot up to a menu and choose "Install or Start Ubuntu". when it loads up to its default live desktop, you can choose the install icon on the desktop to install. I am not sure if I understood your question right but if I did, then I think your getting into your original Ubuntu install and not the "live" disc environment.

EDIT: I seen from other post that you where trying to watch a dvd. like Dr. Small said try VLC. also get your libdvd file off synaptic. VLC and your dvd files can be gotten from Synaptic once you enable all your repos.

---

### Post by rdsii64 on 2007-10-16
> **tshirtz1013 said:**
> " Since I am on the subject of 7.10 I purchased a rather lengthy book (Sams Ubuntu Unleashed) on 7.04 to help me along.
How much will this book still be relevant when 7.10 hits the street? "

Ubuntu is based on a flavor of Linux called Debian, and any book that has information about Debian and any release of Ubuntu, will have heaps full of good information.  There are many changes in 7.10 but most are changes that fix small quirks or other annoyances. Just like those windoze books for dummies, any book bought about Ubuntu is going to serve as a great and helpful resource, regardless of the version you are running.

As for the DVD, once you have it in your drive, you should be able to boot up to a menu and choose "Install or Start Ubuntu". when it loads up to its default live desktop, you can choose the install icon on the desktop to install. I am not sure if I understood your question right but if I did, then I think your getting into your original Ubuntu install and not the "live" disc environment.

EDIT: I seen from other post that you where trying to watch a dvd. like Dr. Small said try VLC. also get your libdvd file off synaptic. VLC and your dvd files can be gotten from Synaptic once you enable all your repos.
That is the strange part.  I have researched this forum and found which ones I needed to play commercial dvd's. I have enabled all the repositories and used the apt-get command to install the libraries and codecs.  I have the VLC media player. I must assume that I have something incorrectly or out of order.  So just because I can I am going to start from scratch

Since I am on the subject, how do I find if I have made any mistakes installing the libraries and codecs.

---

### Post by tshirtz1013 on 2007-10-16
You can use synaptic, and go under edit and there is an option to fix broken packages. You can try that. Also you can try going to the terminal and typing 
> sudo apt-get update
which will update your package lists, then
> sudo apt-get upgrade
this will upgarde any packages you have that are out of date, and then
> sudo apt-get autoremove
This automatically removes and packages or library's that are no longer used or left behind. and finally, 
> sudo apt-get autoclean
which also cleans up some information.

I dont know if this will help your current istuation but atleast it may be helpful in the future.

---

### Post by rdsii64 on 2007-10-16
i ran update upgrade autoremove and auto clean
then I use synaptic to reinstall libdvdcss2 and the win32 codec.
I still can't get a commercial dvd to work. 

I know has to be something I am either not doing that I should or should not be doing something that I am.

I will find it some day. it is the last thing I need. once I get that working. K9Copy will work and I can fire Bill Gates for good. the only other alternative is to spend a wad of cash, buy a mac and use mac the ripper.(LOL)

that isn't such a bad purposal since I want to buy a mac even If I do get my linux box running the way I want it to. their pricey but they would make a good retirement present.

---

### Post by mramsey on 2007-10-16
Odd...VLC plays my commercial DVD just fine.:confused:

---

### Post by tshirtz1013 on 2007-10-16
Just out of curiosity have you tried automatix ?

---

### Post by rdsii64 on 2007-10-16
> **tshirtz1013 said:**
> Just out of curiosity have you tried automatix ?

not yet but I just installed it a few minutes ago.
how will that help me get my box to play commercial dvd's

---

### Post by rdsii64 on 2007-10-16
forget my last question about automatrix I should have looked at it before asked such a dumb question. I see how it can help me get my box to play commercial DVD's now.

I will let you know how it turns out. later

---

### Post by rdsii64 on 2007-10-16
> **tshirtz1013 said:**
> Just out of curiosity have you tried automatix ?

I tried automatrix2  after that my box played the comming attractions of a commerical DVD. when I tried to play the main movie, I got a msg box that asked me if I was trying to watch an encrypted DVD without lidvdcss.  
now I am really confued.

HELP!!

---

### Post by tshirtz1013 on 2007-10-16
that is the library required to watch retail dvd's that support encryption. if you type 
>  libvdcss 
in the search box for synaptic, it should bring up libdvdread3, install that.
 or you can type 
> sudo apt-get install libdvdcss
if that doesnt work try 
> sudo apt-get install libdvdread3

I think libdvdread3 is for the gusty release though so try the libdvdcss install first.

hope this helps a bit more...

---

