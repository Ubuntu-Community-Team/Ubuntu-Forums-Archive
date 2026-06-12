---
title: "About root"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by lab0rized on 2006-03-07
Hello, it was the second time i installed ubuntu in 2days :)

First time i installed it i did it fast while reading a book, so i just spottet the informations about the different things and hit the enter button. When i had installed it i tried to do the "su" command in the terminal, and enter the password i used for my user, it said that my password was wrong ?

But now to the big question ? How can the password be wrong when it was the only password i had wrote in the installation ?

And because i became unsure i installed it today again to see if i was promted for the root password and i didnt ?

:KS

---

### Post by meborc on 2006-03-07
use SUDO instead of SU... more information: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Xian on 2006-03-07
Read the [RootSudo How-To](https://wiki.ubuntu.com/RootSudo) for more information.

---

### Post by lab0rized on 2006-03-07
Thanks meborc..
I used the search button on the forum as i use to do.. But this time i was so stupid to forget it. My bad but thanks again :)

---

### Post by towsonu2003 on 2006-03-07
wiki.ubuntu.com/RootSudo

this is a good read ^
su won't work in ubuntu. for any commands requiruing root access, use sudo command instead. be careful with it though, root is dangeruos (you type a command wrong, you'll reinstall everything...)

edit: wow people are fast!!

---

### Post by nocturn on 2006-03-07
Ubuntu does not have a root password set.

Try using sudo -s to get a root shell (give it your own password).

---

### Post by stanz on 2006-03-07
Hi All,
I did 'something', again.
I was changing permissions to: *usr/share/gdm* , to save themes and such.
I didn't type anything for etc, to get this,- so now i'm more in the dark.
> *sudo: /etc/sudoers is owned by uid 1000, should be 0* This is now a constant response, in the terminal, and i've lost access to: *Admin->Users&Groups*.
I figured i'ld try to give *chown*, back to *root*, but- no change?
Any Ideas? Thoughts? HowTo's?
:confused:

---

### Post by meborc on 2006-03-07
well... you can boot up in "rescue" mode... then you don't get to gnome, but you are automatically with root permissions... then you can solve the problem in shell...

EDIT: oh... did you tried it already? there were instructions how to create a new user with all permissions... then log in as that user... fix the problem for your old user and kill the "dummy" ... srry don't remember where i saw it...

---

### Post by Pragmatist on 2006-03-07
The message is that the /etc/sudoers file should be owned by root not by your regular user (id 1000).  To be sure try ```
ls -l /etc/sudoers
```  > su won't work in ubuntu  sudo is the preferred way, but su should definitely work. I've used it many many times.  What happens if you use ```
su
``` type in your root password and administer that way?  or switch virtual terminals (VTs) by:
```
CTRL-ALT-F5
```
and login as root

---

### Post by Iowan on 2006-03-07
**su** works only IF you've enabled the root account (not active by default so there's no root password to provide).

---

### Post by Pragmatist on 2006-03-07
Wow!  I've used su on over a half-dozen different Linux distros.  I understand that the purpose of sudo is to protect the user from the computer and vice-versa...but isn't this going too far.  In other words, to use sudo for one-time root access makes sense since you could forget to logout from root.  But if you have both options whats the problem? I'll forget that there is a command called sudo and then I'll use su and then I'll forget to logout!! :)

Sorry...getting off topic here a bit.  How do you create a root account in this case?

---

### Post by towsonu2003 on 2006-03-07
[QUOTE=Pragmatist]
Sorry...getting off topic here a bit.  How do you create a root account in this case?[/QUOTE]
Read this one from start to end: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) than decide whether you'll want root account enabled.

I use sudo -i as an emulator of su in terminal.

---

### Post by stanz on 2006-03-07
Hi All..  Pragmatist, meborc - Thanks for being here!!
I just thought of 'Rescue' mode, and will try that after these attempts.

[quote=Pragmatist]The message is that the* /etc/sudoers* file should be owned by root not by your regular user (id 1000).[/quote] Thanks for typing that. I thought that- but,
 i'm newbie- so recieving confimation is a big help, in how i think- i understand, whats going on.
> ls -l /etc/sudoers Done that, & its shows:
[I]stanz@gyspy:$ ls -l sudoers
-r--r-----  1 stanz root 406 2006-03-06 08:59 sudoers[/I]
 So i tried:
