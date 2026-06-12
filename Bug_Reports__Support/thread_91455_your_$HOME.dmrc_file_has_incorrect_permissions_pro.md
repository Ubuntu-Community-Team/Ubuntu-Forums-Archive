---
title: "your $HOME/.dmrc file has incorrect permissions problem"
date: 2005-11-17
forum: Bug Reports / Support
---

### Post by Justin Morgan on 2005-11-17
Hi, when i start up Unbuntu at the login after I put in my password it says your $HOME/.dmrc file has incorrect permissions and is being
ignored. ... file sould be " "owned by user and have 644 permissions. ... what is this all about???? Thanks.

---

### Post by rjwood on 2005-11-17
from a terminal

```
sudo chown (your user name) /.dmrc
```
then you can change your permissions

---

### Post by Justin Morgan on 2005-11-17
Great thanks! Is there anything I should change it to in particular? Sorry for the elementry questions but i am new to Linux. Thanks.

---

### Post by Justin Morgan on 2005-11-17
When I tried that formula it said "cannot access `/.dmrc': No such file or directory" any Ideas?

---

### Post by rjwood on 2005-11-17
[quote=Justin Morgan]When I tried that formula it said "cannot access `/.dmrc': No such file or directory" any Ideas?[/quote]

perhaps without the ( / ).

---

### Post by Justin Morgan on 2005-11-17
Im also getting this message :justin@ubuntu:~$ sudo chown justin /.dmrc
chown: cannot access `/.dmrc': No such file or directory
justin@ubuntu:~$ sudo chown justin/.dmrc
chown: too few arguments
Try `chown --help' for more information.

---

### Post by Justin Morgan on 2005-11-17
I tried it without the ( / ), still getting the too few arguments message.

---

### Post by rjwood on 2005-11-17
```
sudo chmod 644 .dmrc
```

---

### Post by rjwood on 2005-11-17
[quote=Justin Morgan]Im also getting this message :justin@ubuntu:~$ sudo chown justin /.dmrc
chown: cannot access `/.dmrc': No such file or directory
justin@ubuntu:~$ sudo chown justin/.dmrc
chown: too few arguments
Try `chown --help' for more information.[/quote]

you need space between justin and .dmrc

---

### Post by mysurface on 2005-12-28
Sometimes its not the .dmrc problem

try to do this if chmod .dmrc doesn't work

sudo chmod 755 /home/{your username}

---

### Post by levi-ubuntu on 2006-02-17
When i try the above commands  i get as result:

sudo: unable to lookup ubuntu-on-acer via gethostbyname()


what shoudl i do..

---

### Post by jwh400 on 2006-02-18
> sudo chmod 644 .dmrc

After entering that it sits waiting for another command. I think this is why most people are intimidated by Linux. After someone says enter this command and we do and nothing happens, we don't know what to do next. After several failures at command line computing (especially the folly known as gksudo nautilus), we approach the command line with the same confidence one has when playing the lottery.

> sudo chown (your user name) /.dmrc

I tried this with and without the slash and a space between my username and .dmrc.  After entering it without the slash it sat waiting for another command. Entering with the slash gave me, "cannot access `/.dmrc': No such file or directory". 

My problem isn't identical to Justin's and I don't mean to hijack his thread but I think the solution to his problem would also solve mine and vis-a-vis. I have a lot of files that were transfered from Windows that can't be written to, moved, or copied because "You're not the owner". gksudo nautilus is _not_ the same as root because I'm still not the owner. Running in gksudo nautilus will exchange the locked folder icon for one that isn't locked but the files inside still aren't mine and I can't make them mine. My computers are;

Cyberpower
AMD 64

Toshiba A20 S207
Intel P4

Problem is identical on both.

---

### Post by Mustard on 2006-02-18
[QUOTE=levi-ubuntu]When i try the above commands  i get as result:

sudo: unable to lookup ubuntu-on-acer via gethostbyname()


