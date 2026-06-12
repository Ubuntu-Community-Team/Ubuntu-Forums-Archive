---
title: "The Linux Nightmare continues"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Permanent Beginner on 2007-07-25
So far every single instruction I've received from any source was either wrong or incomplete, and I've had to come here and ask you guys what the real answer is.

Here's today's nightmare.  I finally get Ubuntu running (by going against instructions that I had received), and the first thing I want to do is uninstall every application that isn't bolted down.

So I go into Add/Remove Applications, start with removing  the games, and the screen asks me for a password.  

I tried every password or user name I could think of, and it either said that what I typed was wrong, or Ubuntu  just froze.  Yes I am observing case.

What's the apparently undocumented secret password?

Better yet, how do I make my Ubuntu completely password- and username-free?  The only thing I need passwords is to help me get more frustrated, inconvenienced, and miserable.  Since in my opinion these are negative attributes, I want to get rid of all password requests.

Thank you.

PB

---

### Post by feelie88 on 2007-07-25
it should be your login password

---

### Post by tgm4883 on 2007-07-25
> **Permanent Beginner said:**
> So far every single instruction I've received from any source was either wrong or incomplete, and I've had to come here and ask you guys what the real answer is.

Here's today's nightmare.  I finally get Ubuntu running (by going against instructions that I had received), and the first thing I want to do is uninstall every application that isn't bolted down.

So I go into Add/Remove Applications, start with removing  the games, and the screen asks me for a password.  

I tried every password or user name I could think of, and it either said that what I typed was wrong, or Ubuntu  just froze.  Yes I am observing case.

What's the apparently undocumented secret password?

Better yet, how do I make my Ubuntu completely password- and username-free?  The only thing I need passwords is to help me get more frustrated, inconvenienced, and miserable.  Since in my opinion these are negative attributes, I want to get rid of all password requests.

Thank you.

PB

The password that it is asking for is the password of the current user (providing the current user has sudo priviledges, which the default account does)

Why are you using Ubuntu if you want no username or passwords?  That would be a huge security risk.

---

### Post by jvc26 on 2007-07-25
Its not undocumented - its your login password.
Il

---

### Post by wolfen69 on 2007-07-25
the very nature of linux demands passwords. without them, you might as well be using windows without a firewall.

---

### Post by Atomic Dog on 2007-07-25
sorry you have had such troubles.  I have found most responses to be accurate on this forum.

Synaptic requires your user password, the one you log in with.  I am assuming you are using the default account, one that makes you a sudo'er.  A simple test would be to type "sudo su" then your password in a terminal session.  If it takes your password and the prompt changes to something like "root@systemname:" then you are certainly part of that group and should not have problems using synaptic.

ps. make sude you close the terminal after the test

---

### Post by st33med on 2007-07-25
No, you don't want to get rid of password requests. Reason? Security. Say a hacker got into your system and you didn't have those on. He could freely delete files, make your computer into a zombie, or even screw around with you (if the person who was hacking really hated you:P). 

And it is definitely better than Vista's password for just changing your desktop.

---

### Post by tgm4883 on 2007-07-25
> **wolfen69 said:**
> the very nature of linux demands passwords. without them, you might as well be using windows without a firewall.

Well, you can remove the password, but it is strongly urged against

---

### Post by st33med on 2007-07-25
> **wolfen69 said:**
> the very nature of linux demands passwords. without them, you might as well be using windows without a firewall.

But if your using windows with its own firewall, there would be no difference;)

---

### Post by stchman on 2007-07-25
> **Permanent Beginner said:**
> So far every single instruction I've received from any source was either wrong or incomplete, and I've had to come here and ask you guys what the real answer is.

Here's today's nightmare.  I finally get Ubuntu running (by going against instructions that I had received), and the first thing I want to do is uninstall every application that isn't bolted down.

So I go into Add/Remove Applications, start with removing  the games, and the screen asks me for a password.  

I tried every password or user name I could think of, and it either said that what I typed was wrong, or Ubuntu  just froze.  Yes I am observing case.

What's the apparently undocumented secret password?

Better yet, how do I make my Ubuntu completely password- and username-free?  The only thing I need passwords is to help me get more frustrated, inconvenienced, and miserable.  Since in my opinion these are negative attributes, I want to get rid of all password requests.

