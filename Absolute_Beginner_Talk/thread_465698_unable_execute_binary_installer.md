---
title: "unable execute binary installer"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by thedarky on 2007-06-06
Howdy,

Absolute beginner with linux.
I would like to install realplayer plugin for firefox - my daily round needs a dose of BBC and ABC/PBS.

I got the linux installer from the official real site,
[http://www.real.com/linux/](http://www.real.com/linux/)
changed the permissions and fired up Terminal to run it. 
At first, bash reported unable to execute, so I got it to tell me what the file's name is, copied and pasted  the name to be sure, but still unable to execute.
Am I doing anything wrong here?
Should I look for another way to install the plugin?

Terminal output from the execute 

/home/me/Desktop/RealPlayer10GOLD.bin
bash: /home/me/Desktop/RealPlayer10GOLD.bin: cannot execute binary file

and filename check here


me@me:~/Desktop$ ls -la
total 5688
drwxr-xr-x  2 me me    4096 2007-06-06 10:26 .
drwxr-xr-x 23 me me    4096 2007-06-06 11:29 ..
-rwxr-xr-x  1 me me 5802563 2007-06-06 10:26 RealPlayer10GOLD.bin

thanks in advance for looking at my question.

---

### Post by yabbadabbadont on 2007-06-06
You probably need to use sudo when you run it.

sudo /home/me/Desktop/RealPlayer10GOLD.bin

---

### Post by thedarky on 2007-06-06
> **yabbadabbadont said:**
> You probably need to use sudo when you run it.

sudo /home/me/Desktop/RealPlayer10GOLD.bin

thanks for posting.

The output from that sudo command was

>  1: Syntax error: "(" unexpected

Does this mean that the command is invalid?
Does it refer to something in the binary itself?

I thought that since I'd enabled execute permission for the binary that I could run it from the user desktop.

A bit more confused now.
Any help would be appreciated.

---

### Post by yabbadabbadont on 2007-06-06
Try running it this way:
```
sudo /bin/bash /home/me/Desktop/RealPlayer10GOLD.bin
```

---

### Post by thedarky on 2007-06-06
> **yabbadabbadont said:**
> Try running it this way:
```
sudo /bin/bash /home/me/Desktop/RealPlayer10GOLD.bin
```

the output is back to unable to execute file:

> /home/me/Desktop/RealPlayer10GOLD.bin: /home/me/Desktop/RealPlayer10GOLD.bin: cannot execute binary file

So do you reckon we can say that the file is the problem, not ubuntu?

thanks so much for helping here

---

### Post by yabbadabbadont on 2007-06-06
Hmmmmm.  If you run "mount" in a terminal, what is the output?

---

### Post by thedarky on 2007-06-06
> **yabbadabbadont said:**
> Hmmmmm.  If you run "mount" in a terminal, what is the output?

Output is

> /dev/hda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-powerpc/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

I hope I'm not keeping you from productive work  - really appreciate it.

---

### Post by yabbadabbadont on 2007-06-06
Well, it isn't what I suspected.  :?

At this point I can only assume that there is a problem with the shell script that is embedded in that bin file.  (bin files are usually shell scripts with a compressed archive concatenated to the end of it)  I'm sorry I wasn't able to solve your issue tonight.  I'll check this thread again tomorrow and, if it hasn't been resolved yet, I'll download the bin file myself and see if I can figure out the problem.  (it's after midnight here and I need my beauty sleep.  :D)

---

### Post by thedarky on 2007-06-06
> I'll download the bin file myself and see if I can figure out the problem. (it's after midnight here and I need my beauty sleep. )

night night yabbadabbadont, sweet dreams.  Please don't fuss over this before important stuff - - time lasts for ever, as Hawking says, and I favour the slow and steady approach to all things.

My neighbour has a pooter with a Realplayer plugin, and I can keep up with my radio listening by taking wine with me until this gets ironed out :-)   thanks so much so far!

---

### Post by yabbadabbadont on 2007-06-06
It was a small download so I went ahead and grabbed it.  It isn't a shell script but an actual ELF binary.
```
/home/daffy/temp $ file RealPlayer10GOLD.bin 
RealPlayer10GOLD.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped

```
Making executable and then using sudo to run it directly (not the bash stuff I had you do) should have worked.  Since it didn't, either the program expects different versions of various libraries to be installed, or it is just buggy...

You might read through this: [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)
and see if it helps any.  It looks like it is intended for Dapper, but it might also work with Edgy/Feisty.  Good night.

---

