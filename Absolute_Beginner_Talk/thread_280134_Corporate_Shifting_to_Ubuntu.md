---
title: "Corporate Shifting to Ubuntu"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Abhi Kalyan on 2006-10-19
**Introduction:**

Good day,
Am new here and will take some time to catch up with the culture.

**Subject:**

Shifting an entire company from Windows XP to UNBUNTU!

**The Issue in Detail:**
We are an organization of 150 people from India, We manage Construction projects, Basically Project Management Consultants.

one of my colleagues and I have suggested to our MD that we should shift to Linux. We chose UNBUNTU.

It would be of great help if any one can guide us towards any case studies or project of this magnitude. So as to aid us in a smooth conversion.

**The problems:** 
Maximum of the people involved fall under the age group of 35-55.
everyone here have been using Microsoft XP for quite a long while.
we use softwares such as
Microsoft Project 
Autocad
CAMPX
Tally 
We are interested in finding out alternate softwares, and or the possibility of running these windowes based softwares in ubuntu

**Immediate Problem:**
1. How to get gnome running in the server taht we have installed(LAMP)?
2. How to access windows file shares?
3. How to connect to our local Active Directory Domain(run on windows 2003)?

**Closure:**
I understand this is a set of very dedicated people,
So i would not want to burden anybody.
All we hope is for somebody to point us in the right direction.
And after following the way ubuntu is run and the forum messages, I have no doubt about not getting help.
TIll then i will keep searching and keep waiting
Thank you

---

### Post by Iarwain ben-adar on 2006-10-19
Hi Abhi,
welcome!

First of all,
i don't know much, but i only try to help :)

To get Gnome running, try to install ubuntu-desktop, like this
```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```
This updates (sudo aptitude update) your sources, and installs (sudo aptitude install ubuntu-desktop) Gnome.
You enter this in the terminal (the dos-like interface ;) )

To acces your windows shares, try [this]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29%7C%28shares%29")

As for the other problems, i don't know, sorry


Iarwain

---

### Post by dolphinsonar on 2006-10-19
You might have a little more success in getting answers by making a seperate forum post for each individual issue (that has not already been posted in previous forums).  Just a thought.

Welcome to the community!

---

### Post by Foudre on 2006-10-19
as far as culture goes, no need to be so formal here on the ubuntu forums. I know there are cad programs for linux, i can see it in my head but no names come forth, i can't really tell you about those type of programs but i can tell you that there is something called wine.

wine is a windows emulator type thing (its not technicly an emulator but it is close to being one) 

perhaps if you had just a spare computer you could install ubuntu and use it as a testing computer. Try running the programs you already have under wine.  as well as finding new equivilent software availible or if there are linux version for the same software availible.

to do this you'll need of course install ubuntu on a computer, setup an internet connection, and  then add/remove programs check the boxes that say unsupported software, and do not remember what the other one says buts they are next to each other check them both. Find wine, check it, apply and hit apply it'll tell you it has to activate a certian repository tell it ok.

next open a terminal, type wine
it should set it self up, if not type winecfg
now type wine 
insert a space
insert the disk that has the software you want to install meant for windows, or what ever the install source may be. Right click on the installer, hit copy and paste on the terminal; you may aslo just drag the installer over the terminal
hit enter

the installer should be trying to run. let it run test the program out, you have issues with it you can try to change some settings for wine by going to the terminal and typing
winecfg
the easiest thing you can do is change the windows version you trying to mimic and see if the program works any better, tweak some setting around and see if the program works

repeat for each program. 

for anything an employee would do working on the computer from the desktop would be about the same as from windows, with some improvements (multiple desktops, where they can have every program open maximized or adjusted the way the want and simply change desktops between programs, very good for research). And ubuntu is very self explainitory so people gettin used to it shouldn't be that hard, even at that age.

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Mr.Iarwain ben-adar, very kind of you to pitch in.
Will try out the options and keep posting on the goingone.
Thank you once again.

---

### Post by Abhi Kalyan on 2006-10-19
Thank you dolphinsonar,
Thats a grand idea, I ' ll follow this method.

---

### Post by Ashrael on 2006-10-19
Abhi Kalyan:

For CAD, maybe use QCAD??

