---
title: "Administrator as Root"
date: 2013-02-26
forum: Any Other OS
---

### Post by offgridguy on 2013-02-26
Recent events have me wondering, besides Fedora, are there other linux distro's
that allow administrator privileges as Root?

---

### Post by cortman on 2013-02-26
?
There is a root account on every Linux system- it's part of the system. Ubuntu has it disabled by default, but you can enable it just by editing /etc/passwd. This holds true for any distro.

---

### Post by mörgæs on 2013-02-26
In case someone is wondering why it is disabled:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by offgridguy on 2013-02-26
Thank you for the replies, I have read the links provided and realize that ubuntu
regards this as a security feature, I also know how to set the root password and
log in as root using the methods we are not allowed to post in this forum, but I was thinking of distro's that don't come with these restrictive measures.

---

### Post by oldfred on 2013-02-26
I have only used Ubuntu, but most other distributions make you log into root to perform administrative activities and then log back in as your user. And only certain authorized users can login as root.

The disadvantage is then somewhat like Windows in that once you log in as root you do not want to change back to a user. But that creates all sort of issues.

---

### Post by buzzingrobot on 2013-02-26
The notion of an "Adminstrator" is, more or less, a Windows-ism. Administrator privileges in Windows are directly comparable to root privileges in Unix/Linux. Broadly speaking, you can either log in as root, become root temporarily, or use the sudo command to escalate your privileges to that of root on a command-by-command basis.

By default, Ubuntu limits the ways you can acquire root privileges.  This is to keep users from doing something like becoming the root user, forgetting they did this, and unintentionally deleting system files they would not be able to delete as a normal user.

Hence, the recommendation to just use sudo.

However, you can use "sudo -i" in a terminal to acquire root privileges, keeping them until you enter "exit".

There's nothing in Unix/Linux that requires users to constantly run as root, unlike Windows where many users always needed to run as the Administrator.  If someone is constantly staying logged in as root in Unix/Linux. they do not understand the system they are using.

---

### Post by cortman on 2013-02-26
Debian and most variants enable the root account by default. Straight Debian doesn't come with sudo configured.

---

### Post by offgridguy on 2013-02-26
> **oldfred said:**
> I have only used Ubuntu, but most other distributions make you log into root to perform administrative activities and then log back in as your user. And only certain authorized users can login as root.

The disadvantage is then somewhat like Windows in that once you log in as root you do not want to change back to a user. But that creates all sort of issues.
Thank you for the reply oldfred, your synopsis as always is correct:).
I have found some other distributions make it much easier to do, than ubuntu.

The potential for problems is certainly there, as you suggest in your comparison
to windows as administrator in windows has power to trash the entire system,if
they are foolish enough to do it.

My thoughts though are that most if not all newcomers to ubuntu are windows
users, and in spite of the unfettered control allowed by windows, probably
never had any serious problems because of it.  Myself included.  So I  find the
ubuntu restrictions puzzling.

---

### Post by prodigy_ on 2013-02-26
> **offgridguy said:**
>  I am thinking of Administrator in the
sense of admin. in windows which allows complete control of the Operating System.:-k

Windows in-built Administrator doesn't have full control. It's an elevated account but, for example, it can't even take ownership of an arbitrary registry key.

And root isn't really disabled in Ubuntu, only locked so that you can't directly log on to it. sudo -i still gives you interactive root shell, so in practice there's little difference.

---

### Post by offgridguy on 2013-02-26
> **buzzingrobot said:**
> The notion of an "Adminstrator" is, more or less, a Windows-ism. Administrator privileges in Windows are directly comparable to root privileges in Unix/Linux. Broadly speaking, you can either log in as root, become root temporarily, or use the sudo command to escalate your privileges to that of root on a command-by-command basis.

By default, Ubuntu limits the ways you can acquire root privileges.  This is to keep users from doing something like becoming the root user, forgetting they did this, and unintentionally deleting system files they would not be able to delete as a normal user.

