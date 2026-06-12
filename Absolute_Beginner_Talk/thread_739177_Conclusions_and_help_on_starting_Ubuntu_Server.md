---
title: "Conclusions and help on starting Ubuntu Server"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by rgotten on 2008-03-29
:)All of you have being excellent on your comments and help, and after few weeks of thinking about this project I would like to summarize my ideas and get a consensus from all of your ideas so I can start it, let me say that I may ask some questions that might be out of this forum spectrum, but your help an orientation is very highly appreciated. As I mention at the beginning, I am a doctor and so far I have paper chart for my patients, and I am planning to do this project in about a year time and if it works after multiple testing, and being safe proof then I might move all my charts to this approved and safe project. I am going to express my project and at the same time ask question and would appreciate answer to them so I can make a start of this. 

My office has 3 computer + my laptop that run on windows xp professional, there are network thru a router (3 wired and my laptop wireless). My plan is as follow: I use word for windows with different templates to create the history and follow up evaluation of my patient. I use zoombrowser from cannon to save the images in a organize way (jpeg format). As you can see this is very primitive and this information is basically saved on my laptop and regularly safe into an external hard drive with Ghost. I would like to create a simple database where my front desk girl will place the name of the patient and chart number; this will have subfolder called for example: Medical record (where I will dictate on the word document template), Billing (where my secretary will scan and safe on pdf format payment from the insurance company, patient, etc), Photos (where I will safe the jpeg files), and other subfolder. (Help also on creating this database will be appreciated).

i.e John Smith 1111 ….Medical Record
Billing
Photos
Laboratories
Etc..

It is my believe after reviewing this forum and all your greatly appreciated comments that this is the step to follow:

a) Build a computer: probably a duo core or sempro with 2 gb of ram, 500 wt of power, on raid 1 with 2 (500 gb) drives build on a chip case

b) From this forum I heard about using xubuntu, kubuntu, etc, or even ubuntu desktop, and then add server software of my choice (Apache, MySQL, Samba server, etc) but also some of you feel very confident that I should use ubuntu server edition with LAMP. So I guess I have to install this (unless somebody has any other idea), and play with it, (I hope you guys will be there to help me on this.

c) In my impression this server will be use for the following purpose (please correct me if I am wrong): all this files world, jpeg, pdf, etc) from any of my 4 windows xp computer will be save and also be access from these server. At the same time, being a raid 1 computer if one of the 500 gb hard drive fails, the other will start working as a mirror, also will have an external hard drive connected to one of the window xp computers from where a copy can be done from the server in a incremental way to have all the data of the server on a windows format external hard rive as a backup, and also be able to do a remote connection to the server on a weekly basis from my home windows computer and also do a remote backup in a incremental way. After I play with this and can safe some of the files from all this computer into the server, then I can safe bigger folders and see how this works to be access from the computers and also remotely access, and if after playing and this works, then work on creating the database…

d) If anybody will guide me on how to build this database to be use on windows environment computer and safe the information on the ubuntu server and also be able to access this remotely from any computer I guess as a web page..Your help on this may be very highly appreciated.

One more time, I know I am asking many things and some of them may be out of the scope from Ubuntu forum, but on the same token, you guide has being excellent, as well as your help and instruction and your orientation will be appreciated, I will follow steps and instructions of the most expert people…and in advance…..Thanks

rgotten
:)

---

### Post by Barrucadu on 2008-03-29
If you install Ubuntu Server it will give you a list of server software you can install during the install process (of course, this is only a small subset of the possible server software, but it will suffice).
However, Ubuntu Server is all CLI based, no GUI by default, so if you are not particularly comfortable with that, you could look at either running Xubuntu (as a server wants to be as fast as possible) or installing a desktop environment on top of Ubuntu Server. I managed quite happilly running Fluxbox and iDesk on top of Ubuntu Server, to give me a nice and fast server computer, though I rarely used the GUI.

---

### Post by rgotten on 2008-03-30
So for a beguinir like me what wil you advise...which is the most stable, buy the way what is the diference between ubuntu, kubuntu and xubuntu??

---

### Post by superprash2003 on 2008-03-30
if you are a beginner and you really want to start a server, then install ubuntu server and then install the gui for it

---

### Post by rgotten on 2008-03-30
Which gui you recomend

---

### Post by rgotten on 2008-04-14
--------------------------------------------------------------------------------

I have installed the server edition and have the option to install the extras: DNS server, LAMP, Mail Server, open SSH, postgreg SQL, print server, Samba files.
As i mention, I am new to this, Should i install all of them based of what i have said in the past and for the purpose i am building the server?

---

### Post by hyper_ch on 2008-04-14
A gui won't do any good for operating the server... a server is configured by editing text files and for this there is no difference if you use a simple text editor from the command line or whether you run a fancy gui.

I think a web-browser based product would probably the best. I haven been evaluation similar stuff myself but am not too happy with what's out there... sugarcrm, vtiger could to the job - but I think it's just much more than I need...

So I'll probably write my own little application for that.

---

### Post by rgotten on 2008-04-16
> **Barrucadu said:**
> If you install Ubuntu Server it will give you a list of server software you can install during the install process (of course, this is only a small subset of the possible server software, but it will suffice).
However, Ubuntu Server is all CLI based, no GUI by default, so if you are not particularly comfortable with that, you could look at either running Xubuntu (as a server wants to be as fast as possible) or installing a desktop environment on top of Ubuntu Server. I managed quite happilly running Fluxbox and iDesk on top of Ubuntu Server, to give me a nice and fast server computer, though I rarely used the GUI.

