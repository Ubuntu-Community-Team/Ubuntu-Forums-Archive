---
title: "Perspective from a Windows User"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-09
I have been messing around with Ubuntu recently.  This is my first delve into the world of Linux. I am not versed in Linux and until the last 2 weeks could not even tell someone what Linux is.  Therefore I am the tried and true Windows user.  I started using Windows just after Win 95 came out so I never really even worked with DOS.  I am the definition of "user".  So here is my main observation.

Windows users looking for an alternative are generally going to be uncomfortable with typing ANY sort of code.  I am.  In the world of Windows everything is done through a graphical interface.  We build web pages, SQL databases, install and uninstall programs, drivers, and manage our hard drives through the Windows GUI. 

The graphical interface is the thing that Windows does best.  Ubuntu (and I am sure many other Linux OS's) is very close to providing a true alternative for numbskulls like myself.  One thing that I have found myself doing a lot of recently is poring over the web forums looking for Terminal Command Lines that will mount drives and partitions, install programs, or load drivers.

So if there was one thing that Linux developers could do to ease the transition for folks like myself, it would be to expand on GUI Interfaces for these processes.

Just an observation.  I am pretty excited here and learning more every day.

Thanks all,

Wood

---

### Post by Brunellus on 2006-03-09
a lot of the help we dish out here on the forums is command-line based, because it is easier for us to know that they will be followed explicitly and without deviation.

It's a lot easier to tell someone to paste a series of commands into a terminal than to have to walk them through a GUI method.  Not only is walking someone through the gui more time-consuming, but ambiguities and so forth in description may result in mistakes.  If you're mucking about as root, graphically, and you don't know what you're doing, you could do some serious harm to your OS. 

If you're at all interested in how and why the command line is what it is, I recommend that you read this excellent essay:

[http://folk.ntnu.no/shane/dokumentasjon/commandline.html](http://folk.ntnu.no/shane/dokumentasjon/commandline.html)

Not technical, more historical.

As for me, I grew up on DOS 3.3, so Linux/Unix gives me back the commandline that I have been missing...and a more powerful one at that.

---

### Post by el3ktro on 2006-03-09
Well, thats the Linux way of doing things ;-)

Honestly, I also really had to learn a lot when I switched to Linux. At first I thought Linux would just be Windows with a different name - but it's not. Linux is different. It has a different philosophy, many different concepts and a different technology "under the hood". But this is for good purpose.

When it comes to doing things on the command line: When you really try to learn Linux, try out Gentoo for a while. EVERYTHING is done on the command line there, you have to do everything for yourself to get the system up & running.  After this experiecnce - believe me - you never want to miss the Bash again! It's so damn powerful. If you know your Bash well, you can do things often faster & more comfortable than if you had a GUI.


Tom

---

### Post by mlind on 2006-03-09
One thing I miss from windows desktop is drag-and-drop features that nowdays
seem to work quite well on Gnome. Few years back it was really different.

More well designed graphical tools are available for tasks that you could only
do in terminal session. I'm not fan of GTK toolkit, and I feel windows still has more
professional look&feel, but my attitude is changing every moment.

It's great to see linux desktop going to way that normal users like myself
find themselves comfortable and do not miss going back to windows desktop.

---

### Post by John.Michael.Kane on 2006-03-09
WoodyMahan this should help..
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)

---

### Post by trorion on 2006-03-09
[QUOTE=WoodyMahan]In the world of Windows everything is done through a graphical interface.  We build web pages, SQL databases, install and uninstall programs, drivers, and manage our hard drives through the Windows GUI. 

...

So if there was one thing that Linux developers could do to ease the transition for folks like myself, it would be to expand on GUI Interfaces for these processes.[/QUOTE]