Hence, the recommendation to just use sudo.

However, you can use "sudo -i" in a terminal to acquire root privileges, keeping them until you enter "exit".

There's nothing in Unix/Linux that requires users to constantly run as root, unlike Windows where many users always needed to run as the Administrator.  If someone is constantly staying logged in as root in Unix/Linux. they do not understand the system they are using.
Thank you for the reply, you have touched on the very core of the issue,
ie;you can escalate your privileges to root on a command by command basis.

How true, but this requires a proficient working knowledge of the CLI, as
administrator settings using the GUI in ubuntu are almost non-existent.
making the CLI an absolute must to utilize ubuntu to the fullest potential.

Realizing the importance of this, I am attempting to increase my knowledge
in this area, as you and many others are no doubt aware, it is a huge
learning curve.

---

### Post by offgridguy on 2013-02-26
> **prodigy_ said:**
> Windows in-built Administrator doesn't have full control. It's an elevated account but, for example, it can't even take ownership of an arbitrary registry key.

And root isn't really disabled in Ubuntu, only locked so that you can't directly log on to it. sudo -i still gives you interactive root shell, so in practice there's little difference.
Thank you for the insight, and especially for pointing out, that root is locked, I was
aware of this but other readers may not be.

---

### Post by MadmanRB on 2013-02-26
Eh there are ways to cheat in Ubuntu to enter applications under root/administration.
But in reality new users should not have the ability to much up the system thus why command line backends are encouraged.
If you are smart enough to know the terminal then you are smart enough to take responsibility for what you do to the OS.
Really being root is over rated, it allows so much to go wrong, this is why windows has so many security issues after all.
Really having to use command line isnt that hard if you have someone guiding you.
For a windows user this seems confusing but linux is not windows.

---

### Post by offgridguy on 2013-02-26
> **MadmanRB said:**
> Eh there are ways to cheat in Ubuntu to enter applications under root/administration.
But in reality new users should not have the ability to much up the system thus why command line backends are encouraged.
If you are smart enough to know the terminal then you are smart enough to take responsibility for what you do to the OS.
Really being root is over rated, it allows so much to go wrong, this is why windows has so many security issues after all.
Really having to use command line isnt that hard if you have someone guiding you.
For a windows user this seems confusing but linux is not windows.Thank you for the input, I don't find it confusing at all. Perhaps frustrating at times.  You are right, there are ways
to circumvent the restrictions, for new users these have to be found elsewhere than the forums.

However back to my original post, the only distro where I noticed you could establish a root
account ,has been Fedora, and yes you can do it in ubuntu, once you know how.
Probably for most users it doesn't matter.  The advanced user has taken control of their computer, the inexperienced don't even know there are other options. I would place myself
uncomfortably in the middle, too adventurous to be content with being denied access to my
own computer and not advanced enough to do much about it.:):)

---

### Post by deadflowr on 2013-02-26
> Really being root is over rated, it allows so much to go wrong, 

This is usually my main point in why not to run as root all the time.

As the old line says, "we have seen the enemy, and it is us."

I am, and would be, far more concerned by my own stupidity than someone trying to break into my system.
Though, being protected is a high priority.

---

### Post by offgridguy on 2013-02-26
> **deadflowr said:**
> This is usually my main point in why not to run as root all the time.

As the old line says, "we have seen the enemy, and it is us."

I am, and would be, far more concerned by my own stupidity than someone trying to break into my system.
Though, being protected is a high priority.Glad you weighed in here,
always appreciate your insight:) Actually I have never suggested  running as root all the time.  I have read enough of your posts to ever believe you would need to
be protected from your own stupidity:) nor would the vast majority of ubuntu
users.

---

### Post by The Cog on 2013-02-26
> **offgridguy said:**
> You are right, there are ways
to circumvent the restrictions, for new users these have to be found elsewhere than the forums.