Well i install everything on the server option setup, since i heard that is ligth. One thing i left with no configuration during the installation was the " mail configuration" and I am having problems with the sudo command since it is asking for a password that i never setup. Reading and googling i found that this is because i did not perform the " mail configuration", and do not know how to configure it now.

Base on the above i have the following questions:

1) how to do the mail configuration or
2) reinstall completelly ubuntu server and just install some options (please advise on this, or is good to have everything install or if i need to install some componets after,  how you do this?) or
3) keep on playing for another 8 days and install server version 8.04 (by the way, will ubuntu upgrade authomatically??when new version come out??)

Thanks

---

### Post by sryth on 2008-04-16
Webmin works for me.  Best bet in my opinion would be try to install webmin, if it works, great, if it doesn't, try a fresh install, then install webmin immediately, it should auto-detect everything and configure itself, then you have a nice GUI through your web browser to configure everything from your mail server, web server, databases, firewalls...everything.   The only reason I recommend a fresh install if it doesn't work right the first time is that webmin generally looks for the default options to detect, so it may have problems if you've changed the wrong things prior to installing it.

---

### Post by rgotten on 2008-04-17
Thanks for your help, I am repeating part o my question form before but have not recive an answer that clarify my question.

I finally decided to istall ubuntu server, and on installation i had the option to install the extras, and i install all of them, thinking there were part of the package, which includes:  DNS server, LAMP, Mail Server, open SSH, postgreg SQL, print server, Samba files.
As i mention, I am new to this, Should i install all of them based of what i have said in the past in this forum and for the purpose i am building the server? or should i reinstall and select only some options like LAMP, etc. 

Also when i did the installation one thing i left with no configuration during the installation was the " mail configuration" (i though i could do it later) and I am having problems with the sudo command since it is asking for a password that i never setup. Reading and googling i found that this is because i did not perform the " mail configuration", and do not know how to configure it now.

Base on the above i have the following questions:
1) What shold i have install to beguin with in the ubuntu server, based on the above, 
2) how to do the mail configuration or so wound not have the problem with the sudo command password or
3) reinstall completelly ubuntu server and just install some options (please advise on this, or is good to have everything install or if i would like to install some componets after, how you do this?) or
4) keep on playing for another 7 days and install server version 8.04 , or if i keept it the way it is , will ubuntu upgrade authomatically, when new version come out??)
5)If i do webmin, do i have to install any of the option of ubuntu serv er other than Samba...please advice

Thanks

---

### Post by rgotten on 2008-05-09
--------------------------------------------------------------------------------

I have finish testing my software raid configuration and is working perfect. I did Radi 1 100 mb for boot, Raid 1 2 gb for swap, Raid 5 10 gb for the / (system), and Raid 5 (aprox: 980 Gb) for /home. (please let me know if this appears ok for you guys), then I have zero one of the hard drive (for testing) and it boot well in degrade mode, after i have rebuild the Raid without any problem. So now I am ready to continue with the server and this is what i need or questions i have:

I finally installed ubuntu server 8.04, from my understanding of what i needed after reading the threat i had to install the "LAMP" option and the "Samba" option. Which i had selected during my instalation of the server 8.04. NOW:

1) I need a easy way of configuring this ( i assume it was install simce i selecte it during the cd installation, can somebody give me some guidence on this.

2) If i would like to access this remotly from home or another computer, how can i do this (i have a router)??

3)How do i secure my server so nobody can access it from the outside

4) How do i do backups of the server??

Help will be apreciated

rgotten

---

### Post by rgotten on 2008-05-09
I have finish testing my software raid configuration and is working perfect. I did Radi 1 100 mb for boot, Raid 1 2 gb for swap, Raid 5 10 gb for the / (system), and Raid 5 (aprox: 980 Gb) for /home. (please let me know if this appears ok for you guys), then I have zero one of the hard drive (for testing) and it boot well in degrade mode, after i have rebuild the Raid without any problem. So now I am ready to continue with the server and this is what i need or questions i have:

I finally installed ubuntu server 8.04, from my understanding of what i needed after reading the threat i had to install the "LAMP" option and the "Samba" option. Which i had selected during my instalation of the server 8.04. NOW:

1) I need a easy way of configuring this ( i assume it was install simce i selecte it during the cd installation, can somebody give me some guidence on this.

2) If i would like to access this remotly from home or another computer, how can i do this (i have a router)??

3)How do i secure my server so nobody can access it from the outside

4) How do i do backups of the server??

Help will be apreciated

rgotten

---

### Post by hyper_ch on 2008-05-10
> **rgotten said:**
> 2) If i would like to access this remotly from home or another computer, how can i do this (i have a router)??
That depends on how you want to access it... easiest way:
```

sudo apt-get install openssh-server

```
And then forward port 22 from the router to the server... and then on windows use WinSCP or Putty and or linux use the fish://user@homeip protocoll in Konqueror (dunno about others) or ssh user@homeip from the cli to connect to it...

> **rgotten said:**
> 3)How do i secure my server so nobody can access it from the outside
That contradicts question 2

> **rgotten said:**
> 4) How do i do backups of the server??
different ways... I use my own little backup script with rsync, cron, hardlinks to create an incremental snapshot-style backup every 6h dating back for 90 days.

---

### Post by rgotten on 2008-05-10
Question 2) Can you access the server from outside my office with openssh. I though that was use to access the server from inside the office network. What about ebox???

Question 3) I want a secure server but able to look or access the server from outside the office thru the net, better as a web interface, BUT SECURE..That is what i was meaning. Can i do that??.

Question 4) If i do not have a backup script, what can i use??I would like to do backups of the server inside the office, but also remotly

Thanks

Rgotten

---

