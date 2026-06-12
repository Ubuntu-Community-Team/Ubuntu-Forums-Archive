---
title: "Firefox closes when opening Yahoo or MySpace how Can I fix this?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by szaemon on 2007-06-25
Firefox closes when opening Yahoo or MySpace how Can I fix this? I tried searching for this question but I get a message that says the term is under the minimum word length and won:t be found. I don:t understand this, the question has 14 words. Please help.

---

### Post by tgoose on 2007-06-25
If you run firefox from the terminal
i.e., simply type
```
firefox
```
then the terminal will display any error messages. Copying and pasting them here will help to find the problem.

---

### Post by szaemon on 2007-06-25
Thank You tgoose for offering your assistance. This is the terminal's messege when opening MySpace:

me@HOME:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
me@HOME:~$ 

I wish I could say that I understood what this means, but....

---

### Post by szaemon on 2007-06-25
Yahoo! gives the same message. At least it:s consistent...

---

### Post by Clay_Banger on 2007-06-25
are you using the latest version of firefox?

---

### Post by szaemon on 2007-06-26
I'm using version 2.0.0.4 when I check for updates it says there are none, so I believe this is the latest version of Firefox.

---

### Post by DBStevens on 2007-06-26
Are you running any third party extensions?

What is an exact page on Yahoo that does this.

I run Firefox and have been known to spend more than a couple of minutes on Yahoo.

---

### Post by szaemon on 2007-06-26
I don't know what a third party extension is, I can you tell I'm not intentionally running any. As for an exact page. Yahoo.com the main page.Also myspace .com geocities .com and quite a few others. I have a feeling my problem is something very basic, but I haven't a clue what it could be. Perhaps a common plug in is missing. How would I check what plugins  are installed or what ones I might need?

---

### Post by phr0ze on 2007-06-26
Check your flash or reinstall flash. Flash often causes firefox problems.

---

### Post by cowkiller on 2007-06-26
a 3rd party extension is any addon, skin or plugin wich are not officialy supported by firefox. I had the same problem that you after installing some plugins and skins in my firefox. The only way to fix it would be uninstalling firefox and installing it again, taking care about anything you add on it...
If the problem persist,try using Opera.
Good luck!

---

### Post by DBStevens on 2007-06-26
Well the yahoo.com home page has flash on it.

Did you install a flash player?  If so do you have a 64 bit system installed?

There are issues with flash on a 64 bit system.  Search this forum for flash firefox 64  you may find an answer if that is the case.

---

### Post by szaemon on 2007-06-26
Thanks for the advice.
How do I discover what plugins are installed?
I tried uninstalling firefox through add/remove programs but was told I need to use the synaptic package manager...hmmm, sounds like something I shouldn't be messing with...
I went to the add-ons page in firefox and downloaded the Adobe Flash plug-in, in the installation instructions I'm told to open the terminal and navigate to the desktop. Opening the terminal is no problem, but I don:t know how to navigate to the desktop. I tried typing desktop  but that was an invalid command. I tried the Help file in the terminal, but that only contains information on how to adjust the terminal. Where can I learn how to use the terminal? As for the 64 Bit System...I've never heard of it. How would I check?
Sorry for such basic questions....

---

### Post by Clay_Banger on 2007-06-26
> **szaemon said:**
> Thanks for the advice.
How do I discover what plugins are installed? [COLOR="SeaGreen"]within Firefox, Tools > Add-Ons will display any third party add-ons. however there is one or two in that list that are offical add-ons.[/COLOR]
I tried uninstalling firefox through add/remove programs but was told I need to use the synaptic package manager...hmmm, sounds like something I shouldn't be messing with... [COLOR="SeaGreen"]Can't remember how to get to the package manager in gnome, but if you wish to uninstall firefox, open the terminal and type(without the quotes): "sudo aptitude remove firefox" then to install it again type: "sudo aptitude install firefox"[/COLOR]
I went to the add-ons page in firefox and downloaded the Adobe Flash plug-in, in the installation instructions I'm told to open the terminal and navigate to the desktop. Opening the terminal is no problem, but I don:t know how to navigate to the desktop. I tried typing desktop  but that was an invalid command. I tried the Help file in the terminal, but that only contains information on how to adjust the terminal. Where can I learn how to use the terminal? [COLOR="SeaGreen"]To navigate to the desktop within the terminal you use the "cd" command. cd = change directory. so as the desktop it located in you home folder you would type "cd ~/Desktop" and that would move you to the desktop. "cd" tells it to change the dir, "~/" tells it to go to the current users home folder and "Desktop" tells it to then go to the Desktop folder.[/COLOR]
As for the 64 Bit System...I've never heard of it. How would I check?[COLOR="SeaGreen"] It depends on the iso that you downloaded, if you downloaded the i386 one, you are not running 64 bit, if you downloaded amd64 or i684(or sumthing similar) you are running 64 bit.[/COLOR]
Sorry for such basic questions....

I hope all of you questions are answered above.

---

### Post by szaemon on 2007-06-26
Yes Clay, all my questions are answered, and quite thouroughly. thanks again. I just discovered that I have no add-ons aexcept for the default Themes and The Language Pack. So if that:s where my plug-ins would be then I have none. I'll put inthe flash player and see what that does.

---

### Post by szaemon on 2007-06-27
The Installation instructions for Adobe Flash Player require me to log in as root with mdg. Perhaps some of the terminology has changed but I think is system administrator but what does it mean to log in as with mdg? And how do you do it ?

---

### Post by Seisen on 2007-06-27
You can install flash by using apt-get unless you have a 64-bit computer than its a pain

```
sudo apt-get install flashplugin-nonfree
``` Also make sure that the universe repo's are uncommented so this will work.

---

### Post by Grigorius on 2007-06-27
> **szaemon said:**
> Thanks for the advice.
How do I discover what plugins are installed?
I tried uninstalling firefox through add/remove programs but was told I need to use the synaptic package manager...hmmm, sounds like something I shouldn't be messing with...


I had to uninstall and reinstall firefox, I did it with synaptic and had no problems (actually I solved my problems this way) I think you should try and do the same and choose the completely remove option (the second one) ... and the simply reinstall with synaptic or add/remove as you like ...

---

### Post by DBStevens on 2007-06-27
szaemon,

In a terminal please run

cat /proc/cpuinfo

Then post the results on the forum.

The synaptic package manager is desigined to properly handle installing software for the system, it is not something to be afraid of.

---

### Post by szaemon on 2007-06-27
Problem solve and I want to thank everyone who held my hand and walked me through it. It must be very cumbersome dealing with people who are both ignorant and  in fear of computers... I finally used synaptic to uninstall and reinstall firefox, of course it worked like a charm. And all my fears were abated. All my settings and bookmarks were preserved.
Thanks for the tutelage.

---

