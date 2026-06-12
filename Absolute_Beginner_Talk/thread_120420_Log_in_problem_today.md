---
title: "Log in problem today"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Temis on 2006-01-21
After log in I get this message:
 "Could not look up internet address for. this will prevent GNOME from operating
correctly. It may be possible to correct the problem by adding to the 
file/etc/hosts"
What file is this and where do I find it?

---

### Post by christhemonkey on 2006-01-21
that file lets ubuntu know which ip addreses or whatever to allow the pc to access (or something not 100% on this!)
This file is in /etc
TO edit it:
sudo vi /etc/hosts

(replace vi with gedit if your using a gnome terminal)

---

### Post by cayamara on 2006-01-21
[QUOTE=Temis]It may be possible to correct the problem by adding to the 
file/etc/hosts
What file is this and where do I find it?[/QUOTE]
You'll find it in /etc/hosts. ```
$ sudo gedit /etc/hosts
```
Here's my file for comparison (looks pretty standard to me):
```
127.0.0.1       localhost.localdomain   localhost       ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
You could try it with my file or post yours to see where the error is ... :cool:

---

### Post by cwaldbieser on 2006-01-21
[QUOTE=Temis]After log in I get this message:
 "Could not look up internet address for. this will prevent GNOME from operating
correctly. It may be possible to correct the problem by adding to the 
file/etc/hosts"
What file is this and where do I find it?[/QUOTE]
The file is /etc/hosts.
It is located it the /etc folder.

If you are not used to reading folder names in this fashion, the first "/" is the very top level folder of your system.  Then you traverse the folders reading left to right.  So /home/joe/pictures/horse.jpg would mean start at the top folder, look in the home folder, look in the joe folder, look in the pictures folder, the file is horse.jpg.

There should be a line somewhere at the top of the file like this:
```

127.0.0.1 localhost.localdomain localhost <computer-name>

```
The bit in angle brackets, <computer-name>, should be replaced with the name you want to give your computer.

You will probably have to log in via a virtual consol (CTRL+ALT+F1) and edit the file with nano, pico, or vi:
```

$ sudo nano /etc/hosts

```
Hope that helps!

---

### Post by Temis on 2006-01-21
Thanks everybody. I will be back with result.

---

### Post by Temis on 2006-01-21
I tried the gnome terminal and the virtual console and in both cases I got this message: "unable to lookup via gethostbyname()"
Not sure how I got into this mess. When I go to the terminal only my log in name
appears. Before this problem it looked like this: my log in name@ computer name.
Now the computer name disappeared.

Another question: How do I exit properly from the virtual console?

---

### Post by GreyFox503 on 2006-01-21
When you're done using a virtual console, logoff by typing "exit" and then it should go back to a login prompt.

To switch between virtual terminals, press Ctrl + Alt + F#, where F# is the F-key that you want to switch to.  Normally, your graphical session runs in F7, and F1-F6 are reserved for text terminals.

If you're having trouble editing that file, you could try rebooting the computer and choosing the "recovery" option at the GRUB selection screen.

---

### Post by cayamara on 2006-01-23
[QUOTE=Temis]When I go to the terminal only my log in name
appears. Before this problem it looked like this: my log in name@ computer name.
Now the computer name disappeared.[/QUOTE]
Hmm ...
What does ```
$ set|grep HOSTNAME=
```give you?

---

### Post by Temis on 2006-01-24
I tried this and the result was "no such file or directory". I guess I have to delete and reinstall ubuntu. But this will be my last resort. Maybe somebody has a better idea.

---

### Post by GreyFox503 on 2006-01-24
Did you copy and paste it directly?

```
$ set|grep HOSTNAME=
```

This character :  |

between set and grep is a pipe, not a slash.  On my keyboard it's above the Enter key.  Just checking to make sure.  :)

---

### Post by Temis on 2006-01-24
OK I used this character | . After the equal sign I entered the host name (computer name I entered during install) and hit enter. The result was:
myloginname@ $. (It should have been myloginname@$hostname)                 Then I rebooted. But the problem persists. I cannot copy and paste. I been trying  to connect to the internet since weeks now(dial up).That how I got into this mess, somehow I deleted the host name.

---

### Post by Temis on 2006-01-28
Problem solved by reinstalling ubuntu.

---

### Post by gagatz on 2007-01-02
type in terminal:

su

and after entering the password,

nano /etc/hosts

then replace the first line with


 127.0.0.1 localhost.localdomain localhost computername

where computername is the name that comes up if you type 

host 

in a terminal

---