what shoudl i do..[/QUOTE]

It sounds like your /etc/hosts file is misconfigured.

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt, open up the /etc/hosts file with this command.

```
nano /etc/hosts 
```

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

An additional command you can look at with regards to hostnames is this command below.

```
hostname #returns the current hostname
hostname <hostname>  #sets the hostname according to the value entered for <hostname>
```

---

### Post by zorkerz on 2006-03-16
[quote=jwh400]I tried this with and without the slash and a space between my username and .dmrc.  After entering it without the slash it sat waiting for another command. Entering with the slash gave me, "cannot access `/.dmrc': No such file or directory".[/quote]
it it is waiting for another command chances are you have already changed the owner.  Navigate to it in nautilus press Ctrl+H to show hidden files (the . infront of .dmrc means its hidden), then right click and select properties.  See if you are now the owner of the file.  Another way to enter the same command is like this ```
sudo chown (your user name) /home/(your username)/.dmrc
```
however this is just typeing extra unnecissary characters.
It is confuseing when it immediatly waits for another command, but that should mean that the previous command you entered worked without a hitch.
elias

---

### Post by Peacepunk on 2006-03-25
I am assuming people here would finally have set the proper permissions & ownerships.

I am astonished when I read a reply to a newbie that just says "Easy, man, just Chmod it": without exact llines of code, we starters are dead. I pretty much feel close to this Lottery Guy, that's right. Never know what's the output will look like.

So, just in case, And I am Checking this in a terminal @ the same time, to be sure not to give fake info:

Open this F@$@%&*ing terminal. Use a fresh session if you are already playing around for a while. I mean: close the Terminal and open it again.

It should simply show

 *username@machinename:~$*

it means you are into your home folder, it is the default starting location.

Breathe.

```


sudo chmod 644 .dmrc

```

then

```


sudo chown *username* .dmrc

```

* where ** username ** is the name of the folder the .dmrc file is into; typically, it is your login name at startup, unless you are trying to correct the problem for another user on your computer*

**to check the result using the terminal;**

```


ls .dmrc -l

```

should return something like

```


-rw-r--r-- 1 *ownername groupownername* followed by a timestamp

```

*You can copy & paste all this into the terminal if you like, as long as you replace **username** by the right name for your system. To paste into the terminal, it's Shift+Ctrl+V*

** how to check in normal folder view (Nautilus)**

open your home folder from the drop-down menu "places"

Hit "Ctrl + H" *to reveal hidden files and folders*

scroll down until you find the file .dmrc, right click, point to the "permissions" tab:

You should see file Owner, group owner and permissions checkboxes. At the bottom there is the Text view -rw-r--r-- and the number view 644.

You good now.


[CENTER][SIZE="5"][COLOR="DarkRed"]BUT I AM NOT[/COLOR][/SIZE][/CENTER]

Why ? Because I still have this warning each time I boot. With the correct settings...

[COLOR="DarkRed"][SIZE="3"][CENTER]Have fun with Ubuntu !![/CENTER][/SIZE][/COLOR]

---

### Post by Marquis_de_Carabas on 2006-03-30
After installing a new hard drive and transferring my home directory across I had this same problem (not sure what I did, but I must have messed up the transfer process somehow).

.dmrc was owned by me and its permissions were correct, but I was still having the problem.

Then I tried mysurface's suggestion, and that cleared the problem up.

So if anyone's still stuck on this try:

```
cd ~
sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username
```

(Obviously you replace "username" with whatever your username is...)

---

### Post by Peacepunk on 2006-04-08
Nope ladies & gentlemen,

/home/*username* is set to 775
/home/*username*/.dmrc is set to 644

And, yet, still this warning.

...On a brand new computer, first installation, **right after updating** the system...

[COLOR="DarkRed"]offtopic: never buy Sony Vaio, they're Shit. Life expectancy: 14 months at best.[/COLOR]

