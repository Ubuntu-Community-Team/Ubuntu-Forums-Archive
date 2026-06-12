---
title: "Annoyed begginer questions."
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by theriddlen on 2010-04-30
I just installed 10.04 on my Macbook Pro (5,5), but as i expected, nothing changed since my last try to use it, when 8 came out. Still everything is made with huge amount of pure fail. But, i will give it some time.
I have some questions:

1. When i tried to install Opera in this window "Package Installer" status was "Error: Dependency is not satisfiable: libqt3-mt (>= 3.3.4)" How to fix this thing? BTW: Huuuge fail, it is. I never thought that there may be problem with installing browser. When i tried 8, i have successfully done that.

2. Is a way for touchpad to work almost as it does in OSX? At least i want it to scroll with two fingers.

3. Why this "Rythmbox Music Player" (thats what i call a catchy name - iTunes is so hard and sophisticated) after clicking it just pops up and after half of second disappears/turns off?

4. How to turn on my airport card on? This is weird. I can't use my WiFi, but my mobile broadband modem works like magic.

5. After i choose Ubuntu in efi boot menu, it shows me some kind of linux boot menu, and i have to choose what i want again. Is there a way to make it work normally?

---

### Post by kosumi68 on 2010-04-30
Hello theriddlen,

If you are unhappy with Ubuntu at no charge, there are two other operating systems, one called OSX and one called Windows, that you may buy at an affordable price to get a system working with fewer glitches from the start.

If you still like Ubuntu or the idea of free software, you will find that there are a lot of people in this community willing to help you to contribute, so that the experience becomes smoother for the next beginner.

---

### Post by theriddlen on 2010-04-30
I don't want to be rude, but you did not helped me at all. I have both OSX and Windows, and i use them everyday, but i like to taste something new. And the point of my thread is i that need help in using Ubuntu - not choosing OS.

Even tho last questions remain unanswered, i have one more to add:

6. How to make Alt+Tab work like in other systems? I want it to switch between every proogram i have, not only some. Now im using some utility that reminds me SVN to download something, but i see only Firefox.

EDIT:

7. Is there way turn keyboard back light on?

---

### Post by jamesey on 2010-04-30
> **theriddlen said:**
> 

1. When i tried to install Opera in this window "Package Installer" status was "Error: Dependency is not satisfiable: libqt3-mt (>= 3.3.4)" How to fix this thing? BTW: Huuuge fail, it is. I never thought that there may be problem with installing browser. When i tried 8, i have successfully done that.

3. Why this "Rythmbox Music Player" (thats what i call a catchy name - iTunes is so hard and sophisticated) after clicking it just pops up and after half of second disappears/turns off?

5. After i choose Ubuntu in efi boot menu, it shows me some kind of linux boot menu, and i have to choose what i want again. Is there a way to make it work normally?

1. Go into synaptic package manager and look for libqt. check the box to install it. then try installing opera again.

3. You sure Rhythmbox isn't minimized to the panel?

5. You're seeing the Grub boot menu. There are ways to make the countdown not happen. check section 5, booting grub here: [http://ubuntu-install.blogspot.com/2009/11/grub-2-basics-install.html](http://ubuntu-install.blogspot.com/2009/11/grub-2-basics-install.html)

---

### Post by johnystevenson on 2010-04-30
the 2 finger scroll

system>preferences>mouse>touchpad>(and tick)two finger scrolling
give it time

---

### Post by theriddlen on 2010-04-30
Thanks for answers!


After reboot rhytmbox started to work, and drivers notification popped up on status bar (with WiFi drivers). Unluckily Opera looks terrible, and the fonts look like something big stepped on them, but i still have Firefox. 

Everything starts to look better! Really, Ubuntu dev team should work on first impression - it is terrible!

---

### Post by Dukenukemx on 2010-04-30
> **kosumi68 said:**
> Hello theriddlen,

If you are unhappy with Ubuntu at no charge, there are two other operating systems, one called OSX and one called Windows, that you may buy at an affordable price to get a system working with fewer glitches from the start.

If you still like Ubuntu or the idea of free software, you will find that there are a lot of people in this community willing to help you to contribute, so that the experience becomes smoother for the next beginner.

Unhappy with Ubuntu is feedback.  If you want to produce something people wanna use, you listen to it.  Trust me, there's a lot of that going around.

