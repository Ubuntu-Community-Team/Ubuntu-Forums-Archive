---
title: "Wiki Topics"
date: 2007-03-09
forum: Beginner Team
---

### Post by PartisanEntity on 2007-03-09
Brainstorming for the beginner wiki. What topics and sub-topics do we need?

IMO:

1. How to install Ubuntu from the LiveCD
2. How to use the partitioner on the LiveCD during install
3. Definition of commonly used terms
4. How to install wireless cards
5. Useful bash commands
6. How to use gedit & nano
7. How to get back into the GUI desktop after X server has crashed
8. How to backup files while setting up software/hardware


What else?
(perhaps we could sticky this topic or incorporate it into a relevant thread)

---

### Post by Gerard Barberi on 2007-03-09
How about

How to install software. (Enabling Repos, compiling from source, standalone Debs, shell scripts)
The difference between Windows and Ubuntu.  (I'm assuming new users are coming just off windows and will probably need an explanation as to why linux doesn't work the same way Windows does.)

---

### Post by TwistesdTexan on 2007-03-09
Another Sub topic for How to install ubuntu should be "Should I use dual boot and what is it?"
A link to a reference for crossover programs from Windows to ubuntu Like "[http://doc.gwos.org/index.php/AppHelper]("http://doc.gwos.org/index.php/AppHelper")" would answer a lot of questions also.

---

### Post by Gerard Barberi on 2007-03-10
> **TwistesdTexan said:**
> Another Sub topic for How to install ubuntu should be "Should I use dual boot and what is it?"

And a small section included reminding new users to make sure Windows is installed first and Why.

---

### Post by al1b1 on 2007-03-10
Howto setup graphics cards and printers would be helpful plus a guide to automatix or easyubuntu

---

### Post by JanEnEm on 2007-03-10
IMOO it is a good thing to distinguish between desktop and server installations. The majority of users will probably go for desktop information. A few however install Ubuntu for the purpose of serving computer power! They normally have different requirements.

---

### Post by bodhi.zazen on 2007-03-10
> **Gerard Barberi said:**
> And a small section included reminding new users to make sure Windows is installed first and Why.

How 'bout a small section on boot loaders so you can easily install the OS you want, when you want ?

Grub is very cryptic and takes some effort. However, once you become familiar with it it becomes easy to work with (Configure and install).

---

### Post by bodhi.zazen on 2007-03-11
> **JanEnEm said:**
> IMOO it is a good thing to distinguish between desktop and server installations. The majority of users will probably go for desktop information. A few however install Ubuntu for the purpose of serving computer power! They normally have different requirements.

You raise a good point.

New users on the server side ... Perhaps a sub team ? Perhaps you are just the person we are looking for :twisted:

Come on by #ubuntuforums-beginners :lolflag:

---

### Post by useResa on 2007-03-11
> **Gerard Barberi said:**
> The difference between Windows and Ubuntu.  (I'm assuming new users are coming just off windows and will probably need an explanation as to why linux doesn't work the same way Windows does.)
**+1**  -- IMHO this is one of the most important items that should be included!

In line with this I think it is important that new users should become familiar with the **terminal**! 
Although a GUI can be available for certain tasks knowing how to do things in terminal can help you understand what happens and in cases of program failure may give error indications that you do not get from the GUI.
A terminal should not be a scary feature to use, but should be considered a friend!

[COLOR=DarkRed]**EDIT:**[/COLOR]
Just thought of another item. Although Linux may not require disk defragmentation and disk cleanup I think it is good to explain that some cleaning can be done and may be required.
Where I am thinking of is things like **apt-get autoclean**, **localepurge** and removal of orphaned packages.

---

### Post by jvc26 on 2007-03-12
> **bodhi.zazen said:**
> How 'bout a small section on boot loaders so you can easily install the OS you want, when you want ?

Grub is very cryptic and takes some effort. However, once you become familiar with it it becomes easy to work with (Configure and install).
Thats a really good idea - I still have the occasional issue with GRUB and to be totally honest am not really sure about some of the things it can do/does.
Il

---

### Post by MikeSz on 2007-03-14
I agree with all the above - my biggest problem has been getting used to the idea that you cant just double click something and it install automatic.  I think windows users who have never used DOS/Win3.1 (Im one of the oldies who can) will have the same problems as me - getting acquainted (or re-acquainted in my case) with the command line and the massive difference in how to install programs - I still havent got my head round it so I hope you dont mind me asking for some more help later!

