---
title: "su issues"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by sujinge9 on 2008-02-27
I'm having issues getting on as su. 
When I type su in shell, I am prompted for my password and it keeps on telling me its wrong despite the fact that I use the exact same password for sudo. Please help... somehow?

---

### Post by taurus on 2008-02-27
I think you're a little confused between sudo and su.  They are not the same thing.  Sudo requires your own password because you have a root privilege, belonging to group admin.  Meanwhile, su requires the actual root's password which if you haven't created one, you can't run it.

---

### Post by kool_kat_os on 2008-02-27
the root password is different from your user password

i think that you have to set a password,

i think this is the command to set a password:
```
sudo passwd root
```

I wouldnt use the "su"command though...thats what sudo was created for :)

---

### Post by kool_kat_os on 2008-02-27
by the way, what are you trying to do?

---

### Post by kerry_s on 2008-02-27
the root is disabled for security, using sudo, they have to guess your name and password, using su, they only need to guess your password.

use
**sudo su**
or
**sudo -i**

to become root, leave root disabled.

---

### Post by kool_kat_os on 2008-02-27
> **kerry_s said:**
> the root is disabled for security, using sudo, they have to guess your name and password, using su, they only need to guess your password.

use
**sudo su**

to become root, leave root disabled.

so was i wrong?

---

### Post by deepclutch on 2008-02-27
hmm...I had a weird experience of my root password not working with 
"su -" after I swapped my Debian Sid from a dead 80GB sata hdd to current hdd :p.
later found that "su"'s suid bit is disabled,same happened with "mount" command also.anyways I reinstalled/changed the packages to fix the problemo. ;)

---

### Post by redrocket on 2008-02-27
i use:

sudo su -

keeps the alias's of my user when becoming root

---

### Post by kool_kat_os on 2008-02-27
redrocket....

who chose your user name?

no...wait...nevermind...id rather not know.

---

### Post by redrocket on 2008-02-27
you know why :D
south park ;)

---

### Post by kool_kat_os on 2008-02-27
> **redrocket said:**
> you know why :D
south park ;)

oh ya..now i remember......:)

---

### Post by kerry_s on 2008-02-27
> **kool_kat_os said:**
> so was i wrong?

no, he may still choose to enable root, but you should tell them why it is the way it is and how to do it with out compromising security. :)

even when i use debian, i setup sudo and disable root.

to disable root, in case he's already activated it is->
**sudo passwd -l root**

---

### Post by kool_kat_os on 2008-02-27
> **kerry_s said:**
> no, he may still choose to enable root, but you should tell them why it is the way it is and how to do it with out compromising security. :)

even when i use debian, i setup sudo and disable root.

to disable root, in case he's already activated it is->
**sudo passwd -l root**

do you need root to do some crontab stuff?

---

### Post by redrocket on 2008-02-27
is that actually disabling root, or is it just disabling root's password?

sudo su -
id
tells me im root

---

### Post by kool_kat_os on 2008-02-27
> **redrocket said:**
> is that actually disabling root, or is it just disabling root's password?

sudo su -
id
tells me im root

are you talking about sudo su?

---

### Post by Mr. C. on 2008-02-27
> **redrocket said:**
> i use:
sudo su -


This is like **cat |  cat**.  Try:

**sudo -s**

MrC

---

### Post by redrocket on 2008-02-27
no sorry:
this: sudo passwd -l root
this disables password for root, so no password associated with user. account still works though.

and this: sudo su -
this is what i use to become root, even though it's password is disabled.

i phrased all that as statements, it's really a question though, as in, is that right or wrong?

---

### Post by kool_kat_os on 2008-02-27
> **redrocket said:**
> no sorry:
this: sudo passwd -l root
this disables password for root, so no password associated with user. account still works though.

and this: sudo su -
this is what i use to become root, even though it's password is disabled.

i phrased all that as statements, it's really a question though, as in, is that right or wrong?

how do you logon as root if its disabled?

---

