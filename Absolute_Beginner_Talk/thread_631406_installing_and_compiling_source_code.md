---
title: "installing and compiling source code"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by alexisantonakis on 2007-12-04
Hi,

I am trying to install IMAP for PHP5 as referred to at [http://ca.php.net/manual/en/ref.imap.php](http://ca.php.net/manual/en/ref.imap.php)

I have downloaded the file and unzipped it, and am trying to follow the instructions, both on the PHP.net site and the instructions contained within the zipped files, as well as elsewhere online, but have got completely lost.

I have never compiled source code before and to be honest do not really know what I am doing.

Can someone please walk me through this, step by step. I don't even know how to tell PHP to recognise that the IMAP library has been installed. In Windows the installation programme did that for me, or I could go to the php.ini file and make changes there...I understand in Linux, I have to re-compile PHP in order for it to recognise this? But how exactly.

MTIA
Alexis

---

### Post by rickycodie on 2007-12-04
first thing to do is to see if the code is precompilled-- if there is a script of something of the like then you don't need to worry , just execute the script. 

if not you need to get the package  build-essential. enter this into the terminal

sudo apt-get install build-essential

then, in the terminal, navagate to the folder and issue this command
 ./configure

then 

make

then 

make-install

done!!

this link might help too

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by alexisantonakis on 2007-12-04
Thanks Lenovo.

It is not pre-compiled..so I will need to run the first line..does it matter in which directory I am in when i run this...

The answer I got is:
---
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libwrap0-dev libsnmp-perl libsensors-dev libidn11-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
---

When it comes to typing ./configure,, which folder are we talking about please?

As I said I really do need someone to hold my hand through this, for the first time.

Cheers
Alexis

---

### Post by rickycodie on 2007-12-05
the folder you should navagate to is the one with the program that you are trying to install. use cd, for example to navagate to the folder called Videos from the default location ( your home folder) is this 

ricky@ricky-laptop:~$ cd Videos

then it should look like this

ricky@ricky-laptop:~/Videos$

that's where you start at ./configure

so if the folder containing the program is called program1 then do the same substituting program1 for Videos. the terminal is case-sensitives o watch that.
also it looks like you already have build-essential installed-good. 

p.s. it is easier for me to navagate through my home folder, so if you want copy/paste the folder there then there's no complicated and long commands.

---

