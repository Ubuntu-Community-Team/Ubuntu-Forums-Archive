---
title: "Timer Program?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-13
Unbuntu Dapper 6.0.6, Anyone know of a program to shutdown the computer,after a specified time?  Thanks :p

---

### Post by gerbman on 2006-06-13
[QUOTE=Drakkor]Unbuntu Dapper 6.0.6, Anyone know of a program to shutdown the computer,after a specified time?  Thanks :p[/QUOTE]Check out the "shutdown" command with```
man shutdown
```in a terminal window

EDIT:  so the man pages aren't always that readable. An example of scheduling the computer to shut down at 4:51 PM would be the following:```
shutdown 16:51
```

---

### Post by 23meg on 2006-06-13
If you don't want to keep your terminal busy, end the command with a "&"

```
sudo shutdown -h 04:33 &
```

---

### Post by Drakkor on 2006-06-21
Hmmm......it worked twice when I tested it , now I get this:
drakkor@drakkor:~$ sudo shutdown -h 23:30 &
[1] 5732
drakkor@drakkor:~$ Password:
password
bash: password: command not found

[1]+  Stopped                 sudo shutdown -h 23:30

---

### Post by gerbman on 2006-06-21
[QUOTE=Drakkor]Hmmm......it worked twice when I tested it , now I get this:
drakkor@drakkor:~$ sudo shutdown -h 23:30 &
[1] 5732
drakkor@drakkor:~$ Password:
password
bash: password: command not found

[1]+  Stopped                 sudo shutdown -h 23:30[/QUOTE]sudo doesn't like running in the background...do "sudo ls" first and then try the command in the background again.

---

### Post by Drakkor on 2006-06-21
Naw,that didn't work either,as I said it worked before with just sudo.
One thing I noticed is that usually the password field is blanked out,
I can actually see the password typed out,don't know if that helps ?

---

### Post by gerbman on 2006-06-21
[QUOTE=Drakkor]Naw,that didn't work either,as I said it worked before with just sudo.
One thing I noticed is that usually the password field is blanked out,
I can actually see the password typed out,don't know if that helps ?[/QUOTE]Hmmm...does it work if you "su" first?

---

### Post by Drakkor on 2006-06-21
Nope, what's the deal with the visible password , any time I've ever used the 
terminal, it was always invisible ???

---

### Post by gerbman on 2006-06-21
[QUOTE=Drakkor]Nope, what's the deal with the visible password , any time I've ever used the 
terminal, it was always invisible ???[/QUOTE]The password should definitely be blank if you run something with sudo in the foreground (no &). I dunno.

---

### Post by Drakkor on 2006-06-21
Thanks for bearing with me,gerbman, you're right took out the "&" and the password was blank and seemed to work. Funny though, that it worked before,
and was following 23meg 's post. Guess I'll just have to wait till 11:30 PM, to 
see if it goes off,lol, Thanks !

---

### Post by gerbman on 2006-06-21
[QUOTE=Drakkor]Thanks for bearing with me,gerbman, you're right took out the "&" and the password was blank and seemed to work. Funny though, that it worked before,
and was following 23meg 's post. Guess I'll just have to wait till 11:30 PM, to 
see if it goes off,lol, Thanks ![/QUOTE]Okay, cool. But maybe I wasn't clear enough in my above post. If I open up a new terminal window and try to run a program with sudo in the background, this is what I get:```
gerb@home:~$ sudo ls &
[1] 28733
Password:
gerb@home:~$
```
...it doesn't even give me a chance to enter the password. Now, if I do```
sudo ls
Password: <blanked>

```then any following sudo commands won't require a password and can be run in the background no prob. Is that how you read my original post?

---

### Post by Drakkor on 2006-06-22
Not really sure by what you mean "running in the background"  I get this:
drakkor@drakkor:~$ sudo ls &
[1] 7588
drakkor@drakkor:~$ Password:
a;dkfadkfkdj   (visible)
bash: a: command not found

[1]+  Stopped                 sudo ls
bash: sldk: command not found
drakkor@drakkor:~$
drakkor@drakkor:~$ sudo ls
Password: (not visible)
automatix.log
Azureus Problem
Desktop
easyubuntu
Examples
Linux Podcasts
Music
Screensavers Problem
sources.list
Wallpapers

Maybe it's different in Dapper, see you're using Breezy

---

### Post by gerbman on 2006-06-22
Whoops! Forgot to update my profile...I'm using Dapper as well. The "&" tells the process to run in the background, meaning it won't tie up the terminal window while it's working. When you run a sudo command in the foreground (tying up the terminal) it has control of the terminal and will be able to prompt you for your password. After doing this your password will be "saved" for future invocations of the sudo command. That's why I suggested first running sudo with a simple command like ls in the foreground and giving it your password...it should save your password and automatically use it when you try to background the shutdown command with the "&".

---

### Post by Drakkor on 2006-06-22
Hmmmmm......... that somewhat makes some sense, I guess,lol.Still this fore-ground ,background stuff is greek to me, why would I want to use a "&" at all ??  Anyway I just
tried to redo a shutdown and got this:
drakkor@drakkor:~$ sudo shutdown -h 21:10
Password:
shutdown: already running.
drakkor@drakkor:~$
So... I guess it will be shutting down at 11:30 PM !    Thanks !

---

### Post by gerbman on 2006-06-22
I'm still not satisfied, haha...but if you are then great. But you should be able to background it with no problem, keeping your terminal free. Here's my output:```
gerb@home:~$ sudo ls
Password: <blanked>
<file listing>

gerb@home:~$ sudo shutdown -h now &
<doesn't ask for password, just shuts down>

```
You should be able to replace "now" with your time.

---

### Post by Drakkor on 2006-06-22
Yeah,maybe I didn't foreground it before I backgrounded it ??  LOL 
Thanks !

---

### Post by gerbman on 2006-06-22
[QUOTE=Drakkor]Yeah,maybe I didn't foreground it before I backgrounded it ??  LOL 
Thanks ![/QUOTE]You're welcome :)

---

