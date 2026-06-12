---
title: "Resolution problem"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Clavera on 2007-11-10
Hi.

I have a problem with my resoultion or the "HZ" on the monitor.
The thing is that when I try to log in on my default user, everything goes black and theres a text telling me that the HZ is to big (80 instead of 74).
So I cant see anything because everything is black, all I can do is to CTRL+ALT+Backspace to go back to the log in screen.

I dont remember if i have a Root user or some admin user, so Im currently using the Live CD as I dont want to install everything again.

Earlier i had the resolution of 1280x1024, before this HZ problem came to be the resolution changed itself to 1100x"something else" and i couldnt switch back to 1280, as I tried that many times.


I tried to press CTRL+ALT+F2 in the logging screen and came to some dos-based screen where i was told to type:

"sudo dpkg-reconfigure -phigh xserver-xorg"

This would bring up some text based thing that would help me change the resolution or change the graphic cards something I was told. But the only thing that happened was this:

"xserver-xorg postint warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20071108155712".

Oh yes, my Graphic card is a ATI Radeon 9600 if thats any help.

Anyone know what to do?

---

### Post by schauerlich on 2007-11-10
After putting in "sudo dpkg-reconfigure -phigh xserver-xorg" you should be given a choice of drivers. Select the one appropriate for your graphics card, and hit ok. It's supposed to overwrite your xorg.conf.

---

### Post by Clavera on 2007-11-10
Problem is, Im not given this choice to choose anything, as I said, all I got was that message.

---

### Post by anewguy on 2007-11-10
If you don't already know, Ubuntu uses a window manager named X.  In order for you to log on to a window session, X must be running and be set up correctly for your hardware.  These settings are kept in a file called "xorg.conf"  in the folder "/etc/X11".  When X finds something it can't support then usually you'll get a failure like you are experiencing.  There are a LOT of pieces available for the xorg.conf file.  For a full list and what they do, please see this page:

[http://www.linuxmanpages.com/man5/xorg.conf.5x.php]("http://www.linuxmanpages.com/man5/xorg.conf.5x.php")

What you are interested in is the monitor section, and in particular the HorizSync definition.  You first need to know the rates your monitor supports (it should be in the little documentation that came with your monitor - if not, try searching for your monitor online to find the specs.  There is also VertRefresh you can add to specify the vertical rates.

The first thing you should do is go ahead and log on to the terminal window - that's what you are working with when you do the crtl-alt-F2 and log in.  The very first thing I would do is see if you even have an xorg.conf file (you should).  To check this, type in the following in your terminal window:

cd /etc          <enter>  this will change your default folder (directory) to /etc

cd X11          <enter>  this will change your default folder to the X11 folder within the /etc/ folder

ls -al xorg.conf  <enter>  this will list the xorg.conf file's directory listing - this way you'll know it exists 

Now you will need to edit it in order to put in or change the HorizSync line to what you need.  Something to keep in mind is the system "owns" the /etc/X11 folder, so you can't just edit - you must specify that you want to edit the file as 
super user".  To do so:

sudo vim xorg.conf

This will bring up the file in an editor, but the editor is perhaps a little crude to work with compared to other "what you see is what you get" editors.  First use the page down or arrow key until you see a statement that says  "Section Monitor", then scroll a little more until you see "End Section".  Between those 2 statements is where you will find you horizontal and vertical rates, if they are not defaulting.  Modify them as you need, keeping in mind you must press the "insert" key once to begin inserting, and then press the "Esc" key to exit insert mode.  When you are done with your changes, press the ":" key - a command line will show at the bottom, starting with ":".  type "write" and press the "Enter" key.  Press ":" again, and this time type in "quit" and press the "Enter" key.

You have now changed you X configuration file.  The easiest way at this point to see if the changes worked are to just restart your system - type in the following:

sudo shutdown -r now   and press <Enter>  

The system will shutdown and reboot.  Let us know how it turns out.:)

You should also search this forum for ATI driver information.  I seem to remember they can be a little difficult to set up, but I have seen lots of replies here to help people do just that.  It may be that by just changing your driver things will straighten out.

---

### Post by KentS on 2007-11-10
Have you checked your /etc/X11/xorg.conf? Which driver is being used? What are the different screen resolutions listed?
Do you have earlier and functioning backups of xorg.conf? Have you tried ```
cp /etc/X11/xorg.conf*working backup* /etc/X11/xorg.conf
```? (You may want to make a backup first.)
Or have you tried to just edit your xorg.conf and set the right resolution?

Your screen's resolution should be 1280x1024? xorg.conf used this resolution originally? Then, without you doing anything (e.g. installing new driver, editing xorg.conf, choosing a different resolution using your GUI), it changed to 1100x"something else"? What is "something else"?

---

### Post by Clavera on 2007-11-10
Thanks very much, I'm finally able to log in again! :)

As I'm kinda newbie on Ubuntu I couldn't at first go into the /etc folder as I forgot the / before etc.
But I managed to change the HZ, but now its really poor resolution and so, but I think I can handle the rest now.

By the way, I had to make a new insert with "HorizSync 70" in the monitor section.

Thanks again! Great guide! :)

---

