---
title: "How do you remember commands"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-20
I've been perusing the forums today and I want to try a lot of things when I get home, but I got to wondering:   What does everyone do to remember all of the commands to enter into the terminal?  

I'm a total noob to Linux so I know there is no way I'm going to be able to memorize them.  I  was thinking about using notepad (or the Linux compliment) but wanted to know how others do it.

---

### Post by amohanty on 2005-12-20
Keeping a copy does help, but eventually it will be usage that will make it more persistent in your head, and will also make you mad when you cant imagine that MS doesnt provide anything comparable to even a % of those tools :)

---

### Post by frodon on 2005-12-20
The more you use them, the more you know them ;)

---

### Post by deNoobius on 2005-12-20
One thing you can do is type "history" without the quotes at the command line (or better, "history | less" without the quotes, if you have a very long list) and it will list all the commands you have entered, which you can then review.  You can even force it to make a text file of your history from the command line.  $:  history > history.txt (can be any file name).  

Also, you'll learn the common commands by practice.

Also, check this out: [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php).

---

### Post by 23meg on 2005-12-20
Practice doesn't make perfect, but it makes fluent. Tab completion also helps.

---

### Post by ertai on 2005-12-20
In the beginning I used a piece of papier to remember the most basic command's I needed. But eventually you'll get to know them and then you don't need that any more

---

### Post by Sgood1971 on 2005-12-20
[Google Search]("http://www.google.com/search?q=bash+command+reference&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial")

came up with [this]("http://www.ss64.com/bash/") and [this]("http://www.faqs.org/docs/bashman/bashref_toc.html")

---

