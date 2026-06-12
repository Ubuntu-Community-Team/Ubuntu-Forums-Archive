---
title: "The LAST attempt..."
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-21
I have a clean install on my laptop... It actually isn't done yet, but will be in a minute...
Does the ubuntu install disc have ndiswrapper in it already? I don't want to hook it up with a cat5, cause I think that screwed up what we were trying to do with the wireless card.
I have the right drivers on disc, so I am going to copy them to my desktop.

If I hook up the cat 5 to my router, it seems to activate my eth0 network interface, which for some reason 'unconfigures' my wlan0 before it deactivates it. I can have my eth0 deactivated, wlan0 enabled and active, and set as default. I go to log off the system (to re-boot) I check the 'save these settings' box and click OK.

The system re-boots, and the first thing I check is System>admin>networking, and wlan0 is GONE, eth0 is active and is set as default... Anyone know why this might be?   What am I doing wrong?

---

### Post by Papa-san on 2006-03-21
A few things I need help with first, though...

1- hexadecimal WEP What is the difference between this and my standard, numeric (like in 1st grade) numbers that I usually put in?

2- Some people say to do these things as 'root user' some say to do them as 'standard user'(I don't know the term) 

3- What is a 'bash' prompt? I assume 'bash' to be a bad thing. why do some of my commands get 'bashed' ?

---

### Post by Brunellus on 2006-03-21
responses to the things I know

2) Root is "superuser," which is not enabled by default in Ubuntu.  To do things "as root" or with root's privileges, preface the command with sudo. (short for superuser-do.  No kidding)

Regular user is the kind of account you set up by default for yourself. 

This is crucial to understanding why and how security works on a Linux/Unix system.  Nothing prevents you from running as root all the time and having total access to everything on your computer.  Unfortunately, that means all your programs...even the ones you choose not to monitor closely!...have similar total access.  You can break your system in a hurry.  Worse, anyone who gets into your machine has total access and can do whatever he wants:  this is what happens in a normal windows install, and why so many windows machines are so easily taken over.

3) bash is an acronym for "Bourne Again SHell" which is the name of the program that interprets commands at the command line.  Linux/unix has lots of these programs (csh, ash, zsh, sh, and dozens of others I can't remember), but bash is the standard.

---

### Post by Papa-san on 2006-03-21
](*,)
Well, in the amount of time the forums were down, I managed to work through the "SetupNdiswrapperHowto" part of the way... I got stopped in the 'error check' step... I found errors... 
I wonder if maybe we could set up links in these pages to answer questions on the "What if it DOESN'T work?" answer.

Maybe someone could help me find the UNZIPPED bcmwl5a.inf and .sys?
(I say unzipped, because I cannot get the 'file-roller' program.)
I wonder why this error comes up immediately after a clean install?!? :

EDIT: in case someone is interested, to unzip a driver.exe file in linux:
1 - Copy it to your desktop, just as it is.
2 - rename it's extension. Right click on it, and click ' rename'. put the cursor at the end, backspace to the . (dot) and type zip  Hit 'enter'
3 right click the newly renamed file, and 'open with' and use 'archive manager.
4 - When the interface box opens, look for the {driver}.inf and {driver}.sys files.
5 - 'extract' to desktop.

---

### Post by az on 2006-03-22
[QUOTE=Papa-san]](*,)
Well, in the amount of time the forums were down, I managed to work through the "SetupNdiswrapperHowto" part of the way... I got stopped in the 'error check' step... I found errors... [/QUOTE]
What errors?  That would be important to say.

[QUOTE=Papa-san]
I wonder if maybe we could set up links in these pages to answer questions on the "What if it DOESN'T work?" answer. [/QUOTE]

Good idea - like a FAQ.  The wiki pages get revamped every now and then (I love how you can just plop your idea down on the page and then someone comes around and runs with it, redoing the whole page to properly get them message through!)  It would rock if it were easy to mention some of the most common pitfalls in such a page.

There is such a thing as talk pages - basically add /talk to the end of the URL for a wiki page and then put your ideas there.  It would have to be widely used to be effective.  

[QUOTE=Papa-san]
Maybe someone could help me find the UNZIPPED bcmwl5a.inf and .sys?
(I say unzipped, because I cannot get the 'file-roller' program.) [/QUOTE]

Did you do a full install (default?)  Why is file-roller not working. Anyway, here:  See attachments, but you should really use the original 80211g.zip file.  I am puzzled as to why you cannot just click and extract it...

[QUOTE=Papa-san]
I wonder why this error comes up immediately after a clean install?!? :[/QUOTE]

Did you try to add repositories without network access?

---

### Post by Papa-san on 2006-03-22
Hi,
I'll try to clarify:

The error check was to run:
```
tail /var/log/messages
```
This morning, the output is VERY different.

> Did you do a full install (default?) Why is file-roller not working. Anyway, here: See attachments, but you should really use the original 80211g.zip file. I am puzzled as to why you cannot just click and extract it...

Yes, it was a full default install. I just managed to get automatix, and hopefully fileroller is workable from there.

> Did you try to add repositories without network access?

No.

I'll try the file roller again, but also, I thank you for the drivers! (though I have never dealt with a .tar.gz before...lol)

EDIT: Nope, No File-roller...  hmmmm. Also, I extracted the files to my desktop, but they have a little lock icon at the top right corner of each of them, and ```
john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bmcwl5a.inf
Installing bmcwl5a
cp: cannot stat `/home/john/Desktop/bmcwl5a.inf': No such file or directory

