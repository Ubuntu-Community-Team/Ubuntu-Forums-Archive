---
title: "wine, qemu, vmware, what's the difference?"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by Duncan_Idaho on 2005-10-09
so, that's my question
what does they do and what are the differences between them?
if i wanna run a game not supported by cedega and I'm not desperate enough to  install wintendo on mi HDD, wich one is recommended? :confused:

---

### Post by Kyral on 2005-10-09
Actually I think Cedega is your best best for gaming on Linux. If Cedega doesn't support it, chances are that WINE isn't...

I have no clue how QEMU and VMWare perform on Linux. I only use VMWare to test programs

---

### Post by Duncan_Idaho on 2005-10-09
actually the game question is pure curiosity 'n stuff :rolleyes: , the main question is what are the differences between those apps and what are they meant to do......

---

### Post by poofyhairguy on 2005-10-09
Wine is kinda like an emulator for Windows. Kinda.  so it runs the Windows code in Linux.

Teh other two run Windows inside of Linux. Teh full windows.

---

### Post by az on 2005-10-09
[QUOTE=Duncan_Idaho]actually the game question is pure curiosity 'n stuff :rolleyes: , the main question is what are the differences between those apps and what are they meant to do......[/QUOTE]
Cedega is wine with more hacks to run direct-x.  Direct-X is a microsoft library to use you video card's hardware acceleration.

SO, wine, Qemu, (I do not konw about vmware) will not render 3d graphics using your card's abilities.

---

### Post by wishyjr on 2005-10-11
could you tell me if i could 'transfer' files to and from any of these programs? ie, could i be runnig say.. dreamweaver in windows (through, vmware or wine etc.) and transfer the pages or website i was working on over to ubuntu?

i guess what im asking is:

how do / can these 'emulators' be linked to the filesystem in any way?

---

### Post by CbrPad on 2005-10-11
I run Hoary in work with VMware running Win2k and NT4 with any Windows apps I'm working on, and the answer is yes, you can set up a shared folder through which you can copy files to and from your vmware o/s's.

If you have the vmware trial you can try it - It's under 'Edit virtual machine settings' - and the second tab 'Options' has a 'Shared Folders' setting which you use to configure the folder you want to use.

---

### Post by wishyjr on 2005-10-11
ace! thats what i want to hear, thanks!

---

### Post by MartinAustin on 2005-10-11
Along this same topic, does Cedega, VMWare, WINE, etc. run Windows efficiently (and please, spare me the MS jokes)? :)

---

### Post by tseliot on 2005-10-11
[QUOTE=MartinAustin]Along this same topic, does Cedega, VMWare, WINE, etc. run Windows efficiently (and please, spare me the MS jokes)? :)[/QUOTE]
VMware does it but it need at least 256mb of dedicated RAM (in addition to the Mbs you use in Ubuntu) in order to work decently with Winxp (it's just like you ran it natively but a little slower).

---

### Post by wishyjr on 2005-10-11
so i'd be ok running it with a gig of RAM on my system? and how much is a little slower? :)  are we talking seconds or mins?

thanks

---

### Post by MartinAustin on 2005-10-11
I'll definately be looking into it then ... if that is the case, I'll back up my WinXP Pro, wipe the HDD, install Ubuntu as primary and then install VMWare.

---

### Post by nitricacid on 2005-10-11
In my opinion if you are going to use windows apps you should really just either stick with windows or make a partition that has windows on it.
I know i will now get flamed for saying to use windows when there are apps out there ment to do so for linux but if you really want the stableness & functionality of using a windows app then you should do it in windows.
I don't understand why anyone switches to linux and then complains how their windows app doesn't work in linux, no duh it won't work, linux isn't windows.

Linux is good for just about everything and there are people working very hard to make programs so that you can run windows apps on linux but lets just face the facts that untill everything in the windows emulator is 100% there will be bugs and some (if not alot) of windows apps will not work under linux.

Why emulate an OS if you could just partition the disk and have the actual program to run it.

I am sorry if i have come across very harsh in this post but I think WINE is the stupidest program ever made.

---

### Post by Wolki on 2005-10-11
[QUOTE=nitricacid]Why emulate an OS if you could just partition the disk and have the actual program to run it.[/QUOTE]

There are some reasons. People might not have a Windows license. And they might not want to reboot just to use a certain program. And installing windows might be a lot of work just for single programs.

Nobody's forced to use wine, and it's nice that I have little need for it. but I'm glad it's there.

---

### Post by nitricacid on 2005-10-11
[QUOTE=Wolki]There are some reasons. People might not have a Windows license. And they might not want to reboot just to use a certain program. And installing windows might be a lot of work just for single programs.

Nobody's forced to use wine, and it's nice that I have little need for it. but I'm glad it's there.[/QUOTE]
 
I agree with you but I was basicly just talking about anyone that installs linux and then uses it souly for windows programs. 

Sorry, I was just venting my pet peeve.

---

### Post by xequence on 2005-10-11
I dont know how anyone came up with "wintendo" o_O

Good thing I have experience with all these ;)

