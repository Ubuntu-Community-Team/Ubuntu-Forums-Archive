---
title: "Can't use GUI apps as root"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by dino195 on 2007-01-27
Having problems using any GUI apps as root. I can log in to a console and I'm able to su to root in a terminal but everytime I try to use a GUI as root it says that my root password is wrong. 

Any ideas???

---

### Post by jordanmthomas on 2007-01-27
to run a gui app as root do this:
```
gksudo appname
```
to get a root terminal do this:
```
sudo su
```
The reason your password doesn't work is that root has no password by default and if you wish to use root you must give it a password yourself.
You can read up on it here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Bachstelze on 2007-01-27
Running GUI apps from a root shell will not work, the X server will refuse the connection. So the preferred way to launch GUI apps as root is to use gkseudo wile logged in as yourself. If you're using KDE, use kdesu instead.

---

### Post by dino195 on 2007-01-27
gkseudo is not working for me. Could you explaine it step by step? I have a little experience with gnome but I have mostly used KDE. I have Debian Sarge on my desktop computer with gnome and haven't had any  problems getting root. I just installed Ubuntu on my lappy because all my hardware and wirless card worked with the live version. I am very new to Ubuntu. have lots of questions but figured that learing how to get root was a good place to start :D. Just to be clear, I can get a root shell and have no problems logging in as root through the console.

Thanks for the replies! :D

---

### Post by taurus on 2007-01-27
For KDE, use kdesu.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dino195 on 2007-01-27
I am using gnome.

---

### Post by meng on 2007-01-27
gksudo (not gksuedo, that was a misspelling)

e.g.
gksudo nautilus
gksudo gedit

---

### Post by Patrick-Ruff on 2007-01-27
there are also some nautilus scripts that allow this, I'm pretty sure automatix has them.

---

### Post by dino195 on 2007-01-27
OK, the shell is recognizing the gksudo command as a bash command but it is still not recognizing my root password. This is what the shell is printing:

valhalla@VALHALLA:~$ gksudo nautalis
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt
 
I also get an error message popup that  says Failed to run nautalis as user root: Wrong password.

This makes no sence to me. I know my password is good because I can get root in a terminal with the su command.

Kind of aggrievating, I can't even accees my help file for some reason.

---

### Post by Tomosaur on 2007-01-27
Well, it's 'nautilus', not 'nautalis'.

What is the GNOME_SUDO_PASS thing? gksudo is supposed to pop up a password box for you to type your pass into.

---

### Post by dino195 on 2007-01-27
Yup, I had it misspelled, still don't work with the correct spelling or with any other apps. There is a password popup box, it's just not accepting my password. The GNOME_SUDO_PASS thing is what the terminal screen is printing.

---

### Post by dino195 on 2007-01-27
OK, I figured out that I can launch Nautilus using the so command and logging in as root "as I have done with other distros in the past"  Would like to be able to log in as root and configure all my stuff withough having to open them from a root shell

---

### Post by dino195 on 2007-01-27
OK, I figured out that I can launch Nautilus using the su command and logging in as root "as I have done with other distros in the past"  Would like to be able to log in as root and configure all my stuff withough having to open all apps from a root shell or be asked for a password everytime I try to do something minute. Any way to do this?

---

### Post by Tomosaur on 2007-01-27
Logging in as root as generally considered a no-no, you should stick with solving this problem rather than resorting to that.

---

### Post by Pobega on 2007-01-27
Well, are you able to run commands using sudo? Or how about trying "sudo -i", then running the application you want to run as root, i.e.:> user@computer:~$ sudo -i
Password:
root@computer:~# nautilus

---

### Post by Buck2348 on 2007-01-27
Some of the terminology is a little outdated, but [this]("http://easylinux.info/wiki/Ubuntu_Edgy#User_Administration") will tell you a lot about adjusting superuser/password options.  If you really want to log in as root (dangerous), after you enable that in System --> Administration --> Login Window --> Security --> checkmark "Allow local system administrator login", click on the red icon in extreme upper right screen corner, select "logout".  When you get a new login screen, username = "root", and the password you have set with "sudo passwd root".

Buck

---