```

---

### Post by Papa-san on 2006-03-22
OK...

Well, I'm going to walk away for the day, check in later and see if any other suggestions help. The next step is taking great pleasure in running this thing over with my tractor! I usually spend a half hour a day using my computer for my business. In and out, quick and painless. I have been into this thing a good five hours a day for the last two weeks, to no avail. I have learned an incredible amount, but am just not up to the challenge! I am irritating my wife and children, and have been told at least a dozen times to just re-install XP....

I just don't know...

---

### Post by az on 2006-03-22
[QUOTE=Papa-san]Hi,
I'll try to clarify:

The error check was to run:
```
tail /var/log/messages
```
This morning, the output is VERY different.



Yes, it was a full default install. I just managed to get automatix, and hopefully fileroller is workable from there.



No.

I'll try the file roller again, but also, I thank you for the drivers! (though I have never dealt with a .tar.gz before...lol)

EDIT: Nope, No File-roller...  hmmmm. Also, I extracted the files to my desktop, but they have a little lock icon at the top right corner of each of them, and ```
john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bmcwl5a.inf
Installing bmcwl5a
cp: cannot stat `/home/john/Desktop/bmcwl5a.inf': No such file or directory

```[/QUOTE]
First off, how did you open the tarball if file-roller (archive manager) is not there?

Secondly, automatix has nothing to do with default desktop tools like that.

Thirdly, the fact that the files are read-only (lock icon) is not why they are not installing.  I don't know if you are typing the file name wrong or something.

---

### Post by az on 2006-03-22
[QUOTE=Papa-san]
cp: cannot stat `/home/john/Desktop/bmcwl5a.inf': No such file or directory
[/code][/QUOTE]

Shouldn't that be "/home/john/Desktop/bcmwl5a.inf"?

Just use tab completion!  Type 
sudo ndiswrapper -i D[TAB] and that should complete the word "Desktop", then hit b[TAB] and that should complete the filename.

---

### Post by az on 2006-03-22
[QUOTE=Papa-san]I am irritating my wife and children, and have been told at least a dozen times to just re-install XP....

I just don't know...[/QUOTE]

******* command line!

Most (but not all) tasks can be done graphically.  Soon 100 percent of them will be out-of-the-box....

---

### Post by jjf on 2006-03-22
[QUOTE=Papa-san]EDIT: Nope, No File-roller...  hmmmm. Also, I extracted the files to my desktop, but they have a little lock icon at the top right corner of each of them, and ```
john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bmcwl5a.inf
Installing bmcwl5a
cp: cannot stat `/home/john/Desktop/bmcwl5a.inf': No such file or directory

```[/QUOTE]

Looks like you mistyped the file name.  When using the terminal, you can just hit the tab key to have the terminal autocomplete your line (of course it can't read your mind, so you have to have enough already typed that it knows what you're trying to do).

Also, double-check that the unarchived file isn't actually in a folder on your desktop.  I think that's the default behavior for tarballs.

```
~/Desktop/bcmwl5a/bcmwl5a.inf
```

---

### Post by Papa-san on 2006-03-22
Consistency in terminology seems to be one of the issues I am dealing with here. Shouldn't file roller be called file roller? When I try to use file roller/ archive manager to open the driver file I downloaded, It says 'archive type not supported' .

The 'tarball' opened automatically with archive manager. I just kinda guessed where to go from there, and seems to have put them on my desktop... This is a goood thing, I know where to find 'em!

OK, I did the:
 ```
john@laptop:~$ sudo ndiswrapper -i Desktop/bcmwl5a.inf
bcmwl5a is already installed. Use -e to remove it

```

Do you think I should clear the ndiswrapper stuff and give it another go, or leave it alone?   Never mind...lol.... wlan0 disappeared from my network settings again...
I need to go back through my bookmarked archive and wiki's to try to get it back...

---

### Post by az on 2006-03-22
[QUOTE=Papa-san]Do you think I should clear the ndiswrapper stuff and give it another go, or leave it alone?   Never mind...lol.... wlan0 disappeared from my network settings again...
I need to go back through my bookmarked archive and wiki's to try to get it back...[/QUOTE]

By clear it, remove the windows driver that is installed as it says:

sudo ndiswrapper -e bcmwl5a

Then reinstall it and load the ndiswrapper module

sudo ndiswrapper -i Desktop/bcmwl5a.inf

sudo modprobe ndiswrapper

And *then* see if you have a wireless connection to configure.

---

### Post by Papa-san on 2006-03-22
> And *then* see if you have a wireless connection to configure.

This was the first time I got anything like this:
```
john@laptop:~$ sudo ndiswrapper -i Desktop/bcmwl5a.inf
Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
john@laptop:~$ sudo modprobe ndiswrapper

```
OK... I removed ndiswrapper and then installed it again. The wireless now shows up again. 
Should I deactivate eth0 before I do anything with the wireless?

And, once this is done, is there anything I can do to keep it there upon re-boot?

---

### Post by az on 2006-03-22
[QUOTE=Papa-san]
Should I deactivate eth0 before I do anything with the wireless??[/QUOTE]

I guess.  You can untick the box that says the device is configured.


[QUOTE=Papa-san]
And, once this is done, is there anything I can do to keep it there upon re-boot?[/QUOTE]

Well, if ndiswrapper loads on boot, wlan0 will be available.  

You can add the word "ndiswrapper" to the end of the list in
/etc/modules
and so it will load on boot.

sudo gedit
and then open up /etc/modules

That's not the most common way to do it, but it works well and is easily undone.

---

### Post by Papa-san on 2006-03-22
> sudo gedit
and then open up /etc/modules

