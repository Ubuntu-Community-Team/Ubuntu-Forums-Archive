---
title: "Please tell how to install aMSN.."
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by madu on 2006-01-14
HI guys..
I'm a noobie so please help me out..
I'm running the amd64 version of ubuntu...
I want to install aMSN but dont know how to..
I tried downlading both .BIN and .PACKAGE files..
I tried sudo apt-get install, sudo dpkg -i ... but doesnt seem to work...

Can anybody tell me how to install these..
Thank you very much...

---

### Post by bonzodog on 2006-01-14
Here, try this: 

[http://doc.gwos.org/index.php/EasyAmsn](http://doc.gwos.org/index.php/EasyAmsn)

This will install the latest aMSN from cvs with the tcl/tk interface installed, which makes it look and perform like MSN messenger.

---

### Post by public_void on 2006-01-14
I would select "other" when downloading aMSN 64-bit. This will download a .tar.gz, the problem is you have to compile from source to use it. To do this open up the terminal and do the following

tar -xvzf [location e.g. /home/username]/amsn-0.95.tar.gz (Unpacks the file into a new directory called amsn-0.95)
cd /amsn-0.95 (change directory to the new directory)
./configure (configure the install, Note: this is where you could get warnings and messages about missing files, I doubt it. If you do post back with those messages)
make (compiles the program)
sudo make install (installs it)

Hopefully that should do it. Post back with any problems.

EDIT: I really should type faster. Type the about posters method if you find it easier (I'd probably suggest do that anyway)

---

### Post by madu on 2006-01-14
hi guys..
I downloaded the amsn-0.95.tar.gz and did those stuff.. I got these when i did ./config:
m[B]aduranga@Maduranga:~/Desktop/amsn-0.95$ ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH[/B]

How can i install the package for the gcc.. i checked the ubuntu packge library vut there are soo many!!!
Please help me..
Also thank you very much for the support..!!

---

### Post by bscbrit on 2006-01-14
In Synaptic, search for 'build-essential' and install it.

---

### Post by madu on 2006-01-14
Hi..

I couldnt find build-essential in sypnatic so I installed it from sudo apt-get..
After that i went to the amsn-0.95 directory and did ./configure:
And then i got this error-
***checking tcl build dir... configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev***


What can I do about this guys....?
Sorry for all the trouble guys.. But I feel I;m very close...

Thanks..!

---

### Post by bscbrit on 2006-01-14
The error messages are telling you what is missing - known as 'dependencies'.  The build prorgram needs to link your application with lots of other elements but it cannot find some of them on your computer.

Install 'tcl-dev' and it should get passed this point until it finds another missing dependency.  This is the advantage of using Synaptic - it will automatically find and install all the relevant software to make something work.  If you install amsn using Synaptic I think that you will find it much simpler.  Of course, I do not use the amd64 and so amsn might not be in the appropriate repositories  :p

If you enter Synaptic and search for 'tcl' it should find what you are looking for - on mine it finds several different versions.  You will have to work out which version your program needs to build successfully.

---

### Post by madu on 2006-01-14
HI guys..
Got it done..
I followed public_voids method.. also had to install the packges..thanks bscbrit..
I was able to install and all and atlast it started and said something about a SSL thing came up and asked me install it. Anyway because amd64 version was not there I had to download the source code and install.. anyway I have never installed a source code before today.. and i learned a lot by this so far..
But anyway.. i had trouble with it..and i just tried sudo apt-get install amsn..!!
BANG!! there it was..!!
Finally its done.. If ican get skype to work, i;ll be fine.. Surprisingly I have the skype icon in internet menu, but nothing happens when i click it.. lol.. didnt see it there before.. i must have installed when typing around..
Anyway guys.. thanks a million for all the help..!!!
This is so much better than Windows!!

---

### Post by bscbrit on 2006-01-14
I'm pleased that you were successful.

It is always worth spending some time with Synaptic before downloading someone else's package and trying to install it.  Next time you have a spare 10 minutes, just browse through the massive list of programs available in Synaptic (over 17,000 on my machine!).  I always find something interesting to play with and I know that it will not break my computer.

See you around the forums ;)

---

### Post by patrick295767 on 2006-01-14
Have a look there too plz: [http://ubuntuforums.org/showthread.php?t=114006&highlight=amsn](http://ubuntuforums.org/showthread.php?t=114006&highlight=amsn)

---

