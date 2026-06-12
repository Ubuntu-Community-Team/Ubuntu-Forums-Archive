---
title: "Network ubuntu and XP pro"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-05-23
Hi, I have ubuntu on one box and xp pro on another. They are connected to my 4 port router and both have access to the net.

I want to create a network between ubuntu and xp.

I am familiar with networking xp boxes.

I can see my xp box in ubuntu but I have the following error message when I click on the icon:

"The folder contents could not be displayed.

Sorry, couldn't display all the contents of
"Windows Newtwork:name".

I have also tried to create a shared folder on ubuntu, eg:

Folder name "name", right mouse click "Share folder".

"Share with: SMB
Share properties
Name: [what does Name refer to? I put anything in here, eg, "hello"]"

tick next to  "Allow browsing folder".

"General Windows sharing settings"

"Host description server (Samba, Ubuntu)"

WINS server.

[I have no idea what I should do here].

So basically I am stuck and need assistance.

Thanks.

---

### Post by manicka on 2006-05-23
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by u.b.u.n.t.u on 2006-05-23
Thanks for the link but it doesn't really help me.

I found "Mshome" on my XP box "ubuntu server (Samba, Ubuntu)(Ubuntu".

I click on that and it asks me for a username and password. I type that in, and I  am denied access. It is what I type in to access Ubuntu at login.

So it is some other uername and password but what? This is totally confusing.

The instructions may as well be in Chinese!

"For example:
file.png File:/etc/samba/smb.conf

netbios name = kenny_smb_server"

In plain English, what does this mean?

Ubuntu looks great "Dapper Beta" but it still a pain in the neck to use. Simple things are fine as long as you know how, maybe.

It takes a few right mouse clicks to network XP with XP and after several hours I still haven't managed that with Ubuntu.

What is needed are some BASIC step by step instructions and not assuming people have all this knowledge.

Ubuntu is one problem connected to another problem connected to another problem. Very little is explain that makes easy reading and sense.

What is wrong with right mouse click, then "yes" share folder, etc? Why is that approach not used?!

The passwords are another pain, but how to turn them off? I have no idea. I hate having to enter a username and password every 5 minutes.

Not a good experience so far. Ubuntu is still TOO difficult. It is NOT user friendly.

I will persist but it is very frustrating. Little wonder people stay with Windows.

---

### Post by manicka on 2006-05-23
[QUOTE=u.b.u.n.t.u]

What is wrong with right mouse click, then "yes" share folder, etc? Why is that approach not used?!

The passwords are another pain, but how to turn them off? I have no idea. I hate having to enter a username and password every 5 minutes.

Not a good experience so far. Ubuntu is still TOO difficult. It is NOT user friendly.

I will persist but it is very frustrating. Little wonder people stay with Windows.[/QUOTE]
OK, sorry, I didn't realise that you need more help than just in the how-to.

in the how-to where it says

 sudo apt-get install samba

and 


 sudo gedit /etc/samba/smb.conf

you need to run these commands in a terminal. To access a terminal go to

Applications --> Accessories -> Terminal

then type the commands in the terminal window.

Once you have the smb.conf file open you should be able to find the section that need editing as per the how-to

make the changes, then run the command (in a terminal) to set your samba passowrd. 

reboot your machine and all should be well to access your ubuntu box from xp.

As to your other points. Linux isn't windows and isn't designed to be. The reason you are asked for a password so often is to protect your system and make it secure. There is a reason that linux doesn't haven't as many viruses and security flaws as Windows, you are just experiencing it :) . Once you get use to it you'll really enjoy the peace of mind that it brings.

Anyway, happy ubuntuing :)

---

### Post by bigken on 2006-05-23
In the terminal do
[B]sudo smbpasswd -e yourname 
[/B]this will allow you too change samba password and [B]
sudo smbpasswd -a yourname[/B] 
will adds users
you might need to  do  **apt-get install  samba **1st ;)

---

### Post by RudolfMDLT on 2006-05-23
First install Samba. 

I hope you have made a backup copy of the Samba config file! :)

Then go to this topic

[http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityuser](http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityuser)

(This is a very good HOW TO guide for almost anything!) 

Follow every blue link in the steps to make sure you know what you are doing is right.

Then in the terminal do what bigken said

1) sudo smbpasswd -e yourname
2)Type and retype new Samba password
3)sudo smbpasswd -a XP username
(the usernames of your network users)
4)Type and retype their passwords

