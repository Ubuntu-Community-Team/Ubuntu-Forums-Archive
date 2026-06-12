---
title: "Any movement to eliminate the need for a command line"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by nameiwantistaken on 2006-06-28
I'm wondering if there is any movement with Ubuntu to remove the need to use a command line to anything.  This would include updating source lists, using apt-get, installing drivers, compiling the kernel, etc.  Getting the application installed is easy now, but once you get to that point things become very difficult.  What is stopping this OS from getting to the next level in terms of its goal of being suitable for desktop is the reliance on the command line.  No other successful desktop OS requires a user to learn commands to interact with the kernel to do pretty much anything.  I don't think an OS can be considered a desktop option until this is gone.  Any developers out there have any input on this?

---

### Post by matthew on 2006-06-28
Please...no flames. The guy is probably serious.

The command line is one of the most powerful and user-friendly ways to do things in the unix/linux/bsd world. Once you have learned it even a little bit you will never stand for anyone taking it away from you.

Yeah, there are new GUI's all the time in the Linux world, most of which are great. They will never replace the functionality of the command line.

I expect aysiu or someone else to step in here momentarily and explain further. Hey, aysiu? Where's that link of yours??

EDIT: nevermind...I found it. Please read this: [http://www.ubuntuforums.org/showthread.php?t=59334]("http://www.ubuntuforums.org/showthread.php?t=59334")

---

### Post by johnc4510 on 2006-06-28
Well, aysiu isn't answering, so here's a good web site on learning the command line:
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)
As Matthew says, after even a little learning the command line is indespensible to most linux users.

---

### Post by MaximB on 2006-06-28
let me tell you a secret...
I'm studing MCSE (already told you it's just to get work ,I don't like MS)
and I'm using win2003 in order to learn there buggy OS.
b/z of the GUI that windows has it's not working properly.
you set somthing up , it sopose to work fine - but it doesn't.
it's like a russian rulet - somthimes it works and somthimes not - you will never know what's the problem.
command lines always work !!!
the problem is learning them - there's much more command lines in linux , it was built on it.

GUI's I like - there easy to use...but you need to make sure it will ALWAYS work.

---

### Post by avtolle on 2006-06-28
As a relative newcomer to Linux, in general, and Ubuntu, in particular, I hope the command line is never eliminated. I began my computer experience (personal, that is) in the CP/M days, then was forcibly dragged to MSDOS 2.11 (I think), thence through later iterations of DOS and then Windows, beginning w/Windows 3.11.

Anyway, do not fear the command line; it is your friend. I hopefully will, as an older user, regenerate enough brain cells to stave off senility by learning the commands I need. :D Be that as it may, the use of the command line should scare no one, serves to instruct one on how his/her computer works, and in general speeds up many simple processes.

With all that said, I understand the desire for GUI do everything for me, as that is all the newer group of users has really known; and, bluntly, most "just want it to work now".

OK, enough of my 2 cents. Back to the list of commands....:confused:

---

### Post by Al3xanR0 on 2006-06-28
[QUOTE=nameiwantistaken]I'm wondering if there is any movement with Ubuntu to remove the need to use a command line to anything.  This would include updating source lists, using apt-get, installing drivers, compiling the kernel, etc.  Getting the application installed is easy now, but once you get to that point things become very difficult.  What is stopping this OS from getting to the next level in terms of its goal of being suitable for desktop is the reliance on the command line.  No other successful desktop OS requires a user to learn commands to interact with the kernel to do pretty much anything.  I don't think an OS can be considered a desktop option until this is gone.  Any developers out there have any input on this?[/QUOTE]

I like the way Matthew put it best

[QUOTE=matthew]The command line is one of the most powerful and user-friendly ways to do things in the unix/linux/bsd world. Once you have learned it even a little bit you will never stand for anyone taking it away from you.[/QUOTE] and [QUOTE=matthew]Yeah, there are new GUI's all the time in the Linux world, most of which are great. They will never replace the functionality of the command line. [/QUOTE]

To simplify things even further, image Windows XP with no GUI.... <Al3xanR0 allows for a moment of reflection> well that is what it would be like using GNU/Linux without the CLI paradoxically speaking of course.

---