for the rest i have no experience with migrating a whole company to ububtu, but it might be good to use dualboot at first, at least until you get all the issues solved...

hope this is usefull....

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Mr.Foudre
I seriously am overwhelmed by the responces which have been posted by you and the community as a whole.
Following is the scenario underwhich we are operating right this minute.:
“Currently we have installed dapper drake on a good system, and are testing on it.I will work on wine and will keep posting on the updates”
“as a pilot project we had couple of people who were put on this system and Personnally, i was awe struck to see these people getting used to ubuntu, The reason for my surprise was that all these people were essentially against this change and after working on this OS for about half an hour each one of them opted to vote for UBUNTU, they were terribly impressed.”
- As an After thought, is there some place where i can post this original incident so as to help people choose ubuntu.?”

---

### Post by Anonii on 2006-10-19
Of course, [this would be the forum to do that.]("http://ubuntuforums.org/forumdisplay.php?f=103")

Also, for people who suggest QCAD: As far as I know, QCad is not free (both as beer and as speech). And since I guess that they changed to Linux for economical reasons, QCad should be the worst case scenario, imo.

---

### Post by gn2 on 2006-10-19
> **Abhi Kalyan said:**
> **Introduction:**

Good day,
Am new here and will take some time to catch up with the culture.

**Subject:**

Shifting an entire company from Windows XP to UNBUNTU!

**The Issue in Detail:**
We are an organization of 150 people from India, We manage Construction projects, Basically Project Management Consultants.

one of my colleagues and I have suggested to our MD that we should shift to Linux. We chose UNBUNTU.

It would be of great help if any one can guide us towards any case studies or project of this magnitude. So as to aid us in a smooth conversion.

**The problems:** 
Maximum of the people involved fall under the age group of 35-55.
everyone here have been using Microsoft XP for quite a long while.
we use softwares such as
Microsoft Project 
Autocad
CAMPX
Tally 
We are interested in finding out alternate softwares, and or the possibility of running these windowes based softwares in ubuntu

**Immediate Problem:**
1. How to get gnome running in the server taht we have installed(LAMP)?
2. How to access windows file shares?
3. How to connect to our local Active Directory Domain(run on windows 2003)?

**Closure:**
I understand this is a set of very dedicated people,
So i would not want to burden anybody.
All we hope is for somebody to point us in the right direction.
And after following the way ubuntu is run and the forum messages, I have no doubt about not getting help.
TIll then i will keep searching and keep waiting
Thank you


Have you correctly factored the costs?
Re-educating the staff to use different software may take quite some time, and in business time is money.....

That said there is no reason for not switching, and you will always get help on this forum 24/7.

---

### Post by Perfect Storm on 2006-10-19
> Have you correctly factored the costs?
Re-educating the staff to use different software may take quite some time, and in business time is money.....


Longterm investment, so in the end it's costs less in the end. After the re-education. It's allmost "cost-free".

---

### Post by gn2 on 2006-10-19
> **Artificial Intelligence said:**
> Longterm investment, so in the end it's costs less in the end. After the re-education. It's allmost "cost-free".

Not if the re-educated staff move on to another employer......

---

### Post by Perfect Storm on 2006-10-19
> **gn2 said:**
> Not if the re-educated staff move on to another employer......

That's always a risk, like every other investments. But note that when every one is re-educated it's easier and cheaper to learn a new staff member up and it's highly not gonna happen that every staff members leaves from one day to another. It's normal that there's a shift in staff once in awhile and a new person needs to learn, but that's like everything else.

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Mr.Anonii,
Incidently i just found that out just now, got a trial copy and am testing it right away- One problem am having is that the folder where i extracted it is where i have the icon to start qcad'. And the add and remove applet ( i dont know what it should be called) does not have a provision to install the app, Am ready the documentation on installation in ubuntu. Thank you once again

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Mr.Ashrael,
The management is currently doing the balancing act. How they do it is they look at technical variables involed, once that is done the added cost of training and deployment cost. They stretch it over a period of say 6 months, and if this falls below the cost incured during the past six months due to crash, infection, downtime software cost cost (etc) then they would green light a massive overhauls shift , this still stretched over a certain months.
So as of now There are two guys in our Head Quaters who have their fingers crossed. One of them is Nidheesh our sys admin, the other is Me.
Thank you once again for the support

