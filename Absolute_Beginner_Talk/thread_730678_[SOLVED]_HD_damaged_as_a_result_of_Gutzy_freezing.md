---
title: "[SOLVED] HD damaged as a result of Gutzy freezing?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-21
hello

my laptop lately went through a number of "rough" shutdowns. This was due to Ubuntu Gutsy constantly freezing, the fact that the so-called "magic keys" didn't work when it froze (someone suggested that they're useless if there's an issue with kernel), and the fact that all I could do is to press the power button. 

After re-installing Gutsy, it froze only once in the past week, so it looks like things are improving. I was wondering, though, if I could make sure my hard disk didn't suffer in any way from all those forced shutdowns. Is there something I can do to check its integrity? The laptop is new, and I'd rather find out now if there's something wrong. 

Thanks.

---

### Post by billgoldberg on 2008-03-21
The chances the hard drive will be damaged are extremely small.

The chances that the file system comes corrupted are a bit higher. But to be perfectly honest, I've done allot of forced shutdowns and I never have any problems.

Gutsy will check your harddrive every 30th time you boot up the pc or something like that.

But it's strange that gutsy crashes that much (even at all, I haven't had a crash in ages). What programs is crashing and is takin gutsy down with it?

Have you asked about the problem in the forums yet?

---

### Post by jan quark on 2008-03-21
you can find disc info with

```
sudo fdisk -l
```

for further info run
```

man fsck
```

in terminal. fsck is the utility which checks your drive for errors

---

### Post by Herman on 2008-03-21
Shutting down your computer with the big power switch is no good for your file system, I'm not sure about the hard disk but I suppose it wouldn't do it a lot of good either.

If your operating system seems to be frozen on you it could be just your mouse or your keyboard. If your mouse or keyboard stops working on you, try unplugging them at the usb or ps/2 port  and wait a second, then plug them back in again. Often that does the trick.

If it's just one process that has caused your computer to freeze up you can sometimes use the top command to find and kill that specific process.[LIST=1]
[*] Press alt+ctrl+F1 for a console.
[*]Log in with your username and password as prompted.
[*]Use your 'top' command and then take a look at your 'top' output for the PID number of the offending process.
[*] Press 'k'
[*]Type the PID number of the process you want to kill.
[*]You will be asked if you want to kill PID 'xxxxx' with signal [15], type 'y', and press 'enter'.
[*]If a signal 15 doesn't work, use signal 9 only if you have to, it is more rough and forceful.
[*]Press 'q' quit the top program
[*]type 'exit' to exit the console
[*] Press alt+ctrl+F7 to return to GUI.[/LIST]**Another way: **(from the command line)
To 'background' a process: Press 'Ctrl' + 'Z' keys.
To 'foreground' the process: press 'f' and then 'g' keys.
To see what jobs are running: use the 'ps' command (type: ps for a list of jobs, including their job numbers.
To kill a process: type: kill <job number>               


If none of the above is any help and your desktop or mouse is still frozen but your keyboard still works you may be able to switch to a 'tty' by pressing 'ctrl'+'alt'+'F1' (or any 'F' key from 1 to 6. 
That takes you to a black screen where you can log in at the prompt with you username and password. (Pressing 'F7' returns you to your Desktop again).
Log in at the prompt and then issue the following command, `sudo shutdown -h -t 0 now'```
sudo shutdown -h -t 0 now
```or, 'sudo reboot -i'```
sudo reboot -i
```If the frozen computer is an SSH server might use another computer on the network to log in to the computer with the problem and shut it down remotely. Just SSH into it and use the same commands just described above. 

Another way to shut down a frozen computer, ir the 'Raising Skinney Elephants' keyboard sequence. Read this great link from 'Tips For Linux Explorers' links:[CENTER][Skinny Elephants ( if all else fails )]("http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html")

[LEFT]If the keyboard and mouse are both frozen and you have no other computer to SSH from, sometimes you have no choice but to use the big OFF switch. If you do, be sure to run a file system check right away as soon as you can. The best thing to do before booting your operating system again is to boot a live CD, like [GParted -- LiveCD]("http://gparted.sourceforge.net/") first and run a file system check from the live CD.

If you are having your computer freeze up very often, it means there is something wrong and you should try to fix it. Usually it is drivers that cause systems to freeze up. Maybe it will help if you run sudo dpkg-reconfigure xserver-xorg (refresh video, keyboard & mouse drivers, and settings), see this page for details, [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html") . 
Or maybe an update will fix it especially if you are running a pre-release test version. (It is not recommended for new users to run pre-release test versions of Ubuntu).

Regards, Herman :)
[/LEFT]
               [/CENTER]

---

### Post by BoA CoNsTrIcToR on 2008-03-27
I faced this problem in my old PC. Gutsy would freeze every time I connected to the Internet and began downloading a file.

I surmised that the problem was my old hardware and downgraded to dapper. I installed Gutsy in my new laptop and everythign so far works fine (at least in regards to Gutsy freeing)

---

