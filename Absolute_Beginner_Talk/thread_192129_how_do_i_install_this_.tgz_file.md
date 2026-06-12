---
title: "how do i install this .tgz file?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-08
I am trying to install Celtx a screen writing program for windows and liunx. i downloaded the linux version and went to a website and saw instructions. i follwoed them to a T and it wont install. can someone look at this attachment and tell me what i did and what to type to correct this?

also does anyone know how i can hear sound in youtube.com in firefox? i can see the video perfectly but can't hear anything. I downloaded everything media related and enabled all the extra stuff and still cant hear the media. i saw something about w37codec files or something how do i get that?

thanks in advance.

---

### Post by taurus on 2006-06-08
Before you want to compile anything from source, you need to install a compile, gcc.  So, open a terminal and type
```

sudo apt-get install build-essential

```
Then, run your commands again
```

./configure
make 
sudo make install

```
And if those three commands above don't work, then paste the output of this command then.
```

ls -la ~/Desktop/celtx

```

---

### Post by maddbaron on 2006-06-08
lol nevermind sorry...i double clicked the sh file and it started the program....i guess thats how to install it lol

but i still need help with youtube please anyone.

---

### Post by taurus on 2006-06-08
[QUOTE=maddbaron]
but i still need help with youtube please anyone.[/QUOTE]
:confused:  :confused:  :confused:

---

### Post by maddbaron on 2006-06-08
spoke to soon...the link was broken b/c i moved the folder to another folder so i guess i do need to install i'll do what u said.

---

### Post by maddbaron on 2006-06-08
when i go to youtube.com i can play the videos there but i can't hear any of the sound. i out it up and nothing...i dont know what to do.

---

### Post by taurus on 2006-06-08
You do get any sound if you play music on your machine with xmms or any other media player!  Perhaps you need to install plugins for your web browser, firefox!!!

---

### Post by maddbaron on 2006-06-08
ok i am doing something wrong now....can you correct me please?
here is the attachment.

---

### Post by maddbaron on 2006-06-08
yeah i put in a cd and got sound. what plugins do i need for firefox? last nite i downloaded a whole heap of stuff in terminal that installed a lot of firefox plugins. what specific sound plugin do i need please?

---

### Post by taurus on 2006-06-08
[QUOTE=maddbaron]ok i am doing something wrong now....can you correct me please?
here is the attachment.[/QUOTE]
I thought you said you can install it by clicking on the sh file!!!  What is the output of this command then?
```

ls -la ~/Desktop/celtx

```

---

### Post by taurus on 2006-06-08
[QUOTE=maddbaron]yeah i put in a cd and got sound. what plugins do i need for firefox? last nite i downloaded a whole heap of stuff in terminal that installed a lot of firefox plugins. what specific sound plugin do i need please?[/QUOTE]
You can use Automatix to install the plugins for your firefox...

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

