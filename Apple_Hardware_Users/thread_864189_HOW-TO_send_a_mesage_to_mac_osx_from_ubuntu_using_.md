---
title: "HOW-TO send a mesage to mac osx from ubuntu using SSH"
date: 2008-07-19
forum: Apple Hardware Users
---

### Post by lazertek on 2008-07-19
To send a message using ssh to a mac (remote pc) or the other way around you could use the command "write" or "wall"...

but the problem is the terminal has to be open on the remote mac...

**how do you send a message to the remote pc when the terminal is closed?**
[B]
you can always open it manually from ssh but how do you do it without manually having to open the terminal?[/B]

---

### Post by audwan on 2008-07-19
This might actually be more suitable on a Mac forum I guess, because the program to open a messagebox needs to be on the OS X-side.

I'm not a Mac user, but perhaps this might be helpful:
[http://developer.apple.com/documentation/Darwin/Reference/Manpages/mann/messageBox.ntcl.html](http://developer.apple.com/documentation/Darwin/Reference/Manpages/mann/messageBox.ntcl.html)

---

### Post by lazertek on 2008-07-19
I tried that but it said no command found... Guess i'll just launch the terminal and then use "write"

---

### Post by cyberdork33 on 2008-07-19
you could do something crazy like:
```
osascript -e 'say "Heres your message"'
```If you can make a popup or something via applescript that would work too... or you could always open a terminal via applescript and then send a message to it.

This seemed to work:
```
osascript -e 'tell application "System Events" 
> display dialog "Hello"
> end tell'
```

---

### Post by owlgorithm on 2008-07-19
Yeah, the "say" command is awesome, I have used it for this purpose. I always thought it would be cool to use alert sounds remotely as Morse code, but I've never had the time to sit down and bang it out.

---

### Post by owlgorithm on 2008-07-19
Also, it occurred to me that you could use [[COLOR="Blue"]growlnotify[/COLOR]]("http://growl.info/documentation/growlnotify.php"), which is a command-line tool to post Growl notifications. Then, use the following:

```

growlnotify --message &#8220;Mr. Watson, come here, I want to see you."

```

I have tested this without SSH. It has a syntax to allow for sending remote messages without SSH but it sounds risky -- I can't tell if it passes the password in plaintext. Of course, growlnotify would have to be installed on the Mac first. It does, however, provide the advantage of displaying message by text (not audible to others) through your command line to their GUI with the ease of echo. It's also pretty :-)

---

### Post by lazertek on 2008-07-20
yo that is cool! got more of those?

---

