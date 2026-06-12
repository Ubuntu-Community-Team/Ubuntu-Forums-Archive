---
title: "I guess I don't get it"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-11-07
I have been interested in switching to a Linux distro for quite a while now and the other day I took the plunge and installed 7.10 on my Compaq Lappy. I am not any kind of tech expert, I don't know how to "code", no formal training of any sort when it comes to computers. That being said, in the Windows world I find myself pretty competent at solving the little issues that come up from time to time with basic, small-office computer use. Printing, web-aps, email, you know non-techie computer crap. I can normally follow instructions and I know how to google the solution to basic problems. Anyway, for quite a while I have been sympathetic to the idea of open source and free software I followed the rise of Ubuntu on slashdot and similar sites. I switched my office over to OpenOffice and I thought this would be similar. I had to deal with employees that feared change, some small compatibility issues (Remember to save that as a Word file before you send it as an attachment!) I expected a lot of difficulty and a steep learning curve but what I didn't expect was to have so much just not work. The fonts are unreadable, it takes five times longer to boot up, and my wireless card is crippled.  I search these forums and I find that the instructions on the "absolute begginers" threads end to be cryptic and full of jargon. I don't speak the secret code. I don't know the shorthand to help me understand and implement the fixes posted, but most of all I don't know why so much has to be done just to make this usable.

For example, I did a search on slow boot times and I found this solution. What the hell does it mean? Where do I enter the code? Am I supposed to type this all out exactly? Where? Can some of it be cut and pasted? Where? There were two pages of other "absolute beginners" that seemed thrilled with this solution. What is wrong with me? 

 > original

Code:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

now
Code:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70
initrd		/boot/initrd.img-2.6.22-14-generic



Now I do understand about the billions of permutations of equipment and the difficulties of making everything work but this stuff if basic. After installing the latest version websites should be readable and it shouldn't take five times longer to start up I don't even know who I am complaining too. Certainly not all of you selfless people who are so willing to take time out of what you are doing to answer my stupid questions. I do not mean to sound like a petulant little kid. I guess I just wanted Linux to be something it wasn't. I had visions of switching my office over to Linux and having my mom install linux on her old computer and spreading the gospel of Linux to other non-tech computer users and that is just not going to be possible.

---

### Post by steveneddy on 2007-11-07
Maybe you should take some time to learn the OS instead of comparing it to the windows world. The issues you address all have answers and solutions, but you can't find the terminal? 

Applications --> Accessories --> Terminal

When you buy a new car, don't you start clicking all the knobs and buttons jst to see what they are gonna do? You should do the same with your new OS. Click stuff and look around. You are just in the beginning stages of discovery, so feel free to kick the tires a little.

It's not that hard, you just have to accept something that is a little different than the OS you were used to running before.

Have patience. And something to think about. If your VCR is still blinking 12:00, Linux may not be the right OS for you.

:popcorn:

---

### Post by ARhere on 2007-11-07
> **steveneddy said:**
> ...If your VCR is still blinking 12:00, Linux may not be the right OS for you. <---LMAO!

I am always happy to see a "non-techie" realize there are other "hammers" in the tool box besides Windows.

It sounds like you need to educate yourself a little about Linux first, then Ubuntu.  Please go pick up a "[Pocket Administrator's]("http://www.amazon.com/Linux-Administration-Beginners-Steve-Shah/dp/0072122293")" guide to Linux, OR "[Linux for Dummies]("http://www.amazon.com/Linux-Dummies-6th-Dee-Ann-LeBlanc/dp/0764579371")".  The later is **not** a pun because it is actually a very good book.  You need to learn some basics first or you may find yourself getting to frustrated to care.

I did a quick google search on "Linux guide for beginners" and came up with a **lot** of resources.  Please run through some of the exercises found in these books using your Ubuntu distro and you will find your Ubuntu experience pleasant.  The [Official Ubuntu guide]("http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136/ref=pd_bbs_sr_1/104-2712625-5567114?ie=UTF8&s=books&qid=1194496403&sr=1-1") is also well written and I think you will enjoy it.

*Also*, most local State colleges offer cheap and fun "life courses" you can take on Linux.  Give it a try!

Luck
-ARhere

---

### Post by boriquajake on 2007-11-07
> If your VCR is still blinking 12:00, Linux may not be the right OS for you.

Dude, don't be a dick.

Yes I know where the terminal is, what I don't know is if that block of instructions is to be simply cut and pasted directly into it .I tried that  and I got nothing. Are there intermediate steps? That was just one example there were many others. I felt like there is some basic knowledge that everyone else on these forums takes for granted but that normal :) people do not have.

