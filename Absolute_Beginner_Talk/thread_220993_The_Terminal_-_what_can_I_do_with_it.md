---
title: "The Terminal - what can I do with it"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by linuxuser28 on 2006-07-22
What do you use the terminal for that you cant use the GUI for? Is there a need to learn how to use this or is it just for Linux geeks?

---

### Post by Omnios on 2006-07-22
The terminal is a very usefull and powerfull Linux tool. Check out the Know you terminal commands in my signature, think there are even a few threads to advanced scripting stuff there to

---

### Post by moma on 2006-07-22
I use terminal (gnome-terminal) because it's quicker to issue commans than use the GUI.

I like to do all package installations from commandline.
$ apt-cache search this-and-that
$ apt-cache show this-and-that
$ apt-get install package-name

and dpkg command is also available.

Learn bash-scripting (ABS-guide) ;-)
[http://howtos.linux.com/guides/abs-guide/]("http://howtos.linux.com/guides/abs-guide/")

// moma
   [http://www.futuredesktop.net/ubuntu6.06.html#guides]("http://www.futuredesktop.net/ubuntu6.06.html#guides")

---

### Post by dimeotane on 2006-07-22
Its normal for the average person to dislike entering terminal commands, because they're gibberish and scary.  Don't worry; day to day for basic computing needs you won't need to use the terminal, just problem solving during setup. But remember that with a copy and paste of a single text command in the terminal, you're often able to do a task that would normally (in the graphical Windows interface) take much longer to do finding menus and checkboxes, wading through confusing control panels. Eventually you might find yourself doing a whole backup of your harddrive with a copy and paste of one command! 


Here's a case in point.  Notice how the command terminal is simple and easy to do?

You're installing Ubuntu, but your wireless adaptor driver is only available for windows.  So you need to install a program called ndiswrapper. 


Put in your Ubuntu CD. In the terminal enter:
$ sudo apt-get install ndiswrapper-utils

Or you could also use your mouse and the GUI to wade through windows. Go to System--->Administration-->Synaptic package manager, type in your admin password.
Settings-->Repositories click on Add CDrom. Click search and look for ndiswrapper.   right click on ndiswrapper-utils and mark for installation. Click apply. Still think the terminal is too complicated?

---

### Post by taurus on 2006-07-22
When I sit in front of a computer, the first thing I fire up is a terminal because I do everything from a terminal...  Fast and simple.

---

### Post by aysiu on 2006-07-22
Contrary to what many people contend, the terminal is not primitive but more advanced cognitively.

Babies and toddlers point and cry when they want something. Adults speak language with syntax, memorized vocabulary, and sentences.

Cavepeople draw on walls to express themselves. Advanced artists are able to write out their thoughts, even if they use a visual medium for art (the thinking behind a painting, the script for a movie).

A beginning "musician" hums what she hears and has no understanding of chords, octaves, modulation, notes, or any music theory. An advanced musician can sight-read sheet music and even *write* sheet music.

All of these more advanced forms require you to learn a vocabulary and syntax--to memorize stuff. So does the terminal.

If you want to be a digital toddler or a cavewoman, point and click for everything. If you want to be faster and more sophisticated, type--learn a language, a syntax.

**Download a webpage**:
1. Open the terminal. ```
wget -r -c http://www.somesite.com
```

or

2. Click the Firefox icon. Click on the location bar. Type in the address. Start clicking all the links and "saving as." Realize this takes too long. Click on Tools > Extensions > Get more extensions. Search for DownThemAll. Install DownThemAll. Close Firefox. Open Firefox again. Go to the location bar. Type in the web address. DownThemAll.

**Install Adobe Reader, Banshee, Thunderbird, Kolourpaint, Gtkorphan, Audacity, and Epiphany.**
1. Open terminal. ```
sudo aptitude update && sudo aptitude install acroread banshee mozilla-thunderbird kolourpaint gtkorphan audacity epiphany
```

2. Go to System > Administration > Synaptic Package Manager. Click Reload. Click Search. Search for Acrobat Reader. Right-click it. Mark it for installation. Search for all the other packages and mark them for installation. Click Apply.

Are you starting to get the picture? Now, just as musicians don't *always* use sheet music, writers *sometimes* draw pictures, and adults even use gestures to communicate, even most die-hard terminal users will point-and-click.

It all depends on the task, but for many tasks, it's faster to use the terminal, and I think it's worth learning that vocabulary and syntax for bulk tasks and for tasks you do often.

---

### Post by dbw on 2006-08-06
I would say that in general, I use GUI for things that I do rarely, and the terminal for anything thatI intend to repeat.  If I (theoretically) just purchased a dvd burner, and wanted to (theoretically) copy all of my brother's dvds, it's nice to be able to type:
```
vobcopy -m
growisofs -Z /dev/hda -dvd-video -V  MOVIE_TITLE/
```
were I only have to replace one word each time.

plus, TAB auto-completion rocks my face off.

---