### Post by 23meg on 2005-12-20
[QUOTE=deNoobius]One thing you can do is type "history" without the quotes at the command line (or better, "history | less" without the quotes, if you have a very long list) and it will list all the commands you have entered, which you can then review. You can even force it to make a text file of your history from the command line. $: history > history.txt (can be any file name).[/QUOTE]
Here's another VERY practical trick that I can't live without.. enter the following in your ~/.inputrc file:
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```and you can search in your bash history on the fly by entering at least one letter and hitting pageup / pagedown. Try it.

Also, the obligatory URL: [http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by Gurgeh on 2005-12-20
Most important thing I ever did when I started running ubuntu was: Brought a notepad and pen (only thing i've had to pay for so far as well lol)

---

### Post by cstudent on 2005-12-20
I email myself the link of forum threads I find useful. When I get home I open Firefox back up to them and bookmark them under Forum Keepers. This page just got sent.  I definately want to try 23meg's trick later on.

---

### Post by deNoobius on 2005-12-20
[QUOTE=cstudent] I definitely want to try 23meg's trick later on.[/QUOTE]

Me, too.  Nice.

---

### Post by 23meg on 2005-12-20
[QUOTE=cstudent]I email myself the link of forum threads I find useful. When I get home I open Firefox back up to them and bookmark them under Forum Keepers. This page just got sent.  I definately want to try 23meg's trick later on.[/QUOTE]
You can replace that with the forum subscriptions system. Create a folder called "reference" and subscribe to threads you find useful, putting the subscription under this folder, and choose email notifications if you wish to be alerted when there's a reply to the thread. I'm subscribed to hundreds of threads, and every once in a while I get a notification mail that reminds me of a useful trick that I had noted down back in Warty times.

---

### Post by Nameless on 2005-12-20
Thanks for the suggestions.  I never realized I could go back and search my terminal.  That's really handy.  

I had been emailing links to myself, but I thought that was a little out of control.  

23meg, I definitely need to give your suggestions a try.  Thanks so much. One question, though: what is my "~/.inputrc file"?

---

### Post by cstudent on 2005-12-20
Excellent! I didn't realize I could do that with subscriptions. Now I can have my Keepers available from anywhere. Thanks!

---

### Post by tlc on 2005-12-20
Heh. I have an ever-growing text file called upshitcreek.txt - just a bunch of cut'n'pasted how-to-do-stuff type stuff that I've pulled off forums like this over the years. My gentoo period saw it grow rather rapidly... :razz:

---

### Post by earobinson on 2005-12-20
[QUOTE=Nameless]I've been perusing the forums today and I want to try a lot of things when I get home, but I got to wondering:   What does everyone do to remember all of the commands to enter into the terminal?  

I'm a total noob to Linux so I know there is no way I'm going to be able to memorize them.  I  was thinking about using notepad (or the Linux compliment) but wanted to know how others do it.[/QUOTE]

**I dont**, some of them I know because I use them all the time but very few. Why would I learn them when I can just look them up.

Half of them I can figure out how they start so i type the start of the name then hit the tab key and it puts in the rest.

When Im looking for a command that I know is there but cant rember I use the apropos command (man apropos for more info) this lets me put down some keywords and the list all the commands that use those keywords in there man pages.

Also If im looking for a command and know a similar command to it I will sometimes man the first command then look at the see also.

Why would I learn all this when I can look it up very fast using the computer.

But the more you use the commands the more commands you know and the faster you become at looking up commands.


~/.inputrc is just the terminal history no?

---

### Post by 23meg on 2005-12-20
> **earobinson]~/.inputrc is just the terminal history no?[/QUOTE]No, that's ~/.bash_history . ~/.inputrc is a preference file for bash input said:**
> 
Heh. I have an ever-growing text file called upshitcreek.txt - just a bunch of cut'n'pasted how-to-do-stuff type stuff that I've pulled off forums like this over the years. My gentoo period saw it grow rather rapidly... Take a look at the Scrapbook Firefox extension, if you're using Firefox. It will change your life.
[QUOTE=Nameless]One question, though: what is my "~/.inputrc file"?[/QUOTE]~ is a shortcut prefix for your home folder. It indicates the home folder of the active user. If your user name is Nameless, ~ is a substitute for /home/Nameless. Thus, ~/.inputrc corresponds to /home/Nameless/.inputrc .

---

### Post by ecto on 2005-12-20
I keep a notebook of how i fixed certain problems (most of which were in terminal) and have gotten to the point i know how to use vi, bash scripts, as well as switching my terminal editor from emacs to vi. Try learning more about bash itself, thats the best way to remember/learn them. Once you get fairly proficient you dont really have to memorize commands but you can make bash scripts and make life easy on yourself

---

### Post by Rackerz on 2005-12-20
I just remember them, and if I i want to keep something I've seen on this forum I'll add a subscription.

---

### Post by towsonu2003 on 2005-12-20
I spoiled myself by buying a linux pocket guide. it's chic :P

I also have a folder 'guide' where I copy paste how to do stuff when I find it useful (coming accross in slashdot comments, forums, google searches, linux news sites etc.)

But I dont use 'history' because I keep forgetting it ;)

---

### Post by timczer on 2005-12-20
I have been using a personal wiki for a while.  As I work through projects (most recently setting up a server and wiki for work) I save the info I have used on a new wiki page.  I can bookmark web sites, if I have documents created I can link to those as well.  It has helped me get the various methods I was using in one place.  I am using Newton for this, although there are several personal type wiki's out there.  I have newton on the gnome panel and when I am working on bigger stuff, I keep it open, ready to recieve info.

---

### Post by benplaut on 2005-12-20
[QUOTE=timczer]I have been using a personal wiki for a while.  As I work through projects (most recently setting up a server and wiki for work) I save the info I have used on a new wiki page.  I can bookmark web sites, if I have documents created I can link to those as well.  It has helped me get the various methods I was using in one place.  I am using Newton for this, although there are several personal type wiki's out there.  I have newton on the gnome panel and when I am working on bigger stuff, I keep it open, ready to recieve info.[/QUOTE]

yeah, that's a really good idea to use newton (or tomboy - a bit easier to install)

make sure you print out whatever you do, however - if you're stuck in CLI, newton won't do you much good!

i took the hard route, and pretty much just memorized all the stuff :P

---

### Post by DoorGunner on 2005-12-21
once you get acroread installed you can use this site...

[http://homepage.powerup.com.au/~squadron/linuxmanual.pdf](http://homepage.powerup.com.au/~squadron/linuxmanual.pdf)

---

### Post by mdsmedia on 2005-12-21
acroread?

xpdf works just as well :) I guess....unless I missed something...which wouldn't be unusual

---

### Post by darth_vector on 2005-12-21
i dont know if anyone has mentioned this, but apropos is a very helpfull command. if you tell it what you want to do (eg. apropos remove) it will give you a list of commands that match the search parameter. you can then read through the man pages to find the program that does what you need.

---

### Post by Perfect Storm on 2005-12-21
Acroread is availble for linux.


On Topic: The more I use the commands the better I memorize them, sure there's commands I rarely use then I just look them up.

---

### Post by xmastree on 2005-12-21
The only command you really need to remember is this one:
[CENTER]**[SIZE="6"]apropos[/SIZE]**[/CENTER]

For example, you forgot how to copy a file...```
chris@ubuntu:~$ apropos copy
**[COLOR="Red"]cp (1)               - copy files and directories[/COLOR]**
cpfs.reiser4 (8)     - the program for copying reiser4 filesystem.
cpio (1)             - copy files to and from archives
dd (1)               - convert and copy a file
debconf-copydb (1)   - copy a debconf database
FcCharSetCopy (3)    - Copy a charset
FcMatrixCopy (3)     - Copy a matrix
FcStrCopy (3)        - duplicate a string
FcStrCopyFilename (3) - copy a string, expanding '~'
FcValueSave (3)      - Copy a value
install (1)          - copy files and set attributes
objcopy (1)          - copy and translate object files
pax (1)              - read and write file archives and copy directory hierarchies
rcp (1)              - secure copy (remote file copy program)
scp (1)              - secure copy (remote file copy program)
ssh-copy-id (1)      - install your identity.pub in a remote machine's authorized_keys
xcdroast (1)         - graphical frontend to create or copy CDs.
xdfcopy (1)          - Program to copy and format Xdf disks in Linux TQ
xdfformat (1)        - Program to copy and format Xdf disks in Linux TQ
xfs_copy (8)         - copy the contents of an XFS filesystem
xfs_rtcp (8)         - XFS realtime copy command
XColor (3x)          - create, copy, or destroy colormaps and color structure
XCopyArea (3x)       - copy areas
XCopyColormapAndFree (3x) - create, copy, or destroy colormaps and color structure
XCopyGC (3x)         - create or free graphics contexts and graphics context structure
XCopyPlane (3x)      - copy areas
XCreateColormap (3x) - create, copy, or destroy colormaps and color structure
XFreeColormap (3x)   - create, copy, or destroy colormaps and color structure

