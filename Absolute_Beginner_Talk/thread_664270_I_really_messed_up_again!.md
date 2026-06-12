---
title: "I really messed up again!"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2008-01-11
First let me tell you what is wrong then I'll tell you what I think I did wrong.


I noticed that my text editor was not opening so I thought I would restart my PC to see if it was just a glitch or not. I get to the login screen and type is my stuff.

It won't let me log in.

I get the following message...

```
User's $HOME/.dmrc file is being ignored. 
This prevents the default session and language from being saved.
 File should be owned by user and have 644 permissions.
 User's $HOME directory must be owned by user and not writable by other users.
```

I click OK and then I get the following message...
```
Your session only lasted less than 10 seconds.
If you have not logged out yourself, this could mean that there is some installation problems or that you may be out of diskspace.
Try logging in with one of the failsafe sessions to see if you can fix the problem.      
``` 

Below that is a check box that says

```
View details (~/.xsession-errors file) 
```

I click ok and I am back at the login screen


Now, for I think I did wrong. I went into my user profile prefs and changed my home folder to ```
/home
```
Instead of ```
/home/bill
```
If this is the case is there a way to change it back?

I tried some of the failsafe sessions and the only one that works is the terminal.

:(:(:( please help.

---

### Post by zabien1970 on 2008-01-11
Still learning to use the terminal myself but am wondering if  chown  would work

---

### Post by p_quarles on 2008-01-11
Safest bet is to login to recovery mode (from the GRUB menu). If you decide to use the failsafe terminal from the login screen, though, be sure to add "sudo" to the following command.

To change your user's home folder back to its correct location:
```
usermod -d /home/bill bill
```If .dmrc continues to give you trouble:
```
chown bill /home/bill/.dmrc
```then:
```
chmod 644 /home/bill/.dmrc
```If *that* fails, you'll be able to resolve the situation by deleting the .dmrc file in your user's home folder. A new one will be generated automatically.

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> Safest bet is to login to recovery mode (from the GRUB menu). If you decide to use the failsafe terminal from the login screen, though, be sure to add "sudo" to the following command.

To change your user's home folder back to its correct location:
```
usermod -d /home/bill bill
```If .dmrc continues to give you trouble:
```
chown bill /home/bill/.dmrc
```then:
```
chmod 644 /home/bill/.dmrc
```If *that* fails, you'll be able to resolve the situation by deleting the .dmrc file in your user's home folder. A new one will be generated automatically.

OK it is still continuing. I am pretty new to the shell so could you  show me how i would go about deleting the .dmrc file....thanks

all i need to do it get back to GNOME so i can change my home folder back to /home/bill

---

### Post by p_quarles on 2008-01-11
> **moebob24 said:**
> OK it is still continuing. I am pretty new to the shell so could you  show me how i would go about deleting the .dmrc file....thanks

all i need to do it get back to GNOME so i can change my home folder back to /home/bill
The first command I gave should have done that. When you log into the shell, what is the result of typing this command?:
```
pwd
```

---

### Post by zabien1970 on 2008-01-11
P_quarles  Shouldn't the chown and chmod commands have sudo first?

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> The first command I gave should have done that. When you log into the shell, what is the result of typing this command?:
```
pwd
```

When i print it tells me im still in 
```
/home
```

---

### Post by p_quarles on 2008-01-11
> **zabien1970 said:**
> P_quarles  Shouldn't the chown and chmod commands have sudo first?
In multi-user mode, yes, but I was specifically directing the OP to use recovery mode, which is a root login.

---

### Post by p_quarles on 2008-01-11
> **moebob24 said:**
> When i print it tells me im still in 
```
/home
```
Then, did you run the command correctly? As written in recovery mode (from the GRUB menu), or with "sudo" at the beginning if you're using the failsafe terminal from the login menu.

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> Then, did you run the command correctly? As written in recovery mode (from the GRUB menu), or with "sudo" at the beginning if you're using the failsafe terminal from the login menu.

This is what i typed 

```
sudo usermod -d /home/bill bill
```

i ran that and then it came back as if it ran correctly
i ran
 ```
cd
```
to see my home folder and it was still /home

---

### Post by moebob24 on 2008-01-11
I am thinking reformat...I have my files backed up on an external drive...the worst will be updating back to 7.10

---

### Post by p_quarles on 2008-01-11
No, don't reformat. If we can't find a command line solution to the specific problem, it's perfectly easy to just create a new user use your old home folder. 

Did you logout/login after running the command to change the home folder?

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> No, don't reformat. If we can't find a command line solution to the specific problem, it's perfectly easy to just create a new user use your old home folder. 

Did you logout/login after running the command to change the home folder?

...its back...idk y it didn't work the first time but i logged out and back in with GNOME and everything came back....

I just checked my home folder and it is 

/home/bill


I owe you man!!!

THANK YOU!!
:guitar:

---

### Post by moebob24 on 2008-01-11
...new problem....the gnome-terminal has a problem

```
There was an error creating the child process for this terminal
```

---

### Post by p_quarles on 2008-01-11
> **moebob24 said:**
> ...new problem....the gnome-terminal has a problem

```
There was an error creating the child process for this terminal
```
Strange. What happens if you try another terminal emulator? I.e., alt-F2 then type:
```
xterm
```

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> Strange. What happens if you try another terminal emulator? I.e., alt-F2 then type:
```
xterm
```

Already tried it....works perfectly. You think I could uninstall and reinstall the gnome one?

---

### Post by p_quarles on 2008-01-11
> **moebob24 said:**
> Already tried it....works perfectly. You think I could uninstall and reinstall the gnome one?
Might work:
```
sudo dpkg-reconfigure gnome-terminal
```

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> Might work:
```
sudo dpkg-reconfigure gnome-terminal
```

...nope seemed like it worked but when I opened gnome same message.

---

### Post by moebob24 on 2008-01-11
I have them both the terminal and data file set for a reinstall right now in the synaptic manager...do you think that might help?

---

### Post by p_quarles on 2008-01-11
Next step would be to try to get more verbose error output about why gnome-terminal isn't working. Try launching it from xterm:
```
gnome-terminal &
```Then, post the output here.

> I have them both the terminal and data file set for a reinstall right now in the synaptic manager...do you think that might help?Not if the other command didn't fix it.

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> Next step would be to try to get more verbose error output about why gnome-terminal isn't working. Try launching it from xterm:
```
gnome-terminal &
```Then, post the output here.

Not if the other command didn't fix it.



```
[1] 7019
bash: gnome-terminal: command not found 
```
and now it won't come back....its just the cursor with no prompt

---

### Post by p_quarles on 2008-01-11
> **moebob24 said:**
> ```
[1] 7019
bash: gnome-terminal: command not found 
```
and now it won't come back....its just the cursor with no prompt
Command not found? Well, that's darn weird. 

Can you post the contents of this file?:
```
cat /etc/environment
```

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> Command not found? Well, that's darn weird. 

Can you post the contents of this file?:
```
cat /etc/environment
```

```
 PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
```

---

### Post by p_quarles on 2008-01-11
> **moebob24 said:**
> ```
 PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
```
Looks fine.

Umm, maybe try reinstalling gnome-terminal? <scratches head>:
```
sudo apt-get install gnome-terminal
```

---

### Post by moebob24 on 2008-01-11
After they install ill restart to see if that takes care of it

---

### Post by moebob24 on 2008-01-11
same problem...maybe pulling them all the way out, restarting, then installing, and restarting

I don't know if restarting helps with Linux, ive been a Windows guy all my life until now.

---

### Post by p_quarles on 2008-01-11
Logging out is necessary before changes to an account take effect. Rebooting is only necessary for changes to the kernel. The current problem shouldn't fall under either category.

I'd suggest trying the new user account I mentioned earlier. This will, at the very least, help isolate the problem:
```
sudo useradd -d bill2
```
Now, set a password:
```
sudo passwd bill2
```
Finally, add the new account to the users with sudo privileges:
```
sudo addgroup bill2 admin
```
Now, try logging in as the new user, and see if gnome-terminal works.

---

### Post by moebob24 on 2008-01-11
> **p_quarles said:**
> Logging out is necessary before changes to an account take effect. Rebooting is only necessary for changes to the kernel. The current problem shouldn't fall under either category.

I'd suggest trying the new user account I mentioned earlier. This will, at the very least, help isolate the problem:
```
sudo useradd -d bill2
```
Now, set a password:
```
sudo passwd bill2
```
Finally, add the new account to the users with sudo privileges:
```
sudo addgroup bill2 admin
```
Now, try logging in as the new user, and see if gnome-terminal works.

I just uninstalled it completely and reinstalled it...same problem...are there any other emulators that give the same feel as gnome?...im working on the new account now

---

### Post by p_quarles on 2008-01-11
Yeah, there's xfce4-terminal, available via Synaptic. That's very similar to gnome-terminal. I think this problem is fixable, though.

---

### Post by moebob24 on 2008-01-11
bill@bill-linux:~$ sudo useradd -d bill2
[sudo] password for bill:
useradd: invalid home directory 'bill2'
bill@bill-linux:~$

---

### Post by moebob24 on 2008-01-11
log on to pidgin...i got an AIM account, i think it will be a little more efficient

---

### Post by p_quarles on 2008-01-11
> **moebob24 said:**
> log on to pidgin...i got an AIM account, i think it will be a little more efficient
done

---

