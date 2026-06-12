---
title: "Installing from Konsole"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Red David on 2007-06-14
Please bear with me if I'm reinventing a question about the wheel. I'm a complete newbie with linux. So far, pretty smooth but I'm having terminal anxieties in regard to installing software that isn't yet in the repositories. Specifically, I want to install Thunderbird 2.0 and I have seen any number of differing instructions for installation. I want to install it so that  it shows up in the K menu and can be launched from there at a click.

I actually used Konsole to install easyubuntu which I used to install TB 2.0, which showed up in the K menu and wouldn't launch. Trying in Konsole gave an error. Sorry I can't replicate  now because i un-installed.

Part of my confusion regards paths. I downloaded TB 2.0 to /home/david/applications/ (obviously, I created the applications folder) but have just moved it to the desktop. Ubuntuzilla looked like it might be the ticket but it won't download.

All suggestions welcome.

---

### Post by Inxsible on 2007-06-14
I have attached a script which will download and install the latest Thunderbird from the mozilla site.

Open the terminal and cd to the directory where you store the script and then type in
```
sudo installnewthunderbird.sh
```

Enjoy the latest Thunderbird

---

### Post by Inxsible on 2007-06-14
Oh and it will put in the entries in the menu too. I use Gnome, and it put the entries in Applications--> Internet --> ThunderBird Mail

---

### Post by Red David on 2007-06-14
Thanks. Checking this thread from my OS X box. I'll download the script when I fire up my Kubuntu and let you know how it goes. I'm assuming I can download the script to either desktop or my documents folder.

---

### Post by Inxsible on 2007-06-14
> **Red David said:**
> Thanks. Checking this thread from my OS X box. I'll download the script when I fire up my Kubuntu and let you know how it goes. I'm assuming I can download the script to either desktop or my documents folder.
Doesn't matter where you download ...as long as you cd into that folder to execute it or give the full path

---

### Post by Paul820 on 2007-06-14
I got thunderbird2 from automatix2. It takes out the old 1.5 and installs version 2.0. Really easy.

---

### Post by Inxsible on 2007-06-14
> **Paul820 said:**
> I got thunderbird2 from automatix2. It takes out the old 1.5 and installs version 2.0. Really easy.
I would stay away from Automatix. The disadvantages far outweigh the advantages. This is just my personal experience, however.

---

### Post by Paul820 on 2007-06-14
What are the disadvantages? Is there something wrong with it? If there is i'll stop using it.

---

### Post by Inxsible on 2007-06-14
The disadvantage i saw was that it tries to automate a lot of stuff which is simple to do anyway. I'd rather get my hands dirty trying to figure out things by myself

i have seen it mess up my fstab for eg. I cant rbr all of them now. But if it works for you, you might wanna continue using it.

---

