---
title: "A few 'newbie' questions?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Morsolo on 2007-06-13
Hey people,
If you've read my other 2 threads, you'll see I'm not the quiet type when it comes to installing an operating system...I'll ask any question I'll need...

But, instead of posting a few hundred topics, I thought I will just post my questions in here, and hopefully, some or all will be answered...
[LIST][*]How do I get my "[Plantronics DSP-550]("http://www.plantronics.com/north_america/en_US/products/cat640035/cat1430032/prod5500015")" headset to work?
[*]What are the WOW aspects of Ubuntu? Like the 'flashy' features...
[*]How do you work the terminal? Being a windows user, I'm not used to that kind of thing (other than a bit of DOS knowledge...)
[*]How do you use the system folders? Eg. In windows you have "Documents and Settings" or "Users" in Ubuntu you get a bunch of folders that have no immediate meaning to a Windows user...
[*]How do you run a simple game... An executable file (.exe)... I don't want to have to switch between Windows and Ubuntu every time I feel like playing my games...[/LIST]
That's all on my mind for now, I'll edit this list soon, as I know I had more questions :(
- Morsolo

---

### Post by Sig_ZA on 2007-06-13
> **Morsolo said:**
> [*]How do you use the system folders? Eg. In windows you have "Documents and Settings" or "Users" in Ubuntu you get a bunch of folders that have no immediate meaning to a Windows user...
You can find some more info [here]("http://www.linuxnewbieguide.org/chap11.php"). Still rather confusing for me though.

---

### Post by Kobalt on 2007-06-13
> **Morsolo said:**
> [*]How do I get my "[Plantronics DSP-550]("http://www.plantronics.com/north_america/en_US/products/cat640035/cat1430032/prod5500015")" headset to work?
Honestly I don't really know, you should try to boot with a LiveCD and test it. Usual headsets work quite well, but this one seems to be a particular one...
> [*]What are the WOW aspects of Ubuntu? Like the 'flashy' features...
Surely the most visible effect would be Beryl/Compiz. But the power of the package manager is just as impressive to me...
> [*]How do you work the terminal? Being a windows user, I'm not used to that kind of thing (other than a bit of DOS knowledge...)
You will not need much Terminal knowledge to use Ubuntu. And if you do, it will be very simple commands and you'll get plenty of help out here.
> [*]How do you use the system folders? Eg. In windows you have "Documents and Settings" or "Users" in Ubuntu you get a bunch of folders that have no immediate meaning to a Windows user...
The various folders you must have seen (like /opt , /usr etc) are system folders, you should not use any of them. All your personal files should be stored from your Home Directory. Create your different folders (as Documents, Music, etc) from there.[/LIST]
That's all on my mind for now, I'll edit this list soon, as I know I had more questions :(
- Morsolo

---

### Post by jcronkhite on 2007-06-13
Folders didn't have real meaning to me when I began using Windows many years ago either.  I'm a newer Ubuntu user and I'm finding things are becoming more clear each day.  The best way to get use to things is almost on a "need-to-know" basis for most basic users.  When you need to know how to do something in Ubuntu, one usually searches for info online and as a side benefit will discover new directories.  Suddenly these directories have meaning.  Just stick with it, explore around the forums hear, check out the wikis and tutorials and you'll be surprised how you progress!  That's my 2 cents.  :)

---

### Post by Morsolo on 2007-06-13
Heh, thanks for that Jcron...
I'm back on my Windows Vista for now as I want to play WoW...

As soon as I gather some more understanding via here and the internet, I'll use Ubuntu more and more...
On another question, is there a list somewhere of all the key shoutcut commands?

I've installed beryl, and I want to know all the shortcut 'commands', not what to press, but for makign the commands...

**EG:**
The Shift key = <SHIFT>
The Control key = <CONTROL>
The Alt key = <ALT>

---

### Post by avik on 2007-06-13
> 
What are the WOW aspects of Ubuntu? Like the 'flashy' features...


There's Beryl/Compiz, but that's still beta software.  I guess it's more about the subtleties that make all the difference.

> 
How do you work the terminal? Being a windows user, I'm not used to that kind of thing (other than a bit of DOS knowledge...)


If a tutorial asks you to run a command on the terminal, go to Applications->Accessories->Terminal, and paste in the command using <Control><Shift><v>.

> 
How do you use the system folders? Eg. In windows you have "Documents and Settings" or "Users" in Ubuntu you get a bunch of folders that have no immediate meaning to a Windows user...


Just don't worry about any folder but the /home/*your_username* folder, which is where all your data goes.

> 
How do you run a simple game... An executable file (.exe)... I don't want to have to switch between Windows and Ubuntu every time I feel like playing my games...


There's WINE, but that doesn't run everything.  Virtualization is another option.

> 
I'm back on my Windows Vista for now as I want to play WoW...


WoW runs on Ubuntu through WINE: [http://ubuntuforums.org/showthread.php?t=312482]("http://ubuntuforums.org/showthread.php?t=312482")

> 
I've installed beryl, and I want to know all the shortcut 'commands', not what to press, but for makign the commands...

**EG:**
The Shift key = <SHIFT>
The Control key = <CONTROL>
The Alt key = <ALT>

Go to the Settings Manager for Beryl, and whenever you want to edit a shortcut, double-click on the name of the command.  Then use the Grab Key button.  But other than that, the only other significant key is:

The Windows Key = <SUPER>

---

### Post by aquavitae on 2007-06-13
> 
[LIST][*]How do you work the terminal? Being a windows user, I'm not used to that kind of thing (other than a bit of DOS knowledge...)
[*]How do you use the system folders? Eg. In windows you have "Documents and Settings" or "Users" in Ubuntu you get a bunch of folders that have no immediate meaning to a Windows user...
[/list]
Try this link: [http://linuxcommand.org/]("http://linuxcommand.org/").

---

### Post by jcronkhite on 2007-06-13
Morsolo, I've been playing World of Warcraft every day on Ubuntu.  I'm even using Skype to be extra nerdy and group with my friends.  All on 64bit Ubuntu.  It was really easy for me to get working.  Here are the simple steps:
[LIST]Install the 3d driver (hopefully for nVidia)[/LIST]
[LIST]Install WINE[/LIST]
[LIST]Copy the "World of Warcraft" directory from "Program Files" in Windows to my WINE directory[/LIST]

The last item is specific to people (like yourself) who already have it running under Windows like I did.

For me, the most difficult part was figuring out how to create a desktop icon launcher :)
It was honestly this easy for me.  But my hardware is ideal for WINE/WoW in my opinion.  Go to [http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine") and read up on it if you'd like.

I've tried setting up WoW with ATI cards and got very close, but it's just not stable.  Hope this is at least tempting!  Have a good one!

---

### Post by Morsolo on 2007-06-13
Yep, I'm on nVidia GO 7600 (256mb ded. + 256mb share)

Look like I wont be playing, I don't have enough HDD space to have a second copy of WoW...Bugger...
I'm getting another 100gb (at least) on my HDD soon, by then I'll be on my way! :)

Thanx for the help!

---