### Post by Mr. C. on 2008-02-27
Both programs change the Effective UID/GID of the process in a spawned shell, thus yielding changed (possibly elevated) privileges.

There is no reason to use **sudo** to call **su** - it is redundant and superfluous.  In the **sudo su** command line, **sudo** creates a new process by invoking **su**, which in turn then creates its own subshell with changed privileges.  But guess what: the **-s** option to **sudo** tells **sudo** to spawn its own subshell with changed privileges (by default, to root).

MrC

---

### Post by sujinge9 on 2008-02-27
sudu su works well though it still confuses me how the password I use for sudo and su are different.
As for the reason, I'm installing a bunch of things and theres not many reasons why I can't use sudo instead, I just wanted to try su out and was just wondering why it wouldn't work. 
Thanks alot for the quick and helpful replies.

---

### Post by Mr. C. on 2008-02-27
> **sujinge9 said:**
> sudu su works well though it still confuses me how the password I use for sudo and su are different.

The **sudo** command requests YOUR user password.  The **su** command requests the password of the user in which you will become!

Example:

```
sudo ls

```
requests **MY** password and runs the **ls** command as root.
```

su ls
```

requests the **ROOT** password and runs the **ls** command as root.

Therefore, the command:

```
sudo su
```

requests MY password and runs the su comamnd as root, which when run as root, requires no password !


> **sujinge9 said:**
> 
As for the reason, I'm installing a bunch of things and theres not many reasons why I can't use sudo instead, I just wanted to try su out and was just wondering why it wouldn't work. 
Thanks alot for the quick and helpful replies.

Now you know...

MrC

---

### Post by redrocket on 2008-02-27
Thank you MR C :)
now, how to keep my alias' when using sudo -s

I suppose i could just add them to root's profile

---

### Post by Victormd on 2008-02-27
> **Mr. C. said:**
> Both programs change the Effective UID/GID of the process in a spawned shell, thus yielding changed (possibly elevated) privileges.

There is no reason to use **sudo** to call **su** - it is redundant and superfluous.  In the **sudo su** command line, **sudo** creates a new process by invoking **su**, which in turn then creates its own subshell with changed privileges.  But guess what: the **-s** option to **sudo** tells **sudo** to spawn its own subshell with changed privileges (by default, to root).

MrC

ignorant question: Is SU actually disabled or is that a figure of speech?

Because I was following some setup instructions and the thread command was using SU so I tried it and my password was wrong. Then I found out that the root had a randomly generated password and that you could change it under system>administration>users and groups so that's what I did and it worked... does that mean that I enabled my root? Or simply set a password that I know?

---

### Post by Mr. C. on 2008-02-27
Neither command "keeps" the aliases.  Rather, both commands will set certain flags signaling for the newly created shell to perform a particular kind off startup (eg: login shell, interactive shell), and this defines which startup files are read.

In su, the - (same as -l) simulates a full login.  See the man page for all that occurs.
In sudo, the -i option performs similarly

If you just run:
```

sudo -s
```

the new shell will be a root shell, with YOUR current environment and setup.

MrC

---

### Post by Mr. C. on 2008-02-27
> **Victormd said:**
> ignorant question: Is SU actually disabled or is that a figure of speech?

The command is NOT disabled.  You cannot use **su** by default to become root, because the root password is *unknown* to you!  That's the way ubuntu sets things up.

Verify this for yourself.  Run:

```
su -l *myusername*
```

changing *myusername* to your own user name of course.  You'll see that **su** runs perfectly well.

> **Victormd said:**
> 
Because I was following some setup instructions and the thread command was using SU so I tried it and my password was wrong. Then I found out that the root had a randomly generated password and that you could change it under system>administration>users and groups so that's what I did and it worked... does that mean that I enabled my root? Or simply set a password that I know?

There is no *enabling* or *disabling* of root.  There are two concepts here:  the User ID (aka: UID) and an account name called root.  The Unix/Linux kernel only cares about the former - the UID.

