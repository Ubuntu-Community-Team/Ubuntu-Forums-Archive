---
title: "Password in the Terminal Window"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by swooshvapors13 on 2006-02-25
When I am asked to give my password in the terminal window it will not allow me because my password is all numbers. What is going on? How can I fix it?

---

### Post by aysiu on 2006-02-25
Change your password to something else?

Are you sure it's because it's all numbers? How do you know?

By the way, when you enter your password, you'll get no visual feedback--Ubuntu is still accepting your password.

---

### Post by swooshvapors13 on 2006-02-25
Well I don't know for sure if that is why but I don't know why it wouldn't let me enter my password.

---

### Post by aysiu on 2006-02-25
[QUOTE=swooshvapors13]Well I don't know for sure if that is why but I don't know why it wouldn't let me enter my password.[/QUOTE] What do you mean by "wouldn't *let*" you? Did you get some kind of error message? Did it say "sorry, wrong password"?

---

### Post by linuxusr50 on 2006-02-25
Don't take this the wrong way, I just want to make sure you haven't overlooked the obvious.  I have done many things like this in the past and spent time and energy on very simple issues.

Have you checked to make sure num lock is on?

---

### Post by swooshvapors13 on 2006-02-25
Num lock is on for sure.

---

### Post by xhie on 2006-02-25
You wont actually see anything happen while your typeing your password, is a security feature, no little *** or anything, just type it normally and hit enter.

unless your getting an error message?

---

### Post by aysiu on 2006-02-25
Okay. Let's get some further clarification here.

So you installed Ubuntu and created a user with a password that's all numbers. The installer seemed to have no problem with this.

You then logged into the graphical user interface with your username and your password that's all numbers.

Then you fire up a terminal *window* within the graphical user interface and try to do some kind of *sudo* command (for example *sudo apt-get update*), at which point you're prompted for your password. You try to enter your password (that's all numbers) and then what happens exactly?

Is it something like this? ```
swooshvapors@ubuntu:~$ sudo apt-get update
Password:
Sorry, try again.
Password:
```

---

### Post by swooshvapors13 on 2006-02-25
Actually the person above you may have it. I guess that the password isn't seen as you type it in? Let me try what she says.

---

### Post by swooshvapors13 on 2006-02-25
Okay here is what happens:
patrick@ubuntu:~$ sudo sh ~/Desktop/yourfile.bin
Password:
sh: /home/patrick/Desktop/yourfile.bin: No such file or directory
patrick@ubuntu:~$ sudo sh ~/Desktop/yourfile.bin
sh: /home/patrick/Desktop/yourfile.bin: No such file or directory
patrick@ubuntu:~$
patrick@ubuntu:~$ sudo sh ~/Desktop/yourfile.bin
sh: /home/patrick/Desktop/yourfile.bin: No such file or directory
patrick@ubuntu:~$

---

### Post by linuxusr50 on 2006-02-25
Have you set a root password and if so, have you tried to logging in as root and then changing  the user password to something else?

---

### Post by xhie on 2006-02-25
your password is working just fine... you just cant run whatever script your trying to run, thats a whole differnt story.

Atleast the password is ok :)

---

### Post by linuxusr50 on 2006-02-25
Your error is telling you the file does not exist....Your password seems to be working fine.

<snip>
Okay here is what happens:
patrick@ubuntu:~$ sudo sh ~/Desktop/yourfile.bin
Password:
sh: /home/patrick/Desktop/yourfile.bin: No such file or directory
<snip>

---

### Post by swooshvapors13 on 2006-02-25
Oh okay. I just wish I knew why I can't find what I'm trying to download. I mean I have spent about two hours today trying to figure out exactly how to download a music player that supports iTunes files. I have tried extracting them although I don't really know what that means. I don't know what's going on.

---

### Post by aysiu on 2006-02-25
Can you do this? ```
cd Desktop
ls
``` and then post the output here?

---

### Post by swooshvapors13 on 2006-02-25
Okay so I'm trying to download Real Player so I do, it shows up on my desktop, I double click it nothing happens what exactly am I supposed to do with it?

---

### Post by Mustard on 2006-02-25
There are several different ways to install RealPlayer.  I would look at the two methods given for RealPlayer 10 in this wiki link...

[https://wiki.ubuntu.com/RealplayerInstallationMethods](https://wiki.ubuntu.com/RealplayerInstallationMethods)

I think you should try method 3. ie installing Realplayer 10 using the .deb package downloaded from the link on the page.

After downloading the .deb from the ftp link given you would do this (assuming you downloaded to desktop)

```

cd ~/Desktop

#the above command changes the 'working directory' in terminal to your Desktop folder
#This command is only really applicable if that is where you actually downloaded it to.
#If you downloaded it to another folder, you would need to use the cd command to go to
#that folder instead.

sudo apt-get install libstdc++5

#the above command instructs the system to download 
#a particular package from the online repository and install
# a that package, as it is needed to use Realplayer.

sudo dpkg -i realplayer_10.0.6-0.0_i386.deb

#the above instructions tells the system to install the realplayer .deb file
# that you downloaded to your desktop. The dpkg command is slightly different
# from the apt-get command, as dpkg installs packages that you have stored locally
# on your computer, whereas apt-get is used to get the packages from an
# online repository.

```

The above instructions were taken from this link...

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by localzuk on 2006-02-25
This is not due to your password. It is due to it not recognising the command you are trying to get it to run.

Try running sudo chmod ~/Desktop/yourfile.bin followed by sudo ~/Desktop/yourfile.bin

This way you cut out the need to use sh.

You could also try putting the sh ~/Desktop/yourfile.bin bit into quotes such as ```
sudo "sh ~/Desktop/yourfile.bin"
```

---