---

### Post by gn2 on 2006-10-19
> **Artificial Intelligence said:**
> That's always a risk, like every other investments. But note that when every one is re-educated it's easier and cheaper to learn a new staff member up and it's highly not gonna happen that every staff members leaves from one day to another. It's normal that there's a shift in staff once in awhile and a new person needs to learn, but that's like everything else.


The costs of initial and continuation staff training and potential for loss in productivity while they got to grips with the new software would very quickly outstrip any ongoing software costs.

If it was my business and was running profitably there's NO WAY I would countenance such a wholesale change.

From what I can see this business may just need better administration of the systems already in place.

Only giving my opinion which the O.P. is entirely free to disregard.
.

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Mr.Iarwain ben-adar,
That was some thing grand that you have given, i could have access only to tty1 and from there ran the sommand given by you , its starting to download now,. Will keep posting.
Thank you once again.

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Mr.gn2
That is a very valuble poitn whihc is some thing that the management is working on, while having this point in front our Managing Director had this to say
"There is always this risk of them learning and then leaving, But what would happen if they did not learn and decided to stay?" 
So, If its good, even if it costs marginally more, then to improve seems to hold a ground which is better for the whole breed. Thank you once again. Will keep posting as events happen.

---

### Post by Anonii on 2006-10-19
> **Abhi Kalyan said:**
> Thank you Mr.Anonii,
Incidently i just found that out just now, got a trial copy and am testing it right away- One problem am having is that the folder where i extracted it is where i have the icon to start qcad'. And the add and remove applet ( i dont know what it should be called) does not have a provision to install the app, Am ready the documentation on installation in ubuntu. Thank you once again
The add/remove applet, will only help you install applications that APT (the packaging system) has approved. 
You could aswell install QCad using the command 
**sudo apt-get install qcad**
in a terminal, which you can open by pressing "Alt+F2" and then executing "gnome-terminal". I guess that you are familiar with DOS, and you will have some basic experience with command line. 
You can easier install qcad the same way, but using a GUI (a graphical interface), but I havent really used that program , so I cant help you with that.
Your Add/Remove application, **should** had a QCad install, tho. I just opened it up, searched for QCad, and a QCad package popped up. I guess that double clicking it, would install it.

Good luck, and sorry for not explaining it better :/

(BTW, lets stop the marketing discussion and help the thread starter. Corporations always involve _risk_ , and I guess that his corporation took it in account.)

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Mr.Artificial Intelligence,
Yes it is cost free, and the reason why we want to switch accepts the cost factor with a lesser priority in comparision with stability, support, customisability. The latter three had originally prompted us to go for linux, After that The cost point waded in and ruled the roost by tipping the table, atleast along the minor verticals. We are waiting for a full fledged shift order within the week of a fortnight.Thank you once again.

---

### Post by Abhi Kalyan on 2006-10-19
The truth cannot be better stated than what you have expressed AI ( if i could call you that), and in the shade of things the comment by gn2 is very much valid, in that as "gn2" the training and the attrition could outstrip the savings.
point 1: Cost is a problem, and the downtimes that we face in our setup is comparatively small-like server failes twice in a month.
point 2: We have a full fledged internal training department, incidentaly i head that department.
point 3: The cost of training is seen as an investment as it brings the employees closer and makes them feel one.
point 4: The forecasting that we had done on the availability of SF and the impending licencing cost + factors such as current technical skill of employees ( we have to any way train a major chunk of our employees in Windows, so it is much the same if we did the same with Linux)
Looking at all these points and a few more , we proposed to the management to shift to linux within the next fiscal year.
Thats were we stand now. The Information and the concern that this forum is providing is certainily brilliant. Thank you

---

### Post by Grey on 2006-10-19
QCAD Community Edition is in the Universe repositories.  It's a GPL version of QCAD that (according to the QCAD site) lacks a few features from the full version, such as support, polyline, and scripting.  I haven't ever had any professional experience with CAD programs, so I don't know how valuable those are.

But to install the free version of QCAD, you must first enable the universe repositories.

1) Programs->Accessories->Terminal