You prolly wanna slap me by now... lol

There is no 'modules' in  /etc ... I am attaching a screenshot ...

(Have I mentioned how much I appreciate your help?    I do!)

---

### Post by az on 2006-03-22
[QUOTE=Papa-san]You prolly wanna slap me by now... lol

There is no 'modules' in  /etc ... I am attaching a screenshot ...

(Have I mentioned how much I appreciate your help?    I do!)[/QUOTE]

/etc/modules is a file, not a directory.  Keep scrolling down.

That's a useability problem you have pointed out, there!  Gnome is generally easier to figure out for the non-computer literate, but I have to admit that I have seen a few people have the same issue.

I guess your wireless works, then?

---

### Post by Papa-san on 2006-03-22
> /etc/modules is a file, not a directory. Keep scrolling down.

That's a useability problem you have pointed out, there! Gnome is generally easier to figure out for the non-computer literate, but I have to admit that I have seen a few people have the same issue.

I guess your wireless works, then?

I don't know yet... I'm afraid to jinx it...lol
I'll try, and get back to ya!

---

### Post by Papa-san on 2006-03-22
No, just like I figured...

no wireless...
I think I'll go fire up my old Ford 515 ! (She still has chains on, so it'll be messy!)

---

### Post by towsonu2003 on 2006-03-22
[QUOTE=Papa-san]
no wireless...
[/QUOTE]
Reading the post, it looks like you keep loosing the wireless with every boot. That's normal (the addition to /etc/modules may have been insufficient -not sure there). Another possibility is that you are using the wrong .inf file. This would block your wireless connection attempts though... 

First, open one terminal and type tail -f /var/log/messages Don't close this terminal and observe output as you type commands. There shouldn't be any error messages but only info. Any error messages -> stop, post here, along with the command you used. 

Now let's try the following bunch of commands, in a new terminal (act as if you know what you are doing ;) so your wife and children will think you are a computer guru :p ) : 

ndiswrapper -l
^-this will list the drivers you loaded. You should see only one, and the output should be: 
```

Installed ndis drivers:
bcmwl5  driver present, hardware present

```