Wine runs code designed to make windows programs run in linux. It will show the accual program window just like it was a linux program.

Cedega is wine but with some extra things to play games. Cedega isnt free, legally.

QEMU emulates the processor so it can run mac os or any OSes that run on any processor it supports. It is very slow though. About 1/10 of the speed of your hosts CPU speed.

VMware will run an accual OS inside your OS, just like qemu. I like vmware much better and it is great for many things. It has a good speed, but you will need enough RAM for both oses and the accual vmware program. It will have a vmware window open where you can switch the tabs of different guest OSes. You can only run the OSes that can run on your hardware though. It costs money.

---

### Post by kakashi on 2005-11-02
[QUOTE=xequence]I dont know how anyone came up with "wintendo" o_O

Good thing I have experience with all these ;)

Wine runs code designed to make windows programs run in linux. It will show the accual program window just like it was a linux program.

Cedega is wine but with some extra things to play games. Cedega isnt free, legally.

QEMU emulates the processor so it can run mac os or any OSes that run on any processor it supports. It is very slow though. About 1/10 of the speed of your hosts CPU speed.

VMware will run an accual OS inside your OS, just like qemu. I like vmware much better and it is great for many things. It has a good speed, but you will need enough RAM for both oses and the accual vmware program. It will have a vmware window open where you can switch the tabs of different guest OSes. You can only run the OSes that can run on your hardware though. It costs money.[/QUOTE]

quemu work at 0.5 to .33 speed if you use the kqemu module
its way better than vmware cuz its free too

---

### Post by wishyjr on 2005-11-02
how does qemu perform? is it efficient?

---

### Post by _linux_ on 2006-04-10
Wine runs Windows applications in Linux. VMware and qemu run a virtual Windows machine.

---

### Post by andy_cowman on 2006-04-13
Rebooting to a seperate Windows install on a different partition is incrediably annoying! I used to do that, thankfully i recently had a good look at what i wanted and found VMPlayer. Wine normal brand and Crossover (4.2) have all found there way on to my PC aswell. 

If you want to use Windows Apps which are not well supported in Wine or Crossover (basically anything other than MS Office, early Photoshop and Picasa2) then use VMPlayer. Google and check on the forums for the instructions  and make sure you follow the instructions to get more options. I got file sharing working happily by simply using Samba and sharing! It works brilliantly for Photoshop CS2. It simply gets treated as another window. I doubled my RAM to make it work better so when I am using VMPlayer windows has 512mb RAM and Ubuntu gets 512. The other plus is that when windows falls over itself I simply create a new virtual image, easy. Heres a screenshot.

[IMG]http://i50.photobucket.com/albums/f338/andycowman/screen.jpg[/IMG] 

VMplayer also works the other way so you could have Linux running on windows, if security on the web is your problem then apparently theres a stripped down version of Ubuntu just for firefox and you can run that in a window.


I use wine for Picasa and Crossover for MS Office aswell.


Andy

---

### Post by kakashi on 2006-04-16
i'm not reading the entire thread but vmware server beta is out that is free so its your best option to run windows programs (except for games). and its leaps and bounds easier to use than qemu.

---