```

sudo gedit /etc/apt/sources.list

```

Edit the text file by removing the comments (#) before the universe repository lines.

2) Install QCAD
```

sudo apt-get install qcad

```

That should install the community edition, for you to try out.  To get the commercial trial running the way you want to (with a shortcut, and installed to the right place (/opt), is a little more difficult to explain, but I, or someone else will explain it to you if you would like to know how.  :)

---

### Post by Anonii on 2006-10-19
> **Grey said:**
> QCAD Community Edition is in the Universe repositories.  It's a GPL version of QCAD that (according to the QCAD site) lacks a few features from the full version, such as support, polyline, and scripting.  I haven't ever had any professional experience with CAD programs, so I don't know how valuable those are.

But to install the free version of QCAD, you must first enable the universe repositories.

1) Programs->Accessories->Terminal

```

sudo gedit /etc/apt/sources.list

```

Edit the text file by removing the comments (#) before the universe repository lines.

2) Install QCAD
```

sudo apt-get install qcad

```

That should install the community edition, for you to try out.  To get the commercial trial running the way you want to (with a shortcut, and installed to the right place (/opt), is a little more difficult to explain, but I, or someone else will explain it to you if you would like to know how.  :)
Holy shit, I forgot to mention the uncommenting of the repositories :/
Thanks for mentioning it, Grey.

**@Abhi Kalyan:**
A repository is a place where Ubuntu stores information on how to install specific programs. By default some of them are disabled. This can be managed by uncommenting them (By removing the # in front of them) from the config file where they are located. That config file is located in /etc/apt/sources.list . Read more info on:
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

Dont start removing the "#" in front of every line, most of them are real comments, on how the config file works.

After you uncomment that, and you open the add/remove applet. Search for Qcad, it should find it. Double-click it. And it should install itself!

---

### Post by gn2 on 2006-10-19
> **Abhi Kalyan said:**
> The truth cannot be better stated than what you have expressed AI ( if i could call you that), and in the shade of things the comment by gn2 is very much valid, in that as "gn2" the training and the attrition could outstrip the savings.
point 1: Cost is a problem, and the downtimes that we face in our setup is comparatively small-like server failes twice in a month.
point 2: We have a full fledged internal training department, incidentaly i head that department.
point 3: The cost of training is seen as an investment as it brings the employees closer and makes them feel one.
point 4: The forecasting that we had done on the availability of SF and the impending licencing cost + factors such as current technical skill of employees ( we have to any way train a major chunk of our employees in Windows, so it is much the same if we did the same with Linux)
Looking at all these points and a few more , we proposed to the management to shift to linux within the next fiscal year.
Thats were we stand now. The Information and the concern that this forum is providing is certainily brilliant. Thank you


If the staff are not coming to the business fully trained ready to go in Windows, then the costs of training in Windows or Linux are the same.
So you would possibly benefit from a switch.

You seem to have a good grip of employee engagement, giving staff skills at work which give them benefits at home would certainly be a great motivator, by that I mean your staff will be able to use Linux at home and reduce their own personal software costs.

Happy staff = productive staff

As a member of a trade union and former staff union representative, I would suggest you give the staff information about the proposed changes and seek their views. Maybe pass out some free Ubuntu discs from Shippit? 
[https://shipit.ubuntu.com/login](https://shipit.ubuntu.com/login)
.

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Mr.Grey, (Should i use Ms. Instead?it is because of the picture on your comment)
I will do the above command update on the events while installing qcad.
as for the shortcut being at the right spot, If it is not very much trouble this is something i would love to know,:)

---

### Post by Abhi Kalyan on 2006-10-19
Wow Anonii, Thanks a tonne. Will do it First things.
Thank you grey

---

### Post by Anonii on 2006-10-19
> **Abhi Kalyan said:**
> Thank you Mr.Grey, (Should i use Ms. Instead?it is because of the picture on your comment)
I will do the above command update on the events while installing qcad.
as for the shortcut being at the right spot, If it is not very much trouble this is something i would love to know,:)
If you follow Grey's advice dont forget to execute the command: 
**sudo apt-get update**
after editing your /etc/apt/sources.list file. This will make your system notice the repositories you enabled.