Your problem is that you are still thinking windows. You think the restrictions are a bad thing. They are not, any more than a guard rail between a walkway and a busy road is a bad thing. It stops you having disasters. On rare occasions there is a need to bypass the protection, but mainly it protects. 

Try to get used to the fact that there are two separate functions here - system administration, and using the system. When you are merely using the system, you don't need the root access. I have been using Linux all day. I slipped into the admin role for a few minutes to install updates, and later to run a network packet trace. That's all.

It reminds me of wearing car seat-belts. There was a lot of complaining when it was made compulsory here in the UK, with people complaining about removing their rights. But hospital admissions and death rates dropped. Organ transplants became harder to get, apparently, which is unfortunate for those who are waiting for one. These days, I feel rather vulnerable if I am not wearing a seatbelt. And after a surprise a few years ago, I might not be so stunningly handsome now if I had not been wearing a seatbelt that day.

---

### Post by Habitual on 2013-02-26
> **The Cog said:**
> Your problem is that you are still thinking windows. Baby Duck Syndrome?

---

### Post by offgridguy on 2013-02-26
@The Cog, Thank you for the reply, as a neophyte to windows, some years back
i managed to survive, and amazingly so did my computer and Operating System,
without the safeguards that canonical and ubuntu  think are so essential.

Totally agree with you about, system use and system administration.  The actual
term Administrator is probably not even suited to ubuntu, given what most peope
think  when you use the term in windows.  In fedora as well the term administrator
refers to the root account.

---

### Post by haqking on 2013-02-26
> **offgridguy said:**
> @The Cog, Thank you for the reply, as a neophyte to windows, some years back
i managed to survive, and amazingly so did my computer and Operating System,
without the safeguards that canonical and ubuntu  think are so essential.

Totally agree with you about, system use and system administration.  The actual
term Administrator is probably not even suited to ubuntu, given what most peope
think  when you use the term in windows.[B]  In fedora as well the term administrator
refers to the root account[/B].

no it doesnt, root is root, an administrator is a user with administrative privelege

root is UID 0 and there wont be any other accounts with that UID, including your Administrator account.  There is only one ROOT and there can be many administrator accounts.

---

### Post by offgridguy on 2013-02-26
> **haqking said:**
> no it doesnt, root is root, an administrator is a user with administrative privelege

root is UID 0 and there wont be any other accounts with that UID, including your Administrator account.  There is only one ROOT and there can be many administrator accounts.
Thank you for the edit, good explanation.  Maybe I missed something here in Fedora, I don't recall seeing any mention of administrator in regard to my account.
By the way,thanks for the visit.:D

Upon rereading these posts,there seems to be the misconception that I advocate running as root, at all times, this is simply not the case, I have not suggested that or even intimated that.

To clarify, I prefer the approach that fedora takes, where the root account is established with
a password upon installation, then when functions arise requiring administrative permissions
you are prompted for the root password to fulfill those functions, this doesn't mean running
as root, rather root privileges are quickly and easily available.

I am still wondering which other linux distro's offer a similar feature?

From reading this
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
and other similar sites, I realize how ubuntu approaches this and why, but that debate was
not what i started this thread for. I have edited the original post to more accurately
address the question.

---

### Post by Armann on 2013-02-27
> **offgridguy said:**
> 
To clarify, I prefer the approach that fedora takes, where the root account is established with
a password upon installation, then when functions arise requiring administrative permissions
you are prompted for the root password to fulfill those functions,

I am still wondering which other linux distro's offer a similar feature?


"then when functions arise requiring administrative permissions"
Again, it's root permissions, even though your doing administrative tasks it's root permissions. ;)

Yes all the Redhat distros make you setup a root password when you install the operating system, Redhat, Centos, Fedora etc...

---

### Post by haqking on 2013-02-27
> **offgridguy said:**
> 

I am still wondering which other linux distro's offer a similar feature?

.

All Linux distros offer the same thing as does Windows.  it is called least privelege.


You run everything as an ordinary user and elevate privelege to authorise an administrative action.