Also, I can't help but wonder why anyone would suggest to go back to OS X/Windows in a Ubuntu forum?  It's not like he asked if he should use OSX Windows or Ubuntu.  

If you want to make the experience for the next beginner a good one, I suggest not demoralizing them.  Ubuntu doesn't need a scare crow in their forums to ward off beginners.

---

### Post by christopherhaywood on 2010-04-30
Yup plenty of bugs in this one still - it's definitely not apple friendly. If you're a new user using Sun's free VirtualBox system and 10.4 on a MacBook you are greeted with the following problems:

1) Screen Res is fixed at 800x600 max, no options to increase it. [Had this problem on 9, and it took me a few mins of forum searching and the omnipresent terminal to fix it by editing xconfig files - this is NOT user friendly]

2) Trackpad dual touch scrolling does not work - and there is no touchpad option in the system file.[brand spanking new problem! No idea what to do about this!]

Any ideas?

As an aside Keyboard accents and layout in "mac" mode is still essentially PC mode. You need to remap the entire keyboard if you want commands to be as they are on the mac. This is a bit of a bummer too.

---

### Post by jamesey on 2010-04-30
a two finger scroll script
[http://www.reddit.com/r/Ubuntu/comments/byi7c/in_case_anyone_wants_two_finger_scroll_in_lucid/](http://www.reddit.com/r/Ubuntu/comments/byi7c/in_case_anyone_wants_two_finger_scroll_in_lucid/)

---

### Post by blueridgedog on 2010-04-30
> **theriddlen said:**
> I don't want to be rude

Not being rude sometimes takes work, and an open mind.  

Linux and Mac are on opposite ends of the OS spectrum.  In theory, one you can't get to the internals of and the other you occasionally have to.  

To make Ubuntu work, you have to picture yourself as part of the solution.  Your language, though probably humorously intended with the reference to the currently in vogue use of "fail" when you are comparing an open source operating system release on the day of its release with a proprietary OS, creates a difficult environment to provide answers in.

To get around this, try posting your questions not from the perspective that it is a failure if it isn't to your expectations out of the box.  Here is your original post rewritten with that in mind:

> I just installed 10.04 on my Macbook Pro (5,5).

I have some questions:

1. When i tried to install Opera in this window "Package Installer" status was "Error: Dependency is not satisfiable: libqt3-mt (>= 3.3.4)" How can I solve this?

2. Is there a way for touchpad to work almost as it does in OSX? In OSX you can scroll with two fingers.

3. When I lauch "Rythmbox Music Player" it just pops up and after half of second disappears?  How can I tell what is wrong?

4. I am not certain my wireless card is supported.

5. After i choose Ubuntu in efi boot menu, it shows me a linux boot menu, and I have to choose again. Is there a way to make it skip this step?

This is exactly what you stated, but with the words that imply it "should" have worked a certain way to start with removed.  In many ways this is what Ubuntu is all about...being open.

A good read along these lines is the classic:

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

---

### Post by Yarui on 2010-04-30
> **blueridgedog said:**
> 

A good read along these lines is the classic:

[http://www.catb.org/~esr/faqs/smart-questions.html]("http://www.catb.org/%7Eesr/faqs/smart-questions.html")


I would also recommend everyone read over this page.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Don't let the title mislead you.  It isn't meant to be an insult to windows (or mac) users.  It just gives some explanation for why windows and mac users are often unhappy with Linux and explains why Linux users are often unwilling to help those who post rude comments.  It's a good read regardless of what OS you prefer.

---

### Post by MartinFernando1993 on 2010-04-30
I don't understand why everybody rants on Ubuntu. I know it's hard at first, but it's quick to understand and if you need more help look it up on youtube. It's *that* easy and user friendly:P:guitar:!

---

### Post by christopherhaywood on 2010-05-01
It's probably good to clarify at this point that it's unlikely that anyone here is trashing Ubuntu. We all love the idea of the OS. I think the issue with trawling through sites highlighting the big differences between linux and the big-boy systems is that they often aren't in line with Ubuntu's sales pitch. 

"Fun, friendly and easy to use"

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) explains that it is often neither fun nor easy to use. I found that the end results with 9.04 were perfectly useable, although I wouldn't draft legal documents in it, but it took me upwards of 13 hours to get there.

Threads on this board will always have this edge to them, because many people do want to get the heck off any system associated with Bill Gates or Steve Jobs!

I'll probably get around to making Linux work for me again as 10.4 is a clear improvement. However, it's still nowhere near being "easy to use", until the terminal is only necessary for linux pros to tweak and customise, it will always be a bit of a sod to get going. Here's hoping that a few months of board activity pulls up a solution, I'm sure LL is going to be the most popular edition yet.

---

### Post by sastusbulbas on 2010-05-01
> **MartinFernando1993 said:**
> I don't understand why everybody rants on Ubuntu. I know it's hard at first, but it's quick to understand and if you need more help look it up on youtube. It's *that* easy and user friendly:P:guitar:!

LOL, except you cannot view video on the internet with Ubuntu!

---

### Post by theriddlen on 2010-05-01
I don't know why, but when i say something bad about Linux, it's users take it as personal insult. I said "i don't want to be rude" - to this guy who said something totally off the topic. Why i can't be "rude" for OS?

And back to topic:

Why something like that happens?
[IMG]http://img202.imageshack.us/img202/2783/ehh.png[/IMG]
Double battery (only one works, but why there is exclamation mark, when battery is full?), double bluetooth (same, only one works).

How to log in to Ubuntu One? I mean, i have account there, but in OS i just see "unknown" and there is no "Log In" button.

And last question: why when typing, every 15 seconds of writing something happens - half of text disappears, text i write moves somewhere else, things like that?


EDIT:

Just noticed, that speakers don't work on ubuntu. Any idea how to turn them on?

EDIT: 

Argh, i just deleted url bar with buttons in Firefox, and i don't see any way to turn it on...

---

### Post by untmdsprt on 2010-05-01
> **theriddlen said:**
> I don't know why, but when i say something bad about Linux, it's users take it as personal insult. I said "i don't want to be rude" - to this guy who said something totally off the topic. 

You weren't being rude, and the guy was totally off topic. Some people are just trolls, others can't or don't read the question and reply because they like to "hear themselves speak." etc.


> **theriddlen said:**
> 

EDIT:

Just noticed, that speakers don't work on ubuntu. Any idea how to turn them on?
Install the ALSA mixer and check to see if the headphones has been muted. It's usually the case with me.

Ok, some major fails with me ;):