So do this:

1) _Edit the file as Grey said_
2) **sudo apt-get update**
3) **sudo apt-get install qcad**

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Anonii, that was very nice-
Am searching for some documentation regarding repostory, this place seems seriously huge!!

Anonii, i have done something

- iwent to

system
administration
software properties 
and i check marked all available channels,
Currently the system is updateinf files
Is this leading toward serious implications?

---

### Post by Anonii on 2006-10-19
> **Abhi Kalyan said:**
> Thank you Anonii, that was very nice-
Am searching for some documentation regarding repostory, this place seems seriously huge!!

Anonii, i have done something

- iwent to

system
administration
software properties 
and i check marked all available channels,
Currently the system is updateinf files
Is this leading toward serious implications?
If you mean "Software Sources", (I dont have any "Software Properties" in that menu) you did exactly what me and Grey said, but in GUI. Thats great, and alright.
After the update of the files, you should be able to install Qcad using the Add/Remove.
Report back with your results!
Thanks!

---

### Post by 3rdalbum on 2006-10-19
Mr Kalyan, this is completely normal and nothing to worry about. Ubuntu is just updating its list of software that is available for you to download.

---

### Post by Grey on 2006-10-19
**Anonii**, thanks.  I can't believe I forgot the update.

**Abhi Kalyan**, I'm a Mister, I just tend to favour female avatars.  (no sexual motivation, I just prefer them.  Taki is awesome).  But you can just call me "Grey". (Mr. Grey sounds a little awkward to me).

Okay, here's a basic rundown on how to install software the "right" way, when it isn't in the package manager.  (The package manager will only include free software.  If you want to install something commercial or nonfree, you have to do it yourself).  There are gui methods to do what I am about to say, but I will explain how to do it on the command line, as it's a whole lot easier to explain in text form.

1) Open up a terminal
2) (assuming you downloaded the file to the desktop)
```
cd Desktop
```
3) extract the file to /opt:
```
sudo tar xfvz qcad-2.0.0.0-1-demo.linux.x86.tar.gz -C /opt/qcad/
```
4) create a shortcut:
```
sudo gedit /usr/share/applications/qcad.desktop
```
5) put this in the file:
```

[Desktop Entry] 
Name=QCAD
Comment=A Computer Aided Drafting Tool
Exec=/opt/qcad/qcad_demo
Icon=
Terminal=false
Type=Application
Categories=Application;Utility;

```

You **SHOULD** be done at this point...  But I would greatly appreciate it if someone could test this for me.  Due to circumstances beyond my control, I am actually writing this from Windows right now :cry: (I miss my beautiful Linux).  It seems like it SHOULD work, but I probably missed something.

---

### Post by Abhi Kalyan on 2006-10-19
Am trying to find out the qcad on add or remove

---

### Post by Anonii on 2006-10-19
> **Abhi Kalyan said:**
> Am trying to find out the qcad on add or remove
It should have been easier. And you also dont provide enough info, on your problem.
Try following this:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

It shouldnt be hard at all!

---

### Post by Abhi Kalyan on 2006-10-19
am currently running the command that 
1. Anonii
2. Grey
both had suggested , It got into the universe repostory and is downloading the files.
For the sake of knowledge could you please help me out with
what the various parts of the specific command mean, Only if it is not really a trouble.

We currently are testing two systems
1. ubuntu server
2. ubuntu client -desktop
The GUI for the server is getting downloaded and is being installed.

Am right now editing
sudo gedit /etc/apt/sources.list

---

### Post by Anonii on 2006-10-19
> **Abhi Kalyan said:**
> am currently running the command that 
1. Anonii
2. Grey
both had suggested , It got into the universe repostory and is downloading the files.
For the sake of knowledge could you please help me out with
what the various parts of the specific command mean, Only if it is not really a trouble.

We currently are testing two systems
1. ubuntu server
2. ubuntu client -desktop
The GUI for the server is getting downloaded and is being installed.

Am right now editing
sudo gedit /etc/apt/sources.list
Of course, but can you please specify which commands you want to learn more, about?


Also, about 
**sudo gedit /etc/apt/sources.list**

