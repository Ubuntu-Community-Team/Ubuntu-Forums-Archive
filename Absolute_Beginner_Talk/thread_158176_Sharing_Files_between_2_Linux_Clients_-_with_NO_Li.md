---
title: "Sharing Files between 2 Linux Clients - with NO Linux Server?"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-04-10
Hello All!!!

I would like to know how can I share files between 2 Networked Ubuntu v5.10 Desktop (Gnome) Client PCs...

And _without_ using an intermediary Ubuntu Server PC...

So far, _all_ I am reading in the Net, is connecting Clients to an Ubuntu Server & NOT Client to Client connections...

Is that possible & how would someone go doing this?
(what packages do I need to install?)

Thanks.

---

### Post by ubernoob on 2006-04-10
when you are downloading files from one of your clients to the other, the first will act as a server and the second as a client. So actually, bot of your clients will be servers :)


Search for how to set up NFS. And set up both as servers for the spesific service.

---

### Post by KingBahamut on 2006-04-10
apt-get install openssh-server on one of the two boxes. 

Then you can use Places > Connect to Server....> change Drop down to SSH and supply the nessecary information > then connect. 

You can then freely move data from one server to the next.

---

### Post by Spano on 2006-04-10
Sorry - my explanation was incorrect.  Could someone delete this post, please?

---

### Post by dvarsam on 2006-04-10
[QUOTE=ubernoob]when you are downloading files from one of your clients to the other, the first will act as a server and the second as a client. So actually, bot of your clients will be servers :)

Search for how to set up NFS. And set up both as servers for the spesific service.[/QUOTE]

Dear "Ubernoob",

I am sorry for NOT clarifying this...

These 2 client PCs are NOT far away from each other...
They are both wired through an Intermediary Router, and there is NO "downloading" involved... (these 2 Ubuntu Clients are _only_ 2 meters away from each other!!!) 

What should I do?
_Question_:
Is what you are suggesting, _still_ what I should be doing in my case?

OR:

Are things are different now & I should go for a different approach?
And if the later is the case, what should I do?

---

### Post by dvarsam on 2006-04-10
[QUOTE=KingBahamut]apt-get install openssh-server on one of the two boxes. 

Then you can use Places > Connect to Server....> change Drop down to SSH and supply the nessecary information > then connect. 

You can then freely move data from one server to the next.[/QUOTE]

Dear "KingBahamut",

Installing "openssh-server" on PC#1 means that PC#2 can log-in to the PC#1...

But IF I _also_ wanted PC#1 to log-in on PC#2, should I also install "openssh-server" on PC#2?

P.S.> Please keep in mind that those 2 PC's are NOT far away from each other - _only_ 2 meters away & connected through a Router...

---

### Post by ubernoob on 2006-04-10
to answer your two questions. It doesn't matter if they are 2 meters away or in two diffrent countries. Both solution works. (actually samba wouldn't work) 

anyway...I think ssh is easier for you to manage, so you should try that. Your clarifying doesn't change the case.

If you are copying one file from another computer, you are downloading the file ;)

---

### Post by dvarsam on 2006-04-10
[QUOTE=KingBahamut]apt-get install openssh-server on one of the two boxes. 

Then you can use Places > Connect to Server....> change Drop down to SSH and supply the nessecary information > then connect. 

You can then freely move data from one server to the next.[/QUOTE]


Thank you ALL for your Replies!

OK, I installed "openssh-server" on PC#1!

_Question 1_:
Shouldn't I also install "openssh-client" on the PC#2?

_Question 2_:
From the PC#2's Menu, I selected: "Places\Connect to Server..."

a. Under "Service Type:", I selected "SSH".

