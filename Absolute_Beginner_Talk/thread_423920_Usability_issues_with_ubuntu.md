---
title: "Usability issues with ubuntu"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-04-26
Hi folks,

I've been using Ubuntu for some days and this sudo authentication thingy is driving me nuts. 
I can't seem to perform any root level operations using the UI and need to put "sudo" and enter the password after every command. 

This is a bad bad usability issue. Is there any way to turn this off and run the system in the normal root mode.

---

### Post by Seisen on 2007-04-26
You can but I don't advise you too. It makes it way to easy to hose your whole system.

---

### Post by Zuph on 2007-04-26
There is a reason that Ubuntu is built like this.  It protects you from doing stupid things to your whole system without realizing it.  It's a different paradigm from Windows, and something that you need to get used to.

Or you could circumvent it and increase the risk of doorstopping your box.

---

### Post by Joseaa on 2007-04-26
Well, it might be a security measure and making this settings default might make sense. 

However, if you want to run directly from the root there should be an option available. Especially for the ones who are ready to live with the blunders that they've made with the system.

---

### Post by Seisen on 2007-04-26
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME")

There's you answer on how to do it.

---

### Post by igknighted on 2007-04-26
> **Joseaa said:**
> Well, it might be a security measure and making this settings default might make sense. 

However, if you want to run directly from the root there should be an option available. Especially for the ones who are ready to live with the blunders that they've made with the system.

Trust me, you do not want to do it.  And yes, most distro's make it allowable.  And yes, the "sudo" method Ubuntu employs is unorthodox by linux standards (personally I am not a fan, prefer true root, but I see the merits and respect why they do it).  That said, I have only logged in as root about 3 times in about a year and half of linux.  Many times launched as root from the terminal, but very very rarely have I logged in as root.  It is a good way to get hacked or just break something.

In order to be able to open a program as root, edit its launcher to have "gksudo" in front of the command.  This way you enter your password and get root privileges when you run it.  I have a "root file manager" entry in my menu, so when i launch it I can use the file manager and edit text files as root.  I still leave my normal one for most cases, and do very little, almost nothing as root.  But for those times, it is nice.

---

### Post by orb9220 on 2007-04-26
> However, if you want to run directly from the root there should be an option available. Especially for the ones who are ready to live with the blunders that they've made with the system.
Reply With Quote

I created a launcher on my panel that runs a gksudo nautilus so I can copy,move,edit,etc.. files.
Enter password on launch then have sudo in nautilus until I close it.

But as other's here stated you can hose your system if you make a mistake.

---

### Post by Joseaa on 2007-04-26
> **igknighted said:**
>  It is a good way to get hacked or just break something.

Can some one shed some light one this  ? How does the system get hacked if loged in as a root user. 

I guess, half of the frustration will be solved if the file manager can be launched using root privileges. 

I am new to linux and I don't understand the paradigm clearly but still i have no doubt in my mind to believe that this root authentication is a bad bad usability thing. This is clearly not helping Ubuntu (or as a matter of fact linux) to reach out and establish itself as an OS for ordinary human beings. It would be great if the people involved in this project could work their brains and come up with something out of the box. Something more simple and usable instead of typing the sudo password all the time. ( yes I know, it doesn't get anymore abstract than this :P )

---

### Post by igknighted on 2007-04-26
> **Joseaa said:**
> Can some one shed some light one this  ? How does the system get hacked if loged in as a root user. 

I guess, half of the frustration will be solved if the file manager can be launched using root privileges. 

I am new to linux and I don't understand the paradigm clearly but still i have no doubt in my mind to believe that this root authentication is a bad bad usability thing. This is clearly not helping Ubuntu (or as a matter of fact linux) to reach out and establish itself as an OS for ordinary human beings. It would be great if the people involved in this project could work their brains and come up with something out of the box. Something more simple and usable instead of typing the sudo password all the time. ( yes I know, it doesn't get anymore abstract than this :P )

Linux, like every OS, has various security holes.  Most in linux are at the application level, which only give access to intruders taking advantage of the hole at the level the application is running at.  Therefor if a firefox hole gets exploited and your are you user, you could have personal data comprimised in you home folder, but your system is safe.  Same with any form of virus/malware.  It spreads like wildfire in windows BECAUSE you run as admin, and it has access to the entire system.

Linux will never change from a permissions system.  It's a feature, plain and simple.  There are other distro's (and this could be done in Ubuntu with nautilus scripts and such) that let you right click -> run as root or edit as root.  This is nice usability, and I think things are moving there, but Ubuntu doesn't have much in this category yet.  I think Suse does if you want to check it out.  It uses a true root account as well, not sudo.

---

### Post by dstew on 2007-04-26
You can increase the time that sudo leaves you logged in as root by editing the **timestamp_timeout** variable in the **sudoers** file. See **man sudoers**.

---

### Post by aysiu on 2007-04-26
Read this.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It's got everything--why Ubuntu uses *sudo*, the pros and cons of each security model, how to enable a regular root login, etc.

---

### Post by Iokua on 2007-04-26
I was a little annoyed by this at first too, but I quickly saw the value of it once I realized that most Linux commands don't double-check with you to see if you're doing the right thing. In other words, there are very few dialogs that say, "Are you sure you want to do this?"

To keep from getting frustrated with it, I just use a script for nautilus that allows me to right-click a file and select "Edit as root" This is great for modifying config files. It's available through [Automatix]("http://www.getautomatix.com/") if you're interested. It's listed under "Nautilus Scripts" or something like that.

