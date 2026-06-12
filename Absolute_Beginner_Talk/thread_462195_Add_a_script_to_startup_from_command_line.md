---
title: "Add a script to startup from command line"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by h0ax on 2007-06-02
This should be quick and easy - I just can't seem to find it anywhere.
Everyone always says to go to System -> Administration, etc.
I'm running Fluxbox and I want to add one of my scripts to startup when the window manager loads, well actually 5 seconds afterward with a sleep 5 command.

However - where do I add this script via CLI instead of GUI?

Thanks in advance!:D

---

### Post by h0ax on 2007-06-02
Nevermind, I figured it out

> To you have a script of your own that you want to run at bootup, each time you boot up. This will tell you how to do that.  Write a script. put it in the /etc/init.d/ directory.
  Lets say you called it FOO. You then run
   % update-rc.d FOO defaults  
 You also have to make the file you created, FOO, executable, using
$chmod +x FOO
 You can check out 
 % man update-rc.d for more information. It is a Debian utility to install scripts. The option &#8220;defaults&#8221; puts a link to start FOO in run levels 2, 3, 4 and 5. (and puts a link to stop FOO into 0, 1 and 6.)
  Also, to know which runlevel you are in, use the runlevel command. 



---

### Post by h0ax on 2007-06-02
Actually here's a very nice visual tutorial for people who learn better that way:
[http://www.youtube.com/watch?v=d39izaupvEg](http://www.youtube.com/watch?v=d39izaupvEg)

---