What I would like to know is if there exists a comprehensive tutorial to the basics of Ubunu use? Something that would explain the basic principles of Linux layout and navigation to someone that uses computers as a basic  productivity tool for work. My intent in switching was to find something better than Windows, not to pick up a new hobby.

---

### Post by 3rdalbum on 2007-11-07
You've been using Ubuntu for, what; 8 days? (UF join date is November 2007).

Fiddling around with your boot process is not something an 8-day-old Ubuntu user should be doing. Most people wouldn't even consider doing it on Windows even if they've got 5 years experience with Windows.

Don't worry about that particular piece of code you were given. It goes into the file /boot/grub/menu.lst, but it will not make the boot process noticably faster. In fact, it will probably make it slower.

EDIT: As for finding out how to use the command-line, probably the best teacher is to read tutorials on all sorts of things that are posted on the forums. I always try to explain what each command means, and lots of other posters do the same. And if there's a particular command name (the command name is the first word in the command) that you don't understand, you can go to the terminal and type "man " and then the name.

For instance, if you didn't know what "dmesg" means, you could type:

```
man dmesg
```

And it would tell you that the command lists messages that the kernel sends to help you figure out what has happened during your boot process. That's just an example of a command, but you can use pretty much any command name and get this sort of information.

---

### Post by ARhere on 2007-11-07
By the way, we never answered your original question.

The "code" you see is the contents of the **menu.lst** file which controls how your OS boots.  It is located at "**/boot/grub/menu.lst**"  You can use a graphical editor to view/edit this file by opening your terminal and typing...
```
gedit /boot/grub/menu.lst
```
I suggest you do not mess with this file until you have learned a little about your OS.  Linux  is easy to break, easy to fix; where Windows is hard to break, but hard to fix!

Just for fun, another phrase I heard was.  
"Windows is easy to learn, hard to use.  Linux is hard to learn, but easy to use."

Cheers,
-ARhere

---

### Post by aysiu on 2007-11-07
Can you link to what tutorial gave you those "instructions"? I'm surprised they wouldn't explain what the code is and where it lives or how to modify it.

That code you see is part of a text configuration file: /boot/grub/menu.lst

It's a text file called menu.lst, and it lives in the grub directory, which itself is inside of the boot directory.

If you find yourself editing system files a lot, you may want to create a launcher or keyboard shortcut for the terminal command ```
gksudo nautilus
``` This will open the graphical file browser with administrative privileges. For now, though (before you create a launcher or keyboard shortcut), just press Alt-F2 (this is the equivalent of Windows-R in Windows). In the run dialogue, type ```
gksudo nautilus
``` When you're prompted for your password, enter it.

Once you're in the graphical file browser, navigate to /boot/grub

Back up the menu.lst file before you edit it. Then double-click it to edit it.

Replace the original text with the new text, save, and exit.

Reboot.

---

### Post by dwhitney67 on 2007-11-08
> **boriquajake said:**
> Dude, don't be a dick.

Yes I know where the terminal is, what I don't know is if that block of instructions is to be simply cut and pasted directly into it .I tried that  and I got nothing. Are there intermediate steps? That was just one example there were many others. I felt like there is some basic knowledge that everyone else on these forums takes for granted but that normal :) people do not have.

What I would like to know is if there exists a comprehensive tutorial to the basics of Ubunu use? Something that would explain the basic principles of Linux layout and navigation to someone that uses computers as a basic  productivity tool for work. My intent in switching was to find something better than Windows, not to pick up a new hobby.

Many newbies to Linux (and mainly Ubuntu) use the music players, web browsers, compose a document or two using Open Office, etc., and forget about the intricacies of the OS itself.  Details as to how it works is either beyond their comprehension or beyond their level of interest.

If you want to continue shelling out money for M$ and other retailers who want to protect your system from viruses, malware, and the like, then go back to Windoze.  I don't think anyone in the Linux community will give a damn.

With your opening remark in your follow-up post (above), I would appear that it was you who is being the "chingada".  Somebody was trying to give you constructive advice, and you took it as a personal attack.  Makes me wonder WTF are you doing on this forum.  This is a place to learn; not to quip when someone understands and points out your obvious limitations, and then provides advice on how to better yourself.

If you want to learn Linux, then read books, tutorials, etc.  Don't whine that you haven't a clue about Linux and seem left behind.  In the beginning, everybody was in your place.  Many have learned Linux by expanding on the base system to include their personal touches; others merely continue to use it pretty much as it came from the initial installation disk.  Hobbies are good way to enrich one's life; remaining ignorant is not.