In Linux there is ROOT and there is Admin users who usually use "sudo" and enter their own password to authorize actions (entering own password confirms the action) the ability to do so is there group membership.

In windows everyone thinks you do everything as Administrator, well there is a Administrator account in windows aside from the one you create when you first install it.  UAC in recent version is similar to the confirmation model used with sudo (and i said similar not the same) it is just that in Windows it defaults to the user being an administrator, well most Linux distros default the first created user aside from root to being admin also.

You should in all OS use a limited ordinary account (least privelege) for day to day tasks and when required elevate the privelege or login with a elevated account.

In all Linux distros you can if you want login as root, including Ubuntu, and you can use sudo also if preferred or in some you just su (su to root or to any other user), and in all Linux distros it is suggested you run as Least privelege, it is just in Ubuntu root is locked in so much as it has no password set by default.

You might be interested in these: (I am not a fan of opinionpedia but these are decent)

[https://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features](https://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features)
[https://en.wikipedia.org/wiki/Principle_of_least_privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege)


Peace

---

### Post by The Cog on 2013-02-27
> **offgridguy said:**
> To clarify, I prefer the approach that fedora takes, where the root account is established with
a password upon installation, then when functions arise requiring administrative permissions
you are prompted for the root password to fulfill those functions, this doesn't mean running
as root, rather root privileges are quickly and easily available.

I am still wondering which other linux distro's offer a similar feature?
All distros have a root account.
All distros allow the existence of non-root accounts which have reduced priviledges. 

It is many years since I installed a distro that didn't require creation of a non-root account as part of the install procedure, maybe 20, if I recall correctly.

So in effect, all distros have this "feature". Ubuntu is unusual in using sudo rather than su for admin tasks, and thus requiring your own password rather than the root password. But that's the only noticeable difference.

---

### Post by offgridguy on 2013-02-27
> **The Cog said:**
>  Ubuntu is unusual in using sudo rather than su for admin tasks, and thus requiring your own password rather than the root password. But that's the only noticeable difference.Do other distro's lock the root account?

---

### Post by offgridguy on 2013-02-27
> **haqking said:**
> 
In all Linux distros you can if you want login as root, including Ubuntu, and you can use sudo also if preferred or in some you just su (su to root or to any other user), and in all Linux distros it is suggested you run as Least privelege, it is just in Ubuntu root is locked in so much as it has no password set by default.

You might be interested in these: (I am not a fan of opinionpedia but these are decent)

[https://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features](https://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features)
[https://en.wikipedia.org/wiki/Principle_of_least_privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege)


PeaceThank you for the reply and the links, although
you can log in as root in any distro, as you said,I find the
method's so remarkably different between fedora and ubuntu, the latter being hidden in effect and only accessible through the
Command Line Interface. The former being present and visible,
only requiring a password when permissions are required. In effect making it easier to
perform administrative tasks using the GUI, at least for the uninitiated.
Thanks again.

---

### Post by haqking on 2013-02-27
> **offgridguy said:**
> Thank you for the reply and the links, although
you can log in as root in any distro, as you said,[B]I find the
method's so remarkably different between fedora and ubuntu[/B], the latter being hidden in effect and only accessible through the
Command Line Interface. The former being present and visible,
only requiring a password when permissions are required. In effect making it easier to
perform administrative tasks using the GUI, at least for the uninitiated.
Thanks again.

really ?

You give root a password during install thats about it as you do with most distros other than Ubuntu and a couple of others i believe.

Other than that things are the same, your own account uses sudo to authenticate an action.

I am in F18 right now, if i want to perform an admin action I will use:

sudo <command>

same as in Ubuntu or any other distro using sudo.

I rarely if ever need to use the "root" account or its password so may aswell be locked as in Ubuntu.

If i do the methods as the same in Fedora or Ubuntu except that you need to give Ubuntu root a password first (which is what you do during a fedora install) its just a "when" thing.

Peace

---

### Post by buzzingrobot on 2013-02-27
Teapot and tempest.

Fedora, etc., allow ordinary users to be added to the wheel group. The sudoers file can, optionally, be edited to allow a user in the wheel group to, for example, do a "sudo command" without being prompted for a password.

By default, Ubuntu does not have a wheel group. (It doesn't prevent the creation of one.)  So, I can't execute "sudo command" without a password prompt, because I need to be in the wheel group to enable that. 

If someone wants to use the more traditional approach to acquiring root privileges in Ubuntu, and they know how, they can easily do that.

In Fedora, I can do "su -", for example, enter a password, and become root.  I can't in Ubuntu.  The root user exists, though.

In Fedora, I can do "sudo -i" and escalate my privileges to root for as long as I wish.  Ditto in Ubuntu.

In Ubuntu, do a "sudo whoami" and see what it says.

As for the Windows Adminstrator comparision, it's been more than 10 years since I used Windows. But, I do recall that some versions of Windows tried to generate a false sense of security by prompting for a password to do almost any little thing. The easiest way to avoid this annoyance was to simply run as a Windows Administrator. Unix/Linux uses an entirely different design.  If a Linux user is frequently asked to acquire root privileges trying to accomplish routine tasks, then, more than likely, that user is doing something very wrong.

---

### Post by The Cog on 2013-02-27
> **offgridguy said:**
> Do other distro's lock the root account?
Not as such. But the distro I used before Ubuntu (Mandrake) did not allow root to log in using the GUI. This could be reconfigured, just as the root password in Ubuntu can be unlocked, but it was the default. I believe it is normal to discourage permanent login as root. 

I have never tried Fedora. But Mandrake was Red Hat based, and I'm sure I remember a popup password prompt when trying to launch admin tasks, just like I see in Ubuntu. But I had to enter teh root password, not my own. What is this "huge difference" between Fedora and Ubuntu that you refer to? I'm not being sarcastic - I just don't see much difference.

---

### Post by offgridguy on 2013-02-27
> **The Cog said:**
>  
I have never tried Fedora. But Mandrake was Red Hat based, and I'm sure I remember a popup password prompt when trying to launch admin tasks, just like I see in Ubuntu. But I had to enter teh root password, not my own. What is this "huge difference" between Fedora and Ubuntu that you refer to? I'm not being sarcastic - I just don't see much difference.Maybe not a big thing but
as an example, i can be accessing a file , ubuntu gives access denied,or permission denied, fedora prompts for password.

---

### Post by buzzingrobot on 2013-02-27
> **offgridguy said:**
> Maybe not a big thing but
as an example, i can be accessing a file , ubuntu gives access denied,or permission denied, fedora prompts for password.

In both cases, the user -- you -- lacks the necessary privileges. The Fedora tool follows the more traditional route, which is to deny access.  The Ubuntu tool also denies access, as it should, but adds the nicety of popping up a dialog to let you log in as the root user. 

So, the difference is that the Fedora tool assumes you are clever enough to know, or learn, how to temporarily bump up your privileges on your own. There's no difference in the underlying structure.

---

### Post by The Cog on 2013-02-27
> **offgridguy said:**
> Maybe not a big thing but
as an example, i can be accessing a file , ubuntu gives access denied,or permission denied, fedora prompts for password.
By can be accessing a file, you mean in nautilus, the file manager?  If so, I've never seen that before, and to be honest I had never thought of the idea: I always just launch a root file manager when needed (maybe once a week). I wonder just how useful that would be in real life. Hmm...

---

### Post by MadmanRB on 2013-02-27
you can open nautilus as root in ubuntu using unity via the launcher.
or installing the packages from [https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)
Also, pcmanfm

---

### Post by dodo3773 on 2013-03-03
> **buzzingrobot said:**
> Teapot and tempest.

Fedora, etc., allow ordinary users to be added to the wheel group. The sudoers file can, optionally, be edited to allow a user in the wheel group to, for example, do a "sudo command" without being prompted for a password.

By default, Ubuntu does not have a wheel group. (It doesn't prevent the creation of one.)  So, I can't execute "sudo command" without a password prompt, because I need to be in the wheel group to enable that. 

If someone wants to use the more traditional approach to acquiring root privileges in Ubuntu, and they know how, they can easily do that.

In Fedora, I can do "su -", for example, enter a password, and become root.  I can't in Ubuntu.  The root user exists, though.

In Fedora, I can do "sudo -i" and escalate my privileges to root for as long as I wish.  Ditto in Ubuntu.

In Ubuntu, do a "sudo whoami" and see what it says.

As for the Windows Adminstrator comparision, it's been more than 10 years since I used Windows. But, I do recall that some versions of Windows tried to generate a false sense of security by prompting for a password to do almost any little thing. The easiest way to avoid this annoyance was to simply run as a Windows Administrator. Unix/Linux uses an entirely different design.  If a Linux user is frequently asked to acquire root privileges trying to accomplish routine tasks, then, more than likely, that user is doing something very wrong.
 
You don't have to use wheel as your group preference for sudo without a password. Also, if you want to su to root all you have to do is change your root password. It's all pretty trivial. As you said already though:   Teapot and tempest.

---

### Post by mamamia88 on 2013-03-03
> **buzzingrobot said:**
> The notion of an "Adminstrator" is, more or less, a Windows-ism. Administrator privileges in Windows are directly comparable to root privileges in Unix/Linux. Broadly speaking, you can either log in as root, become root temporarily, or use the sudo command to escalate your privileges to that of root on a command-by-command basis.

By default, Ubuntu limits the ways you can acquire root privileges.  This is to keep users from doing something like becoming the root user, forgetting they did this, and unintentionally deleting system files they would not be able to delete as a normal user.

Hence, the recommendation to just use sudo.

However, you can use "sudo -i" in a terminal to acquire root privileges, keeping them until you enter "exit".

There's nothing in Unix/Linux that requires users to constantly run as root, unlike Windows where many users always needed to run as the Administrator.  If someone is constantly staying logged in as root in Unix/Linux. they do not understand the system they are using.
I still don't understand how a person could "accidentally" delete something as root in linux.   To delete something as root you have to first either use sudo rm path/to/file.   A user may delete something thinking it would have one outcome but it might have another doesn't mean that it was an accident.  And how did you forget you became root?  Worse case scenario is you leave a terminal window open with a # showing instead of $.  you would still have to type rm and spell out the path to the file to delete it.   root by itself is kinda harmless just like guns.  a gun has never killed someone without a person behind the trigger.  it may be stupid though to give everybody guns by default though.  i could argue that i could do just as much damage with sudo as i could su.  you hand over your gun to a crazy person and you are asking for trouble.

---

### Post by Woodzman on 2013-03-04
> **offgridguy said:**
> Recent events have me wondering, besides Fedora, are there other linux distro's
that allow administrator privileges as Root?The only distro's that give the features that you are looking for are Slackware, Crux and Zenwalk
which is Slackware based. Slackware sets the root account at installation and does not ask you to establish any other account.

---

### Post by haqking on 2013-03-04
> **Woodzman said:**
> The only distro's that give the features that you are looking for are Slackware, Crux and Zenwalk
which is Slackware based. Slackware sets the root account at installation and does not ask you to establish any other account.

To be clear for the OP, EVERY Linux distro allows logging in as root and you never have to use another account if you dont want to (though as i mentioned before least privelge should always be used)

As far as Installation goes though and not "having" to create another account to use with sudo or similar and giving root a password at installation then there are a few.

Peace

---

### Post by sioxs on 2013-03-04
> **cortman said:**
> Debian and most variants enable the root account  by default. Straight Debian doesn't come with sudo configured.
Yes it does!
But you have to install from the Advanced features not the standard GUI Install

Peace!
***"We can't solve problems with the same kind of thinking we used when we created them"***

---

