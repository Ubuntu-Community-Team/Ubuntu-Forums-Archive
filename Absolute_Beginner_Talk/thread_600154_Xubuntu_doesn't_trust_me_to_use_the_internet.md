---
title: "Xubuntu doesn't trust me to use the internet"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by HandyAndyShortStack on 2007-11-02
I just installed Xubuntu Feisty on an old powerbook of mine.  This is my first experience with Xubuntu, and the first thing I want to get running is my usb wireless card.  I know that my card should work, because my feisty desktop (w/ Gnome) can use it no problem (zydas - zd1211 driver).  I log in and plug in my card, but the little light on it doesn't light up.  Bad sign.  So I go to the system tab in the applications menu and click on "network."  It asks for my password.  I type it in.  here is what it tells me:

[B]Failed to run network-admin as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system administrator.[/B]

:confused: uh oh :confused:

now when i click on the icon, nothing happens.  typing network-admin in the terminal does nothing.  This is a very bad start for my relationship w/ Xubuntu.  Can anyone help me?

---

### Post by Arthur Archnix on 2007-11-02
1. Are you a sudoer? Can you sudo mkdir /media/test successfully?

2. Do you see the wireless with? 
```
sudo iwconfig
```

3. Can you scan using the wireless with?
```
sudo iwlist scan
```

---

### Post by HandyAndyShortStack on 2007-11-02
Perhaps I am not a sudoer.  I tried all three of these cammands in order.  the first one asked me for a password.  I gave it my password.  it gave me another prompt.  I checked in Thunar for the test directory, but I couldn't find it.  So, I ran the other two commands.  I was not asked for a password, just given another prompt.

---

### Post by Arthur Archnix on 2007-11-02
No, it should have told you if you weren't a sudoer and given you an error message. Ok, so just do this to confirm, copy and paste one at a time.
```
sudo mkdir /media/tester
cd /media
ls
```
When you hit ls, do you see tester? It should list all the folders in media.

Then post the output of this, but replace arthur with your username
```
sudo cat /etc/sudoers
grep arthur /etc/groups
```

---

### Post by HandyAndyShortStack on 2007-11-02
hmm...

After telling it to make the tester directory, the terminal gave me another prompt.  I changed directories to /media.  I asked for a list.  I got this:

cdrom cdrom0

So I ran sudo cat /etc/sudoers
i just got another prompt.
Then I typed grep andy /etc/groups
I recieved this message:

grep: /etc/groups: No such file or directory

Maybe I messed up during the install.  I actually had Edgy running for a day or so last week, but I read that Edgy did not have the zd1211 driver I need.  I couldn't get cdromupgrade to run because of permissions issues, so I figured I'd just reinstall with a Feisty disk.  I never wanted to have permissions issues again, so I enabled root login during this install.  As it turns out, I can't figure out how to login as root anyway, and I have worse permissions problems than I did before.  I really don't want to reinstall though, because I spent all last week battling "unable to install selected kernel" errors in the installer!

Something's not right.

---

### Post by Arthur Archnix on 2007-11-02
Something is not right would be a bit of an understatement. Let's back it up a bit. Oh wait... just read through your post again. Ok. Well, it's ironic then that your rationale for a root install was to avoid permision issues. It's certainly caused a great deal of permission issues.

You're going to have to switch to another terminal and login as root. Then do this, but replace username with your username:
```
usermod -G admin,floppy,audio,video,dip,plugdev,scanner,lpadmin,netdev,powerdev,adm,dialout,cdrom username
```
If you logout of this root session, log back into your old session, you should now be able to sudo and do that stuff I mentioned before.

Ctrl+Alt+F1 should switch you to a console that lets you login as root and run that commmand.

---

### Post by HandyAndyShortStack on 2007-11-02
ok, I'll try it.  Except I don't know how to log in/out from a terminal.  What command do I use? oops nevermind you already answered thet

---

### Post by HandyAndyShortStack on 2007-11-02
the login screen I get using Ctrl+Alt+F1 gives me the following message when I try a root login:

**the system administrator is not allowed to login from this screen**

:confused:

---

### Post by HandyAndyShortStack on 2007-11-02
so I used terminal 2 Ctrl+Alt+f2

and now I am trying the code...

---

### Post by Arthur Archnix on 2007-11-02
Reboot in safe (recovery) mode. Should let you login as root from there. You'll need to write that command down though so that you can punch it in.

EDIT: I see. Interesting that. Ok.

---

### Post by HandyAndyShortStack on 2007-11-02
Actually, Im posting from my girlfriend's windows laptop.  If I can get ubuntu running smooth on the powerbook, we'll ubuntu this one, too!

Well, I ran the command and rebooted.  But it didn't seem to work.  Maybe braving a reinstall will be less trouble.  But _why_ didn't it work?  I am very confused.

---

### Post by HandyAndyShortStack on 2007-11-02
Actually, Im posting from my girlfriend's windows laptop. If I can get ubuntu running smooth on the powerbook, we'll ubuntu this one, too!

Well, I ran the command and rebooted. But it didn't seem to work. Maybe braving a reinstall will be less trouble. But _why_ didn't it work? I am very confused.   OOPS I DID THAT TWICE

---

### Post by Arthur Archnix on 2007-11-02
Ok, so you logged in as root, no problems. You ran the usermod command. No problems. You used your username instead of username. No problems. Then, you rebooted, and tried so make a test directory in media, using sudo, but that didn't work? Is that right? What about the cat /etc/sudoers, can you post the output of that command yet? If not, run it from root terminal logged in on F2 or wherever you ended up.