---

### Post by niteshifter on 2007-11-08
Ahem ... I'll try to be a wee bit more helpful than some of what you've encountered so far ...

To answer the questions on the “solution” you found and posted: It's not a solution, it's the result of someone's probing about – looks like a portion of the file menu.lst, a part of the GRUB boot loader. Specifically, what is being done there is to turn off the boot splash screen and permit the boot-time messages to appear ... and fly by on the screen. 

From where I stand, that's not particularly useful. This is a better way to diagnose boot-time problems:

1. Open a Terminal (Applications / Accessories / Terminal)
2. Then type the below in:

```
dmesg > bootmsgs.txt
```

3. Post the file bootmsgs.txt here, I or somebody else will be glad to help.

Cutting and pasting can be done within the Terminal, the keystrokes are Shift+Ctrl+C (to copy) and Shift+Ctrl+V (to paste).

If you are curious as to what “dmesg” is, type the below into a Terminal:

```
man dmesg
```

Another thing is that 7.10 is just a couple of weeks out. It's a bit buggy. It happens – notice the lack of a mad rush to Vista in the corporate world, people are waiting for the first Service Pack to appear (lesson learned with XP). You might consider using the 7.04 (Feisty) or 6.10 (Edgy) versions instead.

---

### Post by aysiu on 2007-11-08
> **dwhitney67 said:**
> 
If you want to continue shelling out money for M$ and other retailers who want to protect your system from viruses, malware, and the like, then go back to Windoze.  I don't think anyone in the Linux community will give a damn. I give a damn, and I'm in the Linux community.

---

### Post by linuxlizard on 2007-11-08
> most of all I don't know why so much has to be done just to make this usable.

It's because of your hardware. You are just "unlucky". I've pieced together several computers for myself, family and friends out of a combination of new and used parts, and I'm always amazed at how many problems people have setting stuff up, because on my hardware, I've been lucky enough that it just works. And I think that's the majority of the time for most users, but you don't hear about the ones that work too often on the forums- people come here for help with what doesn't, after all. However, a couple of times I've helped friends who had problems with ubuntu- a "trick" you can try is to download several distros and try them all on your hardware- sometimes what doesn't work well with ubuntu will work great without manual configuration with pclinuxos, or suse, or fedora core, or mandriva, or freespire. Wierd but true- some hardware is setup better on some than on others. 

You can also check out what hardware works well and what doesn't with google. Some video cards don't work as well as others, and certain brands of wireless cards are often a snag as well.

Bottom line - the amount of stuff that you have to do to make ubuntu usable depends greatly on what kind of hardware you have.
 
Sorry you've been unlucky with yours.

---

### Post by saxofoner on 2007-11-08
First of all, aysiu, you're awesome.  Your webpage is like God, but in HTML form.  

Anyway, boriquajake (how the hell do you say that?), don't give up.  Wireless cards hardly ever work on first installs, and there are easy fixes.  Just be specific like:
--------
Computer Model (if not homebuild)
Wireless Card Model
Linux Version + Anything you've already messed with 
--------
Then we can help you.  I started using Linux (Dual Booting) about a year and a half ago.  I've felt part of this community since the day I registered.  But, I felt totally lost (but also amazed) for a few months, too.  Terminal?  Where's that?  I have to memorize the functions of .., cd, ls, man, the locations and purpose of /usr and /lib?   Oh and the 3 times I've reinstalled from scratch?  That's always fun.  

But ~1.5 years later, and I feel like a 1337 h4x0r== I can compile from source without a guide, I can fix most problems, I know all kinds of stuff off hand, like where is my conf file?  oh yeah, /etc/X11/xorg.conf.  You'll learn.  Don't give up.  Feel the sense of community.  Hell, it's called "Ubuntu" for a reason.  


As far as technical stuff goes, why are your fonts unreadable?  That could mean you don't like the system fonts, your resolution is messed up, you need glasses, we need more detail.  Post a screenshot.  Help us help you.
And like I said before, tell us about your wireless card.  

We WANT you to have a pleasant experience with an operating system far superior to anything else you've used.  I actually get a sense of gratification from helping complete strangers enjoy their computers, and thus their daily routines, more thoroughly, and in a short period of time, you will too.  Just stick with it.  To continue the car analogy, you wouldn't return a used 2004 sports car just because the brakes were a little too touchy.  You'd take it to the mechanic.  Except with Ubuntu, you've got a listening audience of thousands of the friendliest, warmest, most dedicated mechanics in the world waiting around to take time out of *their* daily lives to help you, for free.  Beat that, Microsoft!

