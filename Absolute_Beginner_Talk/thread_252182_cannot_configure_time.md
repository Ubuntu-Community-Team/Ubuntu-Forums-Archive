---
title: "cannot configure time"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by ashoka2004 on 2006-09-06
hi guys whenever i try to configure time it does not allow me to 
when i click on the administrator mode it says su returned with an error
plz.. tell me how to configure time manually

if i try to change anything it says su returned with an error


thanks 

how to configure the network for internet cause whenever i try to click on administrator mode it says su returned with an error

---

### Post by Blairboy on 2006-09-06
Are you using the correct password?

---

### Post by zxee on 2006-09-06
Is the account you are using the primary and first user account you created during install and are you using your user password?

What happens if you open a terminal shell and type > sudo ifconfig?

---

### Post by LeslieL on 2006-09-06
Are you trying to do it in the console using _su_? In Ubuntu you have to use _sudo_.

---

### Post by ashoka2004 on 2006-09-06
hi thanks guys for the reply

the a/c that i am using is the first user a/c that i created.

if i type
 sudo ifconfig (it gives me the following)
sudo: unable to lookup kaps via hostbyname()

su ifconfig
unknown id ifconfig

su root ifconfig
password: i type the password

kapil@kaps:~$

it comes to the next line

i am using the kdm if i click on administrtor mode 
it says su returns with an error

---

### Post by zxee on 2006-09-06
in ubuntu by default su is disabled use sudo and when using sudo you need to use the user password for that account. It sounds like you believe you have a root password though-did you set up a root account??

---

### Post by ashoka2004 on 2006-09-06
i went into the recovery mode and there i did set the root password 

but the issue is whenever i try to configure anything example time or network and i click on administrator mode it says su returned with an error ]

help plz.....

---

### Post by zxee on 2006-09-06
> **ashoka2004 said:**
> i went into the recovery mode and there i did set the root password 

but the issue is whenever i try to configure anything example time or network and i click on administrator mode it says su returned with an error ]

help plz.....

hmmmm  What happens if you type su in a shell/terminal and then enter the root password you chose when setting up the root account? Just to be clear you type su <enter> the shell responses with #password and you type the correct password. So, I'm thinking, if you can become root like you would in many other linux distos you could, possibly, then type administrative commands. I think this is a little dicey in ubuntu though.

---

### Post by ashoka2004 on 2006-09-07
i think so ppl are just better off with windows

and there is no sense in going into the technicalities on ubuntu or linux 

i m sorry for the ubuntu fans
inspite of so much free software it is useless for me 

may be i m not that techiee its been three days and not even one guy has been able to help 

feeling reallllllllyyyyyyyyy badd this sucks guysss

on second thoughts still waiting for someone who could help me 


i do not know a single command in ubuntu and i m interested in the gui but whenever i try to configure time or configure the network i get a message su returned with an error i m not into shell or anywhere 
i can access the root but whatever command i type it does not do anything except going to the next line which is blank


HELPPPPPPPPPP!!!!!!!!!!!!!!!!!!!!!!

---

### Post by bodhi.zazen on 2006-09-07
A few options:
[list]
[*]1. In the gui, enter the admin. mode, try you user passowrd rather then root PW.
[*]2. To run a "gui" as root, use gksudo, example "gksudo nautilus" to open a nautilus session as as root. 
[*]3. In a terminal su into root, type command as root.
[*]4. Error messages?[/list]

---

### Post by monktbd on 2006-09-07
you should start reading some documentation i think.

before changing some deeper things of ubuntu like enabling a root account or similar you should try to stick with what comes out of the box and start from there.

with windows you had probably years to learn it. with linux you try to do exactly the same within minutes or hours. that cannot work.

try to use ubuntu at first with sudo unless you already have enough linux experience to know what you are doing with enabling the root account.

to me it seems that sudo is broken and su is broken as well.

post the whole terminal output of
> 
apt-get install

> sudo apt-get install

and


> su
apt-get install

---

### Post by ashoka2004 on 2006-09-08
apt -get install

E: could not open lock file /var/lib/apt/lists/lock -open (13 permission denied)
e: unable to lock the list directory denied )


sudo apt-get install

sudo : unable to lookup kaps via get hostbyname()

su 
apt - get install 

reading package lists..... done
building dependencies tree.... done
0 upgraded 0 newly installed, 0 to removed and 0 not upgraded.


thats the result dude 



 I GO TO THE KDM  CLICK ON ADMINISTRATOR MODE FOR CONFIGURING TIME IT GIVES ME AGAIN THE SAME ERROR SU RETURED WITH AN ERROR

I M USING AN ETHERNET CONNECTION FOR INTERNET I CANNOT CONFIGURE THE INTERNET I HAVE TO COME TO WINDOWS AGAIN AND AGAIN PLS. TELL ME HOW CAN I CONFIGURE THE INTERNET BY WRITING THE RITE COMMANDS
THANKS A TON

---

### Post by ashoka2004 on 2006-09-08
help plz..

---

### Post by bodhi.zazen on 2006-09-08
First it looks like sudo is broken. See below to fix.

Second is looks like you network is functioning properly, as root (su) apt-get ran fine.

Try (as root, ie su):
```
apt-get install aptitude
```

