---
title: "Problem installing JDK..."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Sporkmaster on 2007-08-05
I installed Java Development Kit, and supposedly I should be able to use "javac" as a normal terminal command. But, I can't. I heard that this has something to do with my $PATH variable. I tried adding /usr/local/jdk/bin (which exists and contains the javac executable) to the ENV_PATH line in /etc/login.defs as follows:

[B]ENV_PATH	PATH=/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games:/usr/local/jdk/bin
[/B]
but it still doesn't show up in my terminal when I type echo $PATH:

[B]/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
[/B]
so I tried typing 

[B]PATH=$PATH:/usr/local/jre/bin
[/B]
after which, echo $PATH turned up this:

[B]/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/local/jre/bin
[/B]
with the java folder there. However, the command javac still turns up 

[B]bash: javac: command not found
[/B]

I have tried this in both Yakuake and Terminal but get the same result. Help here? What am I missing?

---

### Post by nitro_n2o on 2007-08-05
javac is in the JDK not the JRE 
this is wrong PATH=$PATH:/usr/local/jre/bin
please validate that you installed the JDK not the JRE 
check out the ubuntu docs on installing java you don't have to do this manually

---

### Post by Sporkmaster on 2007-08-05
oops. I did install the JDK but I typed the wrong thing into the terminal. After typing 

[B]PATH=$PATH:/usr/local/jdk/bin
[/B]

it works. I'm going to try a reboot to see if it works on startup

Update: No it didn't work at startup, but adding PATH=$PATH:/usr/local/jdk/bin as an autostarted application seems to have worked.
That's what I like about Ubuntu. You can use anything as anything.

---

### Post by tmth on 2007-08-05
Glad it works.
However the propper place to make these kind of changes would be in file /etc/profile. Add  :/usr/local/jdk/bin to the line  within the quotes.

---