I am assuming there is a bug in the auto-updates softs that is being downloaded after you first intall 5.10 - I noticed several warnings coming alongside the auto-update tool, and in the list of unsupported softs (most of them, actually) was a "Login" update, among others.

Shall we move this thread on how to progressively reverse recently applied patches? Yes, my "sources.list" is heavily unlocked, Universe/Multiverse: Can the wrong patch come from there ? Do we have in common that we all played around too much with the ressources listed in "sources.list" ?

[COLOR="Navy"]##EDIT: "Login" software Force-Downgraded to Disk Version, nothing better END OF EDIT##[/COLOR]

BTW, I even tried to suppress the .dmrc file. Nothing more happened, only the boot that complains an unexisting file got wrong permissions... A non-existant file... Kinda funny.

---

### Post by Peacepunk on 2006-04-10
Ok folks, some more on .dmrc issues:

We are talking here about a brand new laptop (Remember: Never Buy A **Vaio**), new fresh install on an unformatted hard disk.

Whole system Ubuntu-dedicated, no other OS'es, 5.10 "breezy"

-At first "boot", and reboot, OK without .dmrc warning, at least.
-I Denied any UpGrade, suspecting one of them may contain a Bug: 

**This is NOT the issue **

-Two only other things I did, in the first 24 hours of use on this empty computer, causing the .dmrc issue to arise again as soon as I rebooted:

1) Installed various MPEG libs, required to play DVD & MP3 files.
2) Networked (using SMB) the /home dir to put my personnal data back on the new computer. It does means I changed permissions, as allowing "Write" in the networking details of SMB is actually not enough for writing files on the Laptop's HDD.

 * I am talking here about the real /home dir, with support for browsing subfolders, not the **/home/USERNAM** dir*.

Got the .dmrc warning on reboot, then. And then, whatever the values I *chmoded* it with, the warning would stay.

I then tried to put ALL FILES including /home to 644, it killed Ubuntu who wasn't able to boot my Gnome Desktop anymore.

Until I am fully cooled down, I will, such I did with my main Desktop, drop the ball with Ubuntu & get back to Suse93. Alas.

End of the Story.

(offtopic: I abandonned Ubuntu on my Desktop because of inconsistencies in handling USB devices: Sometimes, they would appear when plugged, and sometimes not. As I WORK for REAL with computers, I had to cut it short & get an OS that works.)

I may give it another try, be it Badger or Dapper, on my spare time.

Cheer lads, keep on exchanging experiences, Ubuntu is a trully great project. For people that likes to potter around computers.

_

---

### Post by LordMerlin on 2006-04-18
[quote=Peacepunk]Ok folks, some more on .dmrc issues:

We are talking here about a brand new laptop (Remember: Never Buy A **Vaio**), new fresh install on an unformatted hard disk.

Whole system Ubuntu-dedicated, no other OS'es, 5.10 "breezy"

-At first "boot", and reboot, OK without .dmrc warning, at least.
-I Denied any UpGrade, suspecting one of them may contain a Bug: 

**This is NOT the issue **

-Two only other things I did, in the first 24 hours of use on this empty computer, causing the .dmrc issue to arise again as soon as I rebooted:

1) Installed various MPEG libs, required to play DVD & MP3 files.
2) Networked (using SMB) the /home dir to put my personnal data back on the new computer. It does means I changed permissions, as allowing "Write" in the networking details of SMB is actually not enough for writing files on the Laptop's HDD.

 * I am talking here about the real /home dir, with support for browsing subfolders, not the **/home/USERNAM** dir*.

Got the .dmrc warning on reboot, then. And then, whatever the values I *chmoded* it with, the warning would stay.

I then tried to put ALL FILES including /home to 644, it killed Ubuntu who wasn't able to boot my Gnome Desktop anymore.

Until I am fully cooled down, I will, such I did with my main Desktop, drop the ball with Ubuntu & get back to Suse93. Alas.