### Post by dino195 on 2007-01-27
Thanks a lot Buck. Now I can at least begin to work on the problem. I am able to log in as root now that I made the login change. 

I understand very well that it is dangerous to log in as root but I need to be able to get administration priveleges to even begin to work on the problem. I have bigger fish to fry with this install but want to be able to get root priveleges so I can begin to work on the problem.

I would much prefer to be able to log in from user mode and use my apps but it is not allowing me to do that. I tried changing my passwd from a root shell then logged back in to see if I could sudo in to my apps. No luck. I also read your link and tried to work with my passwd using the sudo passwd root command and it would not allow my passwd. It said that my passwd was wrong for the root account. I can however use the su command and log into my root account as I have always done with other distros. Why is it not recognizing my root passwd when I try to use sudo or bring up a GUI app?

---

### Post by dino195 on 2007-01-27
So where do I go from here to a more advanced forum? Surely there has to be a simple explaination as to why I can't use sudo to open my GUI apps or indeed, juct click on them and enter my passwd. Must I log in as root and launch all my apps through a shell? What is the point in even having an App menu if that is the case?

---

### Post by Tomosaur on 2007-01-27
Please understand that yours is a **problem**, it's not normal, and as such, there's no point saying things like 'what's the point in an app menu?'. Your information has been scarce to say the least. Are you the usual administrator? Did you mess around with your user account(s)?

---

### Post by Daveski on 2007-01-27
> **dino195 said:**
> Surely there has to be a simple explaination as to why I can't use sudo to open my GUI apps or indeed, juct click on them and enter my passwd.

Indeed, but you still haven't answered the question whether you are able to run sudo <command> in the terminal successfully. You specifically mention not being able to run GUI apps, and you obviously know quite a bit about Linux in general, but people here will not be able to point you in the right direction unless they know exactly where the problem occurs.

---

### Post by Sef on 2007-01-27
> be asked for a password everytime I try to do something minute.

Once you enter your password for sudo, it stays open for 15 minutes.

> What is the point in even having an App menu if that is the case?

As has been mentioned, you have a problem.  You should focus on getting the problem resolved instead of using an unsafe method to resolved your problem.

(Note to new users reading this thread: Running as root makes your computer as hackable as Windows XP.)

---

### Post by dino195 on 2007-01-27
"I tried changing my passwd from a root shell then logged back in to see if I could sudo in to my apps. No luck."

Sorry if I didn't make myself clear. Yes I can execute a sudo command but it does not recognize my root passwd. It is as though there is a default admin account or something. I can log in as root using the su command but I still can't launch apps. I keep getting an error message saying I am not using the correct passwd for the root account (even when I am logged into the shell as root).

Here is all the info that I can remember.I partitioned my hard drive and created a 10 gig partition for ubuntu using the Ext 2 file system. I then did the install in expert mode and everything seemed to go smoothly except that I used partition magic an have temporarily hosed my windows partition (not ubuntu's fault). It is a minor problem and I should be able to straighten it out after I figure out what is going on with this problem. I first noticed that I could not use my apps after I first logged in and tried to view the available updates that the popup informed me were available. When I tried to veiw the available updates, synaptic would not launch saying that my root passwd was no good. I then opened a shell and logged in as root using the su command and tried to launch a couple of apps. It was still telling me that my passwd was not the root passwd even though I was logged in as root. I then came here and used the advise given to try to use the gksudo and sudo command. Still didn't recognize my passwd. I tried changing my root passwd and that still didn't work. I then changed my login security to be able to login as root at startup just to see if I could launch apps llike that. Sure enough, I was able to launch any and all apps when I logged in as root from startup. I am not wanting to have to login as root everytime I want to run an app. That is why I am trying to figure out why I can't use my root passwd to sudo into an app or more preferrably, just enter my passwd when prompted after I try to launch an app from the menu. Again, I can login as root from a console and a terminal. Just can't luanch programs normally because it's telling me my root passwd is incorrect.

---

### Post by jordanmthomas on 2007-01-27
When you use sudo, you are supposed to use the password of the user initialising the command.
ie, use dino195's password:  **not** the root password.

Or were you already doing this?

---

### Post by dino195 on 2007-01-27
Have tried doing both Jordan. Neither has worked. I can use the su command and launch an app but I would prefer to just launch them from the menu and launch my favorites from the task bar.

---

### Post by taurus on 2007-01-27
Output of 

```
id
```

---

### Post by dino195 on 2007-01-27
What output are you looking for taurus? You'll have to work with me I'm not very experienced. This is what it tells me when I try to look at available updates and I enter my root passwd:

Failed to run /usr/bin/update-manager as user root:
 Wrong password.

---

### Post by taurus on 2007-01-27
Log in with your regular account and paste the output of this command here.  Just want to make sure you belong to groups adm & admin.

```
id
```

---

### Post by dino195 on 2007-01-27
tried it and it's not recognizing it as a bash command.

valhalla@VALHALLA:~$ code:
bash: code:: command not found

---

### Post by Tomosaur on 2007-01-27
Haha, looks like you misunderstood. The command to type is 'id'. The 'code' bit is just something the forum itself puts in to highlight commands :P

---

### Post by dino195 on 2007-01-27
Thanks for the help. it's been a long day.

uid=1000(valhalla) gid=1000(valhalla) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),1000(valhalla)

