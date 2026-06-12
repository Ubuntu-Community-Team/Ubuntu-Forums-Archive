---
title: "what should i install after ubuntu works (now...)"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-11
what should i install first and how?? 
is there an security updates , firewall, antispam? anything else recomnded?

---

### Post by ArieT on 2007-03-11
Use your package manager for installing software: system -> administration -> synaptic package manager. Search in the description for anything you want.

---

### Post by sad_iq on 2007-03-11
Well first enable extra repositories: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29)
...folow the guide and you should have everything updated!!!
 You do not need (as I recall) any antispyware, antispam programs, and there is a large dabate on antivirus...some claim you should only install it if you move any of your files to a Windows computer(so as not to infect it)...but if you have an antivirus on your windows comp it should pick up any virus that your files hold.
 As for a firewall...well it's not really necessary under Ubuntu as it comes with no open ports (no open ports=no danger -in theory)...but you could install firestarter just in case you install a program that opens ports!

---

### Post by groeswenphil on 2007-03-11
I got a book. Ubuntu Linux for Non-Geeks by Rickford Grant.

He says not to worry too much about security issues.
Have you got a firewall in your router?

Updates just appear to arrive automatically. Watch out for a little orange icon next to the clock in the top right hand corner.

Personally, as soon as I got mine to work, I just bumbled around experimenting.

The book I mentioned is a really great read.
All the best,
Phil

---

### Post by igknighted on 2007-03-11
Security updates will show up in a little orange icon in your system tray (upper right).  A firewall is already installed, it can be edited via the command line.  Most ports are closed by default I believe.  If you want a GUI to control the firewall easier, install "firestarter" from synaptic.  Anti-viruses are available, but I don't run one because it's not worth my system resources to lower the risk of windows users I interact with.  If you are running a mail server there are anti-spam programs, but for a desktop I'm not sure what you would want one for.

Oh, for a client... I think thunderbird and evolution have spam filters installed.

---

### Post by Talon2 on 2007-03-11
> **fanny said:**
>  antispam? 

You could just sign up for a Gmail account:

mail.google.com

Then you don't have to worry about finding an antispam utility since Google provides one.  You don't even have to worry about having an email client and you don't need to worry about loosing your data (unless Goggle has a big problem).

---

### Post by houstonbofh on 2007-03-11
> **Talon2 said:**
> You could just sign up for a Gmail account:

mail.google.com

Then you don't have to worry about finding an antispam utility since Google provides one.  You don't even have to worry about having an email client and you don't need to worry about loosing your data (unless Goggle has a big problem).
You just have to trus a company that says it keeps all data it has...  :shock:  Thunderbird has a good spam filter.  Evolution has a weak spam filter.

---

### Post by steveneddy on 2007-03-11
Search the forums for what you want to do and someone will give you the answer. reading and searching the forums will be more helpful than making a dozen or more posts. This is not the first time I have seen this question, so someone has answered it for you already. Careful searching and becoming familiar with the synaptic package manager will do wonders for your experience.

Don't go too fast and take everything in. There is a lot to learn and if you take everthing one small step at a time then the experience will be richer.

Surf on Firefox, IM with GAIM and play with the terminal:

Open the terminal and type, actually, copy and paste this command:

```
sudo apt-get install cowsay 
```

type your password when prompted

after installation, in a terminal type:

```
cowsay ubuntu rocks
```

It's just a toy, but you will learn to use the terminal like this often. Don't be scared and remember that if someone has code to run in terminal and you want to do what they are telling you, then highlight the phrase with your mouse, open the terminal if it's not already, use the middle mouse button, the scroll wheel, press down on the wheel, and it will paste your code into the terminal.

No need in Linux to press copy or right click and then select copy. Just highlight, go to where you want to paste and press down on the wheel. Easy.

Welcome to the world of Linux.

-SE

---

