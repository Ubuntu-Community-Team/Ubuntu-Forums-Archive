---
title: "sudo: command not found"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by intovoid on 2006-12-25
I was trying to install the new JRE & JDK on kubuntu with the following guidelines: [http://doc.gwos.org/index.php/Custom_JAVA]("http://doc.gwos.org/index.php/Custom_JAVA").

And somewhere before or after, i'm not sure, "sudo rm ./java sudo rm ./java_vm sudo rm ./javaws" command, sudo stopped working.

Whenever i type sudo in a konsole session i get the following message: "bash: sudo: command not found".

Anyone in a xmas mood to help me out here.

---

### Post by xyz on 2006-12-25
It's xmas everyday here!!
To find out/learn about : [Root Sudo]("https://help.ubuntu.com/community/RootSudo")
Typing only "sudo" will not be of much help. It gives you option-related sudo command lines:
> th@luser:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

Also in a console:
```
man sudo
```

---

### Post by intovoid on 2006-12-25
Thanks for trying to help, but even after reading it i really don't know what to do.

It seems as if my path is messed up somehow. SUDO can't be found, SU can't be found, i can't seem to start ADEPT because of not finding the SU command, i'm really stuck.

Help ...

---

### Post by wildkarde on 2006-12-25
try typing this on the console.

which sudo

echo $PATH

---

### Post by intovoid on 2006-12-25
echo $PATH gives me:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

could it be i removed a symbolic link to sudo or something with these commands:

```

cd /usr/bin
sudo rm ./java sudo rm ./java_vm sudo rm ./javaws

```

i copy pasted the last command before i saw it actually are 3 commands, maybe executing that command did something wrong.

If so, how do i correct it?

---

### Post by wildkarde on 2006-12-25
what did the other command do?

$ which sudo 

( no dollar sign when running it )

---

### Post by po0f on 2006-12-25
intovoid,

The command you posted deleted sudo.  I don't know if this is recoverable or not.  For the record, the command probably should have been:
```
[FONT="Courier New"]$ sudo rm ./java && sudo rm ./java_vm && sudo rm ./javaws[/FONT]
```
What you did is delete /usr/bin/java, /usr/bin/sudo, /usr/bin/rm, /usr/bin/java_vm, /usr/bin/sudo, /usr/bin/rm, /usr/bin/javaws.

---

### Post by wildkarde on 2006-12-25
Wouldn't he be able to recover by installing it again after booting into single user mode?

---

### Post by po0f on 2006-12-25
wildkarde,

Yeah I guess that should work.  Sorry wasn't really thinking straight.  (I'm more worried about Christmas than anything right now.  BTW, Merry Christmas all.  :))

---

### Post by intovoid on 2006-12-25
> **wildkarde said:**
> what did the other command do?

$ which sudo 

( no dollar sign when running it )

Did nothing, no error, no output.

---

### Post by intovoid on 2006-12-25
> **wildkarde said:**
> Wouldn't he be able to recover by installing it again after booting into single user mode?

Would someone be so kind to explain how to do this, please?

Thanks in advance.

---

### Post by wildkarde on 2006-12-25
> **intovoid said:**
> Would someone be so kind to explain how to do this, please?

Thanks in advance.

Sure.  You will need to reboot your computer.  As the computer starts to come back up, you will see grub.  This will be a black screen that will show the operating systems you have installed.  Here, you can select the particular OS you want to boot.  If ubuntu is the only OS you may not see the menu and may need to hit the escape key.  If this is not the case, please disregard.

First line may say something like the kernel name and the version, then underneath it will say the same thing but will include the line 'safe mode' or 'single user mode', something along those lines.  

Select the second option and after it boots, you will be in a console as root.
Here, you want to run:

aptitude install sudo

You may want to test it works before rebooting by running sudo without any arguments.
After making sure everything works, you can reboot and you should be fine.

---

### Post by MrKlean on 2006-12-25
If your using Edgy.. boot from the cd..there's a repair installation option there.. that might do the trick ; ) Not sure if Badgy has it or not..but it might ; )

---

### Post by intovoid on 2006-12-26
> **wildkarde said:**
> 
aptitude install sudo

I made it "aptitude reinstall sudo" and it worked, thank you very much ... :KS

---

### Post by nichipet on 2007-07-22
**removed by poster**

---