End of the Story.

(offtopic: I abandonned Ubuntu on my Desktop because of inconsistencies in handling USB devices: Sometimes, they would appear when plugged, and sometimes not. As I WORK for REAL with computers, I had to cut it short & get an OS that works.)

I may give it another try, be it Badger or Dapper, on my spare time.

Cheer lads, keep on exchanging experiences, Ubuntu is a trully great project. For people that likes to potter around computers.

_[/quote]

Gee. Something like this makes me want to throw my PC(s) out of the window and get typewriter.  I can't see why a Vaio would simply only last 14 monts. That's odd, but it's not odd to get a factory defect, since Sony(like most large manufacturers) manufacture these by the thousands a day. Funny how mine has lasted much much longer than 14 months.

Anyway. Something interesting which can be seen in this (like many threads on this forum), if something doesn't work for you, it doesn't. But that doesn't mean it's bad, and it's not working for many other people. This problem seems to be a problem due to many reasons. It's strange though that I have different problems with different Linux's. At this stage I use Suse 9.3, Ubuntu 5.10, Fedora 2, Mandiva 2005, FreeBSD 5.4. They all have their own strenghts (and weaknesses in some people's views). BUT, if they all had to have the same strenghts, then you sit with what MS has accomplished up to now. A LOT of strenghts (some are good, even), which DOES introduce a lot of weaknesses as well. 

Heck, I can gaurentee you I'd be able to create problems in Windows (by doing normal day-to-day work), which can't be fixed. Some problems creep up by themselves, even some of those can't be fixed. Think about this before you say Ubuntu is bad, or it's not "Real computer work ready" Running it as a network file & print server / router / firewall with 70+ Windows PC's is real work. Using it for development is real work. 

Just my 2c

---

### Post by Ecthelion on 2006-04-22
I know this .dmrc error 'cause I have the same,

I think the only reason why it comes is becuase you copy your old home dir to the new one, and copying along the .dmrc file

I had found the solutions above myself, but it didn't made the error go away. I suspect the error message is wrong and that the error is caused by something else.

Still i think Ubuntu is great, and doesn't make me being afraid of the command line, even if I have already done rather stupid stuff with it.
Just have some research instead of just copying everything someone says...


I also tried something else: making a new user and copying his default files to my home dir, and then change the owner... It didn't worked either, confirming my suspection that it is caused by something else then .dmrc

But don't do dramatic, if u get so angry about that message, just make a new user and don't copy your old home dir to it.
You wont have your problem then

---

### Post by Mustard on 2006-04-22
I hope someone comes up with the definitive solution to this problem one day and documents it. :)  I could store it in my little desktop wiki then.

---

### Post by kaih on 2006-04-29
[QUOTE=Mustard]I hope someone comes up with the definitive solution to this problem one day and documents it. :)  I could store it in my little desktop wiki then.[/QUOTE]

Hi,
i think i found at least one problem.
this is in /etc/gdm/gdm.conf
solution:
1. leave your permission as they are(see below). 

2. in /etc/gdm/gdm.conf  in section security insert:
"RelaxPermissions=1"

3. restart gdm by killing and starting it again from a real console([CRTL-ALT-F1] ->login->#killall gdm->#gdm).

that should fix it if you havn't screwed up your permissions with your tryes to get them right. and never touch the graphical configuration tool or remember these steps.

bug(szenario):
this is a bug in the configuration tool, as it changes a setting, which it shouldn't(you didn't ask for it to do so!). 
if you do a configuration via the graphical configuration tool(e.g. from the greeter) it deletes this key.  that means default which falls to 0. so after configuration this key is no longer in the file and when gdm is restarted(and this IS usualy only after a reboot) permissions are checked "paranoid". this means at least no group writable home.

group writable homes are no security hole when intended - as well as umask  002. "user private groups" are common in debian(ubuntu as well). in this case each user has its own group and no one but the user can access a group writable home. 


