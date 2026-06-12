---
title: "no permision is frustrating"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by sallam on 2006-01-26
Though I'm the one who installed ubuntu on my own computer, of which I'm the one and only user, ubuntu refuses to give me permission to do just about anything!
Does anyone have a solution for this, other than typing in the terminal everytime I want to do something? How can I convince ubuntu that I'm the owner and that no one else ever uses my box?

For example, how can I delete a folder? I failed to delete some folders that I've wrongly created in /media folder..

---

### Post by ivrobi on 2006-01-26
Hi!

Some commands are executable only by Superuser (root). So type

**sudo <*command*>**

The syste will ask for a password, give your user password there.

---

### Post by frodon on 2006-01-26
In the root space (your ubuntu partition except youir /home) you need to use [sudo]("https://wiki.ubuntu.com/RootSudo?") for everything.

---

### Post by sallam on 2006-01-26
how comforting to know. so what is the command to type to delete a folder?
is there a page that lists all commands that we'll have to type for the rest of our lives then?

---

### Post by Jucato on 2006-01-26
Well, you can't convince Ubuntu that you are it's owner, basically because you really aren't. /root is the owner. the link that frodon gave best explains this stuff, and why Ubuntu is different from other distributions in this regard.

But you should also keep in mind how Linux itself is different from Windows in this sense. XP doesn't care about this kind of stuff. It automatically presumes that the 1st user created during installation is the Administrator. Tough somewhat convenient for new users, it compromises security for ease of use.

---

### Post by frodon on 2006-01-26
sallam, if you don't like command lines you can run your file browser as root, i give you the command line to do it for gnome : ```
gksudo nautilus
```

---

### Post by Jucato on 2006-01-26
Just don't forget to close it when you're done doing root tasks. otherwise everything you do in it will be as root, and not as your own user.

---

### Post by bulldogzerofive on 2006-01-26
By the way, sallam, after having read your post about deep freeze:

It is not true that you are the only user on your system.  **Once you connect to the internet you are no longer the only person with access to your computer**.  Permissions are a vital aspect to keeping your computer safe.

This is why:  _any program you start as a user has the permission to do the same thing as the user who started that program_.  Now, the obvious problem here is malware:  If you download something from the net and open it without knowing what it is or does (something people do very frequently), it could be a virus.  If you are logged in as the superuser ("root"), then that virus will be able to do whatever it wants.  If, however, you are running as another user, that virus will not be able to damage your operating system or infect your programs because the user does not have permission to change system files.

Let's look at this from another angle.  Let's say you are running Firefox.  Now, let's say that firefox has a security flaw that allows websites to execute malicious code on through Firefox (like the recent .wmf fiasco for Internet Explorer).  IF you are running as a normal user, the malicious code that is executed through Firefox will only be able to access things that the original user has access to.  On the other hand, if you are running Firefox as the superuser ("root"), that malicious code will be able to do anything, including infect your entire operating system with malware.

If you look at windows, you will find that it also has the ability to seperate between "superuser" and "user".  This option is simply not enabled by default, for a variety of reasons.  However, if you are trying to deploy windows in a secure environment, enabling that is the first thing you do; it is the only way to protect a system from infection.  The office where I work has windows deployed in a secure environment.  The normal users can not install anything or change certain folders, and even the IT guys have to use the "run as a different user" option to do many things.  That keeps the computers safe.


You described deep freeze as very useful software.  It is, in fact, not that useful; it is only useful if you run an insecure system.  If you run a secure system, things like that appear to be a horrible waste of resources and very difficult on your harddisk.

Good Luck and contact the forums if you need any help!

---

### Post by Jucato on 2006-01-26
It's true that Windows XP does have it's own adminitrator/user distinction. Unfortunately, it doesn't make this option/feature quite known, so that regular users are left to act as administrator, unless someone sets up the installation for them.

This is clearly one thing that makes Linux stands out. And one word of advice: even the most secure system is not secure from the worst kind of attack: ignorance. You yourself can be the source of your own doom. Bottom line, don't do anything as root that you are not at least 90% sure of, and that includes upgrading to unsupported latest versions. Take it from me. I know what it feels to reinstall my system 2 times (make that 3 tomorrow) because of recklessness. :(

---

### Post by sallam on 2006-01-26
thanks everyone, but whats the command to type in terminal to delete a folder, or rename it? and is there a page that lists such commands for reference please?

---

### Post by Madpilot on 2006-01-26
sallam, have a look at [https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands) for an introduction to the Linux command line.

Deleting, moving & copying folders & files are covered there (among other things).

---

### Post by mrwrath on 2006-01-26
you need to go to your comand line and type

man rm

this is your remove command...but there are flags that go along with this so read carefully...you might even have to use the sudo command which will look like:

su rm [-option] [file]

which it will then ask for your password...

---

### Post by mrwrath on 2006-01-26
sorry about that mad pilot...

---

### Post by Lord Illidan on 2006-01-26
[quote=mrwrath]you need to go to your comand line and type

man rm

this is your remove command...but there are flags that go along with this so read carefully...you might even have to use the sudo command which will look like:

su rm [-option] [file]

which it will then ask for your password...[/quote]

Be extremely carefull when using sudo rm.

NEVER USE ```
sudo rm *
```

The asterix is a wildcard... ie.. if you do this : ```
sudo rm *.mp3
```, every mp3 file will be deleted. If you do this: ```
sudo rm * .mp3
``` (a space between * and mp3), EVERYTHING will be deleted. Be extremely careful.

---

### Post by Iowan on 2006-01-26
Perhaps it bears mentioning that if you **rm** stuff from the command line, there's no trash to sift through to get it back... it's gone.  "_Be extremely careful_"

---

### Post by mrwrath on 2006-01-26
I do need to watch what info I give...at least give the warnings that should go with it. Listen to these guys/girls...I was just trying to lead you in the direction to research.

Noob out.

---