I'm using a Macbook 2,1, and the trackpad is way too sensitive to type properly. I'm typing and it's so jumpy that the cursor is way off somewhere else. What is the easiest way to get this fix? Step by step instructions would be nice.
 
The new Apple bluetooth (wireless) keyboard can be seen, but I can never pair it and be able to use it. This is their new 2 battery model.

Thanks!

---

### Post by theriddlen on 2010-05-01
Thanks, sound works!
I think Ubuntu will stay longer on my macbook. It makes better use of apple features than windows.


Is there any Genius plugin for rhytmbox?

And what is new ubuntu font? This new one, not one with childishly rounded corners.

---

### Post by blueridgedog on 2010-05-01
> **theriddlen said:**
> 
Is there any Genius plugin for rhytmbox?


Amarok has something like that and was rated as the best music player this month in the Linux Journal.  You can install it with apt get or Ubuntu Software Center.

[http://amarok.kde.org/](http://amarok.kde.org/)

---

### Post by simonlugi on 2010-05-01
theridden For what its worth, I am not very computer literate so cannot offer technical advice, however would encourage you to hang in there with the linux os. I changed a fews years ago because I purchase a new computer with Vista (need I say more). Expect a brief learning period but once you start understanding the layout, I am sure you will come to appreciate the positive differences compared to windows. In my opinion OS's like Ubuntu are already better than windows, there just isn't the range and quality of apps (programs) available to run on Linux OS's.

---

### Post by DarkestRitual on 2010-05-01
> **christopherhaywood said:**
> Yup plenty of bugs in this one still - it's definitely not apple friendly. If you're a new user using Sun's free VirtualBox system and 10.4 on a MacBook you are greeted with the following problems:

1) Screen Res is fixed at 800x600 max, no options to increase it. [Had this problem on 9, and it took me a few mins of forum searching and the omnipresent terminal to fix it by editing xconfig files - this is NOT user friendly]

2) Trackpad dual touch scrolling does not work - and there is no touchpad option in the system file.[brand spanking new problem! No idea what to do about this!]

Any ideas?