---

### Post by HandyAndyShortStack on 2007-11-02
here is the output for cat /etc/sudoers run from my root terminal:

[B]# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults              !lecture,tty_tickets,!fqdn

# User privilege specification
root      ALL=(ALL) ALL[/B]

and then I get another prompt

oh, and yes, you summed up the order of events very accurately

---

### Post by Arthur Archnix on 2007-11-02
Ok, you'll have to log in as root and type:
```
visudo
```
Then add this to the bottom.
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```
Save and exit. Reboot the computer. Login as normal. And everything should work fine. If I recall correctly, saving means exiting. But read any prompts that you're given.

EDIT: I'm taking this from my install, which is a default gutsy and what you probably would have ended up with had you done a normal install. Just so you understand my source of information on this.

---

### Post by HandyAndyShortStack on 2007-11-02
rebooting now.  This is so cool.  I am learning a lot.  How can I get back into Xfce from a terminal?

---

### Post by HandyAndyShortStack on 2007-11-02
Now I get this when I try to make a test directory as andy:

andy is not allowed to run sudo on Artemis.  This incident will be reported.

Oh man, my admin is going to be pissed when he finds this ;-)

I'll login as root and make sure i copied your script correctly.

---

### Post by Arthur Archnix on 2007-11-02
Lol. Yeah. The first time I saw that message I was at school and it actually did freak me out. Anyway, seeing it is a good sign. 

I rechecked the command I gave you and there's an error. My bad. After -G do -a
so it would be
```
usermod -G -a admin username
```
Don't worry about all the others yet. Once we add you to admin, you can sudo add yourself to the rest. And remember to change username.

---

### Post by HandyAndyShortStack on 2007-11-02
yep, its all there.

is there a way I could just login to Xfce as root?

EDIT:  didn't see your post first

---

### Post by HandyAndyShortStack on 2007-11-02
I get this:

**usermod: unknown group -a**

---

### Post by Arthur Archnix on 2007-11-02
I don't know what you mean, "it's all there". And once your permissions are fixed, yes we can get you logging in as root. But you've demonstrated an ability to manage permissions, so you should consider carefully whether you want to throw out one of the biggest security features of ubuntu and linux.

Not sure if it matters, but I see some places write:
```
usermod -a -G admin username
```
a before the g.

If that goes well let me know the outcome of the mkdir test.

EDIT: IT apparently matters. ;) We're going to fast for each other.

---

### Post by HandyAndyShortStack on 2007-11-02
Yes the reversed version didn't give me an error.
But when I rebooted and logged in as andy, i got the ominous "not allowed to run sudo" message again.
Why is it that the thing that works is always the last one you try?

---

### Post by HandyAndyShortStack on 2007-11-02
Not to lose sight of my goals, iwconfig as root can see my wireless card, but iwlist scan claims that it doesn't support scanning: no such device.  Not even in monitor mode.  weird.  I think it will work anyway, though.

---

### Post by Arthur Archnix on 2007-11-02
The only two things we need for sudo access is for the sudoers file to allow anyone in the admin group to run sudo, second for andy to be a member of the admin group. One of these two conditions must fail.

cat /etc/group | grep andy will list every group you currently belong to. Going by my setup, you should see the following (I've cleaned it up a bit):
```
adm
dialout
cdrom
floppy
audio
dip
video
plugdev
scanner
lpadmin
admin
netdev
powerdev
andy
```
If any of those are missing, run for each one.
```
usermod -a -G missinggroup andy
```
Next, cat /etc/sudoers should look like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

The last line is really important. You may need to do something like Ctrl + O that's an o, like outside, not 0 like  0123 to save your changes before exiting.

If those two are like mine, and you're still getting errors, I'm stumped. I think maybe your change didn't take effect though. That admin line wasn't saved. That's my guess.

Edit. I recall, this is just a means to an end.

---

### Post by HandyAndyShortStack on 2007-11-02
I had neglected to add andy to any group but admin.  I fixed that.  I also had a tab in the last line instead of a space.  I changed that, too.  I saved and restarted.  I still get the error.  I don't know what to think now.  It is after midnight, though, so I guess barring any extremely helpful/confident further posts, I will just reinstall tomorrow in normal mode.  Thanks for the tour into the strange and magical land of linux, though.  I learn more with each challenge.  :guitar:

---

### Post by Arthur Archnix on 2007-11-02
My confidence is as plentiful as my help is useful. Good luck with the reinstall. 

:-?

---

### Post by HandyAndyShortStack on 2007-11-03
UPDATE:

The [reinstall]("http://ubuntuforums.org/showthread.php?t=594324") went smooth as butter.  And I can get internet w/ wicd.  I am posting from the powerbook now :) :) :)

---

### Post by Arthur Archnix on 2007-11-03
8-)

Glad to hear it. By the by, given that you'd said you wanted to run as root, but that gave you grief. You notice that line in the sudoers file I had you messing with? It says, uncomment this to not require a password. I think that may give you a close approximation to what you were looking for. You'd still have to type sudo in the terminal, you just wouldn't get pestered for a password to much.

Of course, best practice would be to run using the default settings, but that may be worth looking into and reading about some more if you're still looking for a way to loosen up permission restrictions on your account.

Best of luck.

---

### Post by HandyAndyShortStack on 2007-11-04
I just screwed up xorg.conf and had to figure out how to use the terminal to fix it in order to be able load xfce.  Maybe its a good idea to keep people like me out of the inner workings of an os.  For now, I am content to jump through a few more hoops if it means I am less likely to render my computer unusable. :neutral:

---

