---
title: "[SOLVED] I cannot install Ubuntu updates any more."
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by penguinv on 2007-12-19
This issue is resolved 
-----------------------------.

I repeated it today for the third time and the same thing happened: 

I have Ubuntu 7.04 and last week tried to install the updates. It failed. I repeated it today (a week ago). It failed again and here is the details provided in the error message.


       E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

      E: _cache->open() failed, please report.


Naturally I would like to help but I have no idea who to report this to.

Last week I tried to install just the firefox and got the same message. This week I highlighted the first and selected check rather than install and got the same message. Ditto the second.

Makes me think the problem is with my computer. 

Just a note for those who would try to OVERhelp me. This computer does not have enough RAM for 7.10 and I am not interested in upgrading, thanks.

penguinv would like this all to be easy, like a user
I'd like to add that I have installed updates several times before with no issues.

What else have I done in between?  Unsucessfully wanted to install 2 or 3 torrents, there was some reason I could not even try to install some.  I needed Java to instal Arcturus so I triied to install Java. That failed and I retried it several times, from tifferent places. I tried with deluge; failed twice.

I could guess that doing that messed up my system.

[I have 7.04 on a P-3 with about 270 MB of RAM.]

---

### Post by jfinkels on 2007-12-19
Open the terminal (Applications > Accessories > Terminal) and type the following:```
sudo dpkg --configure -a
```then type your password and press enter, and follow any directions dpkg gives you.

After that, I suggest taking a look at reading the first link in my signature on installing software.

---

### Post by penguinv on 2007-12-19
> **jfinkels said:**
> Open the terminal (Applications > Accessories > Terminal) and type the following:```
sudo dpkg --configure -a
```then type your password and press enter, and follow any directions dpkg gives you.

After that, I suggest taking a look at reading the first link in my signature on installing software.

Here's the story and it's a new day now. STORY FOLLOWS:
dahlia@Subud-desktop:~$ sudo dpkg --configure -a
Password:
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

dahlia@Subud-desktop:~$ 

Noticed:
Gnome system monitor is only running
Netstat is Zombie ??

Presses unlit update button.
Sees this


Software index is broken
It is impossible to install or remove any software.
Please use the package manager "Synaptic" or run
"sudo apt-get install -f" in a terminal to fix this issue at first.


Noticed terminal window is closed.
Opened a terminal window. did the above instruction.
It went like this:


dahlia@Subud-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-sazanami-gothic
  ttf-sazanami-mincho
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  sun-java6-jre
The following packages will be upgraded:
  sun-java6-bin
1 upgraded, 1 newly installed, 0 to remove and 46 not upgraded.
1 not fully installed or removed.
Need to get 0B/32.5MB of archives.
After unpacking 93.0MB of additional disk space will be used.
Do you want to continue [Y/n]? 

I typed the comment above. Then it refused me, viz.

dahlia@Subud-desktop:~$ y
bash: y: command not found
dahlia@Subud-desktop:~$ Y
bash: Y: command not found
dahlia@Subud-desktop:~$ 
 
So I repeated sudo apt-get install -f
...
got to the question
this time it continued

