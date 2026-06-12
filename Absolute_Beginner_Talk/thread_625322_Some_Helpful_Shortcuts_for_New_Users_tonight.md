---
title: "Some Helpful Shortcuts for New Users tonight"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-11-27
One of the things I wish I would have known when first starting out was how to add alias' to commands.

So tonight I figured I would just throw this out there for any new Linux/Ubuntu users who are browsing the forums.

Open up the terminal and enter:

```
gedit .bashrc
```

Now go to the bottom of this file and add these lines to it:

```

export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '
alias update="sudo aptitude update"
alias install="sudo aptitude install"
alias upgrade="sudo aptitude safe-upgrade"
alias remove="sudo aptitude remove"
alias g="gnome-open"

```

Save the file, close the terminal and reopen it.  Basically what's going on is you have now created alias' for commands like "sudo aptitude update" so that now all you need to enter is sudo update and the command is now shortened down.  I haven't done this myself, maybe someone else can confirm it but if I put an "&&" after the command will it still work for an alias?

The first line you changed, changes the color of every directory you are in to kind of help you visualize differences in the file system while you are at the terminal.

The last one is the one I use the most is the "gnome-open" command to open anything.  Here's an example of me opening the terminal and quickly getting to a movie by navigating to my Movies folder, using ls to show all the files that aren't hidden and then opening one with by simply typing "g 300"
```
Blackbeard ~: cd Movies
Blackbeard ~/Movies: ls
300                  Darjeeling Limited  The Bourne Ultimatum
American Gangster    Pulp Fiction        The Charles Bukowski Tapes
Catch Me if You Can  Rushmore            The Royal Tenenbaums
Blackbeard ~/Movies: g 300
VLC media player 0.8.6c Janus
Blackbeard ~/Movies: [00000281] main playlist: stopping playback

```

One last tip I will leave you with to open up terminals quicker is to go to System > Preferences > Keyboard Shortcuts

You will see that there is no bind set for "Open a Terminal" under the Desktop portion.  I have mine set to be as "ctrl + alt + x" but anything will work.

Well that's all for now, not really much of a guide just some tips to help you out tonight and make your Ubuntu experience quicker and easier.

---

### Post by Dr Small on 2007-11-27
For,
```
export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '
```

Is there some place that lists colors ?

---

### Post by siciliancasanova on 2007-11-27
You need to adjust the values of "35m" and the "33m"

[http://www.understudy.net/custom.html#table2]("http://www.understudy.net/custom.html#table2")

---

### Post by Dr Small on 2007-11-27
Ok. Thanks for the tip ;)

---

### Post by siciliancasanova on 2007-11-28
Ok I just posted this on my website for better reference: [http://anthonylicari.com/use-some-alias-quick-navigation-terminal-ubuntu]("http://anthonylicari.com/use-some-alias-quick-navigation-terminal-ubuntu")

---