As an aside Keyboard accents and layout in "mac" mode is still essentially PC mode. You need to remap the entire keyboard if you want commands to be as they are on the mac. This is a bit of a bummer too.

The 2 finger scrolling was activated for me happily after I installed Guest Additions in virtual box, which also let me go to 1280x800. I run Ubuntu with 2gigs of RAM and 128MB of VRAM, and i'm basically splitting my macbook 2ghz core 2 duo aluminum into 2 equal machines, each capable of running its own OS. I've got 10.04 64 bit installed...

Hope this helps.

---

### Post by Dukenukemx on 2010-05-02
I love how I'm finding new problems with Lucid.  Just for once I wish I could fix something while avoiding the need to use Terminal.  

Ubuntu 9.10 for PPC
1.  Wifi doesn't come back after sleep.  FIXED
2.  No batter meter appears.  FIXED
3.  No TouchPad tab under mouse properties.
4.  No flash.
5.  Can't see network printer (HP Photosmart 2570).
6.  Can't connect to some Windows PCs.

Ubuntu 10.04 for PPC
1.  No Batter meter appears.  FIXED
2.  No 3D drivers loaded up for ATI 9600.  FIXED
3.  Tries to hibernate when set to sleep.
4.  Screen doesn't sleep.
5.  No TouchPad tab under mouse properties.
6.  Can't see network printer (HP Photosmart 2570).
7.  Hibernate doesn't resume (black screen).  --Don't think this was ever meant to hibernate
8.  Can't connect to some Windows PCs.

If anyone can help me with my remaining problems that would be great.

---

### Post by linuxopjemac on 2010-05-02
with cups and samba you should be able to connect to printers and windows machines. Check Google.

---

### Post by untmdsprt on 2010-05-03
> **Yarui said:**
> I would also recommend everyone read over this page.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Don't let the title mislead you.  It isn't meant to be an insult to windows (or mac) users.  It just gives some explanation for why windows and mac users are often unhappy with Linux and explains why Linux users are often unwilling to help those who post rude comments.  It's a good read regardless of what OS you prefer.

I thought the article you suggested was a very good read, and makes me like Linux even more. I HATE Windows with a passion!! I love my Mac, and won't ever give it up, but it has come a time where I need to try something different. :D

I've tried X11, Fink, or Macports on the Mac, and I hate having to compile anything and it not work. I've spent hours on trying to get Gnome to run under X11 on the Mac. The only time it did work is when I used Fink, and installed the binaries.

I think most of the questions that I've posted here are because I don't fully understand how things work, and also most people who are using Macs, aren't using the same Mac I am. Things work for them, but they aren't working for me. Why? What can I do to fix it?

The biggest annoyance for me is the trackpad. I would love to find other users who have the same model as me tell me what they did to get it to stop being so damn sensitive.

I have since put Ubuntu on my bf's Thinkpad, and am having a much better experience with the OS. I'm beginning to think that generic pc parts are better than trying to install it on a Mac.

---

### Post by oswaldkelso on 2010-05-03
> **untmdsprt said:**
> 
The biggest annoyance for me is the trackpad. I would love to find other users who have the same model as me tell me what they did to get it to stop being so damn sensitive.


