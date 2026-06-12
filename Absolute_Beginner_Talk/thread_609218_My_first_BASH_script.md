---
title: "My first BASH script"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2007-11-10
I have a line in my xorg.conf, under the *[Device]* section, that, when I'm operating normally with the display on the monitor, looks like this: ```
Option      "ForceMonitors" "crt2,notv"
```  But, when I want to switch the display I have to edit the xorg.conf, and restart X.  I change the line to look like this: ```
Option      "ForceMonitors" "crt2,tv"
```  Well, I've become a little frustrated with editing the xorg.conf all the time, so I decided to write a script that would do it for me.

First, I created two files (*xorg.conf.tv* and *xorg.conf.notv*), each with one or the other of those *[Device]* lines.  Next, I wrote this script: ```
P=`grep notv /etc/X11/xorg.conf`
if [ "$P" == '' ]
   then sudo cp /etc/X11/xorg.conf.notv /etc/X11/xorg.conf
   else sudo cp /etc/X11/xorg.conf.tv /etc/X11/xorg.conf
fi
```

I created a launcher on the taskbar and set it as type *Application in Terminal* with the command *tvout.sh* (I copied my script to */usr/bin/*).  The problem is, when I push the launcher button it only seems to be executing the *else* statement, and never the *then* statement.  This is confusing, and I would think it was a problem with my script, but it works great everytime I run it in terminal (by just typing the command *tvout.sh*, which is the same command that the launcher points to).

Anyone got any ideas?

Some other things I would love to share with you:

At first I tried to get the script to restart X for me as well with the command: ```
sudo /etc/init.d/gdm restart
```  But restarting this way doesn't work for me, even though  *CTRL+ALT+Backspace* works everytime.  When I use the *gdm restart* command the system hangs between stopping and restarting - you know that black screen that display thing like this?  ```
Running local scripts.... [OK]
```  That's where it gets stuck - it never gives me a prompt or resets into the gui's login screen. 

Also, and I pretty much assume that this is impossible with the BASH script, if I could get the restart thing to work, could I also have the script log me in automatically after the restart?

-Mike

---

### Post by geirha on 2007-11-10
In gutsy there's a newer xorg that should let you do this without restarting xorg. Have you tried this? 

System -> Administration -> Screens and Graphics

---

### Post by mikeserv on 2007-11-10
In *System > Adminstration > Screens and Graphics* I do show two screens.  One is my default, and it is set at 1680x1050.  The other is grayed out and is set to disabled.  If I try to set the second screen as default I get nothing on either screen and I have to restart X (again with *CTRL+ALT+Backspace*).  

So, back to square one.  Really, the script is the simplest and easiest solution, I just want to know why the launcher doesn't work the same way that the terminal command does.  And, if I can figure it out, I'd like to make it restart X for me.

-Mike

---

### Post by geirha on 2007-11-10
Well, try to put " &" behind the script. When you restart gdm from within xorg, then gdm will bring down xorg with it, which in turn will bring down all its running programs, including the script that tries to restart gdm ... if you bring it to the background by adding the " &" after it, it will not be killed along with xorg. 

It's a bad way to bring down your session though. I would rather have the script just toggle the xorg.conf and use zenity to display which xorg.conf is active, and then you should manually log out, and hit CTRL+ALT+BACKSPACE at the login-screen.

---

### Post by mikeserv on 2007-11-10
Wow, I gotta say, that's way over my head.  

First of all, what do you mean by "put " &" behind the script"?  What would the command look like?  And are you talking about doing that in order to have the script login for me or to fix the *gdm restart* issue I'm running into?

Second, what is zenity and how would I use it to toggle my xorg.conf?

Third, and most importantly, any idea why the launcher activation of the script behaves differently than when it's called on in the terminal?

-Mike

---

### Post by geirha on 2007-11-10
Well, you made a launcher which launches "tvout.sh" have it launch "tvout.sh &" instead, that way it will run in the background, and not be a child process of xorg. 

A little more explanation about that: When you run a program from Xorg, that program becomes a child process of Xorg, and if you kill Xorg, all it's children are killed with it. Since Xorg in turn is a child process of gdm, restarting gdm will kill xorg and in turn the script that tries to restart gdm. That might be why you get a blank screen. Putting a process to the background, makes it a stand alone process, with no parents except init (don't ever kill init ;) )

zenity is a nice way for bash-scripts to output and get input using GUI, try running ```
zenity --info --text="Just want to say hi"
``` in a terminal.```
zenity --help
``` will give some help on how to use it to do other things.

---

### Post by mikeserv on 2007-11-10
Ok, I fixed the problem with the launcher acting differently than the command line.  For the launcher I changed the command to *bash /usr/bin/tvout.sh* and now it will correctly change the xorg.conf file everytime.

I'm about to try the thing you are recommending.  One question, though, why is restarting X from within the script a bad idea?

-Mike

---

### Post by geirha on 2007-11-10
All running X applications gets killed when you do that, and they might not get the chance to save their settings properly.

---

### Post by mikeserv on 2007-11-10
Ok, it doesn't matter anyway, since the restart thing still doesn't work.  It's strange, I get the same result when I type *sudo /etc/init.d/gdm restart* at a terminal.  Shouldn't that command work?

-Mike

---

### Post by mikeserv on 2007-11-10
I changed my script to output a dialog.  It now looks like this: ```
TVOut_Var=`grep notv /etc/X11/xorg.conf`
if [ "$TVOut_Var" == '' ]
   then gksudo cp /etc/X11/xorg.conf.notv /etc/X11/xorg.conf
   zenity --info --title="TVOut Script" --text="The display will now switch to the monitor.  Save all of your work and press CTRL+ALT+Backspace to complete." 
   else gksudo cp /etc/X11/xorg.conf.tv /etc/X11/xorg.conf
   zenity --info --title="TVOut Script" --text="The display will now switch to the TV.  Save all of your work and press CTRL+ALT+Backspace to complete." 