P.S. I'm not a fan boy.  I'm writing this from an iBook running OSX, and I still dual boot with Windows because there are *gasp* some things Ubuntu can't do, besides get viruses, like update my iriver's firmware and... well, that's about it.  :)


Welcome to Linux.

---

### Post by keyboardashtray on 2007-11-08
Wow, why are some people being so harsh to this guy?

Seriously, that was a way mild opening post for someone who sounds genuinely frustrated but giving it a chance. I've seen people come in with fists swinging "Ubuntu suxx the gamez are terrible they look like pong  Windowz rulez"  and get treated better than that.

I'm sorry that I don't have any genuine advice for you, all I can say like others have said, you were just one of the unlucky ones with hardware issues. Hopefully you'll get some good help. Yeah, I know its rough when you get handed a line of code your first couple days to stick in the console or some random config file. It's easier when fortune lets you ease into that console stuff.

Edit: BTW that sounds cool how you switched your office to openoffice.org. I sometimes wonder how many people are really implementing this stuff at the professional level. I know what its like to feel like an old pro with computers, above average, then switch and feel like you are starting over.

---

### Post by digital_sabotage on 2007-11-08
...look for books and/or tutorials online that keep it simple at first until you get the basics down pat ...you won't learn it overnight ...guaranteed  ...no tutorial can do that for you  ...the wisdom will come with time as long as you enjoy the learning curve ...be prepared to troubleshoot the problems you come across and make sure you understand what you are doing and why you are doing it or you won't learn  ...knowledge + understanding = wisdom 

...i think you can compare the two OS's as you would two languages ...windows, for most, is the native language  ...not any easier to learn  ...just learned first  ...so the transition to linux seems more difficult

...but just as languages differ in that some enable you to express yourself better ...the same is true between windows and linux   ...i think once fluent a person can "express" themselves better with linux

...in my humble opinion you should become at least semi-fluent before relying on it as a dependable alternative for your business

...mess with it at home and in non-critical scenarios for a few months and then see how you feel  ...keep the faith  ...rome wasn't built in a day:-)

---

### Post by DawnDisciple on 2007-11-08
> **boriquajake said:**
> . I had visions of switching my office over to Linux and having my mom install linux on her old computer and spreading the gospel of Linux to other non-tech computer users and that is just not going to be possible.

I know just how you feel, I am having it hard to, I am no dunce and usually pick stuff up quite quickly, but trying to figure out what linux is all about is like getting dumped in another country where no one speaks your language and does everything completely different you what you are use to, twice now I have reached for the uninstall key but then decided to battle on.  These threads are for the absolute beginner, I dread what one would be like for the absolute expert.:)

What we need is a forum for absolute new born  babes.

---

### Post by boriquajake on 2007-11-08
> **keyboardashtray said:**
> Wow, why are some people being so harsh to this guy?

Seriously, that was a way mild opening post for someone who sounds genuinely frustrated but giving it a chance. I've seen people come in with fists swinging "Ubuntu suxx the gamez are terrible they look like pong  Windowz rulez"  and get treated better than that.

I'm sorry that I don't have any genuine advice for you, all I can say like others have said, you were just one of the unlucky ones with hardware issues. Hopefully you'll get some good help. Yeah, I know its rough when you get handed a line of code your first couple days to stick in the console or some random config file. It's easier when fortune lets you ease into that console stuff.

Edit: BTW that sounds cool how you switched your office to openoffice.org. I sometimes wonder how many people are really implementing this stuff at the professional level. I know what its like to feel like an old pro with computers, above average, then switch and feel like you are starting over.


Thank you so much, man. You and several others understand. I will soldier on, but first I think I am going to buy a book.

---

### Post by mivo on 2007-11-08
> **boriquajake said:**
> Thank you so much, man. You and several others understand. I will soldier on, but first I think I am going to buy a book.

Ubuntu is developing relatively fast, so books always have the disadvantage of being "behind" the current state of the OS. The forum here is really a very good resource, and you will find many links to other good resources on here. It is somewhat time-consuming, but may yield better, more current results.

Welcome to the Linux community, by the way. It's good to see that you are going to stick with it. The beginning can be rough -- but do hang in there, it is worth it. :)

---