b. Under "Server:", I typed "192.168.1.2" (the IP of the PC#1 I want to connect to...)

c. Under "Port:", I typed "22" (do I need to activate a Port?  & where? - on the Router?)

d. Under "Folder:", what do I type here?

e. Under "User Name:", what do I type here?

f. Under "Name to use for connection:", what do I type here?

Thanks!

P.S.> Sorry for being too Noob at this...

---

### Post by ubernoob on 2006-04-10
Q1:
you don't have to. but you can if you want. try to get it working on one of them first. and then set up the other if you like
Q2:
c. no
d. nothing
e. you username on PC#1
f. the name you want to call the connection. a folder on your desktop will be called this name. it doesn't matter what you write

---

### Post by dvarsam on 2006-04-10
Dear "ubernoob", I have done according to your instructions:

From the PC#2's Menu, I selected: "Places\Connect to Server..."

Then:

a. Under "Service Type:", I select "SSH".
b. Under "Server:", I type "192.168.1.2" (the IP of the PC#1 I want to connect to...)
c. Under "Port:", I leave blank
d. Under "Folder:", I leave blank
e. Under "User Name:", I type "dimitris" - the username I use when log-in to PC#1
f. Under "Name to use for connection:", I type "testing"

I then click on the button named "connect" & a window comes up with the following info:

Title:
Cancel Open?

Contents:
Opening "testing".
You can stop this operation by clicking cancel.

Button Choices:
Cancel

This window takes forever to connect & No LEDs are blinking on my Router...
Is this normal?
How long do I have to wait for my connection to finally occur?
It has been 5 minutes now... & I am still waiting...

Thanks.

---

### Post by ubernoob on 2006-04-10
system-->administration-->services
make sure remote shell server (ssh) is checked.

and try it from a terminal and see what the output is:
ssh username@192.168.1.2

---

### Post by dvarsam on 2006-04-10
[QUOTE=ubernoob]system-->administration-->services
make sure remote shell server (ssh) is checked.

and try it from a terminal and see what the output is:
ssh username@192.168.1.2[/QUOTE]

Dear "ubernoob",

I checked under "System\Administration\Services" & the "Remote Shell Server (ssh)" is checked!

From the Terminal, when I tried to connect with the command:

> ssh dimitris@192.168.1.2

I got a successfull connection!!!

Is this the only way I can connect?

Can't I connect through a "window" environment instead of a "CLI" environment?

And how would I do that?

Thanks.

---

### Post by ubernoob on 2006-04-11
if that works, you should be able to do the same from the place->connect to server as you tried in the previous post. You must have done something wrong there.

---

### Post by dvarsam on 2006-04-11
[QUOTE=ubernoob]if that works, you should be able to do the same from the place->connect to server as you tried in the previous post. You must have done something wrong there.[/QUOTE]

Dear "ubernoob",

I am doing exactly as you suggested!!!

As I said before:
From the PC#2's Menu, I selected: "Places\Connect to Server..."

a. Under "Service Type:", I selected > SSH.

b. Under "Server:", I typed > 192.168.1.2 (the IP of the PC#1 I want to connect to...)

c. Under "Port:", I left blank!

d. Under "Folder:", I left blank!

e. Under "User Name:", I typed > dimitris (The username used when I Log-in on the PC#1)

f. Under "Name to use for connection:", I typed > trial

_Question_:
Are you sure I should NOT install "openssh-client" on the PC#2?

What else could be wrong?

P.S. 1> Basically I can access the other PC through the Terminal but NOT through a GUI window...

P.S. 2> Does it matter if both PC#1 & PC#2 have their "hostname" named "ubuntu"? Should they be different?

---

### Post by dvarsam on 2006-04-11
Dear "ubernoob",

I would also like to ask you _IF_ I should perform this:

From the Menu, select "System\Preferences\Remote Desktop"

Under "Sharing", enable the "Allow other users to view your desktop"

Should this be activated?

Is this the reason why from the PC#2 I can NOT see a GUI window with PC#1's contents?

---

### Post by steve.horsley on 2006-04-11
I think I know what the problem is here. SSH likes to know that it is connecting to the right machine. If you manually SSH from one machine to another, the first time you connect SSH asks you if this is the right machine, and if you say yes then it adds the machine to its "known hosts" database. I suspect that if you ter and SSH to an unknown host from the Nautilus GUI, it just sits there with the question unseen and therefore unanswered (I blame Nautilus here). 

Try connecting with SSH from the command line first (**ssh username@servername**). It will get the entry put into the known hosts database, and will also serve as a useful check that basic SSH is working.

---

### Post by dvarsam on 2006-04-11
[QUOTE=steve.horsley]I think I know what the problem is here. SSH likes to know that it is connecting to the right machine. If you manually SSH from one machine to another, the first time you connect SSH asks you if this is the right machine, and if you say yes then it adds the machine to its "known hosts" database. I suspect that if you ter and SSH to an unknown host from the Nautilus GUI, it just sits there with the question unseen and therefore unanswered (I blame Nautilus here). 

Try connecting with SSH from the command line first (**ssh username@servername**). It will get the entry put into the known hosts database, and will also serve as a useful check that basic SSH is working.[/QUOTE]

Dear "Steve.horsley", 

thank you for your reply!!!

I was in the process of doing what you suggested!

And wanted to copy & paste what I got from using the Terminal inside a Text document, then copy to a Floppy, move it to the other PC to provide Feedback...

It seemed that I could NOT even create an Empty Text Document in the Desktop...!

I performed a Restart & now everything seems to be OK & working!!!

However, I would like to ask the following:

_Question 1_:
How can I limit the rights given to the PC#2 only to "Read/Execute" & NOT "write"? (because now, the guy from the other Network PC can come in & delete ALL my files!)

_Question 2_:
I am connecting from the PC#2 (named "elena") to the PC#1 (named "dimitris") with "ssh". If I want to copy a file from the PC#1 to PC#2 _from_ the _Terminal_, I get the following error:

> dimitris@ubuntu:~/Desktop$ cp eautoinstall.sh elena@192.168.1.3:/home/elena/Desktop
cp: cannot create regular file `elena@192.168.1.3:/home/elena/Desktop': No such file or directory
dimitris@ubuntu:~/Desktop$

What is wrong & why it can NOT copy?

Should I do a: "cp [email]dimtris@192.168.1.4:/home/dimitris/Desktop/eautoinstall.sh[/email] elena@192.168.1.3:/home/elena/Desktop" ?

_Question 3_:
When I create the Connection (from the Menu, I select "Places\Connect to Server..."), a folder is created on My Desktop... When I finish, I right-click on that folder & select "unmount"...
But the folder dissapears!!!
So, every time I want my PC's connected I have to re-type ALL the data back in? How can I make that folder (or connection) permanent?
I mean, that my 2 PC's are 2 meters away from each other...
I do NOT want to Log-in & Log-out, every time I boot my PCs...!

_Question 4_:
4. I want a permanent connection tha works on both directions: PC#1 -> PC#2 & PC#2 -> PC#1.
Right now, only PC#2 can actually work on PC#1! Not the opposite!!!
I understand that this would be the case for a "Remote Connection" but NOT the case for a _Local_ Networking situation... In a Local Networking situation you need _permanent_, bi-directional connections...
It is NOT the same case like "Remote Desktop"...

Sorry, but either Networking in Windows is simpler, or I seem to be missing something....:-k
(I mean: in Windows, you go under "Network Places" & you can see all the PCs in the Network & then you double-click to a folder to enter to another Machine and view its files... Here NO PC's are seen on My Network! & every time I want to connect to a different Networked PC, I have to create a connection, Log-in, Log-out, & after Log-out, the connection dissapears... it seems very complicated, and that is why I assume that there must be some easier way... my PC's are only 2 meters away..., I am NOT trying to Log-in from a different planet!???)...

Please help...
Thanks.

---

### Post by dvarsam on 2006-04-11
Regarding my "Question 2":

I visited the following link:
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

And performed the following:

> dimitris@ubuntu:~/Desktop$ scp eautoinstall.sh elena@192.168.1.3:/home
ssh: connect to host 192.168.1.3 port 22: Connection refused
lost connection

Why do I get the above "lost connection" & the copy is never performed?

Thanks.

P.S. 1> Please do NOT forget my other questions too!

P.S. 2> Are my expectations too high to want to have on my Ubuntu a Regular Network like in Windows?

---

### Post by halfvolle melk on 2006-04-11
Q1:
How can I limit the rights given to the PC#2 only to "Read/Execute" & NOT "write"? (because now, the guy from the other Network PC can come in & delete ALL my files!)

A1:
One still needs to know the username and password to access the remote computer. Just make sure the password is good.

Q2:
What is wrong & why it can NOT copy?

A2:
You run a server on PC#1. It can be accessed by PC#2. You don't have a server running on PC#2(right?) and therefore can not be accessed by PC#1. To fix this, set up a server on PC#2 just like you did on PC#1.

Q3:
I do NOT want to Log-in & Log-out, every time I boot my PCs...!

A3:
I read somewhere that it is possible to auto mount ssh. While I'm sure you could, maybe something like NFS is less of a hassle.

Q4 & 5:

See A2.

---

### Post by dvarsam on 2006-04-11
Dear "halfvolle melk", 

Thank you for your reply!

I have still some questions on this...

> Q1:
How can I limit the rights given to the PC#2 only to "Read/Execute" & NOT "write"? (because now, the guy from the other Network PC can come in & delete ALL my files!)

A1:
One still needs to know the username & password to access the remote computer. Just make sure the password is good.

Yes, I understand what you mean...
But suppose I work in a company & want "Every Company's Employee" to be able to _only_ view my computer's files...

In this case, everybody knows my computer's password, because that is the only way they could actually view my files...!

The problem is that I do NOT want them to be able to "tamper" my files, so Read/Execute is fine, but "Write" has to be denied in some way...

Any ideas?

> Q2: What is wrong & why it can NOT copy?

A2:
You run a server on PC#1. It can be accessed by PC#2. You don't have a server running on PC#2(right?) and therefore can not be accessed by PC#1. To fix this, set up a server on PC#2 just like you did on PC#1.

This was fixed, right after I installed "openssh-server" on the PC#2 too!
Thanks, that did the trick!!!
(Personal Note: you must restart your Ubuntu if you want this to work!)

> Q3: I do NOT want to Log-in & Log-out, every time I boot my PCs...!

A3:
I read somewhere that it is possible to auto mount ssh. While I am sure you could, maybe something like NFS is less of a hassle.

I performed a search on this, I found the following thread:
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-%20%20filesystem-using-sshfs](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-%20%20filesystem-using-sshfs)

It is a thread that teaches how to mount a Remote SSH Filesystem using "sshfs".

I followed the instructions & did the following:

1. Run: > apt-get install sshfs(The program needed for this to work)

2. Run: > mkdir /media/dimitris (The PC#1 will be mounted in the following directory created on PC#2)

3. Run: > chown elena /media/dimitris (The owner rights of the folder "/media/dimitris" must belong to the current PC#2's user & not to root)

4. Run: > adduser elena fuse (The current PC#2's user _must_ belong to the group name "fuse" - a group created by the installation of the package "sshfs" from Step 1)

5. Reboot my Ubuntu.

6. Launch a Terminal & type: > sshfs dimitris@192.168.1.2:/home/dimitris/Desktop /media/dimitris
(Here I have no problem, I type the PC#1's user password & a new icon is created on my Desktop, named "dimitris".)

The problem is that when I double-click on that icon on my Desktop, NO window opens & I can see NO contents of the PC#1's directories...

Any ideas?

Thanks.

---

### Post by halfvolle melk on 2006-04-12
Hey Dvarsam,

> But suppose I work in a company & want "Every Company's Employee" to be able to _only_ view my computer's files...
I think creating a not so privileged user on the server side will fix that. It should be something like "sudo adduser iamaguest". Again, do this on the server side. Try it out and see if the defaults are restrictive enough for you.

As for sshfs, let's try one thing at the time ;)
You mentioned earlier you had it working but when you unmounted it, the folder disapeared. So don't unmount it, it will be there even after a reboot!

Reading the man page of adduser I found this:
> The --disabled-password option will not set a password, but login  are  still  possible  for  example through SSH RSA keys.
I can't try it out at the moment because I only have one system running, but you might get it to accept just the username. Try something like this (not sure if it will work):
```
sudo adduser --disable-password iamaguest
```
Go to the other machine and double click the ssh-folder. Enter "iamaguest" and connect. Now if that's too much effort to connect you'll need to have a word with your staff ;)

---

### Post by dvarsam on 2006-04-12
Dear "halfvolle melk",

Thank you for your repply!

> I think creating a not so privileged user on the server side will fix that. It should be something like "sudo adduser iamaguest". Again, do this on the server side. Try it out and see if the defaults are restrictive enough for you.


On PC#1: I created a user "guest" using the _Menu_ (by selecting "System\Administration\User & Groups") instead of doing it from the Terminal.
On PC#2: I tried connecting to the PC#1 (on the LAN):
a. I tried to "ssh" to the folder "/home/dimitris" & was able to Read but not Write (which is good!).
b. When creating the user "guest" from the Menu (instead of Terminal), there was NO dedicated folder created under the "/home" directory for the user "guest" (which is bad!).

So, I decided to _delete_ the user "guest", I created from the Menu...

Instead, I did the following:

On PC#1: I created a user "guest" using the _Terminal_:> adduser guest
I assigned a password & was notified that a directory "/home/guest" were created! (this is much better! :D ).
On PC#2: I tried connecting to the PC#1 (on the LAN):
a. I tried to "ssh" to the folder "/home/dimitris" & was able to Read but not Write (which is good!).
b. I also tried to "ssh" to the folder "/home/guest" & was able to Add/Edit/Delete Files or Folders (which is good!).

Note:
When creating a OOO "Writer's" file, you must save as:> sftp://guest@192.168.1.2/home/guest/aaa.doc, to save it inside the PC#1 (I did not know how to do this!).

_Outcome_:
It is better to Add users from the Terminal & NOT from the Menu, because the  Menu does NOT create a "/home/user" directory, although the Terminal does! 

_Question 1_:
What if I wanted to "disable" (or NOT allow) a "guest" to have Read/Write/Execute Rights to _ANY/ALL_ other Folder except his "/home/guest" folder? 


> As for sshfs, let's try one thing at the time ;)
You mentioned earlier you had it working but when you unmounted it, the folder disapeared. So don't unmount it, it will be there even after a reboot!


All previous procedures were done with "ssh".
With "sshfs" things are different!

Yes, I managed to have an icon created on my Desktop, but that icon had NO contents...
So, basically, it seemed that "sshfs" was NOT working...
That is why I decided to "unmount" it...
Because it was useless!!!

_Question 2_:
So, what do I do here?

_Question 3_:
If instead of "sshfs", I stay with "ssh", will a Reboot make "ssh" Desktop icons dissapear?
OR: will the "ssh" icons on the Desktop remain as is...?
It would be good it they could remain on the Desktop...!


> Reading the man page of adduser I found this:

I can't try it out at the moment because I only have one system running, but you might get it to accept just the username.
Try something like this (not sure if it will work):
```
sudo adduser --disable-password iamaguest
```
Go to the other machine and double click the ssh-folder. Enter "iamaguest" and connect. Now if that's too much effort to connect you'll need to have a word with your staff ;)

I then decided to _delete_ the user "guest", I created from the Terminal, to try out this new stuff you are suggesting, which sounds really good (& promising)!!!

I did the following:

On PC#1: I created a user "guest" using the _Terminal_:> adduser --disabled-password guest
(Note: You had made a typo error on the suggested "--disable-password", it should be "--disabled-password", but that was ok..., I used the "--help" to find out...)
On PC#2: I tried connecting to the PC#1 (on the LAN):
a. I tried to "ssh", but NO matter what the folder I was trying to connect to were, I got a prompt asking me to type-in a "password"...
Even IF I decided to leave it blank & click on "OK" (or "Connect"), I was asked again to retype-in a "password"...
This seems to NOT work...

_Question 4_:
Any ideas how we could make "sshfs" work?

Thanks.

---

### Post by halfvolle melk on 2006-04-12
> Question 1:
What if I wanted to "disable" (or NOT allow) a "guest" to have Read/Write/Execute Rights to ANY/ALL other Folder except his "/home/guest" folder?
I don't know but I think a user that can't execute stuff in /bin, /usr/bin and so on is useless. If you only want to read-only share a specific folder [NFS](https://wiki.ubuntu.com/SettingUpNFSHowTo) or [Samba](http://doc.gwos.org/index.php/Share_files_using_Samba) might be better options than Ssh.
> Question 3:
Will a Reboot make "ssh" Desktop icons dissapear?
No, they will stay on the desktop.
> <the no password thing>
This seems to NOT work...
Hmm, that's to bad. Reading into it some more it says you need to generate RSA keys for this to work. I don't know how that works, but apparently it's not considered to be very secure so you may not want to bother trying.
> Question 4:
Any ideas how we could make "sshfs" work?
When I tried it a while back I did what it says [here](http://fuse.sourceforge.net/sshfs.html) and it just worked.

---

### Post by dvarsam on 2006-04-12
Dear "halfvolle melk", 

Thank you for your reply!!!

Your feedback has been very helpfull!!!

> Any ideas how we could make "sshfs" work?
When I tried it a while back I did what it says here: [http://fuse.sourceforge.net/sshfs.html]here](http://fuse.sourceforge.net/sshfs.html]here)
and it just worked...

The above thread was very helpful!!!

I noticed a very important line in there:
> ...Note, that it's recommended to run it as user, not as root.  For this to work the mountpoint must be owned by the user...

What I did was performing the "sshfs" command, from being "root" - e.g. > root@ubuntu:~#sshfs ...blah... ...blah...

While I should be performing the "sshfs" command, from being "user" - e.g.
> elena@ubuntu:~$sshfs ...blah... ...blah...

When I did the later, everything worked perfectly!!!

You have also suggested the following:

> Will a Reboot make "ssh" Desktop icons dissapear?
No, they will stay on the desktop.

The above is TRUE, I have tested it & it works!
(the only thing I have to do every time, is re-type the password... & I guess that if I would like to avoid this, I would have to read more on what you suggested: "...to generate RSA keys for this to work...").

However, this is NOT what is happening when I create an "sshfs" connection!

The "sshfs" connection's icon, does NOT remain on the Desktop & I have to re-activate the connection (or re-type everything to make the icon appear on the Desktop again), from the Terminal...

Is there a way to make an "sshfs" connection permanent of the Desktop?

Thanks.

---

### Post by halfvolle melk on 2006-04-12
It's good to hear some of my suggestion are of help.
> Is there a way to make an "sshfs" connection permanent of the Desktop?
I guess you could create the mountpoint on you desktop and try the auto mount thing using that mount point. The Sshfs has something to say about that:
> Automatic mounting, if desired, can be added to a shell script such as .bashrc (provided authentication is done using RSA/DSA keys).
I've never done it so I can't realy help you with that.
Again I'd like to stress that doing this is not considered to be secure:
> NOTE: While it is possible to generate a set of RSA keys for use with OpenSSH which do not have a password assigned to them, for easy, password-less logins via ssh, this guide does not describe, or endorse such use as it is very insecure. If your password-less keys fall into the wrong hands, then so does your authentication, thereby allowing easy compromise of all systems which permit the keys. In certain situations, such as insecure clustered environments, completely password-less logins my be desirable, but again, this guide does not explain the process of creating such keys.
[https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH)
You may want to reconsider using either NFS or Samba if all you want to do is access some remote files password and hassle free.
Good luck!

---

### Post by Jose Catre-Vandis on 2006-09-07
> **KingBahamut said:**
> apt-get install openssh-server on one of the two boxes. 

Then you can use Places > Connect to Server....> change Drop down to SSH and supply the nessecary information > then connect. 

You can then freely move data from one server to the next.

Wow, Linux just gets better each day. After months of fighting with samba, I find NFS works like a charm and then I findyou can do file sharing using SSH. Fantastic, and thanks.

---

