---
title: "How to install Limewire?"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by Yaksha on 2006-03-24
hey I was wondering if anyone could tell me how to install Limewire or any other progrems I'm very new to ubuntu and linux so i have no clue.

---

### Post by divague on 2006-04-03
go to [http://www.limewire.com/english/content/downloadfree2.shtml](http://www.limewire.com/english/content/downloadfree2.shtml), download the Linux (RPM), install alien using synaptic, and then in a terminal write this:

alien LimeWireLinux.rpm

this will create a .deb file, install it:

sudo dpkg -i "the-name-of-the-file".deb

limewire needs java to run, there are instructions to install java in the ubuntu help, you have to install java first.

hope this helps you :)

---

### Post by dvarsam on 2006-04-13
Hello All!!!!

Can somebody confirm that the program "Limewire" for Linux contains _HUGE_ spyware...!!! ?

I am behind a Router & when I installed it,... all was ok!

When I decided to Run it, my Router went crazy (even on an idle PC!!!)...

I decided to "Reset" the Router, but still there was "huge" traffic starting again!!!

Closing the "Limewire" program did NOT stop this "experience"...

Only Restarting my Ubuntu PC finally stopped this "spyware" process...

After the Reboot, everything went fine, until I decided to re-run "Limeware"...

Again "huge" traffic started out...

Closing the program did NOT stop this "spyware" process...

I finally decided to uninstall the "Limewire" program!

Even after the uninstall, the "Huge" traffic (on an idle PC) was still going on...

So it must be some other program installed with "Limewire"!!!
(I can NOT think of something else...?)

Restarting My Ubuntu, fixed this...

However, I am still skeptical whether I should Format My Ubuntu or NOT...

Any ideas?

Thanks.

P.S. 1>Q1: Can somebody confirm that "Limewire" includes/installs spyware?

P.S. 2>Q2: Is there any alternative program similar to "Limewire" for My Ubuntu Linux with NO spyware being installed?

---

### Post by taurus on 2006-04-13
LimeWire is a closed source but if you want to use an open source of LimeWire, then go for the Frostwire at [http://www.frostwire.com/static/downloads.html](http://www.frostwire.com/static/downloads.html).  Download the Debian/Ubuntu version and install it with 
```

sudo dpkg -i FrostWire-4.10.9-1.i586.deb

```

---

### Post by geeknation on 2006-04-13
[QUOTE=taurus]LimeWire is a closed source but if you want to use an open source of LimeWire, then go for the Frostwire at [http://www.frostwire.com/static/downloads.html](http://www.frostwire.com/static/downloads.html).  Download the Debian/Ubuntu version and install it with 
```

sudo dpkg -i FrostWire-4.10.9-1.i586.deb

```[/QUOTE]

Thanks for that! :)

---

### Post by dvarsam on 2006-04-13
> If you want to use an open source of LimeWire, then go for the Frostwire at [http://www.frostwire.com/static/downloads.html](http://www.frostwire.com/static/downloads.html).  Download the Debian/Ubuntu version & install...

Dear "taurus",

Thank you for your repply!

I installed "frostwire" (as you suggested!).

I then tried to run the program (from Terminal) & got the following:

> root@ubuntu:~# frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()

What exactly does the "look_for_java()" mean?

What "java" package am I missing, does anybody know?

Thanks.

---

### Post by taurus on 2006-04-13
Okay, here is how you fix that, assuming you already have java installed.  Open a terminal and install dos2unix which is part of the sysutil package...
```

sudo apt-get install sysutil
cd /usr/lib/frostwire
sudo dos2unix runFrost.sh

```
Now, start it again and it should run fine...

---

### Post by Yorgos on 2006-04-24
i have done everything as shown in here and the prog is installed but when i try to run it it wont run and shows no error msg.any ideas?(i have java installed)

---

### Post by S{yndrom}e on 2006-04-24
[QUOTE=Yorgos]i have done everything as shown in here and the prog is installed but when i try to run it it wont run and shows no error msg.any ideas?(i have java installed)[/QUOTE]

Yorgos I wrote a howto on how to fix this problem check it out in the "HOWTO" section

although its been like 10 mins after i posted it and he has't appeared...

---

