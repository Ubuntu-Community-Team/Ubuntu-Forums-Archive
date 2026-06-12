---
title: "I just want permissions.. Without opening an application."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-08-30
I just want full priveledges once i log on. Thats it.

How do I do this?

---

### Post by John.Michael.Kane on 2006-08-30
[COLOR="Red"]**You do this at your own risk. do not post here should you screw up your system  using this method**[/COLOR]

Enabling the root account:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root

---

### Post by IYY on 2006-08-30
You don't want that. Trust me, you don't. It is one of the dumbest things a Linux user could ever do, and will make your system as vonurable as Windows.

But if you really insist... I think you can use the command

```
sudo passwd root
```

to change the root password, and then you'll be able to login as root. Then add the local system administrator login in Login Window (System > Administration > Login Window).

Don't do this!

---

### Post by aysiu on 2006-08-30
Why do you want to do this?

Does your bank offer you an ATM card without a PIN so that people can mug you and take money out of your bank without needing a password?

Do you leave your apartment door unlocked because you can't be bothered to fumble around for a key when you get home?

---

### Post by wana10 on 2006-08-30
hey now...give the guy a break.
i personally love the ubuntu philosophy regarding sudo over root but it isn't for everyone. some people prefer to login as root to do a lot of system maintenence instead of gksudo 'whatever' or sudo 'whatever'
so link to [HTML]https://help.ubuntu.com/community/RootSudo[/HTML] and lets let him make his own choice. linux is about choice and freedom to make those choices. if i were a long time suse or redhat user i would find the transition odd (i wasn't so i didn't) and baby steps are sometimes better than leaps

---

### Post by edrodgers731 on 2006-08-30
I see the point of using sudo instead of logging in as root... But honestly... 99.99% of all *nixes out there have a root login account.  If you have the slightest idea of what you are doing, there is no REAL danger to having a root login.  If someone nabs a user password, with sudo they also get root access.  That sounds like a negative to me.  Just do it the old fashoned way.  Only su to root if you have to.

I have gotten used to sudo in Ubuntu.  But I won't start putting sudo on my production boxes at work.

-Ed

---

### Post by aysiu on 2006-08-30
Yes, people can choose to make foolish choices, and we can choose to let them know those choices are foolish.

---

### Post by goatflyer on 2006-08-30
Maybe he just wants a 'sudo'ed terminal icon, something that does something like "sudo xterm" or something (gksudo xterm?) so when he clicks on that terminal, all his commands are done at root level.  If his own user password is set to empty, this could be very local, maybe even safe, no?

---

### Post by Omnios on 2006-08-30
I hear you about the root thing and I found that I wanted to have root access with my log in I even found that I set up some core file areas with my user permitions and found my computer owned where I found out someone was running a westnort server on my machine. 

 You can run things as root if you want but be warned of the security risks in that if someone accesses your computer they will have access to everything where as using sudo there access would be limited.

 Anyways there are also a few tricks around with root scripts that will allow you to open a directory in root nautilus and root gedit etc. Anyways  we might think of making some more flexability in root run scripts etc or even buttons in the future for convienience and functionality while maintaing a shred of security

---

### Post by aysiu on 2006-08-30
I would read this before you log in as root graphically:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by -deadcats on 2006-08-30
systemintheglitch...appropriate name, gotta congratulate you...I've reviewed all of your posts to date...

MY RECOMMENDATION: (and just mine)
1. Grab a good linux book...plenty of free ones online if ya grok "google"...
2. Linux is not Windows. 
3. Linux, like Windows, is an Operating System. But MORE than that, it's a network operating system and believe it or not, your machine is just another node on the network--EVEN if it's the sole node. By running as a User rather than (say) a Network Administrator, your machine has the highest level of both internal and external protection. It protects you from them bad-guys out thar in the intarweb, and it protect you from yourself. (Personally, my data has always been in more danger of me than anyone else.)
4. Until you become amenable to learning the "linux way" you will continue to have problems with your system.
5. You were on a bicycle with Windows. With linux, you've got a motorcycle to learn how to ride. Learn to learn.

regards,
-dc

---

### Post by edrodgers731 on 2006-08-31
Wow..  This is really interesting.  Giving a "regular" user complete root access is fine, but actually calling it root?  THAT'S BAD.  Having a root account is not foolish for everyone.  Millions of *nix geeks happily live their lives with the occasional su to root.  To call this foolish is like calling the entire *nix world foolish, with the exception of Ubuntu users.  Hmmmm.  But you have decided, so I'll let you sit up there sipping your latte, calling the things other people do "foolish".

Thanks,
Ed

---

### Post by blackened on 2006-08-31
> **edrodgers731 said:**
> Wow..  This is really interesting.  Giving a "regular" user complete root access is fine, but actually calling it root?  THAT'S BAD.  Having a root account is not foolish for everyone.  Millions of *nix geeks happily live their lives with the occasional su to root.  To call this foolish is like calling the entire *nix world foolish, with the exception of Ubuntu users.  Hmmmm.  But you have decided, so I'll let you sit up there sipping your latte, calling the things other people do "foolish".