---

### Post by taurus on 2007-01-27
> **dino195 said:**
> Thanks for the help. it's been a long day.

uid=1000(valhalla) gid=1000(valhalla) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),1000(valhalla)

I think you are missing group admin (112)!  Why don't you boot into recovery mode from GRUB menu and add yourself, valhalla, to group admin. 

```
adduser valhalla admin
```
To be sure you have group admin, run this command to confirm it.

```
id valhalla
```
If everything is good, reboot your machine.

```
shutdown -r now
```
Now, log in with your username and password.  Open a terminal and see what happens when you run this command!

```
sudo aptitude update
```
(Don't forget to use the same password that you use to log in, not the root's password.)

---

### Post by dino195 on 2007-01-27
When I try to add myself using "adduser valhalla admin" I get a mesg saying 
"The group 'admin' does not exist".

Whatcha think?

---

### Post by taurus on 2007-01-27
Can you paste the output of this command here?

```
cat /etc/group
```

p.s.  And did you ever mention which release you are using right now?

---

### Post by dino195 on 2007-01-27
trying taurus... the code is making 52 smilies in my post and won't let me submit it... let me figure out how to turn the smilies off. :)

---

### Post by dino195 on 2007-01-27
valhalla@VALHALLA:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:valhalla
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:valhalla,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:valhalla,hal
floppy:x:25:valhalla,hal
tape:x:26:
sudo:x:27:
audio:x:29:valhalla
dip:x:30:valhalla
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:valhalla
sasl:x:45:
plugdev:x:46:valhalla,hal
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
valhalla:x:1000:
lpadmin:x:104:valhalla
scanner:x:105:valhalla
crontab:x:106:
ssh:x:107:
slocate:x:108:
messagebus:x:109:
hal:x:110:
saned:x:111:
gdm:x:112:
valhalla@VALHALLA:~$

---

### Post by dino195 on 2007-01-27
And root:

root@VALHALLA:/home/valhalla# cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:valhalla
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:valhalla,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:valhalla,hal
floppy:x:25:valhalla,hal
tape:x:26:
sudo:x:27:
audio:x:29:valhalla
dip:x:30:valhalla
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:valhalla
sasl:x:45:
plugdev:x:46:valhalla,hal
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
valhalla:x:1000:
lpadmin:x:104:valhalla
scanner:x:105:valhalla
crontab:x:106:
ssh:x:107:
slocate:x:108:
messagebus:x:109:
hal:x:110:
saned:x:111:
gdm:x:112:
root@VALHALLA:/home/valhalla#

---

### Post by taurus on 2007-01-28
Okay, we need to add group admin to /etc/group so you can use sudo again.  I have no idea why it's not there at all.

Boot into recovery mode and at the prompt, type

```
nano /etc/group
```
Use the down arrow key to scroll down to the end.  Then, add this line to it.

```
admin:x:114:valhalla
```
Exit with <Ctrl>x and save it with Y then Return.  Look at /etc/group again to make sure the last line looks like what you just added.

```
cat /etc/group
```
Now, see if you, valhalla, belongs to group admin (among others) now with

