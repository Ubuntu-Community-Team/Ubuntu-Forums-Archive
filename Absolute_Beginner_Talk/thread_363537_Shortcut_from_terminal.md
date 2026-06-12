---
title: "Shortcut from terminal"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by jwest21 on 2007-02-17
I read somewhere once how to do this and can't find the page now.

I want to set up a shortcut from terminal that opens up a program...for example, when I type "firefox" it opens up mozilla firefox.

I mainly want to do this for programs that I'll run in wine so I don't have to type "wine /really/long/path/to/the/folder/program"

I remember it involved creating a file with the command and putting it in the correct folder...or something.

---

### Post by jordanmthomas on 2007-02-17
something like this perhaps
```
alias winprogam='wine /really/long/path/to/the/folder/program'
```
slap that in ~/.bashrc and then type winprogram to run wine /really/long/path/to/the/folder/program

**after logging out of your terminal and back in, of course.

---

### Post by jordanmthomas on 2007-02-17
Another way:

```
sudo nano /usr/bin/nameofshortcut
```

put this in there
```
#!/bin/bash
wine /path/blah &

```
ctrl-x, y, enter
```
sudo chmod +x /usr/bin/nameofshortcut
```

---

### Post by jwest21 on 2007-02-17
Thanks jordanmthomas!

I used the second method you posted and worked great.

I understand everything you wrote except the ctrl+x, y, enter part.  I know ctrl+x will break out of the program running, but not sure what the rest does.

---

### Post by mcduck on 2007-02-17
for most of the applications you don't need to do any shortcuts. For example 'firefox' starts firefox by default. usually just typing the apps name is enough, as the executable file has same name and is in your path.

---

### Post by jordanmthomas on 2007-02-17
> **jwest21 said:**
> Thanks jordanmthomas!

I used the second method you posted and worked great.

I understand everything you wrote except the ctrl+x, y, enter part.  I know ctrl+x will break out of the program running, but not sure what the rest does.

That was just to save using nano.  I wasn't sure if you knew how.  That's all I meant.
ctrl-x exit nano
y --> answer yes when it asks if you want to save first
Enter --> accept default fileneame
Ctrl-c is actually what quits programs.

Sorry if I made it more confusing than it needed to be.

---

### Post by jwest21 on 2007-02-17
oh, okay...I thought you needed to do that after exiting and saving...haha...thanks for noobieizing it for me anyway ;)

---

