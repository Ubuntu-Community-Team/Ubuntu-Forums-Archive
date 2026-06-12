---
title: "Boot up problem?"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by jeffinhedon on 2006-02-05
I booted up and as the sequence progressed it said
Check Forced
Then it scrolled for ages
Eventually I got the system prompt
but How to get any further
I typed in my machine name and then the password
But how do I get to the "windows" the x server is it???
Whats gone wrong ????
Help anyone please
:(

---

### Post by Pragmatist on 2006-02-05
So you are able to login and you are just on a black screen with white type?

Try ```
sudo startx
```  when prompted give your password

Let us know what happens

---

### Post by bartbes on 2006-02-05
Well try ```
X
``` if it doesn't work try it with sudo in front. Or you can do ```
X :0 & DISPLAY=:0 gdm
``` and if it doesn't work sudo if it says that X is already started just use ```
sudo gdm
```the checking of your drive happens every 30 mounts (it says) and normally it would return to normal, if none of these things work reboot...

---

### Post by jeffinhedon on 2006-02-06
OK Folks
Done all that !!!
Still no joy
gets towards the end of bootup in recovery mode
and then hangs
Will not accept any command except "exit"
Exit to log on screen in terminal mode ..ie just a command line!!
So typed in machine name and password to get command line prompt
Typed in sudo startx
Command not known
typed  X :0 & DISPLAY=:0 gdm
Command not known
also gdm 
command not known
So if I can get to the command line that asks for the machine name and password...there must be a command that activates the "window" or x or gdm or whatever to get it working again
Help!!!!please

---

### Post by Pragmatist on 2006-02-06
So your able to get > just a command line!!  that is a really good thing!  Here are a few things I need to help you:

1.) give the results of the following commands:
a.) /bin/pwd
b.) /usr/bin/whoami
c.) /bin/ls
d.) /bin/echo $PATH

---