If there are more than one, well, remove them one by one with sudo ndiswrapper -e bcmwl5a (or whatever the dirver name is) and re-add yours (sudo ndiswrapper -i /bla/bla/bcm[TAB]blablablablabla.inf

If there is just one and the output doesn't say "hardware present", see ndiswrapper website to find the corret driver to use. There is alist of working drivers for each working hardware in some corner in that web site. 

Even if it says "hardware present", the driver may not be the corect one. You'll see if this is the case later on, when trying to connect. Trying out different drivers (again, using the ndiswrapper website) will solve this most of the time... 

Let's assume you got the right driver and output is fine. activate the driver with: 
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
(did you add ndiswrapper to /etc/modules? do that)

now your wireless is supposed to be "there" (lights on? if off: never mind, continue). System>Administration>Networing will show that it is there. iwconfig (command, in a terminal) will show it as well. As we are now trying to just connect, open up your wireless (no wep, no encryption, nothing to block anything from connecting, should broadcast ESSID as well, and give IP address automatically -called something like dhcp-) Try connecting with this: 

(take down ethernet connection, to reactivate, you can use the Networking tool (Sytem>Administration))
sudo ifconfig eth0 down
(scan wireless access points around and find yours. If it's not there, either wireless point is not broadcasting its essid, or something with the driver is wrong)
sudo iwlist wlan0 scan
(tell it your ESSID, according to the above command)
sudo iwconfig wlan0 ESSID youressidhere
(check if it understood your input: search for the essid you told it in the output)
iwconfig wlan0
(bring wireless up)
sudo ifconfig wlan0 up
(tell it to connect: it should tell you that you got an ip or similar)
sudo dhclient wlan0

Did it connect? If it did, hurra... If it didn't, you may need another driver (.inf file along with the .sys file that comes with it)

Assuming that it did connect, knowing that ndiswrapper is added as a line to your /etc/modules file, if is supposed to come up (working, not connected) in the next reboot. 

Undo your changes: 
1 sudo killall dhclient
2 sudo iwconfig wlan0 ESSID none
3 sudo ifconfig wlan0 down
4 Go to System>Administration>Networking and get your eth0 to connect again
5 Undo changes you did to your wireless access point (wep, encryption, broadcasting, etc -whatever you did have before)... 
6. Figure out how to connect to the wireless access point with the security measures you are using (web or whatever, I'm clueless about that - see [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) bottom of the page) Reboot and test (this time, using System>Administration>Networking).

---

### Post by Papa-san on 2006-03-22
```
john@laptop:~$ tail -f /var/log/messages
Mar 22 17:43:19 localhost gconfd (root-6495): GConf server is not in use, shutting down.
Mar 22 17:43:19 localhost gconfd (root-6495): Exiting
Mar 22 17:58:10 localhost -- MARK --
Mar 22 18:18:10 localhost -- MARK --
Mar 22 18:38:10 localhost -- MARK --
Mar 22 18:58:10 localhost -- MARK --
Mar 22 19:18:10 localhost -- MARK --
Mar 22 19:38:10 localhost -- MARK --
Mar 22 19:58:11 localhost -- MARK --
Mar 22 20:18:11 localhost -- MARK --
Mar 22 20:38:11 localhost -- MARK --

```

I did this and kept an eye on it as I went through the commands up to 
```
 sudo depmod -a
``` 
When I saw no 'movement', I figured I would stop and ask if it is OK so far... I do not know what to be looking for, so I post :D

OK... I lied, I went to the adding ndiswrapper to /etc/modules...

---

### Post by Papa-san on 2006-03-22
OK...

```
john@laptop:~$ sudo modprobe ndiswrapper
john@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

> sudo iwconfig wlan0 ESSID youressidhere
(check if it understood your input: search for the essid you told it in the output)

I guess it did not...
```
john@laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

This is what I saw in the other terminal:
```
Mar 22 21:39:16 localhost kernel: [4309226.110000] ndiswrapper (add_wep_key:644): adding encryption key 1 failed (C0010015)
Mar 22 21:44:07 localhost kernel: [4309517.380000] NET: Registered protocol family 17
Mar 22 21:45:59 localhost kernel: [4309629.339000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Mar 22 21:46:13 localhost gconfd (root-9445): GConf server is not in use, shutting down.
Mar 22 21:46:13 localhost gconfd (root-9445): Exiting
```
 This OK?

the wireless doesn't work...
I'll look for other drivers, I guess...

---

### Post by towsonu2003 on 2006-03-23
it's possible that your wireless access point is not broadcasting its essid. did you open it up and made sure it *is* broadcasting? looks like you didn't open it up al together (says "ndiswrapper (add_wep_key:644): adding encryption key 1 failed (C0010015)")

what is/was the output of sudo iwlist wlan0 scan after modprobing and so on?

the -MARK-s in /var/log/messages are normal. when you modprobe ndiswrapper, it will log it. when you connect, it will log it as well. error messages are not good, but you don't have any except the "encryption" thing. when nothing's happening, it will put "-MARK-"s. ignore the stuff about gconf, they are irrelevant (at this point at least?).

> Scratch that... I'm out!
well, patience is a prerequisite in linux ;) don't forget that this all is happening because manufacturers do not write drivers for linux...

---

### Post by az on 2006-03-23
[QUOTE=Papa-san]OK...
ndiswrapper (add_wep_key:644): adding encryption key 1 failed (C0010015)[/QUOTE]

Did you type in the correct WEP key?

---

### Post by Brunellus on 2006-03-23
this is a lost cause;  OP has probably left, and will harbour a grudge against linux for the rest of his life.

---

### Post by towsonu2003 on 2006-03-23
[QUOTE=Brunellus]this is a lost cause;  OP has probably left, and will harbour a grudge against linux for the rest of his life.[/QUOTE]
I disagree: 
1. someone will search the forum and see this post. the alternatives given in here may offer options.
2. OP may have left, but there is always a chance s/he'll come back... 
example (this is about me, skip-able, nothing new after this point): I first tried linux ~7 years ago (knoppix). nothing worked, so I got pissed off and left. Than I tried it 1 year ago with Slackware but the winmodem didn't work. So I got pissed off and left again. 7 months ago I started trying distros one by one, going down the hit-rating in distrowatch (skipped ubuntu bc. of some reason I don't remember). I tried ~6 distros. Winmodem didn't work, so I left for another month, than tried Dapper, and here I am: the damn winmodem worked with ubuntu... there is a good chance OP will come back after calming down or forgetting the frustration.

#1 is more viable...

---

### Post by Papa-san on 2006-03-23
I'm not gone....
This OS must be like heroine... I have learned so very much in a short while... (No easy task for an old fart!)

This morning, I went to uninstall the bcmwl5 and or bcmwl5a drivers, and results were that neither were installed.... Odd because it said they were last night, and I didn't do anything... I think? lol

azz... Don't curse  the command line... When I was in college,  umm , a year or two ago :rolleyes: , The one computer course I took was heavy on the fact that you don't do anything in DOS or an equivalent without knowing exactly what you are doing... I did not do well in that class because I was forever crashing something, ...lol That fear has stayed strong within me,and the graphical interface of windows seemed to be the solution. What I was not consciously aware of was the fact that the graphic interface was only running these commands 'behind the show'. 

The intimidation of the command line seems to be short lived (to an extent- I still balk at some things)  
What I can say is that you people are awesome in your support of the linux principles, and your willingness to help out those of us who are really not familiar with code of any sort. 

I have to say that I am convinced that this OS is the way I want to go, I am just quite fearful that you fine people will give up on the likes of me before I have a handle on it...

---

### Post by Papa-san on 2006-03-23
[QUOTE=azz]Did you type in the correct WEP key?[/QUOTE]

One of the questions I had was how to input it correctly...
The WEP we use has always been a simple 10 digit number, Is that all I put in? 'cause I read somewhere to preface it with an 's' if it's in hexadecimal ?
Unsure... 

I haven't given up yet, There continues to be progress..

I need to remove all the ndiswrapper stuff, drivers etc. and try again. Somehow neither one seems to have been installed?!?

(By the way... OP?)

The bug sheild on the front of my truck seems to say it best... Once I learn how to install ancient greek fonts on this thing, I'll explain it...
Basically, it means 'To persist obstinately in'

---

### Post by pbaehr on 2006-03-23
Don't worry. From what I've seen of Papa-San in the last couple of weeks he may become frustrated and tell himself (and us) that it's the last straw but he's hooked. His original thread I believe was something like, "I give up! I'm going back to Windows!" or something to that effect. But, a few weeks later, he's still around and fighting the same (or at least a similar problem).

He's definitely got the determination and I suspect, like he said, he will be around as long as this forum keeps helping him get through the hurdles he faces. And from what I've seen on this forum, there is no shortage of helpful people.

I've been keeping an eye on his threads out of interest in his situation (though I can't help so I'm not contributing to the cause). I think he's here to stay. It's certainly not a case of someone who tries Linux for 10 minutes and gives up.

---

### Post by towsonu2003 on 2006-03-23
[QUOTE=Papa-san]One of the questions I had was how to input it correctly...
The WEP we use has always been a simple 10 digit number, Is that all I put in? 'cause I read somewhere to preface it with an 's' if it's in hexadecimal ?
Unsure... [/quote]I'm not sure how to go about wep etc. it seems it's just easier to use the access point without wep or any other "blockage". That's why I wanted you to disable all security of access point. This is so for the initial test of "is this working?". once you get the hardware to work with the driver, you basically have to start learning how to deal with those "blockages". that's my opinion though. 

Ndiswrapper page *may* have some info on WEP. Google must come up with a wireless howto / guide / tutorial. I never used wep. 

Uninstalling ndiswrapper and starting from scratch is a very good idea by the way. 
[QUOTE=Papa-san]
(By the way... OP?)
[/quote]
I believe it means "Original Poster" (you)
[quote=Papa-san]That fear has stayed strong within me[/quote]
oops heheh... I had that fear as well when I started. My solution was: backup everything and type while thinking "if I bork this, I'll just do a clean install". I did clean installs about 4 times :) bc I didn't know how to undo stuff I did/tweaked... it was like re-installing windows bc I didn't know how to uninstall a program :p

