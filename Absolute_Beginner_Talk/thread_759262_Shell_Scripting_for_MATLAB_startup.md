---
title: "Shell Scripting for MATLAB startup"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by pipa on 2008-04-18
I am relatively new to both Linux and shell scripting.
I wrote a very simple script to start MATLAB lincense manager, which is located in /usr/local/matlab75/etc directory. Following is my script:

#
# To Start Matlab
#

cd /usr/local/matlab75/etc
./lmstart 
matlab & 
#
#End
#

I have put the '&' after matlab command as it would open the application matlab and return me the prompt or terminal
However, it doesn't happen, matlab just start within the terminal....and shows its own (matlab's) prompt. I have to hit CRTL-c to get back the prompt of the terminal. Does anybody know the solution to my problem?

Thanks.

---

### Post by joshrobinson on 2008-04-18
background processing doesnt work with all programs

are you launching this script to use a program? 
couldnt you launch it with alt+f2 or a launcher?

that way you wont have to worry about leaving a terminal open

---

### Post by pipa on 2008-04-21
> **joshrobinson said:**
> background processing doesnt work with all programs

are you launching this script to use a program? 
couldnt you launch it with alt+f2 or a launcher?

that way you wont have to worry about leaving a terminal open

The program, I am launching,  is MATLAB. Before launching MATLAB, I have to start license manager from MATLAB's root directory. After launching the license manager, I can start matlab by just typing MATLAB in the terminal.
I am trying to combine both steps (starting license manager and program) in my script.

---

### Post by mkrahmeh on 2008-04-21
invoking a program (like matlab) from the konsole (or something alike) causes the program to become a child process of the bash, you can either work out the matlab using wine, or start the license manager and matlab from two different bash terminals..

---

### Post by casperlingus on 2008-04-21
Instead of changing directories in the script, try running lmstart directly.  And use the -desktop flag

```

/usr/local/matlab75/etc/lmstart
matlab -desktop

```

---

### Post by pipa on 2008-04-21
> **casperlingus said:**
> Instead of changing directories in the script, try running lmstart directly.  And use the -desktop flag

```

/usr/local/matlab75/etc/lmstart
matlab -desktop

```

Wow!!
That worked. I used 
```

/usr/local/matlab75/etc/lmstart
matlab -desktop &

```

Thanks a lot!!

---

### Post by casperlingus on 2008-04-22
Glad I could help.

I would recommend taking things one step further and adding that script to your top panel.  

Right click the panel, choose "Add to panel..." then click the "Custom Application Launcher".  Name it whatever you want.  For the command, type in or browse to the script you just wrote.  Then click on the icon on the left side and select the MATLAB icon to represent it.  As far as I know the MATLAB icon is not installed by default, but you can download it here:

[http://www.scl.utah.edu/computers/mac/help/x11/images/matlab.png](http://www.scl.utah.edu/computers/mac/help/x11/images/matlab.png)

Put it anywhere, just remember where you put it so you can find it when you browse for it in this dialog.  Standard location is /usr/share/pixmaps.  You'll find a lot of other icons there (to be used for other programs, if you feel inclined).

Enjoy!
-Casper

---

