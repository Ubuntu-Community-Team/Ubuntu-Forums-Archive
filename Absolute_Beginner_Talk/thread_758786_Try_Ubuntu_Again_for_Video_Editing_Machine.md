---
title: "Try Ubuntu Again for Video Editing Machine"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by sandmanfvr on 2008-04-18
Well I want to try Ubuntu again, now that I have broadband.  I have Sprint EVDO with the Ovation U727 USB card, and it is Linux compatible.  I read on the forum here that wasn't hard to setup either.  I need to have Cinelerra and Celtx on it to.  I got a Dell Inpiron 531, with AMD 64 X2 chip so I know I would need to AMD 64 bit version.  How easy would it be to download the iso and get onine and add the software I need?  Thank you.

---

### Post by Weidbrewer on 2008-04-18
So, if I follow you, you're just looking for where to DL the 64-bit version?   If so, downloads of the ISO can be found here:  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by indiecast on 2008-04-18
with a 64 bit machine i do believe you can choose between the x86 and x86_64 versions.


anyways i run the same programs

TO GET UBUNTU:

follow his link

burn the iso to a cd

install ubuntu

add programs in ubuntu from a .deb file, the add/remove programs manager, or the synaptic package manager.

TO GET CELTX: 

download the linux version of celtx and copy the extracted folder to your home directory

then add an entry for celtx in your main menu under whichever catagory you want.  to do this go to system > prefrences > main menu...i think...you can figure it out if thats not right tho. 

anyways make a menu item and in the command area browse to the celtx executable.  if that doesnt work i think you need to point it to the shell script. im pretty sure both will work.

close the menu and celtx should be in your programs menu where ever you put it.


TO GET CINELERRA

go to the cinelerra website and add the repository to the list in system > administration > software sources

save and reload the software list (it should automatically prompt you to do this)

then go to the synaptic package manager (system > administration > synaptic package manager)

and search cinelerra

select the one you want

click apply

it should install

exit

now cinelerra should be in the sound and video menu under applications





hope you find this of some use to you,

indiecast

---

### Post by sandmanfvr on 2008-04-18
Cool, I will have to try this again.  On Celtx, the .deb file is like a executable?  Trying to follow you on that.  I understand adding repositories and then downloading.

I think I know what you mean on Celtx, unzip the tar and in the folder there a "executable" or script that runs it?

Second edit, on multimedia I once tried to add multimedia codecs and it hosed Ubuntu.  Is there a SURE FIRE way of doing it, no way to mess it up?  Thanks.

---

### Post by sandmanfvr on 2008-04-18
*bump*

Sorry, I won't bump again.  Man, this forum is hopping more than it ever did!  :)  Just wondering on the multimedia.  I got the iso here at work, then I will try a dual boot install, done it a few dozen times now trying linux, and go for my sprint card to work.

---

### Post by forrestcupp on 2008-04-18
Well, I think I would use the x86 version instead.  I tried the 64-bit one once and certain things were still a pain to deal with.  Either one will work with your processor.

Multimedia is pretty easy to deal with now.  Once you have Ubuntu installed, you first need to add your Universe and Multiverse repos.  To do that, you go to System->Administration->Software Sources and in the Ubuntu Software tab, make sure all of the boxes are checked.  Then open a terminal and type
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```and voila!  You have about all of your codecs including Java and Flash.

[Here](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu) are directions to install Cinelerra CV in Ubuntu.  It's pretty easy nowadays.  Cinelerra works for 32-bit and 64-bit systems.

---

### Post by sandmanfvr on 2008-04-18
Nice, it was more of a pain last time I tried it.  I think I will push the 64 bit version, so that video editing will be using all the processor power.  It will be for internet, audio and video editing.  Oh yeah pictures, but any os can do that.

---

### Post by forrestcupp on 2008-04-19
You're right.  64-bit is best for what you're doing.  Just know ahead of time that some things are harder to get working in 64-bit.  Things have come a long way, though.

---

### Post by indiecast on 2008-04-19
oh yeah i was talking about the celtx precompiled version.  if there is a .deb, you should just be able to double click on it and a manager will pop up and you should be able to install it.

is there a .deb for sure? i wanna know for future installations/advice

---

### Post by sandmanfvr on 2008-04-19
Posting from Ubuntu now!  I got Sprint online of course, all my codecs, and nvidia working.  Finally I can update linux.  On Celtx and Cinelerra, I am stuck.  Downloaded Celtx, but don't get what to do.  In the Celtx folder, see a file just named "Celtx" and I try to run it, but nothing happens. I may have missed something.

On Cinelerra, I add the repositories but NOTHING.  I can't get it to download.  Help please, thanks.  :lolflag:

---

### Post by indiecast on 2008-04-19
cinelerra should be in the synaptic package manager

elaborate more lol sry not enough info here.

glad things are working tho : )

---

### Post by sandmanfvr on 2008-04-19
Just checked Synaptic, I was using "Add/Remove" and Cinelerra is there and it is downloading.  On Celtx, let me look on deb.

Ok, it installed.  Celtx is download as a tar ball only.  Hmm..

I wonder why my Sprint is limited to 65KB down a second, is that KPPP?

---

### Post by indiecast on 2008-04-20
ok yeah, any repositories you add you access through synaptic...glad that worked : )


i believe one of the files is an executable and one is a shell script for celtx. i think either will work, but if the executable doesnt work, click on the script file.  if that doesn't work, navigate to that folder in the terminal and type celtx.  post back and let me know if any of that works or not

---

### Post by sandmanfvr on 2008-04-20
Bash command "celtx" not found.  Weird.

---

### Post by indiecast on 2008-04-20
try typing the shell script file in the terminal under that directory

---

### Post by sandmanfvr on 2008-04-20
I don't know what the shell script is or looksl ike. hah

---

### Post by indiecast on 2008-04-20
in the file manager it should have the same type of symbol as the "celtx" executable

---

### Post by sandmanfvr on 2008-04-20
Ok whoa, I forgot some linux and now I remember.  If I do:

./celtx

from a terminal, it runs.  Ok.  Well it runs, I was doing it wrong.


EDIT:  Got a shortcut on the desktop for Celtx.  I got it all working, but Cinelerra just won't play anything.  I guess I need help on it.

---

### Post by sandmanfvr on 2008-04-20
Cinelerra is junk, or it is not working for me. I installed the AMD64 version with opengl and when I open video files, nothing.  It kind of ran on one, but crashed.  Anymore suggestions?  I read about "Lives".  Tried to install that but I got an error on a dependency of the attached image.  Weird.

Also, got kvpnc on but won't get to my work vpn. Weird.

---

### Post by indiecast on 2008-04-20
try the non 64 bit version. it works for me


also make sure you have all ur codecs installed, that might be one of the problems

---

### Post by sandmanfvr on 2008-04-20
Tried all 3 versions, no go.  I hangs and crashes.  On Lives, how do I get that to install?  Thanks.

---

### Post by sandmanfvr on 2008-04-20
I hate to bump, but this forum moves.  On Lives (site is here:  [http://www.getdeb.net/release.php?id=2393](http://www.getdeb.net/release.php?id=2393))  I can download, but that package is a problem.  Can anybody help me on that?  THank you.

---

### Post by sandmanfvr on 2008-04-20
Bump again, I have searched google left and right, I don't see what the problem could be and I can't find a repository to add.

---

### Post by sandmanfvr on 2008-04-23
Well I go some help, Lives is installed.  I also put on x264 codec.  Lives is pretty good, don't know why Cinelerra keeps crashing.

---

### Post by richandcreamy on 2008-05-29
Can you share the help you got with this issue?  I have the same problem!

---