```
It's up there at the top, along with a whole load more stuff you didn't know you didn't know...

You don't even need to know how to spell it, apr<tab> is enough. :cool:

---

### Post by earobinson on 2005-12-21
[QUOTE=xmastree]The only command you really need to remember is this one:
[CENTER]**[SIZE="6"]apropos[/SIZE]**[/CENTER]

For example, you forgot how to copy a file...```
chris@ubuntu:~$ apropos copy
**[COLOR="Red"]cp (1)               - copy files and directories[/COLOR]**
cpfs.reiser4 (8)     - the program for copying reiser4 filesystem.
cpio (1)             - copy files to and from archives
dd (1)               - convert and copy a file
debconf-copydb (1)   - copy a debconf database
FcCharSetCopy (3)    - Copy a charset
FcMatrixCopy (3)     - Copy a matrix
FcStrCopy (3)        - duplicate a string
FcStrCopyFilename (3) - copy a string, expanding '~'
FcValueSave (3)      - Copy a value
install (1)          - copy files and set attributes
objcopy (1)          - copy and translate object files
pax (1)              - read and write file archives and copy directory hierarchies
rcp (1)              - secure copy (remote file copy program)
scp (1)              - secure copy (remote file copy program)
ssh-copy-id (1)      - install your identity.pub in a remote machine's authorized_keys
xcdroast (1)         - graphical frontend to create or copy CDs.
xdfcopy (1)          - Program to copy and format Xdf disks in Linux TQ
xdfformat (1)        - Program to copy and format Xdf disks in Linux TQ
xfs_copy (8)         - copy the contents of an XFS filesystem
xfs_rtcp (8)         - XFS realtime copy command
XColor (3x)          - create, copy, or destroy colormaps and color structure
XCopyArea (3x)       - copy areas
XCopyColormapAndFree (3x) - create, copy, or destroy colormaps and color structure
XCopyGC (3x)         - create or free graphics contexts and graphics context structure
XCopyPlane (3x)      - copy areas
XCreateColormap (3x) - create, copy, or destroy colormaps and color structure
XFreeColormap (3x)   - create, copy, or destroy colormaps and color structure