The root user name is simply a standard name for any UID=0 account.  By making the root user account's password unavailable to you, in essence, you cannot simply use system login utilities to login as the root user (because you don't know the password!).  But you have discovered all that is required is to set the password to something you know, and then you can login as root, just like you can any other user.

MrC

---

### Post by kerry_s on 2008-02-28
sorry everyone, i always phrase that wrong. i'm just lucky " Mr. C. " is on it.

---

### Post by Victormd on 2008-02-28
> **kerry_s said:**
> sorry everyone, i always phrase that wrong. i'm just lucky " Mr. C. " is on it.
I've read this (SU is disabled by default) in several places and never really understood the concept of disabling root user. I figured it was what Mr. C. explained but it doesn't hurt to ask... :)

---

### Post by bodhi.zazen on 2008-02-28
Actually ....

The root account is locked (as opposed to a random or unknown password). That root has some random or unknown password is a common misconception.

See this link : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **By default, the root account password is locked in Ubuntu.**

You can (dare I say easily ?) confirm this if you examine the system files (and know what they mean).

Also, you should use sudo -i

```
sudo -i
```

Rather then sudo -s to become root. -i = root's environment , -s = your users environment. Using the wrong environment with root is usually "OK" but can cause problems.

---

### Post by aysiu on 2008-02-28
> **bodhi.zazen said:**
> Actually ....

The root account is locked (as opposed to a random or unknown password). That root has some random or unknown password is a common misconception.

See this link : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)



You can (dare I say easily ?) confirm this if you examine the system files (and know what they mean). One file to look at is /etc/shadow. If you look at root's line in that file and read up on the /etc/shadow documentation, it's quite obvious the account is locked and there is no password for it.

---

### Post by Mr. C. on 2008-02-28
> **bodhi.zazen said:**
> Actually ....

The root account is locked (as opposed to a random or unknown password). That root has some random or unknown password is a common misconception.

Good link.

A "locked" accounts via -l simple changes the password to one that cannot decrypt such as the single character * or the word LOCKED.  This is a harder concept to explain, and is pedantic.

Both -s and -i have their places and purpose; I use both, depending upon my needs.  It is probably better to advise when and why to use either, than provide blank "don't do this" statements (since we're being educative here!).

MrC

---

### Post by Joeb454 on 2008-02-28
But as a basic rule - I would advise using ```
sudo -i
``` because depending on what you do, you can end up messing up the permissions on some folders.

It's also less confusing for new(ish) people to say "use this instead of that, because it's a safer method" Then if they want to know more, they can ask :)

---

### Post by Mr. C. on 2008-02-28
There are all sorts of ways to hang yourself.  Using -i sets up root's environment (aliases, PATH, environment, etc), and this also confuses people (where have my aliases gone?, why aren't my commands found?  Why can't I find man pages, etc. etc. etc).

I have no interest in specifying recipes... I prefer explaining how to cook.

MrC

---

### Post by Joeb454 on 2008-02-28
I think having new users knowing that root is completely separate from a normal user, and that they can wipe their system with 1 command in root mode, is a good thing.

But hey, I'm just voicing my opinion...

---

### Post by k33bz on 2008-02-28
> **Joeb454 said:**
> I think having new users knowing that root is completely separate from a normal user, and that they can wipe their system with 1 command in root mode, is a good thing.

But hey, I'm just voicing my opinion...

as do I agree, I think that is very important info for a new user to Linux to have.  Not to scare them into not using root, but to make sure they are more careful in using root, or any super user for that matter.

---

### Post by Mr. C. on 2008-02-28
The Ubuntu-ization of *nix has not made systems safer, more secure, or easier to avoid misconfiguration.  It has simply taught user's to mindlessly type "sudo" in front of every command.  Haggling about which options are best, is like haggling about which car alarm sound is more of a theft-deterrent.  In the end, we've all been conditioned to just ignore the noise...

---

### Post by Joeb454 on 2008-02-28
Just to satisfy my curiosity...When have I or anybody else said that Ubuntu has made it more secure?

Either way, people learn from mistakes, that's why the forums exist. That's my view on the subject.

---