[http://wiki.debian.org/SynapticsTouchpad](http://wiki.debian.org/SynapticsTouchpad)

---

### Post by Dukenukemx on 2010-05-03
> **linuxopjemac said:**
> with cups and samba you should be able to connect to printers and windows machines. Check Google.

Cups was installed but samda wasn't.  Checked again and it still doesn't see my Windows Machines.  It can see the WORKGROUP but it gives the error "failed to retrieve share list server".

Also, my printer can be accessed through 192.168.1.3, which gives a webpage with all information from it.  I type that in in FireFox and it can't find it, but 192.168.1.1 from the router pops up.  Can't ping my printer either.

---

### Post by linuxopjemac on 2010-05-03
If you hook that printer up to a Linux computer, it would be immediately recognised. It can be accessed from the CUPS site
computer_network_address:631

I have no experience with SAMBA. I will give a pic of my HP 4P connected to a Linux server in my bedroom:

---

### Post by Dukenukemx on 2010-05-03
If I hook it up directly, yea sure, but I need it as a network printer.  

Oddly enough, if I go to "Places/Connect to Server" it will actually connect and I can see the shares.  As long as it can do that, I'm happy.

Actually, now I think of it, I set my router to block wifi by mac address.  I'm thinking I might have deleted the mac address of my printer.  I'll check that out later.  

I also found some stuff from Synaptic Package Manager.  Powerpc-utls, which helped me disable double tap on my touchpad.  It came with a tool called trackpad.

Then I installed wmbatppc, a Battery monitor for Apple G3/G4 ibooks/powerbooks.  No idea if it works as I've forced a battery meter with pmu_module.  

Finally pmud, a Apple PowerBook power management daemon.  No idea if it fixed any of my power management stuff.  Installed it for the heck of it.

---

### Post by breimer273 on 2010-05-04
> **Dukenukemx said:**
> I love how I'm finding new problems with Lucid.  Just for once I wish I could fix something while avoiding the need to use Terminal.  

Ubuntu 9.10 for PPC
1.  Wifi doesn't come back after sleep.  FIXED
2.  No batter meter appears.  FIXED
3.  No TouchPad tab under mouse properties.
4.  No flash.
5.  Can't see network printer (HP Photosmart 2570).
6.  Can't connect to some Windows PCs.

Ubuntu 10.04 for PPC
1.  No Batter meter appears.  FIXED
2.  No 3D drivers loaded up for ATI 9600.  FIXED
3.  Tries to hibernate when set to sleep.
4.  Screen doesn't sleep.
5.  No TouchPad tab under mouse properties.
6.  Can't see network printer (HP Photosmart 2570).
7.  Hibernate doesn't resume (black screen).  --Don't think this was ever meant to hibernate
8.  Can't connect to some Windows PCs.

If anyone can help me with my remaining problems that would be great.

I just realized that I don't have a battery meter either how did you fix this?

---

### Post by breimer273 on 2010-05-04
To the original poster: I saw here some of your questions could be answered with this thread:
[https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid)
if you are frustrated this is a good place to start for getting off the ground. Then from there you'll probably notice things that still don't work and you can post questions on here and people will be more than happy to help you.

---

### Post by unntrlaffinity on 2010-05-04
> **breimer273 said:**
> I just realized that I don't have a battery meter either how did you fix this?

Lucid seems to be pretty wonky when it comes to detecting a battery.  Most consistently, when you're running off of A/C power, and your battery is fully charged, upon reboot your machine won't realize there's a battery until it starts discharging.  Sometimes you can spur it into action by unplugging and plugging the adapter, or letting it run down a bit of juice and rebooting.

To make sure that's the same problem you're having, right-click on the battery icon and check the box that displays an icon on the taskbar no matter what.  When it's misbehaving it'll appear as a plug, even if you're not plugged in.

The biggest problem with this bug, aside from not being able to estimate your remaining battery life, is that functions such as dimming the display when on battery power obviously don't work when the OS believes it's running off the wall plug.

---

### Post by dlavizzo on 2010-05-04
I have to agree with the initial poster, even if I don't agree with the way he expressed his frustration. For being no-cost, Ubuntu is an impressive undertaking. Note that I don't call it "free", because it cost the time and effort of a lot of dedicated people working for (as I understand it) the love of coding and creation, and no actual compensation. If I'm wrong there, please call me out. 

I installed Ubuntu on my MacBook Pro 5,5 and I have to admit that since the MacBook itself comes with MacOS, there's very little incentive for me to "switch" to Ubuntu. If someone can explain, in layman's terms, why Ubuntu is better than the pre-packaged operating system, I'm more than willing to listen. 

The reason I'm expressing this frustration is because when I first was turned on to Ubuntu, I was very excited and was looking forward to telling nearly everyone I knew about a no-cost alternative that was nearly as easy as Windows to install. Much as I have with Android, OpenOffice, Firefox (lately, Chrome) and other "open" software, I began advocating Ubuntu. 

As time has worn on and my frustrations with trying to get even the simplest things to work on a MacBook Pro have grown, people have slowly lost interest. Sad to say I've also lost interest in evangelizing Ubuntu, since for the average user, digging into the command line and manually adding things is more work than they are willing to put forth. I'm pretty tech-savvy, however, the moderate difficulty in installing things is not the barrier-to-entry here; I just don't see a benefit in using Ubuntu over the native MacOS. Edit: Further, even though I'm personally interested in open-source, trying to get people to do more work for what they perceive as "less" product (read: less branding / marketing) is an uphill struggle.

So I guess my "question" becomes: is there a disc or download package out there that provides an idiot-proof installation of Ubuntu on a MacBook or MacBook Pro that works "out of the box"? If not, why not? Are the different iterations too time consuming? Is the programming too intensive? I'd really like to understand.

---

### Post by unntrlaffinity on 2010-05-04
Yarui mentioned a good link for explaining the mindset in this thread:

> **Yarui said:**
> I would also recommend everyone read over this page.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Don't let the title mislead you.  It isn't meant to be an insult to windows (or mac) users.  It just gives some explanation for why windows and mac users are often unhappy with Linux and explains why Linux users are often unwilling to help those who post rude comments.  It's a good read regardless of what OS you prefer.

---

### Post by unntrlaffinity on 2010-05-04
.

---

### Post by markling on 2010-05-04
Your Opera problem may yet solve itself.

I got the following error while trying to install Opera today:

"Error: Dependency is not satisfiable: libqt3-mt (>= 3.3.4)"

Another forum entry said all I need do is install the missing program with the following command in the terminal:

sudo apt-get install libqt3-mt

But that gave me another error:

"couldn't find package libqt3-mt"

I was about to throw my toys out the pram but was saved by the Update Manager. Having just reinstalled Ubuntu 9.10, a year's worth of updates were waiting to be made.

After the update manager finished (some 250-odd files if I remember rightly), the Opera package installer worked. It installed the missing libqt3-mt automatically.

m.

---

### Post by P4man on 2010-05-04
This thread is a mess. Next time please keep questions and opinions/rants separate. Feedback and opinion, even the negative ons are welcome, but there is forum for that called testimonials. Keeping this to the point will keep the thread clean, readable and useful not just for yourself, but anyone having similar issues and finding it on google.

Im not sure what issues still remain open, but the double bluetooth/battery is just because you added a second indicator applet to the panel. Right click one of them, and remove it again.

As for the other questions, maybe you want to edit your first post and mark the issues that have been solved as such and add the new questions that are still open ?

---

### Post by unntrlaffinity on 2010-05-04
> **P4man said:**
> This thread is a mess. Next time please keep questions and opinions/rants separate. Feedback and opinion, even the negative ons are welcome, but there is forum for that called testimonials. Keeping this to the point will keep the thread clean, readable and useful not just for yourself, but anyone having similar issues and finding it on google.

Im not sure what issues still remain open, but the double bluetooth/battery is just because you added a second indicator applet to the panel. Right click one of them, and remove it again.

As for the other questions, maybe you want to edit your first post and mark the issues that have been solved as such and add the new questions that are still open ?

Sorry, guvnah, that's partially my fault.  I thought the thread had progressed in an acceptable if more relaxed direction to be rant friendly.

A lot of the original Macbook issues can be addressed via the community documentation at:

[https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

[https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro")

Of the original post, I believe the only real outstanding complaint is "making the touchpad work like OS X".  To that end, there is work on multi-touch being done, and there's another thread at:

[http://ubuntuforums.org/showthread.php?t=1334696]("http://ubuntuforums.org/showthread.php?t=1334696")

The installation instructions are on page 12 or 13.  It requires the command line, which I believe a subsequent poster wanted to avoid.  But it's pretty straightforward.  Just make sure you type everything correctly.

It works pretty well and institutes most of the multi-touch features.  I found it to be overly sensitive and erratic initially, requiring some tweaking of the sensitivity sliders.  Also, scrolling bottom to top, or "up", with two fingers is wonky.  It seems to miss about half the swipes.  Swiping down works perfectly.  

On a sidenote, the touchpad sliders aren't as intuitive as they could be.  Simply sliding them both to one side or the other in the interest of making them more or less sensitive often won't achieve the desired result.  Instead, try the adjusting them differently, on opposite ends.  You might like the results better.

The above mentioned multi-touch support disables tap to click, which some people hate, but I can't live without, so that was a dealbreaker for me.  Still, it's progressing nicely.

---

### Post by untmdsprt on 2010-05-08
Actually I've see a few people skip steps that are needed assuming that everyone knows how to do something. For example: I've seen people say "edit your blahblah.blah file" and yet never give instructions on where to find this file or how to even edit it.

I at least know to type "sudo gedit ~~" to get it started. Now that I've gotten an old PC up and running with Ubuntu, I'm taking my time to look through these forums and see if anything can help me figure out things.

---

