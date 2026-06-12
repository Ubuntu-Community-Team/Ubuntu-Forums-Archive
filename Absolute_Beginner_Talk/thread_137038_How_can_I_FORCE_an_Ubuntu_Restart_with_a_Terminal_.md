---
title: "How can I FORCE an Ubuntu Restart with a Terminal Command"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-27
Hello all !!!

I am trying to make a script which automates the "Customization" Process of my Ubuntu.

I am amazed with what somebody can do with Ubuntu's "Scripting" !!!

When I had to setup a Windows OS, It would take me 5 hours (format, install Windows, customization, install of other programs, etc. etc.)

In Ubuntu I could have ALL within 30 minutes MAX (and I really mean this !!!)

ALL thanks to scripting...

So, I have a question:

What should I type to the "Terminal" to FORCE Ubuntu to restart the PC?

Thanks.

---

### Post by kabus on 2006-02-27
```
sudo shutdown -r now
```

or

```
sudo init 6
```

---

### Post by dvarsam on 2006-02-27
Yes, but after the shutdown, I want it to "automatically" restart.

Not just shutdown...

Is it the "sudo init 6"?

---

### Post by Klaidas on 2006-02-27
So doesn't shutdown -r now do it? :)

---

### Post by dvarsam on 2006-02-27
I checked it & it works !!!

But then I thought it might NOT be the greatest idea, cause if I am working during that time, it might NOT save changes to the documents & loose unsaved data.

Could I just "launch":

1. A window saying "Please Restart your Computer NOW" with an "OK" button?

OR:

2. The familiar window ("from Menu: System\Logout") with "Restart" option 
    checked?

Thanks.

---

### Post by LordBug on 2006-02-27
[Shutdown manpage](http://www.die.net/doc/linux/man/man8/shutdown.8.html)

Good info on using it.  The best suggestion I can give you is to use the -t option to delay the reboot a few minutes, to give you time to close everything out.

---

### Post by wrtrdood on 2006-02-27
There's also the shorthand version:

sudo reboot


Oh.  And for complete shutdown it's:

sudo halt

---

### Post by dvarsam on 2006-02-27
I went to the "manpage" you suggested, but I can not put it to work:

root@house:/# shutdown -r -t 00:01 "Computer is going to Shut Down"
Usage:    shutdown [-akrhHPfnc] [-t secs] time [warning message]
                  -a:      use /etc/shutdown.allow
                  -k:      don't really shutdown, only warn.
                  -r:      reboot after shutdown.
                  -h:      halt after shutdown.
                  -P:      halt action is to turn off power.
                  -H:      halt action is to just halt.
                  -f:      do a 'fast' reboot (skip fsck).
                  -F:      Force fsck on reboot.
                  -n:      do not go through "init" but go down real fast.
                  -c:      cancel a running shutdown.
                  -t secs: delay between warning and kill signal.
                  ** the "time" argument is mandatory! (try "now") **
root@house:/#

I am typing:

shutdown -r -t 00:01 "Computer is going to Shut Down"

"-r" = after you shutdown, Restart
"-t" = I want to set the time when to shutdown
"00:01" or "+1" = The shutdown time is set to: 1 minute
"Computer is going to Shut Down" = The warning message to show up on my 
                                                           screen.

What is wrong with my command & it does NOT accept it?

Thanks.

---

### Post by LordBug on 2006-02-27
-t is a timer, not the time.  -t 60 would start a 60 second (1 minute) countdown.

```
shutdown -r 00:01 "Computer is going to Shut Down"
```would tell it to reboot at 12:01AM.
```
shutdown -t 60 -r  "Computer is going to Shut Down"
```would reboot 60 seconds after the command is sent.  Notice the -t is before the -r

---

### Post by piedamaro on 2006-02-27
For the familiar "do you want to shutdown?" dialog you may want to chek out zenity.

---

### Post by dvarsam on 2006-02-27
root@house:/#         shutdown -t 60 -r "Computer will shutdown"

Usage:    shutdown [-akrhHPfnc] [-t secs] time [warning message]
                  -a:      use /etc/shutdown.allow
                  -k:      don't really shutdown, only warn.
                  -r:      reboot after shutdown.
                  -h:      halt after shutdown.
                  -P:      halt action is to turn off power.
                  -H:      halt action is to just halt.
                  -f:      do a 'fast' reboot (skip fsck).
                  -F:      Force fsck on reboot.
                  -n:      do not go through "init" but go down real fast.
                  -c:      cancel a running shutdown.
                  -t secs: delay between warning and kill signal.
                  ** the "time" argument is mandatory! (try "now") **

It still does NOT work...

I tried to remove the quotes <"> but still NOT work...

Did you try typing this in your Ubuntu & it worked?

Thanks.

---

### Post by LordBug on 2006-02-27
the command is contradicting the manpage, not much of a surpise there.

Flip the -r and -t 60.

And no, I've not tested this yet.  I'm at work, stuck in Windows hell.

---

### Post by dvarsam on 2006-02-27
Can somebody give me a few examples of this, cause I flipped them & still got Nothing...

Just some examples to get me going...

Thanks.

---

### Post by stalefries on 2006-02-27
You need to begin it with a sudo. A normal user cannot shut down with that command, for some reason.

---

### Post by dvarsam on 2006-02-28
OK, I tried this, the way you said it...

root@house:/# sudo shutdown -r -t 60

Usage:    shutdown [-akrhHPfnc] [-t secs] time [warning message]
                  -a:      use /etc/shutdown.allow
                  -k:      don't really shutdown, only warn.
                  -r:      reboot after shutdown.
                  -h:      halt after shutdown.
                  -P:      halt action is to turn off power.
                  -H:      halt action is to just halt.
                  -f:      do a 'fast' reboot (skip fsck).
                  -F:      Force fsck on reboot.
                  -n:      do not go through "init" but go down real fast.
                  -c:      cancel a running shutdown.
                  -t secs: delay between warning and kill signal.
                  ** the "time" argument is mandatory! (try "now") **

Can YOU please give some examples, examples that YOU have tried & they really work?

Cause ANY combination I try, it still does NOT work...

Is there a package I am missing to make this work?

Thanks.

---

### Post by engla on 2006-02-28
It says " ** the "time" argument is mandatory! (try "now") **" in that help text. Try it  (append 'now' to your command)

---

### Post by noigeaR on 2006-02-28
```
sudo shutdown -r now
``` works for me

---

### Post by dvarsam on 2006-02-28
I have that & it works for me, too !!!

Can you give me an example with another "time" option instead of "now"?

... and hopefully with a warning message, like "Shutting Down"?

---

### Post by piedamaro on 2006-02-28
You can always do:
sleep 10m; reboot

or better:
sleep 10m && reboot

so if you cancel it with ctrl+c it won't reboot.

(you need root privileges, do a sudo -s before the above).
Hope this helps.

---

### Post by Brunellus on 2006-02-28
sudo halt

usually did the trick for me.

---

### Post by theturner on 2006-02-28
To invoke the usual log-out dialog, just go to System -> Preferences -> Keyboard shortcuts and configure a shortcut for "log out".

---

### Post by dvarsam on 2006-02-28
... And suppose I can create a shortcut for "log-out" (e.g. "Ctrl+Q+T")....

So, then I can go & launch the Terminal & type:

Sudo Ctrl+Q+T

... and the  Log-out window will pop-up?

Is that what you are saying?

Because I want it to popup, after I type some command in the Terminal...

---