---

### Post by chewearn on 2007-03-14
A topic on pros and cons of 32-bit vs 64-bit install.

I have seen a steady stream of newbies came in with problems with their 64-bit; either installation problem, multimedia related, flash in Firefox, etc.

Not sure if anyone agrees, but perhaps, there should be a strong recommendation for those moving to Linux for the first time to use 32-bit.  It is too tempting to try the 64-bit ubuntu when you have 64-bit processor.  But for newbies fresh from Windows, they might be in for a difficult time, trying to understand the ubuntu experience at the same time fixing cryptic issues.

(I was in the same boat a while back, which made me give up coming into Linux for a year; only now, i realized if I have started of with 32-bit, the experience might be much different).

---

### Post by ncappel1 on 2007-03-14
what about something along the lines of "how to read a man page"? 

there's terminology and phrase structure that isn't really clearly explained.
 
to see the notes of all the switches that are possible. something that's helpful is seeing an example, like
tar -xzvf thing.tar | blah blah
and having each of the individual variables explained.

---

### Post by ncappel1 on 2007-03-14
Also, I wanted to add that though it would be very helpful to have a place where installation of programs and scripts is explained, there are already a lot of places where it is covered very clearly. the argument is already discussed ad nauseum everywhere else. what would be best is a short, concise overview, then links to pages that already do a great job, like [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware), and [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by teaker1s on 2007-03-15
in the appropriate place in beginners wiki
explain
chmod 755 
chown
:popcorn:

---

### Post by o0splitpaw0o on 2007-03-15
Installing Ubuntu: BIOS settings:

**Dell = **
1. Select F12 to select a boot device when you see the Dell Logo come up on start up.
2. Select CD ROM/DVD ROM 
3. Press enter

***If it's not an option:**
1.Hit F2 to BIOS setup at the Dell Logo when it comes up.
2. Select "BOOT" using the arrow keys
3. HIT TAB key to jump to the other window
4. Select the CD ROM/DVD ROM and use the + or - sign to make it the 1st boot instance
5. Hit F10 to quit and Save changes

**HP/Compaq = **
1. Select F2 or F10 when the Compaq/HP logo when it comes up.
2. Use the arrow keys to select "BOOT" at the top of the menu.
3.  Use the TAB key to select the CD ROM/DVD ROM 
4. Either use + or - / or use Page Up/Page down keys and make the CD ROM/DVD ROM the first device.
5. Hit F10 to exit and save changes.

**Non branded PC's (Example purchased from a small computer retailer)**
1. Hit the <DEL> *delete key on startup
2. Using the arrow keys, select boot options or advanced BIOS options
3. Select "BOOT PRIORITY OPTIONS"
4. Select First boot (or 1st boot)
5. Either hit Pageup/Page down OR + or - OR ENTER to change the option to CD ROM/DVD ROM 
6. Hit ESC. 
7. You will be asked "Save changes to the BIOS setup?" HIT Y on the keyboard and hit <ENTER>

That's some of the worked knocked out, I don't have a Toshiba or other named brands to on hand to remember the steps. but many of them are similar.

---

### Post by o0splitpaw0o on 2007-03-15
> **teaker1s said:**
> in the appropriate place in beginners wiki
explain
chmod 755 
chown
:popcorn:

Are chmod or chown commands begginer commands? or even pkill -u ? 

or arn't these more advanced .. don't you think?

I'd see those in the "Mastfwal powa's of terminal & Ubuntu"  list.

:)

---

### Post by bodhi.zazen on 2007-03-15
> **teaker1s said:**
> in the appropriate place in beginners wiki
explain
chmod 755 
chown
:popcorn:

I think they would go under an introduction to permissions.

---

### Post by useResa on 2007-03-16
> **bodhi.zazen said:**
> I think they would go under an introduction to permissions.
Now that you indicate "permissions" although Windows can also be set up having administrator(s) and user rights per group(s) or user(s), I think most people have NOT set up windows this way.
An introduction to permissions, not in a technical sense but in a conceptual way, would be a wise thing. If you can make someone understand the concept, the technical implementation becomes easier to explain.

---

### Post by ferg on 2007-03-16
How about a basic terms glossary?

---