Thank you.

PB

I don't recommend getting rid of passwords.  Linux by nature is secure.  If you want no security use Windows.

---

### Post by pofigster on 2007-07-25
If your login password isn't working, there's a way to set a password for the root user (login name root).  I can't seem to remember where it is though (pretty sure it's under System >> Administration >> Users and Groups) and then, worst case scenario, you could just log in as root, make the changes, and log back in as your regular user name.

---

### Post by Tomosaur on 2007-07-25
> **Permanent Beginner said:**
> So far every single instruction I've received from any source was either wrong or incomplete, and I've had to come here and ask you guys what the real answer is.

Here's today's nightmare.  I finally get Ubuntu running (by going against instructions that I had received), and the first thing I want to do is uninstall every application that isn't bolted down.

So I go into Add/Remove Applications, start with removing  the games, and the screen asks me for a password.  

I tried every password or user name I could think of, and it either said that what I typed was wrong, or Ubuntu  just froze.  Yes I am observing case.

What's the apparently undocumented secret password?

Better yet, how do I make my Ubuntu completely password- and username-free?  The only thing I need passwords is to help me get more frustrated, inconvenienced, and miserable.  Since in my opinion these are negative attributes, I want to get rid of all password requests.

Thank you.

PB

If you want to uninstall every application which is bolted down, then you should have installed the server version of Ubuntu, which has no GUI. If you want a GUI on top of that, you can install it manually by install the appropriate packages from the repositories.

As for your password - it is the same password as you use to log on.

---

### Post by mlentink on 2007-07-25
The password you're being asked for is the password you entered during the installation process. But seeing as how you said you did not really perform that install in a orthodox way...

Might I ask one question first?
If you are really having such a tough time installing Ubuntu, why bother? What is it you want to achieve? 
Tell us what you expect from ubuntu and we might better be able to help you out.

---

### Post by rich.bradshaw on 2007-07-25
Why did you have so many problems before? What was the problem?

---

### Post by por100pre1 on 2007-07-25
> **rich.bradshaw said:**
> Why did you have so many problems before? What was the problem?

The poster doesn't want to use any passwords at all.

---

### Post by tgm4883 on 2007-07-25
> **por100pre1 said:**
> The poster doesn't want to use any passwords at all.

Thats not what he was asking, he was asking the OP what the problem was with the installation, hoping that it may shed some light on what he did to install it and why it isn't working properly now.

---

### Post by por100pre1 on 2007-07-25
> **tgm4883 said:**
> Thats not what he was asking, he was asking the OP what the problem was with the installation, hoping that it may shed some light on what he did to install it and why it isn't working properly now.

I remember this:

[QUOTE=Permanent Beginner]Better yet, how do I make my Ubuntu completely password- and username-free? The only thing I need passwords is to help me get more frustrated, inconvenienced, and miserable. Since in my opinion these are negative attributes, I want to get rid of all password requests.[/QUOTE]

---

### Post by tgm4883 on 2007-07-25
> **por100pre1 said:**
> I remember this:

Correct, thats what the OP wants, is to not have any passwords.  But since he can't even sudo how is he going to achieve this?

This is why rich.bradshaw asks what his problems were before.  Perhaps we can either fix these problems, or we can see what he did to break sudo.

---

### Post by r4ik on 2007-07-25
Perhaps the OP did not break sudo and

