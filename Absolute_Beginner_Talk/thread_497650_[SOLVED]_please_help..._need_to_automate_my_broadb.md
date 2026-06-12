---
title: "[SOLVED] please help... need to automate my broadband client login  during boot up"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-07-10
hello guys

my internet broadband rquires me to login to their server using their client. i have installed the client. this client installs a service/files namely sifyd and sifyconnect in /usr/bin folder.

now i have to do this after every boot up in terminal :

1. sudo sifyd (starts the sifyd service)

2. sudo sifyconnect -l (logs me in after asking me username and password).

i am witting the terminal output below :

{
deepak@cyneuron:~$ sudo sifyd
deepak@cyneuron:~$ sudo sifyconnect -l
Welcome to Sify BroadBand Service

username :deepakgupta78
password :

Login Success
Welcome deepakgupta78,


Account Balance : 114.15
Product Code    : M128
Expiry Date     : 2007-07-14 13:47:56
Last Login      : 2007-07-10 21:00:30

Tue Jul 10 22:15:08 2007

deepak@cyneuron:~$ 

}

now i wish to make this process automatic so that it could happen automatically.

for this one suggested method i got from internet is :

{
Want to automatically login onto sify everytime you switch on the computer. Just write a shell script. Just make a file (something like sify.sh) in "/usr/bin/". The scriptwill be something like this :

$ sifyd
$ echo -e 'accountname\npassword' | sifyconnect -l

To start this everytime the computer switches on add the following lines to the /etc/rc.local file (untested):

$ bash sify.sh

}

i am doing the same by replacing accountname and password with my own values. but its not working.

when i boot up and give command "sifyconnect -l", it says that sifyd service is not running, 

please suggest me a way of automating the process.

---

### Post by KIAaze on 2007-07-10
I think your script should look like this:
_sifyd.sh:_
```

#! /bin/bash
sifyd
echo -e 'accountname\npassword' | sifyconnect -l

```

It should be placed in the "/usr/bin" directory (otherwise, you would have to update the PATH variable).

And at the end of "/etc/rc.local", you should have:
```
bash /usr/bin/sify.sh
```

Is this your case? Because in your post, you left "$" in front of the commands as if they were entered on the command prompt.

One more thing:
**Your login and password appear clearly in the "sifyd.sh" file. I don't think this is a safe solution.**

It will probably work, but it's not safe.

To make it a little bit safer (but still not perfectly safe), make sure that nobody except root can read the "/usr/bin/sifyd.sh" file by doing:
```
sudo chown root.root /usr/bin/sifyd.sh
sudo chmod 400 /usr/bin/sifyd.sh

```

You should inform yourself about public/private key authentication and RSA encryption like the ones used for SSH connections.
This might be a safer solution.

Note: You can place the script elsewhere than /usr/bin, but you'll have to adapt the commands I gave you.
Wherever you put it, just make sure to set its permissions so that only root can read it.

---

### Post by cyneuron on 2007-07-10
thanks a lot for replying...

will try this solution and report back...

one more thing with which i am confused. about the file /etc/rc.local :

in this file according to you i should have "bash /usr/bin/sify.sh"

in this file all lines are uncommented (# pre-suffixed) except one saying "exit 0"

do i need to place "bash /usr/bin/sify.sh" before it or after it ?

or 

should i just delete this line.

i really appreciate your help.... gonna try your solution... and report back....

---

### Post by KIAaze on 2007-07-10
You should place it before it.

edit:
And a little tip:
Before rebooting, make sure your script works by running it:
> sudo ./sifyd.sh
If it connects you to the internet, than it works.
After that, all you need to get to work is that it runs at startup which will hopefully not be a problem.

---

### Post by cyneuron on 2007-07-11
its not working. i still dont get automatically logged in.

i did what you told.

about running sudo ./sify.sh, here is the terminal output "

deepak@cyneuron:~$ sudo ./sifyd.sh
Password:
sudo: ./sifyd.sh: command not found
deepak@cyneuron:~$ 


please help...

---

### Post by akudewan on 2007-07-11
Hi,

If you don't mind that the dialler logs in after you start the X server, then you can have a look at antidialer:
[http://freshmeat.net/projects/antidialer/](http://freshmeat.net/projects/antidialer/)
(There's a .deb file available for download)
Antidialer can save your password, and has a "Login Automatially" option.

Personally, I hate Sify's official client. It starts consuming 100% CPU at times, and doesn't login at times.

---

### Post by KIAaze on 2007-07-11
> **cyneuron said:**
> its not working. i still dont get automatically logged in.

i did what you told.

about running sudo ./sify.sh, here is the terminal output "

deepak@cyneuron:~$ sudo ./sifyd.sh
Password:
sudo: ./sifyd.sh: command not found
deepak@cyneuron:~$ 


please help...

That's probably because you didn't run the command I gave you from where the script is located ("/usr/bin" if you did as I said).
Sorry I forgot to mention that.

Just run:
```
sudo /usr/bin/sify.sh
```

That way it should work if you put the script in /usr/bin. :)

[Make sure it's the right name too. Is it "sify.sh" or "sifyd.sh"?]

_Little lesson about running executables (commands, programs, scripts, etc):_
When a script is executable, you can run it just by typing either its full name+path or just ./script.sh.
In UNIX and GNU/Linux, "."=current directory and ".."=parent directory.

So "./script.sh" is in fact equivalent to "script.sh".

However, it's important to know that when you type a command, the shell will first search in the directories listed in the so called PATH variable.
You can see its contents by typing:
```
echo $PATH
```

This means that if you ever have an executable with the same name as an executable in /usr/bin for example (in PATH by default), just typing "script.sh" instead of "./script.sh" will in fact run /usr/bin/script.sh instead of the script.sh in the current directory.

That's why most of the time ./script.sh is used to test self-created scripts. ;)
It makes sure that you execute the script in the current directory and not a command or another script.

To find out what you're running, a good trick is:
```
which script.sh
```

---

### Post by cyneuron on 2007-07-11
thanks a ton to mr. aku dewan....

i am amazed as if why didn't google gave me this link. i had searched a lot.

and to mr. KLAzae, thanks a lot to you to. 
though it will be a great experience to learn scripting and all, but as now my broadband is working fine  from the client he provided, so i don't want to touch it unnecessarily. 

i really appreciate your help and your time you gave to me in helping me out....

only people like you make learning and using linux a fun.....

thanks

---

### Post by tus on 2007-08-22
Hello,
i have a problem with SIFY net over UBUNTU.I just installed UBUNTU 7.04 on my disk.
 Here is my effort.
 I successfully installed install.sh file

tushar@tushar-desktop:~$ sify

 

sifyconnect  sifyd       

 

tushar@tushar-desktop:~$ sifyd

 

tushar@tushar-desktop:~$ sifyd

 

Sify broadband daemon already running...

 

run sifyconnect --login to login)

 

tushar@tushar-desktop:~$ sifyconnect -l

 

Welcome to Sify BroadBand Service

 

 

 

username :tisai162tushar

 

password :
Now what  should i do ?????
FEw day's before i got error like 
Unable to Connect Sify Access Manager ::: No route to host
But now i don't get this error also.(after entering  password)
i ping my network also.And i think there is no any error.

---

### Post by cyneuron on 2007-08-22
just install antidialer.... google antidialer freshmeat. 

it works out of box.

but it needs a dependency libmcrypt. so you will have to be logged on to sify when you install it.

you can do this by loggin on to windows xp. log in to sify. then restart your computer without logging out of sify (by end task when you restart). 

hope it helps.

---

