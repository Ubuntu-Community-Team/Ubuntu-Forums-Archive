---
title: "Sudo/Synaptic/...confused"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Muzzle on 2006-05-19
I have spent a few hours reading FAQs, man pages, and these forums and have yet to see this covered.  I just installed BB and everything went great.  Now I want to use Synaptic to install current drivers for my video card, and I have run into a problem.  When I try to do anything, including Synaptic, that requires sudo to prompt me for the root password, I get the prompt, type the password.... and nothing happens.  Synaptic never runs, nothing ever happens past that.  I apologize if this is covered in some obvious place.

Thanks for your time.

---

### Post by Sef on 2006-05-19
> Now I want to use Synaptic to install current drivers for my video card, and I have run into a problem. When I try to do anything, including Synaptic, that requires sudo to prompt me for the root password, I get the prompt, type the password.... and nothing happens.

First, root is turned off by default.  Read the link below: 

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

Second, the password you use is your login password.

---

### Post by MiniJames on 2006-05-19
Check that your putting the systems *root* password (set during installation) into the prompt. This could be different from your user account password depending on how you decided to organise your passwords during installation of ubuntu. It also helps to make sure you enter it correctly :)

Thats the only offer of help I can suggest, meh im a new kid too :)

---

### Post by TheFourElements on 2006-05-19
type this:

```
gksudo synaptic
```

then type your main user password. It's that simple.

---

### Post by Muzzle on 2006-05-19
I appreciate the quick replies.  As for your answers:

Sef:  I have read it, thanks for the link, and I understand which password to use, but nothing happens upon typing it.

Minijames: Thanks for the reply, as I am the only user of this computer at present, my user password and the root password are the same for convenience, I understand this should probably not be, but at the moment it was the simplest thing to do during installation.  

TheFourElements: Thanks for the reply, I typed it, no error msgs, no program.  Nothing at all happens.

---

### Post by ductruffe on 2006-05-19
Hello,

I had a similar problem to this, and it also happened with just about everything in the administrator menu.

I fixed it by re-installing ubuntu from scratch.

Regards,
DucTruffe

---

### Post by manicka on 2006-05-19
[QUOTE=Muzzle] 
TheFourElements: Thanks for the reply, I typed it, no error msgs, no program.  Nothing at all happens.[/QUOTE]

do you get any error messages if you type the command  

```
sudo synaptic
```

 in a terminal?

---

### Post by steve.horsley on 2006-05-19
Did you do an expert install and define a root password during the install? I've never done this, but I gather from these forums that if you do so then the installer doesn't crate the sudo rights for the first non-root userlike the default does. In that case, you will have to do **su** and then launch synaptic from your root command shell. 

I hope I'm right - like I say, I've never done an expert install.
For reference, here is my /etc/sudoers file. And of course, I am a member of the **admin** group.

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL


---

### Post by Muzzle on 2006-05-19
Manicka: Nope, no error msgs at all.

Steve.horsley:  Actually, that is exactly what I did.  So, if I change my sudoers file I should be ok?

Edit:  I just tried using SU like you said and running from a terminal and it worked.  Thank you all very much for your help.  Obviously I would like for sudo to work for my user, so what do I need to do to make that happen?

---

### Post by ElijahLofgren on 2006-05-19
[QUOTE=Muzzle]
Sef:  I have read it, thanks for the link, and I understand which password to use, but nothing happens upon typing it.

TheFourElements: Thanks for the reply, I typed it, no error msgs, no program.  Nothing at all happens.[/QUOTE]
I know it's confusing, but when typing your password at the command line, *nothing* will show up, that's ok though, just type your password anyway and hit Enter. It should work then. ;)

---

### Post by Muzzle on 2006-05-19
ElijahLofgren:  I am not confused about that :-D   I did type it, I did hit enter, nothing happens, i.e. the program doesn't run, so no, it doesn't work.

Also, now that I can get synaptic to open just using su as Steve.Horsley suggested, I find that the only repository I have is my cdrom.  None of the ones shown in the wiki site for adding repositories are there.  Could someone toss me a link that shows what I should have and how to go about adding them?  The wiki site shows how to add new, but not the ones you should already have.

Thanks again for all the help!

---

### Post by Muzzle on 2006-05-19
Ok, I have managed to get all the repositories corrected, and it has downloaded 149 updates.  Of course, I still cannot see them or install them since sudo doesn't work. :rolleyes: 

Could someone please point me in the direction of information that will allow me to setup a user for sudo? 

It has been a long time since I installed linux, and had it running well, but I have to say, so far this has been the most infuriating install I have ever done ](*,)

---

### Post by ElijahLofgren on 2006-05-19
[QUOTE=Muzzle]Ok, I have managed to get all the repositories corrected, and it has downloaded 149 updates.  Of course, I still cannot see them or install them since sudo doesn't work. :rolleyes: 
[/QUOTE]
I remember having problems with sudo on Breezy Badger, but since I've upgraded to Dapper Drake I don't think I've had any sudo problems.
More info about Upgrading to Dapper Drake here:
[http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

[QUOTE=Muzzle]
Could someone please point me in the direction of information that will allow me to setup a user for sudo? 
[/QUOTE]
I think these may help you:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://help.ubuntu.com/starterguide/C/ch06.html](http://help.ubuntu.com/starterguide/C/ch06.html)

[QUOTE=Muzzle]
It has been a long time since I installed linux, and had it running well, but I have to say, so far this has been the most infuriating install I have ever done ](*,)[/QUOTE]
Sorry to hear that. I'm guessing that Ubuntu Dapper Drake will turn out better for you.

---

### Post by catlett on 2006-05-19
The easiest thing would be to add a new user. It should be set up like all Ubuntu users (i.e. with a sudo password)
Go back to the root sudo link [https://wiki.ubuntu.com/RootSudo#head-3f8a7e5ae5fe6b048ffecef0bf38c811eede7aec](https://wiki.ubuntu.com/RootSudo#head-3f8a7e5ae5fe6b048ffecef0bf38c811eede7aec)   
There is a section about adding a new user.
Disregard people who are telling you about sudo and your password not showing etc. You don't have a sudo password right now. Only a traditional Debian root password. You become root by typing su (switch user) and entering the root password.
Making a new user should solve your problems except that you will have to be that user.

If you don't understand the new user instructions, this is  from the unofficial ubuntu 5.04 guide. All the commands should be the same for 5.10 [http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

P.S. Just for your information. If you want a root shell when you get a new user and can only execute as root through sudo. Type sudo su to get a root shell.
Good luck. 

P.S.S If you still need a repository list [http://www.ubuntuforums.org/showthread.php?p=1033813#post1033813](http://www.ubuntuforums.org/showthread.php?p=1033813#post1033813)

---