---

### Post by Austin_KW on 2007-04-26
If you know you are going to be doing a sequence of command use the "sudo -i" option to get an interactive root terminal. You enter the password once and dont need to use 'sudo' again.
Use ctrl-D to end the login

If you are going to issue commands that need a gui, then first allow root to use you display 
xhost +local:root
sudo -i
*From here on all commands are issued as root*
gedit&     #eg. run gedit as root, the '&' backgrounds the command so you can continue to use the shell
...
Ctrl+D to exit

---

### Post by unnes on 2007-04-26
As someone who uses both Ubuntu and Vista regularly, I much prefer sudoing certain terminal commands than having to dismiss a dozen UAC popups in Vista :)

---

### Post by st33med on 2007-04-26
Yeah, it is more secure. On top of that, Linux is Open-Source, unlike the honorable Mac and the honorably discharged Windows :), which means people can go in, help fix a bug or security hole much quicker than a team of one. I think that most companies see this as a really bad way to make an OS because hackers and mischievous users can find holes much quicker, when, in reality, it takes a person very long to find a hole in thousands of lines of text, not to mention it would be short lived because of the community. Windows, however, can be exposed my supplying a program and having the user open it and it takes over the system without trouble. Linux requires a password to continue, so, if the virus is just automated, it cannot go any further.

Linux is secure like that, Windows is trash like that :).

---

### Post by Joseaa on 2007-04-27
> **Iokua said:**
> I was a little annoyed by this at first too, but I quickly saw the value of it once I realized that most Linux commands don't double-check with you to see if you're doing the right thing. In other words, there are very few dialogs that say, "Are you sure you want to do this?"

Clicking yes/no may not be the best alternative to deal with such problems but it certainly is the easiest rather than entering password all the time.

---

### Post by Tomosaur on 2007-04-27
It's not a bad usability issue, because you shouldn't be doing it very often. Administrative tasks are not 'everyday' things - you're supposed to get your system how you like it, then use administrative stuff to fix problems if and when they arise. 

Adding / removing new software is surely something worthy of putting in a password?

In any case, for a little history -
Linux was designed (since it's inception) with networking in mind. There is a heavy focus on users, groups, permissions etc. This encourages a system whereby the most common users have the least permissions, and are thus less capable of causing trouble. Ubuntu recognises that for a desktop system, that particular approach is a bit frustrating, so sudo is a way of making sure you don't break your system doing something stupid, but, and this is crucial, **you can if you really want to**. I would strongly advise against it, but you can easily enable the root account, by performing the following command:

```

sudo passwd root

```

This will prompt you to create a password for the root user (after you input your own password of course, prompted by the 'sudo' command). Once it's all confirmed, you can log in and use the root account as you would any normal user.

HOWEVER - it is a very bad idea. Things running as root have control over the entire system. Particularly if you're new to Linux, this is a recipe for disaster, but even experienced users prefer to use root as little as possible. For a sense of how bad running as root all the time is - just look at Windows, and how infected with malware, viruses etc it is. This has been allowed to happen because the default Windows setup gives you control over the entire system, and most people don't even realise it. This makes the job of a virus writer much, much easier. They don't need to look for vulnerabilities in the code of the operating system, they just have to trick you, the user, into installing their virus (a phenomenally easy task, by the way).

In short - if everyone ran Linux as root, you can pretty much bet that we'd have the same situation as Windows eventually. Aside from hosing your own system, enforcing the idea that root is bad, ensures that the rest of us can continue using our systems without having to worry about nasty viruses. 

So anyway, if typing your password annoys you, then there are a few things you can do:
1) Don't perform tasks which require your password. You should really just set your machine up how you like it in one big 'tweak-fest', then you won't have to worry about doing it in the future.

2) Extend the amount of time you stay logged in as root, after typing your password (see the post above this).

3) Log in as root. **Once again, everyone here will recommend against you doing this. You can easily break your own system, but a free-for-all also encourages viruses and such, which can spread to other machines, and then we'll all be back to square one**.

If you need an idea of just how beneficial the 'sudo' idea is - Microsoft have just copied it and stuck it in Vista.

---

### Post by seshomaru samma on 2007-04-27
> **Joseaa said:**
>  

I guess, half of the frustration will be solved if the file manager can be launched using root privileges. 



you can run the file manager as root with this command :
```
gksudo nautilus
```

---

### Post by Tomosaur on 2007-04-27
> **seshomaru samma said:**
> you can run the file manager as root with this command :
```
gksudo nautilus
```

Also, there are scripts and extensions available for nautilus to open files as root, launch programs as root etc. A quick google search should help you out, or you can write your own fairly easily. You can also download nautilus-script-manager which is a command line tool to manage your nautilus scripts.

---

### Post by diskotek on 2007-04-27
if you are a newbie & like to dig your system SUDO saves life..at least it saved mine many times :)
note: i learnt many things about xorg :( haha

---

### Post by Peti29 on 2007-04-27
> **igknighted said:**
> There are other distro's (and this could be done in Ubuntu with nautilus scripts and such) that let you right click -> run as root or edit as root.  This is nice usability, and I think things are moving there, but Ubuntu doesn't have much in this category yet.

Something like this would make life much easyer. This has happened many times that I wanted to move/rename/edit a file in Nautilus and I couldn't. It'd be nice that in such a case an 'Enter password' dialog showed up for me to deal with the problem right there.

---