comment:
further the user who wrote that this problem occured only after a reeboot,   WAS right. the configuration is reread only after a start of gdm - no logout and no zapping(ctrl-alt-backspace) causes a reread. after install he had a correct configuration from the maintainer, he changed the settings(e.g. language or the session, somthing like that) which where not read as long as gdm kept running and only after the reboot they where read in with the missing key. and the message popped up. 

this is at least one bug causing this problem. 
regards,
kai

---

### Post by raovq on 2006-04-30
i had this problem for ages. i usually just ignore it, then out of frustration i just deleted the file and ignored it.

so, to fix it, i recreated the file;

gedit .dmrc
then i closed and saved the file


then i changed the permissions for my entire home directory (not sure why, it was suggested)

> 
sudo chmod 755 /home/{your username}


then i changed the permissions for .dmrc

> 
sudo chmod 644 .dmrc

sudo chown username .dmrc



im not sure what combination fixed the problem, but it worked for me perfectly.

---

### Post by kaih on 2006-04-30
Sorry raovq, but your solution does NOT help in many cases. In cases it helps you only need to follow the messagebox advice.

in many cases this does not help as not only the file ".dmrc" is checked but as well  parenting directories(and the messagebox tells you). additionaly this helps only if you realy have messed up the permissions of .dmrc, wich is NOT the case if you didn't change them before. further it might not help if you have an umask of 0002(or 002) which is sometimes the case[umask gives the default permissions for new created files and is traditionally 0022(recreation helps) but nowadays very often 0002(recreation doesn't help) ] 
and Peacepunk wrote > /home/username is set to 775. so he indeed has group writable homes which is his choice and not necessarily a security hole.
 
```

chown username /home/username;
chown username /home/username/.dmrc
chmod 744 /home/username
chmod 744 /home/username/.dmrc

```(or 755/700?) as mysurface and you suggested might help but may also break things if one needs a 775 home(for what reason ever).  sometimes chown wouldn't work with shares as the server would deny changing the ownership.


Rather than in ".dmrc" the problem lies in  "/etc/gdm/gdm.conf", in which one key(RelaxPermissions) is missing. 
In addition to the above stated:
in ```
section security
```:
```
RelaxPermissions=0
``` means paranoid. may be too much checking for a debian(ubuntu) system(for shure if umask is 002).
```
RelaxPermissions=1
``` means group writeble is ok. this is what you might want with debian(ubuntu) if your users have their own groups.
```
RelaxPermissions=2
``` means world writable. in most case you will not want world writable homes.

 gdm default(the key is missing): ```
RelaxPermissions=0
```

