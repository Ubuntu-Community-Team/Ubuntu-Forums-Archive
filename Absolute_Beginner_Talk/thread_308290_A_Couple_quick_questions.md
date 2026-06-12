---
title: "A Couple quick questions"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by marcusgleason on 2006-11-27
Alright I know some people are going to laugh, but I can take it.  Everyone was new once, so no offense taken.  This has been bugging me...I understand more or less the terminal and what it does (still learning the commands but got the basics), but when you see: command..... | command.... what does that mean?  Does the command after | get entered on a second line...or all on the same line?  Kind of confusing.

I am seeing that Linux is a million times better than Windows, but how do you get used to the commands in the terminal?  By that I mean how do you know that wget [www.website.com](www.website.com) has what you are looking for?  Did you go to that website and find the specific file and path you are looking for?  If so, couldn't you have downloaded it from the website directly as opposed to using the terminal?  I'm not against the terminal, I think it will make things much better than having to go to a million different places to find what you need, just curious how you know what websites have what...if that is even the case.

I'm sorry if this is covered in another thread (classic newbie statement), but I did search around for about a half hour before I posted.  Also, automatix is ridiculous...in a good way.  It simplifies so many things for the new linux user.  I have not tried EasyUbuntu...for some reason I couldn't get it following the instructions I found on this forum.  Maybe they changed the location of the files?  I definitely think that these programs have tons of useful packages and should be recommended to everyone.

Anyway, thanks in advance for the help.

---

### Post by kdawg on 2006-11-27
The | symbol is a pipe, it takes the output from the first command and "pipes" it into the second command.  It is very useful and you see it a lot with the grep command.... like this:

```
ls -l /bin | grep zf
```

Which all this does is lists the files and their attributes in /bin and takes that entire list and searches it for anything with "zf" in it, in my case, zforce and zfgrep, then those matches are all that are output to the terminal.  Of course this is not the only use and I myself am still fairly new to all of this.  I hope I got this right and this helps out!

Oh and also, The way I think of it is the terminal is the guts of the system, behind all the gui stuff.  So its generally more powerful if you know how to use it right.  Windows has a terminal too, the command prompt, but it is pretty much phased out now, which is why linux is so much better imho.  The gui and the Terminal are two different ways of doing the same thing in a lot of cases, but the terminal gives you more options and more power.

Again, this is my opinion and I've only used linux for about a year.  I'm sure there are a lot more explanations out there as well!

A great way to learn about the terminal is to read man pages.  Regarding wget... you can type man wget and read the description it gives you and maybe that can answer some of your questions! (I myself don't know much about it either, I think I will read the man page now)

---

### Post by Agent86 on 2006-11-27
And just in case, the | symbol is the one on your keyboard that looks like a vertically enhanced colon. It's usually paired on the same key as the \ slash.

---

### Post by Smaug067 on 2006-11-27
> I understand more or less the terminal and what it does (still learning the commands but got the basics)

Try these:[Linux Commands](http://www.ss64.com/bash/), [Linux Command Directory](http://www.linuxdevcenter.com/linux/cmd/)

I've been using Ubuntu about a month and these resources have proven invaluable!

---

### Post by freebeer on 2006-11-27
for the record, even DOS supports the pipe operator... it's just not used that often.  :) 


if you type 
```

dir | more

```

You'll get a listing filling the screen, then it'll wait until you press a key to give you another "page". (provided, of course, there's enough lines in the output to require more than one "page")  :D

---

### Post by Peepsalot on 2006-11-27
Here is a tutorial on pipes and redirection, another nice thing to know.
[http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=21](http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=21)

Oh and although many examples use the "more" command, I'd recommend "less" instead since it allows up and down navigation with the arrow keys.

And in case you don't already know the most important Linux command, I will tell you: it is called "man" short for manual.  type man followed by any other command that you want to learn about, and you will be enlightened ;)

As for the question about wget, yes you basically have to know the address beforehand.  But if you already know the address, then in some cases it is simpler to use this one command than to click around a bunch of times in a web browser.
I am guessing you probably saw this command in some tutorial?  I can think of a few good reasons for using it in a tutorial/instructions:
1) It is easier for the tutorial writer to convey the exact commands than it is to explain which links to click on and where to download the file to.
2) You can use wget even if your X server(graphics environment) is broken.
3) If you are following some instructions, you were probably already in a terminal entering the steps before wget.

---

