---
title: "2 lame CLI questions"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by Bartender on 2006-01-16
I've been reading and re-reading ubuntuguide, Automatix, etc. and the same 2 lame-ass questions keep coming up.  Well, there's a lot more than two but you know what I mean

Lots of commands in these guides show several lines of text one right after the other.  How do you enter more than one line?  Hopefully I'll be able to copy and paste when it's time to try following the Automatix steps, but I'd still like to know.

I keep seeing directions for making changes to some text, then "saving" those changes.  How do you save changes?  If it's just "Enter" how do you know anything happened?  I've been poking at the CLI and sometimes it just goes back to the prompt and I don't know if anything even happened or not...

---

### Post by tim15856 on 2006-01-16
How about an example? AFAIK, when you see more than one line of commands, they are performed separately. Type out one, hit enter, then type the other. You should be doing this in a terminal window. To edit and save text, use gedit in superuser mode (sudo gedit 'filename'). Just save the file from the file/save menu.

---

### Post by Bartender on 2006-01-16
Here's an example from Automatix instructions...

[COLOR="Purple"]To install Automatix, do the following from terminal:
Code:

wget [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb) 
sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb[/COLOR]

Both of those command lines are in one box, and I don't understand if you're supposed to type one, Enter, then type the next one or type both of them into terminal before Enter

Here's an example of my second question...


[COLOR="Purple"]Q: How to allow more sudoers?

   1. Read General Notes
   2.

export EDITOR=gedit && sudo visudo

   3. Append the following line at the end of file

system_username	ALL=(ALL) ALL

   4. Save the edited file (sample)[/COLOR]


The format got goofed up copying and pasting.  The last line says "Save the edited file".  That instruction (Save the edited file) is all thru the ubuntuguide, and I'm just not clear on what that means nor how to do it.

---

### Post by Iowan on 2006-01-16
re: The first question... The lines are entered one at a time.  Per your example, type in (or paste) the wget line, [ENTER], after the process completes, type in the sudo line, {ENTER], etc.

re: 2nd question... Most text editors (I usually use vim or nano from command line) have a "save" or "write (to)" combination.  There is usually another key combination to exit the editor.

---

### Post by kakashi on 2006-01-16
one symbol  <\> 
try 
line 1 \
line 2 \
line 3 \

the command enterd after the final enter is 
command = line 1 line 2 line 3

---

### Post by Bartender on 2006-01-16
Hi, Iowan -
Thanks for clearing up #1 for me.  (BTW, my wife is from Goose Lake, IA).

I know nothing about alternative text editors.  I've read where some have their preferences, but there's nothing wrong with the default terminal in Ubuntu is there?  What's the save command for that?

---

### Post by Iowan on 2006-01-16
Problem with a dual-boot system... always booted on the wrong one.  I had to power down XP and restart on Ubuntu so I could check the default editor.

I looked up Goose Lake.  Heard of it, but more familiar w/ names Storm Lake and Clear Lake.  If your wife attended U of I, she was right across town.

**gedit** is the default Ubuntu *editor* (not to be confused with *terminal* )... although if you've opened a terminal window, typing **gedit** will open the editor.  As **tim15856** mentioned,  the file can be saved either by clicking on File->Save or by clicking the **Save** button.  As he mentioned, **sudo gedit 'filename'** might be safer, as some configuration-type files require superuser rights.

---

### Post by Bartender on 2006-01-16
Cripes -
I think that's exactly what I've been doing, is confusing the terminal with - with - whatever it is that you described.  I bought two O'Reilly books, Running Linux and Nutshell, hoping to crawl out of the hopeless newbie mind frame, but both books are just too damn esoteric.  Within a few pages they're both off to the deep end of the pool.  I need some sort of step-by-step book!

---

### Post by goatflyer on 2006-01-17
The best way to learn is to get your feet wet.  Don't worry, we'll stay in the shallow part.

Open terminal with Applications/Accessories/Terminal


Hit return a few times, you should see something like

myname@MYCOMPUTER:
myname@MYCOMPUTER:
myname@MYCOMPUTER:
myname@MYCOMPUTER:

That's the terminal prompt, where 'myname' and MYCOMPUTER will be called whatever your name and computer are called.

When reading someone else's post showing a list of commands, they will often abbreviate the prompt to a single character like this:

$


Here are some safe commands to try (press return at the end of each)
Ignore my comments.  Remember not to type the '$', thats just the prompt.

             change directory to root directory (top level folder)
$ cd /

           show what's there
$ ls

         hmm... show what's there with more info  (dash L)
$ ls -l

        go to where many shell commands live.
$ cd /bin

       show everything in that directory (folder).
$ ls

       find out more about the ls command
$ man ls

Note that the screen is filled with the contents of the ls manual page, explaining all of the other things you can put besides -l.  You can scroll up and down with the arrow keys to read.  When you want to quit out of 'man', press 'q'


Phew, enough reading for now?

$ exit

That closes the terminal window for now.

You can go back any time you like and type

$ man any-commandname-you-want-to-know-more-about

 to learn more about what the named command does.

Be careful in there, but don't be afraid to explore.

Have fun learning Linux.

---

### Post by christhemonkey on 2006-01-17
I use vi in terminal, sorta straight forward when you get your head round it, to save make sure your not in insert mode then just type ZZ and your sorted!

---

