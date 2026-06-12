---
title: "RealPlayer 10 - Please Help!!"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by jonnybwoi on 2007-07-02
Im sure this has been asked a thousand times, but im getting sick of it!

I want to be able to listen to BBC radio, but in order to do that i need to use real player. I have tried to install it using the terminal 

" sudo apt-get install realplay" 

i tried as the site suggests but i get the error message:

"E: Couldn't find package realplay"

I have no idea how to change file permissions or anything like that, and i am an absolute beginner with terminal commands. Please could someone give me a step by step guide on how to install it....It is driving me insane!

(Other than that I absolutely love Ubuntu)

Thankyou!

---

### Post by reset3x on 2007-07-02
[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

---

### Post by jonnybwoi on 2007-07-02
i didnt really get the website....

---

### Post by reset3x on 2007-07-02
follow the repository how-to... then sudo apt-get install realplay....

---

### Post by jonnybwoi on 2007-07-03
nope i added those commands into the terminal, updated the synaptics and used the sudo command again, but the same error came up!:(

---

### Post by AndyCooll on 2007-07-03
> **reset3x said:**
> [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

Medibuntu has moved:
[Medibuntu repositories have moved...]("http://ubuntuforums.org/showthread.php?t=471089")

:cool:

---

### Post by mali2297 on 2007-07-03
As an alternative, you can download Realplayer at [http://www.real.com/linux]("http://www.real.com/linux"). If you have downloaded the file to your home folder, you then type the following in a terminal:
```

chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

```
You then answer the questions given to you and Realplayer will be installed.

---

### Post by pilli on 2007-07-03
I've just recently gone through this installation process.  Before I could play BBC video I had to open up Real Player via applications> (after installing it as in post above).  When it opens you answer a few more questions, e.g. check box for mozilla plugin and there you go.  Watch BBC vid in stand alone player.  I suspect the radio works in the same way.

---

### Post by reset3x on 2007-07-03
> **AndyCooll said:**
> Medibuntu has moved:
[Medibuntu repositories have moved...]("http://ubuntuforums.org/showthread.php?t=471089")

:cool:

Thanks for the heads up!!! Bookmarks updated!!!

Peace

---

### Post by hmg on 2007-07-07
hey! am a dummy here. please help
i installed realplayer. while installing it suggested a folder in my desktop. i let it be.
now, when i click on the bbc player, i get this message - 
could not find an appropriate hxplay or realplay in the system path to use as an embedded player.

thanks

---

### Post by hmg on 2007-07-07
guess there is a problem with just the bbc live news player.
am able to stream other links on the same site

---

### Post by hmg on 2007-07-08
working now without any fixing from me.
all enjoy!

---

### Post by Cnhy on 2007-07-20
> **hmg said:**
> when i click on the bbc player, i get this message - 
could not find an appropriate hxplay or realplay in the system path to use as an embedded player.

I was getting the same error message - here's what worked for me...

I have RealPlayer installed in my home directory. The BBC radio player wouldn't work until I made a symbolic link to [FONT="Courier New"]/usr/bin/[/FONT]  (which is what I think the error message means by 'system path').

If RealPlayer was installed at [FONT="Courier New"]/home/yourname/RealPlayer/realplay[/FONT]  you would open a terminal and type:

```
sudo ln -s /home/yourname/RealPlayer/realplay /usr/bin/realplay
```

Change the first part of the command to match the actual location where [FONT="Courier New"]realplay[/FONT]  is installed.

Restart Firefox, and it should be fixed.

Hope that's useful to someone.

---

### Post by Bablefish on 2007-07-20
Heres another way of installing it

Install Real Player 10

#apt-get install realplayer

This will install all the required packages and after installation you need to logout and login back with your login to access mplayer.This is located under Applications&#8212;>sound&video&#8212;>Realplayer 10

Install Realplayer 10 in debian etch

First you need to edit you /etc/apt/sources.list file

#vi /etc/apt/sources.list

add the following source list and save the file.

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

or

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main

Now you need to run the following command for update your source list

#apt-get update

Install Realplayer 10

#apt-get install realplayer

This will install all the required packages and after installation you need to logout and login back with your login to access mplayer.Mplayer is located under Applications&#8212;>sound&video&#8212;>Realplayer 10

Install Realplayer 10 in debian sid

First you need to edit you /etc/apt/sources.list file

#vi /etc/apt/sources.list

add the following source list and save the file.

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main

Now you need to run the following command for update your source list

#apt-get update

Install Realplayer 10

#apt-get install realplayer

This will install all the required packages and after installation you need to logout and login back with your login to access mplayer.

Realplayer 10 is located under Applications&#8212;>sound&video&#8212;>RealPlayer 10

---

### Post by fremmus on 2007-07-20
try downloading deb file for here
[http://archive.canonical.com/ubuntu/pool/main/r/realplay/](http://archive.canonical.com/ubuntu/pool/main/r/realplay/)

before i kept getting different erros when installing but with this deb file everything is ok

it worked for me, installed fine and everything seems to be working
btw i got a headache now from trying to find a way to install it lol thank god i found that package....

good luck

---

### Post by Paulmd on 2007-07-20
> **jonnybwoi said:**
> Im sure this has been asked a thousand times, but im getting sick of it!

I want to be able to listen to BBC radio, but in order to do that i need to use real player. I have tried to install it using the terminal 

" sudo apt-get install realplay" 

i tried as the site suggests but i get the error message:

"E: Couldn't find package realplay"

I have no idea how to change file permissions or anything like that, and i am an absolute beginner with terminal commands. Please could someone give me a step by step guide on how to install it....It is driving me insane!

(Other than that I absolutely love Ubuntu)

Thankyou!

Read yesterday's post with my name (paulmd). It was a pain, but i got it working.

---