second addition:
i did not check what realy goes wrong. i only found that after configuring with the graphical tool(e.g. from the gdm greeter) and a restart of gdm this key is missing(as others which don't bother to me as the default is what i want. this means it may as well be the case that gdm.conf is rewritten at start of gdm when something is wrong with the file and this causes the loss of the key or somthing else. i only know that this key is missing which shouldn't be the case.

third addition:
you may also expirience this if you have home directories owned by someone else(eg mounted shares). in this case ```
CheckDirOwner=false
``` will help(but this means there is almost for shure a security hole in your system).

... and don't forget to restart gdm after editing the gdm.conf. this means killing gdm. zapping or logging out does not restart gdm! if you don't know how to do this, simply reboot the computer(the point is to get gdm to read its configuration for which you don't need a reboot but a restart of gdm).
kai

---

### Post by raovq on 2006-04-30
is turning down the permissions mearly sidestepping the problem and getting rid of the message box?

unbuntu wants a certain permission for your home for security. wouldn't advising people just to turn the warning off be unwise?

---

### Post by kaih on 2006-04-30
[QUOTE=raovq]is turning down the permissions mearly sidestepping the problem and getting rid of the message box?

unbuntu wants a certain permission for your home for security. wouldn't advising people just to turn the warning off be unwise?[/QUOTE]

yes, as ubuntu has a reason for groupwritable homes, this is why i advise not to change them - but if you mean it is correct that gdm refuses to  read a configuration(!) if a user sticks to this default configuration: no, it is save and gdm should kindly stop moaning. 
there are different scenarios:

_traditional unix_: all users in one group. in this case it would be correct to warn you. in this case (775 permission) is almost for shure a security hole and in this case you will want a warning - the default setting in gdm.conf(**RelaxPermissions=0, 744 for $HOME and 644 for $HOME/.dmrc** . this is what the massagebox tells). 

_nowadays_ you very often have a group for each user. in this case it is no security hole to have group writable homes. in this case, there is no reason moan about homes with writaccess for groups as this group has only one user(the owner) - except other users are put in this group _manualy_ and that means it is intended by the admin. **RelaxPermissions=1, 774 for $HOME and and 664 for $HOME/.dmrc** is save and imho a warning about a not existing security hole is nonsense.

and if you have groups wich work together on a project and give them a working directory you often need umask 002 instead of 022 which is the whole point in giving users their own group. and this means a default creation of files with 664 permission instead of 644.


put it short("id -gn" gives your primary group):
[LIST]
[*]**the way to go with traditional unix -  "users" is the primary group** 
in /etc/gdm/gdm.conf as root set in section security
```

 RelaxPermissions=0

```

```

chmod o-w,g-w,a-x .dmrc
chmod o-w,g-w $HOME

```
additional steps if neccessary(give root password when asked):
```

su -c "chown $USER $HOME"
su -c "chown $USER $HOME/.dmrc"

```
(if you delete .dmrc,  it should be created automaticly correctly with the next start of gdm otherwise "touch .dmrc"). this was also suggested before.
[*]**with user private groups(each user has its own group, "id -gn" tells the same as "id -un" )**

in /etc/gdm/gdm.conf set in section security
```
RelaxPermissions=1
``` 
and 
```

chmod o-w,a-x .dmrc
chmod o-w $HOME

```
additional steps if neccessary(give root password when asked):
```

su -c "chown $USER $HOME"
su -c "chown $USER $HOME/.dmrc"

```

[*] **if you want for $HOME a different owner**
iin /etc/gdm/gdm.conf in section security set
```

CheckDirOwner=false

```
and do one of the above steps without additional steps(chown...).
[*] **if you want an open open box(no security checks - not recomendet)**
set RelaxPermissions=2 in gdm.conf
[/LIST]
(to edit gdm.conf you need to be root and gdm restart is necessary. hope now this is complete?)

[I]one add(remark):
in order to make shure that a user doesn't temper with permissions and make his directories open to the world, it is  best to let the home directory be owned by someone else, some user created only for this purpose, give homedirectories a 770 permission and users their own groups. that way each user can access his directory -  everything is possible but he can neither change group or user nor permissions of the directory. that way you prevent a user from giving away his home directory to the world. you further prevent some linking into the directory.... this is only possible if you have a group for each user and writepermision for this group. 
ahh and  770 is not realy neccessarry 070 shoud do, but ...  off topic - some background to explain
[but you are right, Peacepunk didn't seem to care too much about permissions ... but look at the viewcount of this thread, there are many others ][/I]
look also at the debian bug database for some description:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=339965](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=339965)

---

### Post by nickleus on 2006-05-03
WTF! why does this have to be so complicated? why the piss does a stupid problem like this arise anyways?
when you finally log in do this:
```
rm .dmrc
```

reboot. problem fixed (at least it was for me...) =)

---

### Post by kaih on 2006-05-03
[QUOTE=nickleus]WTF! why does this have to be so complicated? why the piss does a stupid problem like this arise anyways?[/QUOTE]
you had a security hole! good thing you fixed it.
[QUOTE=nickleus]
when you finally log in do this:
```
rm .dmrc
```
reboot. problem fixed (at least it was for me...) =)[/QUOTE]
1. a simple log in would have been enough instead the reboot.
2. you are suggesting users to delete their customization eg. language setting...
3. this solution doesn't help in many cases.
4. in cases ist does chmod 644 .dmrc is the simple solution.
5. you suggest that an admin should tell all its user to delete their customizations - the users will for shure be gratefull.