fi
```

I do have a few more questions, though.  I've noticed that a lot of other scripts start with something that looks like this: ```
#!/bin/bash
```  What does this do?  Is my not including this line the reason that I had to add *bash* to the beginning of my launcher command to get it to work?

And, still, I can't seem to figure out why */etc/init.d/gdm restart* doesn't work.

-Mike

Edit:  Oh, and I know this might sound stupid, but is there a way to keep the terminal window from popping up everytime I run the script?

---

### Post by jw5801 on 2007-11-10
The #!/bin/bash is just good coding practice. So yes I would add it at the start but it won't really do anything. It just tells anyone who opens the file that it is a bash script. The reason you have to run "bash *scriptname*" is because either you don't have execute permissions for the file, or it's not in a place that is on the bash path. Whereabouts is the script stored?
As for restarting gdm, try ctrl+alt+F1, then log in, then run it. Restarting X from outside of X is probably going to be more successful. I'm not sure why a terminal window is launching every time you run your script, is the launcher you made telling it to "run in terminal"?

Also, the "then" in your if statement is redundant. This would work just as well:
```
if [*condition*];
    *execute commands*
else
    *execute other commands*
fi
```

---

### Post by geirha on 2007-11-10
Looks good, are you sure this is your first bash script? CTRL+ALT+Backspace while logged in, is just as bad as running gdm restart btw, you really should logout and only do CTRL+ALT+Backspace while you're at the gdm-greeter (where you log in). CTRL+ALT+Backspace should preferably only be used in "emergencies" when you're logged in. For instance if gnome stops responding.

> **mikeserv said:**
> I've noticed that a lot of other scripts start with something that looks like this: ```
#!/bin/bash
```  What does this do?

It tells the program that attemts to run it, that it should be run with the bash shell. If it was a python script, you would have #!/usr/bin/python instead (or else it would try to run the python code in bash, which surely will fail).


> **mikeserv said:**
> Is my not including this line the reason that I had to add *bash* to the beginning of my launcher command to get it to work?

No, bash is the default shell (read from /etc/passwd), so if no first-line #! is specified, the script will be run by bash. The reason it wouldn't start is that it isn't executable. Right-click the script, select Properties, and give it execute permission in the permissions-tab.


> **mikeserv said:**
> And, still, I can't seem to figure out why */etc/init.d/gdm restart* doesn't work. 

Not quite sure either, never tried it like that.


> **mikeserv said:**
> Edit:  Oh, and I know this might sound stupid, but is there a way to keep the terminal window from popping up everytime I run the script?
Create a new launcher, and choose "Application" instead of "Application in terminal"

---

### Post by mikeserv on 2007-11-10
The file is executable, and it is in /usr/bin/.  Just typing the filename (*tvout.sh*) worked fine at the command line, but until I prefaced the command with *bash* in the launcher, anytime it wsas run from the launcher it would only execute the *else* statement.  After adding *bash* the launcher worked fine.

Yes, I had it set as *Application in Terminal*, but, again, before adding *bash* that was the only way I could get the launcher to work at all - even just the else statement.  Now that I've added *bash* I find that I can set it as a regular *Application* and the terminal window doesn't pop up - just my *zenity* dialogs.

I also removed the *then*, thanks.

It's too bad about the *gdm restart*, obviously the switching levels doesn't make any sense for me.

Here's a question, though.  Is it possible to tell X to logout the current X user with a script command?

-Mike

---

### Post by mikeserv on 2007-11-10
Are you sure the *then* was redundant?  Without it the script doesn't do anything if the variable is empty.  With it, it works.

-Mike

---

### Post by mikeserv on 2007-11-11
After finding a thread about a logout command (*gnome-session-save --kill*) and reading the manual on *zenity* my script now looks like this: ```
TVOut_Var=`grep notv /etc/X11/xorg.conf`
if [ "$TVOut_Var" == '' ]
	then 
		TV_Path='/etc/X11/xorg.conf.notv'
		Monitor="computer monitor."
	else
		TV_Path='/etc/X11/xorg.conf.tv'
		Monitor="TV."
fi
zenity --question --title="TV/Monitor Display Swap" --text="The display will now switch to the $Monitor  Save all of your work and press OK to logout."
case $? in
	0)
		gksudo cp $TV_Path /etc/X11/xorg.conf
		gnome-session-save --kill --silent;;
	1)
		zenity --info --title="No Change" --text="The xorg.conf file was not changed.";;
	-1)
		zenity --warning --title="Unexpected Error" --text="An error has occurred.  Aborting.";;
esac
```

Because I run Compiz with an XGL layer and multiple daily users I've found it better to have *Always Restart XServer* set to *true* in some other script that I edited so long ago that I've now forgotten about.  I remember changing it to stop a system hang in between logouts.  Well, that setup has benefitted me here: as soon as I press "OK" the system will automatically logout the current user and, in doing so, restart X.  This means that it reloads the newly copied xorg.conf and the monitor is automatically switched to either the monitor or the TV.

This may seem a little overkill for such a simple task, but, more than anything, this has been a pretty gratifying learning experience.  And I feel more confident now in working on my next BASH script.

Thanks, gheira and jw5801!

Edit:  This also gives me the added benefit of a clean logout without the messy use of *CTRL+ALT+Backspace*.

-Mike

---

