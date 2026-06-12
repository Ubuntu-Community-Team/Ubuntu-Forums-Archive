---
title: "Perimssions?  Whats up with that?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by singlewc on 2007-11-07
I have been in and out of many linux distros over the years. Maybe I never got it, but something is really weird with Ubuntu 7.10 , and so maybe someone can explain it so I can understand it.

There is a root account, and users accounts. Root has all the rights and privileges, and  no one should log on as root.I get that. Makes sense.  My account is called john, and of course I have a password for that account. Cannot log into the system as root, so that is rather odd to me, but I digress.

When I log onto my Ubuntu install, it asks my name and password, so I give it 'john' and 'johnspassword'

Then, when I want to do something that as far as I ever understood, requires root privileges, like sudo, it asks for john's password,  not root. If I am already logged in as john, why the heck does it keep asking me for john's password to do root processes?

I installed vmware, and really am no pro, so I just did whatever the instructions said to do, and I ended up with vmware not running from the applications menu, because I would have to use terminal, 'sudo vmare' and give it the password for "john' which is who I am, and I already logged in as john, so this is making no sense.

A kindly user pointed out how to change the vmware application to "john" with chown, and so I did the command, and now I can access the vmware application from the applications menu, without it asking for my own password, but now  it constantly gripes about how I don't have permissions to access some of the files. The VM opens anyway, but still complains so I have to close about 15 little windows that say I may not access the file.

What is going on here? Not so much the vmware thing, but what is up with these permissions. I should log in as "john" and anything I have permission to do, I ought to be able to do without having to  sudo and  give my password all day long. Stuff that requires root permissions, is understandable, and it should be asking for the root password when I sudo, but instead, it always demands 'john's' password instead. (again, I  used that password to access the system in the first place. Why does it keep asking me for it?)

I have set up my system, and installed all kinds of things, set up applications, and edited system files, and it has never once asked for the 'root' password. This is not how I have ever seen linux use passwords, permissions, and accounts before.

I am tired of entering my own password every half hour while still configuring and setting up this machine. Very frustrated. Can someone shed some light? I am sure there is a good reason, and that I have misunderstood somethings. 

Help? 

Thanks a lot,

John

---

### Post by Pumalite on 2007-11-07
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mikewhatever on 2007-11-07
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Are you frustrated because you need to enter your own password and root's? What is the difference? Does it really take so long to configure your system? Why? Have you considered that Ubuntu does not have to be like other distros?

---

### Post by amingv on 2007-11-07
Hi,

I think I get what he means. Happened to me while surfing thru various Linux distros. In some distros, when you install, you define a root password AND an user account/password, so that they are not the same.

In Ubuntu it is not so, you define your first admin account and the root account assumes this password. But when you type sudo you are not using john's password, but the root's password/account. Furthermore, you can modify them if you want them to be different.**//<--This is not so, read the next post.**

---

### Post by llamakc on 2007-11-07
The root account DOES NOT assume the user password. The use of the user password with the 'sudo' command is a feature of the software package "sudo" which is used by default in Ubuntu.

Open a Terminal and type:

```

man sudo

```

and 

```

man sudoers

```

'sudo' allows the user in the /etc/sudoers file to perform whatever is defined in the /etc/sudoers file.

---

### Post by amingv on 2007-11-07
> The root account DOES NOT assume the user password. The use of the user password with the 'sudo' command is a feature of the software package "sudo" which is used by default in Ubuntu.


Ooops! I was quite misinformed then. Thank you for pointing that out.

---

### Post by llamakc on 2007-11-07
> **amingv said:**
> Ooops! I was quite misinformed then. Thank you for pointing that out.

It is a minor difference but one that is important when explaining to new folks. For example you can set the /etc/sudoers file so a particular user can execute a single (or a few) commands that normally need "root' privileges.

I think the install process should build in a page of 'info' about this myself. RedHat installs used to pepper the user with snippets as the install proceeded. SO MANY new users do not understand the security model of Ubuntu. Maybe I'll write a spec and propose it for HH.

---

### Post by NT4usB on 2007-11-07
> **singlewc said:**
> ...I am tired of entering my own password every half hour while still configuring and setting up this machine. Very frustrated. Can someone shed some light? I am sure there is a good reason, and that I have misunderstood somethings. 
John

I don't know the 'official' reason why it is this way. 
I see it as a convenient way to be able to quickly administer a machine while maintaining some security. In my Windows world at work, I administer workstations so my username has adm permissions. Also means, anyone can get at the network and do admin stuff from my workstation (if they get to it before the screen locks after ten minutes of inactivity)
I'd go nuts if I had to switch users every time I had to do administraty things.

It is annoying that sudo times out after five minutes and requires you to reenter the PW.
iirc, you can change the timeout time.
If you want to administer as your user without having to enter sudo, use the command```
sudo -i
``` and your PW. Now you can run commands that require sudo every time, without having to type sudo bla bla bla. Still gonna get hit with a PW but if you work fast, (or change the timeout) it shouldn't bug you much. Don't forget to```
exit
``` before doing anything that requires userlevel permissions.

---

### Post by Pumalite on 2007-11-07
Dangerous.

---

### Post by avik on 2007-11-07
Okay, let's say some virus got into your system and wanted to delete all your files (or like in the case of an actual Windows virus, encrypted all your files and demanded you pay the authors to unencrypt them).  Do you want all of this to happen without your knowledge?

Typing in a password, even your own, allows you to know what is going on with your system.  It's also a lot less automatic than pressing an "Allow" button.

Also, see this: [http://www.gnu.org/fun/jokes/evilmalware.html]("http://www.gnu.org/fun/jokes/evilmalware.html").

---

### Post by singlewc on 2007-11-08
Okay. I can't say I agree with the mindset, and I still don't understand the rationale, but I am working on just accepting it :-)

Here is the rub.

I installed vmware simply following the instructions, not really grasping all that I was doing, so I just did what it said, and did sudo 'john' when it was called for, and I ended up with an install that would only run, if I did 'sudo vmware' and gave john's password.

Running it from the applications menu, would fail because of permissions.

A friendly poster here told me to chown the vmware directory, and I did that, and I could get in from the menu, without sudo, but it gave me errors saying I didn't have permission to open certain files. No file names were given, just a dozen or so little error messages. I cannot access the virtual drive I set up, as it kicks me out as not having permission

So, I opened terminal, and did su root, gave the password, and whoami says I am root.

I try to run vmware from that terminal, no sudo, just vmware, and it opens to where I choose the virtual machine, and when I choose the only one I have made so far, it says no, I don't have permission to open that file.

I can't open it as john, I cannot open it as sudo john, and I cannot open it as root. It is marked as belonging to john.

Great :-) Those are the only two users on the machine, so do I have to blow it away, and start over completely? Make a new virtual machine, reinstall the Windows OS, and the apps that I have already set up in there?

Permissions? I could have sworn that root was allowed to do anything, with any file. No?

I can comprehend that some permissions are messed up, but vmware is installed and its files are in places I never heard of before, so is there a way to find out what files are coming up as 'off limits?' the log file simply repeats the 'either the virtual drive file or some associated files' mantra.

Much obliged for your patience. I am frustrated, but don't want to come across as too bitchy, so if it sounds that way, please forgive me. I intend to persevere, but its getting old already.

Thanks,

John

---

