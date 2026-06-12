---
title: "Sudo and su - passwords"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by BWF89 on 2006-11-05
Whenever I'm trying to do something and the people here tell me to use sudo for my commands I start to run into problems.

When I'm useing sudo (or gksudo) it asks me for my password. So I put in the admin password and everytime it says I'm wrong. I even tried putting in my regular user password for good measure. But when I use su - and put in my password it lets me be root.

Why is this?

---

### Post by justifier on 2006-11-05
are you sure you are typing the password correctly, the password doesnt show up in terminal but it is still putting it in!!

you need to use either sudo or su to give you root provilidges

---

### Post by BWF89 on 2006-11-05
> **justifier said:**
> are you sure you are typing the password correctly, the password doesnt show up in terminal but it is still putting it in!!
I'm 100% sure I'm putting it in correctly. Because it works everytime when I use it with su -.

---

### Post by CatKiller on 2006-11-05
**su** requires the root password, if you've set one. Actually, it requires the root password regardless, but you won't know what it is.

**sudo** requires **your** password, the one that you use to log in.

---

### Post by compmodder26 on 2006-11-05
Do you have the root account enabled?  If so, su will use the root password.   Sudo uses your users password (assuming you have your user set up as a sudoer, that is the default for Ubuntu).

---

### Post by BWF89 on 2006-11-05
Ok, I get it now.

---

### Post by steve.horsley on 2006-11-05
You have an unusual configuration if you can use su. The default install sets an impossible password on the root account so that you have to use sudo (which asks for your password, not the root password). Also note that the installer only puts the **first** user in the **admn** group - the group that is allowed to use sudo.

---

### Post by BWF89 on 2006-11-05
I'm still having problems with Sudo.

I was in another thread where someone was getting help with their screen resolution.

Someone posted to do:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

When I put that in it asks me for my password, i give them **my** password, than it goes right back to *bwf89@BWF89-desktop:~$* like nothing even happened.

---

### Post by TigerCR1200 on 2006-11-05
Do an ls on the directory you will see the copy. Just going back to the command prompt means the command worked.

---

### Post by autocrosser on 2006-11-05
That meens that it worked just fine--"cp" means "copy file" & if you look in the directory /etc/X11, you will fine the "copied" file there.  

To empower yourself, take a look at:  [http://www.justlinux.com/nhf/Command_Reference](http://www.justlinux.com/nhf/Command_Reference)

This gives you a basic knowledge for the terminal commands & what they do..


By the way--congrats on the move away from OSX--I was one of the beta-testers for OSX & I am 100% Linux now--didn't like the way Steve was going....;)

---

### Post by Dual Cortex on 2006-11-05
What were you expecting it to ask you?
That's it, the file has been backed up, it doesn't need to show any output.

---

### Post by BWF89 on 2006-11-05
> **Dual Cortex said:**
> What were you expecting it to ask you?
That's it, the file has been backed up, it doesn't need to show any output.
Yes :oops:
> **autocrosser said:**
> By the way--congrats on the move away from OSX--I was one of the beta-testers for OSX & I am 100% Linux now--didn't like the way Steve was going....;)
My parents (on my advice) moved away from Windows **to** OSX. They use OSX (and me also until I get Ubuntu setup) and I got the 5ish year old PC with Windows and installed Ubuntu. I personally love OSX. As soon as we took it out of the box it automatically configured our internet access. I think if Linux was as easy to use as OSX it would be dominating the computer market.

---

### Post by autocrosser on 2006-11-05
I'm glad that you got your family away from Windoze--OSX is Much better than XP--i just don't like the path that Apple is going right now & you would need to know I've used Apple for 15+ years--so I see the move to Intel processors as a bad thing--If I wanted to use a Intel processor--I'd build my own system (wait--I just did;))

My point is that Linux is the way of the future & it will get better as time goes along--

---

### Post by BWF89 on 2006-11-05
I went to use the GDebi package installer to install Easy Ubuntu, when I put in my user password it says something about sudo not being able to do that and that I should consult my administrator.

---

### Post by autocrosser on 2006-11-05
Sounds like your account has some permission problems--take a look at Menu>System>Administration>Users and Groups--tic your user (highlight it) & tic Properties--Look at the tabs Advanced to see if you are in the admin group & then the User Privileges to see if all boxes are checked---if not, correct as needful.

I would recomend you to:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

for more info;)

---

### Post by manishk on 2006-11-05
> **steve.horsley said:**
> You have an unusual configuration if you can use su. The default install sets an impossible password on the root account so that you have to use sudo (which asks for your password, not the root password). Also note that the installer only puts the **first** user in the **admn** group - the group that is allowed to use sudo.


How do I put someone else into the admn group? And how do I enable the root account? (I'm not going to, just wanted to know):-k

---

### Post by autocrosser on 2006-11-06
See my post above & make sure to goto the webpage I referenced--has lots of good info;)

---