### Post by maddbaron on 2006-06-08
I cant seem to add attachments anymore so here is the output in quotes.
> maddbaron@alchemist:~$ ls -la ~/Desktop/celtx
total 8792
drwxr-xr-x 12 maddbaron maddbaron    4096 2006-06-08 12:00 .
drwxr-xr-x  7 maddbaron maddbaron    4096 2006-06-08 12:30 ..
-rw-r--r--  1 maddbaron maddbaron     161 2006-01-26 15:00 browserconfig.propert ies
-rwxr-xr-x  1 maddbaron maddbaron    6330 2006-01-26 13:41 celtx
-rwxr-xr-x  1 maddbaron maddbaron   62016 2006-01-26 16:15 celtx-bin
-rwxr-xr-x  1 maddbaron maddbaron    4201 2006-01-26 09:51 celtx-config
drwxr-xr-x 17 maddbaron maddbaron    4096 2006-06-08 11:58 chrome
drwxr-xr-x  3 maddbaron maddbaron    8192 2006-06-08 11:57 components
-rw-r--r--  1 maddbaron maddbaron      24 2006-06-08 11:58 components.ini
drwxr-xr-x  5 maddbaron maddbaron    4096 2006-01-26 13:41 defaults
-rw-r--r--  1 maddbaron maddbaron      24 2006-06-08 11:58 defaults.ini
drwxr-xr-x  3 maddbaron maddbaron    4096 2006-06-08 11:58 extensions
-rw-r--r--  1 maddbaron maddbaron 5428404 2006-05-26 08:32 FrostWire-4.10.9-2.i5 86.deb
drwxr-xr-x  2 maddbaron maddbaron    4096 2006-01-26 13:00 greprefs
drwxr-xr-x  2 maddbaron maddbaron    4096 2006-01-26 13:41 icons
drwxr-xr-x  2 maddbaron maddbaron    4096 2006-01-26 13:41 init.d
-rwxr-xr-x  1 maddbaron maddbaron  124336 2006-01-26 16:15 libgkgfx.so
-rwxr-xr-x  1 maddbaron maddbaron   95268 2006-01-26 16:15 libgtkembedmoz.so
-rwxr-xr-x  1 maddbaron maddbaron   13416 2006-01-26 16:15 libgtkxtbin.so
-rwxr-xr-x  1 maddbaron maddbaron   89440 2006-01-26 16:15 libjsj.so
-rwxr-xr-x  1 maddbaron maddbaron  449036 2006-01-26 16:15 libmozjs.so
-rwxr-xr-x  1 maddbaron maddbaron   48228 2006-01-26 16:15 libmozz.so
-rwxr-xr-x  1 maddbaron maddbaron  176836 2006-01-26 16:16 libnspr4.so
-rwxr-xr-x  1 maddbaron maddbaron  449708 2006-01-26 16:16 libnss3.so
-rwxr-xr-x  1 maddbaron maddbaron  231512 2006-01-26 16:16 libnssckbi.so
-rwxr-xr-x  1 maddbaron maddbaron   15076 2006-01-26 16:16 libplc4.so
-rwxr-xr-x  1 maddbaron maddbaron    8692 2006-01-26 16:16 libplds4.so
-rwxr-xr-x  1 maddbaron maddbaron  150220 2006-01-26 16:16 libsmime3.so
-rw-r--r--  1 maddbaron maddbaron     476 2006-01-26 16:24 libsoftokn3.chk
-rwxr-xr-x  1 maddbaron maddbaron  460864 2006-01-26 16:16 libsoftokn3.so
-rwxr-xr-x  1 maddbaron maddbaron  137276 2006-01-26 16:16 libssl3.so
-rwxr-xr-x  1 maddbaron maddbaron   98876 2006-01-26 16:16 libxpcom_compat.so
-rwxr-xr-x  1 maddbaron maddbaron  664412 2006-01-26 16:16 libxpcom.so
-rwxr-xr-x  1 maddbaron maddbaron    8204 2006-01-26 16:16 libxpistub.so
-rwxr-xr-x  1 maddbaron maddbaron   30869 2005-03-21 03:20 LICENSE
-rwxr-xr-x  1 maddbaron maddbaron    9720 2006-01-26 16:16 mozilla-xremote-clien t
drwxr-xr-x  2 maddbaron maddbaron    4096 2006-01-26 16:16 plugins
-rw-r--r--  1 maddbaron maddbaron     177 2005-03-21 03:20 README.txt
drwxr-xr-x  8 maddbaron maddbaron    4096 2006-01-26 16:24 res
-rwxr-xr-x  1 maddbaron maddbaron   10897 2005-11-21 16:24 run-mozilla.sh
drwxr-xr-x  2 maddbaron maddbaron    4096 2006-01-26 13:41 searchplugins
-rwxr-xr-x  1 maddbaron maddbaron    5036 2006-01-26 16:16 TestIcal
-rwxr-xr-x  1 maddbaron maddbaron   22988 2006-01-26 16:16 xpicleanup
maddbaron@alchemist:~$



when i click the sh file it opens yes but i have to have the folder on the desktop and it doesnt show in applications.

---

### Post by sherlock-holmes on 2006-06-08
double post?

[http://ubuntuforums.org/showthread.php?t=191765](http://ubuntuforums.org/showthread.php?t=191765)

post #23.

please try to have all the info related to one problem in a single thread...it would be really helpful for people including those who help, as a reference in a later stage...

thank you

---

### Post by maddbaron on 2006-06-08
oh i am sorry...this forum style is different. how can I delete that original post? I clicked the scissors thing only see edit but no delete.

---

### Post by taurus on 2006-06-08
What does the "README.txt" say???

---

### Post by maddbaron on 2006-06-08
the read me txt talks about firefox. nothing about install but I give up. I'll just put the main folder on desktop n open it from there.

in my quest to solve my sound issue in youtube, i downloaded a ton of extensions from synaptic and now I need to add the newest flash player 4 linux i downloaded it but it says install from desktop via command line.

Whats the command line please? what do I enter?

sudo apt-get install flash?

/desktop install flash ?

---

### Post by taurus on 2006-06-08
Again, if you use Automatix that I already told you, you can install flash and other plugins for your firefox!!!  Then, you don't have to worry about command line or anything like that!!!

---

### Post by maddbaron on 2006-06-08
I cant install Automatix. I have tried several times I followed the instructions to the letter in the help guide in this forum and it wont install at all. I am new to Linux cant even get my wireless working if I hadnt tried everything I found in this forum or google I wouldnt ask in a new or old thread.

---