### Post by teaker1s on 2007-03-16
good idea

---

### Post by o0splitpaw0o on 2007-03-16
I made this to show how I see the wiki could be broken down to. Just my ideas.

---

### Post by Ecthelion on 2007-03-16
> **teaker1s said:**
> in the appropriate place in beginners wiki
explain
chmod 755 
chown
:popcorn:
Why explaining this in the beginner part?
I know it is one of the first things I did when I started with ubuntu -look how to change those things- and only thing I got was that I had to reinstall because I used something recursive...
So maybe wait till they know a bit more before telling this kind of things...
Besides that, I though it was much more easy now > rightclick on the file, permissions, and click them right... Isn't that better for a beginner?

---

### Post by ButteBlues on 2007-03-16
A list of applications based upon the task.

Most Windows users have comments like "Search sucks!" or "I don't like Rhythmbox".

A wiki page should be devoted to alternatives offered in the repositories.

---

### Post by ncappel1 on 2007-03-17
> **o0splitpaw0o said:**
> I made this to show how I see the wiki could be broken down to. Just my ideas.

I think this is a pretty good diagram. the progression is logical and natural from a beginner to more advanced topics, but never leaving the realm of what is most important.

edit: how about at the end of the tutorial having a sort of quiz? questions could be answered with radio boxes or little assignments could be given just to see if people understand how to do things themselves. (ex. create a folder named "foldername" in your home directory with the gui and then through the command line, or how do you restart the x server in the event that it crashes?, and so forth) it could just be short, 10 questions or so dealing with the main points.

what about a short ubuntu forum tutorial? A lot of people I know never use forums to search for information or ask questions. they don't know how or don't even think of it as a possibility, only because they never have before. The support offered in these forums and the wiki are one of the strongest things about ubuntu, i think.

---

### Post by teaker1s on 2007-03-17
> **Ecthelion said:**
> Why explaining this in the beginner part?
I know it is one of the first things I did when I started with ubuntu -look how to change those things- and only thing I got was that I had to reinstall because I used something recursive...
So maybe wait till they know a bit more before telling this kind of things...
Besides that, I though it was much more easy now > rightclick on the file, permissions, and click them right... Isn't that better for a beginner?

And compiling- quite simply because these are the questions that keep re-occuring-especially when people have to install/compile to get their hardware to work.
people also start with server installs etc, the problem is we have people wanting more than what a new computer user generally does.

example:- some graphic's cards need nvidia beta driver, this can't be installed with xserver running, further to this when downloaded the run file needs permission to run "chmod755".

While I understand that we don't want to baffle new ubuntu users, It's not possible to never use the terminal with linux and install and maintain it.

Further to this lots of questions go unanswered because because everyone looks and thinks-that question has been asked before, someone else will answer it.:( 

I'm considering setting up my own wiki page and covering some of the things I mentioned if the beginners wiki doesn't want to cover them yet

regards
Daniel

---

### Post by bodhi.zazen on 2007-03-17
> **teaker1s said:**
> And compiling- quite simply because these are the questions that keep re-occuring-especially when people have to install/compile to get their hardware to work.
people also start with server installs etc, the problem is we have people wanting more than what a new computer user generally does.

Some of the questions on Absolute Beginners talk are quite sophisticated.

> example:- some graphic's cards need nvidia beta driver, this can't be installed with xserver running, further to this when downloaded the run file needs permission to run "chmod755".

Case in point (in terms of sophistication, however new users expect their nvidia cards to just work ;) ) . IMO for nvidia/ATI we should advise Envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy will do the latest beta driver (envy unstable).

Small clarifications : Installing the nvidia driver is running a script, not compiling. Not every tar ball is source code, some are binaries, some are scripts (python is not too uncommon).

To compile :

Prep ~ Install build-essential and checkinstall. Download and extract source tar ball.

```
Read any README that came in the tar ball
./compile --help  <- lists options
./compile
make
sudo checkinstall
```

This is how we should advise to compile ~ Add that to the wiki !

Yes, sometimes checkinstall fails but if it works it adds the package as a .deb and this has obvious advantages. If check install fails you can fall back on *sudo make install*.

> **While I understand that we don't want to baffle new ubuntu users, It's not possible to never use the terminal with linux and install and maintain it.**

YES EXACTLY ! I understand the CLI provokes angst in new users. We need to help.

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