_sudo_ -> A way to execute the following command with superuser (root) privileges. /etc/apt/sources.list, is a protected file, and can only be edited with root access, so sudo was nessecary.

_gedit_ -> The main GNOME program for text editing. The second most used program for casual editing would be "nano" . Which is a command line editor. Fast, and easy to use. (Try **sudo nano /etc/apt/sources.list** to check it out. It will allow you to edit the sources.list file, with root access, like gedit, did.)

_/etc/apt/sources.list_ -> Its the file which you want to edit. If you want more info about it run "man sources.list" on a terminal.

So, in total: sudo gedit /etc/apt/sources.list , means that you run the proram gedit, with root access, to edit the file /etc/apt/sources.list.

(If you want more info on specific commands, try using the man command. Example: "man cp" for info about the command cp.)

Tell me other commands we used, and I will explain them to you.

---

### Post by Abhi Kalyan on 2006-10-19
Its 1931 hrs now,
Our company is closing for the day.
Thank you
Iarwain ben-adar
Foudre
Ashrael
dolphinsonar
Anonii
Grey
Gn2
Artificial Inteligance
For all the answers, Support you had come forward with,
I will be logging again @ 1100hrs IST, on 20/oct/2006 again
Will ipdate on the changes that had happened.
Thank you all once Again.
It was a great learning experiance in both humility, selflessness and ubuntu

---

### Post by Abhi Kalyan on 2006-10-19
Thank you Anonii, Thats swelll,
The "man" stuff is really very useful its got everything that...
Seriously Good thank you.
Ill go through them and get back in the morning.
Good night.
Thank you A tonne.

---

### Post by Anonii on 2006-10-19
> **Abhi Kalyan said:**
> Thank you Anonii, Thats swelll,
The "man" stuff is really very useful its got everything that...
Seriously Good thank you.
Ill go through them and get back in the morning.
Good night.
Thank you A tonne.
No problem, see you tomorrow.

Helping people (epsecially corporations) getting used to open-source is really important.

And remember stick to this forum, its a great source for information, and question answering.

---

### Post by Grey on 2006-10-19
Come back tomorrow with more questions, and I'm sure they will be answered.  It was good talking with you today.

---

### Post by Abhi Kalyan on 2006-10-20
Good Morning,
AM at office now-
QCAD got installed in the add/remove applet,
Thank you - This is a major step for me at lease.
In this line there is a query which is sort of bothering.
1. QCAD does not come up on the search if "show unsupported applications" is not switched on.
2. Is it okay to install a package (not only QCAD) if it is [proclaimed to be unsupported?)

Note: Thank you for the end notes, It was great and hoping to stay longer.
I will be leaving town today night and by the time i come back from my native place, i should have atleast a small bunch of peopele using ubuntu.
I have been using Windows XP with loads of softwares at home here,
Yesterday i blew the whole 160GB of data ob my home system and installed UBUNTU-
WIll be installing UBUNTU at my native too, so that my parents and kin can start using UBUNTU too.
Thank you.

---

### Post by Abhi Kalyan on 2006-10-20
Hi Anonii,
Sorry about not providing enough infor.
1. I dont knowhow much is enough.
2. Am learning now so with your help the help of people in this forum ishould be able to catch at least a bit

3. The link which you had provided "http://monkeyblog.org/ubuntu/installing/" is great Thank you.
4. I constantly have this nagging feeling that stops me from asking detailed questions.

QCAD installed and running!!!! Great Thank You

---

### Post by Abhi Kalyan on 2006-10-20
Problem-0002: Installation screen freeze up
Scenario
1. Am installing UBUNTU from the alternative CD-ISO burnt on to a CD.
2. I choose "EXPERT" mode on the boot up screen and choose install OEM.
3. i complete most of the stages, 
4. When i reach "select and install softwares" after chooseing
4.a. universe:yes
4.b. Multiverse:yes
4.c. backported:yes
4.d. un supported:yes
5. The installation bar completes almost 60 %
6. The screen becomes black , but i can still hear the cd and fans turning which indicates processing.
7. Then it becomes silent.
at this point i wait for silence and then hit enter key - screen still blank
then there is some life
again silence 
i hit enter - screen still blank
this goes on for a while
and then there is silence
i hit enter
the system restarts
" VIOLAQ UBUNTU is installed and all is fine