---

### Post by peter21081944 on 2006-05-03
> restart gdm by killing and starting it again from a real console(ALT F1->login->#killall gdm->#gdm)

I've changed the gdm.conf file as described but I don't know how to get a 'real console'. ALT-F1 just drops the application menu so I am missing something!
-------------------
Ah.  1. Start an ordinary console  2. do 'sudo killall gdm' which will logout you out and blow the graphics system away. You are left with a text only screen an invitation to login. 3. Login. Still text only 4. do 'sudo gdm' and it all comes back. 

Oh yes - the problem was fixed as well. I thought only Windows had error messages like that :(

---

### Post by kaih on 2006-05-03
[QUOTE=peter21081944]I've changed the gdm.conf file as described but I don't know how to get a 'real console'. ALT-F1 just drops the application menu so I am missing something!
-------------------
Ah.  1. Start an ordinary console  2. do 'sudo killall gdm' which will logout you out and blow the graphics system away. You are left with a text only screen an invitation to login. 3. Login. Still text only 4. do 'sudo gdm' and it all comes back. 

Oh yes - the problem was fixed as well. I thought only Windows had error messages like that :([/QUOTE]
yes. you're right, it shoud have read  "CRTL-ALT-F1". i'm sorry. corrected and with  "real console" i ment a tty  in oposite to pseudo(pty).  killall from within the running windowmanager might destroy data - thats why i think logout before killing gdm is better  you could also do a ```
su -c "/etc/init.d/gdm restart"
``` or try 
```
su -c "/etc/init.d/gdm reload"
```. last is the preferred way but didn't work quite often in the past, - seems to work currently.

---

### Post by djoefish on 2006-05-06
I have had this problem for a while...and finally tried to fix it. I was getting the message even though my .dmrc was set to 644 permission.

 I changed the home folder permission to 700 (owner=rwx, and all others blank) and...

IT WORKED!!! 

Now I can log on in peace.  I hope this works for you!

djoefish

---

### Post by CameronCalver on 2006-05-07
Hey djoefish is there any way you can do that from the terminal in recovcery mode because i cant sign in default

---

### Post by djoefish on 2006-05-07
I'm not sure about the commands (I'm kinda new), but I think it would be something like:

chmod 700 <home folder>

I'm sure that someone else can correct me if this is wrong

---

### Post by e2art on 2006-06-01
[QUOTE=Peacepunk]Ok folks, some more on .dmrc issues:

-At first "boot", and reboot, OK without .dmrc warning, at least.
-I Denied any UpGrade, suspecting one of them may contain a Bug: 

**This is NOT the issue **

-Two only other things I did, in the first 24 hours of use on this empty computer, causing the .dmrc issue to arise again as soon as I rebooted:

1) Installed various MPEG libs, required to play DVD & MP3 files.
2) Networked (using SMB) the /home dir to put my personnal data back on the new computer. It does means I changed permissions, as allowing "Write" in the networking details of SMB is actually not enough for writing files on the Laptop's HDD.
_[/QUOTE]

Hi,
i do nearly the same thing as descriped above, an the solution:

[QUOTE=djoefish]I have had this problem for a while...and finally tried to fix it. I was getting the message even though my .dmrc was set to 644 permission.

 I changed the home folder permission to 700 (owner=rwx, and all others blank) and...

IT WORKED!!! 

Now I can log on in peace.  I hope this works for you!

djoefish[/QUOTE]

WORKED realy fine.

After a new log on, i set permission of the home folder back to 755 and everything is fine.

thx. :)

---