> Further to this lots of questions go unanswered because because everyone looks and thinks-that question has been asked before, someone else will answer it.:( 

Sometimes. Sometimes unanswered questions are esoteric. I would like the Beginners team to help with this as well ... If there is an unanswered question I would like to steer the poster to the wiki or irc. But not just "have you searched the wiki ?" something a little more personalized, like an answer from the wiki or a wiki page ...

> I'm considering setting up my own wiki page and covering some of the things I mentioned if the beginners wiki doesn't want to cover them yet

LOL I like your enthusiasm ! Obviously you are free to do as you see best, but I would like to channel your ideas and energy to the wiki I have started :

[https://help.ubuntu.com/community/Beginners/](https://help.ubuntu.com/community/Beginners/)

Yes, there is not much there as of yet, but I think that will change. In addition I am working with the wiki team to coordinate our efforts. There is a lot of information out there, I think part of the problem is connecting that information to users :) Also I think there are a number of advantages to working with a team ...

If you would like I am more then happy to help you learn to wiki. There are a number of good ideas in this thread for the wiki and I hope my team will get started soon (hint hint) ...

---

### Post by useResa on 2007-03-17
Bodhi.Zazen: I think you have made a great start on the Wiki.

Although I am sure there are many amongst us that will help you out completing the Wiki, but -- IMHO -- each person has his/her own style of writing. Do you think we should have some procedure/guide on how to add to the Wiki?

Another option is that everyone who is willing to contribute adds text and that it is reviewed.

What is your idea on this matter?

---

### Post by teaker1s on 2007-03-17
[COLOR="Red"]bodhi.zazen[/COLOR] 
I'm with you on envy script- the only current issue is the nvidia  go 6150 isn't recognised by it at the moment.
With my own wiki page I'm hoping to use it as a notepad(rough outline of various issues) when I'm happy with the topic I intend to transfer it to beginners wiki.
 I feel that while I work on a topic and it's not well laid out and incomplete-it shouldn't be inflicted on new users:lolflag:
Could take a while as I have over 700 subscribed threads and loads of bookmarks to work on

---

### Post by bodhi.zazen on 2007-03-17
> **useResa said:**
> Bodhi.Zazen: I think you have made a great start on the Wiki.

Although I am sure there are many amongst us that will help you out completing the Wiki, but -- IMHO -- each person has his/her own style of writing. Do you think we should have some procedure/guide on how to add to the Wiki?

Another option is that everyone who is willing to contribute adds text and that it is reviewed.

What is your idea on this matter?


> **teaker1s said:**
> [COLOR="Red"]bodhi.zazen[/COLOR] 
I'm with you on envy script- the only current issue is the nvidia  go 6150 isn't recognised by it at the moment.
With my own wiki page I'm hoping to use it as a notepad(rough outline of various issues) when I'm happy with the topic I intend to transfer it to beginners wiki.
 I feel that while I work on a topic and it's not well laid out and incomplete-it shouldn't be inflicted on new users:lolflag:
Could take a while as I have over 700 subscribed threads and loads of bookmarks to work on

General thoughts :

[list=number][*]This is the advantage of a team approach. Some members can add content as text , other members can edit text and proof for accuracy, and some can edit for formatting ... screenshots ... the list goes on.

The point is together we are better then the sum of the parts ...


[*]teaker1s : Same general concept as I am proposing. The beginners wiki page is such a "note pad" we can all work on, and when it is done move it to the Ubuntu wiki. Lord knows I think it is unstructured, but I'm working on it ;)

Take all the time you like ...


[*]For general communication / wiki format there ARE standards for the Ubuntu wiki and we should follow them ...  I posted a link here ...

See : [https://help.ubuntu.com/community/Beginners/Development](https://help.ubuntu.com/community/Beginners/Development)

Feel free to add to it...


[*]If anyone adds wiki content and would like me to proof their work, PM me on Ubuntu or join #ubuntuforums-beginners.


[*]Last, all this is yet in development and watch for changes / additional structure over time. Any an all ideas / contributions are welcome.[/list]

---

### Post by useResa on 2007-03-17
Let me give an example: On the page of [Feisty](https://help.ubuntu.com/community/Beginners/Guide/Feisty) you have a heading "Advantages"
Under this heading you indicate > Well, I think it is faster ...

IMHO and not "attacking" you on this, but I think this is not a main advantage of Feisty. I like the improvements that have been made in usability and new "gadgets".

Please find attached two examples what I think are nice improvements to Feisty. 
[LIST=1]
[*]Tomboy -- Use yellow sticky notes to organize your mind
[*]The "Deskbar" feature that you can add to your panel after installing Beagle[/LIST]See attached screenshot

These "gadgets" are I think the goodies that make you want to go from either Dapper/Edgy to Feisty or from Windows to Feisty.

How would you like things like this included? Description of the functionality including an how to on installation (maybe on separate page)?

---

### Post by bodhi.zazen on 2007-03-17
useResa : LOL

Hey, nice screen shot ...

Add away ...

You can even remove those "off the cuff" comments re : I think It's faster & Unstable.

Like I said, the wiki is just starting ... 

And when you create a page, well you have to add something ...

One thing though, screen shots (on the wiki) need to be on a default install, default backdrop, default menus, icons, etc ...

Most people use a virtual machine for this ...

If you add a screen shot, upload it to the wiki server, add as an attachment, I think (that is what I was told by the wiki team).

Bottom line, the content is there for you to improve ... Go for it ...  and don't forget to have fun while you are at it ;)

---

### Post by useResa on 2007-03-17
Another example: Just to get for myself clear what can and cannot be considered as for Beginners.

I consider myself a recent beginner (Linux since summer 2006) and therefore I like to "play around". Just to experience and learn by doing.

One of the things I have done in order to learn is install Enlightment E17 in Feisty (see attachment). Is this something we can do a HOWTO or a WIKI page on for Beginners?

[COLOR=Navy]**[COLOR=Red] EDIT:[/COLOR]** Just read your previous supply. Guess this is a NO-GO for the Wiki since it is not default install etcetera.
If you wish you can delete this post or leave it for others to serve as a bad example[/COLOR]  ;)

---

### Post by teaker1s on 2007-03-17
re previous post [COLOR="Red"]useresa[/COLOR] if you would like to start a section, i'm sure it will be warmly accepted
okay I'm thinking we start with networking, now I think that if we can pull text from good posts and howto's we can avoid spending time reinventing the wheel

identify hardware
[http://ubuntuforums.org/showthread.php?t=384811]("http://ubuntuforums.org/showthread.php?t=384811")

ndiswrapper using synaptic and cdrom add(no internet connection required, or computers where both wireless and ethernet card are not working)

next we should make new users aware if they can only get numeric ip such as router page and no www. that they either need static ip and isp DNS.
or Dhcp and stabilise DNS
[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns]("http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns")

[COLOR="Blue"]I'm looking at grabbing the raw data from the posts, started a little section for general hardware identification I hope this is what you were looking for[/COLOR]

---

### Post by bodhi.zazen on 2007-03-18
useResa : I like the idea of a section explaining alternate window managers ...

I would add your information on Enlightenment there.

There may not yet be a page ... If not, let me know ...

teaker1s : Thanks for that ... I'll look it over ;)

---

### Post by lkuttner on 2008-06-18
Hey folks, I am two days old in this and although I am really enjoying Ubuntu, I have wasted a heck of a lot of time on the fact that until I can figure out how to connect to the internet, I cannot do much. 

There really needs to be a forefront article on how to install your modem driver without an internet connection. The way I see it, there are a load of folks out there who would be testing out Linux on a spare machine with a Windows machine alongside and connected to the internet.

I am gathering that ndiswrapper is the way to do this but I have not cracked it yet.

Lance

---

### Post by NewbieGirl on 2008-06-21
Here are my 2 cents... that is some of the first questions I had:

1. A clear list of system requirements
a) to run Live CD
b) to install from Live CD
c) to run the OS once installed
Yes, I know they are all available if you do a basic search, but for an absolute beginner possibly with an older machine, clear specs (for Ubuntu/Kubuntu/Xubuntu) will save a hell lot of time and aggravation (I almost gave up trying to install - until it dawned on me that perhaps a 2GHz CPU wont help much if you only have 256MB RAM...)

2. Installing software - like others have already mentioned, having used Windows, one expects it to just run - just like that. 

3. Basic mantenance - anti-virus, defrag, disk clean

These are just the basic questions I have had so far... I seem to be finding my way around - but boy is it taking time!

---