### Post by KingBahamut on 2006-06-28
I honestly see the need of a CLI as a nessecary interface within Ubuntu (and any OS really for that matter). And the other Big companies (Microsoft's Monad, Apples CLI interface, Sun is a Uncie , so it too has nessecity) seem to aggree. Command Line Interfacing is a nessecity in life. Server and Desktop user alike. I personally couldnt live with a command line, and I think if users approach it as something not to be afraid of , that its a tool like any other, then any stigma attatched to it will go away.

---

### Post by aysiu on 2006-06-28
First of all, I just want to clarify something--the original post-er is asking if there's a movement to get rid of the *need* for the command-line, not the command-line itself.

The command-line will always be there in Ubuntu. Don't worry. It's not going away.

That said, I think the movement's already happening.

1. Most of the time, when people give you command-line instructions, it's not because there's no way to do it via point-and-click. It's because it's easier, more effective, and less error-prone than giving point-and-click instructions.

So the next time someone says > Just paste this command into the terminal ```
sudo aptitude update && sudo aptitude install firefox mozilla-thunderbird flashplugin-nonfree kolourpaint acroread
``` it's not because this *can't* be done through a graphical environment. It's because walking someone through installing those packages graphically is a pain in the a s s, and it's likely to lead to unnecessary confusion.

Or, the instructions can simply be time-consuming. How long do you think [this page](http://www.psychocats.net/ubuntu/installingsoftware) took to create? How long do you think, by comparison, that [this page](http://www.monkeyblog.org/ubuntu/installing) took to create?

2. You know, I've been using Ubuntu only a little over a year now, and every single new release has a major focus--creating graphical frontends for command-line tasks.

Think about it. What were the improvements from Hoary to Breezy? Breezy to Dapper?

From Hoary to Breezy you got a graphical bootsplash screen, and add/remove applications simplified version of Synaptic, and a graphical menu editor. There may be other graphical frontends, but those are the ones that come to mind immediately. From Breezy to Dapper, you got a graphical doubleclick-install of .deb files, a point-and-click installer for the entire operating system, and a much better-looking Human theme.

Do you think developers are just sitting there twiddling their thumbs? Ubuntu gets released twice a year, and every new release has more focus on making the point-and-click environment more functional.

That said, I have to say Ubuntu seems to be doing a little catch-up to where a lot of the other "user-friendly" distros already were last year in terms of GUI functionality. Well, we're moving at a rapid pace!

There's one thing I will flatout disagree with you on here: [quote]No other successful desktop OS requires a user to learn commands to interact with the kernel to do pretty much anything. I don't think an OS can be considered a desktop option until this is gone.[quote] I'm not sure what you mean by "interact with the kernel," but for day-to-day functioning, I can't think of a single task I do on Ubuntu that *requires* the command-line. I may use the command-line for fun or for speed, but I don't *need* to use it.

I can assure you, based on what I've read, that if people bought System76 computers, they would not need the command-line for very much at all. Most of the time when people "need" the command-line, it's for setting up purposes, not for general use purposes. When hardware detection fails or you need some proprietary driver to get your video card working, well... you may need the command-line.

But if Ubuntu came preinstalled on your computer, seriously... tell me one thing you would **need** the command-line for.

---

### Post by angkor on 2006-06-28
[QUOTE=nameiwantistaken]This would include updating source lists, using apt-get, installing drivers, compiling the kernel, etc. [/QUOTE]

As far as I know all of these things don't *require* the terminal. They all have gui counterparts (except maybe for installing some drivers).

I don't mind choice. Let there be a Gui and a terminal method for everything, just let me decide what to use when.

---

### Post by aysiu on 2006-06-28
By the way, the best way to help this movement is by donating money to Ubuntu and filing bug reports.

---

### Post by matthew on 2006-06-28
[quote=aysiu]But if Ubuntu came preinstalled on your computer, seriously... tell me one thing you would **need** the command-line for.[/quote]A few non-standard examples, but common for me...

-Installing the VMWare server and other cool stuff I like that doesn't come standard with any distro.

-Piping the output from one command into the input of another. *

-Writing shell scripts. *

-Playing Nethack. :)

*These are significant.

---

### Post by T700 on 2006-06-28
[quote=angkor]I don't mind choice. Let there be a Gui and a terminal method for everything, just let me decide what to use when.[/quote]

Exactly.  I enjoy poking around and finding faster/easier ways to do things.  Sometimes that means a GUI and more often, that means a command line.  Neither is perfect for every situation.

I agree with the OP in that for general, public usage, the vast majority of everyday functions should be easily done via GUI.  That said, I would like a clarification from the OP.  Does she/he want the command line to go away or simply to be a redundant method for most uses?

Paul

---

### Post by aysiu on 2006-06-28
[QUOTE=matthew]A few non-standard examples, but common for me...

-Installing the VMWare server and other cool stuff I like that doesn't come standard with any distro.[/quote] Well, unfortunately, I don't know if that's something Ubuntu can help.

> 
-Piping the output from one command into the input of another. *

-Writing shell scripts. * And, of course, these are things that, by definition, need some kind of command-line. Though, I've written shell scripts in Gedit.[/QUOTE]

---

### Post by Shay Stephens on 2006-06-28
I was being lulled to sleep with Windows.  Wanting to do everything graphically.  And look where Microsoft took that mentality.  They now wield undue control over the OS.  When I started using Ubuntu, I wanted to continue to do everything without a command line.

But now, I have come to recognize something important.  Having a strong and robust command line keeps the OS transparent.  Relying 100% on a gui makes the OS less transparent.  There is a disconnect and the OS vendor can start to take undue advantage of that.

So for the sake of maintaining freedom, any OS needs to have and maintain a strong and robust command line.  Build whatever gui you want **on top of that**, even one that does not require the use of the command line, but the command line should always be available.

---

### Post by xtacocorex on 2006-06-28
The movement away from the CLI is very apparent, IMHO, in SuSe. I don't have a problem with SuSe, but I can't stand YaST. I don't like the way that it forces you to do everything with the GUI and even then, everytime I've tried to fix something for my friend, I can't get it working on his system, but if I did it on mine, it'd be cake. The reason being, the GUI prevents the ability to interact with the config file in a more personal way. (In the case of YaST)

Another downfall of the reliance upon the GUI is what happens if, say your x-server crashed. If you can't figure out how to use a CLI based text editor, you'd be up a creek without a paddle. If you don't have a dual boot and can't get to a second computer, how are you going to be able to figure out how to fix something? If you can't have a GUI browser, would one know about lynx to do CLI browsing. I'm not sure how these forums are presented in lynx, but at least you can find information with using the program. 

All this being said, I do like the option of having a GUI for each program to easily change something if it isn't vital to the moment, this way you don't have to dig for the file. But I do prefer to do stuff manually because it is usually faster.

---

### Post by aysiu on 2006-06-28
[QUOTE=Shay Stephens]
So for the sake of maintaining freedom, any OS needs to have and maintain a strong and robust command line.  Build whatever gui you want **on top of that**, even one that does not require the use of the command line, but the command line should always be available.[/QUOTE] And it always will be in Ubuntu.

---

### Post by wpshooter on 2006-06-28
[QUOTE=nameiwantistaken]I'm wondering if there is any movement with Ubuntu to remove the need to use a command line to anything.  This would include updating source lists, using apt-get, installing drivers, compiling the kernel, etc.  Getting the application installed is easy now, but once you get to that point things become very difficult.  What is stopping this OS from getting to the next level in terms of its goal of being suitable for desktop is the reliance on the command line.  No other successful desktop OS requires a user to learn commands to interact with the kernel to do pretty much anything.  I don't think an OS can be considered a desktop option until this is gone.  Any developers out there have any input on this?[/QUOTE]

Dear Nameiwantistaken:

I completely agree with you and I am happy to report to you that it is my belief that with each new implimentation of Ubuntu more and more of the need for use of command line parameter is leaving by the developers providing GUI methods of performing tasks.

Yes, the **necessity** for using the CLI must be overcome before the majority of mom and pop computer users in this world that go down to Wal-Mart and buy an off the shelf computer will have any inclination of thinking of using anything but a M/S windows based computer.

For those that think these command line parameters are somehow cool (and let me say that in the past, I have used plenty of DOS command line parameters and have also in the past even written programs in GWBASIC), please let me say that when I go to some of these how too aids in performing some simple task and I am shown sometimes two to three pages of command line parameter syntax that I must then type in to perform a task and then I have to make absolutely sure that I do not mis-type a single character and that every letter be in the correct case for the command to work and then I must print out and keep a stack of how toos for the various task that I may need to perform again in the future, this is asking just a bit much of the average mom and pop user coming from the M/S world.

And for those that say that it is much easier to give instructions for doing something with CLI commands than it is to give the same instructions for doing that task from a GU interface, I just do NOT buy it.  I would prefer any day to give the user a simple set of instructions regarding the GUI wherein if I make a simple mistake in my instructions to them, that they will readily see my mistake and go ahead and get the task performed, whereas if I mis-type one character in the CLI info that I provide them, the majority of the time they are going to be dump-founded as to why it will not work.

The terminal/command line needs to stay there for those that HAVE the training or the time to learn it, but for the other 98% of computer users, common day tasks that need to be performed need to be performable thru GUI.  And some of the task that were mentioned in one post were NOT IMO task that an average mom & pop computer users would ever have occasion to perform.

If Ubuntu in particular and Linux in general does not get over this problem they will NOT become a product that will be embrassed by the general computer public.  But I again am happy to report to you that I strongly believe that they WILL.

Thanks.

---

### Post by mozetti on 2006-06-28
I can't really add anything meaningful that hasn't already been said regarding the OPs question. But, relatedly, there also aren't many Windows "power-users" that don't use the command-line interface (CLI). The adage that "the CLI is the best/fastest way to do things," also applies to MS OS'.

---

### Post by aysiu on 2006-06-28
[QUOTE=wpshooter]please let me say that when I go to some of these how too aids in performing some simple task and I am shown sometimes two to three pages of command line parameter syntax that I must then type in to perform a task and then I have to make absolutely sure that I do not mis-type a single character and that every letter be in the correct case for the command to work[/quote] Please let me say that you can just highlight the commands and copy and paste them into the terminal.

> 
And for those that say that it is much easier to give instructions for doing something with CLI commands than it is to give the same instructions for doing that task from a GU interface, I just do NOT buy it. Take my word for it, or start making your own GUI instructions. Take a look at this: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

I've made plenty of both CLI and GUI instructions, and the GUI instructions are **much** more difficult to create. And when someone says, "But I don't see that on my computer," what do you do? What if someone says, "I don't have that program," or "The window just seems to disappear"?

It's a lot easier not only to give command-line instructions but also to deal with them afterwards, as command-line instructions will give errors if they don't work.

```
gedit bash: command not found
``` is a lot more helpful to me in helping someone else than > Yeah, I don't see it in the menus

---

### Post by bruce89 on 2006-06-28
And also, the command line is common to every distro (mostly, apart from apt/dpkg etc.) and DE.

---

### Post by aysiu on 2006-06-28
Can we stop the "mom and pop" BS?

I don't think "mom and pop" will be installing VMWare Server or creating shell scripts. So what--if they bought a System76 Ubuntu preloaded computer--would mythical "mom and pop" need the command-line for?

---

### Post by bruce89 on 2006-06-28
[QUOTE=aysiu]I don't think "mom and pop" will be installing VMWare Server or creating shell scripts. So what--if they bought a System76 Ubuntu preloaded computer--would mythical "mom and pop" need the command-line for?[/QUOTE]
This is very true!

---

### Post by zugu on 2006-06-28
[QUOTE=matthew]

The command line is one of the most powerful and user-friendly ways to do things in the unix/linux/bsd world.[/QUOTE]

Powerful ... yes.
Necessary ... yes.
User-friendly? Come on!!! You may see it as user-friendly, but I see it as a necessary evil. A skilled user can do anything through the command-line, but for the newbie it's like 'that ugly thing that returns errors and $#|^'. 

I also think we should decide what defines the command-line: is it only the usual/built-in commands for everyday use or do we assimilate the compiling errors and man pages (totally unfriendly) in the definition too?

Everything is built with usability in mind, such as error details. If something's wrong, *nix tells you the exact spot where that something happened. However, an error spawning on a whole screen, even if minor, can totally turn-off non-tech people. Add the awkward way the text is wrapped sometimes in a terminal to this and you have a frightened user.

I know my way through the command-line: commands, arguments and switches, navigating through the hierarchical file system, starting programs & stuff etc. However, I will never see it as user-friendly. Here's a post of mine about the [ugliness]("http://www.ubuntuforums.org/showthread.php?t=181444") of the command-line.

The 'it should be or not' dispute has a clear answer: the way things are now, the command-line will continue to exist.

Compare with the DOS/Windows combination. Before the appearance of the graphical *nix interfaces, *nix was basically DOS on steroids. You could (and you also can) do anything from the command-line: surf the web, check email, chat on IRC etc. A personal asumption of mine is that the work put in developing command-line far exceeds the work put in graphical interfaces & applications. (Please correct me if I'm wrong).

After GUIs* have appeared, the OS were like a pancake: the powerful commandline + the GUI. In the meantime, Microsoft did a good job eliminating the command-line, creating the NT platform from scratch. DOS was dumped, in a painful move for them. The *nix (particularily the FOSS ones) systems have kept things unchanged. Why? Because there was too much valuable work that has been put into them, more than it had been put into DOS. Poeple could't dump all that.

So that's why we have a command-line today, and we will always have it. Unfortunately.

Cheers.

*Graphical User Interface

---

### Post by wpshooter on 2006-06-28
[QUOTE=aysiu]Please let me say that you can just highlight the commands and copy and paste them into the terminal.

 Take my word for it, or start making your own GUI instructions. Take a look at this: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

I've made plenty of both CLI and GUI instructions, and the GUI instructions are **much** more difficult to create. And when someone says, "But I don't see that on my computer," what do you do? What if someone says, "I don't have that program," or "The window just seems to disappear"?

It's a lot easier not only to give command-line instructions but also to deal with them afterwards, as command-line instructions will give errors if they don't work.

```
gedit bash: command not found
``` is a lot more helpful to me in helping someone else than[/QUOTE]

In all likelyhood when methods for doing these task are converted to GUI, neither YOU or I will not be having to give instructions to anyone.  And that would not hurt MY feelings in the slightest !!!

---

### Post by aysiu on 2006-06-28
Windows has whole books for how to do GUI tasks.

On a nigh-daily basis, I help my co-workers do GUI tasks in Windows that they don't know how to do.

GUIs do not preclude confusion about how to do things.

A well-designed GUI in combination with an open mind will almost always make things easy, though. There's not always a well-designed GUI for the program or an open mind in the user.

I'll give you a couple of examples of this:

1. When our office upgraded from Windows 2000 to Windows XP, I got all sorts of questions from my confused co-workers. One of the number one questions was "How do I get my 'show desktop' button back?" Well, a poorly designed GUI didn't make that obvious. If you right-click the panel in Windows XP, there's no "show show desktop" option. You have to go to **Toolbars** > **Quick Launch**. It wasn't difficult for me to figure out, but for these "mom and pop" people, it was.

2. The add/remove programs feature in Ubuntu is an easy way to install software, but people don't use it. Why? Because they don't come with an open mind. Yes, I realize there are a lot of programs that are not in the repositories, but a lot of people try to install .tar.gz files they downloaded separately even if they could have used add/remove programs. It's not because the add/remove program interface is badly designed. It's because they don't have open minds--they come to Ubuntu thinking it's just like Windows... download a setup file and doube-click it.

---

### Post by az on 2006-06-28
To answer the original question, yes this question has been and is being addressed.

[https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/CommandLineDisintegration?action=show&redirect=CommandLineDisintegration](https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/CommandLineDisintegration?action=show&redirect=CommandLineDisintegration)
It has been in the works since Hoary.  

Keep an eye on this page:
[https://launchpad.net/sprints/uds-paris/+specs](https://launchpad.net/sprints/uds-paris/+specs)
to see if it has a formal spec for Edgy.

---

### Post by aysiu on 2006-06-28
[QUOTE=azz]To answer the original question, yes this question has been and is being addressed.

[https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/CommandLineDisintegration?action=show&redirect=CommandLineDisintegration](https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/CommandLineDisintegration?action=show&redirect=CommandLineDisintegration)
It has been in the works since Hoary.  

Keep an eye on this page:
[https://launchpad.net/sprints/uds-paris/+specs](https://launchpad.net/sprints/uds-paris/+specs)
to see if it has a formal spec for Edgy.[/QUOTE]
It seems as if a few of the things on the to-do list already exist: > **Outstanding Issues**

      Connecting to VPN servers has no GUI equivalent.
    * *kvpnc* is a GUI for that.

>       xkill ... need a better way for users to kill errant applications. GSM doesn't always kill an application and the "Force Quit" dialog sometimes takes a considerable amount of time to come up. Keyboard shortcut? Control-Alt-Escape in KDE.
 > 
      No way of getting to existing windows drives without going to /etc/fstab. (Another BOF) Knoppix has had this capability for a long time. Isn't there some way to easily adapt that to Ubuntu?
> 
      GUI for mass renaming of files. KRename?

---

### Post by Bloch on 2006-06-28
Thanks aysiu.
At last 20+ replies later a concrete answer!!

The normal user, if s/he looks is the administrator,  will inevitably have to use the CLI, even if only once a year!!

That will only change if there is some new (linspire-like) distro pre-installed where you are allowed install software only from the company's repositories or you lose your guarantee.

The way you can change desktop environments, kernels etc make it inevitable that the user will do something to break the system. And if you try out software not in the ubuntu repositories (like flash etc) you are given  CLI instructions because the software producer does not want to give GUI instructions for 3 or 4 different desktops. (gnome, KED, XFCE ...) 

As long as linux users have the freedom to choose their own kernel, desktop, file browser, etc there will be a need to learn the CLI. 
Linux - the choice of those who know what a computer is
that's OK with me. As soon as Linux hits 5%, that's what I would count as mainstream. The price of absolute user-friendliness is too high

---

### Post by aysiu on 2006-06-28
Linspire has always been the "normal user" distro, but few people want to acknowledge it. I prefer not to use it because I'm a cheapskate, and I happen to love the command-line and the *sudo* security model, but it is very graphically oriented.

Mepis and PCLinuxOS are good compromises--a lot of GUI configuration, a lot of preinstalled proprietary codecs.

---

### Post by wpshooter on 2006-06-28
[QUOTE=azz]To answer the original question, yes this question has been and is being addressed.

[https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/CommandLineDisintegration?action=show&redirect=CommandLineDisintegration](https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/CommandLineDisintegration?action=show&redirect=CommandLineDisintegration)
It has been in the works since Hoary.  

Keep an eye on this page:
[https://launchpad.net/sprints/uds-paris/+specs](https://launchpad.net/sprints/uds-paris/+specs)
to see if it has a formal spec for Edgy.[/QUOTE]

Azz:

I have said before and will say again (as a big fan of Ubuntu) that, IMO, it is still "**A diamond in the rough, for now**", but I just can hardly wait to see what it is going to be in say 2 to 3 years from now.

I predict that everyone that is clinging so hard to the good old terminal/command line is NOT going to be saying aaaahhhhhh, I sure miss the good old days.

Because when you come right down to it the real purpose of a good O/S is NOT how to get it setup, configured, etc. but to be used to run applications quickly and reliably and get work done.

The real question in my mind is how Ubuntu and other Linux distributions are going to get the masses to try Ubuntu and drop that other O/S like a hot potato(e) !!!

---

### Post by aysiu on 2006-06-28
It's not an either/or situation *wpshooter*.

In the ideal world, you can use whatever tool you feel like. One day, you can feel like using the command-line. Another day, you can feel like using the GUI.

Ubuntu will never get rid of the command-line (at least I hope not). But hopefully it will continue to *add* good GUI tools for command-line operations.

There are plenty of things for which there is a GUI frontend, but I choose to use the terminal because it's faster--resizing fifty images, for example, or installing eight different applications.

---

### Post by wpshooter on 2006-06-28
[QUOTE=aysiu]It's not an either/or situation *wpshooter*.

In the ideal world, you can use whatever tool you feel like. One day, you can feel like using the command-line. Another day, you can feel like using the GUI.

Ubuntu will never get rid of the command-line (at least I hope not). But hopefully it will continue to *add* good GUI tools for command-line operations.

There are plenty of things for which there is a GUI frontend, but I choose to use the terminal because it's faster--resizing fifty images, for example, or installing eight different applications.[/QUOTE]

I certainly agree.

Want to keep both but have GUI for those who do not choose to use CLI.  And I certain agree that it can be faster IF you know the commands and all of their syntax backwards and forwards.  

But go out and talk to 100 average computer users from the M/S thing and see how many you can convince to learn the Linux commands.

I don't believe that this O/S should be reserved for the few but made usable for the masses.

Have a great day in Ubuntu land.

---

### Post by aysiu on 2006-06-28
I agree with you, *wpshooter*.

GUI and CLI should be available for everything. That's the ideal.

Then everyone's happy and has *choice*. She can choose to use the CLI or the GUI, whatever suits her fancy.

I will still continue to give commands for support, though, as I think that's ideal for a text-based forum. If we move to the Ubuntu Forums being done via webcam or VNC with VOIP, then maybe the GUI will become more important for support purposes, but I doubt that'll happen any time soon.

---

### Post by az on 2006-06-28
[QUOTE=wpshooter]Azz:

I have said before and will say again (as a big fan of Ubuntu) that, IMO, it is still "**A diamond in the rough, for now**", but I just can hardly wait to see what it is going to be in say 2 to 3 years from now."[/QUOTE]
Maybe more, maybe less....

[QUOTE=wpshooter]
The real question in my mind is how Ubuntu and other Linux distributions are going to get the masses to try Ubuntu and drop that other O/S like a hot potato(e) !!![/QUOTE]
I don't think the raison-d'etre of ubuntu is to compete with Windows.  It is what it is and I reckon it will gain marketshare all by itself, without adding on such a cause.

---

### Post by MetalMusicAddict on 2006-06-28
I am _VERY_ happy Ive had to learn to do things from the command line. I like being able to do things with it rather than having to install yet another little gnome app (KDE or XFCE for that matter) to do 1 task. I guess If there were tighter intergration of some apps I might feel a little different.

---

### Post by ProjectGod on 2006-06-29
whilst were eliminating the command line... could we also eliminate the keyboard and mouse? they should make it so that we can plug directly into the computer and have the computer interpret our brain signals so all we need to do is think and the job gets done!@:lol:

---

### Post by Thundercat on 2006-06-29
Just want to add to this discussion that in windows there are a bunch of things that you have to use the command line for. (unless you use third party GUI tools, but the same would apply in ubuntu) 
eg. pinging an IP address
listing the contents of a folder into a text file (I do this often)

but more to the point windows would be a lot better if you could do more things via the command line, and thats one of the main reasons I'm working on switching to Ubuntu!

---

### Post by aysiu on 2006-06-29
[QUOTE=ProjectGod]whilst were eliminating the command line...[/quote] I don't think anyone has suggested that we get rid of the command-line... only that we get rid of the *need* for the command-line--two very different things. > could we also eliminate the keyboard and mouse? they should make it so that we can plug directly into the computer and have the computer interpret our brain signals so all we need to do is think and the job gets done!@:lol: You're joking, but I think I actually read [a news story about something like this.](http://www.pcmag.com/article2/0,1895,1981622,00.asp)

---

### Post by 23meg on 2006-06-29
> 
But go out and talk to 100 average computer users from the M/S thing and see how many you can convince to learn the Linux commands.Go and talk to 100 average Ubuntu-only users and see how many you can convince to get used to the Windows GUI.
> 
I don't believe that this O/S should be reserved for the few but made usable for the masses.I don't believe that this OS should be reserved for the habits of ex-Windows users but made usable for the masses. Ex-Windows users aren't a majority in Ubuntu's long term target audience.

---

### Post by matthew on 2006-06-29
[quote=23meg]I don't believe that this OS should be reserved for the habits of ex-Windows users but made usable for the masses. Ex-Windows users aren't a majority in Ubuntu's long term target audience.[/quote]I love the way you phrased this.

---

### Post by hotbrainz on 2006-06-29
[QUOTE=23meg]Go and talk to 100 average Ubuntu-only users and see how many you can convince to get used to the Windows GUI.
I don't believe that this OS should be reserved for the habits of ex-Windows users but made usable for the masses. Ex-Windows users aren't a majority in Ubuntu's long term target audience.[/QUOTE]

Well no offence but Ubuntu users have readily chosen to adopt the command line. Personally I love it too. But i cant see no way my dad using the command line no matter how good it may be :) As mentioned loads of times before, me thinks it is all a matter of choice. Adding GUI will just add another option to make it easier for people to make the change. If they want to dig deeper, say hello to Mr. Command line.

---

### Post by nocturn on 2006-06-29
I really want to stress this again, I cannot find any tasks any "average joe" user needs to do on his computer that currently *require* the command line.  Maybe there are a couple of niche things that do require it, but it won't be many.

Yes, many of us on the forums offer advice in the form of commands because it is doable over a forum where it would take 10-15 screenshots to accomplish the same.  Additionally, as long-term *nix users, we are often more familiar with the CLI (I am).

If you want to set up servers or advanced programs such as vmware, you should be comfortable enough with your system to use the CLI because if you lack that knowledge, it is dangerous to do what you are doing (like driving a car without knowing what that wheel thingy is for).

---

### Post by skirkpatrick on 2006-06-29
As stated by others, after you have a properly installed system (preinstalled?) there is not real need by the average user to use the command line.  My daughter (22) uses Ubuntu everyday for all her computing needs and never touches the command line.  She occasionally installs a program from the repositories using Synaptic but she is quite happy with using her system.

The original poster may not have noticed but Microsoft finally added more capabilities to its CLI starting with either NT or XP.  Granted, system admins are not considered your average user but most system admins I talk to that administer Windows servers use the CLI because it's quicker for them as well.

One more thing against the original post, when someone can show me that you can recompile your kernel, or for that matter, any major piece of software for Windows or Mac, using either CLI or GUI, let me know because I'll have to travel to a much warmer place to get some ice water.:D

---

### Post by AndyCooll on 2006-06-29
[QUOTE=hotbrainz]As mentioned loads of times before, me thinks it is all a matter of choice. Adding GUI will just add another option to make it easier for people to make the change. If they want to dig deeper, say hello to Mr. Command line.[/QUOTE]

Agree with this. Yes, ensure "average joe" can do all his every day asks without ever needing to touch the command line. And yes, ensure the command line is there for those who want to tackle the more complex tasks (or just prefer the CLI approach).

:cool:

---

### Post by MaximB on 2006-06-29
I read in this topic that you can serf the internet with the command line only and no GUI....now how's that possible ? what are you going to see at the website...it's all graphics.

---

### Post by mozetti on 2006-06-29
[QUOTE=MAXDDARK]I read in this topic that you can serf the internet with the command line only and no GUI....now how's that possible ? what are you going to see at the website...it's all graphics.[/QUOTE]

The browser is called Lynx, at least the one I'm most familiar with - there are probably others. And it doesn't display graphics, just text.

---

### Post by T700 on 2006-06-29
[quote=MAXDDARK]I read in this topic that you can serf the internet with the command line only and no GUI....now how's that possible ? what are you going to see at the website...it's all graphics.[/quote]

You would use the CLI to invoke a graphical application--your browser.  You could also use a text based browser; something akin to Lynx in the Windows world.

Paul

---

### Post by nocturn on 2006-06-29
[QUOTE=MAXDDARK]I read in this topic that you can serf the internet with the command line only and no GUI....now how's that possible ? what are you going to see at the website...it's all graphics.[/QUOTE]

It's pretty convenient to have though, I use elinks a lot on my server
I also use a text-based mailclient on it (handy for checking mail over SSH connections).

---

### Post by xtacocorex on 2006-06-29
[QUOTE=MAXDDARK]I read in this topic that you can serf the internet with the command line only and no GUI....now how's that possible ? what are you going to see at the website...it's all graphics.[/QUOTE]

My intention for mentioning that in my post was to show that, sometimes, you can't do everything graphically, in the case of an x-server crash and you have no other computer. I was attempting to make light that, although a GUI is good for things, not having CLI skills can be a detriment.

NOTE:
Although the likelyhood of a very novice/naive user to attempt to fix a botched xorg.conf file is slim, if they have basic CLI skills, they can work through it.

---

### Post by egon spengler on 2006-06-29
[QUOTE=nameiwantistaken]I'm wondering if there is any movement with Ubuntu to remove the need to use a command line to anything.  This would include updating source lists, using apt-get, installing drivers, compiling the kernel, etc.  [/QUOTE]

Besides the fact that there are GUI apps for the first three things mentioned I would have to wonder how many people would feel compelled to recompile their kernel yet be afraid of the command line. Of course I'm just speculating but wouldn't learning the cli come before such a step?

[QUOTE=wpshooter]I predict that everyone that is clinging so hard to the good old terminal/command line is NOT going to be saying aaaahhhhhh, I sure miss the good old days.[/QUOTE]
[QUOTE=wpshooter]Want to keep both but have GUI for those who do not choose to use CLI.  And I certain agree that it can be faster IF you know the commands and all of their syntax backwards and forwards. [/QUOTE]

So if you concede that it's faster to use the cli (and it nearly always is) then I guess your prediction won't ever amount to much

[QUOTE=wpshooter]But go out and talk to 100 average computer users from the M/S thing and see how many you can convince to learn the Linux commands.

I don't believe that this O/S should be reserved for the few but made usable for the masses.[/QUOTE]

The thing is though, most people have no real compelling reason to learn too much about their computer (and I find this completely understandable) and so as much as you might say "Windows users won't want to learn the cli" as if that in itself is proof of the worthlessness of the cli it equally applies that many Windows/Mac/Linux users don't want to learn *anything* about their pc. We've all heard the countless tales of so called "dumb users" who complain about no internet access while their moden is unplugged. If 100 average Windows users can't be convinced to learn how to set up their router does that mean routers are useless too?

---

### Post by bluenova on 2006-06-29
I don't understand the point of this thread (apart from people giving support in the form of command line entries).

If you want to use a GUI app to do something you use the GUI app, if you want to use the CLI you use the CLI. I use them both about 50/50. Sometimes I will apt-get sometimes I will go to synaptic. I can't say why I use one over the other, I guess it just depends how I'm feeling.

---

### Post by kane77 on 2006-06-29
[QUOTE=matthew]Please...no flames. The guy is probably serious.

The command line is one of the most powerful and user-friendly ways to do things in the unix/linux/bsd world. Once you have learned it even a little bit you will never stand for anyone taking it away from you.

Yeah, there are new GUI's all the time in the Linux world, most of which are great. They will never replace the functionality of the command line.

I expect aysiu or someone else to step in here momentarily and explain further. Hey, aysiu? Where's that link of yours??

EDIT: nevermind...I found it. Please read this: [http://www.ubuntuforums.org/showthread.php?t=59334]("http://www.ubuntuforums.org/showthread.php?t=59334")[/QUOTE]


Completely agree on that! Command line is very powerful!! I used synaptic, but I don't... I enjoy doing it from CLI... :) It's not hard and it's darn fast...

---

### Post by xtacocorex on 2006-06-29
[QUOTE=bluenova]I don't understand the point of this thread (apart from people giving support in the form of command line entries).

If you want to use a GUI app to do something you use the GUI app, if you want to use the CLI you use the CLI. I use them both about 50/50. Sometimes I will apt-get sometimes I will go to synaptic. I can't say why I use one over the other, I guess it just depends how I'm feeling.[/QUOTE]

IMO, the point of the thread was lost a long time ago, with the first couple or so being the most valid.

---

### Post by aysiu on 2006-06-29
There is no point to this thread. People just like to argue.

There are already movements to create more GUI frontends for tasks.

And creating more GUI frontends never prevents people from using CLI.

So no one can complain. Yay!

---

### Post by bluenova on 2006-06-30
[QUOTE=aysiu]
So no one can complain. Yay![/QUOTE]
LOL, they will always find a way :D

---

### Post by oyvindaa on 2006-06-30
I love the terminal. If it were to go away it wouldn't be the same :(

---

### Post by aysiu on 2006-07-01
[QUOTE=oyvindaa]I love the terminal. If it were to go away it wouldn't be the same :([/QUOTE]
It won't go away.

---

### Post by jeremy on 2006-07-01
[QUOTE=nameiwantistaken]No other successful desktop OS requires a user to learn commands...[/QUOTE]
Windows has a command feature, I use it to find out a clients IP for example. But then I suppose that windows could hardly be called "successful".

---

### Post by nameiwantistaken on 2006-07-02
Thanks to everyone for responding.  I forgot to check back before, so the thread kind of went everywhere.  My original post was not meant to see if the command line was being done away with.  It was meant to simply see if there would be a point where someone didn't need the command line to do anything ever.  For anything that wants to be described as a desktop, this basically needs to happen.  

I will address all of the points that I think are open in the thread and then give some commentary of my own.

"1. When our office upgraded from Windows 2000 to Windows XP, I got all sorts of questions from my confused co-workers. One of the number one questions was "How do I get my 'show desktop' button back?" Well, a poorly designed GUI didn't make that obvious. If you right-click the panel in Windows XP, there's no "show show desktop" option. You have to go to Toolbars > Quick Launch. It wasn't difficult for me to figure out, but for these "mom and pop" people, it was."

True, this was a change, but for me as a user with some playing around I was able to fix what Microsoft broke (Luna was a useless late add on to make XP seem different from 2k).  I'm pretty sure I'm not going to be able to guess who to change things with a command line.  If it's in a well designed GUI, I'll probably be able to figure it out.

"2. The add/remove programs feature in Ubuntu is an easy way to install software, but people don't use it. Why? Because they don't come with an open mind. Yes, I realize there are a lot of programs that are not in the repositories, but a lot of people try to install .tar.gz files they downloaded separately even if they could have used add/remove programs. It's not because the add/remove program interface is badly designed. It's because they don't have open minds--they come to Ubuntu thinking it's just like Windows... download a setup file and doube-click it."

You have a good point there.  People don't come in with an open mind.  Many compare it to the MS Add/Remove and it doesn't have free programs there.  I think this can be remedied by offering a guided tour such as MS does when you install windows at first and also changing it to two options.  One being something like "Free Programs" and "Remove Programs".  That would generate more interest from a casual user.  Everyone likes free stuff.

"I really want to stress this again, I cannot find any tasks any "average joe" user needs to do on his computer that currently *require* the command line. Maybe there are a couple of niche things that do require it, but it won't be many."

I'm the average joe trying to do something basic and believe me I've had to mess around with PLENTY OF IT.  Spending 3 weeks to setup a Linux machine that will do basic tasks, raid discs (yes that is a mainstream task these days), run a web server and server side coding/database (mainstream for people to make web pages these days too) is just too much.  Much of that time has been spent messing with command lines.  It's great to 'learn', but by the time I need any of it again I won't remember it.

"Yes, many of us on the forums offer advice in the form of commands because it is doable over a forum where it would take 10-15 screenshots to accomplish the same. Additionally, as long-term *nix users, we are often more familiar with the CLI (I am)."

The problem with CLI instructions is that even if you use them verbatim they don't always work and if people who were given the instructions fully explained them (instead of giving them from a linux expert point of view to another assumed linux expert) it would take much more time.  Normal, average users aren't ever going to want to mess around with a command line.  When you have the brains of the community only giving advice by command line it is a recipe for disaster.  By disaster, I mean giving up on Linux and going back to Mac/Windows.

If you want to set up servers or advanced programs such as vmware, you should be comfortable enough with your system to use the CLI because if you lack that knowledge, it is dangerous to do what you are doing (like driving a car without knowing what that wheel thingy is for)."

I can see your point, but do disagree.  There is a reason why companies like IBM, Microsoft and Oracle put user interfaces in front of their databases.  Also, there are plenty of home users who want to setup basic servers.  Giving them a chance of success is always good.  In terms of hardcore server administrators, I can see your point and if all you do is administer servers then have at it.  You probably should keep up on the syntax of commands and be able to do anything you want.

"As stated by others, after you have a properly installed system (preinstalled?) there is not real need by the average user to use the command line. My daughter (22) uses Ubuntu everyday for all her computing needs and never touches the command line. She occasionally installs a program from the repositories using Synaptic but she is quite happy with using her system.

The original poster may not have noticed but Microsoft finally added more capabilities to its CLI starting with either NT or XP. Granted, system admins are not considered your average user but most system admins I talk to that administer Windows servers use the CLI because it's quicker for them as well."

I'm an average user.  I've had to use plenty of it.  Way, way more than I have wanted and unless you consider something like, say, getting the OS to recognize my hard drive so I can install it and 'advanced task' then you're mistaken.  Not everything is in synaptic or install programs.  Not everything is made for Debian either, so there are plenty of times when you need to hit that command line.

Yes, I did know that MS did that.  Fortunately, I haven't really had to use it for home related items.  Yes, system admins use plenty of it but they aren't really what I was talking about in the post.

"Besides the fact that there are GUI apps for the first three things mentioned I would have to wonder how many people would feel compelled to recompile their kernel yet be afraid of the command line. Of course I'm just speculating but wouldn't learning the cli come before such a step?"

Let's say ones like me that just want to have their damn Linux distro install onto a hard drive.  There are repurcussions for not moving to the 2.6.16 kernel sometimes ;).  

"If you want to use a GUI app to do something you use the GUI app, if you want to use the CLI you use the CLI. I use them both about 50/50. Sometimes I will apt-get sometimes I will go to synaptic. I can't say why I use one over the other, I guess it just depends how I'm feeling."

The problem is that much of the support given in the community (forums, etc) is focused entirely on CLI tasks and desktop users aren't going to go for it.  I think that each HOWTO should include instructions for both graphical fixes and CLI ones.  IF you want Ubuntu to grow outside of the hardcore Linux realm, making things easier for people who just want to do normal tasks is paramount.

I'm sure some people will point out niche things that must still be done in Windows command line, but come on.  I know plenty of people who do plenty of robust things with that software and never touch a dos window.  

What I think is lost on the linux community (and please don't get your panties in a bunch..the Windows community takes plenty of constructive criticism too) in general is that the power of software is what you can do with it not how well you know the operating system and how you can change it around.  Software is power.  Creating 3d animation, complex databases, pulling pictures off of a digital camera, writing documents, creating spreadsheets, email, games and all of the things that people like to do with their machines.  

The power is in what you can accomplish, not how well you know the machines yourselves.  The problem is that so much of the knowledge within the community is focused on how to do things via a command line, that new users who only care about using a Linux based OS rather than knowing a Linux based OS are lost.

Based on what Azz has said, it seems like Ubuntu is already on the right course for this and certainly has respect amongst the online tech world.  Also, I hope that none of you took this as an attack against the work you do or the product you enjoy.  If I really wanted to troll, I wouldn't have taken this much time writing posts or getting Ubuntu working.  I just hope that you can all keep the CLI thing in mind the next time you are thinking of writing a howto or a piece of software.

---

### Post by aysiu on 2006-07-02
You're not an average user if you're posting in these forums. Sorry. You're not.

And if the person giving help has any sense, she won't fail when she **copies and pastes** commands into the terminal, but she will very likely fail if you try to describe the things she should be pointing and clicking.

I'm talking from a lot of experience helping both new and old users here.

You can make up whatever you *think* should be happening, but how many new users have you helped on these boards? Go ahead--give all the point-and-click instructions you want. See how easy it is.

By the way, I've probably uploaded more screenshots to the Ubuntu Forums than anyone else posting in this thread (it's numbering over 500 right now). So it's not as if I'm lazy and give only command-line instructions. Most of the time, command-line instructions are the best way to solve a problem in an online forum.

Once again--we're not doing a VNC, VOIP tutorial here. This is a text-based forum. Text-based instructions are appropriate.

> I think that each HOWTO should include instructions for both graphical fixes and CLI ones. HowTos get created by people who want to help others. Create your own graphical fixes tutorial or clam up about it. You can't demand others create graphical HowTos (which are very time-consuming, bandwidth-consuming, and generally hard to follow if you have a different interface or are on dial-up). Create them yourself. I've created graphical HowTos and command-line HowTos. The graphical ones are a pain and go on for pages and pages.

I applaud efforts like this: [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) , not "efforts" like yours. Money talks.

Since you mentioned it twice, I will, too: **You are not an average user**. Stop pretending you are.

---

### Post by cacharreo on 2006-07-02
You don't need command line for most of linux operations. But it's powerfull tool, much more than all the graphics desktop, and of course it's a **Safe Life** :evil:

---

### Post by otis_u on 2006-07-03
I agree.

To be accessable to every day users heavy reliance on the terminal needs to be done away with.

That said, this is still a linux distro, designed to be a functional linux distro... to totally get rid of the console would be sort of compromising the functionality of linux, but to have put effort into making as many console functions mirrored in the GUI as possible is definitely a good thing.

---

### Post by redelephant on 2006-07-03
Personally, I really enjoy watching something compile form the command line.

It can be a bit daunting at first, but it is well worth the effort to learn (even just a little bit).

---

### Post by jethro10 on 2006-07-03
[QUOTE=matthew]
The command line is one of the most powerful and user-friendly ways to do things in the unix/linux/bsd world.[/QUOTE]

User friendly !!!!

dream on....

J

---

### Post by jethro10 on 2006-07-03
[QUOTE=MAXDDARK]
GUI's I like - there easy to use...but you need to make sure it will ALWAYS work.[/QUOTE]

command line programs have bugs too !!

J

---

### Post by jethro10 on 2006-07-03
It's apparent reading this that the camp is split into 2.

the 1'000 of linux geeks, power users etc = keep command line
for the other billions of normal computer users = no command line.

I feel on balance the latter has to be correct. The masses always win whatever the subject.

Jeff

---

### Post by matthew on 2006-07-03
[quote=jethro10]User friendly !!!!

dream on....

J[/quote]Here's why I said that. With a command line shell like bash you only have to learn how to do things once. It doesn't matter if you change your GUI from Gnome to KDE to xfce or something else. ***You can still do the tasks you want to do the exact same way you are used to doing them.*** You can change linux distros from Suse to Ubuntu, Fedora to Slackware, Debian to Arch, it is immaterial. You can still ***do the same tasks in the same manner with little to no need to learn/relearn a process*** (unless you are using something like a package manager, etc. that is distro dependant, and even then you can change within a range of distros that use the same system).

Is the command line the easiest thing to learn for a newcomer? No. However, you only need to learn the info one time as opposed to when you update your OS from Ubuntu Breezy to Dapper and want to do the same things from a GUI (and don't get me started on the switch within the MS world where I went from Dos 2.x to 3.0 to 5.0 to Windows 3.0 to 3.1 to 95 to 98 to Me to XP and had to relearn each time how to do the same basic things).

So I ask you, which is ultimately more friendly to the end-user, having them relearn how to do things everytime you update the GUI or having them learn one thing that will remain true regardless of GUI changes?

---

### Post by nocturn on 2006-07-03
[QUOTE=jethro10]It's apparent reading this that the camp is split into 2.

the 1'000 of linux geeks, power users etc = keep command line
for the other billions of normal computer users = no command line.

I feel on balance the latter has to be correct. The masses always win whatever the subject.

Jeff[/QUOTE]

The CLI is an essential part of the Unix way.  It will not disappear any time soon.
Sure, GUI's are there  for 99% of the things, but I highly doubt they will ever offer the flexibility that the CLI does, which is it's attraction for power-users.

---

### Post by jonas_larson on 2006-07-03
[QUOTE=jethro10]It's apparent reading this that the camp is split into 2.

the 1'000 of linux geeks, power users etc = keep command line
for the other billions of normal computer users = no command line.

I feel on balance the latter has to be correct. The masses always win whatever the subject.

Jeff[/QUOTE]

Ooops! Not really...

Administrators that needs to fix what is broken (on the users computers) want to fix it with shell-scripts if they can (IMHO)
Also servers are not managed by a GUI. At least not in the Unix/Linux world...
(Imagine administrating 1000 Linux boxes with gui only...)

30 years of wisdome about non-gui management and the possibility to handle a wast amount of computers / sysadmin can't and never will be replaced...

On the other hand, normal users want to click and point to do stuff.

The one does not take away the other...

Seeing the world from another perspective (not your own) can sometimes be a good thing...

or...

A coin has two sides...

---

### Post by jethro10 on 2006-07-03
[QUOTE=jonas_larson]Ooops! Not really...

Administrators that needs to fix what is broken (on the users computers) want to fix it with shell-scripts if they can (IMHO)
Also servers are not managed by a GUI. At least not in the Unix/Linux world...
(Imagine administrating 1000 Linux boxes with gui only...)

30 years of wisdome about non-gui management and the possibility to handle a wast amount of computers / sysadmin can't and never will be replaced...

On the other hand, normal users want to click and point to do stuff.

The one does not take away the other...

Seeing the world from another perspective (not your own) can sometimes be a good thing...

or...

A coin has two sides...[/QUOTE]


I am seeing it from the other perspective. I'm an IT manager and a geek programmer. It's just most people are not, and linux makes them cold. When I tell the wife to pull up a command prompt and type "bla bla bla" 
She just laughs and says how primitive it is.
As long as the masses are like this, were sunk.

J

---

### Post by jethro10 on 2006-07-03
[QUOTE=matthew]Here's why I said that. With a command line shell like bash you only have to learn how to do things once. It doesn't matter if you change your GUI from Gnome to KDE to xfce or something else. ***You can still do the tasks you want to do the exact same way you are used to doing them.*** You can change linux distros from Suse to Ubuntu, Fedora to Slackware, Debian to Arch, it is immaterial. You can still ***do the same tasks in the same manner with little to no need to learn/relearn a process*** (unless you are using something like a package manager, etc. that is distro dependant, and even then you can change within a range of distros that use the same system).

Is the command line the easiest thing to learn for a newcomer? No. However, you only need to learn the info one time as opposed to when you update your OS from Ubuntu Breezy to Dapper and want to do the same things from a GUI (and don't get me started on the switch within the MS world where I went from Dos 2.x to 3.0 to 5.0 to Windows 3.0 to 3.1 to 95 to 98 to Me to XP and had to relearn each time how to do the same basic things).

So I ask you, which is ultimately more friendly to the end-user, having them relearn how to do things everytime you update the GUI or having them learn one thing that will remain true regardless of GUI changes?[/QUOTE]

Sorry, I think your wrong. A GUI effectiley 'reminds' users whats going on Little picture and menu options etc.
A blank command prompt stares you in the face and you type what.... er.. I cant remember.
Talk to more Joe public people who own and use a basic PC. They are scary in their simplicity.
J

J

---

### Post by dmann on 2006-07-03
I don't think that it's really the command line per se that holds back ubuntu or any linux distro for that matter.  It's ease of use that does.

out of the box we can agree that ubuntu is probably almost as easy or easier to use for most daily tasks you can do in windows. (except for dialup, which most users get a downloaded dialer from their ISP and that wouldn't work on ubuntu directly).

Going forward, ubuntu needs to have great support for things like modems, aol (and other ISP specific software), third party programs that you can buy locally to create greeting cards with nifty little graphics and special fonts (you get the picture), games that you can buy from the store, hardware that a best buy geek can sell you that says "compatible with windows xp and Ubuntu 6.06" on the box, iTunes, dvd player software that you can purchase (many people want to do this legally), dvd content creation packages, etc, etc, etc.

This is what a user who gets windows xp expects.  If I buy a pc with windows preloaded on it why in the world (if I'm not a geek) would I put unbuntu on it?  what reason is there for me to change (none).  If I'm an OEM, why would I put unbuntu on a pc?  It might work very well out of the box, but if the user can't go to a store and buy a math program for his/her kids, I'm not going to have many happy customers.

You get the point.


Also, ubuntu doesn't have the development tools that windows has.   Microsoft heavily (very heavily and for good reason) caters to developers.  I can fire up visual studio and write tiny apps that help automate the way my clients work.  There are also many programs out there that people use and purchase for a daily basis for windows - there are almost no commerically available utility or entertainment programs for linux.


And, I've said it before many many times:

Linux/whatever had a huge opportunity to get into the small business sector with a product that can replicate the functionality that Microsoft had with NT4.  A domain, a print server, file server, and ease of use.  I have no idea why Redhat didn't agressively pursue this option when Microsoft officially retired NT4 - why didn't they cater to the thousands who needed a migration path?  tons of these places could have been converted to linux at that point.  Granted the more complex install scenarios maybe not, but IMHO there were many a lost opportunity and this showed imho very poor market strategizing on the part of linux vendors.  Now how easy is it to take market share from microsoft (who makes some damn good products I might add)? 

Dan

---

### Post by aysiu on 2006-07-03
[QUOTE=jethro10]I am seeing it from the other perspective. I'm an IT manager and a geek programmer. It's just most people are not, and linux makes them cold. When I tell the wife to pull up a command prompt and type "bla bla bla" 
She just laughs and says how primitive it is.
As long as the masses are like this, were sunk.[/quote] Then show her how powerful it is. Show her how you can install twenty programs with one command or combine thirty MP3s with one command or convert 100 .jpg files to .gif with one command.

Show her how much faster the command-line is for certain tasks.

[QUOTE=jethro10]It's apparent reading this that the camp is split into 2.

the 1'000 of linux geeks, power users etc = keep command line
for the other billions of normal computer users = no command line.[/QUOTE] I don't see the camp as split in two at all. The original question was about eliminating the **need** for the command-line, not eliminating the command-line **itself**. People just want something to argue about, so they twisted it into whether or not the command-line is a good thing to have around.

No one's arguing to get rid of the command-line--only to add more graphical user interfaces.

---

### Post by w_r_cromwell on 2006-07-03
You may be surprised to learn that the high fat alternative to linux, Microsoft Windows, has some functions that are available only in the command line. Some of those functions have a GUI interface that is incomplete or buggy. Whatever your choice in operating systems it will benefit you to learn how to use the command line. If you are going to do that Linux will offer you more.

Bill

---

### Post by dmann on 2006-07-03
And on a reverse note, Microsoft has their new command line shell coming out with vista I believe, where they took a page from the unix guys and expanded it from what I hear.

[QUOTE=w_r_cromwell]You may be surprised to learn that the high fat alternative to linux, Microsoft Windows, has some functions that are available only in the command line. Some of those functions have a GUI interface that is incomplete or buggy. Whatever your choice in operating systems it will benefit you to learn how to use the command line. If you are going to do that Linux will offer you more.

Bill[/QUOTE]

---

### Post by nocturn on 2006-07-04
[QUOTE=jethro10]I am seeing it from the other perspective. I'm an IT manager and a geek programmer. It's just most people are not, and linux makes them cold. When I tell the wife to pull up a command prompt and type "bla bla bla" 
She just laughs and says how primitive it is.
As long as the masses are like this, were sunk.

J[/QUOTE]

The thing is, you can have her do 99.9% of all tasks with the GUI.  But most of us and maybe you too, are more comfortable with giving instructions in command lines.  It's way to hard to remember in which menu update-manager is when I'm not at my box while 'aptitude install xmms' is easy.

Linux has a big advantage, we're not commercial.  We can do with a niche market share if we need to.  Sure, the more users, the better.  But if we have to become a windows clone to get them, we can and will decline.

If Linux would be dumbed down like that, it would loose it's poweruser base to others (BSD, Minix) and I guess that would include a majority of the developers.

---