I have set up web pages, databases, and what not in windows (windows user new to linux here so it's not a matter of 'I was trained in linux so used a command prompt in windows') and I never used a GUI for them because the GUI programs made it so slow and pre-fabricated that they were attrocious.  If you go back to windows after 6 months on linux and set up a database on a gui you'll understand. 

As for expanding the GUI Interfaces...what is it in linux that you haven't found on a gui interface?  The reason that you see so much terminal code on the linux forums is because it's more efficient and faster than a GUI.  I'd be happy though to help you find the GUI programs to do whatever you are doing though.

There are some things that linux could make more familiar and easy.  One of them that I would love to see would be an automatic launcher for dpkg when you double click on a .deb package that you have downloaded.

---

### Post by mcduck on 2006-03-09
As already said, there are GUI's for mounting, installing programs and many other tasks. But giving instructions how to do things with GUI is harder, and depends on how you have set your desktop and what language you are using.

For example, I can guide someone to install program called ImageMagic in two ways:

GUI:
1. Open System menu, and select 'Administration' and then 'Synaptic Package Manager'. Enter your password.

2. Click 'reload'.

3. Click 'search' and type 'imagemagic' (you must have set 'look at' to either 'name' or 'name and description').

4. Now right-click the package Synaptic found, and select 'Mark for installation'.

5.Then click 'Apply' and wait while Synaptic downloads and installs ImageMagick.

(Giving this instruction required me to do all those things to make sure I remember every step, and even then it wouldn't work if you had replaced your menubar with a single menu, you used any other language or you used KDE or some other desktop enviroment.)

CLI:
1. copy 'sudo apt-get update && sudo apt-get install imagemagic' to terminal, press enter and give your password.

(this is so simple that I didn't need to check it anywhere. And it works always. Whatever DE or language you use. And you only need to copy/paste it instead of following my complex and badly writen GUI instructions)

---

### Post by Pragmatist on 2006-03-09
First of all, I think many of the points made here are excellent.  I've used Linux for several years and exclusively for two years.  I can easily name one hundred good reasons, just off the top of my head, to use Linux instead of Windows.  However, for me, the main advantage of Linux is its **flexibility**.  In a great deal of computer technologies, throughout the history of the computer, there is a trade off between flexibility and complexity.  Obvious examples include TiVo, Stereos equipment, calculators,  in short, anything that has a computer embedded in it.  In many of these you can only use the functions that it's pre-programmed for.  Although even here you see the idea; you can buy a stereo or tv that has few options and is easy to use, or you can buy one that has lots of options, can connect to other devices with lots of options, and has much more complexity and is therefore harder to learn.  Computer languages follow the same pattern. HTML is a subset of SGML and it was created because using a fixed set of 100 tags is easier than using everything; or XML where you define your own tags--more options/flexibility, more complexity and harder to learn.

The computer was created as an "all-purpose" machine.  That *IS* the definition of a computer.  So, my view, from a theoretical standpoint too, is that Linux is the "best" OS in that it maximizes flexibility and choice which are the essence of what a computer is.  Windows, on the contrary, not only makes a huge number of choices for you, they drastically limit your ability to make your own choices. 

However, the bottom line, that I tell friends when they are considering switching to Linux, is: **Are you the kind of person that is an "active" computer user. ** By "active" I mean do you like to tweak your system, get things just the way you like it, have options and make changes when it is to your benefit, and so on.  The opposite of "active" is somebody who just wants their computer to do what they want with the least amount of absolute effort and are willing to pay the price in speed or other specific advantages. There is nothing wrong with this.  It is a personal choice.  In fact, if the Window's defaults are perfect for what they do the smartest choice might be to continue using Windows.  Of course, this assumes they don't mind taking the hit in speed, cost, security, etc...  Many of the people I know, say things like, "yeah, but I don't need those options, so why should I bother learning Linux"  They are right!

I know that Ubuntu is catering to the masses and trying to make it easier for Windows users to switch to Linux.  However, in my opinion, the key is not how much we can make Linux like Windows.  The key is **how we can convert "non-active" computer users to "active" ones.**  "active" computer users that use Windows will come over to Linux eventually if they are smart.  It is converting the "non-active" users that is most difficult.  The reason is, as most computer gurus will be the first one to tell you, is that there is **nothing wrong with being a  "non-active" user** if that is consistent with your priorities and needs.

---

### Post by WoodyMahan on 2006-03-09
All great points, and I am getting there.  Of course after using a system for a certain amount of time (like Windows) certain things become intuitive simply due to experience.  I already feel like I am making progress.  I certainly wouldn't want Ubuntu or any other Linux OS to become a carbon copy of Windows, but we are all creatures of habit, so I find myself thinking "If I right click on it then there should be some options...." etc.  This is turning out to be a fun exploration.  I was having some trouble getting a secondary hard drive to mount and spent a couple of hours of research and conversation, but when I fired it up and found my Storage space and could actually work with....Well, not better than sex, but very gratifying.

---

### Post by az on 2006-03-09
If you look at the ubuntu goals, there is an ongoing goal to eliminate the need for the command line by identifying and providing a gui for such tasks.

It *is* getting better and better.

The reason why it is not already done is because there are a lot of poeple who are completely happy with the command line.  This does not translate into all users being forced into using it.
Well, not forever...

---

### Post by Pragmatist on 2006-03-09
> eliminate the need for the command line by identifying and providing a gui for such tasks.  Do you mean they are going to make GUI applications for every possible thing you would want to do with a command-line? :)

---

### Post by Brunellus on 2006-03-09
I'd hate to see what the gui for ```
cat
``` will look like.  Or how they do pipes and redirects.  :)

---

### Post by brooklynlou on 2006-03-09
****[QUOTE=Pragmatist]I know that Ubuntu is catering to the masses and trying to make it easier for Windows users to switch to Linux.  However, in my opinion, the key is not how much we can make Linux like Windows.  The key is **how we can convert "non-active" computer users to "active" ones.**  "active" computer users that use Windows will come over to Linux eventually if they are smart.  It is converting the "non-active" users that is most difficult.  The reason is, as most computer gurus will be the first one to tell you, is that there is **nothing wrong with being a  "non-active" user** if that is consistent with your priorities and needs.[/QUOTE]

About Me:
- I did my first install of Linux (Ubuntu obviously) last night on an old laptop
- I have no idea about Linux other than muddling through the Ubunt help site
- I teach people how to use software for a living at a large law firm. 

The vast majority of people do not want to be "active users". The computer to them is a tool that allows them to perform their job. They want to learn only as much as they need to know in order to safely operate that tool. When the tool stops working or misbehaves, they experience a moment of unease and panic at what is in effect their own feelings of helplessness in trying to get this tool to work. If their company has a IT staff that can adequately support them, they call on them. If not, they curse the machine and try to soldier on. Very rarely will a typical user dive into a manual.

This is the case for two main reasons (IMHO): 

1 - they are busy and want something that 'works'. Example "I am a corporate lawyer that bills $500 an hour. Every hour that this machine is not working costs me $500. Fix this machine."

2 - they do not look at knowing how the computer is actually doing its job as knowledge that they necessarily need to have. "My job is X, knowing how to fix this is Y. Its not my job to know X and Y. If it is, pay me more."

Hate to make it sound like a class based argument, but the 'Active' users will come over to Linux out of curiosity. If the package intrigues them, they might stay. The 'Non-active' users will work with what ever they are given. If you want Linux to get used, you need to convince the people that buy the software on a corporate level that Linux will:

a - do the work that they need done
b - can be fixed quickly if the xxxx hits the fan. 
c - will not take forever to train the staff how to use (making it look like Windows helps)
d - allow you to find people that know its ina and outs and easily replace them if needed. I do not want the company's IT infrastructure held hostage by a small group of people.
e - its so much cheaper than windows that it will quiet any fears about a,b,c and d.

Till the above happens, either by a entity distributing a flavor of Linux (Redhat, Ubunto, etc) Linux will not be a success on the mass market.

---

### Post by Brunellus on 2006-03-09
IBM may be moving to an all-Linux desktop soon (internally), as will other large corporations.  This kind of movement will generate the momentum your'e looking for.

And yes, brooklynlou, you are correct.   Add to the fact that many of the attorneys I work for (I also work at a law firm) are bloody well computer-illiterate (they dictate faxes in response to e-mails, for instance).  I don't see them moving to Linux on their own unless the firm standardizes on it.

---

### Post by cotcot on 2006-03-09
Quite a lot of things can be done by GUI in linux. But the forum shows that many users see more comfort in command line. Coming from windows after I got a little bit used to the command line i appreciated that command line tells you what is going wrong when you do not achieve a goal.

---

### Post by Perfect Storm on 2006-03-09
[QUOTE=trorion]
There are some things that linux could make more familiar and easy.  One of them that I would love to see would be an automatic launcher for dpkg when you double click on a .deb package that you have downloaded.[/QUOTE]

I recall that it will be avaible in the next release of ubuntu, Dapper.
Can a Dapper user apply if it's true?

---

### Post by Brunellus on 2006-03-09
[QUOTE=cotcot]Quite a lot of things can be done by GUI in linux. But the forum shows that many users see more comfort in command line. Coming from windows after I got a little bit used to the command line i appreciated that command line tells you what is going wrong when you do not achieve a goal.[/QUOTE]
as I said before, it isn't a question of "comfort" as much as a question of *expediency*.  properly-formed shell commands, copied and pasted, cannot be misinterpreted. 

The speed of working in the shell also lets us answer a lot of questions quickly.

---

### Post by kaamos on 2006-03-09
> 
I recall that it will be avaible in the next release of ubuntu, Dapper.
Yep. [https://lists.ubuntu.com/archives/ubuntu-devel/2005-November/013048.html](https://lists.ubuntu.com/archives/ubuntu-devel/2005-November/013048.html)

---

### Post by WoodyMahan on 2006-03-09
OK then I have another question.  Can I upgrade my current Breezy install to a new release seemlessly or will I have to wipe and start over again?

---

### Post by kaamos on 2006-03-09
Yes you can. It is just a matter of changing the repositories in synaptic from "breezy" to "dapper" and updating (dist-upgrade). To upgrade to dapper+1 you won't probably have to do even that since the process is planned to be added to the update manager.

---

### Post by brooklynlou on 2006-03-09
[QUOTE=Brunellus]IBM may be moving to an all-Linux desktop soon (internally), as will other large corporations.  This kind of movement will generate the momentum your'e looking for.

And yes, brooklynlou, you are correct.   Add to the fact that many of the attorneys I work for (I also work at a law firm) are bloody well computer-illiterate (they dictate faxes in response to e-mails, for instance).  I don't see them moving to Linux on their own unless the firm standardizes on it.[/QUOTE]

The fact that things in Linux get 'fixed' with a command line will not phase users one bit. If you tell someone that they can type a string into a window and your problems would be fixed, they'd love it. No muss, no fuss, no thought. As long as someone exists in the organization that knows those magic strings, everyone would be happy. Having a GUI for this is less important than having a repository of those strings. If X doesn't work, type this

Large law firms will be the LAST industry that moves to Linux because the OS is really not that important to them. What is important is the Word Processing program. Law firms are document factories. Until Word get dethroned (or something comes out that matches its features - Hint Open Office does not match features) Windows stays. I hate to say that the best way to get Linux in the corporate world is to create a better Office suite.

---

### Post by Pragmatist on 2006-03-09
> Originally Posted by:** brooklynlou** If you want Linux to get used, you need to convince the people that buy the software on a corporate level that Linux...
 I agree 100%  I was strictly talking about home users.  Making retraining easier would increase corporate adoption, but corporate adoption is not where the tough battle is at.  The real numbers are with home users.  However, you are right, if we make a Windows clone that doesn't cost anything, and is as easy to use as MS Windows, everybody will want it.  And, they will have a new and improved windows, which is good for them.  This would be just another distribution and wouldl have limitations just like any other distribution.  Any full committment to one set of programs, GUI environment, philosophy, etc... by definition precludes the others.  The real power comes when you** committ to the idea of flexibility**.  The flexible user can choose Ubuntu, or the Windows clone (if that ever happens), or MAC OS X, or hundreds of others.  They can choose them based on **what is best for them at that time.**  That is an "active" user.  Computer education and experience begins at home and corporations, just like individuals, if they want the philophy of flexibility, require a steeper learning curve.

---

### Post by Karisson on 2006-03-09
I'm in pretty much the same situation as you. Having been using the Windows GUI exclusively for almost 10 years, I'm extremely comfortable with it, and can do anything I need with it. Switching to Linux on one of my computers has been a big challenge for me. As you mentioned, I'm extremely uncomfortable with the command line, and I'm still having trouble getting a lot of drivers working. I like it though, and it's been a good experience for me. I've learned a lot.

[QUOTE=WoodyMahan]I have been messing around with Ubuntu recently.  This is my first delve into the world of Linux. I am not versed in Linux and until the last 2 weeks could not even tell someone what Linux is.  Therefore I am the tried and true Windows user.  I started using Windows just after Win 95 came out so I never really even worked with DOS.  I am the definition of "user".  So here is my main observation.

Windows users looking for an alternative are generally going to be uncomfortable with typing ANY sort of code.  I am.  In the world of Windows everything is done through a graphical interface.  We build web pages, SQL databases, install and uninstall programs, drivers, and manage our hard drives through the Windows GUI. 

The graphical interface is the thing that Windows does best.  Ubuntu (and I am sure many other Linux OS's) is very close to providing a true alternative for numbskulls like myself.  One thing that I have found myself doing a lot of recently is poring over the web forums looking for Terminal Command Lines that will mount drives and partitions, install programs, or load drivers.

So if there was one thing that Linux developers could do to ease the transition for folks like myself, it would be to expand on GUI Interfaces for these processes.

Just an observation.  I am pretty excited here and learning more every day.

Thanks all,

Wood[/QUOTE]

---

### Post by Brunellus on 2006-03-09
[QUOTE=brooklynlou]The fact that things in Linux get 'fixed' with a command line will not phase users one bit. If you tell someone that they can type a string into a window and your problems would be fixed, they'd love it. No muss, no fuss, no thought. As long as someone exists in the organization that knows those magic strings, everyone would be happy. Having a GUI for this is less important than having a repository of those strings. If X doesn't work, type this

Large law firms will be the LAST industry that moves to Linux because the OS is really not that important to them. What is important is the Word Processing program. Law firms are document factories. Until Word get dethroned (or something comes out that matches its features - Hint Open Office does not match features) Windows stays. I hate to say that the best way to get Linux in the corporate world is to create a better Office suite.[/QUOTE]
Frankly, I'm a bit annoyed with Word for typing pleadings and other legal documents.  It gets pretty unstable with really large docs....

If I had my druthers, I'd really much rather use [LyX](http://www.lyx.org), which is much nicer and offers much finer-grained support for things like tables of authorities and so forth.  It's not ready for prime-time yet, though--LyX and its underlying elements TeX and LaTeX have so far been the preserve of scientific/mathematical/engineering types, and will need some small modifications for legal use:

* Styles and templates for legal documents

* Bibliographies that Bluebook more nicely 

* An easier way of setting up version/revision control (currently, they use CVS, which is very powerful)

The first two are relatively trivial (in fact, I intend to work on them as a side-project), but the latter....  *shrug*

---

### Post by gigi1234 on 2006-03-09
This is my perspective as a relatively new Linux user:

I just spent three days at work recovering from a devastating virus attack that overwrote ALL my data files with pure gibberish. 

The little bit of initial time users must spend to get with the LINUX way of doing things is minor in comparison to the time Windows users spend thwarting and recovering from virus threats. 

LINUX rules (Ubuntu in particular)...enough said!

---

### Post by WoodyMahan on 2006-03-09
My personal belief on the whole virus thing is that those people trying to attack Windows would very quickly turn their vicious intentions to Linux if that would affect the most people.  They suck, but as the Linux community grows, they will be coming.  Is there anywhere we can go to see a list of known viruses for Linux OS?  Surely, we aren't completely free of bad guys here.

---

### Post by WoodyMahan on 2006-03-09
[QUOTE=SD-Plissken]WoodyMahan this should help..
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)[/QUOTE]


By the way, I have been looking at some of these resources.  Any Windows users out there interested in getting ahead shoud really check these out.  Thanks SD

---

### Post by brooklynlou on 2006-03-09
[QUOTE=Brunellus]Frankly, I'm a bit annoyed with Word for typing pleadings and other legal documents.  It gets pretty unstable with really large docs....

If I had my druthers, I'd really much rather use [LyX](http://www.lyx.org), which is much nicer and offers much finer-grained support for things like tables of authorities and so forth.  It's not ready for prime-time yet, though--LyX and its underlying elements TeX and LaTeX have so far been the preserve of scientific/mathematical/engineering types, and will need some small modifications for legal use:

* Styles and templates for legal documents

* Bibliographies that Bluebook more nicely 

* An easier way of setting up version/revision control (currently, they use CVS, which is very powerful)

The first two are relatively trivial (in fact, I intend to work on them as a side-project), but the latter....  *shrug*[/QUOTE]


The big secret to Word is that it is entirely style driven. Don't use style, docs blow up. We spend days training secretaries how to properly style documents. If you think we have it bad, talk to someone working in the pharmacutical industry. Their docs reach the thousands of pages rather than the hundred.

The only thing that ticked me off about Open Office is how little there is out there about the bad of the program. How is a document supposed to be done? How does OO store codes? How it handle complex paragraph numbering? 

I hate to say it, but Office is the killer app for Windows. What a OS, its a tool that gets you quickly to you applications and lets you manage your files. one OS is as good as another to most users. Its the available applications that will push people to Linux, not Linux itself.

---

### Post by Brunellus on 2006-03-09
[QUOTE=brooklynlou]The big secret to Word is that it is entirely style driven. Don't use style, docs blow up. We spend days training secretaries how to properly style documents. If you think we have it bad, talk to someone working in the pharmacutical industry. Their docs reach the thousands of pages rather than the hundred.

The only thing that ticked me off about Open Office is how little there is out there about the bad of the program. How is a document supposed to be done? How does OO store codes? How it handle complex paragraph numbering? 

I hate to say it, but Office is the killer app for Windows. What a OS, its a tool that gets you quickly to you applications and lets you manage your files. one OS is as good as another to most users. Its the available applications that will push people to Linux, not Linux itself.[/QUOTE]
agreed, on almost all points.

I haven't tried OOo on a complex legal document yet, but I can say that it does have a very good way of dealing with styles.  

What I think is amusing is that in pharma, you have scientists writing in LaTeX--which then gets published, and then re-done for corporate hacks working in Word.

---

### Post by az on 2006-03-09
[QUOTE=WoodyMahan]My personal belief on the whole virus thing is that those people trying to attack Windows would very quickly turn their vicious intentions to Linux if that would affect the most people.  They suck, but as the Linux community grows, they will be coming.  Is there anywhere we can go to see a list of known viruses for Linux OS?  Surely, we aren't completely free of bad guys here.[/QUOTE]

I think the security threats we will face are not the same kind as for Windows.  We are an open souce OS with centralised repositories.  Viruses are not the only threats out there - but that's why we have security updates...

Also:
"Pragmatist 
Do you mean they are going to make GUI applications for every possible thing you would want to do with a command-line? "

No, just the most common ones.  Not such a big task when you realise that Ubuntu main only contains a small subset of all the package there are out there.  It's not as big a deal as you could imagine, to only have to support those packages and associated tasks.
 
This is an old page.  I cannot find the equivalent one for UBZ (UBZ came after UDU)  It must be a task on launchpad.
[https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/CommandLineDisintegration](https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/CommandLineDisintegration)

---

### Post by Brunellus on 2006-03-09
[QUOTE=WoodyMahan]My personal belief on the whole virus thing is that those people trying to attack Windows would very quickly turn their vicious intentions to Linux if that would affect the most people.  They suck, but as the Linux community grows, they will be coming.  Is there anywhere we can go to see a list of known viruses for Linux OS?  Surely, we aren't completely free of bad guys here.[/QUOTE]
[http://linuxmafia.com/~rick/faq/index.php?page=virus#virus](http://linuxmafia.com/~rick/faq/index.php?page=virus#virus)

that's a pretty good treatment of the subject there.  Somewhat out of date (written in 2004), but quite good on the structural reasons why Linux and the various UNIX-es are much safter by design than Windows.  

Lesson:  DON'T RUN AS ROOT BY DEFAULT.  This is why everybody hates Linspire...but that's another question.

---

### Post by az on 2006-03-09
[QUOTE=Brunellus]I haven't tried OOo on a complex legal document yet, but I can say that it does have a very good way of dealing with styles.  

[/QUOTE]

Doesn't word implement scripting in a way that prevents really complex documents (like those in publishing and in big law firms) from being able to be properly rendered in Open Source software?  I think publishing houses rely heavily on templates which use these scripts.

---

### Post by Brunellus on 2006-03-09
[QUOTE=azz]Doesn't word implement scripting in a way that prevents really complex documents (like those in publishing and in big law firms) from being able to be properly rendered in Open Source software?  I think publishing houses rely heavily on templates which use these scripts.[/QUOTE]
sounds like a nefarious plot to me.  I'd need to see some documentation of this.

---

### Post by brooklynlou on 2006-03-09
[QUOTE=azz]Doesn't word implement scripting in a way that prevents really complex documents (like those in publishing and in big law firms) from being able to be properly rendered in Open Source software?  I think publishing houses rely heavily on templates which use these scripts.[/QUOTE]

Azz, I'm new to Linux, but I've been playing with OO for windows for a month now. Personally, I'm not at the stage where I'm even worrying if OO and MSWord can understand each other or what templates need to be developed. I'm trying to see if OO can make a legal document look right the way WordPerfect and Word can. So far, I'm not too enthused with the results. 

On a side note - once the new version of office comes out with the new file format, companies are going to have this small window of opportunity with which to switch over. Once it passes and the docs in their system are converted over to the new format, they'll be married to MS for years to come. MS will never create a version of office for Linux. The only way out is if a open source suite comes out using the same file structure as MS. I keep reading in the OO forums how they need to add / fix features, when the truth of the matter is that its all moot unless they mimic the file structure.

---

### Post by m.musashi on 2006-03-09
[QUOTE=brooklynlou]On a side note - once the new version of office comes out with the new file format, companies are going to have this small window of opportunity with which to switch over.[/QUOTE]
I thought XML or something was supposed to become some kind of open standard. Is MS not going to adopt it? If they don't play nice, more and more people are going to leave.

---

### Post by Brunellus on 2006-03-09
[QUOTE=m.musashi]I thought XML or something was supposed to become some kind of open standard. Is MS not going to adopt it? If they don't play nice, more and more people are going to leave.[/QUOTE]
they are under no obligation to play nice when they own the market.  why would anyone leave?

---

### Post by kaamos on 2006-03-09
I could not find a link right now, but I remember some US state was banning ms office from their public offices because there is a law about the use of open formats.

Got to keep digging..

---

### Post by Brunellus on 2006-03-09
[QUOTE=kaamos]I could not find a link right now, but I remember some US state was banning ms office from their public offices because there is a law about the use of open formats.

Got to keep digging..[/QUOTE]
that's Massachusetts, and the regulation would mandate open-document formats, not necessarily a non-Microsoft solution (although it seems that this will be the case).  

All it would take for MS to be in compliance would be to relase a patch that allowed its software to read and write .odt documents.

---

### Post by brooklynlou on 2006-03-09
[QUOTE=m.musashi]I thought XML or something was supposed to become some kind of open standard. Is MS not going to adopt it? If they don't play nice, more and more people are going to leave.[/QUOTE]

Its XML. The pieces of the doc (from what I gather) are kept in seperate XML files that are then put in a zip file container that is given the extention .xdoc. I'm still waiting to get my hands on a beta of the new office to see how they pull it off.

---

### Post by m.musashi on 2006-03-09
[QUOTE=Brunellus]they are under no obligation to play nice when they own the market.  why would anyone leave?[/QUOTE]
Isn't owning the market what has gotten them in anti-trust trouble? It's when you own the market that you need to play nice. No one likes a dictator. Why would anyone leave? Again, look at the history of dictators. Perhaps the comparison is a bit too much but I think you can see the point.

---

### Post by Brunellus on 2006-03-09
[QUOTE=m.musashi]Isn't owning the market what has gotten them in anti-trust trouble? It's when you own the market that you need to play nice. No one likes a dictator. Why would anyone leave? Again, look at the history of dictators. Perhaps the comparison is a bit too much but I think you can see the point.[/QUOTE]
owning the market is not what got them into trouble.  

Using that ownership in one market (operating systems) to compel the creation of *another* monopoly (applications software) was what got them into trouble.

---

### Post by m.musashi on 2006-03-09
[QUOTE=Brunellus]owning the market is not what got them into trouble.  

Using that ownership in one market (operating systems) to compel the creation of *another* monopoly (applications software) was what got them into trouble.[/QUOTE]
Well, I'm no lawyer but I still think that owning the market implies a need for a certain amount of benevolence. Didn't Uncle Ben (Spiderman) say "with great power comes great responsibility"? If MS continues to expect the world to bend to its will then I think their days are numbered - at least as THE standard. Let's see where they are in 10 years. If they still command 95% of the market then I will eat crow. However, I'm betting it will be closer to 50%.

---

### Post by Brunellus on 2006-03-09
I have begun to think of the software industry as less Spiderman than *The Peloponnesian Wars*

In a famous passage, Thucydides has the Athenian envoys to the city of Melos speak frankly:

> 
since you know as well as we do that right, as the world goes, is only in question between equals in power, while the strong do what they canand the weak suffer what they must..

Microsoft are strong;  they do as they will, and their competitors suffer as they must....unless they have other means of righting the balance.  Microsoft owes nothing to their competitors.

---

### Post by m.musashi on 2006-03-09
[QUOTE=Brunellus]I have begun to think of the software industry as less Spiderman than *The Peloponnesian Wars*

In a famous passage, Thucydides has the Athenian envoys to the city of Melos speak frankly:

.

Microsoft are strong;  they do as they will, and their competitors suffer as they must....unless they have other means of righting the balance.  Microsoft owes nothing to their competitors.[/QUOTE]
Point taken but I was thinking more of the users than the competition. Good leaders take care of their subjects. As leaders of the OS and Office software world, they should focus on taking care of their subjects. By this I mean not setting up systems that decrease usability. This was my original point. It isn't right, from a users point of view, for MS to create a closed standard that limits users functionality. Of course if you choose to only use MS products then that's fine, but if you are more or less forced to use MS products then that isn't. As diversity creeps in (more linux and mac os users) more and more people are going to want open standards. If MS resists that then they will breed resentment and resentment leads to revolt. Shouldn't I be able to work on a document at home on linux and then take it to work and finish it in MS Office? I can do that now without too much problem but if MS seeks to decrease what usability I have then that's where I see the problem.

---

### Post by Brunellus on 2006-03-10
[QUOTE=m.musashi]Point taken but I was thinking more of the users than the competition. Good leaders take care of their subjects. As leaders of the OS and Office software world, they should focus on taking care of their subjects. By this I mean not setting up systems that decrease usability. This was my original point. It isn't right, from a users point of view, for MS to create a closed standard that limits users functionality. Of course if you choose to only use MS products then that's fine, but if you are more or less forced to use MS products then that isn't. As diversity creeps in (more linux and mac os users) more and more people are going to want open standards. If MS resists that then they will breed resentment and resentment leads to revolt. Shouldn't I be able to work on a document at home on linux and then take it to work and finish it in MS Office? I can do that now without too much problem but if MS seeks to decrease what usability I have then that's where I see the problem.[/QUOTE]
wishful thinking at best.  they have zero incentive to be better--they are already number 1.

---

### Post by nocturn on 2006-03-10
Just a quick note on this.  

Although many and even most things now can be done via a GUI in Linux too,  there are many cases in which a command is easier to pass.

I can tell you in one or two lines how to set up some complex things on your box that would grow to a long and complicated post when I have to explain how to do this in a GUI.

For a lot of things, there is the added argument that I don't know the GUI tools myself since I do most configuration stuff on the command line myself (a lot of power users do).

Over my 9 years with Linux/Unix, I've learned that a CLI (Command Line Interface) can handle such complex tasks that it is impossible to write a GUI that is equally flexible.

---

### Post by nocturn on 2006-03-10
[QUOTE=WoodyMahan]My personal belief on the whole virus thing is that those people trying to attack Windows would very quickly turn their vicious intentions to Linux if that would affect the most people.  They suck, but as the Linux community grows, they will be coming.  Is there anywhere we can go to see a list of known viruses for Linux OS?  Surely, we aren't completely free of bad guys here.[/QUOTE]

We're not completely safe, and it would be arrogant to think we'd ever be.
But Linux has many more and better security layers than Windows (and things are still getting better).  Designing a virus will always be possible for any OS, but the higher we put the bar in terms of who is able to do it, the better off we will be.

In addition, Linux has many different distributions, which is actually a strength in security.  Malware targetting one distro might not work on any or all others.

---