---

### Post by pbaehr on 2006-03-23
Quick little comment:

I don't think anyone has suggested simply disabling WEP while you figure out exactly what the problem is.

I've never configured a wireless card under Linux but when I'm troubleshooting I like to do it one stage at a time. If WEP is giving you a hard time, I'd disable it and then when you can connect without WEP, turn it back on and open up that can of worms.

That is, of course, assuming you have access to the router settings.

Am I out of line for suggesting this?

---

### Post by imhdd on 2006-03-23
Forgive this off subject!
Been keeping up with Papa-san for a while. I know the feeling. When I read _towsonu2003_'s post I burst out laughing. No one here but me and dogs ... dogs thought I went nuts. Thanks for a good laugh! I, too have been 'fooling' with Linux off and on for a long time and I still don't know how to get  commands to work for me in   terminal. Can't open tarballs, can't get HP 722C printer to work. I give up every few days, then start again. I typically say to myself something like: "today I'm going to get a gzipped tarball opened and installed" but I've yet to accomplish that. I appreciate arnieboy and automatix - it works.

Been building and repairing computers for 10 years (Windows) and still, I come back to Linux. I have books "Linux for Dummies", "Kiss Blue screen of Death Goodbye", etc. No help. They are good promotions for Linux but haven't helped me. 

I keep reading and trying. I'm now 73 and still in kindergarten. At the rate I'm going, I'll be 80 before I can drop Windows for Linux. But no need to say I'm quitting - I don't give up on a challenge and this is a continuing challenge.

Thanks for all the help and support on this forum.

---

### Post by Papa-san on 2006-03-23
> I'm not sure how to go about wep etc. it seems it's just easier to use the access point without wep or any other "blockage". That's why I wanted you to disable all security of access point. This is so for the initial test of "is this working?". once you get the hardware to work with the driver, you basically have to start learning how to deal with those "blockages". that's my opinion though.

Unfortunately, my son has 'tweaked' the router settings, so I am relegated to using it as is... I can say that it was functional with winxp, for what it's worth!
Uh Oh...
```
john@laptop:~$ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
```
If I knew the keystrokes for the headbanging smilie, it would be here--->

---

### Post by az on 2006-03-23
[QUOTE=Papa-san]
```
john@laptop:~$ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
```
[/QUOTE]




That happens when you do not have a correct (valid) .inf driver installed.

From the time that they were correctly installed and to the time you noticed they were no more, what did you do?  (what wiki page, howto, mantra)

If you install the correct .inf, load the module and try to use wireless, what happens?  I mean, don't reboot.

---

### Post by Papa-san on 2006-03-23
Hello?
 The last steps I took... 
```
john@laptop:~$ sudo rm -r /etc/ndiswrapper/ 
john@laptop:~$ sudo rm -r /etc/modprobe.d/ndiswrapper 
```

Now what? Do I try the same things and expect different results, or what?

I have bcmwl5.inf, bcmwl5.sys, and bcmwl5a.inf on my desktop, waiting to be ignored by ndiswrapper.