My query here here is
1. Why does the screen blank - " The integrity check returned 100% OK"
2. Could this be a hardware problem?
3. What should i do ?

---

### Post by Perfect Storm on 2006-10-20
Does it happen when the computer stand untouch for awhile?

---

### Post by Grey on 2006-10-20
> **Abhi Kalyan said:**
> Good Morning,
AM at office now-
QCAD got installed in the add/remove applet,
Thank you - This is a major step for me at lease.
In this line there is a query which is sort of bothering.
1. QCAD does not come up on the search if "show unsupported applications" is not switched on.
2. Is it okay to install a package (not only QCAD) if it is [proclaimed to be unsupported?)

It just means that it's not supported by Canonical.  Much like Microsoft would not provide support for AutoCAD.  If you are having troubles with AutoCAD, you would go to AutoDesk for support.  If you are having troubles with QCAD, you have to go Ribbonsoft for support.

But support is one thing in the Open Source community that is both cheap and expensive.  You are getting support for your big questions right now, from people on these boards.  And you are getting the help you need for free.  But if you ever wanted someone to call and ask these questions to, you could get a support agreement from Canonical, and they will help you with their product.  But packages such as QCAD would go unsupported by Canonical.

Hopefully I've been clear.  :)

---

### Post by Abhi Kalyan on 2006-10-20
Wow, waiting from morning for some type of reply , thanks you for being here.
And yup have understood very clearly what unsupported means, Thanks.

---

### Post by Abhi Kalyan on 2006-10-20
Hullo good morning,
Yeah, i dont touch any thing.
The install begins and after about 60% it freezes up.
But on timed tapping (i.e.) waiti for the silence then hit enter and at last the linux works off course not perfectly but lest this just happens.

---

### Post by Abhi Kalyan on 2006-10-20
Thanks to this forum 
1. am able to install/uninstall using apt-get, aptitude, GUI
2. use the repostory, download what is not there (etc) - Feels good!!!

New problem-Should i post it as a new thread or can i send it as a quick reply?

**Problem statement** :  *cannot access share on windows system*
windows system : windows 2003 server
domain: zen.local
name of server: x
as displayed in system properties: x.zen.local
serves: file sharing, printer sharing, internet sharing(through RRAS-NAT)
share in windows:\\x\home\

---

### Post by Grey on 2006-10-20
What you are experiencing with the black screen, is likely just DPMS, which is supposed to blank your screen for protection and power savings when it's not in use.  Try hitting a key every once in a while while installing, and see if the problem persists.  It could be that it's not coming out of suspend properly.

> Problem statement : cannot access share on windows system
windows system : windows 2003 server
domain: zen.local
name of server: x
as displayed in system properties: x.zen.local
serves: file sharing, printer sharing, internet sharing(through RRAS-NAT)
share in windows:\\x\home\

This is a little more complicated to explain...  and there are many ways of doing it.  First thing you are going to want to do...

```

sudo apt-get install samba smbfs

```

SMB is the protocol that Windows PCs use for filesharing.  Samba is a reverse-engineered application for Linux that supports it.

After you've installed Samba, for a nice graphical way of connecting, open up Nautilus, and try to connect to smb://x.  Alternatively, you can try Places->Network, and try to connect to a Windows network.  :)

If you would like to have the share mounted in your filesystem, that's a little trickier, but can still be done quite easily.  (It's a little faster and more reliable than using Nautilus anyway).  A good guide for how to do this is [this one](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/).

And sorry for the length of time required before anyone helped you.  It's very late here in North America, and I was sleeping.

---

### Post by MKR. on 2006-10-20
> **Abhi Kalyan said:**
> Hi Anonii,
Sorry about not providing enough infor.
1. I dont knowhow much is enough.
2. Am learning now so with your help the help of people in this forum ishould be able to catch at least a bit

3. The link which you had provided "http://monkeyblog.org/ubuntu/installing/" is great Thank you.
4. I constantly have this nagging feeling that stops me from asking detailed questions.

QCAD installed and running!!!! Great Thank You

Don't worry about providing too much detail. Every piece of information you provide helps everyone understand the problem and better help you.

