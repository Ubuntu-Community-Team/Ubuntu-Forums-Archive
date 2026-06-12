---
title: "Something Like .bat File(shortcut?)"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-31
Hello!
I have to use some commands every time. I wanna put them in file and when I click the file they command start automatically. Is it possible? Or even It would be better for me if I can make a shortcut key for them. e.g. alt+t for 2 commands and ctrl+t for two other. Is it possible?
Thank you.

---

### Post by Whiffle on 2008-01-31
Yep!

Open up your favorite text editor, write the commands you wish to use in it, and save the file.  I usually make a .bin directory in my home directory to keep scripts and stuff in.  Next, open up a terminal, cd to the directory where you saved the file, and run:
```

chmod +x nameoffile

```

Now, to run it, you can do ./nameoffile.  In addition, if you look through the system preferences somewhere you should be able to map it to a shortcut key.  On KDE its under control center > regional and accessability > Keyboard shortcuts.  KDE also seems to require that commands that have shortcuts to be in the kmenu.  You can add them with the program kmenuedit.

---

### Post by oedha on 2008-01-31
yes.......
just save as *.sh
then excecute it with sudo filename.sh 
or
double click from nautilus...and choose run from terminal

~E~

---

### Post by Hoom@n on 2008-01-31
And how can I make shortcuts for them by using terminal? (I mean can I use gconftool-2 and if yes how can?!)

---

### Post by oedha on 2008-01-31
when i made a script....named example.sh
i just save and put it on desktop
i dont need shortcut.......
when i am on desktop....jsut double click and choose run from terminal
from terminal just type :=> sudo sh /home/username/Desktop/filename.sh

that's what i done
~E~

---

### Post by Hoom@n on 2008-01-31
Thanks, I know these. I just wanted a shortcut. And I know its possible, but I don't know how and I wanted this forum users to help me.
but thanks.

---

### Post by jordanmthomas on 2008-01-31
I don't think this is what you're looking for, but I'll throw it out:
```
ln -s /bin/sh ~/mysh
```
will create a symbolic link (shortcut more or less) to /bin/sh called mysh in your home directory.  If you try to run ~/mysh /bin/sh will actually get run.

Now, if you want to only run these in a terminal, I suggest creating an alias for it.
In your ~/.bashrc, you can add aliases to commands.  For example:
```
alias homesize="du -sh ~"
```
Then, you could type in homesize and du -sh ~ would be run.

Lastly, you can create a script to run a program
The first line of your script should point to an interpreter that will read your script (typically /bin/bash)
```
#!/bin/bash
somecommand -arg1 -arg2 etc
someothercommand

```
If you make this script executable (chmod +x filename) you can then run it whenever you want.  If it's executable and you double click it in nautilus, you can run it.

Does this make sense?  Aside from making a .desktop file (which may be exactly what you're after...look up how to create launchers in gnome), these are the only "shortcuts" I know of.

---

### Post by Hoom@n on 2008-01-31
Thanks alot for the help. How about KDE? CanI run a file there which ctrl+somebutton?
Again thanks alot.

---

### Post by qazwsx on 2008-01-31
> **oedha said:**
> 
then excecute it with sudo filename.sh 


**Never** use sudo if you are not doing it for administration purposes. It could screw up file permissons or even whole system.

```
sh  script
``` 
 But giving excecuting permisions more convinient ```
chmod +x script
``` -->

Now you can
```
 ./script
```
Or add new line in your .bashrc
like
```
export PATH=$PATH:~/.my-scrpts:
```
 (after .bashrc update like logout)
```
script
```

---

### Post by Hoom@n on 2008-01-31
Thanks. Please tell me if i'm right or not: By making my sh file a script I can run it from any place in terminal. Am I right? If not, why should I make it a script?

---

### Post by qazwsx on 2008-01-31
Yep I prefer to have my own scripts in my own home folder. I like to create hidden directory called /home/me/.scripts where I put all my scripts. Assuming that you can execute them (chmod +x file). Then you can run your script just by typing its name in terminal.
But first you have to add that directory into your PATH  by adding line to your  /home/you/.bashrc 

Like this
```
export PATH=$PATH:/home/me/.scripts:
```

Now you can log out and log in and your .bashrc is updated (please someone tell  me if there is easier way).

---

### Post by jordanmthomas on 2008-01-31
> **qazwsx said:**
> 
Now you can log out and log in and your .bashrc is updated (please someone tell  me if there is easier way).

After doing that you could type
```
source ~/.bashrc
```
You'd have to do this in each terminal you open until you logged out then back in though, I think.

---

### Post by Hoom@n on 2008-01-31
Escuse me. It get a bit hard for me! 
This is what I did:
Made a .sh file in home directory and wrote the commands I needed inside it and nothing more. (I think you said I've to write something in the first line) Now I can run it by sh filename.sh in my terminal.
Now please tell me what should I do, all in one post, a to z, to make it a script and make that script a shortcut.
Thanks alot!

---

### Post by jordanmthomas on 2008-01-31
First, you need to add this to the top of your script:
```
#!/bin/bash
``` so that when you make it executable, it knows to run with bash.

```
chmod +x filename.sh
``` will make it executable, so you don't have to put sh filename.sh and you can just run ./filename.sh

Now, most people want to be able to run their script without specifying where exactly it is, right?  To do this you will need to put the folder somewhere in your PATH.  Personally, I make a bin directory in my home folder for scripts I write.
```
mkdir ~/bin 
mv filename.sh ~/bin  #put script in bin folder

```

Now, you need to add you newly made bin folder to your PATH so bash can find your script.
```
echo "export PATH=$PATH:/home/[COLOR="Red"]yourusername[/COLOR]/bin" >> ~/.bashrc
```  Be sure to change yourusername to your user name.

Now, log off and back on.  Now, you can run filename.sh wherever you want.  You can run it in a terminal, you can run it in the gnome run dialogue (alt + F2), wherever you want.  

Also, it's easier for me to remember scriptnames if I just name them filename instead of filename.sh.  It's a matter of preference, of course.  :)  Hope this helps.

---