### Post by Inxsible on 2007-06-06
You have to make the bin file executable.
cd to the folder where you have stored the bin file then
```
sudo chmod +x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin
```

That should do it.

Hope that helps !!

---

### Post by thedarky on 2007-06-06
Gooodnight,
I had read the official documentation and decided to  go this route as the most direct.
Now you've shown that it's probably a buggy install, and most importantly that I'm on the right track with using commands, I shall have a potter around with one of the other leads.

thanks for all that.

---

### Post by eentonig on 2007-06-06
Before installing anything on your linux/Ubuntu box, did you check if a version of the program (or an alternative) was available in the repositories for your distribution.

As long as this is the case, I would use Synaptic (GUI) or aptitude to install it. This way, at least your sure that:
1. The binary is compatible with you OS
2. You don't need to compile yourself
3. You're sure that the programs stays up to date automatically
4. Things won't break when you update your kernel.

Read the first link in my signature.

---

### Post by thedarky on 2007-06-06
> **Inxsible said:**
> You have to make the bin file executable.
cd to the folder where you have stored the bin file then
```
sudo chmod +x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin
```

That should do it.

Hope that helps !!

I did that originally, I thought.
The output from the ls command upthread for the file is:
```

-rwxr-xr-x 1 me me 5802563 2007-06-06 10:26 RealPlayer10GOLD.bin
```

Isn't that sufficient for running it from the desktop?
The output from your command confuses again
```

chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
```

and if I run the other one you gave, bash says no such file.

confused again.  Thanks for posting.

---

### Post by thedarky on 2007-06-06
> **eentonig said:**
> Before installing anything on your linux/Ubuntu box, did you check if a version of the program (or an alternative) was available in the repositories for your distribution.

Yes, I've read the introductory official documentation about installing and have installed a few other things without setback - for all the reasons you list below.

> As long as this is the case, I would use Synaptic (GUI) or aptitude to install it. This way, at least your sure that:
1. The binary is compatible with you OS
2. You don't need to compile yourself
3. You're sure that the programs stays up to date automatically
4. Things won't break when you update your kernel.

Read the first link in my signature.

I could even list the documentation and other unanswered threads for Realplayer here, but I opened the thread for a specific reason - - which is to try to get an application installed that has **not** got good support so far - and hopefully to gain a few elementary skills using the terminal at the same time.

thanks for posting.

---

### Post by jiminycricket on 2007-06-06
Hi


Here's a good command line guide since you're curious: [http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)

You need to put a "./" or "sh " in front of the binary file to run it.

Anyways, it seems that realplayer is not in the Feisty repositories, but you might still be able to download the .deb file from the repository and see if it runs, of course no guarantees:  [http://archive.canonical.com/ubuntu/pool/main/r/realplay/](http://archive.canonical.com/ubuntu/pool/main/r/realplay/)

---

### Post by thedarky on 2007-06-06
Howdy Jiminycricket,

thanks for the links.

Looks like I've learned a bit more about ubuntu not really being a universal platform wrt to Realplayer at least.  It seems that all install packages are i386 or 64 bit and ppc is unsupported.

I've learned a lot in this thread.
Mainly that even though I managed to get a ppc feisty up and working, it's still limited for some things.

Off now to the ppc forums to see what else I can find out.

thanks for all posts.  Goodbye.

---

### Post by Inxsible on 2007-06-06
> **thedarky said:**
> I did that originally, I thought.
The output from the ls command upthread for the file is:
```

-rwxr-xr-x 1 me me 5802563 2007-06-06 10:26 RealPlayer10GOLD.bin
```

Isn't that sufficient for running it from the desktop?
The output from your command confuses again
```

chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
```

and if I run the other one you gave, bash says no such file.

confused again.  Thanks for posting.

are you sure you cd'ed into the directory where you have the bin file ?

---

### Post by yabbadabbadont on 2007-06-06
> **thedarky said:**
> Off now to the ppc forums to see what else I can find out.

PPC......  are you sure that you downloaded the correct binary for your architecture and not the x86 one?

---

### Post by AngryMallard on 2007-06-06
Perhaps using chmod to modify the .bin would work.

---

### Post by cowbuntu on 2007-06-18
RealPlayer10 needs libstdc++5 to work. I've never heard of the BIN file not installing but you might want to check if libstdc++5 is installed and if not, do a 

sudo apt-get install libstdc++5 and see if that helps. 

You might also want to try out the latest builds of RealPlayer downloadable from

[http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current).

Please note that the current branch is under active development and these builds should be used for testing purposes only. Having said that, i use the current branch builds regularly and they are very stable at the moment.

---

