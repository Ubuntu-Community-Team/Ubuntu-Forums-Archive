---
title: "Can't login to Ubuntu PC from Mac on LAN"
date: 2005-09-07
forum: Apple PPC Users
---

### Post by tjerome on 2005-09-07
I've installed Ubuntu on a PC with no problems. It connects to the Internet over my LAN via Linksys WRT54G (wired) router and to DSL modem. I can move files back and forth to other Windows PCs on the LAN. However, I can neither "see" my Mac running OS X (Panther) from Ubuntu nor can I log in to the Ubunto machine from the Mac.
 
Here's the odd thing:
From the Mac, I can see the Ubuntu machine, and can choose a particular folder that I have shared. When I type in my user/password login info, though, I get rejected, even though I use the *only* user login for the Ubuntu machine! How can it be wrong?

---

### Post by lubod on 2005-09-18
When you say your Ubuntu PC cannot "see" the Mac, you mean ping and traceroute, or ? That by itself won't solve your problem but it may help having that working to achieve what you want.

On the Mac, try ssh from terminal window to the Ubuntu PC with that same username/password. Does that work? 

See this thread, only ignore the posters which claim Samba only works Unix to Windows, it works between two Unixes just fine. 

[http://ubuntuforums.org/archive/index.php/t-30243.html](http://ubuntuforums.org/archive/index.php/t-30243.html)

Maybe the hint about running smbpaswd?

[http://ubuntuguide.org/#addeditdeletenetworkusers](http://ubuntuguide.org/#addeditdeletenetworkusers)

BTW ubuntuguide.org is very good, even if heavily PC centric most tips work on Ubuntu PPC as well, as long as there is nothing x86/AMD spedific about them.

Other guesses:

maybe the Mac OS 10.3 Samba won't play nice with Ubuntu? If at connect time you have any user defined options, I think there was a button dialog to select how OS X sends passwords over the network, plain text or encrypted. If the option is there, try whichever one wasn't on by default.

Find out where Samba stores its logs in Ubuntu and see if it reports the error on login.

Cribbed from O'Reilly's how to for generic Samba, which may or may not apply to Ubuntu:

[INDENT]**By default, logs are placed in samba_directory /var/smbd.log and samba_directory /var/nmbd.log, where samba_directory is the location where Samba was installed (typically, /usr/local/samba).[/INDENT]** 

Try upgrading the Ubuntu Samba in Synaptic assuming it is too old, as in older than the OS X 10.3 one. Not very likely but you never know. To find Samba version in OS X, type smbd -V (has to be capital V) in to Terminal. Tiger (aka 10.4) has Version 3.0.10 for comparison.

Maybe get a hold of 10.4, lots of stuff is relating to OS interoperability is updated to this is likely to solve it if nothing above helps.

---

### Post by tjerome on 2005-09-18
Wow! Thanks for such an in-depth reply!
Unfortunately, none of your suggestions worked.
I *am* able to ping between Ubuntu and Mac in both directions.

When I used "see" in my message, I meant that I could see the name of the Ubuntu PC ("archive") in OS X's Finder, Networking view. Clicking on it brings up the user/password dialog, which has always failed in this case.

I tried "ssh -v archive" from a Mac terminal window, but got an error msg: "Rhosts authorization disabled, originating port will not be trusted. No address associated with nodename."

I am *very* much a newbie at command-line *nix, so please take that into account. I chose Ubuntu for its cababilities and pleasant GUI.

The ubuntuguide.org is offline. I found the wiki, but found nothing useful for this problem.

I am running Samba 3.0.10-Ubuntu, so I guess it's up-to-date.

I have a Mac running Tiger (10.4) as well, and have the same problems there.

I have restarted Samba, but no change is apparent.

The log file had no comment about failed logins.

I'd love more suggestions!

---

### Post by patrickp on 2005-09-20
hi,

have u set the right smbpasswd for the user u try to log in??

smbpasswd username

and have u made the right entry in the smb.conf??

for example if u want to browse and write to a driectory try to add this to your smb.conf


if u want to allow only one user for example peter 
use valid users = peter 
if u like all users
use vlid users = @users

[Documents]
   comment = Documents
   path=/documents
   browseable = yes
   writeable = yes
   valid users = username
   create mode = 0770
   create mask = 0770


i hope this could help u

patrick

---

### Post by tjerome on 2005-09-25
Patrick -
Thanks for your help! I tried everything you suggested, but it's still no-go.
Is the file that stores the smb passwords supposed to be in the samba directory? I don't see that file. The command to change the password (I needed to use "sudo" in front of the command you gave, by the way) seemed to work properly.

I'm still not able to log in from my Mac, either vias the GUI Network icon, or via command-K directly to the folder I want. Both give "pasword wrong"-type messages.

Sigh. I'm very close to giving up on this system. It's proved inscrutable to me, despite 20 years of CPM/DOS/Windows/Mac experience. Why can't all of this be done via the Ubuntu GUI, anyway? I'm not one of those who think CLIs are macho. I just want my tools to *work*!

---

### Post by patrickp on 2005-09-26
hi,

in /etc/samba there should be the following files (u dont have the smb1.conf it was only a testfile for my changes)
server:/etc/samba# ls
gdbcommands  smb.conf  smb1.conf  smbpasswd

the problem also could be that u do not allow your mac to connect to any other devices

to change this behavour you must go to the settings
then go to sharing
and there u can enable the use of ssh samba ....
you have to activate windows file sharing

i hope this could help u gl

cu

patrick

---

### Post by tjerome on 2005-09-26
Patrick,
Thanks!
Are you using the Hoary Hedgehog (current) version of Ubuntu? You specific comments do not jibe with my version. For instance, I do NOT have the smbpasswd file in my samba folder, despite the fact that the password program worked and asked the appropriate questions.

Also, maybe you were relying on memory and not actual screens when you used "settings" and "sharing" -- I have Administration main menu, with "Shared Folders" as a submenu. When I cleicked on my shared folder and got properties for it, it shows shared with SMB, and browsing the folder is allowed.

Under "Administration", "General Windows Sharing", My host server si set to samba, ubuntu. The domain is set to my windows network domain name, and the WINS server option is set to "this is a WIN server".

So no change.
Ted

---

### Post by patrickp on 2005-09-26
ok back again

i tryed to do the same u want to do
it worked

started with an update

apt-get install samba

ps ax | grep smbd (see if samba is running)

su

smbpasswd -a username

type passwd
retype

at mac u press the apple and the k button (connect to server)
smb://ipadress of ubuntu machine

type username
type passwd

username and passwd casesensitve

now it must work

gl

patrick

---

### Post by patrickp on 2005-09-26
ok back again

i tryed to do the same u want to do
it worked

started with an update

apt-get install samba

ps ax | grep smbd (see if samba is running)

su

smbpasswd -a username

type passwd
retype

at mac u press the apple and the k button (connect to server)
smb://ipadress of ubuntu machine

type username
type passwd

username and passwd casesensitve

now it must work

gl

patrick

---

### Post by tjerome on 2005-09-27
Still not working.
I had to pre-pend "sudo" to get your first line to work -- "sudo apt-get install samba". It indicated that my version is up-to-date.

The ps command showed a line ending with "/usr/sbin/smbd -D". Does that indicate that Samba is running?

"su" doesn't work for me, because I don't have a root user defined, apparently. Could that be an issue? Might this whole thing be a permissions problem?

I've already set my username's password as you indicate, several times before.

I also restared samba with "sudo /etc/init.d/samba restart". It said "stopping samba"..."starting samba", so I assume that it HAD been running before.

I used command-k on the Mac to log in as before. It asks for the folder I want of the two that I've set on ubuntu as shared, so I choose one and enter case-sensiive name & password. The answer is always "password not correct".

BTW, in the Mac's sys prefs, Sharing, I've set "personal file sharing" and "windows sharing" to be on.

I'm eager for any other suggestions.

---

### Post by patrickp on 2005-09-27
hi back again

pls send me your smb.conf
mail is [email]patrick.proyer@gmx.at[/email]

i will try to find out if u have a problem in this file 

cu

patrick

---

### Post by tjerome on 2005-09-27
Patrick,
I've sent the file to you.
Ted

---

### Post by tjerome on 2005-09-30
Well, it's solved! Thought I'd finish this thread with an addendum. 
Patrick had lots of ideas to try, and we spent a few days in direct email contact to get it solved.
I think what actually worked was for me to realize that the "root" user was assigned *no* privileges. So I used the System --> Administration --> User and Groups menu to select the root user, go to Properties, select the User Privileges, and check all of the unchecked boxes. I wonder if this makes my system less secure?  :-(

Anyway, after I did that I was able to log in to the Ubuntu machine from my Macs and Windows machines.
Many thanks for all who helped!
Ted

---

