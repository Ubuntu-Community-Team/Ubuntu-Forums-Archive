---
title: "I LOVE IT, but..."
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by theunlib on 2006-12-31
I'm having a bit of trouble.  I've looked through the documentation, but haven't been able to find solutions to my problems.

1. I downloaded the Second Life alpha client, and I can't seem to figure out how to install it.  Normally, with the Windows version, at least, it was simple.  With the Linux client, I get a folder, and have no idea what to do with it.

2.  Similar to number one.  I try to add my printer, but it's not on the list.  I have the installation CD, but when I put it into my CD-Rom drive, it reads it, gives me an icon on the desktop, but nothing seems to happen.  When I try the "setup" file, it gives me an error message, saying that ..well, that it's missing an auto-something...sorry for being vague, I'm on another computer right now, can't be on both...which is explained in #3

3.  When I open Firefox, things seem to be going okay, but then all of the sudden, Firefox closes itself out.  When I try to open it again, it gives me the option to restore my "unexpectedly closed session" or start a new one.  Regardless, at some random point, it will close out again.

I am SO trying to get into open source EVERYTHING.  This is my last great leap, and so far, I'm nothing but frustrated.  Any help would be GREATLY appreciated.  

Thanks!

---

### Post by 23meg on 2006-12-31
> 
3. When I open Firefox, things seem to be going okay, but then all of the sudden, Firefox closes itself out. When I try to open it again, it gives me the option to restore my "unexpectedly closed session" or start a new one. Regardless, at some random point, it will close out again.Do you have any plugins and extensions installed? Type "firefox" at a terminal and see if there are any error messages as it crashes.

---

### Post by Sef on 2006-12-31
> 1. I downloaded the Second Life alpha client....

Expect alpha software to crash.  It is for testing purposes mainly.

From [Second Life]("http://secondlife.com/community/linux-alpha.php")'s site:

> Please visit the Second Life Linux Alpha forum to get news, find out about known issues and share data with other alpha testers.

This is an early version of the Linux client, made for testing purposes only. Be aware that it is designed to work on the main grid. When you launch this viewer you will connect to Second Life as you normally would with the Windows or Mac client. Any changes you make while testing the Linux client are permanent and cannot be undone!

---

### Post by OMRebel on 2006-12-31
What printer are you trying to install?  If you're trying to use a Windows driver for the printer, that's not going to work.  Give us your model for your printer and we'll give ya the steps to get it going.

---

### Post by siucdude on 2006-12-31
> **theunlib said:**
> 
1. I downloaded the Second Life alpha client, and I can't seem to figure out how to install it.  Normally, with the Windows version, at least, it was simple.  With the Linux client, I get a folder, and have no idea what to do with it.

Ok you are going need to start from Linux for Starters.  Looks like from the questions and mainly number 1 you don't know that windows software will not work so any files that start with .exe will not work.  Plus different file formats.  Don't get mad but I was at the same point about 5 years ago.  Just read and ask questions.  But start off on what is Linux/Ubuntu, and Welcome to open source.  Have fun!!!!

TJ

---

### Post by ncappel1 on 2006-12-31
> **theunlib said:**
> 3.  When I open Firefox, things seem to be going okay, but then all of the sudden, Firefox closes itself out.

I had a similar problem, though I can't offer a concrete solution I suggest that you use another browser like "Epiphany" or "Opera" (both open source!) until you find out what's wrong. In my case I never got a chance to solve the issue, after I made an update the problem seemed to go away. Have you downloaded relevant/latest updates for firefox and ubuntu? 

also, try running firefox through the terminal, when it crashes post any output here, it may give a clue to what's happening.

---

### Post by slimdog360 on 2006-12-31
yeah, the type of printer would be handy. If its a canon or epson check my sig for the driver.

---

### Post by theunlib on 2006-12-31
Thanks, everyone.  I'll look into your suggestions.  I have used Second Life on machines running Linux and have had no problems at all...then again, I, personally, didn't have to install it!

My printer is a Lexmark 3100 Series.  Thanks!

I have not installed any plug-ins.  The error message I get in firefox is:
eve@eve-desktop:~$ firefox
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
eve@eve-desktop:~$ 
eve@eve-desktop:~$ 

Get mad?  How could I get mad???  :)  I am 100% clueless and am completely fine with admitting this little tidbit at this point.  I'm just glad I waited to install Linux until after I got my nice new safe little Windows running laptop.

My experience with Linux is sitting next to a coworker/IT god, watching him show me stuff.  I also had something on my desktop at work that let me run Linux compatible programs, but that's it.  

Thanks, everyone.  I really appreciate your help!

---

### Post by Sef on 2006-12-31
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-3000").

Your Lexmark look like it will work.  From a 3000 to 3100 is not a big jump, so hopefully it will; however, Lexmarks do not work well or easily with GNU/Linux.  The company prefers to keep the drivers propriatery, especially for home users.

---

### Post by theunlib on 2006-12-31
Unfortunately, I tried the 3000 driver initially, and I still couldn't get the printer to work.  Any other suggestions?  Thanks!

---

### Post by mahiyar on 2006-12-31
> 3. When I open Firefox, things seem to be going okay, but then all of the sudden, Firefox closes itself out. When I try to open it again, it gives me the option to restore my "unexpectedly closed session" or start a new one. Regardless, at some random point, it will close out again.I had faced same problem. This could be if you are viewing a page with flash player content in it and u have an old version of flash (try going to YouTube.com and see if u can play the clips). The solution for the same might be in this thread  [http://www.ubuntuforums.org/showthread.php?t=320227](http://www.ubuntuforums.org/showthread.php?t=320227) and do not despair with persistence u can make everything work.

---

### Post by szegey on 2007-01-02
> **theunlib said:**
> 
1. I downloaded the Second Life alpha client, and I can't seem to figure out how to install it.  Normally, with the Windows version, at least, it was simple.  With the Linux client, I get a folder, and have no idea what to do with it.


Open up a terminal and cd into the Second Life folder. There you type:

./secondlife

For more help visit: [Linux Client Alpha Testers Forum at secondlife.com](http://forums.secondlife.com/forumdisplay.php?f=263)

---

### Post by teejay17 on 2007-01-02
> **Sef said:**
> Expect alpha software to crash.  It is for testing purposes mainly.

From [Second Life]("http://secondlife.com/community/linux-alpha.php")'s site
This might also explain why Firefox is crashing; *Second Life *could have caused some serious messing around in your machine.

---

### Post by Quillz on 2007-01-02
> **OMRebel said:**
> What printer are you trying to install?  If you're trying to use a Windows driver for the printer, that's not going to work.  Give us your model for your printer and we'll give ya the steps to get it going.
Aren't most modern printers USB plug-and-play? Or are they only pre-formatted for Windows?

---