Got to a place in the terminal window that showed me the contract terms to be accepted to use the program. (I've been here before or have deja vue, heh) I see an

 ------                                   (OK)                                    -----

on the screen but it does not seem to respond to anything, mouseclicks, return key, spacebar...   This is where I have been stuck in the past, installing java. 
...
I get inspired and try arrow key, ah it turns red, Enter. BINGO

Now it's the GOLD and it starts unpacking. 

SEE the results. Notice the SERIOUS WARNING. Notice that it looks a bit like what the Ubuntu Update Package Installer, UUPI, told me.

Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
105077 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
Preparing to replace sun-java6-bin 6-00-2ubuntu2 (using .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
Setting up sun-java6-bin (6-00-2ubuntu2) ...

Setting up sun-java6-jre (6-00-2ubuntu2) ...

dahlia@Subud-desktop:~$ 

ARG and a half.
I'll try the UUPI now.

And it worked.
--------------------------------------------------------------------------------

Dear Co-Ubuntu Bean,

Now I would like to know what happened.
What was wrong; What I did.
What does it all mean?
And last, where can I go to learn more about the general structure of how Linux works,
at that beginning level. (I'm smart but I don't know the community assumptions so the beginning is the best place to start. I can move fast from there.)

Thank you many beans.
PV

PS I am going to read your link now re How to Install Anything.
[I][B]4 ways to install
1. package manager
2. synaptic[/B][/I]
programs need "to be available through" it
wondering if you install synaptic or if you use it to install a program
does it come with the OS?  *indeed it do*.
[B][I]3. with the terminal (program)
4. manually[/I][/B]
klik:// &#8594; .cmg, .sh, .bin, .exe, ...) this must be the extensions that signify the executable programs that are the output of an archive.

Next, find out what that means. Looks like I am annotating my list above as well as marking below. KISS
Libraries** (assume they are functions that do things that are useful to many programs. I do hate being told I do not need to understand what a Library is without a reference to learn what it is, just in case I do not want to be a "patted on the *** and catered to in my doltness" person. I want to really find out.  F'Real Dude.)**

discoveries: 
apt-get is a package manager.
synaptic comes with the os. (since I was told to use it re installing some torrent, I googled it. Nowhere (before your esteemed link) did I see that it was included.
there are minions of programs discoverable once you open synaptic, including libaries (sic)
(oops "programs" was my assumption. the text reads "*packages*". User wonders where to inquire about differences. There are also *repositories* (clicks link. loves tabs.) which are lists of packages. (Heaven forbid calling it a library where you find things. Library is some assigned term. Where can I find this definition?

There exists a thing called The Debian Menu which lists my installed applications. It is not there until I install it.  But I have to know it is called menu-xdg and possibly restart X (ctrl + alt + backspace) for it to show up.
Ah, how to restart X. Another mystery solved.

OK Beans, I am really tired of chasing mysteries. 
I am happy to have this guide HOWTO install anything. I will go through it all. 
If I in my newness can be of help making something to link to help others, let me know.
[I][B]
Your search - "I just installed ubuntu now what" - did not match any documents.[/B][/I]
Peace.

---

### Post by penguinv on 2007-12-19
> **jfinkels said:**
> ... I suggest taking a look at reading the first link in my signature on installing software

--
Installing software : Ubuntuguide : UDSF : Community documentation : psychocats tutorials : Restricted Formats : Root & Sudo
.

I think you gave me all my answers just above.
I also noticed the Read this prior to posting.

I will return more educated.
PV

---

### Post by jfinkels on 2007-12-19
I don't really understand what you were trying to say in your very long post above. If you have any questions, please state them clearly, descriptively, and concisely with correct English syntax and I would be happy to answer them.

Learning a new operating system can be hard, but with some perseverance, reading, and practice, you will become accustomed to Ubuntu. Let me know if I can help you with anything else.

---

### Post by penguinv on 2007-12-20
Thank you very much.  I am complete on this problem, this thread.

1. I went to edit the first post looking for the "radio button" to say this thread is closed but I couldnt find the button. As you can see I edited the post to say it was all fine. Done. Complete.

2. I clicked on a thank you button to you.
    My Java is OK. 
My "big problem" was that I was baffled by the OK button. Finally (see the line with BINGO in the longpost) I tried the arrow key and then it turned red and I knew that it had gotten selected. If I were making that page I would have a YES and a NO so you could see that one was selected already. The previous times I had only tried the spacebar and Enter Key.
    My updates are OK.
Worked like a charm after I went through the Java. Go figure.

3. I Have now read and read and read.
Your sig rules. I also read a lot of things linked to in the stickies.
I will start a new thread with "the next question" so it can be public and useful to more than just me. 

See you there.

---

### Post by Joeb454 on 2007-12-20
For what it's worth, at the top of your first post, there should be a link with a drop-down arrow called "Thread Tools" - click this and click "Mark Thread as Solved"

:)

---

