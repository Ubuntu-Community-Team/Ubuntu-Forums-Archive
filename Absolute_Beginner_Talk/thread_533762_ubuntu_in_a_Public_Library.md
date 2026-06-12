---
title: "ubuntu in a Public Library"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by wilbr on 2007-08-24
Hi,

I work at a public library, and we are planning on setting up 5 extra internet only terminals for our patrons. These computers were donated, and all would need a new OS, so rather than loading XP on them like our other Public computers, we were thinking of Ubuntu.  Here are my questions and concerns.

1.  I do not know too much about linux/ubuntu/debian, etc.  All I know I have learned from using my Nokia 770 tablet. I don't mind working to learn something new, but, at the same time, keep in mind that I am a newbie.


2.  Is there a way to have the computers automatically reboot (or just go to the log in screen) after X amount of minutes after log on?


3.  Is there a way to have a message appear at the log in screen or right after a patron logs on to the computer that states our computer use policies?


4.  These computers would be wireless... Would it be difficult to network them to the same printer?


5. I am concerned about about protecting our computers and our patrons...Our XP machines use DeepFreeze for this (DeepFreeze brings XP back to its previous state after every reboot)...  Is there anything like this for Ubuntu?  Even though the users are not supposed to load programs on their machines, I am not concerned about this as long as the programs are not malicious to our computers or to our patrons (since I can just delete these programs every once in a while) .  Do I need to be concerned about malicious programs with Ubuntu?  If I should be concerned, what can I do to protect our computers and patrons.

Thanks,

wilbr

---

### Post by compmodder26 on 2007-08-24
To give an answer to the first part of question #5, there is a Deep Freeze for linux:

[http://www.faronics.com/html/DFLinux.asp](http://www.faronics.com/html/DFLinux.asp)

---

### Post by Seisen on 2007-08-24
> **wilbr said:**
> Hi,

I work at a public library, and we are planning on setting up 5 extra internet only terminals for our patrons. These computers were donated, and all would need a new OS, so rather than loading XP on them like our other Public computers, we were thinking of Ubuntu.  Here are my questions and concerns.

1.  I do not know too much about linux/ubuntu/debian, etc.  All I know I have learned from using my Nokia 770 tablet. I don't mind working to learn something new, but, at the same time, keep in mind that I am a newbie.


2.  Is there a way to have the computers automatically reboot (or just go to the log in screen) after X amount of minutes after log on?


3.  Is there a way to have a message appear at the log in screen or right after a patron logs on to the computer that states our computer use policies?


4.  These computers would be wireless... Would it be difficult to network them to the same printer?


5. I am concerned about about protecting our computers and our patrons...Our XP machines use DeepFreeze for this (DeepFreeze brings XP back to its previous state after every reboot)...  Is there anything like this for Ubuntu?  Even though the users are not supposed to load programs on their machines, I am not concerned about this as long as the programs are not malicious to our computers or to our patrons (since I can just delete these programs every once in a while) .  Do I need to be concerned about malicious programs with Ubuntu?  If I should be concerned, what can I do to protect our computers and patrons.

Thanks,

wilbr

What kind of specs are the computers?

---

### Post by Seti on 2007-08-24
ubuntu is an ideal system to use for public terminals like those at your library. With a bit of research (a quick read here and there) you can easily implement what you want to do. Someone can correct me if I'm wrong, but using cron and a few scripts, you can automatically control how long people are logged in for, make a welcome message appear when they log in, and easily make it so all workstations print to a shared printer.
congrats on an effort to introduce linux to the community!

good luck!

---

### Post by wilbr on 2007-08-24
> **compmodder26 said:**
> To give an answer to the first part of question #5, there is a Deep Freeze for linux:

[http://www.faronics.com/html/DFLinux.asp](http://www.faronics.com/html/DFLinux.asp)

Oh, thanks...I should have looked there before posting.  Will this run on Ubuntu or would I have to do something to make it run.  (sorry, I did say that I am a newbie.)

---

### Post by compmodder26 on 2007-08-24
I did a little more searching and came upon a free solution for you for the first part of #5.  I involves making a few scripts but nothing too complicated:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux)

---

### Post by eapache on 2007-08-24
DeepFreeze is only for SLED (commercial), not Ubuntu.

1. As long as all of your hardware is detected, you will not need much knowledge of linux, and even then you will be able to find someone to help in the forums.

2. I'm not sure if there is a way to do this automatically, but there should be a script for it. I'll take a look.

3. Yes, although it depends what you want it to do. If you just want a warning, it will be quite easy. An 'accept/decline' box will be slightly trickier.

4. The only difficulty here would be if the wireless card was not detected at all, but you should have no problems with your printer. And there are workarounds for most wireless cards that aren't supported directly.

5. You can use a low-privilege account that forbids users from installing or uninstalling software, or accessing system folders etc. That should be all you need.

---

### Post by rexy on 2007-08-24
i think everything you specified can be done using ubuntu, or any os for that matter. If you need specific solutions you need to be more specific in your questions though.

like the automatic back to login example, do you just want to kill the terminal X amount of time after a logon or after a certain amount of inactivity?

regarding deep freeze, you have to understand that using linux without Superuser rights means that by default you can only write in a limited amount of places. With a few modifications you can set it up such that a user can only write to it's home directory, and/or enforce quota on parts of the disk programs write to prevent users from abusing programs to fill up parts of the disks. I cant really imagne a reason why you would need to use a deepfreeze system with ubuntu, just wipe user created data, which can only exist in specific locations and you have a fresh system.

Showing a message on login is fairly easy, using python or something you can write a small program that opens a window and displays a certain text file, someone probably already coded som ething similar i'm sure. Just add that to the login sequence, i believe under sessions and it will automaticly start as someone logs on to the terminal.

---

### Post by lluisanunez on 2007-08-24
Hi,
You might be interested in this:
[Linux in action: A public library's success story]("http://www.linux.com/articles/35832")

And this:
[do you ubuntu?]("http://www.librarian.net/stax/2042/do-you-ubuntu/")

Good luck!

---

### Post by Seisen on 2007-08-24
A better option would be to set them up so that they boot up from the network, but they may not be an option with the wireless cards.

---

### Post by wilbr on 2007-08-24
Seisen- They are, for the most part, PII & PIIIs with either 256 or 512 RAM.

Seti - thanks for your kind words.  I am really excited to learn more about open-source/ubuntu, and to hopefully demonstrate to the library's patrons that they do have alternatives to Microsoft & Apple.

compmodder26- Thanks!  I'll check out that script.

eapache- Thanks for all the information. Yeah, just having a warning is good enough.  Also, I don't have the wireless cards yet, so I am going to check their compatibility with Ubuntu before I buy them.

Thanks again, and keep the information coming!

-wilbr

---

### Post by rexy on 2007-08-24
yeh it's hard to find a decent wireless card with wpa wpa2/aes support been trying to find out myself too which have good support,since i'm stuck with an acx111 chip based wireless.  For which support is sorely lacking, and still wont be supported in the gutsy kernel either bar WEP encryption.
Which is about as good as no encryption unless you have an enterprise system which changes the key like every 5 minutes.

---

### Post by Seisen on 2007-08-24
You can check out these video's on youtube

[http://youtube.com/user/oldcomputermann]("http://youtube.com/user/oldcomputermann")

Also he is a member on the forum as "oldcomputermann" maybe he can help steer you in the right direction.

---

### Post by MoxJet on 2007-08-24
This is a great idea! I am sure it will work great!

When you get more into hacking your ubuntu boxes (I am sure you will get the motivation when you get started fiddling around with Linux systems), try this:
[http://www.linuxtoys.org/multiseat/multiseat.html](http://www.linuxtoys.org/multiseat/multiseat.html)
It makes you run several seats on one computer, like say three-four sets of monitor, keyboard, mice to one computer! Good luck!

---

### Post by wilbr on 2007-08-24
These responses are great, and are providing with tons of motivation to get this going. 


rexy- Yes, since these computers are meant to be used for an hour or less (since we always have a long line for our computers), we want the computers to automatically log a user off an hour after they log in.  Is this possible?



Seisen- We don't have a server at our library yet. (We are going to have one by the end of this year though.) 

We are not going to be using WEP since the PCs are going to be on our public wireless so can I just follow the following wiki article when buying the cards:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Dr Small on 2007-08-24
You could write a crontab script which would make the computer do a reboot every hour, or have it shutdown, because once it comes back up, it starts counting down again, and if a person didn't get on immediately, they would have less time.

But it can be done with a crontab script.

Dr Small

---

### Post by Aishiko on 2007-08-24
> **Dr Small said:**
> You could write a crontab script which would make the computer do a reboot every hour, or have it shutdown, because once it comes back up, it starts counting down again, and if a person didn't get on immediately, they would have less time.

But it can be done with a crontab script.

Dr Small
could it be written such that they'd have t olog in using a common password and user name like Library and Library?

that way each user would get the same amount of time?

---