I don't know whether you use a Domain or Workgroup in XP
but make sure that these names are the same on both the
XP machines and the ubuntu machine. 
System => Administration => Shared Folders
Pick any shared folder or share one now
click properties
click General Windows Sharing options
Under domain/workgroup enter in your XP workgroup
Also disable the wins server.

On the windows side, make sure that the folders that are shared don't
require passwords to login to via the other XP machines.

I feel your frustration! I had the exact same problem for 3 days but sorted it out last night, stick with Ubuntu, it's worth it!

If stuff gets really hairy click on the bold RudolfMDLT link in the top left of this message and drop me an email.

---

### Post by u.b.u.n.t.u on 2006-05-23
Thank you manicka, bigken, and RudolfMDLT for that. I will start first thing tomorrow and try to follow your suggestions.

A few years ago I played around with linux and networked no problem. I regret not keeping my notes.

"The reason you are asked for a password so often is to protect your system and make it secure." - Protecting me from myself? :-k  After I network ubuntu the next step is no more passwords, if possible.

I played around with firebird and later firefox. Waiting and hoping for the day that I can comfortably migrate over from IE. I have used firefox since about version 1, and now use it in it's portable flavor. 

I desperated want to migrate over to linux. I looked at ubuntu about 18 months or 2 years ago. When it first started and it looked like it had a lot of potential. Though the icons were ugly and it wasn't good enough to move to.

Ubuntu Dapper Beta looks awesome. The icons are Mac XP/Vista quality. Now  if only I can learn how to use it properly without too many problems.

I am going to try my best to push through the linux pain barrier. Only games will keep me with XP but everything else I can do on linux I think (hope).

I'll post to let you know how I go.

Thanks again.

---

### Post by u.b.u.n.t.u on 2006-05-23
"In the terminal do
sudo smbpasswd -e yourname
this will allow you too change samba password and
sudo smbpasswd -a yourname"

I did this and now I can see and access ubuntu from XP but I still can't access XP from ubuntu.

So now I have 2 passwords. The login and the one I just created for samba.

I moved over an mp3 to enjoy some music from ubuntu but it tells me I need to install a mp3 decoder. Now to search and google madly to learn how to do that simple task. ](*,)

---

### Post by RudolfMDLT on 2006-05-23
Getting rid of some of the passwords is also in the guide that I posted. You only need passwords when configuring things and that will come to an end soon enough.

But passwords are good. You'll find out the more you play in Linux, it's very powerful and customizable, sometimes a password or having to type sudo before every major command will make you think twice about what you want to do. Windows has very little password protection and very little system protection, thats why it's so easy to stuff it up or for a Internet app to install spy ware, add ware and who knows what else! On my XP system I had zone alarm, spybot – search & destroy and tea timer running 24/7 just to keep websites from installing junk on my system.

One last thing don't compare Windows with Ubuntu. You've probably been using windows for your whole life and ubuntu for less than a month. Compare them after 6 months and see which you prefer! Even setting up a network between the two platforms will become child's play! Dapper is due soon and we'll see what happens...

PS: Try getting support like this from Microsoft - People around the world taking time off to help you personally for free! Think about it!:rolleyes:

---

### Post by popkid on 2006-05-23
> =u.b.u.n.t.u

I did this and now I can see and access ubuntu from XP but I still can't access XP from ubuntu.



A couple of things to check:

In XP, have you actually chosen to "share" any folders (right click on folder and there should be an option "sharing" or some such)

Also in XP, is your machine allocated to a workgroup, if not, I think it you need to create one

Also in XP, in network connections, bring up the network properties for your network card or wireless card, go to networking --> Network Protocol TCP/IP -->  properties --> WINS, and click on "enable NETBios over TCP/IP"

Reboot your XP Machine.... Think this should all work!

pK

---

### Post by Iowan on 2006-05-23
[QUOTE=u.b.u.n.t.u]
I moved over an mp3 to enjoy some music from ubuntu but it tells me I need to install a mp3 decoder. Now to search and google madly to learn how to do that simple task.[/QUOTE] Check around the forum and wiki, too.  Some formats aren't free, so they aren't included by default - although they are still available.

---

### Post by RudolfMDLT on 2006-05-23
Check your thread on mp3 that you posted:D

---

### Post by u.b.u.n.t.u on 2006-05-25
Hi, I am stuck.

Here is a check list of what I have done.