### Post by tommcd on 2006-11-06
If you really can't use sudo have a look at this:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by BWF89 on 2006-11-06
> **autocrosser said:**
> Sounds like your account has some permission problems--take a look at Menu>System>Administration>Users and Groups--tic your user (highlight it) & tic Properties--Look at the tabs Advanced to see if you are in the admin group & then the User Privileges to see if all boxes are checked---if not, correct as needful.
I went there and got:
*The configuration could not be loaded. You are not allowed to access the system configuration.*
> **tommcd said:**
> If you really can't use sudo have a look at this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
I tried that and it wouldn't even let me access the files.
[I]bwf89@BWF89-desktop:~$ /etc/sudoers
bash: /etc/sudoers: Permission denied
bwf89@BWF89-desktop:~$ /etc/group
bash: /etc/group: Permission denied[/I]

---

### Post by autocrosser on 2006-11-06
Ok--if you look at: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

You'll see a way to boot in via the recovery mode--make sure you print the page, then reboot--select recovery mode & you will  end up logging in as the root user--nano is a bit foreign to new users (i've used it on & off over the years--y=yes n=no & control-<key> are the main functions. In recovery mode EVERYTHING is text-based--no graphical panels at all....

In any case--follow the instructions & then reboot as normal--post back with your results!!

---

### Post by BWF89 on 2006-11-07
> **autocrosser said:**
> In any case--follow the instructions & then reboot as normal--post back with your results!!
Sorry to not respond for an entire day but I was having printer problems on my upstairs computer (iMac) it was refusing to print.

Anyway, when I first got into Nano I put the command *addgroup bwf89 admin* to the file and saved it, and hit the power switch (since I don't know how to shut down/restart the computer from command line). But than when I went to do something I got this when I did *gksudo synaptic* after I rebooted:
```
bwf89@BWF89-desktop:~$ gksudo synaptic
>>> sudoers file: syntax error, line 0 <<<
sudo: parse error in /etc/sudoers near line 0
```

So I went back into the file and deleted *addgroup bwf89 admin* I put in the top and made it the way it was before. I then added that command in the proper way. It said my name got added as an admin and it was done. I couldn't go a ctrl+x to save so I just did a hard shut down. I went back and put the same command into terminal to run synaptic and got the same error I posted above.

But it must have worked because my name now had root priviledges because it now allows me to go to menu > system > administraitor > users and groups. And it showed me as having all the privledges. So why is that line of code on line 0 messed up if I went back and deleted it?

---

### Post by CatKiller on 2006-11-07
> **BWF89 said:**
> So why is that line of code on line 0 messed up if I went back and deleted it?

Didn't you say that you **didn't** save it after you changed your /etc/sudoers file? I think that's what you said. It's not that clear. In which case, you effectively **haven't** gone back and deleted it. The first character of /etc/sudoers should be a #, anyway.

To shutdown from the command line: ```
sudo shutdown -h now
``` To restart from the command line: ```
sudo shutdown -r now
``` You won't need the *sudo* from the recovery console - that's rather the point of the recovery console, after all.

I think you'll find that it was because you got round to adding yourself to the admin group that your menus are working again.

---

### Post by BWF89 on 2006-11-07
> **CatKiller said:**
> Didn't you say that you **didn't** save it after you changed your /etc/sudoers file? I think that's what you said. It's not that clear. In which case, you effectively **haven't** gone back and deleted it. The first character of /etc/sudoers should be a #, anyway.
What I ment was. I added *addgroup bwf89 admin* to the top of the file where "#" is supposted to be. And I saved it. Than I went back, deleted that so that # would be the beginning of the file. Then I actually entered the command so that it would work.

---

### Post by CatKiller on 2006-11-07
> **BWF89 said:**
> What I ment was. I added *addgroup bwf89 admin* to the top of the file where "#" is supposted to be. And I saved it. Than I went back, deleted that so that # would be the beginning of the file. Then I actually entered the command so that it would work.

I don't know why you're getting that error message about line 0 then. Sorry.

---

### Post by BWF89 on 2006-11-08
> **CatKiller said:**
> I don't know why you're getting that error message about line 0 then. Sorry.
I backed up the 2 files (group and sudoers) like the Psychocats tutorial told me to. What command would I enter to replace current ones with backed up ones?

---

### Post by CatKiller on 2006-11-08
> **BWF89 said:**
> I backed up the 2 files (group and sudoers) like the Psychocats tutorial told me to. What command would I enter to replace current ones with backed up ones?

From the recovery console:

```
cp /etc/group.old /etc/group
cp /etc/sudoers.old /etc/sudoers
```

---

### Post by BWF89 on 2006-11-08
I tried those commands it didn't do anything. Went into terminal as soon as I entered them and neither *gksudo synaptic* or *sudo synaptic* would work.

---

### Post by CatKiller on 2006-11-08
> **BWF89 said:**
> I tried those commands it didn't do anything. Went into terminal as soon as I entered them and neither *gksudo synaptic* or *sudo synaptic* would work.

Either you didn't issue those commands from the **recovery console** or you hadn't made the backups **exactly** as specified in the psychocats tutorial.

---

