---
title: "How to have no username or password"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by shawnanigans on 2008-04-12
Is there a way to have Ubuntu start up when I turn on my computer without putting in a username or password. And I guess as an added question is there a way to just never use users and start as root all the time. I don't want any security, I'm the only person on this computer and I have no information worth securing.

---

### Post by zvacet on 2008-04-12
**System>admin>login window>security tab** and you will find it there.

---

### Post by Inxsible on 2008-04-12
> **shawnanigans said:**
> Is there a way to have Ubuntu start up when I turn on my computer without putting in a username or password. And I guess as an added question is there a way to just never use users and start as root all the time. I don't want any security, I'm the only person on this computer and I have no information worth securing.
You can use auto login feature so you dont have to enter your username and password. Its under System>>Administration>>Login Window

but you cannot NOT have users. Linux does not allow root privs to everyone unless you provide a root password.

---

### Post by captain_conrad on 2008-04-12
me too me too
but i want a user name and password, but mine has been set to:
username: conrad
password: conrad
pretty dof i know, but somebody else set up my pc with ubuntu
How do I change my username and password????

---

### Post by R6V2 on 2008-04-12
For everyone question, concerning the system, look under:

System>

It will be there.

:)

---

### Post by Inxsible on 2008-04-12
> **captain_conrad said:**
> me too me too
but i want a user name and password, but mine has been set to:
username: conrad
password: conrad
pretty dof i know, but somebody else set up my pc with ubuntu
How do I change my username and password????System >> Preferences>>About me

You can't miss the 'Change Password' button there :)

---

### Post by sam hassell on 2008-04-12
Hi,

For automatic login, click System -> Administration -> Login Window

Then choose the Security tab.

Then check Automatic login and select your user from the dropdown menu.

Automatic login is a security issue, but  not as much as running in root - PLEASE do not do that - it opens the possibility of people taking complete control of your machine via the internet, regardless of who has physical access to your machine.

All the best,

Sam.

---

### Post by shawnanigans on 2008-04-12
> **Inxsible said:**
> You can use auto login feature so you dont have to enter your username and password. Its under System>>Administration>>Login Window

but you cannot NOT have users. Linux does not allow root privs to everyone unless you provide a root password.

I set up the computer, how would I get the root password? During the install of Ubuntu is there a way to not make any users? Just user root, password root maybe?

---

### Post by sam hassell on 2008-04-12
at the terminal, type 

> 
sudo passwd


and enter your password twice. You should now be able to login as root.

---

### Post by Inxsible on 2008-04-12
> **shawnanigans said:**
> I set up the computer, how would I get the root password? During the install of Ubuntu is there a way to not make any users? Just user root, password root maybe?
The first user name that you create is just that -- a user.

The root only means obtaining admin privs. That's of course a very basic explanation

---

### Post by shawnanigans on 2008-04-12
> **sam hassell said:**
> Hi,

For automatic login, click System -> Administration -> Login Window

Then choose the Security tab.

Then check Automatic login and select your user from the dropdown menu.

Automatic login is a security issue, but  not as much as running in root - PLEASE do not do that - it opens the possibility of people taking complete control of your machine via the internet, regardless of who has physical access to your machine.

All the best,

Sam.

It's pretty unlikely that will ever happen so I'm not worried. I usually run Windows without a virus scanner or firewall and have only once got a virus and that was from a torrent that had warnings about a virus that I ignored.

---

### Post by Inxsible on 2008-04-12
> **shawnanigans said:**
> It's pretty unlikely that will ever happen so I'm not worried. I usually run Windows without a virus scanner or firewall and have only once got a virus and that was from a torrent that had warnings about a virus that I ignored.


Not all viruses and attacks are displayed to the user. There are many that run in the background without the user's knowledge.

You seem pretty confident(?) about security issues

---

### Post by shawnanigans on 2008-04-12
> **Inxsible said:**
> Not all viruses and attacks are displayed to the user. There are many that run in the background without the user's knowledge.

You seem pretty confident(?) about security issues

Confident may not be the best word, but definitely apathetic to them.

---

### Post by captain_conrad on 2008-04-12
ok here what i did
system
preferences
about me

and then it comes with this damn message:

There was an error while trying to get the adressbook information
Evolution Data Server can't handle the protocol



what do i do now? help

---

### Post by mikewhatever on 2008-04-12
Here's a good place to start with and about root passwords [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201).

---

### Post by phillipchandler on 2008-04-12
Im a bit concerned at the fact that as a Windows users, he only ever had one virus ? A friend of mine is paranoid about viruses and has only ever had one from a Computer Magazine DVD, but he has all the jave and flash turned off by default, and never does anything that could have a virus hidden. Ive used Windows since the days of Win 3.x, I consider myself more experienced than a lot of people, but not as clever as a whole lot more. But even Ive had shed loads of viruses.
Im running a clarkconnect firewall now, and the reports I get from it, IE the port scans, someone scanning a whole range of the ISP's IP addresses to see what they find, ping requests is unbelieveable.
The whole idea of Linux, root passwords and the directory structure is so that security is basically as close to zero as you can get it. Having root privelages permanently could (and I say COULD) open you wide to script kiddies, war drivers, old school hackers etc. Wardrivers if you have wireless internet.

The risks of hacks especially if your behind a software firewall, rather than a hardware/software combo is quite a high risk, and as someone said before, you dont get the hackers telling you that you've been hacked and that they have your identity and are currently getting a Capital One credit card with a £5000 limit, and are going to splah out. I never trust a software firewall like ZoneAlarm, I wouldnt even trust the "KMyfirewall". In fact i wouldnt even connect to my modem direct, and antiviruses will  tell you different things. So please reconsider having auto login etc as it really is asking for more trouble than you need.

But hey, who are we to preach. If the guy wants his PC compromised, then thats his freedom of choice. I just hope he doesnt get hacked, and then comes back to ask how he can protect himself.

---

### Post by mikewhatever on 2008-04-12
> **phillipchandler said:**
> 
But hey, who are we to preach. If the guy wants his PC compromised, then thats his freedom of choice. I just hope he doesnt get hacked, and then comes back to ask how he can protect himself.

We can't stop him from logging as root, however, we don't have to help him, especially since such discussions are restricted by the forum rules.

---

### Post by cometa2k7 on 2008-04-12
It is not at all advisable to log in as root. It is possible, but I definitely sugget that you don't run root at all.

You can run "sudo" in a terminal if you need to do something as root. Running root all of the time is a security risk, and a major risk to your filesystem.

You can change the root password if you need to know it, and have the ability to use the root account for lengthy things that require root privileges, but not as your default.

Some programs even recommend that you run as a standard user, and not root.

[SIZE="4"]**DON'T RUN AS ROOT, IT IS UNNECESSARY**[/SIZE]

As for autologin, could be a security risk. But that said I use it, it much easier, well I have a 10 second delay set as I have two accounts. Auto-login makes life a bit easier, and my computer doesn't need to be 100% secure, and you could pull of every files without booting the operating system anyway. Auto-login to a normal account, fine. Auto-login to root, not good.

However, it is your choice if you want to do something on your PC that might cause damage to your system; it's you that gets the problems.

---

### Post by russo.mic on 2008-04-13
I think everyone here should try and understand that the reasons for having a password and username are more than just for security from outside sources, but also from yourself, no offense meant to anybody.

Russo

---