### Post by bmartin on 2007-11-08
> **boriquajake said:**
> I have been interested in switching to a Linux distro for quite a while now and the other day I took the plunge and installed 7.10 on my Compaq Lappy. [snip] in the Windows world I find myself pretty competent at solving the little issues that come up from time to time with basic, small-office computer use. Printing, web-aps, email, you know non-techie computer crap. I can normally follow instructions and I know how to google the solution to basic problems. [snip] The fonts are unreadable, it takes five times longer to boot up, and my wireless card is crippled. [snip] I search these forums and I find that the instructions on the "absolute begginers" threads end to be cryptic and full of jargon. I don't speak the secret code. I don't know the shorthand to help me understand and implement the fixes posted, but most of all I don't know why so much has to be done just to make this usable.
I don't know why many of the other people responding here have been so rude. Most of the help you'll find on here is of pretty good quality.

You're obviously interested in Linux, willing to use Google to find help, and persistent. It shouldn't take too long to work your problems out.

First, get a pen and paper. You'll need these to 

The crippled wireless card and the slow boot time are likely related issues. I used to have that problem. While the computer is loading up, you can press CTRL+ALT+F1 to see what's happening. My guess is that it's hanging up at the step that gets your (wireless) network adapter ready. Next time you reboot, try looking at the messages there and see if that's the problem, or if it's hanging at something else.

It's easiest to find what network adapter you have by using the terminal. Open it up and enter the following line of text (please copy and paste it to avoid any errors), then post the result here:
```
lspci -nn | grep -i -e ethernet -e network
```
From there, I can direct you on how to get it working better. Wireless is still a pain in Linux. I'm working on that problem myself (i.e., I'm writing software to make the process easier).

The fonts problem could be related to the screen resolution. I recommend using Google to solve that problem.

Linux can be a pain to set up. Generally speaking, once it's set up, there's little maintenance to be done.

---

### Post by philinux on 2007-11-08
Welcome to ubuntu. It seems a stiff learning curve at first thats true but its a much better OS once you know your way round it.

Cut and paste is your friend. Don't bother retyping these commands at first chances are you'll get a typo.

---

### Post by AndyCooll on 2007-11-08
A good place to begin is the starter guide link in my signature.

:cool:

---

### Post by LizardKing73 on 2007-11-08
> **aysiu said:**
> I give a damn, and I'm in the Linux community.

Here, here.

The last time I checked this forum was for learning to use Linux, Not to attack the hell outta newbies that dont get what their doing and Steveneddy that was EXACTLY what u did. If u couldnt go without posting the VCR remark then prehaps u shouldnt be posting at all. I'm still fairly new to Linux, REALLY new to Ubuntu but I can tell u that I wouldnt want to learn from someone that says things like that, dont forget u started as a newbie to. Most people just playing around with Linux can find and activate the Terminal, its knowing WHAT TO DO WITH IT.
Oh and my VCR still flashes 12:00 not because I dont know how to set it (I do) but because I really dont give a damn.

As for u boriquajake, maybe u should have just asked "How do I do this?" rather than blowing in the door and complaining about how u installed Linux and now this and this and that doesnt work and that is such a disappointment because u wanted to change to Linux so bad and it wasnt what u thought it would be.
In all that time u were watching the rise of Ubuntu and thought about changing to Linux did u not study one thing about the OS itself? Not trying to be a dick just merely asking.

If u really want to learn about Linux and how to use it then the best advice I can give u is FIRST approach this forum as someone that wants to learn about Linux instead of attacking the OS for not doing the things u want it to....because IT CAN, Linux is an awesome OS u just have to learn how to get it to do what u want, unlike windows Linux rarely does anything without being told to first, no bloated .dll's that auto configure everything for u, nope Linux is MUCH more hands on. To me thats part of what makes it so much fun I actually like typing out the commands and watching it take off.....is that strange??? Ah who cares?
SECOND read anything and everything u can get about Linux ESPECIALLY the flavor u'r using, in this case Ubuntu. U dont have to learn how to write "code", its just learning the Linux Commands and really their not all that hard, Check the net, their all over the place.
And THIRD...Ignore people like Steveneddy, u know the people...the ones that know how to make their Linux Boxes do what they want them to and forget how they felt the first time they sat down at their newly loaded Linux machine with a look on their face like a Monkey staring at a Math Problem. If their gonna run u down for being new then u dont want their help to begin with but on the other hand YOU have to be more willing to actually ask for help instead of whining and crying about all the things u cant do

......yet.

---

### Post by K.Mandla on 2007-11-08
And on that note, let's call this thread "closed."

---

