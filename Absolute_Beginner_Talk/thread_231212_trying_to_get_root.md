---
title: "trying to get root"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by gpw1 on 2006-08-07
I'm trying to use a HOWTO: to install pdf printer
This HOWTO: asks me to go to terminal and type: "sudo nautlius", when I do this my computer just sits with a cursor blinking.

gpw1

---

### Post by Christmas on 2006-08-07
You have to enter your user's password. Don't worry it doesn't appear as you type, it goes in even if you don't see what you're typing. After you typed it hit enter. Better instead of "sudo nautilus" do a:
```
gksudo nautilus
```
This will open a GUI (Graphical User Interface) window where you will be able to enter a password. Also note that if you run CLI (Command Line Interface) like Nano, you will have to type "sudo nano" and enter the password in the terminal. You can also read the Wiki's RootPassword article in my signature.

---

### Post by gpw1 on 2006-08-07
This my results:

george@george-laptop:~$ gksudo nautilus
(nautilus:8765): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by cantormath on 2006-08-07
> **gpw1 said:**
> This my results:

george@george-laptop:~$ gksudo nautilus
(nautilus:8765): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

try sudo: 
```
cantormath@cantormath-laptop:~$ sudo nautilus
Password:
```
it show the password as you type it....

---

### Post by gpw1 on 2006-08-07
I have tried that. It lead me to my original post.

---

### Post by cantormath on 2006-08-07
> **gpw1 said:**
> I have tried that. It lead me to my original post.

is your user a member of the "admin" group?

---

### Post by gpw1 on 2006-08-07
I'm sure I am as I have loaded a bunch of programs and installed Automatix. I have just noticed this issue just lately. I have used sudo many times, and noticed that if I typed sudo "and a program name" and miss spelled the program name the cursor would just start blinking and nothing would happem. In the current case that is not the problem. Stumped...

What is the terminal code to find out the answer to your question? All I was trying to do is get root in Nautilus so I could edit some conf files to losd Cups-pdf printer

gpw1

---

### Post by cantormath on 2006-08-07
when you type 

```
sudo -i
```

or 

```
sudo -s -H

```
what happens? Do you get root?

---

### Post by gpw1 on 2006-08-07
Hi,
Both those commands put me into root... BUT "sudo nautilus" FAILS or at least does nothing...
It also failed yesterday when I was trying to do "sudo gedit and a file name

gpw1

---

### Post by steve.horsley on 2006-08-07
A work-round for now might be to use **sudo su** to get root and then launch **nautilus** from there. But that doesn't explain your problem with sudo nautilus.

---

### Post by gpw1 on 2006-08-07
hi,
Now it cannot find the program nautilus... I used "sudo su nautilus"

What kind of squirrel I got in my system...

gpw1

---

### Post by gpw1 on 2006-08-07
I did "sudo su nautilus"... Now it tells me it cannot find nautilus...

---

### Post by steve.horsley on 2006-08-07
They should be two different commands: 
> sudo su
nautilus
The first command gets you root, the second launches nautilus. 

If the forst command gets you a root prompt (with a #) properly, the second _should_ launch nautilus. If not, maybe root's path is screwed? Try the command:
**echo $PATH**
which lists where the shell looks for programs. Mine looks like this:
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

Also try **whereis nautilus**

---

### Post by gpw1 on 2006-08-07
george@george-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
george@george-laptop:~$ whereis nautilus
nautilus: /usr/bin/nautilus /usr/lib/nautilus /usr/bin/X11/nautilus /usr/share/nautilus /usr/share/man/man1/nautilus.1.gz
george@george-laptop:~$

These look like they are correct... I got a grapical error when I tried to open "nautilus" 

Should I reinstall Ubuntu before I get any further? I need a stable system to work from...

---

### Post by cantormath on 2006-08-07
well, so you can get root........must be that you are having a nautilus
problem.

---

### Post by steve.horsley on 2006-08-07
> **gpw1 said:**
> george@george-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
george@george-laptop:~$ whereis nautilus
nautilus: /usr/bin/nautilus /usr/lib/nautilus /usr/bin/X11/nautilus /usr/share/nautilus /usr/share/man/man1/nautilus.1.gz
george@george-laptop:~$

These look like they are correct... I got a grapical error when I tried to open "nautilus" 

Should I reinstall Ubuntu before I get any further? I need a stable system to work from...

You didn't get root. It looks like **sudo su** didn't work either - you should have gotten a # prompt instead of a $ prompt. I am having trouble thinking what could cause this. Ideas anyone?

---

