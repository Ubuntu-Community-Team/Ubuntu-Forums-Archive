---
title: "Terminal ls colors"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ubz on 2007-06-21
Hi, I've tried applying the info in this Howto to change colors but no success using Feisty
[http://ubuntuforums.org/showthread.php?t=41538](http://ubuntuforums.org/showthread.php?t=41538)

This approach was suggested in another post.
Run the command "dircolors", copy the output to, for instance, ~/.dircolors, then source that file in ~/.bashrc. You can of course change the colors for each filetype as you wish.

I'm confused what modification/edit needs to be made to ~$ .bashrc before sourcing it.

Yes I am a noob and the reason I want to change the terminal dark blue directory color is eyesight related.

Thanks for any help!

---

### Post by 5-HT on 2007-06-21
Here's a page that indicates the available colour codes: [http://www.ibm.com/developerworks/linux/library/l-tip-prompt](http://www.ibm.com/developerworks/linux/library/l-tip-prompt)
And, of course: [http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html)

dircolors will use the same colour codes.

---

### Post by h0ax on 2007-06-21
based on the previous thread it looks like
> 
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    [COLOR=DarkRed][ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors" <--THIS is what will change where it looks for the dircolors file.
    [ -e "$DIR_COLORS" ] || DIR_COLORS=""
    eval "`dircolors -b $DIR_COLORS`"[/COLOR]
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi


---

### Post by h0ax on 2007-06-21
Sorry, forgot the rest so edit your .bashrc with a text editor (Gedit, if you prefer) and put in those lines that are red.

---

### Post by ubz on 2007-06-21
Thanks for the help.  The .dircolors file is working now!  Could you please tell me how to set the terminal color change so it will be global for all users and sudo.

An easier way to login to Ubuntu Forums (Firefox extension).
[https://addons.mozilla.org/en-US/firefox/addon/4429](https://addons.mozilla.org/en-US/firefox/addon/4429)

---

### Post by pmg on 2007-06-21
> Could you please tell me how to set the terminal color change so it will be global for all users and sudo.
Put your .bashrc updates in a file in /etc/profile.d/ that ends with **.sh** which will be sourced by any bash shells as they are started.

---

### Post by ubz on 2007-06-22
> **pmg said:**
> Put your .bashrc updates in a file in /etc/profile.d/ that ends with **.sh** which will be sourced by any bash shells as they are started.

There isn't a /etc/profile.d directory.  Please correct me if I'm misunderstanding your instructions, I mkdir 'profile.d' then create a file anyname.sh that contains the .bashrc updates.  By updates do you mean the few lines of code I added/modified in the ~$ .bashrc file? -thanks

---

### Post by pmg on 2007-06-22
> There isn't a /etc/profile.d directory. Please correct me if I'm misunderstanding your instructions, I mkdir 'profile.d' then create a file anyname.sh that contains the .bashrc updates. By updates do you mean the few lines of code I added/modified in the ~$ .bashrc file? -thanks
Ops, my bad.  I got my "RedHat" and "Ubuntu"-isms mixed up.  That's how things are set up in RH Linux.

In Ubuntu, you want to add it to **/etc/bash.bashrc**, and yes, take the lines you put in your .bashrc (which is your personal startup file) and put them in /etc/bash.bashrc (which is the system-wide startup file.)

Sorry about the confusion.

---

### Post by dannyboy79 on 2007-06-23
i've tried this and it isn't working. I didn't however restart the machine yet but I wouldn't think that I would have to? I did retart the gnome-terminal and that's it. I created the file called .dircolors within my home dir, and all I changed was the dir color from blue to white because I have a different color scheme for my entire shell. Then I added the following to both the /etc/bash.bashrc file as well as the ~/.bashrc file and it's still not working. My goal is so that if I do an ls command, I want the files and Directories to be white so I can see them a little better, you'll see what I mean in my example below.

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
[ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors" <--THIS is what will change where it looks for the dircolors file.
[ -e "$DIR_COLORS" ] || DIR_COLORS=""
eval "`dircolors -b $DIR_COLORS`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

I have pasted my .dircolors at pastebin and the owner and permissions are as follows: 
-rw-r--r--  1 daniel daniel   2780 2007-06-23 09:57 .dircolors
[http://pastebin.com/934718](http://pastebin.com/934718)

Here's whats still occuring as far as colors of directories: [[IMG]http://img453.imageshack.us/img453/6664/lscolorsgnometerminalfn1.png[/IMG]](http://imageshack.us)
Shot at 1969-12-31
Any help on this would be appreciated.

---

### Post by ubz on 2007-06-23
> **dannyboy79 said:**
> 
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
[ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors" <--THIS is what will change where it looks for the dircolors file.
[ -e "$DIR_COLORS" ] || DIR_COLORS=""
eval "`dircolors -b $DIR_COLORS`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi


Hi, You probably know this. Don't include this as part of the bashrc code ( <--THIS is what will change where it looks for the dircolors file.)

The default .dircolor is DIR 01;34 # Directory
if you change the 34 (text color) value use a text color (37 is white) Note: text and background values are different for the same color.

Default DIR 01;34 # Directory (when I changed the 01 value to 00 which determines BOLD etc the color I assigned for text was messed up so I left the first value at the default 01.

I added an additional value (background color) to DIR 00;34 so it looks like DIR 44;01;35

After modifying .bashrc I sourced it then the dir color change took effect.
```
~$ . ~/.bashrc 
```

---

### Post by dannyboy79 on 2007-06-25
thank you, that must have been it. I'm so silly for not realizing that. I actually thought it was commented out but now that you showed me, it's not. THanks so much.

---