```
id valhalla
```
If everything is good.  Reboot your machine with

```
shutdown -r now
```
Log in with your username, valhalla, and password and run this command from a terminal.  Let me know what's the output is.

Applications -> Accessories -> Terminal
```
sudo aptitude update
(use the same password that you log in with, NOT root's password.)
```

---

### Post by dino195 on 2007-01-28
Hmm... Still can't use sudo. I checked id valhalla and it successfully added 114(admin) but when I enter :~ sudo aptitude update nothing happens. Here is the output:

valhalla@VALHALLA:~$ sudo aptitude update
Password:
valhalla@VALHALLA:~$

and when I try to do it a second time it doesn't even prompt me for a passwd:

valhalla@VALHALLA:~$ sudo aptitude update
valhalla@VALHALLA:~$


Here is the output from my id:

valhalla@VALHALLA:~$ id valhalla
uid=1000(valhalla) gid=1000(valhalla) groups=1000(valhalla),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),114(admin)

---

### Post by dino195 on 2007-01-28
should I possibly have made that 113 (admin)?

---

### Post by taurus on 2007-01-28
There is something fishy going on with your machine!  :-k

---

### Post by taurus on 2007-01-28
> **dino195 said:**
> should I possibly have made that 113 (admin)?

It's (admin) 114 on my Edgy.

---

### Post by taurus on 2007-01-28
Can you boot into recovery mode again and post the contend of this file here?

```
cat /etc/sudoers
```

---

### Post by dino195 on 2007-01-28
Just ran apt-get update from a console and it worked fine. It's how I usually update anyway. What do you think, try a new install? everything worked fine in the live version and this is the first distro I have used on my lappy that recognized all of my hardware and wireless card out of the box. I'm not getting any funky messgs in dmesg | tail. Everything seems to be good to go except I can't access my help file and I cant use sudo. Funny thing is I can bring up any app when I su to root. What do you think?

---

### Post by taurus on 2007-01-28
It's probably best to reinstall and don't forget to format the partitions.  Then, try not to create any password for root.  Instead, see if sudo works with your regular account.  

Good luck.

---

### Post by dino195 on 2007-01-28
LOL, will do. I am so used to creating a root acct and passwd that it is second nature. Probably  where I went wrong. Won't be the first time I have had to start from scratch. Hey, if I can install Debian I can make anything work. :)

---

### Post by taurus on 2007-01-28
After you finished re-installing it, see right away if you can update your machine from a terminal with

```
sudo aptitude update
sudo aptitude upgrade
```
And if there is a problem, then it's easier to fix then since it's a new install and you haven't changed anything, yet.  Of course, may want to start a new thread since this one is getting a little long.

---

### Post by dino195 on 2007-01-28
Gotcha. Thanx for the help!

---

### Post by dino195 on 2007-01-28
For anyone who searches and finds this post with the same problem as me read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Apparently you are not allowed to have a root account with ubuntu. Guess that's OK for someone who is new to linux and needs to be protected from themselves. However it is unacceptable to me and probably to most others with some experience. I think Ubuntu should rethink this, Haven't decided if I will keep using this distro or not. Depends if I can find a work around for the sudo problem. Not having a root account is just not an option. Great distro for compatibility but needs to loosen up and not try so hard to protect it's users from themselves.

---

### Post by jure1873 on 2007-01-29
the way I "solved" the thing that root couldn't run gui apps
# allow root to access the display (maybe specifying only localhost would be better)
xhost +
# go into superuser mode
su -
# tell it where is the local display
export DISPLAY=:0
# start the gui app
kate /etc/X11/xorg.comf or whatever

but I'm not sure if this works if sudo is not working

---

### Post by luke16 on 2007-02-02
> **jure1873 said:**
> the way I "solved" the thing that root couldn't run gui apps
# allow root to access the display (maybe specifying only localhost would be better)
xhost +
# go into superuser mode
su -
# tell it where is the local display
export DISPLAY=:0
# start the gui app
kate /etc/X11/xorg.comf or whatever

but I'm not sure if this works if sudo is not working

But that would only work temporarily wouldnt it? Is there a permanent way to fix glitch?

---

