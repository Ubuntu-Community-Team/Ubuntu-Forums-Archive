---
title: "aMSN not not recognizing username and password"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-27
I have installed aMSN to use it for my hotmail account instead of gaim .. gaim is fine but looking for something more similar to MSN that runs on windows. now  I can type my logins without thinking ... I tried like 50 times and it kept telling me "Wrong username or password" ... does anybody know whether if should be working with certain preferences??? 
I am using a proxy-server ... does that affect the connecting process?

any help will be appriciated.

---

### Post by Isoss on 2006-04-27
Hello ... isn't there anybody who've had the same problem? or at least would tell me what could the problem be?

---

### Post by manicka on 2006-04-27
[QUOTE=Isoss]
I am using a proxy-server ... does that affect the connecting process?
[/QUOTE]

did you enter your proxy info into amsn as well?

Tools--> Preferences --> Connections

---

### Post by Isoss on 2006-04-28
Yes I did ... but even if I didn't enter it, there must be show a connecting error, not a login error!

---

### Post by manicka on 2006-04-28
the only thing I can think of is the username. Are you using an email address and not just the username?

---

### Post by Isoss on 2006-05-01
I am using the full e-mail address: [email]username@hotmail.com[/email] ...

---

### Post by Isoss on 2006-05-01
Does anybody have any solution for this?

---

### Post by Isoss on 2006-05-02
Helloooooooooooo .. please help ... I've been offline with MSN for days .. somebody help!

---

### Post by manicka on 2006-05-02
In the meantime, Gaim will connect to msn for you

---

### Post by Isoss on 2006-05-02
That one is not connecting either.

Actually, it connects for 10 seconds, and then it disconnects.

The wierd thing is that after I installed Ubuntu for the first time and I then solved the proxy server IP and Port problem through editing /etc/apt/apt.conf it worked! then I had to reinstall ubuntu for some reason and it didn't work as proper as it was at first.

Now I removed aMSN and installed aMSN .095 through Automatix and it's not connecting, nor giving me a wrong username and password ... just keeps logging in forever without eing Logged in!

I am using a proxy server ... I entered everything reqiured in the Preferences -> Connection ...

---

### Post by manicka on 2006-05-02
did you enter your proxy info in System--> Preferences-->Network Proxy

---

### Post by public_void on 2006-05-02
Same problem (and behind a proxy) it says the username and password are wrong. Even though i haven't changed them and its been working fine for a while. It just suddenly stopped. Strange thing is, its the exact same problem on Windows.

EDIT: found the solution on the [aMSN forums](http://amsn.sourceforge.net/forums/viewtopic.php?t=816), and guess who caused it.

---

### Post by Isoss on 2006-05-02
I ran amsn using terminal and it gave me these errors:
```
bgerror failed to handle background error.
    Original error: bad variable name "options(-proxy_writing)": upvar won't create a scalar variable that looks like an array element
    Error in bgerror: unable to convert date-time string "5//20/12/0 05::00"

```
I don't really know what is the problem ... I entered the proxy server in Preferences -> Connection choosing the option "I connect to the internet using a proxy server:" and selecting "HTTP (POST method)"
Any clues?

---

### Post by manicka on 2006-05-03
Isoss, try the link in public_viod's post

---

### Post by hellerite on 2006-05-03
You can give [http://www.meebo.com]("http://www.meebo.com") a try for basic im services until you find an answer to your problems.

---

### Post by manicka on 2006-05-03
[QUOTE=hellerite]You can give [http://www.meebo.com]("http://www.meebo.com") a try for basic im services until you find an answer to your problems.[/QUOTE]

ah good old meebo, I'd forgotten about them :)

---

### Post by Isoss on 2006-05-03
[QUOTE=manicka]Isoss, try the link in public_viod's post[/QUOTE]
Can u please make it more clear? I didn't get what you mean!
[QUOTE=hellerite]You can give [http://www.meebo.com](http://www.meebo.com) a try for basic im services until you find an answer to your problems.[/QUOTE]
Thanks a lot, it's an amazign website. I'm using it while finding my answers. althoguh it doesn't have a webcam chat or VC, but it's better than nothing!

---

### Post by manicka on 2006-05-03
Issos, I've posted a possible solution for you in your mercury thread

---

### Post by manicka on 2006-05-03
[QUOTE=Isoss]Can u please make it more clear? I didn't get what you mean!
[/QUOTE]

I meant the link to amsn forums in the section below

[QUOTE=public_void]
EDIT: found the solution on the [aMSN forums](http://amsn.sourceforge.net/forums/viewtopic.php?t=816), and guess who caused it.[/QUOTE]

---