I also have the original 'wireless drivers' cd in my drive, mounted, and unable to be opened by archive manager...

](*,)
sorry azz didn't see your post before I shot my mouth off...
I'm guessing the bcmwl5a isn't the right one... I apologize for making you prep it for me to download... I'll retry the bcmwl5
When I did have the wireless in the network settings window, configured, active and set as default, I disable the eth0 and internet is gone... (even without a re-boot... The times I have re-booted, the wireless option in the network settings window is gone, most of the time. (to be honest, I have gone through these steps so many times with so many variations, I can't tell you what I was doing... Sorry)

---

### Post by Papa-san on 2006-03-23
The closest I have come is by following the steps here:
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+HOWTO](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+HOWTO)

can't find it now... bookmarks went with last re-install
just did: install ndiswrapper-utils... went ok,  then did this:
```
Setting up ndiswrapper-utils (1.1-4ubuntu2) ...

john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5
Installing bcmwl5
cp: cannot stat `/home/john/Desktop/bcmwl5': No such file or directory
john@laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
```

---

### Post by Papa-san on 2006-03-23
Next step (with results shown) is this:
```
ohn@laptop:~$ sudo ndiswrapper -m
Password:
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
john@laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/*.conf: Permission denied
cat: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
```
](*,)

---

### Post by towsonu2003 on 2006-03-24
[QUOTE=Papa-san]The closest I have come is by following the steps here:
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+HOWTO](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+HOWTO)
[/QUOTE]
It seems your having problem loading the actual driver... 

The forum link you're following may be problematic bc it's for an earlier (hoary) version of ubuntu. If I were you, I would first read very carefully this page starting with "Install Windows Driver", take notes (which command is used for what, how/where to get driver files, what to pay attention to etc): [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) (ignore "installation of ndiswrapper" part)

and refer to this page for step by step instructions: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

Reading the first link is important because it will give you insight of whats going on in the second page (and tells you where to find your own hardware's drivers). 

To start from scratch, do the following (source:wiki.ubuntu):
```

sudo modprobe -r ndiswrapper 
sudo apt-get --purge remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
```

---

### Post by Papa-san on 2006-03-24
OK, I read the first page, and think I understand what is going on. (Ubuntu is newer, so some of the command line codes are different) So I went to the second page, (after cleaning out ndiswrapper as per the instructions given) Everything seems to have gone well. 
Ndiswrapper -L showed 'hardware and drivers present' 
I attached a screenshot of where things seem to me to have gone awry... Everything went as described until I ran ifconfig and iwconfig... I am not sure what 'sit0' is, and (I don't know if you can read the screenshot instructions, but it mentions editing the file by hand if options other than those offered in 'network settings' (sit0)
```
john@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:192.168.1.224  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fee1:ba40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8047052 (7.6 MiB)  TX bytes:665693 (650.0 KiB)
          Interrupt:11 Base address:0xec80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9113394 (8.6 MiB)  TX bytes:9113394 (8.6 MiB)

john@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:39   Missed beacon:0

```
Also, the Access Point doesn't seem right...

---

### Post by towsonu2003 on 2006-03-24
your ifconfig and iwconfig output is fine. ifconfig -a would include wlan0 as well I believe). Now, you have to do following steps. 

0. (this is a note, not a step) forget about sit0, it can sit where ever it wants ;) I don't know what it is, but I have it too and it doesn;t do anything. just ignore it

1. to check the wireless driver, type this: lsmod | grep ndiswrapper
this has to give you some output (that includes "ndiswrapper"). if there is no output, modprobe ndiswrapper (sudo modprobe ndiswrapper) and check that it is on (first check output of dmesg | tail for errors then check output of *lsmod | grep ndiswrapper* which should give you output).

2. take down eth0 connection: 
sudo killall dhclient (I think?? maybe skip this?)
*sudo ifconfig eth0 down*

3. configure and activate wireless. use the System>Administration>Networking to configure your wep and stuff settings. As usual, open a terminal and monitor the output of *tail -f /var/log/messages* for errors or connection notification in the meantime. dmesg | tail at the end of finishing these steps may give some insight as well. 

-> I think, basically, (in Networking) you click on "wireless connection" > properties > fill out everything you have (ask here if you don't know what fields are for what) > "enable this connection" > "ok" > change "default gateway device" to wlan0 > "activate" > if you have firewall installed (firestarter or similar), don't forget to set it up to use wlan0. What is tail -f /var/log/messages saying to you? error or info? etc check dmesg | tail as well. 

Hopefully, this will connect you. If it doesn't, see bottom of [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) on how you can set up wireless using the command line (terminal). 

Note: *tail -f /var/log/messages* will give the output of /var/log/messages in real time (as it is written)
*dmesg | tail* will give you the end of kernel messages. the whole thing (all kernel messages starting from the boot) can also be accessed for some nice info on your hardware: *dmesg | less* (use page up and down o navigate, q to quit). if you use *dmesg* by itself only, it will just burst a bunch of info very fast. 

I'm curious about the result.

Note 2: Once you connect, the following output (in bold) of iwconfig will change and give you your ESSID:

```

wlan0     IEEE 802.11g  ESSID:**off/any**
          Mode:Managed  Frequency:2.462 GHz  Access Point: **00:00:00:00:00:00**
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:39   Missed beacon:0

```
The following output of ifconfig (in bold) will also change with relevant info: 
```

wlan0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:**192.168.1.224**  Bcast:**192.168.1.255 ** Mask:**255.255.255.0**
          inet6 addr: **fe80::206:5bff:fee1:ba40/64** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8047052 (7.6 MiB)  TX bytes:665693 (650.0 KiB)
          Interrupt:11 Base address:0xec80

```

sorry for the long post, I couldn't help myself ;)

---

### Post by cantormath on 2006-03-25
you could always

#sudo passwd root

set a root password, then su into root via terminal...

---

### Post by towsonu2003 on 2006-03-25
[QUOTE=cantormath]you could always

#sudo passwd root

set a root password, then su into root via terminal...[/QUOTE]
I'm not sure how this is useful, on-topic, or practical. If you are tired of typing sudo all the time, do like the following ```

sudo -i
iwconfig
ifconfig
exit
``` between sudo -i and exit, you have root privileges in the terminal (and in /root directory) so be very careful of what you are typing. I saw posters here deleting their installation while using root privileges due to typos (*do not post the code for this please*). 
if chose to activate root password (tru the command cantormath gives) please read [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) **beforehand** to better understand the risks.

---

### Post by Papa-san on 2006-03-25
```
john@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:192.168.1.224  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fee1:ba40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:767085 (749.1 KiB)  TX bytes:135528 (132.3 KiB)
          Interrupt:11 Base address:0xec80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:70411 (68.7 KiB)  TX bytes:70411 (68.7 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:2C:52:6B
          inet addr:192.168.1.223  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:f8ffc000-f8ffdfff

```

Step 0  8) Letting it sit...lol

Step1 - ```
john@laptop:~$ dmesg | tail
[4294736.206000] Bluetooth: RFCOMM TTY layer initialized
[4294809.049000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294819.850000] eth0: no IPv6 routers present
[4295645.737000] wlan0: no IPv6 routers present
[4295669.319000] wlan0: no IPv6 routers present
[4295843.040000] wlan0: no IPv6 routers present
[4295942.137000] video bus notify
[4307351.430000] video bus notify
[4307382.022000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4307392.836000] eth0: no IPv6 routers present

```
and:```
john@laptop:~$ lsmod |grep ndiswrapper
ndiswrapper           114376  0
usbcore               104316  3 ndiswrapper,uhci_hcd
john@laptop:~$ sudo modprobe ndiswrapper
Password:
john@laptop:~$ lsmod |grep ndiswrapper
ndiswrapper           114376  0
usbcore               104316  3 ndiswrapper,uhci_hcd

```
Step 3:
```
john@laptop:~$ tail -f /var/log/messages
Mar 25 18:18:48 localhost -- MARK --
Mar 25 18:38:48 localhost -- MARK --
Mar 25 18:58:48 localhost -- MARK --
Mar 25 19:18:48 localhost -- MARK --
Mar 25 19:38:48 localhost -- MARK --
Mar 25 19:58:48 localhost -- MARK --
Mar 25 20:18:48 localhost -- MARK --
Mar 25 20:38:48 localhost -- MARK --
Mar 25 20:58:48 localhost -- MARK --
Mar 25 21:18:48 localhost -- MARK --
Mar 25 21:28:54 localhost gconfd (root-16819): starting (version 2.12.0), pid 16819 user 'root'
Mar 25 21:28:54 localhost gconfd (root-16819): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 25 21:28:54 localhost gconfd (root-16819): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Mar 25 21:28:54 localhost gconfd (root-16819): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Mar 25 21:28:54 localhost gconfd (root-16819): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Mar 25 21:28:54 localhost gconfd (root-16819): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4Mar 25 21:28:54 localhost gconfd (root-16819): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Mar 25 21:28:54 localhost gconfd (root-16819): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Mar 25 21:28:54 localhost gconfd (root-16819): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
```
Then I used Network settings, no changes to above, 'till I clicked 'activate' for wlan0, then this:
```
Mar 25 21:29:57 localhost kernel: [4336621.631000] ndiswrapper (add_wep_key:644): adding encryption key 1 failed (C0010015)

```
dmesg | tail netted this:
```
john@laptop:~$ dmesg | tail
[4295669.319000] wlan0: no IPv6 routers present
[4295843.040000] wlan0: no IPv6 routers present
[4295942.137000] video bus notify
[4307351.430000] video bus notify
[4307382.022000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4307392.836000] eth0: no IPv6 routers present
[4336593.416000] wlan0: no IPv6 routers present
[4336621.631000] ndiswrapper (add_wep_key:644): adding encryption key 1 failed (C0010015)
[4336631.713000] wlan0: no IPv6 routers present
[4336937.100000] wlan0: no IPv6 routers present

```
I think I'll tell my kid to disable WEP, don't ya think?!?
(Sorry about the extreme length of this post, but ya did say you were curious... ) lol

---

### Post by Papa-san on 2006-03-25
However, quite strangely, as I write and post this, I am holding the end of my cat 5 between my teeth! What's up with that?OK, whatever actually ended up happening through all this, it worked. Now I need to figure out how to make it stay, and do it automatically when I boot...set it as a module. (right?)

---

### Post by towsonu2003 on 2006-03-25
[QUOTE=Papa-san]```
john@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:**192.168.1.224**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: **fe80::206:5bff:fee1:ba40/64** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:767085 (749.1 KiB)  TX bytes:135528 (132.3 KiB)
          Interrupt:11 Base address:0xec80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:70411 (68.7 KiB)  TX bytes:70411 (68.7 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:2C:52:6B
          inet addr:**192.168.1.223**  Bcast:**192.168.1.255**  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:f8ffc000-f8ffdfff

```
[/QUOTE]
I see above that you did not de-activate eth0 (ethernet connection), which may be cause of connection problems (I bolded output that shows both are connected). deactivate eth0 first (using "Network Settings maybe?), than activate wlan0... please check the output of sudo iwconfig to see if it gives you the ESSID (which, I think, it will) after activating wlan0. 

as for the wep, you may be entering it wrong. there are two options in "Network Settings", hexadecimal and ascii. I don't know the difference and how to convert one to the other, so you might wanna research that... maybe your sun knows this? I never used a wireless access point with wep (I don't even own one, my school has an open wireless access point...). 

PS. Following is my ifconfig output for eth0, which is NOT in use:
```
eth0      Link encap:Ethernet  HWaddr 00:02:3F:6E:8C:4C
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xa000

```as you see, unlike yours, it doesn't give info on inet addr:; Bcast:; Mask:; and inet6 addr: -> as it's not connected.

---

### Post by Papa-san on 2006-03-27
> see above that you did not de-activate eth0 (ethernet connection), which may be cause of connection problems (I bolded output that shows both are connected). deactivate eth0 first (using "Network Settings maybe?), than activate wlan0...

I did this, and that is when it began to work... It kept coming up as default because I didn't save when I logged off...


Thank you so very much!

I am going to be compiling some of the information in all the posts so maybe a wiki how to could be built, or maybe adding the missing steps to an existing one?!?

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=Papa-san]I did this, and that is when it began to work... It kept coming up as default because I didn't save when I logged off...[/quote] great to hear it's working :)
[QUOTE=Papa-san]I am going to be compiling some of the information in all the posts so maybe a wiki how to could be built, or maybe adding the missing steps to an existing one?!?[/QUOTE]
If you have a manufacturer's product (like pavilion zv5120us rather than self-built computer), you could create a new wiki page at wiki.ubuntu.com and post your configuration notes there. You could also post a howto (specifically for wifi in our system) at the Tips and Tricks section. Or, you could edit the wiki page where ndiswrapper and wlan0 connection are described to include steps they missed (taking down eth0 for instance?)...

This was what you are asking right? I may have misunderstood you :)

---

### Post by az on 2006-03-27
Towsonu2003, YOU DID IT!!!

and the crowd goes WILD!


Woooooooooooooaaaaaaaaaaaaaaaaaaa!  (druken fans cheering!)

And papa-san deserves a tribute for his tenacity!

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=azz]Towsonu2003, YOU DID IT!!!

and the crowd goes WILD!


Woooooooooooooaaaaaaaaaaaaaaaaaaa!  (druken fans cheering!)
[/quote] lol :-D 
[QUOTE=azz]
And papa-san deserves a tribute for his tenacity![/QUOTE]
actually, I've never seen a new user this dedicated/committed :)

---

### Post by az on 2006-03-27
But seriously, a few things struck me in papa-san's posts.  This thread and another one of his previous threads on this topic brought forward some useability issues.

Maybe I'll make a wiki page for really intersting case-studies which show useability problems in things that more experienced usres never think of or take for granted...

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=azz]
Maybe I'll make a wiki page for really intersting case-studies which show useability problems in things that more experienced usres never think of or take for granted...[/QUOTE]
I'd love to see such a wiki page.

---

### Post by Papa-san on 2006-03-27
I have to say that it has been one heck of an experience... 
I did learn a LOT, which seems to be a good thing. Windows users tend not to think about everything (or in my case, anything!)that goes on within the depths of the box... I am currently using a live cd on my wife's system, to see how it works, and to show her how nice this can be.

A wiki page like you mentioned would be a good thing, and please feel free to pick my feeble mind for anything that might aid in it's evolution! 

You guys were awesome with all the help you gave me! I wouldn't have been able to do it without your patience, and your willingness to give up some of your time!
I think that is one of the most awesome facets of this OS... It's not an OS, it's a community!
Thank you, again, and I consider myself hooked!:-D

---

### Post by niranjan on 2006-03-28
Reading through this thread has been a combination of fun, admiration and education, even though I have not been setting up a WLAN on my dapper desktop.

Papa-san you might want to disable ipv6 on your system since it is not supported by your routers. You do that by editing aliases file and turning off ipv6.

```
sudo nano /etc/modprobe.d/aliases
```
then go on to the following line
alias net-pf-10 [COLOR="Red"]ipv6[/COLOR]
replace ipv6 with [COLOR="Red"]**off**[/COLOR]
press Ctrl-X , answer y and you are done.

I salute your tenacity, and admire the patience of all those who have helped on this thread.

---

### Post by az on 2006-03-28
[QUOTE=towsonu2003]I'd love to see such a wiki page.[/QUOTE]

A lot of people do useability testing.  The way the forums attract inexperienced users makes it a nice place to find useability issues.  I'll see about making that wiki page in the next few days....



[http://www.nat.org/2005/may/](http://www.nat.org/2005/may/)

From Nat Friedman's blog concerning useability testing:

"We've all read about the benefits of usability testing, but until you actually try to sit still through two hours of these videos, it isn't a visceral experience for you. It is exciting, and totally emotionally exhausting. You squirm. And it focuses you like a laser. 

For example, we asked a lady to send mail to a friend. Against all odds, she started Evolution (nothing in the menus indicates that it's a mail program; something we hadn't realized before but which was immediately obvious after watching her stalk one-by-one through the menu items muttering to herself along the way). 

The correct next step would have been for her to click on the "New" button that's in the upper-left-hand corner of the window. This button didn't even register for her, however. Instead, because she wanted to "send" a mail, she clicked repeatedly on the "Send" part of the "Send / Receive" button just to the right. For about a minute. "



I have to descibe reading the threads by papa-san trying to solve this problem as "a visceral experience."

---

### Post by az on 2006-04-03
[https://wiki.ubuntu.com/UsabilityCaseStudies](https://wiki.ubuntu.com/UsabilityCaseStudies)

---

### Post by Papa-san on 2006-09-02
This was a long time ago... However, with all the issues created with the upgrade to Dapper, I was forced to revisit this thread to try to re-establish wireless through ndiswrapper. I was reading through, and noticed that right around post #35, the driver name I was working with changed... Not sure where I got it or how, but the bcmwl5a that I had been trying wasn't going to work. At some point, I must have got ahold of the bcmwl5 driver, and because I did the same steps with the right driver, it worked. I don't know why I ended up changing them, but I had a lot of irons in the fire at the time. 

At least now I have learned to get the proper driver off my Dell drivers disc. (For the life of me, I couldn't figure out how to get into an .exe file.) This has simplified the whole thing. I edited a post in an earlier part of the thread to show how to do this. Maybe someone will find it in a search sometime...

Anyways... Kudos to all who make themselves available to us n00bs here! We COULDN'T do it without you!

---

