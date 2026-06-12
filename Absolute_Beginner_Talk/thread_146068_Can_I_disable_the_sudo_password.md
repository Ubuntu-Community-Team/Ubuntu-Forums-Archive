---
title: "Can I disable the sudo password?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by p.n on 2006-03-17
I need to run an unattended task that requires sudo.  I do not want to enter the password every 15 minutes.  Is there a way to disable the password at all?

Regards
p.n

---

### Post by mlind on 2006-03-17
You shouldn't be running tasks that require root permissions for every 15 minutes.
Sudo (session) remembers password for like 5mins. Are you migrating from windows
to linux?

Could you tell what kind of root activities you need to execute so frequently?

/etc/sudoers (edit with visudo -command) may help if you need to run command
as a root without a password. There's NOPASSWD attribute that you should check.

---

### Post by p.n on 2006-03-17
Widows?  No haven't been running Windows for years.  Have been with Gentoo for some years and am trying Ubuntu out.

Why I need it?  I have a dialup which runs from my gateway.  I need to start the dialup from my other PCs.  I used to have a script using sudo and attended ssh that did this for me, but for the life of me I cannot remember how I got it not to prompt me for a password everytime...

---

### Post by mlind on 2006-03-17
lol, sorry about that :mrgreen: 

how about that /etc/sudoers ?
try running *sudo visudo* and insert this as the last line on that file

username ALL=NOPASSWD: /path/to/your_own_script

and fill in the username and path to your script.

before trying the sudo, remember to clear the previous sudo session with *sudo -k*

---

### Post by aysiu on 2006-03-17
You don't need to re-enter your password every fifteen minutes if the task takes longer--trust me.

I've done *sudo apt-get install _______* and *sudo apt-get dist-upgrade* commands that have lasted hours to complete, and I was prompted only once for my password.

---

### Post by pbaehr on 2006-03-17
Those took hours to complete but p.n is starting a script every 15 minutes so after 15 minutes the sudo password has be reinstated and it prompts for it again.

---

### Post by ubuntuuser on 2006-03-17
[QUOTE=aysiu]You don't need to re-enter your password every fifteen minutes if the task takes longer--trust me.

I've done *sudo apt-get install _______* and *sudo apt-get dist-upgrade* commands that have lasted hours to complete, and I was prompted only once for my password.[/QUOTE]
Exactly. Once the process is running it has root privileges and will not ask you for a password. I also have written a little SSH script on my computer to create some tunnels to my university server, and because I didn't want to enter the sudo passwd for this, I adapted the sudoers file as follows: ```
username ALL=PASSWD: ALL; NOPASSWD: /usr/bin/ssh
```
This way, I am still asked for my password except for ssh.

---

### Post by aysiu on 2006-03-17
[QUOTE=pbaehr]Those took hours to complete but p.n is starting a script every 15 minutes so after 15 minutes the sudo password has be reinstated and it prompts for it again.[/QUOTE] So chmod the script to be executable by the user in addition to/instead of root.

---

### Post by Jucato on 2006-03-17
sudo will not ask you for the password again if the process that is running with sudo privileges is still running. So if he started the process with sudo and kept it running in the background, it won't need to be sudo'ed again unless the process stopped and restarted.

---

### Post by Burgresso on 2006-03-18
I've been studying this thread for while, been toying around with (sudo visudo) sudoers and need some help.

I'm trying to configure it so that I can run these commands:
/usr/sbin/apache2ctl start
/usr/sbin/apache2ctl stop
/usr/sbin/apache2ctl restart
without sudo because I am trying to set up launcher buttons to run these commands. I've tried a lot of things - mostly variations on

> username ALL=NOPASSWD: /path/to/your_own_script

and

> username ALL=PASSWD: ALL; NOPASSWD: /usr/bin/ssh

Okay - I've replaced my username with "username" and tried things like replacing "/usr/sbin/apache2ctl start" for "/usr/bin/ssh".

What *should* work, or what are somethings that I may be doing wrong?

Regards and thanks,
burgresso

---

### Post by p.n on 2006-03-18
I understand that once a process runs it has root privilages but that is not the problem.  I wan to start and stop my dial-up whenever I feel like it and then it is anoying to always enter a password.  Hence my desire to somehow get around this.

---

### Post by p.n on 2006-03-18
[QUOTE=aysiu]So chmod the script to be executable by the user in addition to/instead of root.[/QUOTE]

It is owned by the user.

---

### Post by ubuntuuser on 2006-03-18
It doesn't matter if the script is owned by the user, if a process started from inside the script needs root privileges, it will still ask for the password. Try the line I gave you in my last post, it should work. You can then call ```
sudo *processname*
``` from your script without entering the password. Just be sure that you enter the name of the program that needs root access behind the NOPASSWD parameter. If you enter the script name, it will only work if you run ```
sudo *scriptname*
``` but in most cases it's not desirable to have the whole script run as root.
--------------------
[QUOTE=Burgresso]I'm trying to configure it so that I can run these commands:
/usr/sbin/apache2ctl start
/usr/sbin/apache2ctl stop
/usr/sbin/apache2ctl restart
without sudo because I am trying to set up launcher buttons to run these commands.[/QUOTE]

You will still need to use sudo, the NOPASSWD tag will only stop sudo from asking for your password. You can use sudo inside a launcher, just make sure to check the "Run inside terminal" box (<- be creative with the name, I don't use English ubuntu :-)).

---

### Post by Jucato on 2006-03-18
I'm not familiar with programming or scripting in Linux, but a thought kind of popped in my head.

Is it possible to make a script or short program that will run (as root) in the background which can start/stop the dial up depending on a command that you give it, something like the processes or daemons running in the system? That way, the program/daemon/process/script need only be run once (as root), left in the background, and is called whenever you feel like starting/stopping the dial up. Again that's just an idea that I suddenly had. But not knowing about programming/scripting, I don't know if something like that is actually possible or even advisable. (or maybe there's actually a program that already does that?)

---

### Post by chuckyp on 2006-03-18
Yes its possible and you can look at the skeleton file in /etc/init.d/skeleton I beleive or in the rc.d directory for an example.  You would use update-rc.d to do it.  

Also the proper way to do what you are trying would mostlikey be to create a user specifically for that script with the necessary priveledges for security reasons.  The user wouldnt' need shell etc...  They just need the ability to execute whatever commands are in that script.  And I would block them out of remote login shell access and everything.  

Hopefully you understand.

---

### Post by Jucato on 2006-03-18
[QUOTE=chuckyp]Hopefully you understand.[/QUOTE]
I don't, but I hope the thread starter does. :D
(I'm just not good with programming... yet)

---

### Post by mlind on 2006-03-18
[QUOTE=Burgresso]
Okay - I've replaced my username with "username" and tried things like replacing "/usr/sbin/apache2ctl start" for "/usr/bin/ssh".

What *should* work, or what are somethings that I may be doing wrong?

Regards and thanks,
burgresso[/QUOTE]


NOPASSWORD entries must be the last ones on sudoers file, otherwise they could
be overriden by other entires.

you still have to call your script with sudo, no password is prompted tho.
first *sudo -k* to kill possibly existing sudo session, then *sudo yourscipt*.
It should work.

If you're trying to run application this way that needs to draw something on X,
then you have to use xauth or xhost to allow the root use the same X.

---

### Post by p.n on 2006-03-18
OK, so now I have stuffed up my sudoers file:

```
 >>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19