[I]stanz@gyspy:etc$ chown root sudoers
chown: changing ownership of `sudoers': Operation not permitted
-----------------
stanz@gyspy:~$ su chown root /etc/sudoers
Unknown id: chown
-----------------
stanz@gyspy:~$ su chmod root /etc/sudoers
Unknown id: chmod
-----------------
stanz@gyspy:/etc$ sudo chown root sudoers
sudo: /etc/sudoers is owned by uid 1000, should be 0
-----------------
stanz@gyspy:~$ su
Password:
su: Authentication failure
Sorry.
[/I]----------------
> or switch virtual terminals (VTs) by:CTRL-ALT-F5 and login as root I've not done VTs, and using the buttons- nadda happened? 
------------------
I'm reading that 'rootsudo-wiki' & have a debian bible next to me- but, i'm feeling the 'unexperianced user' feeling. 
and have the disk handy- for my easy way out- to reinstall.
AAHhhhhhhhhh!!!!!!!!

---

### Post by towsonu2003 on 2006-03-07
sudo gives errors, so you cant get root permissions, meaning you can't modify sudoers. give it a try in the rescue mode, where you'll have root.

the command will be
chown root:root /etc/sudoers
in *rescue* mode. in normal ubuntu, command will be *sudo* chown root:root /etc/sudoers

---

### Post by stanz on 2006-03-07
Thanks towsonu2003... I first tried now- on normal ubuntu::
[I]stanz@gyspy:~$ sudo chown root:root /etc/sudoers
sudo: /etc/sudoers is owned by uid 1000, should be 0
stanz@gyspy:~$[/I]
I'm thinking its how i'm addressing the change~?~ but, donno.
I'm restarting...check ya's in abit!
Thanks again for the help & time!! :)

---

### Post by Pragmatist on 2006-03-07
> Read this one from start to end: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) than decide whether you'll want root account enabled.
Thanks for the info towsonu2003.  I read it and found it useful and interesting even though I don't agree with all of the points made.

---

### Post by towsonu2003 on 2006-03-07
[QUOTE=Pragmatist]I read it and found it useful and interesting even though I don't agree with all of the points made.[/QUOTE]
8-)

---

### Post by stanz on 2006-03-07
Never made it outta here- grins - I googled the wiki a few different ways, and glanced this one, before shutting down: [_this wiki page about file permissions_]("https://wiki.ubuntu.com/FilePermissions?highlight=%28permissions%29")
and thought i needed to try it. 
I managed to change permissions abit- tho, where i'm too go with this, is still 'blindly'.
[i]stanz@gyspy:~$ chmod o+rwx /etc/sudoers
stanz@gyspy:~$ ls -l /etc/sudoers
-r--r--rwx  1 stanz root 406 2006-03-06 08:59 /etc/sudoers[/i]
I'm trying to give root or other(?)permission to take me out, & get root back in.
`er... this sound right?

---

### Post by stanz on 2006-03-07
stanz@gyspy:~$ sudo chmod root:root /etc/sudoers
sudo: /etc/sudoers is mode 0447, should be 0440

---

### Post by towsonu2003 on 2006-03-07
As I mentioned before
[QUOTE=towsonu2003]sudo gives errors, so you cant get root permissions, meaning you can't modify sudoers. give it a try in the rescue mode.[/QUOTE]
more clearly, you cannot get root permissions because sudo is broken. you cannot fix sudo, because you cannot get sudo permissions. try the rescue mode...

when you go to rescue mode, type: 
```

chown root:root /etc/sudoers
chmod 440 /etc/sudoers
ls -l /etc/sudoers

```
I don't have my ubuntu here, but I believe (logically), output should look like:
```

**-rw-r--r--** 1 **root root** 406 2006-03-06 08:59 /etc/sudoers
``` *I am not sure about these permissions and I don't remember what 0440 was, so someone with a working sudo please check the output...*

---

### Post by Pragmatist on 2006-03-07
**-r--r-----  1 root root 374 Jan 29 19:32 /etc/sudoers**
This is 0440  first 0 is for special bits (SUID, SGID, and sticky bit are disabled)
440 is r--r----- as r=4 w=2 x=1

---

### Post by stanz on 2006-03-07
Yep... Your right, i'm changing permissions, which isn't the fix- 
guess i needed to hear it twice.
[I]stanz@gyspy:~$ chmod 0440 /etc/sudoers
stanz@gyspy:~$ ls -l /etc/sudoers
-r--r-----  1 stanz root 406 2006-03-06 08:59 /etc/sudoers

bowing my head...and logging out.........
[/I]

---

