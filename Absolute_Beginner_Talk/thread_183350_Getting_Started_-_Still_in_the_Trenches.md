---
title: "Getting Started - Still in the Trenches"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2006-05-27
The following represents instructions given to install F-prot. Can you help me with the clarification requested for each section, please and thank you.

sudo apt-get update
sudo apt-get upgrade 
sudo apt-get install build-essential 
sudo apt-get install libwww-perl 
sudo apt-get install libgtk2.0-dev 
sudo apt-get install checkinstall

I conclude that each line must be added separately meaning there are 6 steps is this corect?

cd /where/you/saved/the/files/ 
sudo dpkg -i fp-linux-ws.deb
The line cd.........  implies I need to provide a path something like c:/ my documents / programme files. How do I do this in Ubuntu?

cd /where/you/saved/the/files/ 
tar zxvf xfprot-1.15.tar.gz 
cd xfprot-1.15 ./configure --with-gtk2 --with-sudo --autodetect --without-debug sudo make 
sudo make install 
sudo dpkg -i xfprot-1.15_1.15-1_i386.deb

smeg
Pick System tools in the left tree viewer. Then Press the New Entry button.

    Name: F-Prot 
    Comment: Anti-Virus Application 
    Command: xfprot 
    Icon: /usr/local/xfprot/icons/antivirus-48x48.png 

Press OK button. 
on the Icon line / user ..... is this generated when I choose an icon from "Browse" ?
How can I debug Launcher if it fails to faunch my app?

---

### Post by Sef on 2006-05-27
> sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
sudo apt-get install libwww-perl
sudo apt-get install libgtk2.0-dev
sudo apt-get install checkinstall

I conclude that each line must be added separately meaning there are 6 steps is this corect?

I would have done it this way:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential install libwww-perl libgtk2.0-dev checkinstall

---

### Post by dmizer on 2006-05-27
[QUOTE=clemkonan]The following represents instructions given to install F-prot. Can you help me with the clarification requested for each section, please and thank you.

sudo apt-get update
sudo apt-get upgrade 
sudo apt-get install build-essential 
sudo apt-get install libwww-perl 
sudo apt-get install libgtk2.0-dev 
sudo apt-get install checkinstall

I conclude that each line must be added separately meaning there are 6 steps is this corect?[/QUOTE]
yes, that is exactly correct.  in terminal (command line) you have to type each line individualy followed by the enter key.  or as sef points out above, you could combine the last four lines as suggested.

> cd /where/you/saved/the/files/ 
sudo dpkg -i fp-linux-ws.deb
The line cd.........  implies I need to provide a path something like c:/ my documents / programme files. How do I do this in Ubuntu?
when you saved the file, you saved it in a folder.  since we have no idea where that folder is, you have to provide that information yourself.  can you see the file on your desktop?  if not, in terminal type:
```
ls
```followed by "enter" and see if the file is there.  you might also be sucessfull by typing whereis filenameyousaved

> cd /where/you/saved/the/files/ 
tar zxvf xfprot-1.15.tar.gz 
cd xfprot-1.15 ./configure --with-gtk2 --with-sudo --autodetect --without-debug sudo make 
sudo make install 
sudo dpkg -i xfprot-1.15_1.15-1_i386.deb

smeg
Pick System tools in the left tree viewer. Then Press the New Entry button.

    Name: F-Prot 
    Comment: Anti-Virus Application 
    Command: xfprot 
    Icon: /usr/local/xfprot/icons/antivirus-48x48.png 

Press OK button. 
on the Icon line / user ..... is this generated when I choose an icon from "Browse" ?

you will have to type (or copy/paste) that line in for the path to your icon.  and make sure you see that it's /usr not "/ user" <-- will not work.  this is just the directory path. 
> How can I debug Launcher if it fails to faunch my app?
if the launcher fails, it will give you an error, just post it here or do a search in google for the error and it should give you an idea of what to do next.

---

### Post by clemkonan on 2006-05-27
Ok, that helps. Now regarding folders in Ubuntu, I see a Home folder, Desktop and tmp. How does one create folders in Ubuntu?Typically I have a folder called Clemkonan which  carries subfolders > Data > Music> Pictures>Spreadsheets. Can I do this in Ubuntu?

Also for the programme I was trying to download I have a launch icon next to help , admittedly I cannot recall the exact path that led me to a graphical list of icons from which I chose one. Clicking the icon creates a brief screen flicker and thats all.
Launch properties declares
Name : Festival
Generic Name: Text to Speech Editor
Comment: KDE Text to Speech mgr
Command : Festival
Type: Application
Icon: graphic is highlighted 
Run in terminal : box is unchecked
If I enter this in terminal  I get:
clem@ubuntuhurricane:~$ sudo apt-get install festival
Reading package lists... Done
Building dependency tree... Done
festival is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
clem@ubuntuhurricane:~$
So I conclude the programme has already been installed and the icon set up is incorrector the add application process went horribly wrong somewhere. 
I was hoping if I could understand the f-prot install I could go back and fix Festival.

