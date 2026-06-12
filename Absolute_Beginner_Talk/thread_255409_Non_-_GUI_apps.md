---
title: "Non - GUI apps"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by bigbearomaha on 2006-09-11
Is there a list  somewhere of non-GUI apps to access from the command line.

I am an immersion type learner, so the best way for me to figure out the intricacies of the commands and system is to only use the command line for awhile.  Most of the apps I seem to find are GUI desktop apps though.

I am sure I am not seeing something right in front of me, but can anyone point me in the right direction?

I appreciate all constructive assistance

Big Bear

---

### Post by tatimmer on 2006-09-11
You might look thru your man page directory (/usr/local/man...), I also have a file called "tomslinuxtips" which is an alphabetical list of command line tools I use.

---

### Post by Brunellus on 2006-09-11
thread moved to more appropriate forum. "Testimonials" is really about success/failure reports....

---

### Post by Solver on 2006-09-11
Many command-line apps are something you can install for yourself, so naturally there's a very wide selection. I can recommend [http://linuxcommand.org/](http://linuxcommand.org/) as something that has the most commonly used commands. In the subfolders of /usr/share/man, you can see the list of most programs you have installed.

---

### Post by Klaidas on 2006-09-11
You don't need to go back to stone age just to learn linux command - you could better use some guides (like the linux lessons in my sig) :)

---

### Post by bigbearomaha on 2006-09-11
I am more looking for more than the commands actually.  Ie word processor, music player, database tools, etc...

Perhaps I am calling too far back into pc history.  I recall when there were everyday apps that executed from command line without GUI.

It's just the way I like to do things.  Total immersion etc.


Thanks to all,
Big Bear

---

### Post by Aurdal on 2006-09-11
Talking of command-line application, I've been wondering for a while if theres's a command-line music player?

---

### Post by Brunellus on 2006-09-11
> **bigbearomaha said:**
> I am more looking for more than the commands actually.  Ie word processor, music player, database tools, etc...

Perhaps I am calling too far back into pc history.  I recall when there were everyday apps that executed from command line without GUI.

It's just the way I like to do things.  Total immersion etc.


Thanks to all,
Big Bear
The superminimalist "word processing" solution is one of the standard *nix text editors:  vim, emacs, or nano.  all three are included.  I use vim.  

for music playing, there's quark or mpd.  for individual files, there's always mpg123/ogg123.  

web browsing can be accomplished via lynx (my favorite), or links (which can even give a graphical version from the commandline, without an X server, using libsvga, apparently).  

for net news (usenet's not dead!), I prefer slrn.

For e-mail, use mutt

For IRC:  irssi-text

For AIM:  nAIM

That's all I can think of off the top of my head.

---

### Post by pbaehr on 2006-09-11
> **Aurdal said:**
> Talking of command-line application, I've been wondering for a while if theres's a command-line music player?

mplayer can play music from the command line, I believe.

---

### Post by Indras on 2006-09-11
There's three command-line web page browsers that I know of: Lynx, Links, and w3m.  Links is by far my favorite.  I always install it in every Linux OS I try, that way if I accidentally break my x-server I still have a way to check FAQs online.

To play MP3's and other music from command line, use the command "play" like this:
```
play song.mp3
```

If you want to play this in the background and still use your terminal, you have to use this instead:
```
play --silent song.mp3 &
```

There's lots of information on running things in foreground or background, so you can do everything from a single terminal... I won't delve into details, go find a FAQ!

For a good IRC chat client, use irssi.  The command-line version of synaptic is aptitude.  In ubuntu use "sudo aptitude" to play around with it.  F1 will bring up a list of the hotkeys.

There's also a decent file-manager like dosshell, called midnight commander.  In synaptic it's just called "mc"

To cut and paste with the mouse in CLI, install gpm and answer the configuration questions.  Then, left-click and drag to highlight something, and middle-click to paste it.

bitlbee supposedly will let you use AIM and Yahoo accounts from CLI, but I've never tried it.

Nothing else comes to mind, google around and you should find plenty of others I don't know of.

---

### Post by cwaldbieser on 2006-09-12
> **bigbearomaha said:**
> I am more looking for more than the commands actually.  Ie word processor, music player, database tools, etc...

Perhaps I am calling too far back into pc history.  I recall when there were everyday apps that executed from command line without GUI.

It's just the way I like to do things.  Total immersion etc.


Thanks to all,
Big Bear

Tap the TAB key twice at the command line.  You will get a big list of all the commands you can run.  If you type a couple letters first and then TAB, you will see all the commands that start with those letters.

---

### Post by bigbearomaha on 2006-09-17
Thank you for your help.  I  LOVE mpg123.  great things.

Big Bear

---

### Post by bigbearomaha on 2006-09-17
I have found mpg123 and ogg123 as command line music players.  they are great.  also  mp32ogg is a very good command line converter app to make mp3's into ogg vorbis format.  now from what I've read, it really isn't recommended to convert as you lose more of the file but it's neat to know about.

Big Bear
=D>

---

### Post by IYY on 2006-09-17
There is no command line word processor (for obvious reasons) but there are many text editors (**vi**, **Emacs** and the simpler **nano**) and **LaTeX** if you want to do advanced formatting. The way this works is like this: you write your text, then format it by adding tags (kinda like in HTML), run it through a program and get a beautiful PDF output. It's perfect for writing things like reports, theses and books because you don't have to worry about making it look good, it's all done automatically.

**centericq** is an IM client like Gaim. It supports ICQ, MSN, AIM, Yahoo and Jabber.

Another useful command-line app is **bitchx**. It's a command line IRC client.

To install software, you can use **aptitude**.

I use the shell for file management, but some like to use **Midnight Commander**, a clone of Norton Commander for DOS.

---

### Post by bigbearomaha on 2006-09-17
Thank you all for you input, 

I have found many command line apps based on your suggestions.  most work very well.

Gnome-Commander is interesting.  I can see the value in it.still not as flexible as the complete command line but certainly valuable.  I did notice that it does have a command line in it also, so you really have it all if you want it .

javaps is kinda wierd as a process browser I guess. it allows one to alter process by kill, nice, or unnice, etc

wierd look though in the lava lamp.  xcruiser is another wierd appactually, these are both not CL but GUI instead. I bumped into those looking for gnome-commander.

Big Bear

---

### Post by guyforget on 2006-11-27
This is way late, but you never know when someone else will be searching for the same information.  

Ive been using a Linux desktop for at least 4 years now, and I still like to use the CLI.  Some of my favorites are:

NCFTP - CLI FTP Client
WGET - for my http downloads
IRSSI - for idling in irc chatrooms 
BitTorrent - Yes, behind the GUI there is are actually two cli's also installed: btdownloadheadless and btdownloadcurses both of which have the same configurability of the GUI client.  You can also use btlaunchmany and btlaunchmanycurses to start an entire folder of .torrent files all at once.
The of course theres Top, and Nano.

---

