---
title: "Problem with root logging"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by BBD on 2006-03-24
Hi there...I am still new in Linux and Ubunto so my problem could sound comically, but I have searched for a solution several days, before I decieded to post here. When I have installed Ubunto, I set up root passwd and another account for regular logging. Everything was cool, but every time when I try to configure something, the linux says that my password for "root user" is incorrect, whitch is impossible! I have tried to reinstall it 2 times and the problem still exists...When I login from the console, there is no problem and the linux accepts the pass for the root account, but I am not skilled enough to configure something from this console yet :(
If anyone could help me, I would be very grateful.

---

### Post by aysiu on 2006-03-24
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) explains *everything*, including:

1. Why Ubuntu disables root by default and favors sudo
2. The pros and cons of the sudo model (as opposed to the root/user model)
3. How to set the root password
4. How to restore a more traditional Linux security model (root/user)

---

### Post by BBD on 2006-03-24
Thank you for the quick answer! I have read this article before, but it didn`t work...( or I am making something false, but I think that It can`t be so damn hard to set up a root passwd. ) 
I will try to explain it better. When I try this with "sudo" in the console from the menu and when I type the pass, it says "Try Again" !?!?...When I run the console with alt+ctrl+f1 there is absolute no problem to enter the root account with the same passwd. From there I have typed this with "sudo passwd root " and I have changed the password but the problem still exists. Every time when I try to use something like "Login Screen Setup ", "Networking" or something else, that requires pass, it says that the pass is wrong. I have tryied with the pass from my normal account but nothing...It stopps to ask me for pass but this things simply don`t start.
I have tried also to login again with the root account from the enter screen after I have typed this command with sudo but it`s still not possible.

---

### Post by aysiu on 2006-03-24
It's not enough to enable the root account.
It's not enough to assign a root password.

Ubuntu's default is built for *sudo*, not root. So when you do administrative tasks, it's looking for the *sudo* password, not the root one.

If you go way to the bottom of the Wiki page... > **Let sudo ask for the root password**

You can make sudo ask for the root password instead of the user password, you can do this by adding the keyword rootpw to the line in /etc/sudoers that starts with Defaults.

---

### Post by trent dillman on 2006-03-24
Are you putting in the root pass, or are you using your user name's pass?

Also, I believe this is a problem from enabling the root account. You might try disabling it again.

---

### Post by BBD on 2006-03-24
I don`t know why I have such a problem.....How I have written, I have reinstalled Ubunto 2 times and the problem exists.
When I put the root password it says that it is incorrect ( thanks to aysiu, now I know why ) but I have tryed 10000 times with my user name`s password and simply nothing. There is no error message - It seems that it accepts the password ( I see this "clock" ) but nothing appears. 
I tried this with "... /etc/sudoers" but I don`t have rights to edit it...

---Just have two questions: What`s this sudo passwd, whitch is different from the root passwd? I mean, about what security are we talking when the sudo pass is the same like the normal user`s pass?( noob question but I simply don`t understand the conception of this Ubunto  - I have had SUSE for 3 months and despite it was my first linux, I hadn`t got any problems )

The second question: What should I do to have the ability to configure something on this Ubuntu Linux? 

(Thank you trent dillman and aysiu for your help!)

---

### Post by ububaba on 2006-03-24
[QUOTE=aysiu][https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) explains *everything*, including:

1. Why Ubuntu disables root by default and favors sudo
2. The pros and cons of the sudo model (as opposed to the root/user model)
3. How to set the root password
4. How to restore a more traditional Linux security model (root/user)[/QUOTE]

I believe I have not fully understood what is being said here. I have a 
**Dual Boot**. When I am in **Ubuntu** while looking at a file which is lying on
an **XP disk** and then try to start some application in **Ubuntu**. It cannot be
launched. A message appears [COLOR="Red"]*Failed to change to directory /home/myownfiles*.[/COLOR] 
It needs a restart besides one must wait some minutes to login again.
It surely has to do with my misunderstanding.
Solution?

---

### Post by BBD on 2006-03-25
any ideas for solution?

---

### Post by Madpilot on 2006-03-25
[QUOTE=BBD]
---Just have two questions: What`s this sudo passwd, whitch is different from the root passwd? I mean, about what security are we talking when the sudo pass is the same like the normal user`s pass?( noob question but I simply don`t understand the conception of this Ubunto  - I have had SUSE for 3 months and despite it was my first linux, I hadn`t got any problems )
[/QUOTE]

On Ubuntu, you do not need a seperate root account, and there is no such thing by default.

When you need root privs on the command line (terminal), just preface the command with 'sudo' and when the system asks for a password, enter **your own user password.**

For the graphical tools, when the popup asks for a password, it's asking for (guess what?) **your own user password.**

Enabling a root account can mess up a stock Ubuntu install in various ways, and isn't encouraged or needed.

---

### Post by squidward_tentacles on 2006-03-25
I have expierenced a similar problem, while attempting to run Debian packages <nmap> and others that I have installed upon my Ubuntu.....also during the course of my <multiple> failed installations, ubuntu 5.10 only once gave me the oppertunity to enter a root password, and that quickly flashed off, directly into user account set-up before I was able to enter any kind of root password. The Debian packages require a root password and will not accept my standard use password that all the regular Ubuntu packages will....any ideas?

---

### Post by squidward_tentacles on 2006-03-26
nevermind, actually *reading* the article linked to earlier above, answered my question, thanks.

---