---

### Post by uzi09 on 2006-05-27
hmm, i'm not sure what it is you're trying to install (like, i don't know anything about the program), but as far as creating new folders within your home folder:

Procedure 1 (using command line):
open up a terminal (sorry, i don't know which ubuntu you are using, these are instructions for dapper):
```

Applications > Accessories > Terminal
[/code

you'll automatically be placed in your home folder, then type:
[code]
mkdir new_folder

```

where you can sub in any name for "new_folder".

Procedure 2 (using gui):
go to:
```
 Places > Home Folder
```

then:
```
 File > Create new folder
```

> 
clem@ubuntuhurricane:~$ sudo apt-get install festival
Reading package lists... Done
Building dependency tree... Done
festival is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
clem@ubuntuhurricane:~$

yeah, this does mean it's installed, and usually when you use apt-get -- there aren't very many chances of the installng "messing up".

try this:
press: Alt+F2
you should get a run dialogue box appear. in there type in the name of the program.

let us know what you come up with.

if that still doesn't work, try this:
open up another terminal,
then type in the name of the program. if there were any errors, you should see them in the terminal and you'll get the prompt back (clem@ubuntuhurricane:~$)

---

### Post by clemkonan on 2006-05-27
Alt F2 gives
Festival Speech Synthesis System 1.4.3:release Jan 2003
Copyright (C) University of Edinburgh, 1996-2003. All rights reserved.
For details type `(festival_warranty)'
festival>
New terminal wondows gives same thing
Is there a way to review a download and install, for errors or how can I delete any downloaded festival files and start over the download again?

---

### Post by clemkonan on 2006-05-27
Using Breezy 5.10?

---

### Post by uzi09 on 2006-05-27
well, if it gives you the festival prompt
(festival>) then the program is working, but just waiting for some input.

try typing in 'help' or something to see the list of commands.

to remove festival:
```

sudo aptitude remove festival

```

try to use aptitude over apt-get -- it works a lot better :D

---

### Post by clemkonan on 2006-05-27
Here is some information that may be useful in the hands of an expert which I am not, unfortunately.
o install Festival you will need to download the following source packages from the Festival download page:

    * festival-1.95-beta.tar.gz -- The core festival package
    * speech_tools-1.2.95-beta.tar.gz -- The Edinburgh Speech tools library
    * festlex_OALD.tar.gz -- The lexicon distribution
    * festlex_POSLEX.tar.gz -- The lexicon distribution
    * festvox_rablpc16k.tar.gz -- The speech database

You will find several other packages available for download at the Web site, but you won't need them unless you wish to add support for more voices to the basic TTS system.

Having downloaded all the above packages, log in as root, change to the directory where you downloaded the packages, and issue the command tar --xvzf package_name to unpack them. After the unpacking, your current directory will contain the subdirectories speech_tools/ and festival/.

Next, you need to compile the source files. Change to the speech_tools directory and issue the commands:

./configure
make

Then change to the festival directory and issue the same commands.

That's it! The Festival Speech Synthesis System is now installed on your Linux box.

Using Festival

There are various ways you can use Festival. To get into the Interactive Festival Console, type festival at the shell prompt. You should find yourself at a prompt like the one below:

festival>

Your speech synthesis system is now ready to accept input. To get your system to talk to you, try out the following command:

festival> (SayText "type the text you want to hear over here")

The parentheses are required here, and the text to be spoken must be enclosed in double quotes.

If you have a text file with something in it that you want to hear, use the command:

festival> (tts filename)

Replace filename with the relative path to your file, and make sure that the file is a plain ASCII text file. You can use the Tab key here for automatic file name completion.

If you have a plain ASCII text file that you wish to hear, you can call Festival from the command prompt:

festival --tts filename

For more information on using Festival, check out the man pages or type help at the festival prompt to see a list of useful commands. More documentation is also available in texinfo and HTML format on the project's site.

Flite and other open-source TTS alternatives

An alternative TTS engine is Flite (Festival-lite), a small, fast run-time binary speech synthesis engine. Flite was designed for embedded systems like PDAs as well as large server installations, which must serve synthesis to many ports. It was written in ANSI C, and is designed to be portable to almost any platform.

---

### Post by uzi09 on 2006-05-27
okay!
have you tried this yet?:
festival> (SayText "type the text you want to hear over here")

> 
o install Festival you will need to download the following source packages from the Festival download page:

* festival-1.95-beta.tar.gz -- The core festival package
* speech_tools-1.2.95-beta.tar.gz -- The Edinburgh Speech tools library
* festlex_OALD.tar.gz -- The lexicon distribution
* festlex_POSLEX.tar.gz -- The lexicon distribution
* festvox_rablpc16k.tar.gz -- The speech database


i don't think you need to do this since apt-get (or aptitude) *should* do this for you automatically.

give the above line a try and let us know what happens. be sure you have your sound turned up! :D
(ps, can you also double check to see if your sound work properly by trying out a music cd or something?)

---

### Post by clemkonan on 2006-05-27
Here is what I get from help not sure if there is a specific command I should choose
Getting Help
  (doc '<SYMBOL>)   displays help on <SYMBOL>
  (manual nil)      displays manual in local netscape
  C-c               return to top level
  C-d or (quit)     Exit Festival
(If compiled with editline)
  M-h               desplays help on current symbol
  M-s               speaks help on current symbol
  M-m               displays relevant manual page in local netscape
  TAB               Command, symbol and filename completion
  C-p or up-arrow   Previous command
  C-b or left-arrow Move back one character
  C-f or right-arrow
                    Move forward one character
  Normal Emacs commands work for editing command line

Doing stuff
  (SayText TEXT)      Synthesize text, text should be surrounded by
                      double quotes
  (tts FILENAME nil)  Say contexts of file, FILENAME should be
                      surrounded by double quotes
  (voice_rab_diphone) Select voice (Britsh Male)
  (voice_ked_diphone) Select voice (American Male)
"
festival>

---

### Post by uzi09 on 2006-05-27
when you get this prompt:
festival>

copy/paste this in the terminal and hit enter:
```

(SayText "type the text you want to hear over here")

```

let us know if you hear anything

---

### Post by clemkonan on 2006-05-27
Typing test and listening for sound I get no sound but an error message
clem@ubuntuhurricane:~$ festival
Festival Speech Synthesis System 1.4.3:release Jan 2003
Copyright (C) University of Edinburgh, 1996-2003. All rights reserved.
For details type `(festival_warranty)'
festival> The rain in Spain falls mainly on the plains
SIOD ERROR: unbound variable : The
festival>

---

### Post by uzi09 on 2006-05-27
you have to TYPE EXACTLY AS IT SAYS:

(SayText "type the text you want to hear over here")

that means brackets, double-quotes and all.
just copy paste the EXACT line and try it.

---

### Post by clemkonan on 2006-05-28
clem@ubuntuhurricane:~$ festival
Festival Speech Synthesis System 1.4.3:release Jan 2003
Copyright (C) University of Edinburgh, 1996-2003. All rights reserved.
For details type `(festival_warranty)'
festival> (SayText "type the text you want to hear over here")

#<Utterance 0xb71d2d38>
festival>
festival>

---

### Post by uzi09 on 2006-05-28
hmm, not sure what
#<Utterance 0xb71d2d38>
means...maybe you should try posting on a forum of theirs if they have one.

btw, i'm assuming you didn't get any sound did ya?

unfortunately,  i dont' think i would be able to help any further. we're really heading into the program's own territory and like i said, i think it may be best for you to try posting in their own forums. they should know more about the program and what it means.

i'll keep searchin for ya as well, but it maybe a while before i get anything cuz i'm gettin very tired now and got work tomorrow morning.

good luck
uzi

---

### Post by clemkonan on 2006-05-28
Update. Hello izi09 and everyone who so kindly helped out, I rechecked my microphone repeated your commands this morning and Eureka! we have sound. It worked.
Can you explain for me however, typically a programme brings up a menu screen say for example open office, so you see menus like File| Edit | Tools With this there is nothing similar. My speech to text programme in windows can be docked to my browser, I can right click text in MS Word and it is read to me.
I guess I have to find the manual or documentation. Bottom line your instructions ( that is collectively all of your input) worked, Please accept my thanks I could not have done it without your team . I am one step closer to exiting Windows for good

---

### Post by uzi09 on 2006-05-28
hey clemkonan.
Glad it worked out!

As far as there not being any File menus and no docked toolbar. Well, basically in Linux, there are a lot of programs that are run straight out of the terminal. Others have a nice GUI (graphical user interface). Sounds like this festival program you're using is a CLI (command line interface), so you may have to either look through its documentation to try to find out whether there is a way to turn on a graphical mode, or look for another program that does provides a GUI for you.

To see the manual for the festival program type this in:
```

man festival

```

The man command has a **TON** of manuals for pretty much every program you'll use in Linux.
Try it out with any other command:
```

man <program_name>

```

---

### Post by clemkonan on 2006-05-28
Thanks I will check it oui

---

