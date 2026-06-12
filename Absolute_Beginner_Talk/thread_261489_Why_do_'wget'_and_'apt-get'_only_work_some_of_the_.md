---
title: "Why do 'wget' and 'apt-get' only work some of the time?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by wajvpitt on 2006-09-20
I've just thought to myself, 'I want to spend time using ubuntu, rather than setting it up.'  I've spent long enough messing around now.  

So I thought I'd turn to Easyubuntu - doesn't seem to run at all.  

Now I'm trying Automatix - why does 'wget' not work for me?  Connected via the wifi I painstakingly set up.

I'm getting so very frustrated that it took me about five minutes to find the 'new thread' button.

---

### Post by deadgobby on 2006-09-20
> **wajvpitt said:**
> I've just thought to myself, 'I want to spend time using ubuntu, rather than setting it up.'  I've spent long enough messing around now.  

So I thought I'd turn to Easyubuntu - doesn't seem to run at all.  

Now I'm trying Automatix - why does 'wget' not work for me?  Connected via the wifi I painstakingly set up.

I'm getting so very frustrated that it took me about five minutes to find the 'new thread' button.
 Woo slow down and place down the hammer. I understand you may be fluster and want to get Ubie rock and finding your way around the forum. Can you tell us as in the Ubie forum family why Easy Ubie or Automatix will not work. Is it hanging up and such. We are here to help and help you find the nail to go with the hammer.
Gobby

---

### Post by wajvpitt on 2006-09-20
I installed Easyubuntu and it simply didn't run.  I clicked on the icon all I liked, but it didn't run.  Rather like when I clicked 'install' on the Live CD.  I thought I'd remove it and reinstall, and I get this > E: easyubuntu: subprocess pre-removal script returned error exit status 1
 error whenever I try to remove it.  

Now I'm trying Automatix - the automatic Automatix installer doesn't get fetched by 'wget' - I type, 
```
wget http://www.getautomatix.com/files/automatix-installer
```
and I get ```
Error parsing proxy URL http://:8080/: Invalid host name.

```.  This error seems to occur most of the times I've tried, 'wget.'  

Next I tried the slightly less automatic Automatix - I think I edited 'sources.list' successfully and the next step is to type ```
wget http://www.getautomatix.com/apt/key.gpg.asc
``` and I get the same error.  

It seems that it would be near impossible to get a working Ubuntu system without the internet!  

I'd love to find that nail - my vision is becoming more and more blurred - I really need a hand to guide me there now...

---

### Post by kick6 on 2006-09-20
> **wajvpitt said:**
> 

It seems that it would be near impossible to get a working Ubuntu system without the internet!  



are you saying you *don't* have an internet connection?

---

### Post by wajvpitt on 2006-09-20
No - I've got a wired connection and a wireless connection.  It would've been nice to've got the wireless one working without the wired one though!

---

### Post by deadgobby on 2006-09-20
> **wajvpitt said:**
> I installed Easyubuntu and it simply didn't run.  I clicked on the icon all I liked, but it didn't run.  Rather like when I clicked 'install' on the Live CD.  I thought I'd remove it and reinstall, and I get this  error whenever I try to remove it.  

Now I'm trying Automatix - the automatic Automatix installer doesn't get fetched by 'wget' - I type, 
```
wget http://www.getautomatix.com/files/automatix-installer
```
and I get ```
Error parsing proxy URL http://:8080/: Invalid host name.

```.  This error seems to occur most of the times I've tried, 'wget.'  

Next I tried the slightly less automatic Automatix - I think I edited 'sources.list' successfully and the next step is to type ```
wget http://www.getautomatix.com/apt/key.gpg.asc
``` and I get the same error.  

It seems that it would be near impossible to get a working Ubuntu system without the internet!  

I'd love to find that nail - my vision is becoming more and more blurred - I really need a hand to guide me there now...
 Ok I think you got too carry away and gun hoo with the hammer. First did you read the docs on installing Easy Ubie? Cause you need to to do a couple of things before running easy Ubie. [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) 
 Last time I install Easy U. You DL a package, unpack it with archive manager, once unpacked. You open up the unpack folder, and click on easyubuntu.sh icon. I run Automantix with no problem. If you are just converting from windows. Please put in mind that the commands for linux are case sensative. So for sample. You open up a terminal and type in WGET, you get nothing, if you type in wget in lower case. off you go. 
 I am getting the feeling you are using dial up. So you will need to take the time and DL this and will save you time
[https://ubuntuplus.bountysource.com](https://ubuntuplus.bountysource.com)
Gobby

---

### Post by wajvpitt on 2006-09-20
I'm using a broadband connection. 

I do understand that things are case-sensitive.  I did read the preable for Easyubuntu - it seemed to install fine, just doesn't start up.  

I'd hope I could say that I'm more frustrated than gung-ho.  

Let me get this straight - for the absolute easiest (Windows perspective still) install of Automatix, I run terminal, paste in ```
wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
``` and it should work?  

It's not - 'wget' isn't working.

---

### Post by jbennet on 2006-09-20
i have the same problem. i am an experienced debian (but new to ubuntu)user. I downloaded easyubuntu and installed the deb. It put a launcher in the gnome menu but does nothing when i run it.

---

### Post by wajvpitt on 2006-09-20
exactly... 

I'm sure there's a reason why 'wget' isn't working.  The file does exist - it is a script to do everything else for me.  

Is my syntax wrong somewhere?  Is there a proxy issue or something?

---

### Post by wajvpitt on 2006-09-20
can anyone suggest a 'wget' command that will **definitely** work...

---