[http://ubuntuforums.org/showthread.php?p=2162248#post2162248](http://ubuntuforums.org/showthread.php?p=2162248#post2162248)

helps.

Good luck !

---

### Post by Permanent Beginner on 2007-07-25
"it should be your login password"

Well, I could have sworn that I did that at least twice, but I did it again and it worked.  

Maybe this whole thing is over my head.  Every source told me "just burn a cd and it'll run"...you know that's not true, you have to do it some special way that ordinary people don't know about.  Nobody anywhere told me about the "off" switch, I had to come here and find out about that.  The instructions for installing and partitioning said that hard drives have an "hd" designation; mine has an "s  something" designation which threw me off for a while.  And absolutely positively nobody told me that my login password had admin status.

Maybe I'm just stupid but I've read every instructional doc I could find and none of these little but essential scraps of information penetrated my consciousness.  I'm thinking that the Linux community is a community that likes puzzles and games, and people who want their computers to just work are a different group.

Thanks

PB

---

### Post by tgm4883 on 2007-07-25
> **Permanent Beginner said:**
> "it should be your login password"

Well, I could have sworn that I did that at least twice, but I did it again and it worked.  

Maybe this whole thing is over my head.  Every source told me "just burn a cd and it'll run"...you know that's not true, you have to do it some special way that ordinary people don't know about.  Nobody anywhere told me about the "off" switch, I had to come here and find out about that.  The instructions for installing and partitioning said that hard drives have an "hd" designation; mine has an "s  something" designation which threw me off for a while.  And absolutely positively nobody told me that my login password had admin status.

Maybe I'm just stupid but I've read every instructional doc I could find and none of these little but essential scraps of information penetrated my consciousness.  I'm thinking that the Linux community is a community that likes puzzles and games, and people who want their computers to just work are a different group.

Thanks

PB

The hard drive thing changed recently, went from being hdX to sdX.  Most computers it is pop the cd in and it will run, but there are a few brands and components out there that cause trouble.

---

### Post by por100pre1 on 2007-07-25
Sorry for any inconvenience I could have caused... I just have 3 months using Linux and I know how you feel. Just keep in mind that Linux is not Windows nor an alternative... I needs learning, just like we took time to learn Windows. But I tell you... learning how to use Linux is a rewarding experience. But is up to you to give yourself that chance. Hope you stay around.

---

### Post by tgm4883 on 2007-07-26
> **por100pre1 said:**
> Sorry for any inconvenience I could have caused... I just have 3 months using Linux and I know how you feel. Just keep in mind that Linux is not Windows nor an alternative... I needs learning, just like we took time to learn Windows. But I tell you... learning how to use Linux is a rewarding experience. But is up to you to give yourself that chance. Hope you stay around.

If it's not Windows and not an alternative to windows, what is it?

---

### Post by mpeters on 2007-07-26
> **Permanent Beginner said:**
> "it should be your login password"

Well, I could have sworn that I did that at least twice, but I did it again and it worked.  

Maybe this whole thing is over my head.  Every source told me "just burn a cd and it'll run"...you know that's not true, you have to do it some special way that ordinary people don't know about.  Nobody anywhere told me about the "off" switch, I had to come here and find out about that.  The instructions for installing and partitioning said that hard drives have an "hd" designation; mine has an "s  something" designation which threw me off for a while.  And absolutely positively nobody told me that my login password had admin status.

Maybe I'm just stupid but I've read every instructional doc I could find and none of these little but essential scraps of information penetrated my consciousness.  I'm thinking that the Linux community is a community that likes puzzles and games, and people who want their computers to just work are a different group.

Thanks

PB

hd designates an IDE drive, sd designates scsi (or SATA)

Regards your user and admin rights read this page - [https://help.ubuntu.com/7.04/administrative/C/](https://help.ubuntu.com/7.04/administrative/C/)

---

### Post by asmoore82 on 2007-07-26
> **tgm4883 said:**
> If it's not Windows and not an alternative to windows, what is it?

GNU/Linux is an Operating System.
Asking what it is in the context of Windows really makes little sense.

---

### Post by tgm4883 on 2007-07-26
> **asmoore82 said:**
> GNU/Linux is an Operating System.
Asking what it is in the context of Windows really makes little sense.

I beg to differ, Contrary to popular belief Windows is also an Operating System (As is OS X).  Since they are both OS's, would they not be alternatives to each other?  Is Honda not an alternative to Toyota? 

I always believed there were two groups on these forums, those who think Linux is better than Windows, and those who say Linux is an alternative to Windows.  Now your telling me that they are both wrong.  That Linux in no way, shape or form relates to Windows?

We're talking about 2 different Operating Systems.  It's not like I am asking what is an apple compared to the Atlantic Ocean.

---

### Post by asmoore82 on 2007-07-26
What if we agree to say that Windows is an alternative to UNIX or Macintosh systems.

---

### Post by tgm4883 on 2007-07-26
> **asmoore82 said:**
> What if we agree to say that Windows is an alternative to UNIX or Macintosh systems.

We can agree to that.  But did you conveiniently leave out linux?

---

### Post by asmoore82 on 2007-07-26
Ubuntu is always
Debian which is always
Linux which is always
UNIX.

:KS

---

### Post by misfitpierce on 2007-07-26
username password used when installing ubuntu.

---

### Post by Permanent Beginner on 2007-07-26
" hd designates an IDE drive, sd designates scsi (or SATA) "

So I've got am SCSI hard drive and didn't know it?  Might be; the motherboard has an SCSI port for a Zip drive...

Is that good or bad?

PB

---

### Post by tgm4883 on 2007-07-26
> **asmoore82 said:**
> Ubuntu is always
Debian which is always
Linux which is always
UNIX.

:KS

ah

But isn't it

Ubuntu is always
Debian which is always
Linux which is always
Minix which is always
UNIX.

:EDIT:

Although, linux contains no Minix code that I know of

---

### Post by tgm4883 on 2007-07-26
> **Permanent Beginner said:**
> " hd designates an IDE drive, sd designates scsi (or SATA) "

So I've got am SCSI hard drive and didn't know it?  Might be; the motherboard has an SCSI port for a Zip drive...

Is that good or bad?

PB

No, the above quote is no longer valid.  All hard drives are now designated at sdX

---

### Post by Permanent Beginner on 2007-07-26
Thanks, TGM;

Massive Thanks to everyone.

PB

---

### Post by Modernity on 2007-07-26
> **tgm4883 said:**
> No, the above quote is no longer valid.  All hard drives are now designated at sdX

Not necessarliy true. I installed 7.04 last month on an old machine and it designated them hd1, hd2, hd5. If your computer has sata, it will show up as sd1 and so forth. So IDE=hd and Serial ata= sd.

---

### Post by JPorter on 2007-07-26
> **Permanent Beginner said:**
> "it should be your login password"

Well, I could have sworn that I did that at least twice, but I did it again and it worked.  

Maybe this whole thing is over my head.  Every source told me "just burn a cd and it'll run"...you know that's not true, you have to do it some special way that ordinary people don't know about.  Nobody anywhere told me about the "off" switch, I had to come here and find out about that.  The instructions for installing and partitioning said that hard drives have an "hd" designation; mine has an "s  something" designation which threw me off for a while.  And absolutely positively nobody told me that my login password had admin status.

Maybe I'm just stupid but I've read every instructional doc I could find and none of these little but essential scraps of information penetrated my consciousness.  I'm thinking that the Linux community is a community that likes puzzles and games, and people who want their computers to just work are a different group.

Thanks

PB

Come on now, that's your frustration talking.  

I'm not sure how you've managed to overcomplicate your install to the point that you couldn't just install it and start using it without beating your head on a wall... that's just not what most users encounter when installing.  

The distro comes pre-configured with just about everything the average desktop productivity user needs to get rolling and do basic tasks like surf the web, download email, write a letter, use a spreadsheet, etc.

I don't think what you've experienced can be considered "typical".  And why are you trying to uninstall a bunch of stuff anyway?  Some special intended use?  It's not that bloated in standard form.

---

### Post by tgm4883 on 2007-07-26
> **Modernity said:**
> Not necessarliy true. I installed 7.04 last month on an old machine and it designated them hd1, hd2, hd5. If your computer has sata, it will show up as sd1 and so forth. So IDE=hd and Serial ata= sd.

Feisty replaced the PATA storage drivers with libata-pata.  This should make everything sdX instead of hdX.  Technically we should be using the UUID though instead of /dev/**X

[https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks](https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks)

---

### Post by asmoore82 on 2007-07-26
> **tgm4883 said:**
> ah

But isn't it

Ubuntu is always
Debian which is always
Linux which is always
Minix which is always
UNIX.

:EDIT:

Although, linux contains no Minix code that I know of

No.
Linux is UNIX and Minix is UNIX but Linux is not Minix.
The first Linux kernel was built on a Minix system but not based on said Minix system.

:confused: >>> :lol:

---

### Post by por100pre1 on 2007-07-26
> **tgm4883 said:**
> If it's not Windows and not an alternative to windows, what is it?

To tell people that Linux is just an alternative to Windows is wrong. In fact it is a different OS which works differently in many ways. I'm sure you know that better than me...

---

### Post by fastpakr on 2007-07-26
> **tgm4883 said:**
> Feisty replaced the PATA storage drivers with libata-pata.  This should make everything sdX instead of hdX.  Technically we should be using the UUID though instead of /dev/**X

[https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks](https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks)

I'm running Feisty at home, and both of my PATA drives are hd's.

---

### Post by tgm4883 on 2007-07-26
> **por100pre1 said:**
> To tell people that Linux is just an alternative to Windows is wrong. In fact it is a different OS which works differently in many ways. I'm sure you know that better than me...

Define alternative and see post #26

---

### Post by nlbs on 2007-07-26
I think everyboddy will agree with me
this long conversation is for a simpel problem which is by default not a problm at all . 
Its a Feature . I cant belief 4 Pages Long conversation just for this small topic ??

---

### Post by por100pre1 on 2007-07-26
> **tgm4883 said:**
> Define alternative and see post #26

In that post you used the words I *really* wanted to use... **yes, Linux is better than Windows** ;).

---

### Post by Old Pink on 2007-07-26
To be honest, I don't think you have enough common sense for Linux. I mean, something asks you for your password, and you've only set one since setup, what's it going to be?

And a google search for "what's the sudo password?" then tells you, without even clicking: "[SIZE=-1]Therefore it sets the **sudo password** to be the same as that user's **password**"As for the hda/sda thing you complained about, a quick google for "difference between hda sda" quickly provides us with "[/SIZE]HD - denotes that the disk drive is IDE based and  if the drive SCSI or SATA based it will be designated as SD."

Installing Windows takes more knowledge than installing Linux, Windows still has a text based interface, most Linux desktops give you a full on LiveCD with firefox and web access to find any answer, as well as System > Help and Support which would've given you many of your answers.

For example. When trying to find out your password, you could've hit System, then Help and Support, and typed in password. A quick scroll would have taken you to [**this**](ghelp:administrative):> In Ubuntu, for security reasons, administrative tasks are confined to users with special privileges. Administrative access is given to individual users, who may use the sudo command to perform administrative tasks. The first user account you created on your system during installation will, by default, have access to sudoand many more!

The problem is your not **trying**.

---

### Post by tgm4883 on 2007-07-26
> **por100pre1 said:**
> In that post you used the words I *really* wanted to use... **yes, Linux is better than Windows** ;).

In what way?

---

### Post by phr0ze on 2007-07-26
> **Old Pink said:**
> To be honest, I don't think you have enough common sense for Linux. I mean, something asks you for your password, and you've only set one since setup, what's it going to be?

And a google search for "what's the sudo password?" then tells you, without even clicking: "[SIZE=-1]Therefore it sets the **sudo password** to be the same as that user's **password**"As for the hda/sda thing you complained about, a quick google for "difference between hda sda" quickly provides us with "[/SIZE]HD - denotes that the disk drive is IDE based and  if the drive SCSI or SATA based it will be designated as SD."

Installing Windows takes more knowledge than installing Linux, Windows still has a text based interface, most Linux desktops give you a full on LiveCD with firefox and web access to find any answer, as well as System > Help and Support which would've given you many of your answers.

For example. When trying to find out your password, you could've hit System, then Help and Support, and typed in password. A quick scroll would have taken you to [**this**](ghelp:administrative):and many more!

The problem is your not **trying**.


I agree with some of this. I don't want to be hard on the guy, but if something asked me for the password, I'd try the password I used to log in. Also OP seems to be trolling. Most people complain about a lack of games in linux and this guy complains that all we do on the system is play games and not work. bleh. Personally I would not remove the games even if I don't want them.

---

### Post by por100pre1 on 2007-07-26
> **tgm4883 said:**
> In what way?

Is this some kind of test? I have found it more secure, more efficient, and more fun to use... oh well, that's just my humble opinion. Are you trying to convince me otherwise? :)

---

### Post by xpod on 2007-07-26
> Is this some kind of test? I have found it more secure, more efficient, and more fun to use... oh well, that's just my humble opinion. Are you trying to convince me otherwise? 

Have you been peeking at my test paper by any chance as i have the exact same answers as you do :wink:

---

### Post by por100pre1 on 2007-07-26
> **xpod said:**
> Have you been peeking at my test paper by any chance as i have the exact same answers as you do :wink:

I'm not cheating!!! I'm not cheating!!! :lolflag:

---

### Post by tgm4883 on 2007-07-26
> **por100pre1 said:**
> Is this some kind of test? I have found it more secure, more efficient, and more fun to use... oh well, that's just my humble opinion. Are you trying to convince me otherwise? :)

Am I trying to convince you that Windows is better than Linux?  No.  Am I trying to convince you that Linux is better than Windows?  No.  There are different, each suited for different audiences, but both have the same function.


But what I really really want to know is how you cannot compare Windows and Linux, yet say that Linux is better than Windows.  That in itself is a contradiction.  Either Linux is to Windows as an Apple is to an Mango, or Linux is to Windows as an Apple is to a swimming pool.  Can't be both

---

### Post by Permanent Beginner on 2007-07-26
I wonder how this helpful forum turned mean?  Is it after work and the beers are coming out?

"I don't think what you've experienced can be considered "typical". And why are you trying to uninstall a bunch of stuff anyway? Some special intended use? It's not that bloated in standard form."

I am an old-fashioned American.  I want what I want and I don't want to be stepping over anything that I don't need, like game folders or office suites.  And if the screen and the instructions say different things, what does that mean?  Back in Windows3 it meant "touch one key and I'll blow up your computer".

**
"To be honest, I don't think you have enough common sense for Linux. 

This is certainly true, in the context of what computer operators call "common".  But every day I try to do things that I can't do, the large volume of which keeps me busy indeed.

**
"I mean, something asks you for your password, and you've only set one since setup, what's it going to be?"

I think it asked for an Admin password and I know nobody ever called me Admin.  You mean putting in somebody else's name is common sense?

**
"And a google search for "what's the sudo password?" then tells you, without even clicking: "Therefore it sets the sudo password to be the same as that user's password""

Who would look for the particular combination of words,  "sudo password?", except by chance?

**
"As for the hda/sda thing you complained about, a quick google for "difference between hda sda" quickly provides us with "HD - denotes that the disk drive is IDE based and if the drive SCSI or SATA based it will be designated as SD."

And since I had an SCSI Zip drive in there I thought it wanted to try to install to that.

**
"complained", "complaining"

Say what?  Oh, complaining?


I thought this issue was closed in messages 20 and 34 where I took my info and said thanks...Probably what I need to do is write a log of all the things that my mind interpreted differently from yours and hang it somewhere for the assistance of similarly-wired people.  You hear about 15-year-old kids who never have to read a manual...I'm on the other end of that spectrum...


Bless you all,

PB

---

### Post by buzzmandt on 2007-07-26
excellent response pb, i thought the thread had taken a distinctive ugly turn myself.....

"the only dumb question is the one you don't ask"

I've used linux for many years before ubuntu, it was mandriva...when i tried ubuntu i had no idea what sudo was and tried all the admin rights stuff with su, didn't take long to figure it out, but i had prior linux experience.  First time i tried linux at all, took me a while to know what su was

Beginners and new users shouldn't be led to feel stupid, let alone be called stupid.  Uninformed or lacking knowledge in something does not make someone stupid.  I've used linux for many years, only recently after finding ubuntu is it my main os and i still consider myself a beginner.

and by the way, welcome to the boards and ubuntu

---

### Post by Old Pink on 2007-07-26
> **Permanent Beginner said:**
>  
**
"And a google search for "what's the sudo password?" then tells you, without even clicking: "Therefore it sets the sudo password to be the same as that user's password""

Who would look for the particular combination of words,  "sudo password?", except by chance?


The use of the combination of words "sudo password" has been noted by Google over [SIZE=-1]**2,150,000 **times, with [/SIZE][SIZE=-1]**1,690,000 **of these being Ubuntu related and [/SIZE][SIZE=-1]**230,000 **from this forum alone. [/SIZE]

---