### Post by stanz on 2006-03-07
Hello again... and Thanks...
[I]stanz@gyspy:~$ ls -l /etc/sudoers
-r--r-----  1 root root 406 2006-03-06 08:59 /etc/sudoers
[/I]Tho, the "*root:root" *got an "*invalid string"* response- using "*root*" worked!
I'm still unable to load: Admin->Users&Groups ?
I get the busy spinning curser, then nadda.
Geez- even Synaptic Package Manager, isn't loading.
and Add Application, & Login Screen Setup.. :(
~very deep breath....

Thanks again towsonu2003, I've still got the point-n-click of M$ in my brain,
And i've jumped into linux full time. :)

---

### Post by stanz on 2006-03-07
So Far...It's getting better!
I found & used the commandline to run 'synaptic' & it gave the
same owner error.
I logged out again, ran rescue & code again~ and Whala...
Did i say thanks?
I'm left with ' HAL ' failing to initize, wherever that came from?
Now i really wonder, what i did, to create this- from jus' changing
permissions- to save themes & splashs in /usr/share/ ??

---

### Post by towsonu2003 on 2006-03-07
I still have windows around (dual boot, 6-8 months now, never used Windows for last 3 months) just in case I screw something... you went cold turkey: stressful ;)

type gksudo synaptic[1] in terminal, what does it say (in terminal)? [1]: if you're kubuntu, I think the command was something else (should be in the wiki page RootSudo). the output from terminal for gksudo synaptic should tell something for inability to use synaptic... does sudo work? (try with sudo ifconfig, which will just give you a list of enabled interfaces -ethernet, modem and stuff- nothing important). 

thanks pragmatist for the important correction. 

what's the output of ls -l /etc (to see if you changed just sudoers or everything), preferably as a file attachment instead of text -too long. For now, I'm clueless what's wrong though.

edit: what were your exact procedures while changing fonts and stuff?

---

### Post by stanz on 2006-03-09
Hi All, Hi towsonu2003...
I'm Ubuntu- gksudo is it:
[I]:~$ gksudo synaptic
(synaptic:9127): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 
`gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed[/I]
But it loads, so i believe its all good? But, what do i know :rolleyes: ?   and i usually go thru the panal anyway.

I was trying to add splash screens & themes, by following directions from another thread. 
I was in "*/usr/share/gdm*", with no access- as all was owned by root.
I changed ownership to load/save themes and such.
The "*/share*", folder i now/still own, w/group root;
----------------------
I believe i *typo'ed* bad...reallly bad.
Thanks again for your help!!

ps...would loosing 'mount' & panal icon, share my blunder?
the "*/usr*" folder- root owns w/group root.
I think this is what your asking for- the "*/etc*" is attached.

---

### Post by towsonu2003 on 2006-03-10
> **stanz]Hi All, Hi towsonu2003...
I'm Ubuntu- gksudo is it:
[I]:~$ gksudo synaptic
(synaptic:9127): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 
`gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed[/I]
But it loads, so i believe its all good? But, what do i know :rolleyes: ?   and i usually go thru the panal anyway.[/quote] if that loads from terminal, it should load from the panel as well. it's the same "command"... (I get the same errors, no worries there) Everything root related should now be working as well... 
[QUOTE=stanz]
I was trying to add splash screens & themes, by following directions from another thread. 
I was in "*/usr/share/gdm*", with no access- as all was owned by root.
I changed ownership to load/save themes and such.
The "*/share*", folder i now/still own, w/group root[/quote]
I see. you probably mistyped and it changed permissions for more than youasked. themes are installed using the user's home, System>preferences>theme. default permissions of root folders are not changed, unless you spot a security issue (such as too broad permissions for something that should only be read by the root). Your new permissions may introduce security weaknesses to your system. I would wait until dapper comes around and do a fresh install to fix this... it's too easy to screw thing while using root. root is kinda the regular windows user if not careful  said:**
> 
ps...would loosing 'mount' & panal icon, share my blunder?
the "*/usr*" folder- root owns w/group root.
I think this is what your asking for- the "*/etc*" is attached.
file isn't attached. I am attaching mine so you can compare stuff. use it only as a general reference to see what's changed after your command. I wouldn't change permissions based on my output, especially bc. each file and folder within /etc has their own permission patterns. use it just to get an idea of what the command did... 
oh, I was asking for /etc, bc your command apparently changed sudoers under /etc. 

what do you mean by loosing mount and panel icon? can't you mount / unmount stuff with sudo? and by the panel icon you mean...? (sorry, I'm sleepy ;) )

---

### Post by stanz on 2006-04-07
Hi All....Hi towsonu2003...
Sry~ Got busy... but, Thanks for your info & reply...it worked out fine.
I did some back tracking with the terminal command memory use, and
it got fixed.
I had loaded a 'debian menu' type thingy...thru synaptic- and it doubles up
- giving its own menu icons...and it took away- others.
The mount/unmount icon was one of 'em. I only noticed, cause i used it often!
Thanks again for your help...!!!

---