Thanks,
Ed

I think you're misunderstanding Ed:

They're not at all saying he's foolish for wanting a root login, they're saying he's foolish for wanting to run as root ALL THE TIME. 

You must admit that any sane *nix geek would agree with that idea.

I agree that some users are better off with a root login to forego the hassle, but most I've talked to don't have any problem with sudo. The largest benefit I see is if you unknowingly/unwittingly have certain ports (ssh for instance) open, then it's a heckuvvalot easier for outsiders to hammer at brute-forcing the root user than it is for them to have to randomly guess your user name AND password. Sudo is, at least, a step in the right direction.

---

### Post by suhaib on 2006-08-31
Is there anyway of disabling this root user later.  That is, lets say i type "sudo passwd root" is there anyway I can get rid of it after?

---

### Post by edrodgers731 on 2006-08-31
> **blackened said:**
> I think you're misunderstanding Ed:

They're not at all saying he's foolish for wanting a root login, they're saying he's foolish for wanting to run as root ALL THE TIME. 

You must admit that any sane *nix geek would agree with that idea.

I agree that some users are better off with a root login to forego the hassle, but most I've talked to don't have any problem with sudo. The largest benefit I see is if you unknowingly/unwittingly have certain ports (ssh for instance) open, then it's a heckuvvalot easier for outsiders to hammer at brute-forcing the root user than it is for them to have to randomly guess your user name AND password. Sudo is, at least, a step in the right direction.

That's a sane argument.

I have turned many of my collegues on to Ubuntu, and the first thing they want to do is put in a root password.  It's simply the way people have worked for the last 36 years.  I must admit that I too gave a password to root at first.  I've since gone back to the sudo method.  But sudo is no silver security bullet.  Sudo has been around for a long, long time, and has always been thought of as a security compromise.  A way of giving regular users the ability to run a few root commands.  THAT was considered foolish.  It's hard for an old dog like me to feel cozy about sudo.  But, I understand the arguments and it is SLIGHTLY safer. (until everyone does it and attackers change focus)

I think it's better to explain the pros and cons of a thing, rather than to just start dictating how one should run their system.  Then I start ranting.

Sorry for the explosion.

-Ed

---

### Post by toasted on 2006-08-31
> **suhaib said:**
> Is there anyway of disabling this root user later.  That is, lets say i type "sudo passwd root" is there anyway I can get rid of it after?

Simply issuing the root password will not enable you to log in as root. You also have to enable root log in. 

Go to System/Administration/Login Window
click the security tab

Check the "Allow Local system administrator login' box to allow root log in

---

### Post by suhaib on 2006-08-31
> **toasted said:**
> Simply issuing the root password will not enable you to log in as root. You also have to enable root log in. 

Go to System/Administration/Login Window
click the security tab

Check the "Allow Local system administrator login' box to allow root log in

Just as I thought, I checked that already but was unsure.  Thanks for the clarification!

---

### Post by edrodgers731 on 2006-08-31
> **toasted said:**
> Simply issuing the root password will not enable you to log in as root. You also have to enable root log in. 

Go to System/Administration/Login Window
click the security tab

Check the "Allow Local system administrator login' box to allow root log in

Interesting.  I didn't know that.  When I did my root login, I was using the server edition.  Because there was no X, it wasn't an issue.  Learn something new every 30 seconds.

Thanks,
Ed

---

### Post by suhaib on 2006-08-31
> **edrodgers731 said:**
> Interesting.  I didn't know that.  When I did my root login, I was using the server edition.  Because there was no X, it wasn't an issue.  Learn something new every 30 seconds.

Thanks,
Ed For some reason I needed root log-in to configure my Xserver.  Sudo was returning permission denied everytime!

---

### Post by blackened on 2006-08-31
> I think it's better to explain the pros and cons of a thing, rather than to just start dictating how one should run their system.

While I agree with this, I do see the point in starting new users with no root login by default. Most hardened (or at least seasoned) *nix users will quickly hit the forums with "Why the heck can't I log in as root?".

Actually I take that back: Most hardened (or at least seasoned) *nix users will hit the forum search function or google with the search query '"root login wtf" site:http://ubuntuforums.org' or some such. Then if they find no answers after ten hours of silent trolling, then they MIGHT start a thread with that subject. This includes me.

---

### Post by steve.horsley on 2006-08-31
> **suhaib said:**
> Is there anyway of disabling this root user later.  That is, lets say i type "sudo passwd root" is there anyway I can get rid of it after?

Yes. > sudo passwd -l root -l for lock.

---

### Post by suhaib on 2006-08-31
> **steve.horsley said:**
> Yes.  -l for lock.

Oh ok, thanks for that.

---

### Post by angkor on 2006-08-31
Just having a root login at the console is perfectly safe (strong password as always) and if you want to do it enable the root account as mentioned before. 

Just don't enable a graphical root login. If you need a graphical root login at your linux box chances are very high you'll fsck up your system.

---

