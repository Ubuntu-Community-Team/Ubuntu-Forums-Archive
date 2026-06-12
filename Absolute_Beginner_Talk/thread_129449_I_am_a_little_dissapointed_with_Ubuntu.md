---
title: "I am a little dissapointed with Ubuntu"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-13
Hello everybody!!!

I need some cheer up & I' ll explain.

I am trying to learn Linux, I am really trying...

So I tried to download:

1.  w32 Codecs &
2. latest Acrobat Reader from Adobe.

Both files were in ".tar.gz" format.

So I went on the following internet page to learn how to work with ".tar.gz" files:

        [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

I read everything & got so excited, so I thought I could type my new commands to install the programs manually.
I know I can use the "Synaptic Package Manager".
But my whole goal here is to LEARN.
And even though I am learning, I can NOT go & tryout what I just learned...

I was only able to type just the first command, which is:

         tar xvzf package.tar.gz           (the Unpacking procedure)

Then I entered the Folder, to see the README Files & thats it:

         cd /home/dimitris/Desktop/w32codecs*
         cat README

Then, each program says diff things:

1. The w32codec says to copy all files to 1 of the following 4 directories:

    a. To /usr/local/lib/codecs                (default directory)
    b. To /usr/lib/codecs                        (for prebuilt Mplayer)
    c. To usr/local/lib/win32                   (default past directory)
    d. To usr/lib/win32                           (default past directory)

    I know how to copy:

                    cp *.* /but_to_which_directory?

    But none of the above "later" directories existed.

    So, I went & created a "codecs" directory, in /usr/local/lib.

    Now I am supposed to type: ./configure     (to assign required system variables) 

    root@ubuntu:/usr/local/lib/codecs# ./configure
    -bash: ./configure: No such file or directory
    root@ubuntu:/usr/local/lib/codecs#

    And the program says, for the above case "a", in the README file:

    "...if you are compiling from source, but you can change that value by passing 
     the '--with-codecsdir' option to './configure'."

    What on Earth am I supposed to do?

    I replaced "./configure" with "--with-codecsdir".

    root@ubuntu:/usr/local/lib/codecs# --with-codecsdir
    -bash: --with-codecsdir: command not found
    root@ubuntu:/usr/local/lib/codecs#

    Why did I have to go through the Tutorial, if NOTHING goes according to that...
    I tried to learn it so hard...
    I am back to nowhere...
    What else is there to learn...
    Why does it have to bee soooo hard...
    That is why I get dissapointed.... now you probably understand...

    Why does the "Synaptic Package Manager" install so easily, and WE the normal
    users have to pass through these time-consuming & no result situations?

    ... and the "Synaptic Package Manager" installs so easily...
    How come that the programmers make Synaptic work so successfully, but at 
    the same time they can NOT help US & make pretty straightforward 
    instructions on HOW to install a Package? The programmers are Humans & 
    so are WE, and since they have created some code for Synaptic to work so well, 
    WHY can't they give us a pretty straightforward way to install a program 
    manually?
    I am trying to learn here - what is the meaning of learning something that I can 
    NOT put it to work?  

2. The program Adobe Reader's ReadMe file says the following:

    In the newly created AdobeReader directory, run the INSTALL  script.

    Add <adobe_install_dir>/bin to the PATH environment variable to allow 
    browsers to launch Adobe Reader, where <adobe_install_dir> is the installation 
    directory of Adobe Reader 7.0.5.

    Note: To install in a pre-defined directory, use --install_path=<dir> .

    By default, Adobe Reader is installed at /usr/local/Adobe/Acrobat 7.0. You can 
    however, specify a different location.

    It sounds like "swahilly" to me - no offence to the "swahillians" - by the way I do 
    not even know how to spell swahilly - no offense to the swahilly guys!!!

    I tried to Run the INSTALL file, only to get:

    1. Nothing... if I double-click from within the Window.
    2. The following ... if I type "install" from the Terminal window

        root@ubuntu:/home/dimitris/Desktop/AdobeReader# install
        install: too few arguments
        Try `install --help' for more information.
        root@ubuntu:/home/dimitris/Desktop/AdobeReader#

        When I typed "install --help", it was pretty suicidal....

        I needed a /bin, a path, the commands, and a pill for the headache...

        Maybe the /bin was the Recycle Bin, the path was to Hell & the command 
        was go kill yourself...

Can somebody tell me, why does it have to be so complicated?

And can somebody help me out with these...

Cause to work with ".tar" files, I need a TARZAN out there...

... and you TARZANs out there, will probably make it work in CHEETAH time...

---

### Post by Robgould on 2006-02-13
The answer to your problems so you can have some fun, then learn.  Click the link below.
 
[http://www.ubuntuforums.org/showthread.php?t=114251]("http://www.ubuntuforums.org/showthread.php?t=114251")

---

### Post by shamrock_uk on 2006-02-13
Do understand that Synaptic is there for a reason - it makes a lot of these things *very* easy. If you're finding it hard to get instructions on installing packages, it's because you normally don't need any. 

If you insist on using .tar.gz files to build your software from scratch then it will be a learning curve, but please understand that there are practically one-click solutions to your problems available - don't let your current difficulties disappoint you about Ubuntu.

With regards to your codecs:

```
sudo mkdir /usr/lib/win32
sudo cp -v ~/Desktop/w32codecs/* /usr/lib/win32/
```

Should do the trick. You can ignore the readme, that seems to be the default location where all your multimedia programmes will find them.

> "...if you are compiling from source, but you can change that value by passing 
the '--with-codecsdir' option to './configure'."

I think all this is basically talking about is adding an option so that when you finally build the package you can specify exactly where the codecs are deposited. I should imagine that you can add a line specifying which directory you want the codecs installed to in a config file, installing with the --with-codecsdir flag would then use that directory.

It's not really necessary for the codecs as they're just zipped up, simply copying them across as above should see you fine.

---

### Post by Bartender on 2006-02-13
Robgould, you beat me to it - 
dvarsam, your desire to meet new challenges head-on is admirable, but you have the rest of your life to become a Linux guru.
Give yourself a break and install Automatix.  There's a little bit of terminal work involved so you needn't feel like you're cheating ;)

Do you have a fast connection?  I hope so because Automatix wolfed down - wow - I don't know for sure, but I thought I saw at least 200 MB come thru.

After that, you might want to head on over to Gnome-Look.org and play around with some themes and desklets and wallpaper.  It's been a few days & I still haven't figured out how to install most of it so that might keep you occupied for a half hour or so...

---

### Post by BenTyreman on 2006-02-13
Skills learned here can be transferred to other packages and distros. Blindly using Automatix, while quick and easy, doesn't teach you anything.

---

### Post by Robgould on 2006-02-13
I'm all in favor of learning, but sometimes you just want to listen to an mp3 and check your e-mail.  I remember what it is like when you first come to linux and EVERYTHING is new.

---

### Post by Bartender on 2006-02-13
I don't know about "blindly" using Automatix, although in my case "two hands and a flashlight" does come to mind...

---

### Post by BenTyreman on 2006-02-13
I guess it depends on the attitude of the person. If someone says that they have checked out a few guides and want to learn how to do something, suggesting Automatix could be counterproductive (unless they were following the guides purely because they weren't aware of any alternatives).

On the other hand, if they just want to play mp3s and the like, and aren't interested in the nuts and bolts, Automatix is the way to go.

---

### Post by nurdin on 2006-02-13
[QUOTE=dvarsam]Hello everybody!!!

I need some cheer up & I' ll explain.

I am trying to learn Linux, I am really trying...

So I tried to download:

1.  w32 Codecs &
2. latest Acrobat Reader from Adobe.

Both files were in ".tar.gz" format.

So I went on the following internet page to learn how to work with ".tar.gz" files:

        [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

I read everything & got so excited, so I thought I could type my new commands to install the programs manually.
I know I can use the "Synaptic Package Manager".
But my whole goal here is to LEARN.
And even though I am learning, I can NOT go & tryout what I just learned...

I was only able to type just the first command, which is:

         tar xvzf package.tar.gz           (the Unpacking procedure)

Then I entered the Folder, to see the README Files & thats it:

         cd /home/dimitris/Desktop/w32codecs*
         cat README

Then, each program says diff things:

1. The w32codec says to copy all files to 1 of the following 4 directories:

    a. To /usr/local/lib/codecs                (default directory)
    b. To /usr/lib/codecs                        (for prebuilt Mplayer)
    c. To usr/local/lib/win32                   (default past directory)
    d. To usr/lib/win32                           (default past directory)

    I know how to copy:

                    cp *.* /but_to_which_directory?

    But none of the above "later" directories existed.

    So, I went & created a "codecs" directory, in /usr/local/lib.

    Now I am supposed to type: ./configure     (to assign required system variables) 

    root@ubuntu:/usr/local/lib/codecs# ./configure
    -bash: ./configure: No such file or directory
    root@ubuntu:/usr/local/lib/codecs#

    And the program says, for the above case "a", in the README file:

    "...if you are compiling from source, but you can change that value by passing 
     the '--with-codecsdir' option to './configure'."

    What on Earth am I supposed to do?

    I replaced "./configure" with "--with-codecsdir".

    root@ubuntu:/usr/local/lib/codecs# --with-codecsdir
    -bash: --with-codecsdir: command not found
    root@ubuntu:/usr/local/lib/codecs#

    Why did I have to go through the Tutorial, if NOTHING goes according to that...
    I tried to learn it so hard...
    I am back to nowhere...
    What else is there to learn...
    Why does it have to bee soooo hard...
    That is why I get dissapointed.... now you probably understand...

    Why does the "Synaptic Package Manager" install so easily, and WE the normal
    users have to pass through these time-consuming & no result situations?

    ... and the "Synaptic Package Manager" installs so easily...
    How come that the programmers make Synaptic work so successfully, but at 
    the same time they can NOT help US & make pretty straightforward 
    instructions on HOW to install a Package? The programmers are Humans & 
    so are WE, and since they have created some code for Synaptic to work so well, 
    WHY can't they give us a pretty straightforward way to install a program 
    manually?
    I am trying to learn here - what is the meaning of learning something that I can 
    NOT put it to work?  

2. The program Adobe Reader's ReadMe file says the following:

    In the newly created AdobeReader directory, run the INSTALL  script.

    Add <adobe_install_dir>/bin to the PATH environment variable to allow 
    browsers to launch Adobe Reader, where <adobe_install_dir> is the installation 
    directory of Adobe Reader 7.0.5.

    Note: To install in a pre-defined directory, use --install_path=<dir> .

    By default, Adobe Reader is installed at /usr/local/Adobe/Acrobat 7.0. You can 
    however, specify a different location.

    It sounds like "swahilly" to me - no offence to the "swahillians" - by the way I do 
    not even know how to spell swahilly - no offense to the swahilly guys!!!

    I tried to Run the INSTALL file, only to get:

    1. Nothing... if I double-click from within the Window.
    2. The following ... if I type "install" from the Terminal window

        root@ubuntu:/home/dimitris/Desktop/AdobeReader# install
        install: too few arguments
        Try `install --help' for more information.
        root@ubuntu:/home/dimitris/Desktop/AdobeReader#

        When I typed "install --help", it was pretty suicidal....

        I needed a /bin, a path, the commands, and a pill for the headache...

        Maybe the /bin was the Recycle Bin, the path was to Hell & the command 
        was go kill yourself...

Can somebody tell me, why does it have to be so complicated?

And can somebody help me out with these...

Cause to work with ".tar" files, I need a TARZAN out there...

... and you TARZANs out there, will probably make it work in CHEETAH time...[/QUOTE]

Okay good start, couple things though
cp *.* will only copy files with a . in them example foo.exe, In windows everything had a .abc extension, in linux a great deal of files do not have extensions. (This actually still gets me every once in a while when I forget to name a text file .txt so windows understands what it is...)

so when you did a cp *.* some of the files where not copied, namely the configure file (which doesn't have a . in it).

Instead what you want to do is cp * /target-directory

Also there is a win32 codec .deb file in the wiki somewhere, search for restricted formats which would probably be easier to use, just a dpkg -i win32-blah-blah.deb

So now hopefully you have the configure file copied over (./ just means "use the file in the current directory, don't bother searching the path of executable files" if you didn't already know that)

I replaced "./configure" with "--with-codecsdir".

very close, very very close. But you have to append --with-codecsdir to ./configure
not replace So :
./configure --with-codecsdir

Proly don't need this but its something to think about.

Synaptic Package manager uses files called .deb files which basically have all the files you need and where they are go, they are prebuilt binaries, usually easier to use than what you have done which is download a .tar.gz source code. (Although source code lets you tweak stuff) So any time you wanna use source it's slightly more difficult than binaries.

As for acrobat a couple of things, I don't want to deal with path too much cuz it is sort of complicated. Your path is the directories to look for executable files. That way you can type "gedit" in the terminal and linux will go and find /usr/bin/gedit (or wherever it is)

So best solution is to use one of the many free alternatives for acrobat reader, I think a few are included in ubuntu by default, they work for me. 

If you need the adobe version, try to find a .deb file for ubuntu (not debian which is were .deb files come from)

If you still want to do it and can't find a .deb file (or want to do this from source just because).

So the INSTALL adobe is talking about is a local install script
that means you want to type ./INSTALL (case sensitive) rather than install, install is some program in the path that I don't understand when I did a quick check.

That might help a little bit.

Can't help too much with modifying the path cuz I don't know too much about that. I tend to just make links in a directory I know is in the path, (for a list type "echo $PATH")

---

### Post by aysiu on 2006-02-13
[QUOTE=dvarsam]
I am trying to learn Linux, I am really trying...

So I tried to download:

1.  w32 Codecs &
2. latest Acrobat Reader from Adobe.

Both files were in ".tar.gz" format.[/quote] This was your first mistake. You can just get the .deb for w32codecs and then download it your desktop and type ```
cd Desktop
sudo dpkg -i w32*.deb
``` and it'll install--no dependencies, compiling, or anything. You can also install Adobe's Acrobat Reader through Synaptic if you have the right repositories enabled (see the first link of my signature).

How about asking what the simplest way to do stuff is before complaining about how disappointed you are with Ubuntu?

Or... just use Mepis or PCLinuxOS.

---

### Post by dvarsam on 2006-02-13
[QUOTE/]
I think all this is basically talking about is adding an option so that when you finally build the package you can specify exactly where the codecs are deposited.
I should imagine that you can add a line specifying which directory you want the codecs installed to in a config file, installing with the --with-codecsdir flag would then use that directory.

It's not really necessary for the codecs as they're just zipped up, simply copying them across as above should see you fine.[/QUOTE]

I performed the copy successfully.
But that does not change any of my results...

So how do I apply the remaining commands?

./configure	        ( < - The Configure Procedure assigns System Variables)
make			( < - The Building Procedure creates the Executable Program)
make install	      ( < - The Install Procedure installs the Program)

Cause when I type "./configure --with-/win32" I get:

root@ubuntu:/usr/lib/win32# ./configure --with-/win32
-bash: ./configure: No such file or directory
root@ubuntu:/usr/lib/win32#

I have NO clue...

---

### Post by shamrock_uk on 2006-02-13
Sorry, I'll try to be clearer. 

You don't have to do anything else for the codecs - any player using the xine engine, or Mplayer, will automatically look in the /usr/lib/win32 directory and use the codecs.

Just to be clear - you don't need to do the usual ./configure, make, make install procedure for the codecs.


Where you do need to do it is when you're installing a programme that you have to compile from source. Then *./configure* checks your computer for all the requirements, *make* compiles it and *make install* installs it. 

The codecs are simply a bunch of inanimate files and don't require any kind of compiling - they are not programmes - and therefore there's no need to do any of the above in this particular case.

Edit:  Just a note, if you are doing lots of compiling then it'll make life a lot easier if you dip into the packaging system just once and do this:

```
sudo apt-get install build-essentials
```

That will solve a lot of initial problems that you may be having, although I would reiterate that you are going about this in probably the hardest way possible ;)

---

### Post by poofyhairguy on 2006-02-14
[QUOTE=BenTyreman]Skills learned here can be transferred to other packages and distros. Blindly using Automatix, while quick and easy, doesn't teach you anything.[/QUOTE]

Maybe not. But it saves your stamina to fight another day. Makes all that easy, so you can spend time making this program how you want, or making that theme how oyu want, or swaping Kwin for Metacity, etc.

---

### Post by Jucato on 2006-02-14
Automatic/Easy Ubuntu: use this if you want to get working immediately, and save learning for later.
Wiki/dpkg/apt-get: if you're not in a hurry and want to learn some basics.
./configure,make,make install: only when you've learned a bit and fill a bit confident.

...different flavors for different tastes. :D

---

### Post by GreyFox503 on 2006-02-14
[quote=dvarsam]
So how do I apply the remaining commands?

./configure            ( < - The Configure Procedure assigns System Variables)
make            ( < - The Building Procedure creates the Executable Program)
make install          ( < - The Install Procedure installs the Program)
[/quote] 
Well, since no one has answered the original question, I'll tell you why you're getting that error with ./configure.

Before you execute those commands, cd to the directory where the source files are.  That would be all the new stuff that unpacked itself from the .tar.gz file.  Go inside the directory, then run the commands.

It's because 'configure' is the name of a specific file inside the source's directory that you downloaded, it's not part of your system.

Depending on the size of the program & your computer's speed, compiling from source (the 'make' step) could take a while.

Also, you should run 'make install' as root, or with sudo:

```
sudo make install
``` 
Because this command will install the compiled program to directories on your system like /usr/bin where normal users don't have write permission.

---