aptitude replace apt-get and has a number of advantages. Now to install:
[aptitude install <program_name>[/code]

As root (su) you should be able to ifconfig (**Linux uses ifconfig** Windows uses ipconfig).

to fix sudo see:
[psychocats can't sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by ashoka2004 on 2006-09-08
hi there is no problem with the sudo as i checked both the files they are fine in the configuration its correct

if i type adgroup kapil (myusername) admin 
it gives me a reply that the user is already added 

so sudo file seems to be okay 

tell me something else 


whenever i try to click on administator mode in the gui mode i get an error su returned with an error unable to configure anything

---

### Post by bodhi.zazen on 2006-09-08
> **ashoka2004 said:**
> hi there is no problem with the sudo as i checked both the files they are fine in the configuration its correct

if i type adgroup kapil (myusername) admin 
it gives me a reply that the user is already added 

so sudo file seems to be okay 

tell me something else 


whenever i try to click on administator mode in the gui mode i get an error su returned with an error unable to configure anything

Good work. Did you learn anything?

I use the command line because GUI's do not always work. As you become more familiar with Linux you will likely do the same.

The best advice I can give you is to learn how to administrate your box via the command line. Learn to use man pages. Learn to google and how to ask questions. Yes it will take time, but no more then learning Windows.

Advice of less quality is:

I do not yet understand where the problem is with your GUI. Error message please?

The GUI tool wants you to use your user password (not root's PW). If that is not working you system is misconfigured (congratulations, you broke something with root powers, don't worry we all do it. This is how we learn to **[color=red]respect root[/color]**).

Perhaps someone more knowledgeable will read your post and respond.

The likely hood you are to get a response depends somewhat on the attitude you convey in your posts and the quality of the information you provide. 

Keep in mind we are mostly volunteers here. 
Avoid
> The squeaky wheel gets ignored
syndrome.

As such, few people want so scroll back 2 or 5 or 10 posts to understand you question. Consider each post/question as a stand alone question.

---

### Post by ashoka2004 on 2006-09-09
hi thanks for your reply dude

you know i almost figured out what the problem is 

actually there is a file /etc/hosts  in this file there is an entry

127.0.0.1 localhost.localdomain localhost 

here i had to add kaps to this line which is my hostname 

so i went into the recovery mode and used nano text editor

nano /etc/hosts

to

127.0.0.1 localhost.localdomain localhost kaps

now the error that i was getting is not comming anymore 

su returned with an error  it not comming anymore its now asking me for my password of the username that i m using which is not the root password once i enter the password it does not do anything

just takes me back to the same page where i cannot change anything but atleast i resolved the issue of su returned with an error at least 

the following is the link i got help from 

[http://www.ubuntuforums.org/showthread.php?t=99780&highlight=su+returns+error](http://www.ubuntuforums.org/showthread.php?t=99780&highlight=su+returns+error)

can you please tell me how to configure teh time of the system through cli  i.e. what command should i use to configure time through cli(command line) well i did not know the full form till yesterday.

thanks for your support guys

---

### Post by bodhi.zazen on 2006-09-09
If I am understanding you correctly, you want to set the time?

I do this with ntp (network time protcol)

You may need to install ntp, assuming you do:
```
sudo aptitude install ntp openntpd
sudo ntp ntp.nasa.gov
```

To set timezone:
```
tzconfig
```
This allows you to set your timezone.

Is this what you are asking?

---

### Post by bodhi.zazen on 2006-09-09
127.0.0.1 localhost.localdomain localhost kaps

should read

127.0.0.1 localhost.localdomain kaps

---

### Post by bodhi.zazen on 2006-09-10
See this post regarding admin access:

[thread=254707]administration access[/thread]

---

### Post by ashoka2004 on 2006-09-12
hi bodhi thanks a ton buddy its all because of you that i was able to resolve the issue of not being able to configure the time you were rite abt the settings that i had to change in my 
/etc/hosts file


127.0.0.1 localhost.localdomain kaps

as soon as i changed the line to this it started to work i was successfully able to modify the time and now i m not getting any error 


SO FOR THE NEWBIES IF THEY GET AN ERROR LIKE (SU RETURNED WITH AN ERROR ) IF THEY ARE CLICKING ON ADMINISTRATOR MODE THEN ALL THEY NEED TO DO IS  check the file 

/etc/hosts

it should look like 

127.0.0.1 localhost.localdomain ubuntu (ubuntu or whatever was the host name they gave at the time of install kubuntu)

which they can check by typing hostname on command line 
whatever is the result should be a part of the file /etc/hosts

if hostname is empty they have to first set a hostname by typing

nano hostname 

nano is the text editor in ubuntu

their they can specify the hostname press ctrl x for saving the document then press y for saying yes to saving the document
then change the file 

nano /etc/hosts it should look like

127.0.0.1 localhost.localdomain ubuntu

thanks bodhi thanks a ton dude

you are simply great

---

### Post by bodhi.zazen on 2006-09-12
FYI: You need the same host name in 2 places:

[list=number][*]/etc/hostname
[*]/etc/hosts[/list]

/etc/hostname```
<hostname>
```

/etc/hosts```
127.0.0.1 localhost.localdomain <hostname>
```

8-)

---

### Post by ashoka2004 on 2006-09-13
thanks take care

---