### Post by Red David on 2007-06-14
Actually, Automatix2 was my first real foray into the terminal. All went well and I proceeded to fetch TB 2 (didn't have 1.5 installed to begin with) and all seemed to go well, including a shiny new item in my K menu. Which wouldn't actually do anything. Typing Thunderbird in Konsole just returned an error, so I used Automatix to remove 2 and haven't tried it since.

---

### Post by Inxsible on 2007-06-14
> **Red David said:**
> Actually, Automatix2 was my first real foray into the terminal. All went well and I proceeded to fetch TB 2 (didn't have 1.5 installed to begin with) and all seemed to go well, including a shiny new item in my K menu. Which wouldn't actually do anything. Typing Thunderbird in Konsole just returned an error, so I used Automatix to remove 2 and haven't tried it since.

did you try the script i gave you earlier ?

---

### Post by Paul820 on 2007-06-14
I have not had any problems with it so far. Guess i've been lucky. I'm still learning ubuntu myself so when i get a bit more experience i will do more things myself. At the moment it's convenient, although i will keep an eye out for any mistakes automatix does.

---

### Post by Red David on 2007-06-14
Inxsible: My apologies, I haven't yet fired up my linux installation yet today but your script will be first order of business and I will report back. Eager to take baby steps into terminal land.

---

### Post by Inxsible on 2007-06-14
> **Paul820 said:**
> I have not had any problems with it so far. Guess i've been lucky. I'm still learning ubuntu myself so when i get a bit more experience i will do more things myself. At the moment it's convenient, although i will keep an eye out for any mistakes automatix does.

Here's another user whose fstab got screwed up due to Automatix. Glad you have been lucky
[http://ubuntuforums.org/showthread.php?t=474088](http://ubuntuforums.org/showthread.php?t=474088)

---

### Post by Red David on 2007-06-15
No luck so far. Here is my terminal session.

david@Beowulf:~$ cd /home/david/Documents/Downloads (which is where script downloaded)
david@Beowulf:~/Documents/Downloads$ sudo installnewthunderbird.sh
sudo: installnewthunderbird.sh: command not found
david@Beowulf:~/Documents/Downloads$


I'm sure I'm missing something obvious but don't know what

---

### Post by Inxsible on 2007-06-15
> **Red David said:**
> No luck so far. Here is my terminal session.

david@Beowulf:~$ cd /home/david/Documents/Downloads (which is where script downloaded)
david@Beowulf:~/Documents/Downloads$ sudo installnewthunderbird.sh
sudo: installnewthunderbird.sh: command not found
david@Beowulf:~/Documents/Downloads$


I'm sure I'm missing something obvious but don't know what

sorry, I forgot to tell you that you have to make it an executable first
try this: Cd to the folder where you have downloaded the file.
```
sudo chmod +x installnewthunderbird.sh
```
then ```
./installnewthunderbird.sh
```

---

### Post by jordanmthomas on 2007-06-15
after you've cd'd into the directory you need to type one of these two things:
you typed:
```
sudo installnewthunderbird.sh
```
Unless the current directory is in your PATH (which is a BAD thing to have) this won't work.  You need to specify the directory
```
chmod +x installnewthunderbird.sh
```
make it executable
```
sudo [COLOR="Red"]./[/COLOR]installnewthunderbird.sh
```
the . represents "directory I am currently in"

alternatively, you could pass the file as an argument to sh like so:
```
sudo [COLOR="#ff0000"]sh[/COLOR] installnewthunderbird.sh
```

Try one of these and see if it works then.


And I was beaten.  Sorry.  :)

---

### Post by Red David on 2007-06-15
Morning here and starting at it again. Thanks to all of you. I am making progress (gratifying to see lines appear in response to a command) but not quite there yet. Have arrived at:


Welcome to the Ubuntuzilla Thunderbird script version 3.1.0

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

Please enter a valid action argument for the script. Run 'bash installnewthunderbird.sh -h' for help.

Not at all sure what an argument should/would be.

Nevertheless, I am encouraged. Thank you all again.

---

### Post by Inxsible on 2007-06-15
> **Red David said:**
> Morning here and starting at it again. Thanks to all of you. I am making progress (gratifying to see lines appear in response to a command) but not quite there yet. Have arrived at:
 
 
Welcome to the Ubuntuzilla Thunderbird script version 3.1.0
 
This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)
 
Please enter a valid action argument for the script. Run 'bash installnewthunderbird.sh -h' for help.
 
Not at all sure what an argument should/would be.
 
Nevertheless, I am encouraged. Thank you all again.
I think its -install
 
But to be sure run 'bash installnewthunderbird.sh -h ' like it says...and it will list out the options for you

---

### Post by Red David on 2007-06-15
Hmm...I'm continuing to miss something. Just getting a series of command not founds

david@Beowulf:~/Documents/Downloads$
david@Beowulf:~/Documents/Downloads$ bash installnewthunderbird.sh -h

Welcome to the Ubuntuzilla Thunderbird script version 3.1.0

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any prob        lems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://pykeylo](http://pykeylo)        gger.sourceforge.net/wiki/index.php/Ubuntuzilla

Usage: installnewthunderbird.sh -install | -remove [OPTIONS]
-install: install Mozilla build of Thunderbird
-remove: remove Mozilla build of Thunderbird
OPTIONS:
-h: print help
-d: run with some debug output
david@Beowulf:~/Documents/Downloads$ -install: install Mozilla build of Thunderbird
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -i
bash: -install:: command not found
david@Beowulf:~/Documents/Downloads$ -install
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -i
bash: -install: command not found
david@Beowulf:~/Documents/Downloads$ installnewthunderbird.sh -install
bash: installnewthunderbird.sh: command not found
david@Beowulf:~/Documents/Downloads$ install Mozilla build of Thunderbird
install: target `Thunderbird' is not a directory
david@Beowulf:~/Documents/Downloads$ -h
Usage: command-not-found [options] <command-name>

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -d DATA_DIR, --data-dir=DATA_DIR
                        use this path to locate data fields
bash: -h: command not found
david@Beowulf:~/Documents/Downloads$ -h, --help
Usage: command-not-found [options] <command-name>

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -d DATA_DIR, --data-dir=DATA_DIR
                        use this path to locate data fields
bash: -h,: command not found
david@Beowulf:~/Documents/Downloads$ -install:
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -i
bash: -install:: command not found
david@Beowulf:~/Documents/Downloads$

---

### Post by jordanmthomas on 2007-06-15
```
sudo ./installnewthunderbird.sh [COLOR="Red"]-install[/COLOR]
```
the -install should go as an argument for the installation script.

---

### Post by Inxsible on 2007-06-15
Try this one last time:
 
cd to the directory where you have your script.
 
```
sudo chmod +x installnewthunderbird.sh
```
 
after that returns, immediately do this:
 
```
sudo ./installnewthunderbird.sh -install
```
 
 
If that doesn't work, I don't know what else to tell ya :(

---

### Post by Inxsible on 2007-06-15
whoops, i think i missed the last page before posting

---

### Post by Red David on 2007-06-15
Hooray! You guys have been terrific and I've enjoyed the learning process. Of course, I need lots more practice.

---

### Post by Inxsible on 2007-06-16
> **Red David said:**
> Hooray! You guys have been terrific and I've enjoyed the learning process. Of course, I need lots more practice.

Glad to have helped

---

### Post by nanotube on 2007-06-26
> **Inxsible said:**
> I have attached a script which will download and install the latest Thunderbird from the mozilla site.

Open the terminal and cd to the directory where you store the script and then type in
```
sudo installnewthunderbird.sh
```

Enjoy the latest Thunderbird

hi,
thanks for pointing out ubuntuzilla... but you are using a pretty old version. ubuntuzilla is now up to version 4.1.0 :)
of course, the old one still seems to work, but it is no longer supported, so if something changes on the mozilla site, that's that. so for "the future", you might consider just pointing over to the [ubuntuzilla homepage]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla") (which, by the way, contains detailed running instructions) or making sure to post the latest release. 

glad everything worked out, though. :)

-nanotube (ubuntuzilla creator)

---