```
It's up there at the top, along with a whole load more stuff you didn't know you didn't know...

You don't even need to know how to spell it, apr<tab> is enough. :cool:[/QUOTE]


man is also very usefull, if your looking for a command like copy for example move, you can do a man copy and go to the see also and there you find  mv for move

---

### Post by 23meg on 2005-12-21
I often use grep to search manpages for specific operations. For example, type ```
man cp |grep remove
``` and see what you get.

---

### Post by earobinson on 2005-12-21
neat!

---

### Post by Danielle on 2005-12-21
i use Tomboy, it's in Synaptic. i put it in "Startup Programs" - System>Preferences>Sessions>Startup Programs. i can click it and open a note called commands.

if you want to find a note you can't remember the name of you can click on Search Notes and type in a word, it will show any note with that word in :D

---

### Post by Danielle on 2005-12-21
i don't understand the tab key completion. can you show me a half complete command which will do something when you press the tab key? i tried putting in a half complete command i was just shown then pressing tab and nothing happened:
ps -

---

### Post by LoclynGrey on 2005-12-21
I post them as I fnd them, in my wordpress blog, which has a built in index system and search feature.
It good for when I do something stupid like knocking my self out of the xmanager and all im left with is the terminal to use. I can jump on another PC, check my blog for some forgottem commands and slowly get my self out of the sh**. The same applies with rocking on up to the Ubuntu forums and doing a search.

---

### Post by 23meg on 2005-12-21
[QUOTE=Danielle]i don't understand the tab key completion. can you show me a half complete command which will do something when you press the tab key? i tried putting in a half complete command i was just shown then pressing tab and nothing happened:
ps -[/QUOTE]If there's only one command that matches, one tab stroke will do it. If there are multiple ones, you'll have to hit tab twice to see a list of possible commands you can enter.

---

### Post by Danielle on 2005-12-21
[QUOTE=23meg]If there's only one command that matches, one tab stroke will do it. If there are multiple ones, you'll have to hit tab twice to see a list of possible commands you can enter.[/QUOTE]
thanks, 23meg

---

### Post by DirtDawg on 2005-12-21
I found a copy of O'Rielly's *Linux in a Nutshell* for three bucks at a second-hand store (the source of the majority of my technical books, despite living in the same city as legendary Powell's Books).

---

### Post by Hygelac on 2005-12-21
I've been writing them down with pen and paper, and I keep the papers in a drawer in my desk.  As others have already said; you will eventually remember the commands that you use most, depending on how much you use them.  I don't keep them solely on the computer 'just-in-case'...
Have fun with Ubuntu!

---

### Post by 23meg on 2005-12-22
Setting up aliases for frequently used commands also helps.

[http://www.linuxcommand.org/wss0020.php#aliases](http://www.linuxcommand.org/wss0020.php#aliases)

---

### Post by LoclynGrey on 2005-12-22
"apropos" is now my new friend, along with google and the search feature on this Ubuntu forum. lol

---

### Post by xmastree on 2005-12-22
[QUOTE=23meg]Setting up aliases for frequently used commands also helps.[/QUOTE]Yeah, but you still have to remember your aliases though... :p 
That's fine if you have a head full of DOS commands.

---

### Post by 23meg on 2005-12-22
[QUOTE=xmastree]Yeah, but you still have to remember your aliases though... :p 
That's fine if you have a head full of DOS commands.[/QUOTE]
I don't remember much back from the DOS days but I do remember all my aliases; it's far easier to remember something you've explicitly made up yourself than something that's been made for you. Plus you can make commands much shorter and that helps. Here are some I use:

```
alias p0='sudo killall powernowd'
alias p1='sudo powernowd'
alias xed='sudo gedit /etc/X11/xorg.conf'
alias xedn='sudo nano /etc/X11/xorg.conf'
alias restart='sudo shutdown -r now'
alias fstab='sudo nano /etc/fstab'
```
and...
```
alias glxgears='glxgears -iacknowledgethatthistoolisnotabenchmark' 
```:cool:

---

### Post by fog on 2005-12-22
[QUOTE=23meg]Here's another VERY practical trick that I can't live without.. enter the following in your ~/.inputrc file:
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```and you can search in your bash history on the fly by entering at least one letter and hitting pageup / pagedown. Try it.[/QUOTE]
Amazing, you save me, thanx   :)

---

