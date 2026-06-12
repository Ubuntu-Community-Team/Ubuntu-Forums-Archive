---
title: "passwords really needed for login and users and sudo stuff?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Zenmind on 2006-11-27
serious question... when you setup Ubuntu you have to create usernames and passwords and login names and passwords, and whatever else.  Is It REQUIRED to have a passwrod for all of these? or can you leave the password nlank and move on in the process?  I have done this on my macs and no issues.

I am the sole user and basically do not need to worry about this Password stuff. the computer that will have ubuntu on there will not have anything of personal importancere: secure information so just wondering if the password left blank will work on setup.  extra stuff i do not have to type, etc....

just asking.

thank you.

---

### Post by AndyCooll on 2006-11-27
As far as I'm aware, you do need a password.

You can however set your system up so that it automatically logs in to a user account (e.g. yours). I think the settings are in System-->Administration-->Login screen (or something similar, I'm not at my Ubuntu box at the moment sorry).

:cool:

---

### Post by konst88 on 2006-11-27
I think that in the beginig, you don't know the linux well, so you make some mistakes.
When it askes for password, it askes for additional attention, so less chance for mistakes.
But i think after you play with ubuntu some time, and understand well what's going on, you may remove the password for sudo, but still login as a normal user.
I may be wrong, but i am more then a month without it, and all just fine.

---

### Post by Zenmind on 2006-11-27
Thank you - but not a real concrete knowledgeable answer yet.

Hmmm....

---

### Post by MartynA on 2006-11-27
AFAIK, you need to set a root password and user password during the installation. As someone said, you can remove the password for sudo by and set up auto-login, to make things easier. Some reference:

[http://ubuntuforums.org/showthread.php?t=17520](http://ubuntuforums.org/showthread.php?t=17520)

---

### Post by faithsnathan on 2006-11-27
Yes, you should have a password for doing any sudo (administrative) tasks.  The reasoning behind this is:  if a virus/spyware/whatever were to try to do something destructive on your computer, it would do it as sudo.  If it's password protected, then the virus/whatever cannot execute that task.  This is one great security feature that linux has that Windows does not.  It may be a little annoying at first, but if you think of it along those lines and just do it for a little while, it'll become "just the way it is" for you.  My wife isn't big into computers, but she got into it after a couple of weeks.

Also, if you go ahead and change it to where it will auto-log you into your screen name, then you'll only have the password issue whenever you try to do an administrative task (either in the terminal using sudo or graphically in the Administration section).

Hope this helps!

Nathan

---

### Post by MartynA on 2006-11-27
Also, if you don't have a user or root password and enable any form of network login (i.e. sshd) then you're in for a whole lot of trouble.

---

### Post by Zenmind on 2006-11-27
ok - thank you.

---

### Post by yota on 2006-11-27
> 
I am the sole user and basically do not need to worry about this Password stuff. the computer that will have ubuntu on there will not have anything of personal importancere: secure information so just wondering if the password left blank will work on setup. extra stuff i do not have to type, etc....

The point in having a password is not just to protect your informations from people, but from malicious software too.
The system asks for a password anytime an action can potentially impact on its configuration; if there's no password (like Windows) every single program you dowload&launch can do anything it wants with your computer (spam, ddos and be a part of a botnet included).
Anyway free software is about freedom, so if you like a more usable system at the cost of security you can (but I really would not advice you to) log on as root with an empty password (e.g. linspire does so by default). In that way no confirmation will be asked ever.
But I suppose password requests are a little hassle for a great security gain (and they teach implicitly what's safe and what's not).

---Edit: damn! I'm so slow writing in english! faithsnathan has already told what I wanted to say... well at least I hope that two answers are better than none... :)

---

### Post by konst88 on 2006-11-27
1. What is the chance to get a virus? I don't think i'll manage to get one..
2.If you have network login, so you should have the password, but i am talking about a single user pc.
3.Programs will not to try to use sudo, because they know it should be password there;)

---

### Post by _David on 2006-11-27
I am trying to install xampp and ubuntu will not let me use the auto extractor to extract the tar file into the /var/opt directory could some one tell me how to get root access for this purpose and others like qtparted?

---

### Post by faithsnathan on 2006-11-27
> ---Edit: damn! I'm so slow writing in english! faithsnathan has already told what I wanted to say... well at least I hope that two answers are better than none... :smile:

Well, thanks for the compliment!    :redface:  I'm glad I'm finally at the point where I can pitch in my help too, and not just receive help.  :biggrin:

---

### Post by faithsnathan on 2006-11-27
konst88,

>   1. What is the chance to get a virus? I don't think i'll manage to get one..  

Check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=25421") by Artificial Intelligence.

>   2.If you have network login, so you should have the password, but i am talking about a single user pc.  

As yota and I said above on this thread, a password will help keep any malicious or potentially malicious software from wreaking havoc on your computer (i.e. doing administrative stuff that could make your computer bonkers).

>   3.Programs will not to try to use sudo, because they know it should be password there:wink:  

Never underestimate a hacker.  Doing things on a wish and a prayer may not always work on your computer.  I hope that doesn't sound too mean, but I'd like to emphasize the fact that security in Ubuntu is already set up for you, and tinkering w/ the security too much can leave your computer as open as a screen door on a submarine.

I hope this answers your questions.

Nathan

---

### Post by faithsnathan on 2006-11-27
> **_David said:**
> I am trying to install xampp and ubuntu will not let me use the auto extractor to extract the tar file into the /var/opt directory could some one tell me how to get root access for this purpose and others like qtparted?
_David, you might try [this article]("http://monkeyblog.org/ubuntu/installing/#source").  If it doesn't work, you might want to search the forums for the answer to it (or even start a new post about it).  If you use a clear title about it, I'm sure someone will answer it soon.

About the gparted thing, though:  if you open it in the terminal using ```
 sudo gparted 
``` , then it should open just fine.  Remember the disclaimer for gparted, though, that you should back up your data, be careful with it, et cetera.

---

### Post by _David on 2006-11-30
> **faithsnathan said:**
> _David, you might try [this article]("http://monkeyblog.org/ubuntu/installing/#source").  If it doesn't work, you might want to search the forums for the answer to it (or even start a new post about it).  If you use a clear title about it, I'm sure someone will answer it soon.

About the gparted thing, though:  if you open it in the terminal using ```
 sudo gparted 
``` , then it should open just fine.  Remember the disclaimer for gparted, though, that you should back up your data, be careful with it, et cetera.

I can run qtparted that way fine however it should ask for the root password as other applications do. I think this may be a bug.

As for the guide it is extremely helpful if the ubuntu community would do more like that windows would go bankrupt.

---