Another side effect is that it makes it more likely that someone with the same problem will get the thread most useful to them.

---

### Post by Abhi Kalyan on 2006-10-21
Thank You Artificial Intelligence, I just happened to stumble on to a possible solution:
the screen going blank happens @ 61% while in the install applications part of the installation.
while installing i changed the screen resolution to the max that my screen could take (1024*768)
the problem ended, it no longer gets blank,
one interesting thing is that @ 61% install the screen does go blank for a milli second and comes back alive, I just happened to do this and it worked- i dont have any idea why or how!!!

---

### Post by Abhi Kalyan on 2006-10-21
Thank you Grey, I tried this out and then i happened to stumble on the screen resolution solution.

---

### Post by Abhi Kalyan on 2006-10-21
Thank you MKR,
thats swell . If thats the case i think i should start a documentation of the problems i faced and the solutions provided by the forum and post it her.
I will write down all the details as relevant and correct as is possible to me. Thank you Once again

---

### Post by Abhi Kalyan on 2006-10-21
you should be joking Grey, The help am experiancing here is phenominal- I thank tha forum and every one here for giving so much of support- it only drives me to start thinking that one day i should become useful to this community. hope that day comes fast. Thank you for the support.

Am right now 500 Kilometers from the nearest UBUNTU system that i was configuring and testing, will be getting back to this system on 23rd october 2006 IST. Will correspond from there on.
Thank you once again,

---

### Post by JayTee on 2006-10-21
Here's a link that you might find useful. It's for Samba server services in a Windows/Linux Active Directory domain that would prove useful in migrating your users in manageable groups instead of all at once.
[http://sadms.sourceforge.net/](http://sadms.sourceforge.net/)

---

### Post by Cariboo1938 on 2006-10-21
> **Abhi Kalyan said:**
> **Immediate Problem:**
2. How to access windows file shares? Hello Abhi Kalyan, I'm not really an expert in Linux, but 
[HERE]("http://www.ubuntuforums.org/showthread.php?t=217009&page=66&highlight=NTFS") (go to the 1fst page to get the whole story) is a HowTo which probably answers this question. I got it working on a 64-bit Ubuntu Dapper 6.06 installation.
Good Luck
Cariboo

---

### Post by Abhi Kalyan on 2006-10-24
Thank you Jaytee,
thank you for the link, will read it and will keep posting.

---

### Post by Abhi Kalyan on 2006-10-24
Thank you Cariboo1938,
Am right away checking out the link provided by you, thank you once again.

---

### Post by Abhi Kalyan on 2006-10-24
linneighbourhood- I found this as not installed when i searched for "smbfs" in synaptic,
after installing this with the dependencies, i could get connected to the folders on the windows system.
This once again i could do only when connecting using th IP address.
Somehow the connection
smb://x does not work - Could thid be a DNS resoution issue?
smb://192.168.1.3 works perfectly as this is the IP address of system "x"
Thank you Grey - 
Am right now back and am working on the issues.
Trying to mount usinf fstab file-
Will keep posting on the developments
Thank you and the forum once again.

---

### Post by cdfs on 2006-10-24
this will absolutely be a DNS-Problem. You could try trhe folowing:

- Startup a terminal (gnome-terminal ex.)
- sudo nano /etc/resolv.conf
- You now have to edit this file as follows:
search zen.local    (if zen.local is your domain)
nameserver ipaddress       (put in here the IP-address of your DNS-Server)

If you have multiple DNS-Servers in your network, just add another line with nameserver ipaddress for every DNS-Server you want to use.

CDFS

---

### Post by Abhi Kalyan on 2006-10-24
i opened resolv.conf using sudo gedit ( just wanted to test my memory!!)
these are the contents of the file

search zen.local
nameserver 192.168.1.3
domain zen.local

And when i try connecting to
smb://x.zen.local/home
Am getting
" sorry couldnt display all the contents of home"
Home is the place whihc contains the necessary official data
"smb://192.168.1.3/home" connects to the datat perfectly.
Am just thinking-where i have made the mistake,
Is there a way out?

---

### Post by Abhi Kalyan on 2006-10-24
Thank you cdfs,
That was a thing that you taught me, Thank you once again.

---