* installed Samba
* XP pro has full access to Ubuntu Dapper Beta2, full access to my test share folder on Ubuntu
* Sygate on XP doesn't seem to be the problem as I have another XP box networked with no problems
* Netbios has been enabled in for my ethernet connection (Internet Protocols TCP/IP)
* Ubuntu can see my XP workgroup and computer name but no further. I have shared folders set up

Is there a place in Ubuntu where I can type in the path to XP?

Would a ping be of any use from Ubuntu to XP?

Any suggestions are welcomed.

Thanks.

---

### Post by Iowan on 2006-05-25
[QUOTE=u.b.u.n.t.u]
* Ubuntu can see my XP workgroup and computer name but no further. I have shared folders set up [/QUOTE]How are the shares set up (permissions and access in particular)?

---

### Post by u.b.u.n.t.u on 2006-05-25
On XP, I right mouse click on a folder / Properties / Sharing / Network sharing and security / a tick in both boxes.

That is all I need to do to network XP boxes. (Oh and permissions in sygate).

I seem to remember a path in some linux window that shows the route to XP. 

Ok something good just happened. I have 3 boxes. 2 XP and 1 ubuntu. Ubuntu can see and access my other XP box. That is running the same security setup as the one that does not work.

So I have 2 XP pro boxes with sygate. Ubuntu is networked with one box but not the other.

The box that works with ubuntu has DMZ enabled. The box that doesn't work needs certain ports to be allocated access for certain programs.

I am begining to think it may be the router (D-link 4 port DSL-504G).

Suggestions are welcomed, thank you.

---

### Post by u.b.u.n.t.u on 2006-05-25
My boxes are networked through my router. Ubuntu can see the XP box where the IP is in the DMZ (all ports exposed to the internet). Ubuntu cannot see the other box XP.

However, the XP box that Ubuntu cannot see, that XP box, it can see Ubuntu. Ubuntu and this XP box have the same router settings.

I am probably missing something obvious and welcome any suggestions.

---

### Post by user1397 on 2006-05-25
i'm almost positive that it's a port/firewall problem, cause i had a very similar problem very recently, actually like an hour ago, lol.
did you install firestarter?
if you go to your router setup, what ports are enabled/disabled?

---

### Post by u.b.u.n.t.u on 2006-05-25
I haven't installed firstarter yet. I have changed the DMZ from the XP box that Ubuntu can access to the XP box that Ubuntu cannot access. No difference.

So it doesn't seem to be a port issue after all. I ghosted to my XP from about 10 days ago and that hasn't helped either.

One thing I did notice however, my XP box would take many (10+) tries to get back an internet connection after making changes to my router. The few times I tried this on Ubuntu, it worked almost immediately. This is something, if repeatable, will make me very happy as I alway dread making changes to my router because it is so difficult to get a connection afterwards.

Can I use ping? If so how? To test?

Can I use a url eg "smb://whatever else goes here" to access my XP box what doesn't want to network? If so how.

Thanks.

---

### Post by user1397 on 2006-05-25
in a terminal (applications->accessories->terminal), you would type:
```
ping *computername*
```
or 
```
ping *ipaddress*
```

As for the other thing, go to nautilus (applications->accessories->file browser), and press CTRL+L, and type smb://*ipaddress *or smb://*computername*

---

### Post by u.b.u.n.t.u on 2006-05-25
Hi Erik,

Thanks.

"Home Folder", "ctrl-L" works well to test.

smb://10.1.1.3 works (Ubuntu can connect to this XP box)

smb://10.1.1.2 does not work (Ubuntu cannot connect to this XP box)

Is there any way to always display the full path address bar? Toggle ctrl-L on/off?

I may have to ghost back to the first complete install of XP. I can't figure out what the problem is. The security settings are idential.

---

### Post by u.b.u.n.t.u on 2006-05-26
Problem solved!

First a huge thanks for all the suggestions. Without your support I would have given up. So thanks everyone!!! 

The problem was that the path from Ubuntu to XP was in complete!

Eg

Error (before)

smb://computer-name

Correct (after)

smb://computer-name/hdd-name
(where the entire HDD is shared)

or even

smb://computer-name/folder-name
(where a folder is shared)

The path was incomplete. So it couldn't connect. Moral of the story, set a full path.

"ctrl-l"  in "file browser", actually "Home Folder" on the desktop did the trick. I won't forget ctrl-l for a while. I want to see it all the time when I browse lol.

I am so pleased.

Ubuntu - XP fully networked
2nd HDD formated and mounted

I feel like I climbed Mount Everest today!

:mrgreen: 

I even learned to change my cumbersome login password to something simple.

Now for tomorrow:

* HDD links to the desktop
* installing a firewall
* migrating firefox and thunderbird over

I am really happy with my progress today :-D

Thanks agains everyone that helped.

---

### Post by manicka on 2006-05-26
I'm glad things worked out well for you. Good luck with your next challenge/s :)

Let us know if we can help

---

### Post by u.b.u.n.t.u on 2006-05-26
Thanks manicka.

It helped a lot that some time ago I switched from IE and Outlook to Firefox and Thunderbird.

Now it is the turn of my IM. Gaim is great but their font size bug (very small font - has to be hacked with a dll and even that doesn't work with their latest beta), just makes it impractical to use. I was testing aMSN last night and it works well. Several years ago all my friends and I standardised our IM to MSN. I need 2 hacks to get MSN IM where I want it. Too much already! So I am testing aMSN.

I will still have XP running but that will be purely for games. Maybe an external USB HDD with XP that I can use for gaming.

________________________
Some more reflections below
________________________

I write HTML code and use Editplus. It is awesome, but I can give it up. There are a few cool linux editors to try out.

I use bsplayer free, not the ad one they snuck in! That can go.

I use Filezilla for FTP. Any FTP will do, not important.

I use Word. Well stuff that. I like Abiword and if anyone complains then THEY can change! "Sorry your word document looks all weird" - "Install Abiword to see it properly or don't worry!" Time to make a stand.

Why does Vista need more CPU power, more RAM, and more HDD space than XP? Security? A nice desktop? I just don't get it. Vista runs like a snail from what I hear (ok it is a beta but still) and they want money for this? Sure XP is better than 98 but Vista isn't something that new.

Compare that with Ubuntu which from Dapper looks really nice (and that is very import - that is why people buy BMWs and Mercs if they have the money and not Fords and Holdens). Looking great is essential. It is a human experience. With Dapper, Ubuntu have moved into the class of OSX and XP. Even 5.10 wasn't good enough in my view.

So I am using a beta, Dapper and it is great. I have many friends for whom I am the local computer guru (obviously not for linux). So as soon as I figure out how all this works I will do my best to help them switch. They aren't gamers so it should be easier than for me.

Is Vista the best thing M$ have done for Linux? How many more times the resouces does Vista need over Ubuntu Dapper? Two? Three? And for what?

Windows will be reduced to a gaming experience in my world. Ubuntu will be elevated to a day to day computer experience.

What we really need are some professional Ubuntu training videos! Free of cause. A library of them. From the basics to the more advanced.

Show someone a well presented Ubuntu video and they will have a positive experience. Show someone the pages and pages of "helpful" text pages and they will reach for the headache tablets.

Without this forum I would have given up already. I think Ubuntu need to consider enlisting some professional people (as volunteers) to start a training video library.

My suggestion is English speaking (not American) persons, well presented. I won't say what not to do as I don't want to offend the Americans here - lets just say that some fat dudes in t-shirts and long hair don't really cut it for being "professional". I would love John Cleese to do these - I am a huge fan of his Basil Fawlty days.

These are just my views, suggestions - something I am putting on the table for people to consider, accept or reject what they want. No offence meant.

Thanks everyone.

:-D

---

### Post by rodrigo666 on 2006-06-03
Greetings, I am using Ubuntu for about twoo weeks and was searching for a way to share my HD's in Ubuntu for my other Windows XP in my network.

This thread come really handy. I didn't have all that problem to make Ubuntu access the Windows XP machine, but as I'm writting this words Samba is getting installed on my Ubuntu.

Well, the mainly reason why I wanted to writte this is that I found myself with many things in similar with u.b.u.n.t.u. and share some of his early opinions (as Ubuntu not that user-friendly).

But still, I also has his force of will to keep going and go to next level with Ubuntu. Soon I want to get rid of Microsoft and I truly believe that Ubuntu is the way.

Many thanks to all of the experienced users that replyed to this thread and to u.b.u.n.t.u. who asked something I was searching for.

---

### Post by u.b.u.n.t.u on 2006-06-03
Good to hear rodrigo666. You may want to search my username as I have covered some other areas too like installing a 2nd HDD (hard disk drive). Where the community have helped solve problems.

The HDD I found the most challenging. Just because it is so different.

Cheers.

:D

---

### Post by Lomz on 2006-06-04
I have problems with giving spesifications to my folders in samba concerning how to share them.
I have a tread for it here: [http://ubuntuforums.org/showthread.php?t=188987]("http://ubuntuforums.org/showthread.php?t=188987")

---