```

I can't do anything with sudo now.  Please help.

p.n

ps, I really miss root...

---

### Post by cwaldbieser on 2006-03-18
[QUOTE=p.n]OK, so now I have stuffed up my sudoers file:

```
 >>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19

```

I can't do anything with sudo now.  Please help.

p.n

ps, I really miss root...[/QUOTE]
You can reboot into recovery mode and visudo to correct your mistake.

---

### Post by p.n on 2006-03-18
[QUOTE=cwaldbieser]You can reboot into recovery mode and visudo to correct your mistake.[/QUOTE]

Thanks that sorted that out but obviously leaves met with the problem that this:
```
 username ALL=PASSWD: ALL; NOPASSWD: /usr/bin/ssh
``` does not work.

I'll try to read up a bit on sudo.  man does not say too much.

p.n

---

### Post by mlind on 2006-03-18
you must use visudo to edit sudoers file. If you don't like the default vi editor, do
```

EDITOR=nano sudo visudo

```

did you try

```

p.n  ALL=NOPASSWD:/usr/bin/ssh

```

?

---

### Post by p.n on 2006-03-19
[QUOTE=mlind]you must use visudo to edit sudoers file. If you don't like the default vi editor, do
```

EDITOR=nano sudo visudo

```

did you try

```

p.n  ALL=NOPASSWD:/usr/bin/ssh

```

?[/QUOTE]
nope.  still no joy.  sudo does not co,plain, but i am still asked for a password.

---

### Post by cwaldbieser on 2006-03-19
[QUOTE=p.n]Thanks that sorted that out but obviously leaves met with the problem that this:
```
 username ALL=PASSWD: ALL; NOPASSWD: /usr/bin/ssh
``` does not work.

I'll try to read up a bit on sudo.  man does not say too much.

p.n[/QUOTE]
The man pages for "sudoers" contains the complete grammar for the file, but it probably would have been better to include a few examples (not everyone likes reading EBNF).

I would open 2 terminals when experimenting.  In the first, I would issue a "sudo bash" to get a root shell and keep that open so I could visudo if I mess anything up.  In the second terminal, I would try to type in what I thought the line should look like.

---

### Post by p.n on 2006-04-20
OK, I finally got round to sorting this little irratation out.  I was doing everything right but was ignoring mlind's comment on where the entry should be placed in the file...

p.n

---

